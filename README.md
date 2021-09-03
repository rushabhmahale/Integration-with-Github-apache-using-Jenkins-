# Integration-with-Github-apache-using-Jenkins
In this, I have Integrate Github with Jenkins and Hosted my webpage also I can do real-time changes</br>


## Diagram:- 

![git presention](https://user-images.githubusercontent.com/63963025/132023976-ce62b78d-64a0-4b71-b7b4-f64a351c386f.png)

## set-up step :- 
- Go to AWS account create 2 instance with name <b>Jenkins and Webserver</b> 
- Now set all as default only change Configure Security Group <b>(All traffic) for Jenkins and change there from Anywhere</b> and </br> 
  <b>For webserver select HTTP and in custom change Anywhere</b>
- Now Open puttygen load pem file and genrate ppk key and save it 
- Open putty and paste ip of jenkins machine</br>
    <b>Jenkins Machine</b>:- </br>
    * Login with <b> ec2-user
    * `sudo su`</br>
    * `sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo ` 
    * `sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key`
    * `sudo yum upgrade`
    * `sudo yum install java-11-openjdk-devel`
    * `sudo yum install --nobest jenkins`
    * `sudo systemctl start jenkins`
    * `sudo systemctl status jenkins`
    * `sudo systemctl enable jenkins`</b>
   
 - Copy the Ip adress of Jenkins machine <b>(IP address:8080)</b>
 - Now Open putty and paste ip of webserver machine</br>
   * Login with <b> ec2-user
   * `sudo su`
   * `yum install httpd -y`
   * `yum install java-11-openjdk-devel`
   * `yum install git -y`
   * `systemctl start httpd`
   * `systemctl status httpd`
   * `systemctl enable httpd`</b>
   
 - Now go to jenkins and go to manage Node 
 - create Node `slave1 perment agent` 
 - Name :- `slave1`
 - Remote root dir :- `home/ec2-user`
 - Label :- `slave1`
 - usage :-`use this node as much as possible`
 - lounch method :- `lounch agents via SSH`
 - Host:- `IP address of Webserver`
 - Creditial:- 
    * add 
    * kind:- `SSH` VN and PK`
    * Discription:- `Slave1_key`
    * Username:-`ec2-user`
    * Enter :- `enter Your pem file key open pem file you have downloaded copy and paste the key`
    * Host key Verify:- `non verifying verification Strategy`
 - All the Configuration has been done. Now your jenkins is connected to Webserver 
 - Go to jenkins create Job name test1 and select free style project 
 - in restrict where this project can be run under that option select label experession</br>
   write slave1
 - Go to build execute shell write `sudo mkdir /root/test1` 
 - now go to job and build now run the job you will see that you have successfully deployed your job   
 
  

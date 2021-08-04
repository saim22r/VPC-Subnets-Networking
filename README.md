# VPC, Subnets, Networking, NACL

## Initial steps
- Create a VPC with the ip 10.103.0.0/24
- Create Subnets (Public, private, bastion) with different IPS for each subnet `10.103.CHANGE_THIS_NUMBER.0/24`
- Create internet gateway 
- Create route table and add route 0.0.0.0/0 and target internet gateway 
- Set the route table in the public and bastion subnets 

## Create security groups
  
App
![img_2.png](images/img_2.png)

Database
![img_3.png](images/img_3.png)

Bastion
![img.png](img.png)

## Create separate NACL for subnets
Public 
![img_1.png](img_1.png)

Private
![img_2.png](img_2.png)

Bastion
![img_3.png](img_3.png)

## Final steps
- Create instances for app (public), DB (private) and bastion (public)
- Choose the appropriate subnets for each of them and the correct security groups 
- Once running, copy the eng89_devops.pem key into the bastion server using the command `scp -i eng89_devops.pem eng89_devops.pem ubuntu@BASTION_IP:~/` 
- SSH into the bastion server and check key has copied using `ls`. 
- Move the key into a ssh folder `mv eng89_devops.pem .ssh/` and run `chmod 400 eng89_devops.pem` in the folder. 
- SSH into the DB from this folder and you should be able to connect to the DB instance.

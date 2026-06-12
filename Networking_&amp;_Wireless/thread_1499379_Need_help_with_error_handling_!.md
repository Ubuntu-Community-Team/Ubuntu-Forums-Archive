---
title: "Need help with error handling !"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2010-06-01
hey all, 

here is my script 

#!/bin/bash 
if [ $? != 0 ]; then
{
    echo "BACKUP ERROR: problem !! $variable to $variabe"
    echo $CMD
    exit 1
} fi
#this small script in a nutshell basically shows us how we would connect to another machine via ssh enjoy 
echo "hello , so your sick of having to connect to your network manualy, so you decided to create this BASH script.... lets test your network :)"
#the echo command prints the input you specify and outputs it to the shell, in this case the BASH shell
sleep 4 
#the sleep command, tells the shell to wait for 2 seconds. 2 is a variable which can be set to anytime you specify
ping -c 5 XXX-XXX-XXX-XXX
#the ping command, sends a signal to the ip-address specified and if there is a connection it replies by showing packets bouncing off that machine back to the machine you are working from, here i have told ping to stop sending packets after 5 have been recived. 
clear
#clear basically just clears the screen for easier visibility in a sense, very useful command indeed
echo "well now we have recieved 5 packets of data showing clearly we have a response from 169.254.10.97 :)" 
sleep 4
ssh -X user@XXX-XXX-XXX-XXX
#ssh is a (Secure-SHell) which allows two or more machines to connect to a network. The -X is a window manager i believe. once connected to 169.254.10.97, otherwise known as computer A, you may enter for e'g (banshee) as a command and use that program remotley. :D 



i basically need help on how to do error handling and how to make this script fully operational when it comes to error handling. Please help i have to have this script done for collage in 2 days. thank you in advance my fellow linux users.

---


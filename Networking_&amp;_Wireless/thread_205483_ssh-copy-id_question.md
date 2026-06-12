---
title: "ssh-copy-id question"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by rmmst49 on 2006-06-28
i'm running kubuntu dapper, with a verizon evdo card for my internet.  

in trying to connect to this machine via ssh, i had to add port 768(since for some reason ubuntu by default won't let me connect on port 22) to my sshd_config file, and restart ssh.  now, to connect to this machine i have to run the following command from the remote machine

ssh -o "Port 768" -v -l ryan ##.###.###.###

(if i don't add that -o port option, the request times out)

so i can connect, but only with password authentication

my question is, how to i change this command

ssh-copy-id -i ~/.ssh/id_rsa.pub ryan@##.###.###.###

so that it connects through a port different than 22?  i've trieda bunch of things, and it just keeps timing out.

thanks.

---

### Post by harisund on 2006-06-28
Here's everything you want to know about SSH and more. 

First, in order to start the SSH server, you have to execute ```
sudo invoke-rc.d ssh start
```and replace start with stop for the inverse. You will have to do this in order to effect any changes you might have made. 

The SSH server configuration page is at /etc/ssh/sshd_config. The main things you might want to edit in that are the port option (which you seem to have already changed) and the X11Forwarding option (which by default is yes, meaning encrypted X sessions over SSH are allowed)

I am surprised why port 22 seems not to be available. What I would suggest you try is stop the ssh server, execute ```
sudo netstat -plant | grep LISTEN
```which tells you all open ports on your machine (TCP). See if 22 is being used by somebody else. If not, change your SSH server config to listen on port 22 and restart it. Execute the same command again and check if 22 is being used correctly by SSH or what is happening. 

Ok, so much for the server. Now for the client side. 

The thing that most people do not know about SSH is that the client too can have a config folder. Now, in all likelihood (and by default) your private and protected keys are in ~/.ssh (that's a ".ssh" folder in your home directory). Go to that directory, and create a new file called config. ```
touch config
```This will create a new empty file called config. Open it in any favorite editor of yours. 

Looking at your code, I understand "##.###.###.###" is your machine IP address or DNS name, ryan is the user and 768 is the port. So let's create a connection with the name "home" and the above parameters. In your "config" file type in as follows:
```
Host home
 Hostname ##.###.###.###
 User ryan
 Port 768
 ForwardX11 yes
```From now on, you just have to type in ```
ssh home
``` and the connection with the above parameters will automatically be established. No "-o" , "-p", "-l" and other annoying switches at all. You can create it for any number of machines you want. The word following "host" tells the name of the connection that you will use in the command line, the word following "hostname" is the actual machine name, the word following "user" is the username and the port too is obvious. You can ignore the ForwardX11 line if you do not wish to forward X11. 

In the above case, you can simply do ```
ssh-copy-id -i ~/.ssh/id_rsa.pub home
```

I am not sure about ssh-copy-id. Does it work on Ubuntu? It doesn't work on my Cygwin (Windows) and Mac OS X SSH client agents. I use another method that is more cross platform. 
```
cat ~/.ssh/id_rsa.pub | ssh home "cat >> ~/.ssh/authorized_keys"
```
Basically I am asking my terminal to print out id_rsa.pub onto my screen, but then the output gets piped through SSH to the remote computer. In the remote computer I then print everything, this time redirecting it to the authorized_keys file, so that eventually my id_rsa.pub contents get added to the authorized_keys file of the remote computer. Of course, in the above you would replace "home" with whatever follows "host" in the ~/.ssh/config file you have.

Neat, eh?

---

### Post by rmmst49 on 2006-08-04
thanks

---


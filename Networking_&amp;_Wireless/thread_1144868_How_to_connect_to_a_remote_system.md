---
title: "How to connect to a remote system"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by aprashanth on 2009-05-01
I have two system connected in lan.. and both of the system has ubuntu (Linux) as the operating system... 

I am not able to have access from one system to the other..

I tried using the command ssh [email]mike@xx.xx.xx.xx[/email]
I am getting an error as below

ssh: connect to host xx.xx.xx.xx port 22: Connection refused


please help

---

### Post by coutts99 on 2009-05-01
Is ssh enabled? Is there a firewall blocking it?

---

### Post by Sub101 on 2009-05-01
I would suggest you need to install the openssh-server.

```
sudo apt-get install openssh-server
```

---

### Post by aprashanth on 2009-05-01
I have installed ssh by the command given by you
sudo apt-get install openssh-server

still i am getting the same error
ssh: connect to host xx.xx.xx.xx port 22: Connection refused

---

### Post by aprashanth on 2009-05-01
> **coutts99 said:**
> Is ssh enabled? Is there a firewall blocking it?
I have installed ssh..

How can i know that the fire wall is blocking me..
I am very new to this..

---

### Post by neu2buntu on 2009-05-01
do code in terminal ```
gksu ufw status
``` this will show firewall status...................................................................................................also look at man page for ufw to see how to punch hole in firewall for your connection...```
man ufw
```

---

### Post by aprashanth on 2009-05-01
> **neu2buntu said:**
> do code in terminal ```
gksu ufw status
``` this will show firewall status...................................................................................................also look at man page for ufw to see how to punch hole in firewall for your connection...```
man ufw
```
I am getting this error message

root@photon:/home/mike# gksu ufw status
No protocol specified

(gksu:10318): Gtk-WARNING **: cannot open display: :0.0
root@photon:/home/mike#

---

### Post by neu2buntu on 2009-05-01
are you running as root already ie "root@photon:/home/mike" just run as your normal user and try commands again....

---

### Post by aprashanth on 2009-05-01
> **neu2buntu said:**
> are you running as root already ie "root@photon:/home/mike" just run as your normal user and try commands again....
Sorry i am very new to all these...

when i am giving command as a normal user.. a dialog box pops up and asks me for password..when i gave the user password it is not acepting.. neither is it accepting the super user password... 

now how to proceed ??????

---

### Post by neu2buntu on 2009-05-01
the passwords dont show (as if they have not even been typed) just type your user password and hit enter.....  also running as root is a bad idea for security risks and doing damage to your file system,if you make a mistake.... thats where the "gksu" and "sudo" commands come in,... they allow the execution of the 1 command as root

---

### Post by neu2buntu on 2009-05-01
ooops just realised "gksu" open a seperate dialog box,.. the password will show as blanked out letters ie circles....then press ok

---

### Post by aprashanth on 2009-05-01
> **neu2buntu said:**
> the passwords dont show (as if they have not even been typed) just type your user password and hit enter.....  also running as root is a bad idea for security risks and doing damage to your file system,if you make a mistake.... thats where the "gksu" and "sudo" commands come in,... they allow the execution of the 1 command as root
ok... now I got it

Its giving the firewall is not loaded..

---

### Post by neu2buntu on 2009-05-01
try this on the other ubuntu box too...... am not really sure if i can be of much more help here.... have you the correct cable for connecting the 2 machines ie crossover cable.. be very specific when posting as it will help others to help you...

---

### Post by aprashanth on 2009-05-01
> **neu2buntu said:**
> try this on the other ubuntu box too...... am not really sure if i can be of much more help here.... have you the correct cable for connecting the 2 machines ie crossover cable.. be very specific when posting as it will help others to help you...
yes it is connected well..there is no doubt in it..

---

### Post by pwaldo on 2009-05-01
Try these steps.  Hydra is the machine I will SSH to.

This command will tell if you have network connectivity to the remote machine:
```
paul@zeus:~$ ping -q -c 2 hydra
PING hydra.waldo.home (172.16.0.5) 56(84) bytes of data.

--- hydra.waldo.home ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1006ms
rtt min/avg/max/mdev = 0.146/0.166/0.187/0.024 ms

```

If you have anything other than "0% packet loss", you have deeper network problems.  Now let's see if the remote machine is listening for SSH connections on port 22:
```
paul@zeus:~$ telnet hydra 22
Trying 172.16.0.5...
Connected to hydra.waldo.home.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
^]
telnet> quit
Connection closed.

```
Note that I hit Control-close-square-bracket to get the telnet prompt in order to quit.  This shows that indeed hydra is listening on port 22 and that it is the OpenSSH server that is doing the listening.  Here is an example of what you would get if there is no server listening or a firewall is blocking:
```
paul@zeus:~$ telnet hydra 23
Trying 172.16.0.5...
telnet: Unable to connect to remote host: Connection refused

```

If you get a positive response from the telnet to port 22, try ssh again.  If not, you need to get logged into the remote machine to continue finding out what is going on.  So once on the remote machine, we first see if OpenSSH is installed and if it is running:
```
paul@hydra:~$ dpkg -l openssh-server
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  openssh-server           1:4.7p1-8ubuntu1.2       secure shell server, an rshd replacement

```
"ii" at the beginning of the line indicates SSH is installed.  Now lets see if SSH is running:
```
paul@hydra:~$ sudo netstat -anp|grep :22
tcp6       0      0 :::22                   :::*                    LISTEN      6548/sshd
tcp6       0      0 172.16.0.5:22           172.16.0.8:54347        ESTABLISHED 14736/sshd: paul [p

```

This shows us that sshd is listening for connections on port 22.  Lastly, we check the firewall:
```
paul@hydra:~$ sudo ufw status
Firewall not loaded

```

Hopefully these steps should point out where the problem is.  If not, please post the results of all of these commands.  Good luck!

Paul

---


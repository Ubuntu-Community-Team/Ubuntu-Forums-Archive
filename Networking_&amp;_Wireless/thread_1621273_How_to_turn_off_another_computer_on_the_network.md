---
title: "How to turn off another computer on the network"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by alibahaloo on 2010-11-14
Hello people, i have something in mind that i want to share with you and hopefully get some new opinions...

I have a laptop and a server at home, and with my laptop i can start up the server remotely. the process is:
1. activate WOL (wake-on-lan) settings in the BIOS.
2. then using the package (wakeonlan) from ubuntu, send a set of data to turn on device.
note: the instructions are here [http://ubuntuforums.org/showthread.php?t=234588]("http://ubuntuforums.org/showthread.php?t=234588")

this works perfectly, now what i want to do is to somehow turn the server off remotely as well. i might be able to do it with SSH or some other network interfaces to send shutdown command to the server.
the server is running Ubuntu 10.10. i'm not familiar with SSH and sending commands via network, so please if anyone has a good tutorial or HowTo, post it, that would be great.
in the other hand, if any one comes with a cleaner and wiser solution, please let me know, i'd be glad to hear your opinions.

Cheers

---

### Post by spiky001 on 2010-11-14
I use ssh, I ssh into server as you said then send shutdown command, install ssh server, commands are not that hard once you get used to them, it,s usefull in other ways as well

---

### Post by alibahaloo on 2010-11-14
> **spiky001 said:**
> I use ssh, I ssh into server as you said then send shutdown command, install ssh server, commands are not that hard once you get used to them, it,s usefull in other ways as well

great, thanks...
could you show me how to install SSH, and how to send a simple command as example?

---

### Post by spiky001 on 2010-11-14
no prob in synaptic manager search "ssh openserver" install it on the machine you will want ssh into

---

### Post by alibahaloo on 2010-11-14
i searched in the synaptic package manager for "ssh openserver".. the result is only the following package:
Name: ssh
Description: secure shell client and server (metapackage), This metapackage is a convenient way to install both the OpenSSH client
and the OpenSSH server. It provides nothing in and of itself, so you may remove it if nothing depends on it.

is this the one? does it need to be installed on both systems or only the server?

---

### Post by spiky001 on 2010-11-14
install it on the machine you want to connect to. The ssh client comes with Ubuntu already yes install it

---

### Post by alibahaloo on 2010-11-14
SSH is now installed on the server (the machine i want to connect to). 
now how do i send the shutdown command to it?

---

### Post by spiky001 on 2010-11-14
from the client machine open terminal ```
ssh user@ipaddress
```, when it connects it will ask you to save a key y/n select y, it will now ask for password of user, then you will be logged into server, prompt will cahnge to username@servername:~$

---

### Post by alibahaloo on 2010-11-14
nice... now i'm connected to the server,
as you said, prompt is now: user@server :~$... many thanks :)
now what's the command to shut the system down?

---

### Post by spiky001 on 2010-11-14
```
sudo shutdown -h 0
``` ```
sudo reboot
``` depends what you need to do

---

### Post by alibahaloo on 2010-11-14
thank you very much... now all is set as i wanted ;)

thanks for your help

cheers

---

### Post by spiky001 on 2010-11-14
Is the server on the internet? if so I would change the ssh port number and maybe setup firewall or is it behind a firewalled router

---

### Post by alibahaloo on 2010-11-14
no it's not on the internet, it's on my local network

---

### Post by spiky001 on 2010-11-14
I changed the port number of ssh just incase p22 is the common number for ssh

---


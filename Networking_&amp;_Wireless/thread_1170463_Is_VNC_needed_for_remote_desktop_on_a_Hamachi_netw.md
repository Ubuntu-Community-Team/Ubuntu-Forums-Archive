---
title: "Is VNC needed for remote desktop on a Hamachi network?"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by oneiric on 2009-05-26
I read these very useful guides [here]("http://www.computechgroup.com/?p=360") and [here]("http://ubuntuforums.org/showthread.php?t=135036") on setting up Hamachi (thanks y'all).  Now that Hamachi is set up, and both computers are logged into the same hamachi network, how do I establish a remote desktop connection between the 2 computers??  Is there a guide for how to use remote desktop via hamachi? 


What else do I need besides Hamachi to enable remote desktop?  I'm using Jaunty (9.04) and the built-in System>Preferences>Remote Desktop only allows remote desktopping through local networks.


btw i'm new to linux.

---

### Post by superprash2003 on 2009-05-26
first make sure they can ping each other.. enable remote desktop , on the other machine in the terminal type vncviewer 5.x.x.x.x

 where 5.x.x.x.x is the hamachi ip of the machine which is to be remote controlled

---

### Post by doas777 on 2009-05-26
yes you still need a client. hamachi only priovides a network. now you need an app to use it. could be vnc/ssh/ samba, or whatever else,.

---

### Post by oneiric on 2009-05-26
update

 First I had to make sure that the two computers ping each other (at first pinging didn't work because I had forgotten to issue the command, hamachi go-line <network>)   

Then I typed vncviewer 5.x.x.x 

and TightVNC opened the remote display!  So it worked in one direction. 

The same thing didn't happen when the vncviewer 5.x.x.x was issued from the vice versa computers. Both computers have installed the packages tightvncserver, xtightvncviewer, tsclient, and openssh-server. One computer is Intrepid 8.10, and the other is Jaunty 9.04

---

### Post by superprash2003 on 2009-05-27
do you  use firestarter or anything similar?? did you enable remote desktop on both machines..

---

### Post by oneiric on 2009-05-27
thanks for your feedback.  Firestarter isn't installed on either machine - is it necessary??  Each computer is behind some kind of building-wide (campus) firewall so i don't have access to the "routers", but I thought that Hamachi could work even with firewalls. 

Remote desktop is enabled on both computers, by going to System>Preferences>Remote Desktop, and checking the box "allow other users to view your desktop" and the box "allow other users to control your desktop".  

 Do i have all the packages needed, because I was hoping to remotely control the mouse, and right now when TightVNC opens after typing vncviewer 5.x.x.x, I can only view the remote desktop screen.  Also I was hoping to get this working in the opposite direction, with the client as the server, and the server as the client.

---

### Post by doas777 on 2009-05-27
> **oneiric said:**
> thanks for your feedback.  Firestarter isn't installed on either machine - is it necessary??  Each computer is behind some kind of building-wide (campus) firewall so i don't have access to the "routers", but I thought that Hamachi could work even with firewalls. 

Remote desktop is enabled on both computers, by going to System>Preferences>Remote Desktop, and checking the box "allow other users to view your desktop" and the box "allow other users to control your desktop".  

 Do i have all the packages needed, because I was hoping to remotely control the mouse, and right now when TightVNC opens after typing vncviewer 5.x.x.x, I can only view the remote desktop screen.  Also I was hoping to get this working in the opposite direction, with the client as the server, and the server as the client.

your "view only" problem is probably Desktop effects enabled on the target machine. you can disable them graphically, or use 'metacity --replace' to disable them over ssh.

---

### Post by doas777 on 2009-05-27
> **oneiric said:**
> thanks for your feedback.  Firestarter isn't installed on either machine - is it necessary??  Each computer is behind some kind of building-wide (campus) firewall so i don't have access to the "routers", but I thought that Hamachi could work even with firewalls. 

Remote desktop is enabled on both computers, by going to System>Preferences>Remote Desktop, and checking the box "allow other users to view your desktop" and the box "allow other users to control your desktop".  

 Do i have all the packages needed, because I was hoping to remotely control the mouse, and right now when TightVNC opens after typing vncviewer 5.x.x.x, I can only view the remote desktop screen.  Also I was hoping to get this working in the opposite direction, with the client as the server, and the server as the client.

Hamachi will work with many firewall configurations, but not all of them. can the machines ping eachother after establishing the hamachi connection?

---

### Post by oneiric on 2009-05-27
So even though the Hamachi release for Linux 0.9.9.9-20-lnx from 2006 is somewhat difficult to install, I finally got it working between 2 ubuntu computers.  The 2 computers can ping and SSH each others 5.x.x.x and 192.x.x.x address.

The question still remains - is it possible to set up remote desktop, where I can control the mouse of the remote computer? The built-in Remote Desktop Viewer doesn't allow me to control the mouse.  Running tsclient through its GUI interface, nor typing vncviewer 5.x.x.x which opens TightVNC will allow me to control the mouse of the remote desktop. Firestarter isn't installed and Desktop effects are off for both computers.

---

### Post by doas777 on 2009-05-28
> **oneiric said:**
> So even though the Hamachi release for Linux 0.9.9.9-20-lnx from 2006 is somewhat difficult to install, I finally got it working between 2 ubuntu computers.  The 2 computers can ping and SSH each others 5.x.x.x and 192.x.x.x address.

The question still remains - is it possible to set up remote desktop, where I can control the mouse of the remote computer? The built-in Remote Desktop Viewer doesn't allow me to control the mouse.  Running tsclient through its GUI interface, nor typing vncviewer 5.x.x.x which opens TightVNC will allow me to control the mouse of the remote desktop. Firestarter isn't installed and Desktop effects are off for both computers.

does it work if you tunnel the vnc connection via ssh?
```
vncviewer -via user@5.x.x.x localhost:0
```

also what message do you get back from:
```
telnet 5.x.x.x:5900
```

---

### Post by oneiric on 2009-05-29
the commands ping 5.xxx.xxx.xxx and ssh 5.xxx.xxx.xxx show that the 2 computers can talk to each other over a hamachi connection, but

telnet 5.xxx.xxx.xxx:5900

telnet: could not resolve 5.xxx.xxx.xxx:5900 / telnet: name or service not known

and I wasn't sure what to use as localhost in the command 'vncviewer -via user@5.x.x.x localhost:0'

i really don't know whats goin on with setting up a VNC connection, so unless theres an easy way to set up VNC through my existing ssh connection, i'll be stuck with using [NTRConnect or logmein]("http://ubuntuforums.org/showthread.php?t=272986&NTRConnect or logmeinpage=16")

---

### Post by doas777 on 2009-05-29
> **oneiric said:**
> the commands ping 5.xxx.xxx.xxx and ssh 5.xxx.xxx.xxx show that the 2 computers can talk to each other over a hamachi connection, but

telnet 5.xxx.xxx.xxx:5900

telnet: could not resolve 5.xxx.xxx.xxx:5900 / telnet: name or service not known

and I wasn't sure what to use as localhost in the command 'vncviewer -via user@5.x.x.x localhost:0'

i really don't know whats goin on with setting up a VNC connection, so unless theres an easy way to set up VNC through my existing ssh connection, i'll be stuck with using [NTRConnect or logmein]("http://ubuntuforums.org/showthread.php?t=272986&NTRConnect%20or%20logmeinpage=16")

ok, first things first. VNC = Ubuntu Remote Desktop. they are the same protocol with only minor differences. in this discussion the terms are interchangable.

that said, remeber, ubuntu remote desktop requires the interactive user to be logged in before the connection can be established. this is the key differance betweens ubuntus implementation and the standard VNC server.

the 'localhost:0' is the display on the ssh server that the VNC (remote desktop) is listening on (0 is the default). Do not change that parameter, just paste it in as is, and change the IP address and username. sorry it does look like an expandable variable doesn;t it. 

if I want to connect to the server 235of2.doas.net, logging into ssh with the username 'ishmael' I would use this commmand exactly:
```

vncviewer -via ishmael@235of2.doas.net localhost:0

``` 

if we discect this command, we are running VNCviewer and using the -via command to indicate that we are goign to tunnel over ssh.
'ishmael@235of2.doas.net' is the info we need to connect and login to ssh.
'localhost:0' is the vnc service location relative to the ssh server. since we have ssh'ed into the server, and from the servers perspective, the vnc service exists on localhost, we can just use that. does that make sense?

your telnet error indicates that you do not have telnet installed. no biggie. telnet can be used to test if a port is open for communication. if you want, you can install it and run the command again.

never heard of those protocols. if they work, then you may want to use them. is there functionality you can't obtain from them?

---

### Post by oneiric on 2009-05-29
localhost does look like a variable :)  but when I left it in, vncviewer command worked, and presumably this connection is pretty safe because it is encrypted. Running  

```
vncviewer -via user@5.x.x.x localhost:0 
```

is actually easier than to use the Applications>Internet>Remote Desktop Viewer. 

Another thing is that I had to sudo apt-get install 'x11vnc' and run 'x11vnc' on the host computer (i'm sure thats obvious to most people, but until I did that I was getting the error, connection refused, VNC server closed connection).  So it turns out that hamachi networks are ok for linux to linux remote desktop, saving me from web-based remote desktop.

---

### Post by tictac232434 on 2009-08-03
If you wanted to control the other computer over the "Internet" why don't you just use Logmein. It gives you complete control over another PC for tech support and other things. You can even send files and stuff if you don't feel like uploading such things. Its your call just saying it might be easier because it is universal and works on every OS from my knowledge. Plus best of all if you get the commercial license its completely free!

Logmein: [https://secure.logmein.com/home.asp?hp=5]("https://secure.logmein.com/home.asp?hp=5")

---


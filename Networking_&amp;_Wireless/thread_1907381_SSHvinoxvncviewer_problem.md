---
title: "SSH/vino/xvncviewer problem"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by Warthaug on 2012-01-11
I am trying to setup an ssh/VNC access to a computer running lubuntu, using the following instructions:

[https://wiki.edubuntu.org/Lubuntu/RemoteDesktop](https://wiki.edubuntu.org/Lubuntu/RemoteDesktop)

It almost works, but seems to fail at the last stage.  On the lubuntu system I installed SSH and vino, and then configured vino to accept incoming connections with a password.  I can connect via ssh to the localhost, and I have confirmed that the SSH port (#22) is open to the outside on our network.  This is a work network, and I confirmed with IT that the SSH ports are open to internal and external traffic.

I then added xtightvncviewer to my ubuntu laptop, and opened two terminals.  In the first terminal I established an ssh connection using the command (where UID and 1.2.3.4 were replaced with the appropriate user name and IP):
```
ssh -L 12345:localhost:5900 uid@1.2.3.4
```
The connection worked, and I get terminal access to the host.  This access seems to be flawless, as I can run any command I wish through the terminal, including installing/removing software.

At this point I switch to the second terminal and try to start xvncviewer with the following command:
```
xvncviewer localhost:12345 &
```
When I try this the connection fails - on the "host" terminal I get the message "[1] 30143", followed on the next line by "xvncviewer: VNC server closed connection" (note: the value of 30143 increases with repeated attempts).  On the remote/ssh terminal I get the message "channel 3: open failed: connect failed: Connection refused".  Removing the ambersand from the command doesn't change the issue.

Anyone know why this fails?

Thanx

Bryan

---

### Post by woodyg on 2012-01-11
Earlier today I have been doing exactly what you are describing, following the same instructions, and I had the same problem. When looking more closely at the terminal output (after ssh -L 12345:localhost:5900 you@1.2.3.4), I noticed that it wanted a reboot. So I rebooted the remote machine, and after that the problem you described was gone.

Instead I got stuck on the very last step. Typing in

```
vncviewer localhost:12345 &
```leads to the following output

```
[1] 12907
user@mycomputer:~$ Connected to RFB server, using protocol version 3.7
Performing standard VNC authentication
```and it gets stuck there. Nothing else happens. What is going on?

---

### Post by Warthaug on 2012-01-12
Turns out mine is not working as the ports I was trying to connect via are blocked on our network.

Oh well...

Bryan

---

### Post by woodyg on 2012-01-13
> **Warthaug said:**
> Turns out mine is not working as the ports I was trying to connect via are blocked on our network.

Oh well...

Bryan

You couldn't get around it?

---

### Post by liquid_legs on 2012-01-13
> woodyg

vncviewer localhost:12345 &

im not exaclty sure why you put in the numbers 1-5 and then the & symbol unless youre trying to connect to multiplal users at once, but it seems to just work for me if i want to connect to myself using this code

vncviewer localhost:1

---

### Post by woodyg on 2012-01-14
> **liquid_legs said:**
> im not exaclty sure why you put in the numbers 1-5 

I don't know much about these things, so I just followed the instructions, which stated

> 
 The "12345" can be any number you like that is over 1024 and under 65536, as long as that port is not in use on the machine you are typing at.  The number 12345 works fine, and is easy to remember Removing the & symbol did the trick however... now it works.:p Thanks!

---


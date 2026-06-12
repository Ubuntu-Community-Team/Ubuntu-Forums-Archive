---
title: "Remote control ubuntu from vista"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by ingvald on 2009-01-29
People says it is so easy to do remote control but I can't get it to work. I want to remote control (with GUI) my ubuntu 8.10 from my laptop with vista home premium OS installed. I have followed this guide: [http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html)

Basically I have done the following steps:

- ticked the box next to the following two options
Allow other users to view your desktop 
Allow other users to control your desktop 
- ticked the box next to the following two options
Ask you for confirmation 
Require the user to enter this password
- under advanced I have chosen "Only allow local connections", required enqryption, locked screen on disconnect and "only display an icon when there is someone connected".

Thats all I have done in my Ubuntu. I have a network that works with ubuntu (that is sharing out files on my network) and vista pc's, i can access ubuntu folders (both read and write options) from my windows PC's, so the network is okay. 

I have not done anything more that includes installation of VNC or something like that. Have not installed any programs other than default from ubuntu installation and "automatic upgrade/downloads"

In windows, to remote control my ubuntu, I have installed tightvnc. I use tightvnc viewer on my vista laptop. I have not changed anyone of the default setup. When I enter the ubuntu laptop IP adress in the VNC server field and press connect I get the error message that it can't connect.....

What is wrong here.
Appreciate some help. Thanks in advance.

---

### Post by cariboo on 2009-01-29
I just checked controlling ubuntu from windows, and it works fine using vncviewer for Windows. I would suggest starting with a basic setup, to make sure you can connect, no passwords or confirmation, then once you can connect setup security.

Setup a good strong password as vnc is one of the most common ways for a cracker to break into your system.

Jim

---

### Post by jryprt on 2009-01-29
I just did this 1 hour ago here are some links i used 1 is a youtube video its easy
[http://www.youtube.com/watch?v=wmyKBWe_d_0](http://www.youtube.com/watch?v=wmyKBWe_d_0)
& i used ultra vnc is free
[http://www.uvnc.com/](http://www.uvnc.com/)

[http://answers.yahoo.com/question/index?qid=20081206170015AA1DzJ4](http://answers.yahoo.com/question/index?qid=20081206170015AA1DzJ4)
if you need help ask me

---

### Post by ingvald on 2009-01-31
Thanks for your answers. I did as one of these links said, unchecked all under advanced settings in ubuntu remote control. Now I got one step further. TIghtVnc viewer on vista asked me for my password but I still doesn't make to do the remote control. It hangs on Connection to "IP adress...XXX" , Status : Client initialization message sent. This message stands for hours, and I dont get any further. 

Tigthvnc viewer is allowed on my windows firewall.

Any suggestions?

When I get this to work I also have to do something about the advanced settings.....if you cannot check the encryption and "only allow local network" box the security is not very good.....Anyone that managed to do the remote control only for local network and encrypted?

---

### Post by Another Monkey on 2009-01-31
I don't use Vista, but I do use XPsp3.  The only "extra" bit I had to do was allow port 3389 for my LAN in Firestarter (a Gnome iptables GUI), e.g. allowed 3389 for 192.168.0.0/24

I just used bog-standard Windows Remote Desktop.

---

### Post by graysky on 2009-01-31
Firstly, I don't know anything about vino (the default desktop sharing on gnome/ubuntu).  For example, does it still use port 5900 with the 'encrypt connections' checked?  Further, does the windows tightvnc client support this connection encryption?  This might be the problem with connections that the op is experiencing.

I use [vnc4server](http://knoppmyth.net/phpBB2/viewtopic.php?t=19428) which allows me to have totally parallel vnc sessions.

Vnc uses port 5900 by default.  3389 is the windows rdp port.  Since he's using vnc on the LINUX side, I would say make sure your LINUX box will allow comms to 5900.

@op - if you're planning to vnc from INSIDE your own LAN and your LAN is not wireless, there is no need to worry about encryption.  If however you plan to vnc to your LINUX box from outside your own LAN, or if your own LAN is wireless, you should NOT use VNC without [tunneling it via ssh](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211).

---

### Post by ingvald on 2009-02-01
Sorry for all my questions, but I need to understand more before I try this. I just realized that it's more to think of than I originally thougth, and that my linux experience is too short.....
Hope that someone have the answers:-)

"does it still use port 5900 with the 'encrypt connections' checked?"
Yes, however, I unchecked this in my troubleshooting.




"I would say make sure your LINUX box will allow comms to 5900."

How do I make sure of that? I don't even know if I have a firewall on my ubuntu 8.10.....default installation, havn't configured except samba for connection to windows pc's. 




"@op - if you're planning to vnc from INSIDE your own LAN and your LAN is not wireless, there is no need to worry about encryption. If however you plan to vnc to your LINUX box from outside your own LAN, or if your own LAN is wireless, you should NOT use VNC without tunneling it via ssh."

My LAN is wireless. So I will follow your guide tunneling it via ssh.
But I don't really understand. After reading guide for tunneling it visa ssh: should I uninstall tightvnc on my windows pc's and instead install PUtty? 
What does the guide mean with "I'm assuming you have ssh setup and working on your mythtv box".How to ensure that? 




"Also, if your windows machine is outside your LAN, you'll obviously need to have the port that you've used for ssh (default is 22) forwarded to the IP addy of your LINUX box so that ssh is freely open to the outside world."
I need to do remote control wireless, so then I guess I need to do the port forwarding. I dont understand what is meant with "IP addy", but should I forward like this: Port from 22 To Port 22 Protocol: TCP & UCP, IP adress: IP to my LINUX Box?

---

### Post by graysky on 2009-02-01
> **ingvald said:**
> "does it still use port 5900 with the 'encrypt connections' checked?"  Yes, however, I unchecked this in my troubleshooting.

OK, keep it simple at first, then go back and add encryption once you get vnc working.

> **ingvald said:**
> ]"I would say make sure your LINUX box will allow comms to 5900."

How do I make sure of that? I don't even know if I have a firewall on my ubuntu 8.10.....default installation, havn't configured except samba for connection to windows pc's. 

8.10 does come w/ a firewall ([ufw](https://wiki.ubuntu.com/UbuntuFirewall), but by default it's disabled.  Verify this by the following command:

```
$ sudo ufw status
Status: not loaded
```

I don't know anything about vista.  Are you running a firewall on vista that would block connections from your client?

> **ingvald said:**
> My LAN is wireless. So I will follow your guide tunneling it via ssh.  But I don't really understand. After reading guide for tunneling it visa ssh: should I uninstall tightvnc on my windows pc's and instead install PUtty?

What does the guide mean with "I'm assuming you have ssh setup and working on your mythtv box".How to ensure that?

"Also, if your windows machine is outside your LAN, you'll obviously need to have the port that you've used for ssh (default is 22) forwarded to the IP addy of your LINUX box so that ssh is freely open to the outside world."

I need to do remote control wireless, so then I guess I need to do the port forwarding. I dont understand what is meant with "IP addy", but should I forward like this: Port from 22 To Port 22 Protocol: TCP & UCP, IP adress: IP to my LINUX Box?

No, you need both.  PuTTY is just serving as the means to encrypt the connection.  

As to the rest of your questions about using PuTTY for the ssh tunneling vnc, please post them over in [the original thread at knoppmyth.net](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211).  I ask that you do this because many folks trying Knoppmyth (soon to be renamed LinHES for _LIN_UX _H_ome _E_ntertainment _S_ystem) for the first time have ZERO experience running LINUX and will likely have the same questions as you and the KM community can benefit from my replies.  Registration is free of course.

I would recommend that for now you simply attempt to get unencrypted vnc to work and then add the encryption layer.  Did you install vnc4server yet?

---

### Post by ingvald on 2009-02-02
Ok, I got the vnc to work. I kept it simple and connected successfully. Howerver, when I used encryption connection tightvnc viewer informs that it's not supporting the encryption form..or something like that, just as graysky said.  

I just realized that using Putty only gives me remote control in terminal mode of my Ubuntu. What I am looking for is a GUI remote control, as I sit in front of my ubuntu laptop, and a secure remote control.Are the posts by graysky still relevant then? Other suggestions?

---

### Post by graysky on 2009-02-02
> **ingvald said:**
> Ok, I got the vnc to work. I kept it simple and connected successfully. Howerver, when I used encryption connection tightvnc viewer informs that it's not supporting the encryption form..or something like that, just as graysky said.  

I just realized that using Putty only gives me remote control in terminal mode of my Ubuntu. What I am looking for is a GUI remote control, as I sit in front of my ubuntu laptop, and a secure remote control.Are the posts by graysky still relevant then? Other suggestions?

Glad to hear you got the connection.  PuTTY is doing more than a shell ("terminal mode" as you put it).  When configured correctly, it is tunneling your vnc connection through an encrypted tunnel.  Trust me, this is how you want to do it with your LAN setup.

Everything I said in my post is relevant :)

> **graysky said:**
> As to the rest of your questions about using PuTTY for the ssh tunneling vnc, please post them over in [the original thread at knoppmyth.net](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211).  I ask that you do this because many folks trying Knoppmyth for the first time have ZERO experience running LINUX and will likely have the same questions as you and the KM community can benefit from my replies.  Registration is free of course

---

### Post by ingvald on 2009-02-05
Thank you graysky for your response. There must be something wrong with the [http://knoppmyth.net/phpBB2/profile.php](http://knoppmyth.net/phpBB2/profile.php), for some reason I can not register. They say my email adress is banned. I have neven been on that site. I checked with register a new gmail adress, and it got banned too..... ok...will try some more to get it to work:-)

---

### Post by graysky on 2009-02-05
> **ingvald said:**
> Thank you graysky for your response. There must be something wrong with the [http://knoppmyth.net/phpBB2/profile.php](http://knoppmyth.net/phpBB2/profile.php), for some reason I can not register. They say my email adress is banned. I have neven been on that site. I checked with register a new gmail adress, and it got banned too..... ok...will try some more to get it to work:-)

Dunno what to say... I'm not aware that they're banning any domain at all.

---


---
title: "Remote access over WLAN - vnc too slow"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by tushar_t on 2009-09-03
Hi, I've got a few questions regarding some basic networking configurations. Let me first explain my current setup: 

1) I've got a Desktop and a Netbook between which I want to do my networking (both of them have Ubuntu installed).
2) They both connect independently to the Internet using a modem/router.
3) The subnet IPs of the 2 PCs are 10.1.1.2 and 10.1.1.3

So my questions are: 

1) If both of them are connected to the internet, does that mean they're automatically  part of the WLAN? Or do I have create a separate wireless LAN and explicitly include them in it? I'm a bit confused because if I execute this command from the terminal in the Netbook:-
```
ssh username@desktop-name
```I can't connect to the desktop. But if I do this:
```
ssh [EMAIL="username@10.1.1.2"]username@10.1.1.2[/EMAIL]
```where 10.1.1.2 is the desktop's IP address, then it works just fine.

2) The more important questions are, firstly, what does VNC viewer depend upon? Does it depend upon just the connection speed or the CPU and GPU as well? Because after installing xtightvncviewer on my netbook, I find that the updates that are made on the Desktop screen take ages to be reflected on the netbook screen. Can I actually make it usable by somehow reducing the graphic detail that is sent across to the netbook?

Secondly, is there a way to remotely run applications using SSH within the terminal (i.e. CLI)? For example, could I play a .avi file in VLC media player on my desktop while sending commands to it using SSH from my netbook? If I can manage to run a few desktop applications remotely from the netbook using command prompt, then I won't bother with the VNC viewer.

---

### Post by i.r.id10t on 2009-09-03
You can put the IP of the other machine and its name in /etc/hosts

10.1.1.2  desktop-home

So you can then do ssh username@desktop-home and it will connect

You can forward X over SSH as well -

ssh -CY username@othermachine 

Once you log in and get a prompt, you just need to launch an application. 

If the GDM packages in Jaunty ever get fixed, you could do XDMCP and get a full desktop as well... 

Either method of remote gui works fine on my very old very slow 802.11b connection at the house...

---

### Post by tushar_t on 2009-09-03
Thank you for your reply. 

> **i.r.id10t said:**
> You can put the IP of the other machine and its name in /etc/hosts

10.1.1.2  desktop-home

So you can then do ssh username@desktop-home and it will connect

Excellent. Is there a command to check what other IP addresses within the subnet are part of the LAN?

> **i.r.id10t said:**
> 
You can forward X over SSH as well -

ssh -CY username@othermachine 

Once you log in and get a prompt, you just need to launch an application. 

When I do that, and execute this command for example:
```
vlc somefile.avi
```It runs the media player on my local machine, not the remote desktop I want it to run on. I'd like the local machine to remain in command prompt, but the desktop which I'm remotely controlling to open up the media player.

> 
If the GDM packages in Jaunty ever get fixed, you could do XDMCP and get a full desktop as well... 

Either method of remote gui works fine on my very old very slow 802.11b connection at the house...Apologies, but I'm very new to both Ubuntu and Networking in general. If GDM packages do get fixed, will XDMCP provide an improvement over a VNC session? 

I just can't understand why VNC viewer won't work smoothly and why the screen updates back on my netbook are so slow. It's not even a common problem either, I've tried some google searches but nothing really helps.

---

### Post by AliTabuger7 on 2009-09-03
I'm not entirely sure what the command is, but you should be able to choose which machine the window shows on with something LIKE
DISPLAY=othermachine:0 vlc file.avi

---

### Post by tushar_t on 2009-09-04
> **AliTabuger7 said:**
> I'm not entirely sure what the command is, but you should be able to choose which machine the window shows on with something LIKE
DISPLAY=othermachine:0 vlc file.avi
Hmmm I'll try that. So this should let me launch applications on the remote desktop right?

Also I just read somewhere that I need to enable portforwarding to port 22. I haven't done that. Could that be one reason that VNC is so slow?

---


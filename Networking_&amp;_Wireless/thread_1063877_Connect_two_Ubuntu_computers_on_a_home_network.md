---
title: "Connect two Ubuntu computers on a home network"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by greenco on 2009-02-08
How do I setup two Ubuntu 8.04 computers, on my home network?

Here is my situation:

1 .. I have a PC running Ubuntu 8.04, as the operating system. This PC does not have "Windows" installed. The PC connects to the internet via a high speed modem (COMCAST) and it is working great.

2 .. I have a laptop running Ubuntu 8.04, as the operating system. The laptop does not have "Windows" installed. The laptop's wireless card connects to the COMCAST modem via a "Wireless" router and it is working great.

I can access and surf the internet, with both computers. 

How do I setup the network so that I can see both computers? I want to be able to share (copy & paste) files between them. I would also like to use the PC's printer to print from my laptop.

I did a search and found lots of posts about connecting a Ubuntu system to a Windows system. 

I can't imagine that this should be this difficult!!!

Thanks

---

### Post by FishRCynic on 2009-02-08
samba or nfs?

if you want to browse with samba (ie windows protcol) 
make one the wins server

[http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/](http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/)

and the other a wins client

this will solve a plethora of samba networking issues

if nfs

just install via synaptic on both machines (client and server)
and it should work "out of the box)

---

### Post by greenco on 2009-02-08
I DO NOT have windows installed, on either computer, so will "Samba" work for me?

There are several "NFS" packages in Synaptic, so which ones do I need to install on and on which computer?
Thanks

---

### Post by FishRCynic on 2009-02-08
drawbacks to each protocol
see
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

for client and server pick
nfs-kernel-server

should add
nfs-common etc

which will give you nfs client and server 

(if you want windows machines to connect in the future i would use samba)

---

### Post by greenco on 2009-02-08
I will not be connecting to any Windows systems, so I don't need Samba. I installed the nfs server files, using Synaptic, but I can not see or connect the computers. Is there another step I need to do? Do I need to use a Terminal command, to mount them or can I do it another way? These two computers will be the only ones on this network.
Thanks

---

### Post by superprash2003 on 2009-02-08
samba can be used even if its a linux only network..

---

### Post by FishRCynic on 2009-02-08
should have sent you here, sorry

[http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64](http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64)

---

### Post by greenco on 2009-02-08
Thanks for your help, but I think it will be easier to copy the files to a rewritable cd and do what I need to do from there. I hate to give up, but I don't know if it is worth all the hassel. I just have not been able to get it setup. I was hoping that when I selected "System/Administration/Networks" I would be given an option to select the network I wanted to connect to. 
Thanks again for all of your help!!

---

### Post by FishRCynic on 2009-02-08
sorry its not working for you

its a pain - but in fact i have had issues with xp home, xp pro not connecting properly without the other computers booted up - but with the
wins server running peer-to-peer allocations just work properly now.
orry 

would be nice if there was something similar to xp network setup (not that it ever worked for me) where it would put the various configs on the usb key or floppy disk and you just put it in the various machines - might give me something to think about
'

---

### Post by greenco on 2009-02-08
I just found a way to share the files. I installed the "SSH" package and used this URL to set it up.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Now I will work on setting up a network printer.

Thanks again!!

---


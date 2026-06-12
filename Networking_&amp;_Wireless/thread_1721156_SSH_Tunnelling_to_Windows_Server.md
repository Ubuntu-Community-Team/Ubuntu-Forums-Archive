---
title: "SSH Tunnelling to Windows Server"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by ubundom on 2011-04-04
I need a little help with replicating my Ubuntu Linux Client SSH tunnelling setup (where I am using the standard tools: ssh and mount) into an equivalent Windows 7 Client using PuTTy.exe or Plink.exe (which are available from [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")). I have followed Mike Chirico's excellent tutorial religiously and with success for my Linux Client PCs. Look at [http://souptonuts.sourceforge.net/sshtips.htm]("http://souptonuts.sourceforge.net/sshtips.htm"). (Thanks, Mike!)

[SIZE="2"]_Network Diagram_[/SIZE]
[IMG]http://souptonuts.sourceforge.net/networkl.png[/IMG]

[SIZE="2"]_Linux works fine_
[/SIZE]I can securely tunnel from my Local-Linux box to mount a Samba ShareName which is located behind the firewall on the WindowsServer at 192.168.0.66

*SSH Tunnel*
[FONT="Courier New"]$ sudo ssh -2 -q -f -N -g -L 445:192.168.0.66:445 user@66.35.250.203[/FONT]

*Mounting Shares*
[FONT="Courier New"]$ sudo smbmount \\192.168.0.66:\ShareName /home/user/ShareName -o credentials=/home/user/.creds,uid=1000,gid=1000,umask=000,ip=127.0.0.1[/FONT]

*Notes*
[COLOR="DimGray"]stop smbd[/COLOR]
On the Laptop Linux I must first:

[FONT="Courier New"]$ sudo stop smbd[/FONT]

... otherwise {it|something} will not allow me to mount ShareName and I receive mount.cifs errors a-plenty!

[COLOR="DimGray"]Authentication[/COLOR]
The credentials for the Windows server are stored in a file [FONT="Courier New"]/home/usr/.creds[/FONT] that contains:

[FONT="Courier New"]username=user
password=secret[/FONT]

[SIZE="2"]_Windows 7: I need help!_
[/SIZE]Although this machine is not shown on Mike's diagram, suffice it to say that it performs the same function as the Linux Laptop: I am using it to connect to the Windows shares on the Windows server at 192.168.0.66. 

*Loopback Adapter*
I have set up a loopback adapter with address [FONT="Courier New"]10.0.0.1[/FONT] and installed PuTTy.exe and Plink.exe. Windows 7 perplexingly reports that I am not allowed one to enter a loopback address of 127.0.0.1 because it says they are "reserved for loopback addresses"!?!

*Login Success*
I can securely login to the remote Firewall-Linux box using the following PuTTy.exe configuration:

[FONT="Courier New"]Session Hostname: 66.35.250.230 Port: 22[/FONT]

*Tunnel*
I have tried various combinations of port forwardings using PuTTy.exe "Connection->SSH->Tunnels" 

[FONT="Courier New"]L 10.0.0.1:445 192.168.0.66:445
R 10.0.0.1:445 192.168.0.66:445
L 10.0.0.1:139 192.168.0.66:139
R 10.0.0.1:139 192.168.0.66:139[/FONT]

I am not sure how I check whether this is working properly yet.

*Map Drive Fails*
I have tried using the Windows Explorer "Tools->Map Network Drive" to map an arbitrary Windows drive Z: to

[FONT="Courier New"]\\10.0.0.1\ShareName
\\192.168.0.66\ShareName[/FONT]

and I ensure that I "Connect Using Different Credentials" e.g.: [FONT="Courier New"]username DOMAIN\user[/FONT] and the Windows password for 192.168.0.66 in /home/user/.creds (which of course, is different from the password that is used to connect to 66.35.250.203).

[SIZE="2"]_Ideas Please_[/SIZE]
Ideally I would like to use the PuTTY.exe GUI to set up the tunnel and the connection. But equally I am happy to set up a batch file to use command line [FONT="Courier New"]Plink.exe[/FONT] and/or [FONT="Courier New"]PuTTY.exe[/FONT] and the Windows native [FONT="Courier New"]net use[/FONT].

Cheers, fellow Ubuntu folk!

---

### Post by Doug S on 2011-04-05
I am only commenting on one small item from your posting:
>  
Windows 7 perplexingly reports that I am not allowed one to enter a loopback address of 127.0.0.1 because it says they are "reserved for loopback addresses"!?!

When I have used SSH tunnelling with PuTTY, it has been on a windows Vista box. I do have access to a Windows 7 computer, so I tried it there. I was able to set up an SSH tunnel between 127.0.0.1:12345 on my Ubuntu server box and 127.0.0.1:12346 on the windows 7 box without any issues. I realize that this is of little help for your problem, but thought I would mention it anyway.

---

### Post by Doug S on 2011-04-05
For this line:
[FONT=Courier New]> [FONT=Courier New]Session Hostname: 66.35.250.230 Port: 22[/FONT]
[/FONT]
I think you meant to say this:
> 
[FONT=Courier New][FONT=Courier New]Session Hostname: 66.35.250.203 Port: 22[/FONT]
 
[/FONT][FONT=Courier New]
While probably still of little use to you, I went a little further. I have an old old Ubuntu server (6.06) box at 192.168.111.140 on my network. My main new Ubuntu server (10.10) is at 192.168.111.1. So, I tried to create a SSH tunnel from my vista windows computer to my old box web server via my PuTTY session between my vista box and my new server. It worked fine and I was able to access the web pages via [http://127.0.0.1/](http://127.0.0.1/) . In the PuTTY SSH-tunnels window I had added source port 80, destination 192.168.111.140:80, local button and IPv4 selected. (I might edit in a screen shot later, if I can figure out how (seems I have to post it on a web page first)).
 
[IMG]http://www.smythies.com/~doug/network/temp/ssh_tun1.png[/IMG]
 
For this part of your posting:
> I have tried using the Windows Explorer "Tools->Map Network Drive" to map an arbitrary Windows drive Z: to
[FONT=Courier New][\\10.0.0.1\ShareName]("file://10.0.0.1/ShareName")[/FONT]
[FONT=Courier New]\\192.168.0.66\ShareName[/FONT]

At that level, your windows 7 box wouldn't know about 192.168.0.66.
[/FONT]

---

### Post by Doug S on 2011-04-07
I read the notes about sshtips at the link provided in the original post. My old old untuntu box does not have samba, but my new box does. I thought to try to make a PuTTY SSH session between my windows vista box and the old old ubuntu server box and then forward the ports to the new ubuntu server box and then try to connect to a share via 10.0.0.1. My thinking was if I would get it to work to then try with the Windows 7 box and then try to connect to another windows file server box ( it is an old XP box, actually ) . Anyway it did not work. I tried lots of things. I even had a wireshark session monitoring the 10.0.0.1 loopback device and another monitoring the new ubuntu server box looking for forwarded packets. There were never any forwarded packets. The 10.0.0.1 monitor showed tons of unexpected stuff to 10.0.0.255 and many other ip addresses, but it pretty much never showed anything like I might expect.
 
Well, O.K. as a sanity check, how about if I try to follow the instructions on the sshtips web page, that were written for windows XP, using the old windows xp box. That worked just fine. I could also see the forwarded packets on the wireshark session on the new Ubuntu server box, as expected.
 
My interest in this thread is purely educational. It took me this long to catch up to what the original poster, ubundom, already knew.
 
Edit: I have decided that the ability to do this is a potential security problem on my network. I have disabled forwarding in sshd_config, and disabled ssh access for other users. Sometimes I use forwarding to feed realtime tcpdump data from my Ubuntu server to wireshark running on another computer. I will enable forwarding as needed for that application. Sometime in the future, and maybe with further input from this thread, I will decide what I will do for a long term solution.

---

### Post by ubundom on 2011-04-28
> **Doug S said:**
> 
My interest in this thread is purely educational. It took me this long to catch up to what the original poster, ubundom, already knew.

Thanks for taking an interest. It is so odd and perplexing; I have a new (Lenovo T510) Win7 box that cannot do the obvious and easy task of connecting via SSH to a Windows server. The bloaty and cumbersome Cisco VPN application works fine. I have never gone down as low-level as to use Wireshark etc.

PS: Of course what I would really rather do is run Linux as host on the bare metal and have Win7 running as a guest in VirtualBox. (I do this on my old Dell D810 with WinXP as guest) but it is so tough to get around all the gotchas about the Recovery partitions etc etc. Oh well ...

---

### Post by ubundom on 2011-05-17
SOLVED in [http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html](http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html).

All thanks to Jan Just! What a :KS

---


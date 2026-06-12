---
title: "Trouble using Sonicwall NetExtender SSL-VPN client"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by AMat on 2009-08-22
Briefly as I can... I use the Sonicwall NetExtender client to do my work from home. I am not using a firewall on my machine but I might be behind one on my landlord's router.

I installed netExtender-3.0.597 and had it running properly on Jaunty for a couple of months before I did a complete re-installation of ubuntu to rid myself of a bunch of Windows partitions. 

I now have trouble with my new installation of netExtender. After connection to the server is established and my Login is accepted, I get the following feedback in my terminal...

```

Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
kill: No such process
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
Connection interrupted.  Reconnecting...
```

and then my password is invalidated and I have to try again, with the same result.

I seem to remember this happening once in the past, but I have no idea how I fixed it. Does anyone know what is happening, and how to remedy the problem?

This might be useful: 

When I installed netExtender the very first time after re-installing ubuntu, the installer warned me of a couple of dependency issues that it thought it could solve. It needed libssl.so.4 and libcrypto.so.4, which it said it could replace with libssl.so.0.9.8 and libcrypto.so.0.9.8 respectively. I confess, I only have a vague idea what these libraries are. This is the first time I found my connection terminated.

I then found that both libssl.so.4 and libcrypto.so.4 files were added to /usr/lib, which I thought was a good thing. I uninstalled the software and tried re-installing it again. As expected there were no dependency issues, but it still didn't work.

After a half-dozen installations/removals I am now in a situation where I do not have either libssl.so.4 or libcrypto.so.4 files in /usr/lib and yet I can install the software without dependency issues, and of course, it does not work.

I have tried installing a newer version of the software, for which I found an .rpm online, but it has other issues and does not even install without challenging my limited skills. The man page for netExtender is of little help to me but I learned that alien might not invoke the post-install scripts on the .rpm, but never mind that.

---

### Post by AMat on 2009-09-12
Solution: have to use root

---

### Post by chickenSandwich on 2010-05-04
Greetings,
   I have had a similiar set of problems, however, I have not been able to connect to the vpn.  I had the same depenecy quirks with libssl.so.0.9.8 and libcrypto.so.0.9.8 that AMat had, and created hard links:

cd /usr/lib
ln -s libcrypto.so.0.9.8 libcrypto.so.4
ln -s libssl.so.0.9.8 libssl.so.4

then I reinstalled net extender: NetExtender-3.5.632.tgz

I end up with the same result:

sudo netExtender

NetExtender for Linux - Version 3.5.632
Copyright (c) 2009 SonicWALL, Inc.

SSL-VPN Server: x.y.com
User Access Authentication
User: chickenSandwich
Password: 
Domain: xyz.com
Connecting to SSL-VPN Server "x.y.com:443". . .
Connected.
Logging in...
Login successful.
Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
Using new PPP frame encoding mechanism
(it waits here for about a minute)
SSL_read ZERO RETURN
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
Connection interrupted.  Reconnecting...
Connecting to SSL-VPN Server "x.y.com:443". . .
Connected.
Logging in...
Login successful.
Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
Using new PPP frame encoding mechanism
pppd: no device specified and stdin is not a tty

(...and it will continue again and again and again. )

I am running Ubuntu 10.04 LTS - the Lucid Lynx
- A side note:  This version of net extender was working for me in Ubuntu 9.1

I will try to solve this problem and post back here.  If anyone has any ideas, I would love to hear them.

---

### Post by mckinnon81 on 2010-05-05
> I am running Ubuntu 10.04 LTS - the Lucid Lynx
- A side note: This version of net extender was working for me in Ubuntu 9.1

I am having the same issues, if you find a solution would love to know as well.

Thanks

---

### Post by slowpoison on 2010-05-06
I was facing the same problem since upgrading to Lucid Lynx. I was able to fix it by upgrading to NetExtender.Linux.4.0.665. Download that one and you should be fine.

---

### Post by gkimovski on 2010-05-06
Hey slowpoison, Where did you get NetExtender.Linux.4.0.665?
The Download Center on MySonicWALL lists only 3.5.632 for Linux, i.e. the same version I get when going to the Virtual Office web. Googling for NetExtender 4.0 doesn't help eaither :-(

I ran into the same issue as you, chickenSandwich and mckinnon81 after upgrading to Ubuntu 10.4 ... though it was reconnecting from time to time it worked under Ubuntu 9.10

/Kima

---

### Post by chickenSandwich on 2010-05-06
Greetings,
   I would like to confirm slowpoison's solution.  I contacted my network administrator, and he gave me a copy of NetExtender-4.0.658.tgz.  I extracted it and ran the install:
sudo ./install

It allowed me to connect flawlessly.

I would suggest that you go to [https://www.mysonicwall.com/Login.asp](https://www.mysonicwall.com/Login.asp)
and download this version of the netextender.  You have to log in to get this version.

Thanks ya'll

---

### Post by gkimovski on 2010-05-07
Thanks chickenSandwich

when I tried the download centre on mysonicwall.com with my account I was offered only the 3.5 version ... I'll see if my network admin can get the 4.0 version

/Kima

---

### Post by aeplos on 2010-05-18
Hi, having same problem in fedora12, I would like try netextender 4, but I'm not able to find it in the above link.
Some body have another place where pic it or the way to have it from site? In the sonicwall site there are only the 3.5.632 version.
[chickenSandwich]("http://ubuntuforums.org/member.php?u=1063400"): perhaps you can place your file somewhere so we can try it.
Thank you

---

### Post by RPDH on 2010-05-25
Hi all,

Hope this helps clarify things. Because version 4 of the NetExtender client is still pre-release, Sonicwall have not made it available for download from the MySonicwall portal. 

I had to call Sonicwall support to get a copy of the clients (which involved being on hold for 60 minutes, with Enya filling my ears).  To save you all the pain, I have included the pre-release version 4.0.665 client (32 and 64bit) here. I stress that again...they are pre-release, so use with care.

Cheers,

---

### Post by walt_schmenge on 2010-05-31
> **RPDH said:**
> Hi all,

Hope this helps clarify things. Because version 4 of the NetExtender client is still pre-release, Sonicwall have not made it available for download from the MySonicwall portal. 

I had to call Sonicwall support to get a copy of the clients (which involved being on hold for 60 minutes, with Enya filling my ears).  To save you all the pain, I have included the pre-release version 4.0.665 client (32 and 64bit) here. I stress that again...they are pre-release, so use with care.

Cheers,
thanks for the files. worked for me! (after uninstalling netextender-3 and reinstalling netextender-4).

cheers.

---

### Post by Nullivex on 2010-06-06
Hello,

I was able to get around the issue by doing the following with the 3.x version.

```

nullivex@nullivex-laptop:~$ sudo su -
root@nullivex-laptop:~# /home/nullivex/netExtenderClient/netExtender
SUSE/Ubuntu compatibility mode on  
NetExtender for Linux - Version 3.0.581 
...

etExtender connected successfully. Type "Ctrl-c" to disconnect...

```Seems it does not like sudo in 10.04. Possibly a problem with sudo? Might have other regressions like this.

---

### Post by tcolvin03 on 2010-06-07
I am running a 64-bit installation.  I noticed that the netExtender executable is 32-bit which may explain why my installation's libraries don't work with it.

Does anyone know if there is a 64-bit version of netExtender available from SonicWall?

---

### Post by t_anjan on 2010-07-09
Try using this demo site from Sonicwall to get the latest version of NetExtender.

[https://sslvpn.demo.sonicwall.com/cgi-bin/welcome](https://sslvpn.demo.sonicwall.com/cgi-bin/welcome)

---

### Post by kwilson090507 on 2010-08-10
I believe the file [RPDH]("http://ubuntuforums.org/member.php?u=1082536") posted on page 1 has both the 32 and 64 bit version.

Extract the file, then run the install (bash install).
After install, type sudo netExtender  (the install says netExtenderGUI, but leave the GUI off)
Enter the parameters then you should log in.....at least I did.  This was the only version that's worked for me (Ubuntu 10.04)

---

### Post by James2k on 2010-09-14
I was having the same problem with the 3.5 netExtender client, I just installed the 4.0 release but it seems to crash, anyone else had this problem on Ubuntu 10.10 Lucid?

Edit: Finally got it to successfully connect, I just needed to reboot my machine.

---

### Post by rofu on 2010-09-17
Im using Ubuntu 10.04 and NetExtender 4.0.665 and the vpn-connection breaks when trying to commit a lot of files to subversion.

Password accepted
Using SSL Encryption Cipher 'AES256-SHA'
Using new PPP frame encoding mechanism
You now have access to the following 6 remote networks:
	0.0.0.0/0.0.0.0
	0.0.0.0/0.0.0.0
	128.0.0.0/128.0.0.0
	192.168.1.0/255.255.255.0
	169.254.0.0/255.255.0.0
	0.0.0.0/0.0.0.0
NetExtender connected successfully. Type "Ctrl-c" to disconnect...
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
Connection interrupted.  Reconnecting...

---

### Post by krackersk on 2010-10-04
Anybody have the final version for 64bit of version 4?

It installs fine but when it is connecting the pre-release version crashes.

I have the 32bit version running on a netbook and it works great but I need to get my main computer running 64bit version working.

---

### Post by carl.davis on 2010-11-16
> **krackersk said:**
> Anybody have the final version for 64bit of version 4?

It installs fine but when it is connecting the pre-release version crashes.

I have the 32bit version running on a netbook and it works great but I need to get my main computer running 64bit version working.

I just installed 4.0.671 64-bit and was able to get connected and pass traffic to the Sonicwall's local subnet. I am running Ubuntu 10.10.

---

### Post by bbdimitriu on 2010-11-19
Where did you manage to get the 4.0.671 64-bit version from? Would you be able to post a link?
Thanks

---

### Post by carl.davis on 2010-11-24
> **bbdimitriu said:**
> Where did you manage to get the 4.0.671 64-bit version from? Would you be able to post a link?
Thanks

I emailed SonicWall support and they provided me with a pre-release copy.

---

### Post by syedwasi on 2010-12-08
> **RPDH said:**
> Hi all,

Hope this helps clarify things. Because version 4 of the NetExtender client is still pre-release, Sonicwall have not made it available for download from the MySonicwall portal. 

I had to call Sonicwall support to get a copy of the clients (which involved being on hold for 60 minutes, with Enya filling my ears).  To save you all the pain, I have included the pre-release version 4.0.665 client (32 and 64bit) here. I stress that again...they are pre-release, so use with care.

Cheers,

Hello RPDH,

Thanks you very much for such a software ,it got started working on my ubuntu 10.10 ...can you pls let me know about compatiblity of this vpn 4.0 client for MAC OS.

regds
wasi

---

### Post by BalazsPH on 2011-03-05
Hi,

I have managed to install NetExtender on Ubuntu 10.10. I have all the log in details, to connect, and additionally there's a pre-shared key. Where can I add/enter this pre-shared key ?? I have tried in the System->Preferences-> Passwords and Encryption Keys,
but so far no luck.
Thanks

---

### Post by mck666666 on 2011-03-16
On Pardus linux I have solved theproblem with: 

sudo chmod 755 /etc/ppp/ip-up
sudo chmod 755 /etc/ppp/ip-down

You need:
libpcap and pppd

---

### Post by chickenSandwich on 2011-03-25
Hi there.  I just wanted to follow up on trying to use the Sonicwall Netextender v 4.0.665 on Ubuntu 10.10
I get frequently disconnected while working on the remote desktop connection.  It's really not of much use except to irritate me.  Just thought anyone interested might want to know.

---

### Post by 6tonspacefly on 2011-05-16
> **chickenSandwich said:**
> Hi there.  I just wanted to follow up on trying to use the Sonicwall Netextender v 4.0.665 on Ubuntu 10.10
I get frequently disconnected while working on the remote desktop connection.  It's really not of much use except to irritate me.  Just thought anyone interested might want to know.

Same here with 11.04

Sadly it doesn't give any more information than just:

SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client

For no reason.  Any way to get a more detailed output, like a -v switch?

---

### Post by Sidsmooth on 2011-05-26
I believe I found the solution for Netextender 4.0.665 disconnecting during RDP sessions. I am running 11.04 and was having constant disconnects thru Netextender. I found the following blog:

[http://jdbausch.blogspot.com/2010/04/default-java-implementation-on-ubuntu.html](http://jdbausch.blogspot.com/2010/04/default-java-implementation-on-ubuntu.html)

Apparently OpenJDK breaks the SSL Tunnels created by Netextender. I followed the steps in the blog to remove the OpenJDK then install Sun Java and my Netextender has worked flawlessly ever since.
:D

---

### Post by 6tonspacefly on 2011-06-10
> **Sidsmooth said:**
> I believe I found the solution for Netextender 4.0.665 disconnecting during RDP sessions. I am running 11.04 and was having constant disconnects thru Netextender. I found the following blog:

[http://jdbausch.blogspot.com/2010/04/default-java-implementation-on-ubuntu.html](http://jdbausch.blogspot.com/2010/04/default-java-implementation-on-ubuntu.html)

Apparently OpenJDK breaks the SSL Tunnels created by Netextender. I followed the steps in the blog to remove the OpenJDK then install Sun Java and my Netextender has worked flawlessly ever since.
:D

Fixed the problem.  Thank you so much for finding this.  My connection stays nice and strong the whole time.  Good call.

---

### Post by ajmatson on 2011-06-16
Same here. Have to have the correct Java version for the NetExtender to work properly. Just like waking up it's all about the Java :)

---

### Post by DrCR on 2012-12-29
It appears you can stay open, but only via the CLI route. Your call if that's a acceptable route to take.
> Prerequisites for Linux Clients:

Linux 32-bit or 64-bit clients are supported for NetExtender when running one of the following distributions (32-bit or 64-bit):
- Linux Fedora Core 15 or higher, Ubuntu 11.10 or higher, or OpenSUSE 10.3 or higher
- Java 1.5 and higher is required for using the NetExtender GUI.

The NetExtender client has been known to work on other distributions as well, but these are not officially supported.

Note: Open source Java Virtual Machines (VMs) are not currently supported. If you do not have Java 1.5 or higher, you can use the command-line interface version of NetExtender.

Source:
[http://help.mysonicwall.com/sw/eng/6390/ui2/6000/user_netExtender.html](http://help.mysonicwall.com/sw/eng/6390/ui2/6000/user_netExtender.html)

---


---
title: "[SOLVED] Copying or Moving files via a network"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Dr Zin on 2008-12-22
I want to move files form one computer to another. I know the command is going to be use are CP or MV. ```
$cp /home hostname /home
``` but one pc is static and the other is dynamic

---

### Post by tigerstripedcat on 2008-12-22
I'm not  sure what you mean by 'dynamic'.  You mean, it's not always hooked up to the network?

---

### Post by Dr Zin on 2008-12-22
every thing is on a network. the computer in question is get an ip form the DHCP server.

---

### Post by riseringseeker on 2008-12-22
> **Dr Zin said:**
> I want to move files form one computer to another. I know the command is going to be use are CP or MV. ```
$cp /home hostname /home
``` but one pc is static and the other is dynamic

A little more information would help.  Are both computers on a LAN, or are you trying via a WAN?  Do you want to move the file, or merely copy it?

If you're on a LAN, you can see what the IP is by using nmap.  It's not installed by default, but I'll assume you know how to install from the repos.  Then, the command to find what the current IP is would be ```
nmap -sP <IP range>
``` (i.e. nmap -sP 192.169.1.1-255)

If you're on a WAN, you haven't said what if any control you have over the dynamic machine.  If it's your machine, you might want to look into DynDNS, or something similar.  It will allow you to assign a name (such as drzin.homelinux.org) to the IP, and update it automatically once you get it set up. Then instead of using a set of numbers, you would just use the name.

If you merely wish to copy it, you should more likely use scp rather than cp, or you could also look into using rsync, a great little tool!

---

### Post by Dr Zin on 2008-12-22
Look i am on a lan I need to copy my /home to another computer that is on Lan. I have all the ips i need. I just need to understand the right command to do this.

---

### Post by Dr Zin on 2008-12-22
For get about the last post.

Ok I am On LAN and need to copy a directory form one PC to a another PC on the network. Like i said in the first post i just need a little help with command. I am not give out any info about my network. I have point A and i need to copy to point B. I have a basic idea what command i am going to use just needing some guidance. This for is for work so if i come off stressed its because i am a little stress.

---

### Post by Iowan on 2008-12-22
Linux-Linux?
Windows-Linux?

What kind of file-sharing is set up - Samba, NFS, SSHFS, FTP?  Depending on the file system, you should be able to mount the directory from Point A on Machine B.  Then it would be a matter of using the commands you mentioned. SSH and FTP have other options.

---

### Post by jonobr on 2008-12-22
For one time Ubuntu to ubuntu copy 
use secure copy

scp username@remoteIP:/home/directory .

scp = secure copy
username@remoteIP = go to the remote IP and supply username as username

:/home/directory  = go to the /home/directory directory

. = copy to the current directory on the host your scping from.



For frequent copies from one ubuntu to another, consider using samba,
or use rsync (cwrsync on a windows machine)

For the windows machine, you could install an ftp client or a winscp client and perform the copy that way,

however, as everyone else has stated , the machines and OS's you are using will determine what you can do and the programs you require.

What suits you best is your decision, however, you need to provide more detail, and when you do, dont be surprised to get a load of possibilities. This is due to Ubuntus )linux) flexibility.

---

### Post by Dr Zin on 2008-12-22
Thank you jonobr for clearing that up. Ok this what to work with. So I am using putty to SSH in the Computer that i am going to copy the directory form.  which is a ubuntu. now the computer that pasting it to is a Ubuntu. But I am useing a windows system to do the copying.


So I use putty to ssh into the computer that has the directory that I am going to copy form. once i am log in to the system I type```
$scp /home localhost@whatever.com: /home
```

I checked this with man page for SCP. so if this right then i am good to go. :confused:

---

### Post by jonobr on 2008-12-22
Eh gad, Dr Zin :-)

Just to clarify, you are copying using a windows box from one ubuntu to another,
but you are logged into the Ubuntu machine using windows / putty?

If thats the case then the windows piece is not relevant (but thanks for mentioning)

So the general syntax is (assuming you are logged using putty into ubuntu machine a) and want to copy from b,
and machine b is 10.10.10.10 and you have an user account on b with login name dr_zin

[I]
scp dr_zin@10.10.10.10:/home/directory_of_b /home/[/I]

in english and from left to right 

copy using username = dr_zin, at machine address 10.10.10.10 from the directory /home/directory_of_b and copy to the local machine , i.e. server a, to the /home directory.


This will work in either direction, but its easier if you wanted to copy in the other direction from a to b, where a = 10.10.10.11

login into b using putty
and assuming username is dr_zin 

[I]
scp dr_zin@10.10.10.11:/home/directory_of_b /home/[/I]

---

### Post by Dr Zin on 2008-12-22
ok i will give a good try then

---

### Post by jonobr on 2008-12-22
sure thing,

If you want to get your windows machine in on the act, you could install winscp which is a nice gui front end to scp and allows you to move files and folders around.


Also, if you wanted to use windows , you could try samba which allows your ubuntu boxes to access the windows box like a normal windows network share

---

### Post by andguent on 2008-12-22
I would completely agree with Jonobr, WinSCP is highly recommended for this type of setup. Samba is a good thing to have functioning as well, as it allows file copying in both directions via windows file sharing.

If you really do prefer command line scp on Windows, and you don't have it already, I would recommend installing OpenSSH for Windows from here: [http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

---

### Post by Dr Zin on 2008-12-24
**** it I am using gftp its working it. thank for all the help.

---

### Post by Dr Zin on 2008-12-26
well gFTP crashed and we are going witha better plain at his piont. So agian thank guys for your help.

---


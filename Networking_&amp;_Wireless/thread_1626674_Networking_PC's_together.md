---
title: "Networking PC's together??"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2010-11-20
I am having a heck of a time trying to find directions on networking my two computers together in order to share files.  I have two machines running Ubuntu 10.10 Desktop & Netbook remix.  


They are both connected to my wireless router to connect to the internet.

Please help
:popcorn:


Edited to focus on the Ubuntu machines

---

### Post by Atomic Fusion on 2010-11-20
What do you mean by "networking"? I'm assuming you mean file sharing, but is it centralized? Do you want two of them to connect to the other one, or all to be able to connect to all?

---

### Post by spiky001 on 2010-11-20
You might wanna look into ssh

---

### Post by Sxynerd on 2010-11-20
> **Atomic Fusion said:**
> What do you mean by "networking"? I'm assuming you mean file sharing, but is it centralized? Do you want two of them to connect to the other one, or all to be able to connect to all?

I would like all of them to be able to share files with each other.  The most important connection right now is the two Ubuntu machines.

> **spiky001 said:**
> You might wanna look into ssh
What is ssh?

---

### Post by garvinrick4 on 2010-11-20
I use Windows Workgroup in 7 and Vista and Samba in Linux installs, have to have a password
to login with in Windows or Workgroup does not take. Have Vista, 7, WUBI 9.10, 10.04, 10.10, Fedora 14 and 11.04 and will show in network and can share whatever I need in all installs. The printer shows up under Windows workgroup installing printer which is a USB connection in Vista, WUBI  box and all installs including Fedora sees. Set up Workgroup in Vista first and then the Samba's. Matter of fact anymore I have Workgroup set up and the Ubuntu installs just work out of box to see the Windows Vista machine and printer but needed Samba to include the Ubuntu WUBI on Vista box.

---

### Post by spiky001 on 2010-11-20
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)  there are plenty on google as well

---

### Post by randumnumber on 2010-11-20
You need to hook them all up to a network first. though a router is the easies way. Then you need to install samba on the linux machines. samba allows them to share files with windows machines. there are lots of resources on this site in reference to how to setup and use samba.

edit:
AND as mentioned above you can use ssh and sftp to share files, this is usually done at command line, or sftp can be done though nautilus.

---

### Post by Atomic Fusion on 2010-11-20
SSH is excellent, but it won't work so well on Windows, however you said your concern was mainly Ubuntu.
Ubuntu comes with the SSH client, so to install the SSH server, go to Synaptic (System>Administration>Synaptic) and install the "ssh" package, or enter "sudo apt-get install ssh" in a terminal.
After you've done that on both Ubuntu machines, you SHOULD be able to on either one, go to Places>Connect to Server, set service type to SSH, and server to the name of the other Ubuntu machine, and press connect.
Unfortunately, I can't verify that the installation will go that smoothly.

---

### Post by Sxynerd on 2010-11-20
Lets just focus on the Ubuntu Machines.  [Edit Above]

I am a noob and have no idea what most of the terms you guys are throwing around.

Both the computers are connected to the internet by my wireless routers.

---

### Post by Sxynerd on 2010-11-20
> **Atomic Fusion said:**
> SSH is excellent, but it won't work so well on Windows, however you said your concern was mainly Ubuntu.
Ubuntu comes with the SSH client, so to install the SSH server, go to Synaptic (System>Administration>Synaptic) and install the "ssh" package, or enter "sudo apt-get install ssh" in a terminal.
After you've done that on both Ubuntu machines, you SHOULD be able to on either one, go to Places>Connect to Server, set service type to SSH, and server to the name of the other Ubuntu machine, and press connect.
Unfortunately, I can't verify that the installation will go that smoothly.

How do I find the name of my computers?  I have made it to "Typing in the Server name" but I don't know how to tell what the names of my computers are.

---

### Post by spiky001 on 2010-11-20
open a terminal Applications/terminal  username@pcname

if you type ```
ifconfig
``` it will give you the ip address of the machine

---

### Post by Atomic Fusion on 2010-11-20
To find the name of a computer, open a terminal (Applications>Accessories>Terminal), type "hostname" and press enter. Remember, you need to put that in the other computer. And you did install SSH on both, right?

---

### Post by Sxynerd on 2010-11-20
> **spiky001 said:**
> open a terminal Applications/terminal  username@pcname

This is what i get:
> michael@michael-desktop:~$ username@pcname
username@pcname: command not found
michael@michael-desktop:~$ 


---

### Post by spiky001 on 2010-11-20
"michael-desktop" name of pc

---

### Post by Hakunka-Matata on 2010-11-20
```
hostname
```

---

### Post by Atomic Fusion on 2010-11-20
> **Sxynerd said:**
> This is what i get:
What he meant was look at the terminal, and where it said
```

michael@michael-desktop:~$

```Take the part after the @ and before the :.
The format for that is USER@MACHINE:DIRECTORY$.

But in the end all you need to know is what your machine name is, and for that it's michael-desktop, as previously stated.

---

### Post by Sxynerd on 2010-11-20
I have installed SSH server on both.  

When I select "connect to server" I select "SSH" and then type in the other PC's name... 

 ..in both directions I receiver the error: [Cannot display location "Shtp://michael-desktop"] & [Cannot display location "Shtp://michael-1000H"]

---

### Post by spiky001 on 2010-11-20
Ok for now type in ssh username@ipaddress make sure it works then we can fix names after, when you ssh in from terminal 1st time it will ask you to save a key enter yes

---

### Post by Atomic Fusion on 2010-11-20
It says "shtp://"? Okay, open a folder and go to Bookmarks>Add Bookmark, and then go to Bookmarks>Edit Bookmarks. Edit you new bookmark so that the locations is "sftp://michael-desktop/" for the michael-1000H computer and "sftp://michael-michael-1000H/" for the michael-desktop computer. Then exit the edit bookmarks window, and in the sidebar, go to that bookmark (you may want to rename it).

---

### Post by Sxynerd on 2010-11-20
> **spiky001 said:**
> Ok for now type in ssh username@ipaddress make sure it works then we can fix names after, when you ssh in from terminal 1st time it will ask you to save a key enter yes

I don't understand.

> **Atomic Fusion said:**
> It says "shtp://"? Okay, open a folder and go to Bookmarks>Add Bookmark, and then go to Bookmarks>Edit Bookmarks. Edit you new bookmark so that the locations is "sftp://michael-desktop/" for the michael-1000H computer and "sftp://michael-michael-1000H/" for the michael-desktop computer. Then exit the edit bookmarks window, and in the sidebar, go to that bookmark (you may want to rename it).


I have done that.  When I click on the new "sftp" bookmark It says, > "Could not display "sftp://michael-michael-1000h/" Access was denied.

---

### Post by spiky001 on 2010-11-20
Ok have you ssh server installed on micheal-desktop?

---

### Post by Sxynerd on 2010-11-20
Yes, on both.  Was there something I was supposed to do with the IFconfig command?

---

### Post by spiky001 on 2010-11-20
yes it will tell you the ip address of micheal-desktop. Open a terminal type ```
ifconfig
``` it will give you a list of network info if you can copy paste it so we can see what we need

---

### Post by Sxynerd on 2010-11-20
Desktop
> michael@michael-desktop:~$ username@pcname
username@pcname: command not found
michael@michael-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:932676 (932.6 KB)  TX bytes:932676 (932.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:19:6d:51  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe19:6d51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:475377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:341337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:613355330 (613.3 MB)  TX bytes:33240743 (33.2 MB)
          Interrupt:18 Memory:ef8fc000-ef8fe000 



1000H to follow in edit:

> michael@michael-1000H:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:11:a9:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:25:07:8e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe25:78e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1665756 (1.6 MB)  TX bytes:35398 (35.3 KB)
          Interrupt:19 



---

### Post by spiky001 on 2010-11-20
ok just for your info your wireless connection is wlan0 so you can look up your ip "192.168.1.3 micheal-desktop".  open a terminal in the other machine type in ```
ssh michael@192.168.1.3
``` it will ask for a password of micheal-desktop type it in YOU WONT SEE WHAT YOU ARE TYPING but dont worry is going in, it will then ask you to save a key type yes terminal will now change to michael@micheal-desktop

---

### Post by Sxynerd on 2010-11-20
> **spiky001 said:**
> ok just for your info your wireless connection is wlan0 so you can look up your ip "192.168.1.3 micheal-desktop".  open a terminal in the other machine type in ```
ssh michael@192.168.1.3
``` it will ask for a password of micheal-desktop type it in YOU WONT SEE WHAT YOU ARE TYPING but dont worry is going in, it will then ask you to save a key type yes terminal will now change to michael@micheal-desktop

Done.

> michael@michael-1000H:~$ ssh michael@192.168.1.3
The authenticity of host '192.168.1.3 (192.168.1.3)' can't be established.
RSA key fingerprint is 55:aa:ce:29:7f:53:c7:32:91:e3:34:0d:f1:8d:59:6a.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.3' (RSA) to the list of known hosts.
michael@192.168.1.3's password: 
Linux michael-desktop 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

michael@michael-desktop:~$ 


Does it matter that "michael@" doesn't include the actual computers name?  

Should the opposite be "ssh michael@192.168.1.5".

---

### Post by spiky001 on 2010-11-20
you want to be on the pc that you want to view the other pc from so ssh username(of pc to be viewed)@ip of pc to be viewed. Just use ip at moment

---

### Post by Sxynerd on 2010-11-20
Ok, nothing is happening.  I can not connect to either one.  It still says cannot connect/access denied


I'm confused.



(Why can't it be as easy as windows networking?)

---

### Post by spiky001 on 2010-11-20
> michael@michael-1000H:~$ ssh michael@192.168.1.3
The authenticity of host '192.168.1.3 (192.168.1.3)' can't be established.
RSA key fingerprint is 55:aa:ce:29:7f:53:c7:32:91:e3:34:0d:f1:8d:59:6a.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.3' (RSA) to the list of known hosts.
michael@192.168.1.3's password: 
Linux michael-desktop 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

michael@michael-desktop:~$  			 		
From what you posted you were connected to micheal-desktop?

---

### Post by rabbit_fighter on 2010-11-20
This is something I am struggling with as well.  I have gone around in circles, looking through forum threads but haven't gotten anywhere.  I was running Linux Mint 9 KDE awhile back, and the pre-packaged Samba stuff seemed to work fine (all I had to do was share a folder through Dolphin and I could see it on the Windows XP laptop).

Now I am on Ubuntu 10.10 and I can't seem to get anything working.  If there is a simple step by step (that doesn't make big assumptions about prior knowledge), I'd love to see it.

---

### Post by Sxynerd on 2010-11-20
> **spiky001 said:**
> From what you posted you were connected to micheal-desktop?

It said access denied when I clicked the sftp bookmark I made and I could not see any files.

> **rabbit_fighter said:**
> This is something I am struggling with as well.  I have gone around in circles, looking through forum threads but haven't gotten anywhere.  I was running Linux Mint 9 KDE awhile back, and the pre-packaged Samba stuff seemed to work fine (all I had to do was share a folder through Dolphin and I could see it on the Windows XP laptop).

Now I am on Ubuntu 10.10 and I can't seem to get anything working.  If there is a simple step by step (that doesn't make big assumptions about prior knowledge), I'd love to see it.

I honestly have no idea how Ubuntu has been able to get as far as it has without having a better networking feature.  When I ran windows I could network all 5 of my PC's in minutes and have links to all drives waiting on my desktop.  This is really absurd.    *frustrated*

---

### Post by Hakunka-Matata on 2010-11-21
> **Sxynerd said:**
> It said access denied when I clicked the sftp bookmark I made and I could not see any files.



I honestly have no idea how Ubuntu has been able to get as far as it has without having a better networking feature.  When I ran windows I could network all 5 of my PC's in minutes and have links to all drives waiting on my desktop.  This is really absurd.    *frustrated*

Ubuntu & local file share browsing - Samba worked fine without too much tinkering prior to 10.04 (guessing @ release No.), maybe it was 9.10, but about that time major changes were made to Samba and sharing defaults.  A very informative thread ran on it, lots of complaints, still looking for it.  I do have Local share browsing working 'sort of' on my LAN with one windows XP Professional os, one ubuntu 9.04 i386 Desktop machine and an ubuntu 10.10 i386 Desktop machine.  I share a folder to start with (via file manager and right button share), if sharing isn't available, it prompts to install samba.  
     To reiterate, it did work smoothly prior to Release 10.04, I think that's where the changes and problems began.
     Sometimes I can browse directly to the shares using "Places > Network--Workgroup--etc" but using "Places > Connect to server > Windows share > Server ip address" has been the most reliable.  Some useful bash commands (for **Release 10.10**) on this topic:  ```
findsmb
``````
sudo restart smbd
``````
sudo status smbd
``````
sudo stop smbd
```

some links to look at: [http://ubuntuforums.org/showthread.php?t=1169149&highlight=network+browse]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=network+browse")
[http://www.jonathanmoeller.com/screed/?p=1590]("http://www.jonathanmoeller.com/screed/?p=1590")

Ubuntu is still a really great OS for me, i'll work through the Network file browsing issue, and let's hope the developers come to an agreement soon on how to handle the issue.

---

### Post by spiky001 on 2010-11-21
Sxynerd you will need to do a few more things yet we need to check that ssh is working

---

### Post by headvampyre@hotmail.co.uk on 2010-11-21
just a question... whats the point in using ssh for filesharing, its just a pain at the end of the day. you should try NFS or Samba (apt-get install samba smbclient smbfs libpam-smbpass acl) or for nautilus just use apt-get install nautilus-share . Samba will allow you to share files between windows, Mac OS and linux boxes easily. NFS is different and harder to get working on windonws and Mac OS, which is why i would recommend samba for doing this.

---


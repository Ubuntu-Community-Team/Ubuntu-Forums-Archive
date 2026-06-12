---
title: "Share: Windows cannot access \\ubuntu"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2011-12-12
In Ubuntu 11.10 (Unity) 
I create new folder (rename to shared) 
right click folder, click "Sharing Options"

enable sharing and allow others to create and delete files, and allow Guest access. 

it installs samba and sets everything up. The folder has a shared arrows icon applied to it. no error messages upon install of samba. 

--

In windows 7, I browse the network. Windows 7 sees the name of the machine in the network "Ubuntu" 

I double click "ubuntu" 

it takes about a minute and says "Windows cannot access \\ubuntu"

I checked the smb.conf and the workgroup name is "WORKGROUP" my windows workgroup name is "WORKGROUP" 

I added to the smb.conf "netbios name = ubuntu" 

then sudo /etc/init.d/samba restart
"/etc/init.d/samba: command not found" 

so I "sudo service smbd restart" 

smbd start/running, process 3965

then try accessing Ubuntu again from windows 7. again the same error. 

--
from within Ubuntu I browse the network, it says "windows network" i double click "Windows Network" it takes a minute before displaying nothing. An empty white folder, where there should be windows machines. 

in windows, if I create a folder and right click it and enable sharing, it is visible instantly to all other windows machines. 

is there a quick and painless way to share files across a windows/ubuntu network? if not, what is the not so quick and painless way to do this?

thanks!

---

### Post by RealityMaster on 2011-12-12
What security type are you using in smb.conf?  

Also the problem may be that you have MS running, formatting and installing Linux would fix it;-)  jk.

---

### Post by davethewave83 on 2011-12-12
> **RealityMaster said:**
> What security type are you using in smb.conf?  

Also the problem may be that you have MS running, formatting and installing Linux would fix it;-)  jk.

haha, no need to joke. I was thinking the same thing. Actually everything in the smb.conf is default, the way it comes in ubuntu 11.10 except that I've added the netbios name. So it's in user security

---

### Post by capscrew on 2011-12-12
> **davethewave83 said:**
> haha, no need to joke. I was thinking the same thing. Actually everything in the smb.conf is default, the way it comes in ubuntu 11.10 except that I've added the netbios name. So it's in user security

From the terminal, check to see if you have 2 *smbd * and 1 *nmbd *daemons running like this```
pgrep -l mbd
```

You should get a return similar to this ```
pgrep -l mbd
933 smbd
1152 smbd
1341 nmbd

```

---

### Post by davethewave83 on 2011-12-12
> **capscrew said:**
> From the terminal, check to see if you have 2 *smbd * and 1 *nmbd *daemons running like this```
pgrep -l mbd
```

You should get a return similar to this ```
pgrep -l mbd
933 smbd
1152 smbd
1341 nmbd

```

I get ```
2718 nmbd
4013 smbd
4015 smbd
4019 smbd
4021 smbd
4024 smbd
4028 smbd
4046 smbd
4051 smbd
4113 smbd
```

---

### Post by N00b-un-2 on 2011-12-12
name resolve order = bcast host lmhosts wins

---

### Post by davethewave83 on 2011-12-13
> **N00b-un-2 said:**
> name resolve order = bcast host lmhosts wins

I tried this. still having the issues. Maybe it is a Windows issue. Maybe something to do with the homegroup settings or something.

---

### Post by N00b-un-2 on 2011-12-13
I assumed you knew that.   Home group has to be disabled for Windows 7 to access normal network shares.  Disable it, make sure that your Windows PC is a member of the same work group as your Ubuntu computers and then reboot.  You should be able to access your samba shares.

---

### Post by davethewave83 on 2011-12-13
> **N00b-un-2 said:**
> I assumed you knew that.   Home group has to be disabled for Windows 7 to access normal network shares.  Disable it, make sure that your Windows PC is a member of the same work group as your Ubuntu computers and then reboot.  You should be able to access your samba shares.

it turns out it was already disabled.

---

### Post by N00b-un-2 on 2011-12-13
try opening up an explorer.exe window and manually browsing to the hostname of the computer you're trying to access, ie; *\\ubuntu*.  If you can do this from another linux machine with samba installed, then the issue is with windows.  If you can't do it from another linux machine with Samba, then the issue lies with your Ubuntu PC.

---

### Post by gordintoronto on 2011-12-13
This can also be caused by a setting in your router. Sorry, I don't have details.

---

### Post by davethewave83 on 2011-12-16
I don't think gnu/linux likes me. 

I decided to get rid of Windows on the windows machine and install Ubuntu 11.10 in it's place.So now I have no Windows machines. 

I have 3 PCs running ubuntu 11.10
when they were Windows they could share files and when two were ubuntu I could ssh from windows through putty to the two ubuntu machines, but now neither sharing nor ssh work on any of them.

Because windows was able to do these things, this rules out a router setting issue. 

on this fresh install of Ubuntu, when I create a new folder and right click it > sharing options. I allow sharing but there is an error within the sharing options window ```
"Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
	No such file or directory
Error loading services."

```
I decide, there is probably a problem with the samba installation so I sudo apt-get install samba4 but install of samba4 fails ```
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so I delete /etc/samba/smb.conf 

sudo apt-get install samba4 and it has the same error as above, even though I just removed the file. :confused:



When I try to browse the network to access the other Ubuntu machines using Go>Network>Browse Network> it shows a folder "Windows Network" within that is "WORKGROUP" when I double click that, it tries to open but fails to retrieve share list from server.

a dump of issues I am facing, in hopes someone might be able to help with at least one of them;
samba seems to not work on any of the 3 installations of ubuntu 11.10
##*
VLC plays music and video, but at launch there is an 8-bit sounding distortion that screeches and eventually, sometimes it goes away (sometimes it doesn't go away) no errors in the ctrl-m on level 2
##*
Encrypted dvds play choppy and jerky after installing dvdread4 and using the /usr/share/doc/libdvdread4/install-css.sh 
##*
I cannot ssh to other machines which have ssh server activated. when I ssh NameOfThePC -l username it times out, unable to connect on port 22, however when I ran putty with windows there was no issue connecting. 
##*
I cannot share files between any of the 3 ubuntu 11.10 machines, though they could share when they were windows. 
:confused:

edit: apologies, i guess that last part was redundant

---

### Post by N00b-un-2 on 2011-12-16
why samba4?  You should be installing the regular samba packages.  This how to I wrote applies specifically to XFCE, but it does in fact work well on other DEs.

[http://ubuntuforums.org/showthread.php?t=1891590]("http://ubuntuforums.org/showthread.php?t=1891590")

more than likely, you're having issues with name resolve order.

> 
VLC plays music and video, but at launch there is an 8-bit sounding distortion that screeches and eventually, sometimes it goes away (sometimes it doesn't go away) no errors in the ctrl-m on level 2

Don't use VLC.  Follow the instructions to install multimedia codecs in the stickied multimedia how to
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

> Encrypted dvds play choppy and jerky after installing dvdread4 and using the /usr/share/doc/libdvdread4/install-css.sh

Known issue from what I understand.  work around?  Rip the DVD, I've had really good luck with MakeMKV [http://www.makemkv.com/]("http://www.makemkv.com/")

> I cannot ssh to other machines which have ssh server activated. when I ssh NameOfThePC -l username it times out, unable to connect on port 22, however when I ran putty with windows there was no issue connecting.


check that the server is configured to use port 22.  Check your router settings.  To use ssh I have to do this
```
ssh 192.168.0.x -l username -p 5000
```
ssh can't resolve hostnames on your local network subnet from what I've seen.  It's best to assign static IP addresses to your machines in your router's DHCP settings menu if you plan on using SSH extensively.  I use a DNS to ssh my computer from my phone all the time.
> 
I cannot share files between any of the 3 ubuntu 11.10 machines, though they could share when they were windows. 
Follow my instructions in the link and report back.

---

### Post by davethewave83 on 2011-12-16
> **N00b-un-2 said:**
> why samba4?  You should be installing the regular samba packages.  This how to I wrote applies specifically to XFCE, but it does in fact work well on other DEs.

[http://ubuntuforums.org/showthread.php?t=1891590]("http://ubuntuforums.org/showthread.php?t=1891590")

more than likely, you're having issues with name resolve order.


Don't use VLC.  Follow the instructions to install multimedia codecs in the stickied multimedia how to
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")



Known issue from what I understand.  work around?  Rip the DVD, I've had really good luck with MakeMKV [http://www.makemkv.com/]("http://www.makemkv.com/")



check that the server is configured to use port 22.  Check your router settings.  To use ssh I have to do this
```
ssh 192.168.0.x -l username -p 5000
```
ssh can't resolve hostnames on your local network subnet from what I've seen.  It's best to assign static IP addresses to your machines in your router's DHCP settings menu if you plan on using SSH extensively.  I use a DNS to ssh my computer from my phone all the time.

Follow my instructions in the link and report back.

Thanks for all the tips. I tried the ssh with IP instead of hostname and it worked.

I did a full purge on all samba and then tried ```
sudo apt-get install samba smbfs smbclient fusesmb gvfs-backends
``` and it appears to have installed now. I had to sudo apt-get purge it all first.

Samba appears to be partially working now, after I followed your guide. When I open the network and navigate into windows network > WORKGROUP I can now see the shares, but I cannot access them. "It says Unable to mount location Failed to mount Windows share"

it is working better, but still not working.

I tried adding many different options to get around the unable to mount issue but nothing is working. 

edit* and now suddenly smbd will not stay started. 

sudo service smbd start 
smbd start/running, process 12557
sudo service smbd restart
restart: Unknown instance:
sudo service smbd start
smbd start/running, process 12605
sudo service smbd stop 
stop: Unknown instance:

it was staying running earlier but now it won't, although when I: 

ps -ef | grep mbd 
returns: 
root     11684     1  0 23:27 ?        00:00:00 smbd start
root     11685 11684  0 23:27 ?        00:00:00 smbd start
root     11753 11684  0 23:28 ?        00:00:00 smbd start
root     11763 11684  0 23:28 ?        00:00:00 smbd start
root     11773 11684  0 23:29 ?        00:00:00 smbd start
root     12479     1  0 23:43 ?        00:00:00 nmbd -D

i am at a loss. network is not browsable anymore either.

*final edit*
Unable to get samba to work, it kept asking for a password regardless of if guest was on or not. I am going to sleep for now it's late. 

my last attempt in desperation was to start fresh with Samba so I 
sudo apt-get purge samba smbfs smbclient fusesmb gvfs-backends
sudo rm -r /etc/samba
sudo rm -r /var/lib/samba
sudo apt get install samba smbfs smbclient fusesmb gvfs-backends

now nothing works at all. there is no /etc/samba/smb.conf or anything :(( 

Is there an alternative to samba? Samba doesn't work very well. 

As a last resort I might setup an FTP server within the network or an apache Html/php-based file hub for my network. I'd really rather just have file sharing though

---

### Post by N00b-un-2 on 2011-12-16
there are two alternatives to Samba that I would recommend.  The first being NFS and the other being SFTP.  NFS is Network File Sharing and it's by far the easiest file sharing to set up on Linux.  Not only that but I've noticed substantially higher data transfer rates when using NFS but that may just have to do with my router.
Configuring NFS consists of two parts /etc/hosts and /etc/fstab.  you add the file you want to share and who can access it to /etc/hosts, and you can set the shares to be mounted at boot on the client computers fstab.

SFTP is somewhat easier to use as there are no configuration files, but you have to log in at least the first time using the terminal.  SFTP is File Transfer Protocol via SSH so it's going to use the same port and username, but you should note that despite sftp using ssh, the syntax is different eg;
```
ssh 192.168.0.x -p 5000 -l user
sftp -P 5000 user@192.168.0.x
```

after the first time you login to sftp and it creates a security fingerprint, you should be able to do so with whatever file manager you use provided its supported.  nautilus, thunar, dolphin all work.  Believe me, I feel your pain in configuring samba.  By far, Samba is the biggest PITA about Linux

---

### Post by N00b-un-2 on 2011-12-16
I should mention that the '5000' in those two commands is specifying the port.  SSH/SFTP use port 22 by default but if you want to ssh to your machine from outside your local network you will need to forward the port, and most ISPs will block most lower ports.  Anything above 5000 is usually good for port forwarding, just make sure each computer has it's own port configured in your router and that the server is configured to use the port correctly.  But for the purpose of using ssh from within your own network, simply using port 22 should be fine

---

### Post by N00b-un-2 on 2011-12-16
[FACEPALM] I forgot to tell you the most important part.  to use SFTP in your browser, do it like this

[[IMG]http://img844.imageshack.us/img844/323/sftp.jpg[/IMG]](http://imageshack.us/photo/my-images/844/sftp.jpg/)

---

### Post by davethewave83 on 2011-12-16
> **N00b-un-2 said:**
> [FACEPALM] I forgot to tell you the most important part.  to use SFTP in your browser, do it like this



Thanks for the help, the strange thing is, I created a new standard user account and logged into it. The standard user account could access the shares for a while, but then it started to say that it didn't know how to open that "file type" (folder) when I'd try to open the network share. :confused:

Anyways, I installed Dolphin and it accesses the shares with no problems at all. It seems like the problem doesn't lie with Samba as much as it does with the file manager. I'm not sure what the default file manager is for ubuntu, do you? Is it Nautilus? 

I just open Dolphin and navigate to network to share, and that works good for now.

when I sftp i get access denied. 

I guess you gotta know the secret hand-shake, and for me it's Dolphin :P

---

### Post by N00b-un-2 on 2011-12-16
yeah, it seems like nautilus (yes it is the default gnome File Manager) got hosed somehow.  Very strange.
As for sftp, the server and client must be installed.  I failed to mention that.  Same for NFS and Samba.  I really don't like how Ubuntu handles packages sometimes, because in this instance I would recommend purging nautilus and reinstalling, but I'm pretty sure that it would actually uninstall Ubuntu Desktop and then reinstall, which is just plain crazy.

In the past I would often patch certain parts of Nautilus (until nautilus elementary came out and then I didn't need to 	:wink:) , which required downloading the source and compiling which may work for you.  But even that is pretty drastic.

---


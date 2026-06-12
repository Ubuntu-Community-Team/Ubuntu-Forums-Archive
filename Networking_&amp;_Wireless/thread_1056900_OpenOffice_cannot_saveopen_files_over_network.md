---
title: "OpenOffice cannot save/open files over network"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by grashdur on 2009-02-01
I cannot save, and usually cannot even open, any files with OpenOffice over my (wired) network. The client computer in this case runs Intrepid Ibex, the host Hardy Heron. Other programs currently have no problem opening my files over the network. 

When I cannot open the file, what happens is I get a dialog box asking me to enter username and password to gain access to the remote folder -- this is after I've already mounted the folder with Nautilus. After I type in the correct username and password, I see the OpenOffice splashscreen, I wait... and then nothing happens. Or I get an error message in a dialog box: "General internet error has occurred."

Sometimes I can open a file over the network, but when I try to save it, I get a dialog box saying, "Error saving the document [filename]: General error. General input/output error."

A few months ago I was allowed to save documents over the network, but they always got corrupted.

In the past I had a very similar problem with OpenOffice, and was able to solve it by changing the name of the host computer. That fix is no longer helping. In some earlier versions of Ubuntu I did not have this problem at all. Today I just tried upgrading OpenOffice to version 3: Right now it looks like I am able again to open any file, sometimes after that extra password request, but like before I still cannot save the files.

---

### Post by AlanR8 on 2009-02-01
I had a similar problem using Kubuntu. If I went into the network via Konqueror and connected to the remote drive I could not save or open files.

However, I now use a program called smb4k that mounts the drive on a session by session basis and everything's fine.

---

### Post by grashdur on 2009-02-07
Has anybody out there succeeded in making OpenOffice open and save files over a network? In the current versions of Ubuntu (Hardy Heron, Intrepid Ibex) and OpenOffice (2.4, 3.0) it just doesn't seem possible. And I've had this same problem off and on for several years now! But I just can't accept working with files only on the local client computer, and I hate copying and saving my files back and forth -- this is just too prone to error and perhaps eventual corruption of files. 

I just can't believe that the developers of OpenOffice never thought about using files over a network!!

---

### Post by FishRCynic on 2009-02-08
to solve a variety of browsing samba issues with ibex (both 386 and amd64)
i made one machine (a ubuntu ibex 386 server in this case) the wins server and subsequently made every other machine
xp, 2000, vista, solaris, ubuntu etc. use it for wins resolution.

i referenced this for example:

[http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/](http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/)

still works in ibex :-)

now before using open office i browse to the folder i want to save to over the network using nautilus to ensure its accessible.  this mounts it for open office use as it will show up now in the save dialog and voila the file saves and can be opened just like is supposed to be.

ps this made lan game connections work consistently over tcp in xp (always had issues before)

---

### Post by AlanR8 on 2009-02-08
> Has anybody out there succeeded in making OpenOffice open and save files over a network?

Yes, as above!

---

### Post by grashdur on 2009-02-08
Ah -- apparently I should have mentioned: I'm not currently running Windows anywhere on my network -- only Ubuntu. And I don't have a "server"; I just set up Samba and enabled file sharing on each computer. 

So is there any way to share OpenOffice files when using an Ubuntu-only network? All other files/programs share just fine over the network. But as far as OpenOffice is concerned, logging into and mounting a folder from a different computer in Nautilus just isn't enough to access that folder.

---

### Post by FishRCynic on 2009-02-08
are you using samba - if so wins as described

(samba is windows networking revisted)

samba is installed by default, nfs isn't

did you install nfs?



note if you file share with samba - you are running samba server
in order to add the wins server to one machine you edit smb.conf -- 
the samba configuration file

---

### Post by grashdur on 2009-02-08
No, I'm only using Samba on both computers for file sharing. Does wins apply at all if I'm using Ubuntu on both computers? I looked at the link you gave but it gave special Windows-related instructions for the client computer, and the article's title specifically addressed Windows networks. Or am I misunderstanding this?

---

### Post by FishRCynic on 2009-02-08
for ubuntu make one computer the wins machine as described

on the other machine(s) 

in smb.conf

change these lines to

wins server = xxx.xxx.xxx.xxx (the ip address of the wins server machine)

name resolve order = wins lmhosts hosts bcast

---

### Post by grashdur on 2009-02-08
Okay. I'm going over the instructions, and looking around at the files on my computer. I have three files called "smb.conf": one is in /etc/samba one is in /usr/share/doc/nautilus-share/examples and one is in /usr/share/samba -- the contents of these various identically-named files are not identical. Should I change all of them? Also I have a file called :etc:samba:smb.conf in /var/lib/ucf/cache. And in /usr/share/samba I also have files called smb.conf.dapper and smb.conf.etch and smb.conf.feisty and smb.conf.gutsy -- I'm confused. Before I obtain root privileges and change these files, which do I change? And this same question will also pertain to changes made on the client computer.

Regarding setting up static IP addresses, I had thought that I'd be doing that from my router's web interface, but it looks like I was wrong on that. But apparently I can probably set this up in System > Administration > Network. Or am on the wrong track here?

---

### Post by grashdur on 2009-02-09
Can anybody help with this? It looks like I've gotten a good suggestion to try, but I'm bewildered by the profusion of identically-named system files -- I don't know which one(s) to modify.

---

### Post by FishRCynic on 2009-02-09
the wins changes make in your /etc/samba/smb.conf

can your router give you dhcp leases with a dhcp reservation?
ie can you use dhcp and have the router always give you the same ip address?

---

### Post by grashdur on 2009-02-10
Hi FishRCynic -- Thanks for the additional details. I made the changes to smb.conf on my "server" computer, rebooted, made the appropriate changes on my "client" computer, and rebooted that one too, but my problem is unchanged. (Though I have the impression that the network is now working a bit faster.)

Is it possible that the Linux version of OpenOffice is simply not designed to work on remote files over a network? I've noticed in that past that a number of programs don't even have the option to browse to a network location for opening/saving files, though OpenOffice can browse to network locations. Among the programs I currently use, OpenOffice seems to be the only one that works poorly with the network.

Or is it possible that OpenOffice has some mysterious incompatibility with my router? (D-Link EBR-2310) Back when I used Windows XP regularly, I had the same problem with OpenOffice in Windows. I was able to solve that problem by "mapping the network drive" (similar to what I do now in Ubuntu, mounting the network folder). More recently, in older versions of Ubuntu I was able to make OpenOffice work on the network by removing the space from my host computer's name -- but that's not helping any more.

Today I'm actually able to open files remotely, but not save them except on the client computer. (Both before and after making these network changes today)

Regarding the router and static IP addresses: On the router's webpage I don't seem to have any option for assigning an IP address to a given computer. It's set to do DHCP by default, and I haven't been able to turn that feature off. However, on my "host" computer I was able to go into System > Administration > Network, and change the properties for the wired connection from DHCP to static addresses. When I assigned an address within the address range my router uses, it didn't work. When I assigned an address outside that range, it seems to work just fine, except that I don't see my main computer listed among the computers on the (DHCP) network.

---

### Post by grashdur on 2009-02-10
Btw, currently when I try to save an OpenOffice file over the network, I get the error message: 

**Error saving the document [the name of my file]: Nonexistent file.**

After I press the OK button, another error message pops up: 

**Error saving the document [the name of my file]: General error. General input/output error.**

---

### Post by yther on 2009-02-10
> **grashdur said:**
> Btw, currently when I try to save an OpenOffice file over the network, I get the error message: 

**Error saving the document [the name of my file]: Nonexistent file.**

After I press the OK button, another error message pops up: 

**Error saving the document [the name of my file]: General error. General input/output error.**

I've been having the same problem.  I believe it's because OpenOffice lost (or never had) the ability (in Linux) to handle connections via Samba/CIFS.  Using the KDE file picker would enable me to see the files, but I'd still have to deal with OO's lack of capability.

After some searching, I found a fix, not only for OO but for any program that doesn't include an awareness of Samba.  Basically what we can do is map the Windows share to a directory, and then *any* program can access its contents without needing to care about how they got there, because the operating system takes care of that.

This guide, [How to Mount a CIFS Network Share]("http://www.swerdna.net.au/linhowtosambacifs.html"), although it was written for a different Linux distribution, was the best one I found.  It's clear and easy to follow, at least for me.  As long as the machine *serving* these folders always has the same IP address, it should work.

It boils down to adding a line in my /etc/fstab for each shared folder I want to access.  For example:

```
//192.168.2.104/share           /mnt/nasdrive/share       cifs auto,username=joejimbob,_netdev,nobrl,noexec 0 0
```

The above is on my laptop.  When I get to work and start it up, it mounts that folder for me.  Now I can fire up OpenOffice Calc and navigate to /mnt/nasdrive/share and get to the files I need.  I can do the same with anything else, even command-line tools such as "ls" that certainly don't know what a Windows shared folder is.  :)

---

### Post by grashdur on 2009-02-12
Hello yther -- I'd like to try that out. Just a couple things I'm unclear about: 

Do I need to revert first to the default version of my smb.conf file? Or do I need to retain the changes I just made to it (see in discussion above)? Or does it matter either way?

In that webpage you provided a link to, under the instructions for setting up the server side, under "Secure Shares," I see the recommended text:

```
[share_name]
path = /path_to/shared_directory
read only = no
force user = server_user
```

Is there any particular place I should put this in smb.conf? And I would replace [share_name] with my chosen share name, *without* these square brackets?

By the way, when I started out by adding the share to my samba database with the recommended commands in Terminal, it all looked the same as on your link, with password entered twice, except that it didn't conclude by saying "added user" -- perhaps this is still okay(?), since that was written for a different distribution.

---

### Post by FishRCynic on 2009-02-12
it is a network resolve address issue - other programs won't work
correctly either - using samba wins fixes it

your other option is to add the ip addresses and machine names 
manually to your  /etc/hosts file
the names should then resolve correctly
 for example
to the existing:

127.0.0.1	localhost
127.0.1.1	machinename

# The following lines are desirable for IPv6 capable hosts
::1  localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




add something similar to these using your ip addresses and machine names
you will need either static or dhcp static ip addresses

127.0.0.1	localhost
127.0.1.1	machinename
192.168.0.10    name1
192.168.0.11    name2
*etc etc

# The following lines are desirable for IPv6 capable hosts
::1  localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

note: use nautilus first to browse the share so that the share is mounted
then the other programs (including openoffice) should have the share mounted in the save dialog

---

### Post by dmizer on 2009-02-12
How are you mounting the Samba share? Are you just browsing to it in Nautilus? If so, you will continue to have your problem. If you mount the share in /etc/fstab as outlined in the second link in my sig, then you will be able to save Open Office files directly to the share.

Edit:
I have directions in that howto (under "Troubleshooting") specifically for your Open Office error.

---

### Post by grashdur on 2009-02-13
Hi FishRCynic: I just tested one more time: Just as before, since making the changes to smb.conf I'm still not able to save OpenOffice files over the network, even with first opening the relevant folder in Nautilus. (And when opening the first time in OO, I always get an extra dialog box asking for username and password for the network share.) Other programs seem to work fine over the network -- I just tried to do Save As within the Eye of Gnome applet and it worked fine saving to the same network folder.

In your last post, the idea makes sense but I'm not fully clear where you say:

> your other option is to add the ip addresses and machine names
manually to your /etc/hosts file
the names should then resolve correctly
for example
to the existing:

127.0.0.1 localhost
127.0.1.1 machinename

Should first I undo the changes you suggested before in smb.conf, or leave those changes as-is? (Perhaps it doesn't matter?) And should these additions to /etc/hosts be done on the host computer, client, or both?

Tomorrow I'll try out these various fixes, yours and from yther and dmizer.

---

### Post by FishRCynic on 2009-02-14
i have gone and looked at the networks i have set up, for me the wins server solution works the best

i just realized having just done a fresh ubuntu-desktop install on an intrepid 386 server package openoffice.org does not always (or maybe never) get installed by default. reinstall or install as it might not be there -this will ensure the proper support gnome is installed (and approximately 25 other packages on a fresh install)

if you are using static addresses and listing them in your hosts file wins is unnecessary (if you have the occasional added computer wins won't hurt) you may want to change the name resolve order= , to suit hosts first

fixed samba shares in fstab will work, its just (and the same with the static/hosts solutions) as your network grows/changes these files have to be updated manually (new shares etc) with wins this is unnecessary

******* see we reinvented the wheel for you ***** this might explain this a little better

[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

---

### Post by grashdur on 2009-02-15
FishRCynic, yther, dmizer: Thank you for the time you've taken to try to help me through this problem. I spent about five hours yesterday and some more time today trying all the rest of your suggestions -- but nothing has worked. 

I've decided to leave my network in the first configuration that FishRCynic suggested (wins), because it really makes my network faster. 

I think this is just a bug in OpenOffice -- no other programs seem to have this problem. I'm reporting it to the OO people, so hopefully they can make it work better on future releases.

---

### Post by dmizer on 2009-02-15
> **grashdur said:**
> FishRCynic, yther, dmizer: Thank you for the time you've taken to try to help me through this problem. I spent about five hours yesterday and some more time today trying all the rest of your suggestions -- but nothing has worked. 

I've decided to leave my network in the first configuration that FishRCynic suggested (wins), because it really makes my network faster. 

I think this is just a bug in OpenOffice -- no other programs seem to have this problem. I'm reporting it to the OO people, so hopefully they can make it work better on future releases.

Please post the contents of your /etc/fstab file.

---

### Post by grashdur on 2009-02-16
Here are the contents of etc/fstab: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

I never modified it, as I only tried doing temporary mounting from command line. Oh, by the way, I'm not sure if this is the correct one to show: This is from my main computer, while the one that would serve as client for file sharing is not available at the moment (my wife is using it to watch You-Tube). Let me know if that's the one you want to see.

---

### Post by dmizer on 2009-02-16
What is the exact command you use to mount from the command line then?

I need the command on the computer you say you are having trouble saving OOo files from.

---

### Post by grashdur on 2009-02-16
I don't remember now the exact commands I tried -- but I went through all the various links that you and others have offered in this thread, and from them I tried the commands I found that were specifically for secured read/writable mounts.

Here are the contents of the etc/fstab file on my laptop (the computer where I'm trying to mount and access network folders):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=09e23a1f-d5e4-4ae9-8108-651aa9cf4ead /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d83c05d9-6c7e-41d0-b587-4afa0746ba8b /home           ext3    relatime        0       2
# /dev/sda5
UUID=3299675c-358a-464e-a1a7-2862a6a490c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I haven't made any modifications to this fstab file either.

---

### Post by dmizer on 2009-02-16
The second link in my sig has directions on how to mount your share without authentication, as well as how to mount the share to fix your specific problem.

If that did not work for you, I'm interested in pursuing this so I can add a fix to my howto.

Please make sure that smbfs is installed:
```
sudo aptitude install smbfs
```
Then post the output of:
```
smbtree
```

---

### Post by grashdur on 2009-02-19
Hi dmizer: I just went into the Synaptic Pkg Mgr and verified that I do have smbfs installed. 

Here is the output from that command (with both computers turned on and connected to the network):

```
grashdur@Gateway3:~$ smbtree
Password: 
WORKGROUP
	\\SONY2          		Sony2 server (Samba, Ubuntu)
		\\SONY2\music          	
		\\SONY2\private        	
		\\SONY2\HP-LaserJet-1200	Hewlett-Packard HP LaserJet 1200
		\\SONY2\HP_LaserJet_1200	Hewlett-Packard HP LaserJet 1200
		\\SONY2\MP150          	Canon MP150
		\\SONY2\Stylus-C42     	EPSON Stylus C42
		\\SONY2\IPC$           	IPC Service (Sony2 server (Samba, Ubuntu))
		\\SONY2\print$         	Printer Drivers
	\\GATEWAY3       		Gateway3 server (Samba, Ubuntu)
		\\GATEWAY3\shareddocs     	
		\\GATEWAY3\our stuff      	
		\\GATEWAY3\HP_LaserJet_1200	Hewlett-Packard HP LaserJet 1200
		\\GATEWAY3\PDF            	PDF
		\\GATEWAY3\Stylus_C42     	EPSON Stylus C42
		\\GATEWAY3\IPC$           	IPC Service (Gateway3 server (Samba, Ubuntu))
		\\GATEWAY3\print$         	Printer Drivers
```

---

### Post by dmizer on 2009-02-19
First, create a moutpoint for your share:
```
sudo mkdir /media/gateway3
```

On the laptop, edit fstab with the following command:
```
gksudo gedit /etc/fstab
```
Then add the following line to the end of your fstab file:
```
//GATEWAY3/shareddocs    /media/gateway3        cifs    guest,nobrl,rw,file_mode=0777,dir_mode=0777 0 0
```
Save the file, exit gedit, and restart your network with the following command:
```
sudo /etc/init.d/networking restart
```

You should get a new icon labeled "gateway3" on your desktop. If not, try rebooting. Then try editing a file with OO.

---

### Post by grashdur on 2009-02-21
Hi dmizer: Your instructions were especially clear and easy to follow this time. Thank you. But: When I tried to restart the network:

```
grashdur@Sony2:~$ sudo /etc/init.d/networking restart
[sudo] password for grashdur: 
 * Reconfiguring network interfaces...               
Ignoring unknown interface eth0=eth0.
```

So I tried rebooting. Still nothing mounted. Then I thought it might be because my file share on the host computer is set for username/password and not for guest access, so I allowed guest access. I restarted networking. Same result as above. I rebooted again. Still nothing.

---

### Post by dmizer on 2009-02-21
Argh ... Ibex ;) /etc/init.d/networking restart won't work in Ibex, sorry ... my fault.

After you reboot, can you open Nautilus and browse to /media/gateway3? Are your shares there?

---

### Post by grashdur on 2009-02-21
When I browse to /media/gateway3 I see a pointing-hand icon instead of the arrow icon -- suggesting that it's about to display something there. But it always stays blank. And using that hand icon to click inside the empty box does nothing.

---

### Post by natxoo on 2010-02-26
I've solved it installing gvfs-fuse package. This make openoffice use fuse an automagically 'copy' in /home/user/.gvfs

---


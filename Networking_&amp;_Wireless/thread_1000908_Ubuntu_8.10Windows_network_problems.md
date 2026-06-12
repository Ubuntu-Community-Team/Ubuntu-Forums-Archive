---
title: "Ubuntu 8.10/Windows network problems"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by KisbyRing on 2008-12-03
First let me apologize if this has been answered several times.  I've been combing the forums trying different solutions but nothing seems to work.  

I'm a newbie to Linux and Ubuntu, although I've been toying with them for several months.  I've been slowly trying to switch my family to the open source world with mixed results.  Software that runs under Windows is generally not a big deal.  The biggest hurdle is switching the OS.  I tried to show how easy Ubuntu was only to run into a couple of issues.

I set up the OS fine to a USB drive so I can switch without having to worry about MBR/Grub issues and I can turn it off and everyone is safely back to Windows!

The problem occured when I tried to show them that the network still worked!  They could still transfer files with the windows PCs and print to the network printer.  

Guess what?  They couldn't! Ubuntu doesn't see the windows shares and can't print to the network printer.  

The network runs fine using windows.  It is a wired/wirelessnetwork and I have 2 (wired) pcs running XP with printer attached to one of those, 1 (wireless) laptop running Vista, and then the (wired) PC which runs Vista/Linux (the "see how easy it is machine").

I've updated all the packages I can, samba included, installed Webmin, and made sure of the easy stuff, right workgroup name, can ping and administer the router from linux PC.

Any suggestions would be appreciated.  And thanks for reading a long post from a new guy....

---

### Post by puppywhacker on 2008-12-03
Hi,

You can try to browse with nautilus using "Network" as a place. And for me that would work. The thing is that windows uses the NMB and/or WINS to browse the network, all windows will elect a master browser every 11 minutes so there is only one machine keeping track of the machines in the workgroup. This is proves for me to be an unreliable way of "seeing" machines.

So what I usually do is I reference them by ip-address. for instance in nautilus in the location bar you can type smb://192.168.1.2/
(if you can't you have to click the button left of the location bar)

you could also create an /etc/lmhosts file (kind of similar to the /etc/hosts) which has all the names to ip-address mappings already.

to be honnest, there are an overdose of things you could try, so goodluck

---

### Post by Halbarad on 2008-12-03
Hi, this is an old problem that may depend on several causes. I had to struggle with it several times -- my network presently works very well in all respects (three Linux boxes, a Win XP and a Win2000).
I can just tell you what practically worked for me.
I think the first thing to try is this: open Places-->Home, click the notebook near the address bar and write the IP of a Win pc in it (preceded by smb://, as puppywhacker said above). If you can browse the network this way, your problem is with name resolution or with messed up security options.

To fix this, my advice is to install winbind first:

```
apt-get install winbind
```

and restart your pc (restarting the network or samba is often not enough).

Check if it works. In the second place,

```
gksu gedit /etc/samba/smb.conf

```

Have a look at it. For a home network, a very short file is normally required. You get the working part of your file if you type

```
sudo testparm -s /etc/samba/smb.conf
```

Mine is quite short:

```
[global]
	server string = Samba Server Version %v
	security = SHARE
	log file = /var/log/samba/log.%m
	max log size = 1000

[Shared]
	comment = Temporary Share Area
	path = /home/Shared
	read only = No
	guest ok = Yes

```

In order to browse the other boxes, you need only the [global] section; you might start with it in order to see if it works. Make a backup copy of your original smb.conf before editing it: 

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.bak

```

Winbind and "security=SHARE" in my smb.conf fixed several problems for me: I hope they can be of some use to you.

Another thing which helped a lot was to change a bit my file /etc/nsswitch.conf -- but that was because I could not actually ping the other boxes in my network. You say you can. But are you sure? Sometimes you actually ping *something*, but not your network pc. One of my PCs was called "Morgenstern" (this is its netbios name, which is still used by network software): when I tried to ping it, I got in fact a response -- but the pinged machine was a Corel one, some 10000 kms away from my home. That is, if a machine named like that is not found in your local network, your router looks it up in an external server and redirects you far away. Try this instead:

```
nmblookup <name>

```
This asks the IP of the machine corresponding to a network PC called <name>.
If you get back an IP number (such as 192.168.1.100) then you can resolve the names of your network boxes; otherwise you cannot -- and we have to make some changes in your nsswitch configuration file.
There are more commands we can give to test your samba tree, the recognized machines and folders etc. -- but this may be enough to start with.

Good luck

---

### Post by KisbyRing on 2008-12-16
Well I tried all the suggestions so far and even totally reinstalled everything from scratch, made sure I had the latest update of everything and no luck.  It still doesn't work.  Can't see Windows shared files and can't print to windows network printer.

Unfortunatley Ubuntu, and Linux in general, will disappear from my systems.  While I applaud all those who stick it out and "eventually" find solutions or live with the limitations, we live in a Windows world and I can't accept not being able to accomplish very basic networking with this OS.  

I love most of the open source software I've tried and really do like Ubuntu...Most of the network use in my house is web surfing and sharing and printing the odd file.  My lads use it for chat and the odd online game (WoW). All tasks I think should be achievable with Ubuntu.  I had really hoped to get everyone, to at least some degree, into a Linux world.  But unless Linux is made a bit more user friendly to those of us who are only moderately tech savy, it won't gain mass acceptance anytime soon. It's a shame really.

---

### Post by cabomix on 2008-12-29
I found a rather easy way to fix this. After trying many options this works great!

find the workgroup for your workgroup network and note it.Type
```
sudo gedit /etc/samba/smb.conf
```
find the workgroup = (your windows workgoup)
in my case,
> 
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

SAVE AND CLOSE
now Type
```
sudo gedit /etc/nsswitch.conf 
```

and add the word "wins" BEFORE the word "dns" under hosts
Example:

> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return]wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Reboot and you shall be able to find all your workgroup shares in you windows machines!
I hope this helps.

---

### Post by mahlerchiro on 2009-01-07
I have been searching for days and this last post relay worked but I am not sure what I might have performed before this that might have helped but this is a definet step. Thanks cabomix

---

### Post by tim15856 on 2009-01-21
As far as Ubuntu printing. In order to avoid problems I put my USB printers on a USB print server. You may not have all the bi-directional communications with the printers, but it works well enough. It's easy to set up in both Windows and Linux. I also have a Brother laser printer with built in ethernet. Ubuntu detects that printer automatically so installation is a snap.

---

### Post by jonandrews on 2009-01-21
I've done a step-by-step guide to configuring network printing between Ubuntu & Windows which should be helpful to you..
[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

---

### Post by snowglyder on 2009-02-19
> **cabomix said:**
> I found a rather easy way to fix this. After trying many options this works great!

find the workgroup for your workgroup network and note it.Type
```
sudo gedit /etc/samba/smb.conf
```
find the workgroup = (your windows workgoup)
in my case,

SAVE AND CLOSE
now Type
```
sudo gedit /etc/nsswitch.conf 
```

and add the word "wins" BEFORE the word "dns" under hosts
Example:



Reboot and you shall be able to find all your workgroup shares in you windows machines!
I hope this helps.

You are *the* man!! I've been having these issues since 6.10, and this fixed it! THANKS!!! :o

---


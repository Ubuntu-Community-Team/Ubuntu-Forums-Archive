---
title: "Windows Shares..........Again!"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2010-03-24
I'm at a real crossroads here and though I realize this might have been covered in one of the thousands of threads here, to date (6 months) I've found NOTHING that I can understand to address it.   
 

 I'm somewhat of a “new user” in that I just started using Ubuntu with the release of v9.10.  Prior to that I had toyed with several different distros, ie Suse, Red Hat, Mandrake, Fedora, Mephis etc. and had never run up on the problem I have with Ubuntu now.  It involves file/drive shares on a Windows network and I'll list what I'm doing below so hopefully someone can tell me how to make this work before I scrap the whole project.  Suse use to be my favorite and file sharing was NEVER a problem although there were other issues that were.  THAT is the reason I have settled on Ubuntu as my Linux OS as the “other” problems (multiple) I had with previous distros are not in Ubuntu.   
 

 What I've got:
 

 I've got a home network that currently has 5 computers on it.  I have an MBR1000 Cradlepoint router/firewall with a Laptop Connect card for my Internet service.  The Cradlepoint has DHCP enabled along with wireless.  Three of the computers on this network have multiple operating systems on them and the other two are either XP or Ubuntu as I have multiple hard drive caddies for my laptop that can be changed in a minute or so.
 

 The multiboot systems consist of Ubuntu 9.10, XP, Suse, Vista and 7  and the others only XP and Ubuntu 9.10.  I run a repair shop so that's the reason I have one computer with so many systems on it.  I know this might be confusing to some but bottom line is I've got computers with Ubuntu and multiple Windows drives on them that I need to be able to file share on a Windows network and to date, I've found nothing simple that works!
 

 If someone has a fix for this I'd appreciate some help here, other wise I'm going to have to abandon Ubuntu as well, which I really don't want to do but I'm continually having to exit Ubuntu and boot Windows to copy files, etc off of customers computers before I  re-install Windows on them.
 

 So if someone can either point me to a fix or send me a fix or send me a phone number in the USA that I can call to  discuss a fix I'd appreciate it!
 

 Thanks,
 

 Ken

---

### Post by coffeecat on 2010-03-24
Curiously, I was just copying some files from my NAS device smb share to Ubuntu as I came across your post.

First, make sure you have samba installed. I find it helpful to make a new folder for a share in my Ubuntu home, right-click on it and select "sharing options", which will install the necessary samba bits for you.

Once you've logged out and in again, you'll be able to finish creating the share and you may now be able to browse smb shares on your network. If there are any problems still, have a look at this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

The simple edits of smb.conf and nsswitch.conf described there and installing winbind (if it's not already installed) has allowed me both-way sharing between Ubuntu Karmic, Windows, MacOS and my NAS box.

The good news is that sharing seems to work out of the box in Lucid. Iirc, all I did was to create the shared folders in Lucid.

---

### Post by ken0069 on 2010-03-24
Coffeecat thanks for the info.  I guess I left off something that was kinda important concerning Samba so I'll add that here.  Yes Samba is installed but obviously not configured correctly.  The part that really gets me is I can access ANY Windows computer drive from any Ubuntu computer but although I can see the Ubuntu drives from Windows box but can't access any of them from that Windows box.   I'll read over the link you posted to see if that will turn on a light.  Thanks,  Ken

---

### Post by amit@nitttrchd.ac.in on 2010-03-25
> **ken0069 said:**
> Coffeecat thanks for the info.  I guess I left off something that was kinda important concerning Samba so I'll add that here.  Yes Samba is installed but obviously not configured correctly.  The part that really gets me is I can access ANY Windows computer drive from any Ubuntu computer but although I can see the Ubuntu drives from Windows box but can't access any of them from that Windows box.   I'll read over the link you posted to see if that will turn on a light.  Thanks,  Ken


Run this

$sudo apt-get install nautilus-share

and thru right click u can share

---

### Post by ken0069 on 2010-03-26
First of all, thanks for the input.  Using info here and more that I got online I finally got all drives shared and in the end it was done by point and click, no command line at all.  

I've even figured out how to run some of my Windows only apps in Wine although Unreal Tournament doesn't seem to function well in that environment but that's a case for running Linux VM instead, which will probably be my next challenge.

Anywho, I'm getting closer and closer to a Ubuntu only computer, especially since I've also learned to use Gimp for photo editing for my web page work.  

Thanks again all!

Ken

---


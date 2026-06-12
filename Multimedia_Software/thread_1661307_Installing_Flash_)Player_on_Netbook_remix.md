---
title: "Installing Flash )Player on Netbook remix"
date: 2011-01-06
forum: Multimedia Software
---

### Post by phantommullet67 on 2011-01-06
Can anyone explain to me how to install the newest flash player on netbook remix?  I am pretty rusty with linux and want to put it on my netbook.  I currently have it on a flash drive.  I want to make sure i can do everything I need on it before I wipe Windows.

---

### Post by ajgreeny on 2011-01-06
A few points!

1.   Make sure your netbook works with Ubuntu before wiping Windows, or use a dual boot if you have the disk space.

2.   If you want the netbook desktop that works, stick with 10.04 rather than 10.10 with the unity desktop, which many including myself find rather baffling.  Or, of course, stick with the gnome desktop in either of the two versions.

3.   If you do go ahead after ascertaining that Ubuntu works OK, open up System ->Administration ->Software Sources (*that's where it is on the gnome desktop, but I've no idea how you get to it in the unity desktop*) and enable the **universe** and **multiverse** plus the canonical archive **Partner** repositories, if they're not already enabled.

4.  Carry out a full update of the system with ```
sudo apt-get update
sudo apt-get upgrade
```4.  Search for and install adobe-flashplugin, and any other apps you want and need using software-centre..

---

### Post by lovinglinux on 2011-01-06
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the latest flash from Adobe, according to your system architecture and version. Additionally, it will apply some tweaks to improve performance.

---

### Post by phantommullet67 on 2011-01-06
> **ajgreeny said:**
> A few points!

1.   Make sure your netbook works with Ubuntu before wiping Windows, or use a dual boot if you have the disk space.

Yeah, i have it on a USB drive right now, but I have noticed that nothing you save to it (documents and downloads) stay after shut down.  I wouldn't mind dual booting as I have 250 GB and don't intend to use this for much other than school and web browsing.  I am rusty on how to make a partition without reformatting the whole disk, however.  

> **ajgreeny said:**
> 
2.   If you want the netbook desktop that works, stick with 10.04 rather than 10.10 with the unity desktop, which many including myself find rather baffling.  Or, of course, stick with the gnome desktop in either of the two versions.

Gnome doesn't come with 10.10 does it. Relating to what I posted on top, I don't think I can install it on the USB drive :(.  All drivers and everything do seem to be working ok.  Streaming video is the last capability that I can think of that I need it for and don't currently have.

---

### Post by ajgreeny on 2011-01-06
> **phantommullet67 said:**
> Yeah, i have it on a USB drive right now, but I have noticed that nothing you save to it (documents and downloads) stay after shut down.  I wouldn't mind dual booting as I have 250 GB and don't intend to use this for much other than school and web browsing.  I am rusty on how to make a partition without reformatting the whole disk, however.  
You are right, nothing is saved to your system on a standard live version, though it is possible to use what is known as a persistent install on either a live CD or USB.  Your disk is plenty big enough for a dual boot, but I would need to know the current partition layout to be able to give you recommendations.  from the live ubuntu run ```
sudo fdisk -l
```(capital L at the end, not 1) in terminal and post the output back here.


> **phantommullet67 said:**
> Gnome doesn't come with 10.10 does it. Relating to what I posted on top, I don't think I can install it on the USB drive :(.  All drivers and everything do seem to be working ok.  Streaming video is the last capability that I can think of that I need it for and don't currently have.
Yes gnome is in netbook 10.10 version.  Just choose it from the session menu bottom right after clicking on your name at login, or to try in the live version simply logout, enter "ubuntu" as user at the login screen, choose **classic desktop**, I think it is called, and just hit enter at the password screen.

---

### Post by phantommullet67 on 2011-01-06
I don't see a session menu(and on this live version, there is no loging in on startup) to use Gnome.  

It says that 1 and L are not valid options for fdisk.  When i try it with -l, it doesn't output anything, no errors or responses.

---

### Post by ajgreeny on 2011-01-07
Sorry, my typo mistake on the fdisk command; I meant to say lower case L, not capital.

I am amazed that it gives no output; that suggests that there is no hard disk seen in the machine.

As for the session menu, have you logged out from the live session, not restarted, just logged out?  If you do the login screen will appear and you can then enter "ubuntu" as the username, then choose from the session menu and finally hit enter on the empty password screen to login again

---


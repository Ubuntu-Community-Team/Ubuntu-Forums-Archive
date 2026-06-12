---
title: "Ubuntu suddenly cannot mount Windows shares"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Emporata on 2010-11-19
I am running Ubuntu 9.10 (upgraded from the 9.04 disk).  Upon installation, Ubuntu instantly saw our Windows home network and could open Windows shares.  Then one day it inexplicably was unable to do so.  It can see that there is a Windows Network but cannot mount the shares. I have tried everything I can think of and have even purchased a new modem/router combo to make sure there was nothing wrong on that end.  However, it still can't mount the Windows shares.  

Interestingly, I also have a couple of old computers running on Puppy Linux and samba enables me to use both of those computers to see what is on my Windows computer, access the files, etc., but they can't see the Ubuntu computer and the Ubuntu computer can't see them.  Also, the samba on my Ubuntu computer does not seem to work in the same way as the samba on Puppy.  That is, I can't seem to get it to really scan the network, looking for other computers, but I am sure that must be some sort of operator malfunction.  


Thanks very much. 

PS: I don't know if this would change anything but we do plan to upgrade to 10.04.1 LTS but I have some work I need backup first.

---

### Post by cavalier911 on 2010-11-19
You indicate Ubuntu can see the shares offered by windows but can not mount them.Other computers running linux can view and mount the shares on this same windows computer.Write down the i.p. address of the windows computer by opening it's terminal and typing ipconfig. Go to the Ubuntu computer,open it's terminal.
```
smbtree
```
This will list the windows netbios name followed by it's shares.
Make a mount directory:
```
mkdir win.share
```
Mount share with **windows i.p. address **to local mount directory:
```
sudo mount //*i.p.address.windows.box*/share.name   win.share/ 
```
Post all errors you see if the mount fails.

If this work's whatever method or program you use to mount requires netbios name to i.p. address resolution (nmblookup) which is broken on your system.

---

### Post by Emporata on 2010-11-19
Would it be less work to do the Ubuntu upgrade?  Would doing so fix nmblookup?

---

### Post by Emporata on 2010-11-19
Sadly, I was unable to do anything with the ubuntu termnial but give it my password.  That is, I tried typing in the code you sent me but when I hit "enter" it just asked for my password.  I did learn DOS about 20 years or so--so I guess I should be able to do this!  Still, I must be doing something incorrectly!

---

### Post by cavalier911 on 2010-11-19
I know most people would rather have a root canal than use the terminal.:p
An upgrade is more likely to introduce additional problems than it is to fix this one.
Back up your personal files, upgrade and keep your fingers crossed. 
If the upgrade goes bad you'll have to download the iso and do a clean install.


Use: smbtree -N
So it won't ask for the password.

Make the mount directory in your home folder.

When you use the sudo command it elevates you to root privileges. This is required with the mount command.You have to enter the password of your user account,(it doesn't print out as you type your password in case someones looking over your shoulder at your display to steal your password).Then hit enter,if the password is correct it will execute the command.

---

### Post by Emporata on 2010-11-20
I think I am forced to work with the terminal. I guess I don't mind if I am just fixing something but I wouldn't want to do it on a daily basis just to get my work done.  It was just too easy to lose work, etc., in the old days! At any rate, there is just too much important work on this computer for me to be able to get it all off of there and do a clean install at this time.  

Anyway, here is the error message I got:

mount: wrong fs type, bad option, [code I typed was here]
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Thanks very much for your help!

---

### Post by cavalier911 on 2010-11-21
Reinstalling the **smbfs** package which provides smb/cifs mount utilities may fix the problem.
Open synaptic package manager, click the reload button,do a search for the smbfs package.
When it finds the smbfs package,if it's not installed, right click mark for installation,if it suggests an upgrade right click choose mark for upgrade, if it's the current version right click mark for re-installation.
Agree to install of any dependencies.
Click the Apply button
Then Edit/Fix Broken Packages
Reboot,see if samba mount is fixed.
If not rerun the mount command and report back any errors.

---

### Post by Emporata on 2010-11-22
I ended up getting frustrated and reinstalling the OS.  Well, I reinstalled because I saw a "problem," which turned out to be operator malfunctions and not a problem at all, panicked and decided to start from scratch.  It will be a little while until all that is finished and then I will see if the Ubuntu computer can see the others.  Will come back with an update as soon as I know.  

Thanks.

---

### Post by Emporata on 2010-11-23
The new OS is installed and things are back to where they were before the problem occurred.  The Ubuntu computer can see the Windows network and, unlike before, can identify the Windows machine on it, but the Ubuntu computer still cannot mount the Windows shares!  It still says that if failed to receive the list from the server.  :(  I am wondering if this is a Windows issue. This Windows computer is XP, service pack 3  

Since I am thinking about trying to create a dual boot on the Windows computer over the holidays (when I don't have quite so much work to do), I think I will just wait and see how the networking goes after that is completed.  I will try to get Ubuntu on the Windows computer but, if I can't, I will put Puppy Linux on it.  If the two computers can't mount shares from each other after all that is done, then I guess I will just have to proceed from there and try to fix it.  

Thanks very much for your help!

---


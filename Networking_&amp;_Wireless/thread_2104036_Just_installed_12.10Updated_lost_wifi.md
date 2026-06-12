---
title: "Just installed 12.10/Updated lost wifi"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by lferg on 2013-01-11
Hello all, I have googeld and searched the forum for the answer for the better part of the day.  I just did a complete wipe of my machine (Dell Inspirion N5010) and installed 12.10.  Wifi worked and then I did the update and now wifi is gone.  :(  Wireless is gone from my network options but the name of the wireless network I used prior to update is still in the Wireless tab of the Network Connections.  This is my first experience with Linux.  In the terminal, I put in "rfkill list" and it returned nothing at all.  Any help is appreciated.

---

### Post by iponeverything on 2013-01-11
get connected via wired connection and go into the package manager (or whatever they call it these days) and install:

linux-backports-modules-compat-wireless

---

### Post by lferg on 2013-01-12
Well I have no clue what happen but now when I boot I get the purple splash screen and then my screen goes dark and thats it.

---

### Post by Bucky Ball on 2013-01-12
Are you getting a menu with a selection of kernels to boot? If not, try hitting shift just after boot.

Select the top kernel, hit 'e' to edit it, find that line that ends in 'quiet splash' or either of those words and after a space add 'nomodset'.

Follow the instructions at the bottom of the screen to save the changes and continue with the boot.

What happens?

As for the wireless problem, if you can get in please open a terminal and copy/paste this:

```
sudo lshw -C network

```Hit return and post the output back here.

---

### Post by lferg on 2013-01-13
Nothing at all happened.. It was just black and thats it.. Not on and a black screen, more like the screen was off but the system was on.  I reinstalled Windows to format then reinstalled Ubuntu. Now I am back to the 12.10 no wifi issue.  :(

lspci -nn | grep 0280
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

I reinstalled **bcmwl-kernel-source** Then went to shell and I get this???


apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
niviah@niviah:~$ apt-get --reinstall install bcmwl-kernel-source
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I have no idea what to do... Baby steps please.

---

### Post by mapes12 on 2013-01-13
The no wifi issue happened to me the other week following a fresh install. I Googled everywhere, then noticed that the hardware had turned itself off. A simple Fn+F10 (or whatever it is on your machine) to turn on and it worked perfectly.

---

### Post by audiomick on 2013-01-13
> **lferg said:**
> Then went to shell and I get this???


apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
niviah@niviah:~$ apt-get --reinstall install bcmwl-kernel-source
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/),[COLOR="Red"] are you root?[/COLOR]


There is your clue, what I have marked in red. You need root privileges to run apt-get, same as you do for installing from the software centre or synaptic. Sudo is used in Ubuntu to gain root privileges.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

What you need in this case is
```
sudo apt-get update
```

You will be asked for you password in the terminal. Don't be phased by the fact that you can't see what you are typing. Just type your login password and hit enter.

You can safely follow that command with
```
sudo apt-get upgrade
```

which will make sure that all the packages in the package  list, which apt-get update refreshes, are all at the newest version.


One other thing: you mentioned that you "reinstalled windows to format". There is no need for this. You can do all the formatting you need, at least for a Linux only install, using the partitioning tool gparted from the live environment. That is the "try without installing" option on the installer CD or USB that you used to install Ubuntu. That is likely to be loads quicker than wading through a Windows install just so you can format your drive.

Having said that, if you want to do partitioning work on an ***existing*** Win7 (and presumably Win8) partition, you should use the windows tool.

Edit:
Regarding the wifi, you might like to look at this post
[http://ubuntuforums.org/showpost.php?p=11826283&postcount=4]("http://ubuntuforums.org/showpost.php?p=11826283&postcount=4")

I don't know for sure that the commands there will work, but they seem to be applicable to at least most of the Broadcom 43xx cards.

---

### Post by Bucky Ball on 2013-01-13
Now the other problem is fixed ...

*Thread moved to **Networking & Wireless***

---

### Post by lferg on 2013-01-13
> **audiomick said:**
> There is your clue, what I have marked in red. You need root privileges to run apt-get, same as you do for installing from the software centre or synaptic. Sudo is used in Ubuntu to gain root privileges.


Audiomick, this helped SO much!! I can't thank you enough for that. I just assumed psudo was ones user name.  OMG this helped.

I have everything worked perfectly now.
 
I used this thread to make it happen. 

[http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell](http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell)

---

### Post by audiomick on 2013-01-13
Glad I could help. ;)

---

### Post by Bucky Ball on 2013-01-15
Please mark thread as solved to help others and post a new thread for any further issues/problems/questions. 

Good luck with it. ;)

---


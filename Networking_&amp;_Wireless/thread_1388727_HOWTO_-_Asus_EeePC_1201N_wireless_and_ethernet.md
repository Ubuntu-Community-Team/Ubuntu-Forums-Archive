---
title: "HOWTO - Asus EeePC 1201N wireless and ethernet"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by gadolinio on 2010-01-23
I'm not sure whether this is the right place to post this, but thought it could be useful; it was for me, actually.
In a new Asus EeePC 1201N i couldn't use karmic because the keyboard and the touchpad were frozen, after installation (though they worked normally when in liveUSB).
So i tried jaunty and that problem didn't take place, but it didn't recognize the wireless nor the ethernet/wired connections. There was no way to connect to the internet.
I found this in an eeebuntu forum, and it solved the problem:
[http://forums.eeebuntu.org/viewtopic.php?f=45&t=4968&view=next&sid=b97dd4e6d7d77966526fcadcc6b2ca89](http://forums.eeebuntu.org/viewtopic.php?f=45&t=4968&view=next&sid=b97dd4e6d7d77966526fcadcc6b2ca89)
It was originally meant to work with the asus 1005, but did the job with the 1201N too.
In case the site stops being available before this post does, i'll copy its content here:

----------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------
How to enable eee 1005ha easy install guide for wifi and ethernet

This 1005ha EEEnbr 3.0.1 guide

Credit to the following:
siege (moderator for that great ACPI guide)
[http://www.jfwhome.com/2009/08/06/perfe ... nd-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/")
and guitarholic for the keys

Requirements
1.  Goto this link [http://kernel.ubuntu.com/~kernel-ppa/ma ... v2.6.30.4/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.4/")
download the following:
	linux-headers-2.6.30-02063004-generic_2.6.30-02063004_i386.deb
	linux-headers-2.6.30-02063004_2.6.30-02063004_all.deb
	linux-image-2.6.30-02063004-generic_2.6.30-02063004_i386.deb
copy and save the files a USB
2. Download and install the ISO to USB via UNetbootin to 1005ha eeePC
3. Download the file [http://www.jfwhome.com/wp-content/uploa ... -linux.zip]("http://www.jfwhome.com/wp-content/uploads/2009/08/atheros-wired-driver-1005ha-linux.zip") to USB

Start Guide: 
1.  copy all linux headers to your home directory
2.  Go to accessories>terminal and copy the code: 
sudo dpkg -i linux-headers-2.6.30-02063004-generic_2.6.30-02063004_i386.deb linux-headers-2.6.30-02063004_2.6.30-02063004_all.deb linux-image-2.6.30-02063004-generic_2.6.30-02063004_i386.deb
3.  Copy atheros file to home directory
4.  double click on atheros file>extract to home directory
5.  go to home directory press CTRL+H then go to src folder
6. look for kompat.h, right click on kompat.h then press properties > permissions > change owner access by clicking the Read-only (below owner) and select Read & Write then close
7.  Goto Terminal again and type (Note:change username to user name under your home directory): 
	cd /home/(username)/src
	sudo gedit kompat.h
	press CTRL+F type #define IRQ_HANDLED

		change the following entries to:
			#define IRQ_HANDLED 1
			#define IRQ_NONE 0
		press SAVE
8.  Go back to TERMINAL and type (press enter after each line):
	make 
	sudo make install	
	sudo insmod atl1e.ko
9.  Reboot

FINAL STEP
goto terminal and type:
wget -q [http://eeebuntu.org/Eeebuntu.key](http://eeebuntu.org/Eeebuntu.key) | sudo apt-key add Eeebuntu.key

this will allow your software to update itself
REMINDER: 
1. Do not upgrade to 9.10
2. I am not sure about installing unauthenticatad stuff.  Do a software update and your good to go

For skype the setting for speaker in/out must be hd intel (hw, intel 0) .. internal mic does not work but works well with external mic

Ethernet works well but still yet to test wi-fi
  					---------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------


There's just one thing i did appart from what this guide says.
In step 6:
"6. look for kompat.h, right click on kompat.h then press properties > permissions > change owner access by clicking the Read-only (below owner) and select Read & Write then close"
I also did it with "kcompat.h" (it has a C after the k). It's a user-owned file. Ethernet didn't work before i repeated the modification with this file too.

And then in step 7, it says
"7.  Goto Terminal again and type (Note:change username to user name under your home directory): 
	cd /home/(username)/src
	sudo gedit kompat.h
	press CTRL+F type #define IRQ_HANDLED

		change the following entries to:
			#define IRQ_HANDLED 1
			#define IRQ_NONE 0
		press SAVE"
I did this also to that same "kcompat.h" file.

Well, i hope this is useful to somebody...

---


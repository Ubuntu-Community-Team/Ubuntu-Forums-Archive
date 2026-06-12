---
title: "Quick Question About Drivers ~DESPRATE~"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Da64uu on 2010-06-06
Hey, So I obtained the linux drivers for my card (Realtek RTL8192E). 
I extracted them, CD'd to the extracted folder. Typed sudo su, make, make install, and reboot. In that order. 
 
After rebooting I typed lshw -C network and it showed the card but said that it was unclaimed (From what I understand, no driver assigned) and under "configuration", no mention of a driver. 
 
When making the install I didnt see any errors. How can I check to see where the drtiver is, and assign it to my card? Would it have anything to do with the Wicd Network Manager, in prefrences where it says "WPA Supplicant Driver:" I have it set to "wext"
 
 
 
I would really appriciate any help. Ive been browsing many of these threads about installing my specific driver, but yet to see somebody have the same issue as me.

---

### Post by purelinuxuser on 2010-06-06
Hello, it appears that whatever driver you installed does not claim your wireless card.  I trust you installed the correct one! :) Anyway, try running
```
sudo modprobe rtl8192e
```
or whatever the module is called.  I read somewhere that the RTL8192E driver only supports USB and not PCI cards, but that was back in '08, so maybe things have improved since then.  If this is the case, however, you'll have to use ndiswrapper.

---

### Post by Da64uu on 2010-06-06
> **purelinuxuser said:**
> Hello, it appears that whatever driver you installed does not claim your wireless card. I trust you installed the correct one! :) Anyway, try running
```
sudo modprobe rtl8192e
```
or whatever the module is called. I read somewhere that the RTL8192E driver only supports USB and not PCI cards, but that was back in '08, so maybe things have improved since then. If this is the case, however, you'll have to use ndiswrapper.
 
 
Module not found =\ where might I find the correct name to type?
 
Thanks for writing back!

---

### Post by purelinuxuser on 2010-06-06
Where'd you get those Linux drivers?  I just checked the Realtek driver page ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)) and the only drivers for the RTL8192E are for Windows. :(

---

### Post by Da64uu on 2010-06-06
> **purelinuxuser said:**
> Where'd you get those Linux drivers? I just checked the Realtek driver page ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)) and the only drivers for the RTL8192E are for Windows. :(
 
 
I got them from this thread. I also tried some from a similar thread with a newer / older driver cant remember where each came from.
 
[http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038)
 
 
 
**_I didn't do_** because it wasnt listed in the readme. 
 
sudo apt-get install git-core
cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git
sudo cp -av firmware/RTL8192E /lib/firmware/
*RESTART WILL WORK*  ONLY x86
 
 
I have no clue what this does...
 
 
Thanks for your reply. Sorry for my limited reply, im at work. I can respond better in about 3-4 hours when im home with a correct link to where I got the driver that I installed.

---

### Post by Da64uu on 2010-06-06
Look man... Honestly.. My computer is 64 Bit.. I did the command line to tell me what it is and it is showing 32 Bit linux installed.. The driver I installed was supposed to be 64 Bit. . Might this honestly be a problem? Does the 64 bit driver match the version of linux, or the specs of the computer?

---

### Post by purelinuxuser on 2010-06-06
Your best bet is probably ndiswrapper.  Plug into Ethernet, and install the following packages:

[LIST]
[*]ndiswrapper-utils-1.9
[*]ndiswrapper-common
[*]ndisgtk
[/LIST]
Then download the **Windows XP** driver (seriously) for your card.  Extract the exe, and look for an *.inf file (usually in a folder called DRIVER).  Then go to System > Administration > Windows Wireless Drivers, click install, and browse for the *.inf file you found earlier.  Then reboot- hope this helps :D

---

### Post by Da64uu on 2010-06-06
Thanks again for your reply, unfourtanatly ndiswrapper isnt an option for me, I need the "Monitor Mode" which is not compatible with Ndiswrapper =\\ any other way?

---

### Post by northd_tech on 2010-06-06
Hi Da64,

There are BIG differences between the Realtek 8192E and its "cousins" like the 8192SE, etc., and between the 32-bit and 64-bit versions.  I've had a HELL of a time getting 64-bit Realtek 8192E to work (still not working several months later).  I'm planning on working on that laptop tonight, but its owner is busy packing for a week long vacation (so that the owner might be able to use WiFi under something other than Widows 7 on the road).

On your driver troubles, can you post the results of the following terminal commands here?

```
lsmod

sudo lshw -C network

lspci

ifconfig

iwconfig

uname -a

```I don't know if you have read these threads, but they might have something helpful for you:

[http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038)

[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)

---

### Post by northd_tech on 2010-06-06
> **Da64uu said:**
> 
**_I didn't do_** because it wasnt listed in the readme. 
 
sudo apt-get install git-core
cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git
sudo cp -av firmware/RTL8192E /lib/firmware/
*RESTART WILL WORK*  ONLY x86
 
 
I have no clue what this does...
 
That looks slightly similar to all that firmware copy stuff that I tried (**unsuccessfully**) with a 64-bit Realtek 8192E wireless on a Toshiba Satellite P505D laptop months ago.

We might get those modules to build successfully for you with that newer sourcecode, but the firmware thing might still be a problem and WiFi won't be recognized.  It has been months since I looked at this Realtek trouble though.  It might be worth searching for "realtek 8192E firmware" or else emailing Realtek directly- there should be links on one or both of those threads that I linked above.

---

### Post by Da64uu on 2010-06-06
> **northd_tech said:**
> That looks slightly similar to all that firmware copy stuff that I tried (**unsuccessfully**) with a 64-bit Realtek 8192E wireless on a Toshiba Satellite P505D laptop months ago.
 
We might get those modules to build successfully for you with that newer sourcecode, but the firmware thing might still be a problem and WiFi won't be recognized. It has been months since I looked at this Realtek trouble though. It might be worth searching for "realtek 8192E firmware" or else emailing Realtek directly- there should be links on one or both of those threads that I linked above.
 
 
Thanks for your help bro! The command I needed was 
modprobe r8192e-pci
 
Im so glad you linked me, I looked over that thread like 5 times. Thanks for you guy's help =]]

---

### Post by purelinuxuser on 2010-06-06
Don't forget to mark this thread [SOLVED] :)

---


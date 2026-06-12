---
title: "hp pavilion ze4900 can't see wireless card w/ ubuntu 9.10"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Bernie Gallagher on 2010-07-03
I just installed Ubunto 9.10 on my HP Pavilion ZE9400 laptop (more specifically a ze4930us) that was formerly running Windoze XP. Right now, I'm using my Win 7 desktop machine. The problem with the laptop is that Linux can't connect to my wireless network. It seems that it can't see the wireless card. When I tap the button on the laptop case, a little blue light normally switches on and off to indicate whether the wireless card is enabled or not, but that light doesn't come on. I suppose I need a HP/Ubuntu driver. Any advice, links, etc?
 
BTW, I also went to the HP site to download a driver, but Linux isn't one of the OSs that they support and have no drivers.

---

### Post by thomas144 on 2010-07-03
A similar thing happened to my laptop. It's a different model (Dell Inspiron 1545), but I had the same problem. When I booted up the computer, my wireless didn't work and Ubuntu didn't seem to be able to use my wireless card. I was able to fix it by installing a driver for my wireless card. We have to firgure out what kind of wireless card you have and install the driver. I'm far from an expert, but I might be able to give you some help.

---

### Post by thomas144 on 2010-07-03
We can make sure that your wireless card is turned on. Start up you Ubuntu laptop and log in. From the top menu, go to Applications, then Accessories, and Terminal. You should see a window with a white background and some text pop up. Type in:
```
rfkill list
```
and hit enter. What does it say?

---

### Post by Bernie Gallagher on 2010-07-03
It says:
 
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

---

### Post by thomas144 on 2010-07-03
That basically means that you wireless card is not turned off. Next, we'll see if we can locate any drivers for your wireless card. Go to System > Administration > Hardware Drivers. If you are prompted for your password, type it in. A windows should pop up. What does it say?

---

### Post by Bernie Gallagher on 2010-07-03
It says:
 
No proprietary drivers are in use on this system.

---

### Post by thomas144 on 2010-07-03
Are there any drivers that are listed that you can activate? For example, is there a driver or drivers listed after "Proprietary drivers do not have public source code that Ubuntu developers are free to modify....Ubuntu cannot fix or improve these drivers."

---

### Post by Bernie Gallagher on 2010-07-03
No drivers are listed on that screen below that message.

---

### Post by thomas144 on 2010-07-03
Okay. You might be able to install the drivers if you connect to the Internet. Can you connect your laptop to the Internet with a wired connection?

---

### Post by Bernie Gallagher on 2010-07-03
Yeah, I can connect if I hardwire to my router.  
 
BTW, thanks for the help!

---

### Post by thomas144 on 2010-07-03
Wait! I didn't get your wireless working yet, did I? Once you've connected to the Internet through the wired connection, go to System > Administration > Hardware Drivers. Are there any drivers there now?

---

### Post by thomas144 on 2010-07-03
I'll check back here in a few days. If you're satisfied with just having a wired connection, that's fine. If not, I'll be willing to help. Goodbye for now.

---

### Post by Bernie Gallagher on 2010-07-03
I'd really prefer to use my laptop over my wireless network, but it can wait until you're back. 
Anyway, I was poking around and found something interesting:
 
I went to System >Administration > Network Tools and then chose Wireless Interface (wlan0) from the Network Device drop-down list. 
 
It says the device is Inactive, but there's no button to acticate it. Is that something that needs to be done from the command prompt?  I can do basic Windoze admin stuff because I know DOS, but I'm totally clueless with raw Linux...

---

### Post by thomas144 on 2010-07-03
Oops. It appears that I'm still around. Did you check for drivers while you were connected to the network?
The fact that the wireless card is inactive probably is because Ubuntu doesn't have the right driver.

---

### Post by Bernie Gallagher on 2010-07-03
I went to the HP site to find a driver, but HP doesn't support any flavor of Linux.  Only Windoze...

---

### Post by thomas144 on 2010-07-03
Sorry, I was accidentally confusing you. I mean check for drivers in System > Administration > Hardware Drivers, not on HP's web site.

---

### Post by Bernie Gallagher on 2010-07-03
Nope.  I'm connected via hardware, but it still says: No proprietary drivers...

---

### Post by ajgreeny on 2010-07-03
Whilst connected by the cable, do a full update of the system.  In terminal type ```
sudo apt-get update
sudo apt-get upgrade
```
as separate commands, wait for it to finish, then try again with the **Hardware Drivers** dialog.  The updated system may have more luck with drivers.

---

### Post by thomas144 on 2010-07-03
I'm not sure how else to help you. If you really want to be able to use your wireless, I suppose you can get help from someone else. I still might come back to read if anything new happened here in a few days. Goodbye for now.

---

### Post by Bernie Gallagher on 2010-07-03
> **ajgreeny said:**
> Whilst connected by the cable, do a full update of the system. In terminal type ```
sudo apt-get update
sudo apt-get upgrade
```
as separate commands, wait for it to finish, then try again with the **Hardware Drivers** dialog. The updated system may have more luck with drivers.
 
Making progress :-)
 
I did that and it found a new driver in Hardware Drivers: Broadcom B43 Wireless Driver
 
But when I clicked on Activate, I got the following error:
 
System Error: Failed to lock /var/cache/apt/archives/lock

---

### Post by roosh on 2010-07-03
I think that something updater/installer is open. Close any open programs and try again. If it doesn't work try to reboot and try again.

---

### Post by Bernie Gallagher on 2010-07-03
Oh wait...  Ubuntu just forced itself to reboot a moment ago.  When it started, the little blue wireless light came on!  Then it said it detected my wireless network name!  I'm now downloading Flash for Ubuntu so I can watch a YouTube video!  w00t!  Thanks a bunch!!!!

---

### Post by roosh on 2010-07-03
Your welcome. :) Please add [solved] to the thread header.

---

### Post by Bernie Gallagher on 2010-07-03
Okay :-)

---

### Post by roosh on 2010-07-03
Click on "Thread Tools" and then you will see "mark this thread as solved"

---


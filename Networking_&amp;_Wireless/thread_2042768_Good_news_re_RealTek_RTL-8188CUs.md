---
title: "Good news re RealTek RTL-8188CUs"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2012-08-15
There have been some posts here about adapters using RealTek's 8188CUs chips  being recognized but not working.  You enter the pass phrase, it thinks about it for a minute or so and asks for the pass phrase again and repeats.  I've used and recommended downloading and installing RealTek's driver and blacklisting the 'built-in' driver if necessary.  That solution worked for me.

The good news is that on 12.04, Xubuntu 12.04 and Ubuntu 12.10, after updating my Edimax EW7811Un  appears to be working with the built-in driver with no issues and no file edits.  This adapter - and presumably its clones - is IMO a great solution for older portables with B or G speed wireless or portables with problematic wifi chipsets.  It only protrudes from the USB port about 1 cm.  My only niggle is that the blue activity light stays on continuously rather than flashing when active.  I believe someone had a file edit that would fix the light-on-continuously problem, or there's always black tape :wink:.

---

### Post by noconaway on 2012-08-20
Hey, thanks for posting this! I'm new to ubuntu and having exactly this issue. But being new to ubuntu, i'm afraid i don't know how to blacklist the built in driver. I'm sure this is a somewhat simple task, but i can't seem to figure it out.

Any help is greatly appreciated!
nc

edit: i am running 12.04

---

### Post by kurt18947 on 2012-08-20
> **noconaway said:**
> Hey, thanks for posting this! I'm new to ubuntu and having exactly this issue. But being new to ubuntu, i'm afraid i don't know how to blacklist the built in driver. I'm sure this is a somewhat simple task, but i can't seem to figure it out.

Any help is greatly appreciated!
nc

edit: i am running 12.04

Hi

Is your built-in driver not working in 12.04?  Is your system fully updated?  My built-in driver **wasn't** working until recently but is working properly now (the blue light doesn't flash though - it's on steady)so I don't need to blacklist anything.  If your built-in driver is not working, you could try RealTek's driver.  When the built-in driver wasn't working in 12.04, I installed Realtek's driver but did not have to blacklist the built-in driver in order for the USB dongle to work in Ubuntu 12.04.  With Mint 13 - based on 12.04 - I installed Realtek's driver but the adapter still didn't work.  In that case I did have to blacklist the built-in driver in order for the USB dongle to function.  Bear in mind my experience is only with the Realtek RTL-8188CUs used in Edimax EW-7811Un.  If you have a different adapter or chip set,  I don't know that my experience applies.

---

### Post by noconaway on 2012-08-20
My built in driver does seem to be working, and i'm updated as of last night. So, to try out blacklisting the built in driver, i followed these steps:
[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

and now my connection is running smoothly!

Essentials pasted here:
> Step 0: get a network cable

In order to solve this issue you will need Internet.  Get a network cable which you can physically connect to your router.  Once you have Internet access the following steps are much easier to follow.

Step 1: make it easy to open terminal window in a specific folder location

This step is important since it makes several other steps easier to manage.

The instructions on how to do it are given here.  You simply need to open a terminal window (press CTRL+ALT+T), and type:
sudo apt-get install nautilus-open-terminal

From now on, whenever you want to open a new terminal window in a specific folder &#8211; you simply right-click that folder (from the folder which is a level above it) and choose &#8220;Open in Terminal&#8221;

Step 2: Download the latest edimx drivers
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

Step 3: Install the new driver

Go to the download folder and open (using right click, if you followed step 0) the terminal for the folder &#8220;RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922&#8243;.  Then run:

sudo bash install.sh

(note 1: it will ask for your user&#8217;s password &#8211; as will any command which is using the sudo = super user do prefix)
(note 2: in order to paste in the terminal, use ctrl+shift+v instead of just ctrl+v as is in the GUI and other editors)

Step 4: blacklist the old driver

Next, we want to edit /etc/modprobe.d/blacklist.conf Getting there using the GUI wouldn&#8217;t work, because ubuntu wouldn&#8217;t let us save the changes we will make. Instead, just open the terminal and type:
sudo gedit /etc/modprobe.d/blacklist.conf

Go to the end of the file and add the line:

blacklist rtl8192cu

(thanks goes to icracked for the advise)

Step 5: remove and re-insert the network USB (and reboot)

Once done &#8211; I was finally able to see and connect to my home Internet network.

At this point, some people also said reboot helped, so if you got this far, why not do that too&#8230;

---

### Post by labidus on 2012-10-03
Sorry finally I resolved my issue..

---


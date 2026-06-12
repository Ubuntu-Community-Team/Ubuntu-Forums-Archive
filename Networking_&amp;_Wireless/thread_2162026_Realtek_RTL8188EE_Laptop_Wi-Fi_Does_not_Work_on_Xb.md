---
title: "Realtek RTL8188EE Laptop Wi-Fi Does not Work on Xbuntu 12.04"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by tjones10 on 2013-07-12
I am unable to get the Realtek RTL8188EE Wi-Fi adapter on my HP ENVY 17t-j000 Quad Edition laptop to work on Xbuntu 12.04. The Network Manager applet does not show any "Wireless Network" options, nor are any networks listed. When I have searched the web I have found very limited information about running this card on Linux. A [previous post]("http://ubuntuforums.org/showthread.php?t=2158123&highlight=RTL8188EE") on this forum seems to deal with a similar issue but there were no responses to that thread.

I have attempted to use NDISwrapper to load [a windows driver ]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=ob-117672-1")for the card, as per [the instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on the Ubuntu wiki.. A usb wi-fi adapter works. My current Xbuntu install is fresh and I have had this laptop for less than a week. NDISwrapper loaded the driver but the card did not work. I have also tried to use the Wi-Fi on other Linux distros, but none of them have worked. The Wi-Fi worked on the (now removed) windows 8 install that came with the laptop.

The relevant output of lspci is as follows

*0.8:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01) * 
*0.9:00.0 Unassigned class [ff00]: Realtek **Semiconductor Co., Ltd. Device 5227 (rev 01)*

The output of iwconfig on Xbuntu is as follows 
[I]
lo             no wireless extensions 
eth0         no wireless extensions

[/I]
The output of iwlist scan is as follows

[I]lo             Interface doesn't support scanning.
eth0         Interface doesn't support scanning.[/I]

Thanks for your help in advance.

---

### Post by varunendra on 2013-07-13
[SIZE=3][COLOR="#800000"]=====================================
**EDIT:** The official driver from Realtek site is now outdated and not compatible with the latest kernels. If the patch suggested in step 3 in [this post]("http://ubuntuforums.org/showthread.php?t=2169602&p=12770984#post12770984") doesn't help compiling it without errors, please try the solution by Dr. Chili555 in post #11, which is probably a better fix anyway.
=====================================[/COLOR][/SIZE]

> **tjones10 said:**
> I am unable to get the Realtek **RTL8188EE** Wi-Fi adapter......
.....
*0.8:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device **8179** (rev 01) * 

If you are sure about the chip, then you should be able to get it working with the proprietary Linux driver downloaded directly from realtek's site (RTL8188CE). That package is actually a collection of some common realtek drivers including RTL8188EE.

But to install it, or any other driver, you must first completely purge the ndiswrapper driver (including its configuration folder in /etc directory). Once done, install the above driver as -

[INDENT]**1)** Download it from : [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722) and copy it to your desktop (it's about 12 MB download).

**2)** Right-click the downloaded file (linux_mac80211_0012.0207.2013.tar.bz2) > "Extract here". This will extract a folder named "rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013" on your desktop.

**3)** Open a terminal (Ctrl+Alt+T) and run following commands :
```
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install
```

**4)** Reboot or manually load the driver with -
```
sudo modprobe -v rtl8188ee
```[/INDENT]

Let me know if you need more help with any of the steps above, or if there are any errors in the process.

---

### Post by tjones10 on 2013-07-13
That driver worked. Thanks for your help.

---

### Post by varunendra on 2013-07-13
> **tjones10 said:**
> That driver worked. Thanks for your help.

You're welcome ! Hope it works nicely. :)

---

### Post by jaime3 on 2013-09-02
> **tjones10 said:**
> I am unable to get the Realtek RTL8188EE Wi-Fi adapter on my HP ENVY 17t-j000 Quad Edition laptop to work on Xbuntu 12.04. The Network Manager applet does not show any "Wireless Network" options, nor are any networks listed. When I have searched the web I have found very limited information about running this card on Linux. A [previous post]("http://ubuntuforums.org/showthread.php?t=2158123&highlight=RTL8188EE") on this forum seems to deal with a similar issue but there were no responses to that thread.

I have attempted to use NDISwrapper to load [a windows driver ]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=ob-117672-1")for the card, as per [the instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on the Ubuntu wiki.. A usb wi-fi adapter works. My current Xbuntu install is fresh and I have had this laptop for less than a week. NDISwrapper loaded the driver but the card did not work. I have also tried to use the Wi-Fi on other Linux distros, but none of them have worked. The Wi-Fi worked on the (now removed) windows 8 install that came with the laptop.

The relevant output of lspci is as follows

*0.8:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01) * 
*0.9:00.0 Unassigned class [ff00]: Realtek **Semiconductor Co., Ltd. Device 5227 (rev 01)*

The output of iwconfig on Xbuntu is as follows 
[I]
lo             no wireless extensions 
eth0         no wireless extensions

[/I]
The output of iwlist scan is as follows

[I]lo             Interface doesn't support scanning.
eth0         Interface doesn't support scanning.[/I]

Thanks for your help in advance.

Hi sorry for getting out of subject but how does this laptop perform in xubuntu 12.04? Does everything work? Including intel drivers?

---

### Post by john_richardson2 on 2013-09-23
Can you instruct me on how to purge the driver and folder?

---

### Post by varunendra on 2013-09-23
> **john_richardson2 said:**
> Can you instruct me on how to purge the driver and folder?

If you have not tried installing ndiswrapper (which you don't seem to have), just follow the instruction steps 1 to 4 and ignore the ndiswrapper part. If there are any errors (I suspect there may be, due to kernel changes), post back in your original thread : [http://ubuntuforums.org/showthread.php?t=2176052](http://ubuntuforums.org/showthread.php?t=2176052)

---

### Post by Mike_H. on 2013-10-21
I created an account just to be able to log in and thank you as this post helped me as well!

I tried to get this card to work for about a week... then gave up. That is until I tried again just now cause I'm stubborn!

---

### Post by varunendra on 2013-10-22
> **Mike_H. said:**
> I created an account just to be able to log in and thank you as this post helped me as well!

That is so nice of you Mike !

Thanks for the feedback, and Welcome to the forums !! :)

---

### Post by Reaudribion on 2013-12-31
Hi, I tried this and got this on the Make command

jan@jan-Satelliter-C55D-A:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.8.0-34-generic/build M=/home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-34-generic'
  CC [M]  /home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/jan/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-34-generic'
make: *** [all] Error 2
jan@jan-Satelliter-C55D-A:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ 



What can I do with this?

---

### Post by chili555 on 2013-12-31
Please try the procedure here: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

---

### Post by Reaudribion on 2013-12-31
That worked, thanks!

---

### Post by mosaphire on 2014-01-10
Hy! I have a new HP 15 Pavilion Notebook. I removed Windows 8 and installed Ubuntu 12.04. I have the same problem with the wifi connection, I tried your steps, and downloaded the drivers but in step 3:
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install

The terminal says: the folder or directory doesn't exists. Then it also says: there's no makefile.

What can I do? I have RTL8188EE

---

### Post by chili555 on 2014-01-10
> **mosaphire said:**
> Hy! I have a new HP 15 Pavilion Notebook. I removed Windows 8 and installed Ubuntu 12.04. I have the same problem with the wifi connection, I tried your steps, and downloaded the drivers but in step 3:
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install

The terminal says: the folder or directory doesn't exists. Then it also says: there's no makefile.

What can I do? I have RTL8188EEI recommend the procedure in my post #11 above instead.

---

### Post by varunendra on 2014-01-10
> **chili555 said:**
> I recommend the procedure in my post #11 above instead.

+1

---

### Post by mosaphire on 2014-01-12
Thank you for your tips. I've tried your way but in the first step:
sudo apt-get install linux-headers-generic build-essential

An error occured: 

 fglrx-pxpress
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm completely new in that stuff, thank you so much! :)

---

### Post by chili555 on 2014-01-12
> **mosaphire said:**
> Thank you for your tips. I've tried your way but in the first step:
sudo apt-get install linux-headers-generic build-essential

An error occured: 

 fglrx-pxpress
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm completely new in that stuff, thank you so much! :)fglrx is a video driver and I doubt this has anything to do with wireless. You might just try again; I got a similar error on one of my machines during an update and trying again seems to have fixed it. You might try:```
sudo apt-get update
sudo apt-get upgrade
```Then try again. Obviously, if you get any interesting errors or warnings, post them here.

---

### Post by mosaphire on 2014-01-12
Thank you so much! I've tried again and the result is the same error with fglrx. Everything I try to install shows me the same error. :(

---

### Post by chili555 on 2014-01-12
> **mosaphire said:**
> Thank you so much! I've tried again and the result is the same error with fglrx. Everything I try to install shows me the same error. :(I have Googled the specific error and the proposed fixes sound pretty scary to me; however, I'm not a student of fglrx or any video drivers, for that matter. For instance: [http://askubuntu.com/questions/290042/ati-4850-on-13-04-64bit](http://askubuntu.com/questions/290042/ati-4850-on-13-04-64bit)

I suggest you address the show-stopper video issue here first: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by mosaphire on 2014-01-13
Thank you for everything, I will keep on searching the solution. If I get it, I'll post here. Thanks! You make a really good work with this forum.

---

### Post by azhar.basit on 2014-03-04
I want to add a comment for me the "unsupported drivers" from post # 2 [COLOR=#000000]: [/COLOR][http://152.104.125.41/downloads/down...oads=true#2722]("http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722")[COLOR=#000000] 
actually worked better than the backported drivers suggested in post # 11.

I can connect with both but the backported drivers give me a very unstable wifi connection while the drivers from [/COLOR][COLOR=#000000]: [/COLOR][http://152.104.125.41/downloads/down...oads=true#2722]("http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722")[COLOR=#000000]  work perfectly.  No drops.

[/COLOR]

---

### Post by varunendra on 2014-03-04
Thank you so much for the feedback Azhar. It is valuable and appreciated.

Could you please also confirm which kernel version you are on? Because as far as I remember, the one from Realtek was failing to build on kernel 3.11 and later ones. Which means either their driver has been updated, or you are using kernel 3.8 or earlier.

To confirm the kernel version, please post the output of the following command -
```
uname -mr
```

And something that you should be aware of - The backported driver suggested in post #11 was from kernel 3.11, while we have seen that the one from 3.12 works much better. So -

***** If you upgraded to **kernel 3.11** (comes by default on a fresh installation of 12.04.4), you might need to install the backported version 3.12 (available [here]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/")).
***** If you upgraded to **kernel 3.12** or later, your native driver will already be probably the best available, no need to install anything.

Once more, I appreciate your taking time to share your experience with us. :)

---

### Post by azhar.basit on 2014-03-15
Ooops I did not see this reply, hence the late reply.  Thanks for the follow up Varun.  And yes you are right according to "uname -mr" 

I have 3.8.0-37-generic x86_64

Which is a surprise as whenever I am given a new kernel option to update from the ubuntu "Update Manager" I always update.  

Thank you Varun for pointing out which kernel version works with the backported drivers.

---


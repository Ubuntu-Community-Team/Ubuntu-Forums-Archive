---
title: "r8712u for my adapter?"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Labhrain on 2012-12-17
I have a USB wireless adapter with id 07d1:3304.  So, the chip is rlt8192su.  I am running ubuntu 12.10 64-bit. 

I was able to get my Broadcom 4311 running with very little effort (just minor tweak to get the  b43 going.)  But, I have been working on this Realtek situation for a few days, but to no avail.  I've done a lot of reading and trying things, and from what I'm reading (if I'm understanding it correctly,) the proper driver to use now is called r8712u.  Is this correct?  If so, how do I get the device and the driver to meet up?  It just not happening.  When I modprobe for r8712u, I get nothing at all.

Any help is appreciated.  Thanks!

---

### Post by ahallubuntu on 2012-12-17
Did you try downloading  and building the latest driver from Realtek for the 8192su?  You'll have to do it in a terminal:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

You may have to blacklist the existing driver.

---

### Post by Labhrain on 2012-12-17
> **ahallubuntu said:**
> Did you try downloading  and building the latest driver from Realtek for the 8192su?  You'll have to do it in a terminal:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

You may have to blacklist the existing driver.

I've tried this three times.  It just doesn't seem to work.  I don't think that it works for this kernel (3.5.0-19-generic.)  It states it's for Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2.  As far as blacklisting an existing driver, I don't even see an existing driver for this.  It shows up in lsusb, but no driver at all appears to be "attached" to it.   ifconfig -a doesn't show this wlan at all.

I'm pretty new at all this, so I may be missing something here.  Thanks.

---

### Post by ahallubuntu on 2012-12-17
OK - you might start here:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by chili555 on 2012-12-17
I think you'll need to add the device ID to r8712u as here: [http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html)

Please note post #3 and post #8:> the instructions worked just the same and the wireless usb card works perfectly.Thus was done in 2010, so you may have to adapt somewhat. Post back if we can help.

---

### Post by Labhrain on 2012-12-17
> **chili555 said:**
> I think you'll need to add the device ID to r8712u as here: [http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html)

Please note post #3 and post #8:Thus was done in 2010, so you may have to adapt somewhat. Post back if we can help.

That's the one of the threads I poured over for days, and I followed this particular thread to a "T" about three times trying to make it work.  The problem seems to be that it has you download the drivers from the Realtek site, and those drivers don't appear to be correct for 12.10 kernel.  I can't find anything recent for this, and I don't know where to go from here.  For days, I feel I've really done my due diligence as far as searching high and low for information on this, and really, really trying to make this work.   Not sure what else to do at this point.

Thanks.

---

### Post by ahallubuntu on 2012-12-17
> **Labhrain said:**
> That's the one of the threads I poured over for days, and I followed this particular thread to a "T" about three times trying to make it work.  The problem seems to be that it has you download the drivers from the Realtek site, and those drivers don't appear to be correct for 12.10 kernel.  I can't find anything recent for this, and I don't know where to go from here.  For days, I feel I've really done my due diligence as far as searching high and low for information on this, and really, really trying to make this work.   Not sure what else to do at this point.

Thanks.

I can't help you more until you provide the basic information asked for in the link above.  Plus, I don't know where in the process you are having problems.  All you are telling us is your assessment of what you did.  From that, I can only make guesses.

I have built the 8192CU driver (may not be exactly the same as your driver) from the Realtek website, on Ubuntu 12.10, and it worked fine.  Are you getting errors during the make process?  Is the driver loading?  Was an old driver used at all?  See - we don't have much to go on here.

---

### Post by Labhrain on 2012-12-17
Okay, I decided to try this all again.  When I get to the part where you run "make" I get the following errors:

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/labhrain/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

So, I can't go on from there.  I've tried to figure out what causes this error, but I don't know what it is or how to fix it.

---

### Post by chili555 on 2012-12-17
> **Labhrain said:**
> That's the one of the threads I poured over for days, and I followed this particular thread to a "T" about three times trying to make it work.  The problem seems to be that it has you download the drivers from the Realtek site, and those drivers don't appear to be correct for 12.10 kernel.  I can't find anything recent for this, and I don't know where to go from here.  For days, I feel I've really done my due diligence as far as searching high and low for information on this, and really, really trying to make this work.   Not sure what else to do at this point.

Thanks.Would you try an experiment for us?```
sudo su
modprobe r8712u
echo -n "07d1 3304" > /sys/bus/usb/drivers/r8712u/new_id
exit
```Now does it come to life?```
iwconfig
```

----------

Reference:```
$ ls /sys/bus/usb/drivers/r8712u
bind  module  *new_id*  remove_id  uevent  unbind
```

---

### Post by Labhrain on 2012-12-17
Chili, yes that has worked.

Here is the output of ifconfig:

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am going to configure it and see how it goes.

When I did modprobe earlier, without su, it didn't work.   Perhaps this has been the issue all along?

Thank you both so very much!

EDIT:

So far, so good.  It's remaining up.  I connected to my Freenas file server (which is kind of slow) but I had good results with that, and with surfing the Web.  I noticed in iwconfig for this adapter that it's not getting the speed it should (although faster than my built-in adapter,) but I'll look around to see how to tweak for that, if it's possible to do so.

---

### Post by ahallubuntu on 2012-12-17
> **Labhrain said:**
> Okay, I decided to try this all again.  When I get to the part where you run "make" I get the following errors:

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/labhrain/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

So, I can't go on from there.  I've tried to figure out what causes this error, but I don't know what it is or how to fix it.

You might need to install some Kernel stuff.  Try this:


```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
```


and then try building the driver again.

---

### Post by chili555 on 2012-12-17
Awesome! In order to make it persistent, please do:```
sudo gedit /etc/rc.local
```At the end, above exit 0, add two lines:```
modprobe r8712u
echo -n "07d1 3304" > /sys/bus/usb/drivers/r8712u/new_id
```Proofread carefully, save and close gedit.

There is very little information about this device out there in the google-sphere, as you know. Please mark the thread Solved using thread tools at the top so the searchers will benefit from your experience.

Keep us posted, please.

---

### Post by chili555 on 2012-12-17
> **ahallubuntu said:**
> You might need to install some Kernel stuff.  Try this:


```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
```


and then try building the driver again.And then you get:> rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type

---

### Post by Labhrain on 2012-12-17
Thanks again to both of you.  

I went ahead and updated the build-essential/headers stuff without issue for future need.

Thanks for the instructions for making it persistent.  I didn't want to have to modprobe after every reboot :)    I rebooted to test it and it worked fine.

I will go ahead and mark this as solved.

I am guessing that I had the right driver available the whole time, but just needed to get it going with the root modprobe.  Is that about right?

Thanks for all the great help!

---

### Post by chili555 on 2012-12-17
> but just needed to get it going with the root modprobe. Is that about right?Not quite. You needed the new_id part as well so that the driver recognizes and drives your device. One can sudo modprobe anything they want, but it may or may not recognize your device. The stock, in-kernel driver does not.

---

### Post by Labhrain on 2012-12-17
> **chili555 said:**
> Not quite. You needed the new_id part as well so that the driver recognizes and drives your device. One can sudo modprobe anything they want, but it may or may not recognize your device. The stock, in-kernel driver does not.

Gotcha.  Thanks for the explanation.

Oh, and I found a thread that showed me how to change the rate, so it's now running at a much higher speed.  I used iwconfig wlan1 rate 150M.

---

### Post by bogan on 2012-12-18
Hi!, **Labhrain** & **Chilli**,

@**labhrain**,  Would you please Post a link for: "a thread that showed me how to change the rate," maybe it would help others, as well as me.
 
I have a similar Realtek RTL8191SU internal USB Lan Adapter, but with a different ID: "13d3:3306".
 I got it to run - after a fashion - with a lot of help from Chilli555 - first with 9.10, then with 11.10 & 12.04. With 12.10 it runs, also after a fashion, from the included kernel r8712u driver.

" After a fashion" because it is very unpredictable, very slow, often drops the connection, or only detects it when another, external USB Dongle is plugged in. 
Sometimes it is already connected when the log-in screen appears, at others it can take several scanning attempts, over several minutes, before finally giving up or establishing contact.

This behaviour is the same whether running the downloaded Realtek rtl8712u driver, or the default kernel equivalent.

**@chilli555**, I tried your solution for this thread, on the basis it could hardly be worse,
With 12.10, I found the module was not at:
```
/lib/modules/2.6.28-18-generic/kernel/drivers/net/wireless/r8712u.ko
```But at:```
/lib/modules/3.5.0-21-generic/kernel/drivers/staging/rtl8712/r8712u.ko
```When I tried to edit the: /etc/rc.local file it did not exist and gksudo gedit was not able to save text to the '/sys/bus/usb/drivers/r8712u/new_id' file.
Eventually I got it to enter the ID from a root terminal. At the moment, things seem much the same.

Is it OK to create the /etc/rc.local file with just the 'modeprobe' & 'echo'  cmds?

Should I expect this modification to give an improvement.?

Chao!, **bogan**.

---

### Post by chili555 on 2012-12-18
> I have a similar Realtek RTL8191SU internal USB Lan Adapter, but with a different ID: "[COLOR="Red"]13d3:3306[/COLOR]".Your device is covered by default in r8712u in 12.10. You don't need any of this.> When I tried to edit the: /etc/rc.local file it did not exist If you have no /etc/rc.local file, then something is terribly wrong. I'd assume you mis-typed. However, you needn't fix what isn't an issue for your device.>  Would you please Post a link for: "a thread that showed me how to change the rate," maybe it would help others, as well as me.He already told us:```
 iwconfig wlan1 rate 150M
```Your interface is probably wlan0 and you will need to precede the command with sudo.> Should I expect this modification to give an improvement.?No. You needn't add your device ID to the r8712u file. It's already there.

Your instability is an entirely different issue from Labhrain's, which is, how to get the driver to recognize the device at all. I suggest you start your own new thread.

---


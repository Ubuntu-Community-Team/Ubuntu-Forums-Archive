---
title: "Installing an Asus N13 USB Wireless receiver"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by Stupendous man on 2011-05-24
Hello,

Can I trouble someone to provide some assistance on how to properly install this  thing and get it to work? I have been all over the web trying all sorts of different "tutorials", but most of them start off okay, and then I get errors in the terminal, or the commands in the tutorials become specific to one person's particular system, and I can go no further...


I really want to use Ubuntu 11 on a system that currently is running the reprehensible Windows Vista, and if I could just get this Wireless receiver to work, I would be able to format Vista into oblivion. 


So, can someone start at the very beginning, and help me through this? Please keep in mind that I am as green as a leprechaun when it comes to Ubuntu, so please make instructions verbose and geared to a layperson, if it wouldn't be too much trouble.

So, the unit is plugged in, and ready to go. What's first?

---

### Post by drunkfish on 2011-05-24
Prepare the driver first, if the ubuntu can not identity it.

[http://www.asus.com/Networks/WiFi_Networking/USBN13/#download](http://www.asus.com/Networks/WiFi_Networking/USBN13/#download)

---

### Post by chili555 on 2011-05-24
The file that is linked will not compile in Ubuntu 11.04 without some major changes as well as installing build-essential and linux-headers-generic. Maybe there is an easier way. Please open a terminal and run and post:```
lsusb
```That command, as you might guess, asks the system to **list** all the **USB** devices. Post the result and we'll move forward.

---

### Post by Stupendous man on 2011-05-24
Okay. I will post those in a few hours when I get home from work. Thanks!

---

### Post by Doorknob on 2011-05-24
I will be also watching for the replies, I have my Asus Usb N13 up and running but can't get it to use the N band.

---

### Post by Stupendous man on 2011-05-24
Okay, there were three entries, but I think the relevent one is this:

Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter

The other two were linux foundation 1.1 and 2.0 root hubs

Ready for instruction!
:)

---

### Post by chili555 on 2011-05-24
Good news! Your device is supported out of the box with the module rt2870sta.

Bad news! It is also claimed by a conflicting driver rt2800usb; viz:```
$ modinfo rt2870sta | grep 1784
alias:          usb:v0B05p[COLOR="Red"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2800usb | grep 1784
alias:          usb:v0B05p[COLOR="Red"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```All we need to do is blacklist a few things and we'll be all set:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Just for good measure, let's load rt2870sta explicitly:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and tell us how marvelously your wireless is working.

NB: If you are running later versions of Ubuntu, say 10.10 or later, this works perfectly. If earlier, a devious trick is required.

---

### Post by Stupendous man on 2011-05-24
It works!
I can't believe it actually works!
Now to format and reinstall ununtu exclsively!

thank you so much!

---

### Post by 1vel on 2011-05-24
THANK YOU CHILLI555


i also have an asus n13 . IT WORKS AT ONCE

i am new in this forum (and ubuntu) ,i did register for about one hour ago

THANKS

---

### Post by 1vel on 2011-05-24
:popcorn:> **chili555 said:**
> Good news! Your device is supported out of the box with the module rt2870sta.

Bad news! It is also claimed by a conflicting driver rt2800usb; viz:```
$ modinfo rt2870sta | grep 1784
alias:          usb:v0B05p[COLOR=Red]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2800usb | grep 1784
alias:          usb:v0B05p[COLOR=Red]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```All we need to do is blacklist a few things and we'll be all set:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Just for good measure, let's load rt2870sta explicitly:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and tell us how marvelously your wireless is working.

NB: If you are running later versions of Ubuntu, say 10.10 or later, this works perfectly. If earlier, a devious trick is required.

---

### Post by chili555 on 2011-05-24
Thatnk you both for your kind comments and popcorn! Glad it's working. Have fun!> I can't believe it actually works!Even a blind pig finds an acorn; I guess this was my lucky day!

---

### Post by 1vel on 2011-05-24
speed is only 54mp/s
does not ubuntu support 802.11n ?

---

### Post by chili555 on 2011-05-24
I have but one suggestion. Edit /etc/Wireless/RT2870STA/RT2870STA.dat to be sure that WirelessMode=5 or =9. Try both. Reload the module:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```If that doesn't do it, I'm afraid I'm out of ideas.

---

### Post by Doorknob on 2011-05-24
> **chili555 said:**
> I have but one suggestion. Edit /etc/Wireless/RT2870STA/RT2870STA.dat to be sure that WirelessMode=5 or =9. Try both. Reload the module:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```If that doesn't do it, I'm afraid I'm out of ideas.

My N13 is running fine at 54 Mbs, but I would like to take advantage of N band. I looked in the location you post and I have RT3070STA folder that is empty no .dat file anywhere. Is this something I must create? and if so how would I go about doing so.

Thanks in advance for your help, you seem to be quite the wireless guru here.

---

### Post by chili555 on 2011-05-24
If you are using the rt2870sta module, it ought to be calling for RT2870STA.dat. Are you sure you're using the rt2870sta driver?```
lsmod | grep -e rt2 -e rt3
```

---

### Post by Doorknob on 2011-05-24
> **chili555 said:**
> If you are using the rt2870sta module, it ought to be calling for RT2870STA.dat. Are you sure you're using the rt2870sta driver?```
lsmod | grep -e rt2 -e rt3
```

This is what it shows:
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  2 rt61pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta

When I run "sudo gedit  /etc/Wireless/RT2870STA/RT2870STA.dat"
It opens said file which is blank.

---

### Post by chili555 on 2011-05-24
> rt2x00pci 13986 1 [COLOR="Red"]rt61pci[/COLOR]
rt2x00lib 39075 2 rt61pci,rt2x00pci
mac80211 257001 2 rt2x00pci,rt2x00lib
cfg80211 156212 2 rt2x00lib,mac80211
[COLOR="Red"]rt2870sta[/COLOR] 410104 1
crc_ccitt 12595 1 rt2870staDo you have two wireless devices?? Is the built-in not performing as expected?

---

### Post by Doorknob on 2011-05-24
> **chili555 said:**
> Do you have two wireless devices?? Is the built-in not performing as expected?

Yes I have a pci wireless G card that I think I have disabled. I was wanting to utilize my N band on my new router if it was possible so got the Asus USB N13 to try.

---

### Post by chili555 on 2011-05-24
> I think I have disabled.Not well, it appears. I suggest you blacklist rt61pci, rt2x00pci and rt2x00lib using the process I described earlier in this thread.

It appears that rt2870sta doesn't require a dat file, otherwise it wouldn't work at all. We might write one just for fun and see if it kicks the device up to N speeds. Nothing ventured, nothing gained.```
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Add two lines:```
Default
WirelessMode=5
```Proofread, save and close gedit. Unload and reload the module:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```If it does nothing, just mark it up to a failed experiment. If it hurts, remove it:```
sudo rm /etc/Wireless/RT2870STA/RT2870STA.dat
```If it helps, post back so the searchers will learn from our knuckle bleeding labors.

---

### Post by Doorknob on 2011-05-24
When trying to make the ".dat" file when I went to save it I got an error "Could not find the file /etc/Wireless/RT2870STA/RT2870STA.dat."

When I browsed my file system the only folder in etc/wireless is the one labeled RT3070STA which contained no file whatsoever.

---

### Post by chili555 on 2011-05-25
Then precede the above with:```
sudo mkdir /etc/Wireless/RT2870STA
```And then continue as above.

---

### Post by Doorknob on 2011-05-25
Ok made the directory and followed the previous steps. When I got to 
"sudo rmmod -f rt2870sta"

I got an  "ERROR: Removing 'rt2870sta': Resource temporarily unavailable"

Went ahead and rebooted just for giggles and still remain at 54Mbs

---

### Post by chili555 on 2011-05-25
> "ERROR: Removing 'rt2870sta': Resource temporarily unavailable"Sometimes, but not with all drivers, you can't remove a loaded module when it's driving the interface. In such cases, you either need to reboot, which you've done, or take the interface down:```
sudo ifconfig wlan0 down
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
sudo ifconfig wlan0 up
```If the .dat file doesn't do it, I am at the end of my ideas/talent/mojo. Sorry.

---

### Post by Doorknob on 2011-05-25
Well we gave it a shot, still running 54Mbs. Was hoping for N speeds on Ubuntu, it is great when streaming multiple storm chaser live feeds. 
Thanks for all your help, I learned a few new things, maybe in some future release it will work. Thanks again!

---

### Post by chili555 on 2011-05-25
Here's someone you could email about it. If you get a response, please post back; there are a few people here with the same issue.> chili@LAPTOP60:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
[COLOR="Red"]author:         Paul Lin <paul_lin@ralinktech.com>[/COLOR]
firmware:       rt3071.bin
--- snip ---

---

### Post by Doorknob on 2011-05-25
Ok thanks for the link, I will write to him and see what happens.

---

### Post by Doorknob on 2011-05-26
> 
[COLOR=black][FONT=&quot]May we know what is the security setting of your N band AP router? [/FONT][/COLOR]
 [COLOR=black][FONT=&quot]Is WPAPSK/TKIP or WEP security? If yes, please set to AES or OPEN/NONE.[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]Thanks![/FONT][/COLOR]
[COLOR=black][FONT=&quot]This is the reply I received first. I have yet to try it because I am at work but will as soon as I am home. But a thought came to me, I have a Netgear Dual Band router, I know my security settings on it WPA2-AES.[/FONT][/COLOR]


[COLOR=black][FONT=&quot]I think I may have had a DERP moment.....  :confused:
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Being a dual band the N band is separate meaning that I must set my computer to login under the N band SSID  correct?  Much like you would have too if you had two separate routers I should have too choose which one I want to connect to. This seems like common sense. [insert idiot face] now when I get home I must check to see which "router" it is connecting to the 2.4GH.z or the 5......and adjust Network Manager accordingly.
[/FONT][/COLOR]

---

### Post by Doorknob on 2011-05-28
Well still no luck, Ubuntu doesn't seem to see my N band being broadcast, although my one lone computer running WinXP does. Guess I will keep messing about in hopes that I can get something going. If I do I will repost to let all know my progress.

Thanks again Chili

---

### Post by WantSomethingNew on 2011-06-01
This has been a fantastic thread to read.  I am completely new to Ubuntu (or any form of Linux for that matter), aside from giving a previous version about a 24 hour shot a year or so ago.  Didn't have time to mess with it then, but am giving a fair chance now.  I too have been having issues with the N13 not getting above 54, which I know it gets at least 150 in Vista.  I'm at work now but anxious to try some of these steps when I get home.

Doorknob, have you managed to get the N working at this point?  Is there any more follow up to this that would be beneficial for me to know?  Does anyone actually have the N13 working faster than 54?

Thanks all!

---

### Post by thenickrulz on 2011-06-03
Anyone having troubles doing anything with this adapter view this! [http://ubuntuforums.org/showthread.php?t=1467291&page=4](http://ubuntuforums.org/showthread.php?t=1467291&page=4) 
TNR

---

### Post by Doorknob on 2011-06-07
> **WantSomethingNew said:**
> 

Doorknob, have you managed to get the N working at this point?  Is there any more follow up to this that would be beneficial for me to know?  Does anyone actually have the N13 working faster than 54?

Thanks all!

No. nothing new yet. I did receive another response from Ralink, and all he said was to update to the newest driver RT8070/3070/3370 usb V2.5.0.1 

I have yet to try it because the adapter is working for the time being and I need the connection, but as soon as I have time I will give it a try and see what happens, in the meantime I will just hum along at 54. It is a shame though I plug the thing into a Winblows computer and it flies at above 200....at first I was wondering if it was my router setup but that seems to prove it isn't.

---

### Post by Jeffreytooker on 2011-12-06
Chili555:
Many thanks.  Loaded 11.04 and USB-N13, no P&P.  Used your fix: [http://ubuntuforums.org/showthread.php?t=1766327](http://ubuntuforums.org/showthread.php?t=1766327)  Message 3-7.

I have been working on this problem since yesterday afternoon.  Started with 10.04.3 and finally loaded 11.04 this morning and found your fix.  Again Thanks.

Jeffrey Tooker

---

### Post by CatalystKat on 2012-09-10
> NB: If you are running later versions of Ubuntu, say 10.10 or later, this works perfectly. If earlier, a devious trick is required.

Hi, Thanks for all this info! I am running 8.10... what kind of devious trick might I employ? Thank you!

---

### Post by chili555 on 2012-09-10
Plug the device in and post:```
lsusb
```Thanks.

---

### Post by CatalystKat on 2012-09-10
When I try to run the initial program, here is the error: 

[/media/cdrom0/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/setup.exe or
          /media/cdrom0/setup.exe.zip, and cannot find /media/cdrom0/setup.exe.ZIP, period.

---

### Post by CatalystKat on 2012-09-10
lsusb:
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by chili555 on 2012-09-10
> When I try to run the initial program, here is the error:

[/media/cdrom0/setup.exe]A Windows .exe is not going to run on Linux. Please remove it and file it away.>  0b05:1786 ASUSTek Computer, Inc.This device uses the driver rt2870sta in older versions. We have made a lot of progress in drivers since 8.10, now almost 4 years old. Upgrade to 12.04 and it will work perfectly. Any chance?

---

### Post by CatalystKat on 2012-09-10
I could do that- have ethernet hooked up and am happy to upgrade since the computer has zero important info on it right now. Might I trouble you to suggest the best place to find upgrade instructions? Thank you!!

---

### Post by chili555 on 2012-09-11
If you are running 8.10, it is probably best to download the 12.04 .iso, I prefer bittorrent, and burn the image to CD. Once it's done, boot into the CD and do a fresh install. I have the best luck with the alternate CD: [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

You may also be interested in this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by WantSomethingNew on 2012-09-11
> **chili555 said:**
> ... Upgrade to 12.04 and it will work perfectly.

Chili, your posts and comments about the N13 have been priceless!  I have to ask though, "perfectly"?  I have not had a problem with my N13 working in a very long time and, overall, am very happy with it.  However I've never been able to get a faster connection than 54, even since the release 12.04.  I move the N13 to a Windows machine and can easily get 150.  Eventually I stopped trying (out of frustration) to get faster speeds, but would really like to know if I should expect better than 54 or not.

Thanks!

---

### Post by chili555 on 2012-09-11
> Eventually I stopped trying (out of frustration) to get faster speeds, but would really like to know if I should expect better than 54 or not.I've seen quite a few posts about N speeds in the rt28xx suite of drivers. I've seen people compile drivers directly from Ralink and compile compat-wireless. I have not yet seen anyone say it works reliably. I have seen many instances of "I stopped trying (out of frustration)."

However, today is a new day and 3.2.0-30 is a newer kernel. Moreover, there are even newer kernels that you can install: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm more than willing to work with you to try again. I'd estimate our chances as low.

In defense of the author of the driver, Ralink, I'm confident they don't devote the resources to Linux, 2% of the desktop space, that they do to Windows or even Android.

---

### Post by WantSomethingNew on 2012-09-11
> **chili555 said:**
> I've seen quite a few posts about N speeds in the rt28xx suite of drivers. I've seen people compile drivers directly from Ralink and compile compat-wireless. I have not yet seen anyone say it works reliably. I have seen many instances of "I stopped trying (out of frustration)."

I'm more than willing to work with you to try again. I'd estimate our chances as low.

Thanks for your offer.  At this point I'm more content with reliability than I am speed.  Everything else on my (nearly 10 year old) system works reliably.  At this point I'd rather be upgrading my system completely rather than trying to eek out any more performance.  Spending my time, and more importantly yours, seems a little wasted.

On the note of upgrading systems (apologies for digressing), is there anything I should be on the look-out for to ensure that whatever I upgrade to would provide N speeds?  I'm committed to Ubuntu now and would only be running windows as a VM for all those necessary evils out there.  So any system I buy, I'd want to make sure the hardware could perform to its complete abilities with Ubuntu.

---

### Post by chili555 on 2012-09-11
All I can suggest is that you search this forum for N-speeds. I am not aware of which devices do. I am usually only called out when they don't!

Even my own Intel parts don't do N.

This may be a clue: [http://www.vijayp.ca/blog/2011/03/how-to-get-lenovo-x201-to-connect-802-11n-n-wireless-networks-on-ubuntu-high-speeds/](http://www.vijayp.ca/blog/2011/03/how-to-get-lenovo-x201-to-connect-802-11n-n-wireless-networks-on-ubuntu-high-speeds/)

> Also, note that WMM (QoS) is technically required as part of a 802.11n deployment, and you must be running WPA2/AES to get 802.11n speeds.Be sure you test with your router set for QoS and WPA2/AES.

---

### Post by WantSomethingNew on 2012-09-11
Good read, thanks for the advise!

---


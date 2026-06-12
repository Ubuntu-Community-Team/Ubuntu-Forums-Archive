---
title: "Can't get wireless Broadcom WiFi Adapter to work with Ubuntu 9.04?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Unew on 2009-05-09
I can't get Ubuntu 9.04 to recognize my laptop's built-in Broadcom 4321AG 802.11 a b g draft-n WiFi adapter.  The adapter works very well with Vista, but I can't get Ubuntu to recognize the WiFi card.  I downloaded the "ndiswrapper package" and tried installing the card's native WiFi driver, but that did not solve the problem.  It said something about not being able to "see" the device. 

What steps can I take to troubleshoot this problem and get Ubuntu to work with my  Broadcom WiFi adapter?  I'm a newbie at Ubuntu, so I'd appreciate the clearest, step-by-step instuctions possible.

Thanks!

---

### Post by RedSingularity on 2009-05-09
What is your lspci output?

---

### Post by Unew on 2009-05-09
> **Shadow121 said:**
> What is your lspci output?

Sorry, but I don't know what you mean by "lspci output." ???  Where do I look to get that information so I can post it to the forum?  Thanks.

---

### Post by RedSingularity on 2009-05-09
Just type it into terminal and post what it gives you.

```
lspci
```

---

### Post by albinootje on 2009-05-09
> **Unew said:**
> I can't get Ubuntu 9.04 to recognize my laptop's built-in Broadcom 4321AG 802.11 a b g draft-n WiFi adapter.  The adapter works very well with Vista, but I can't get Ubuntu to recognize the WiFi card.  I downloaded the "ndiswrapper package" and tried installing the card's native WiFi driver, but that did not solve the problem.  It said something about not being able to "see" the device. 


Did you install the ndisgtk (GUI) package or did you follow a certain howto ? If so, which howto ?

And as a side note, I just came across this article (posted 10/08/2008) :
[http://digg.com/linux_unix/New_Linux_Broadcom_Wi_Fi_drivers_arrive?t=19552673](http://digg.com/linux_unix/New_Linux_Broadcom_Wi_Fi_drivers_arrive?t=19552673)
which says :
> 
Now Dell, with some help from Broadcom and Canonical, the company behind Ubuntu, has just released a Linux friendly Broadcom Wi-Fi driver for both 32 and 64-bit Linuxes. According to John Hull, Dell's Manager of Linux OS Engineering, "updated Linux wireless drivers that support cards based on the Broadcom 4311, 4312, 4321, and 4322 chipsets" are now available.

I wonder what the details about that are, and whether/when this will be available in plain Ubuntu (not just Ubuntu offered by Dell).

---

### Post by Unew on 2009-05-09
I installed the ndisgrk package.  Here;s the output from the "lspci command:

xxxxxx@xxxxxx-laptop-ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
xxxxxx@xxxxxx-laptop-ubuntu:~$

---

### Post by RedSingularity on 2009-05-09
Can you remove the ndisgrk package?  

Do that and then look in System>Admin>Hardware drivers

See if you can activate it in there.

---

### Post by Unew on 2009-05-09
I was able to uninstall the ndisgtk package, but I can not activate the Broadcom wireless adapter.  Other suggestions?

---

### Post by RedSingularity on 2009-05-09
Any reason why you cant activate it?  Do you at least see it in there?

---

### Post by Unew on 2009-05-09
I see the Broadcom adapter listed, but when I click "activate" nothing happens.

---

### Post by rpwdh on 2009-05-09
First, if you're on a laptop and there is a switch to turn the wireless on / off, make sure it's on.

The only other thing I had to do is go to System > Administration > Hardware Drivers and actvate the driver.

If that doesn't work, I'll leave you in the capable hands of those with more knowledge.

Good luck!

---

### Post by RedSingularity on 2009-05-09
Oh you need a wired connection set up with internet when you go to activate the "Hardware Drivers".  It downloads them from online.   Can you get a temporary wired connection for that?

---

### Post by Unew on 2009-05-10
I went into System>Admin>Hardware drivers and was able to activate the Broadcom WiFi card and connect to the Internet.  However, when I rebooted the laptop, the card was somehow deactivated.  To connect to the Internet again, I had to go into System>Admin>Hardware to activate the driver again.  In my WiFi set-up I told the system to connect automatically (as it does in Vista), but for some reason Ubuntu is requiring me to manually activate the driver everytime.  The good thing is that the WiFi adapter is now working; the bad thing is I have to manually activate it everytime I want to use it.

Any suggestions/solutions for making the connection automatic (i.e., not having to activate the adapter everytime)?

Thanks for all the help!

---

### Post by RedSingularity on 2009-05-10
Read [these](http://ubuntuforums.org/showthread.php?t=1144301) couple posts.  The guy had the same problem as you.

---

### Post by Unew on 2009-05-10
I followed the directions in the referenced posts, but the solution that worked for that poster did not work for my laptop / wireless adapter.

My laptop is an HP Pavilion tx2000 and it has a hardware switch to turn on /off the wireless card. However, following the turn /off procedure in the referenced post did not solve my problem (Ubuntu still requires me to reactive the wireless adapter each time I boot the laptop.)  Note that in the "Hardware Drivers" box which lists the "Broadcom STA wireless driver," that when I activate the adapter the "Activate" button never changes to "Remove" and the text remains "This driver is not activated."  Nevertheless the Broadcom driver IS activated because I can then connect manually to the Internet.  It appears that for some reason Ubuntu is confused about the presence or activation of the adapter.  It seems like one part of the system "thinks" the adapter is not activated, but another part knows that it exists and is activated.  I hope that makes sense; that's the best way I know to express what appears to be happening. 

Bottomline, #1  every reboot requires reactivation of the card, and  #2  even when I activate the adapter, Ubuntu "thinks" that it is not activated when it really is.   Any solutions / suggestions for how I track down this problem and solve it.  Having to reactivate the adapter is a hassle I've like to solve if at all possible.

Thanks again for all your help!

---

### Post by RedSingularity on 2009-05-10
Ok when you activated the driver did you restart the computer right away?  If not do that.

---

### Post by Unew on 2009-05-10
Yes, I immediately rebooted the laptop after "activating" the Broadcom adapter.  Note that when I "activate" the adapter, Ubuntu [in the Hardware Drivers app) says that the adapter is "not activated" despite the fact that it really is.  I have to manually connect everytime.  Upon reboot, Ubuntu seems to forget the fact that I already activated the adapter.  Anything else I might try to troubleshoot / solve this nagging problem?   Thanks!

---

### Post by albinootje on 2009-05-10
> **Unew said:**
> Note that when I "activate" the adapter, Ubuntu [in the Hardware Drivers app) says that the adapter is "not activated" despite the fact that it really is.  I have to manually connect everytime.  

Can you post the output of 
```

lsmod

```
before *and* after activating ?

---

### Post by Unew on 2009-05-10
Results of the lsmod command BEFORE activiting the Broadcom adapter:

xxxxxx@xxxxxx-laptop-ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_rawmidi            29696  1 snd_seq_midi
iptable_mangle         10880  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iptable_filter         10752  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63240  0 
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
x_tables               23044  2 iptable_nat,ip_tables
joydev                 18368  0 
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
usbhid                 42336  0 
psmouse                61972  0 
soundcore              15200  1 snd
nvidia               7233756  29 
k8temp                 12416  0 
wacom                  28808  0 
btusb                  19608  2 
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_nforce2            14980  0 
agpgart                42696  1 nvidia
ndiswrapper           193436  0 
video                  25360  5 
output                 11008  1 video
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
xxxxxx@xxxxxx-laptop-ubuntu:~$ 



Results of the lsmod command AFTER activiting the Broadcom adapter:

xxxxxx@xxxxxx-laptop-ubuntu:~$ lsmod
Module                  Size  Used by
ieee80211_crypt_tkip    16896  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_rawmidi            29696  1 snd_seq_midi
iptable_mangle         10880  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iptable_filter         10752  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63240  0 
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
x_tables               23044  2 iptable_nat,ip_tables
joydev                 18368  0 
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
usbhid                 42336  0 
psmouse                61972  0 
soundcore              15200  1 snd
nvidia               7233756  29 
k8temp                 12416  0 
wacom                  28808  0 
btusb                  19608  2 
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_nforce2            14980  0 
agpgart                42696  1 nvidia
ndiswrapper           193436  0 
video                  25360  5 
output                 11008  1 video
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
xxxxxx@xxxxxx-laptop-ubuntu:~$

---

### Post by albinootje on 2009-05-10
Thanks for posting that. This is the difference :
```

> ieee80211_crypt_tkip 16896 0
> wl 1489748 0
> ieee80211_crypt 13444 2 ieee80211_crypt_tkip,wl

```
In both cases the ndiswrapper was already loaded.
Can you try adding these lines in /etc/rc.local (Read the comment inside that file!) :
```

modprobe wl 
modprobe ieee80211_crypt

```
And reboot.

---

### Post by Unew on 2009-05-10
I'm a newbie and need clarification ... 

1. How do I open the location /etc/rc.local?  When I type that into a terminal window, nothing happens.


2.  Where exactly do I add the suggested lines of code in /etc/rc.local (after I figure out how to open that location)? 

Please clarify step-by-step so I can follow.  Thanks!

---

### Post by albinootje on 2009-05-10
> **Unew said:**
> I'm a newbie and need clarification ... 

Okay, sorry.

Try this in a terminal :
```

gksu gedit /etc/rc.local

```

Then make it look like this :
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe wl       
modprobe ieee80211_crypt         
      
exit 0

```

---

### Post by gpredrag on 2009-05-10
There is also isue, I beleive that afther uninstaling ndiswrapper package, file /etc/modprobe.d/ndiswrapper remains intact, and that file loads ndiswrapper module (but not any ndis drivers).
If ndiswrapper is not used, that file should be removed, and proper linux drivers should be loaded automatically.

---

### Post by Unew on 2009-05-10
My Broadcom wireless connection problem has been SOLVED!  I used the recommended code and after rebooting, Ubuntu automatically connects to the Internet now.  Thanks for all the help!

---


---
title: "Lenovo S10E Wireless not in snowcone menu upper right corner (ubuntu 11.04)"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by ctt2 on 2011-06-08
I am a very new and hopefully now life long ubuntu and linux user. I followed several tutorials which may have been for older versions of ubuntu to try and fix this before deciding to post and noticed in some similar threads the masters seemed to ask for the info I will paste below. This is really tweaking me out, I am a computer guy by trading and can't find the solution on google on my own for the first time. I did extensive searching and loading/unloading before resorting to asking for help. Before I pull out my hair I am hoping there is an easy fix. After installing ubuntu into this Lenovo Ideapad S10E and additionally loading the broadcom STA drivers that the OS asked me to load. The wireless does not work. I have unblocked the wireless on rfkill and made sure the physical switch is set to not block and the wireless LED is turning on. The rfkill list command shows no and no.. but the snowcone in the upper corner does nto show anything about wirelss and the broadcom STA driver says it is actived but not in use. I have tried reloading it and trying the solutions for broadcom wireless in the sticky thread at the top of wireless and networking.

rchris@chris-mini:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

chris@chris-mini:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
joydev                 17322  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  3 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
drm                   180037  4 i915,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               75143  1 uvcvideo
ideapad_laptop         13262  0 
psmouse                73312  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
sparse_keymap          13666  1 ideapad_laptop
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lib80211               14570  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
tg3                   131476  0 
chris@chris-mini:~$

---

### Post by chili555 on 2011-06-08
Your efforts in rfkill are great work! We see no driver in your lsmod that is for wireless. Are you sure you have a Broadcom wireless card? Please run:```
lspci -nn
```Is it a Broadcom? If so, please do:```
sudo modprobe wl
```Does the snowcone come to life? If not, please post:```
dmesg | grep wl
```Thanks.

---

### Post by ctt2 on 2011-06-08
Hello Chilli, thank you for the help and your props, I looked up the specs to double check and the wireless chipset was listed as broadcom 4312, the command you asked verified the same as you will see below. The second command sudo modprobe wl generated an error which you will see below. I will also include the third command if it helps. I am just starting to read Ubuntu Unleashed 2011 Edition I am hoping after completing it I will be on the other side of the help fence. Eitherway thank you for helping to launch my netbook into the wireless world. :)

chris@chris-mini:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

chris@chris-mini:~$ sudo modprobe wl
[sudo] password for chris: 
FATAL: Error inserting wl (/lib/modules/2.6.38-8-generic/updates/dkms/wl.ko): Invalid argument

chris@chris-mini:~$ dmesg | grep wl
[   11.587117] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.612461] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   11.612475] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   12.543905] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   12.543920] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[  105.009744] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  105.009759] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
chris@chris-mini:~$

---

### Post by chili555 on 2011-06-08
Hmmm! Ugly! Please get a wired  ethernet connection and do:```
sudo apt-get install brcmwl-kernel-source
```If the terminal reports it's already installed, then do:```
sudo apt-get install --reinstall brcmwl-kernel-source
```I wish I could say this is a common, well-known problem, but it's new to me. I'm feeling my way along a bit here.

Then reboot and do:```
sudo modprobe wl
dmesg | grep wl
```Any improvement?

---

### Post by ctt2 on 2011-06-08
okay, ended up doing the sudo apt-get install --reinstall bcmwl-kernel-source (needed to omit the r from brcm, hoping it is the same package because brcm was not found..) then ran sudo modprobe wl and error again. Output below.. I am wondering if my previous tinkering to fix problem is causing one here? I am not against quick reinstall starting fresh with your solution to see if it works..

chris@chris-mini:~$ sudo modprobe wl
[sudo] password for chris: 
FATAL: Error inserting wl (/lib/modules/2.6.38-8-generic/updates/dkms/wl.ko): Invalid argument

chris@chris-mini:~$ dmesg | grep wl
[   11.125394] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.144902] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   11.144917] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   12.068057] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   12.068071] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   81.506756] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   81.506766] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
chris@chris-mini:~$

---

### Post by ctt2 on 2011-06-08
I just found this.. [http://ubuntuforums.org/showpost.php?p=10527475&postcount=5](http://ubuntuforums.org/showpost.php?p=10527475&postcount=5)

Do you think it would work? 

his directions are a little bit more technical than I am.. 

I understand them in theory.. but not sure how I am supposed to know what files to # out from this part .. 

"Changing these will require gksudo gedit open then go to root then  /etc/modprobe.d/ *and find the files where you need to comment out the  blacklist."

---

### Post by ctt2 on 2011-06-08
Okay I figured out what he was saying.. he was just multi-stepping in one line..

and, It worked! :)

Going to repeat steps for the benefit of step by step followers..

---

### Post by ctt2 on 2011-06-08
So you have a Lenovo Ideapad S10E (many people do) with a Broadcom 43xx chipset and want the most important part of any netbook working, the wireless. The Ubuntu built in broadcom STA driver says it is installed, activated and not currently in use. Your almighty snowcone in the upper right hand corner is empty, when it's full so are you, of internet, life and the world to enjoy. When it's empty, you are here pulling hairs and wanting answers.

Some of these steps maybe redundant and unnecessary they are just what I had to do to fix this.

Click the Ubuntu Circle (equivalent to windows start button)
In search type in "Terminal"
Click on the Terminal icon
In the Terminal window (where magic happens)
Type in "rfkill unblock all"
Type your password if asked.
Type in "rfkill list all"

You want the word "no" to show up after soft blocked and hard blocked behind all wireless devices, especially the one you intend to connect with. If it is soft blocked, well it shouldn't be you type in rfkill unblock all.

In fact, add this to your system startup as quoted from another post on this forum by my very helpful friend Chilli..

Please do (in the terminal window, what is in the big boxes below..):     Code:
     sudo gedit /etc/rc.local 
Right *above* Exit 0 please add:     Code:
     rfkill unblock wifi 
Proofread, save and close gedit. Enjoy!

If you have a "yes" behind hard blocked that means you need to hit the little green button above the F10 key on your lenovo S10E, if you have another model, look for the physical wireless on/off switch and press it!

Go ahead and run another rfkill list to see if anything has a yes, you want to see 'no'

Now for the fun part (or just the second part, however you want to look at it. From NM_Geo's directions)

Click the Ubuntu Circle (equivalent to windows start button)
In search type in "Synap"
Click on the Synaptic Package Manger icon
Type in your password if it asks

In the upper corner where Synaptic Package Manager states "Quick Filter"
Type in "BCM" 

RIGHT-CLICK on bcmwl-kernel-source (if it has a solid green box to the left of it)
in the menu that appears (popup menu) LEFT-CLICK on 'Mark for Removal'

RIGHT-CLICK on bcmwl-modaliases (if it has a solid green box to the left of it)
in the menu that appears (popup menu) LEFT-CLICK on 'Mark for Removal'

Look for any other items with "STA" in the name that have the same solid green box, RIGHT-CLICK on them and use the same option 'Mark for Removal'

When done with marking, click the 'Apply' button at the top. If asked for a password provide it, if asked to confirm your actions please click confirm.

When this process is complete, locate your terminal window if you have not already closed it, it should within the start bar icons. Alternatively you can;

Click the Ubuntu Button (start button)
Type in 'Terminal' in the search box and either press the Enter key or click on the 'Terminal' Icon

At this point copy the line in the box below and paste it into the terminal window. You can not paste with Ctrl-V in a terminal window, you can copy it from the box with CTRL+C but you must RIGHT-CLICK in the terminal window and Click on 'Paste'

Code:     cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl' 
The previously installed STA driver blacklist the B43 driver and the ssb module. What this means in plain English is that broadcom doesn't like you. To fix this you need to tell your computer to ignore the black listing. The point of the cat command above was to narrow down the field to give you an idea of what you might see in the blacklist files.

 You  will need to make your computer ignore the black listings by doing what is known as 'comment out' those blacklist by placing # in front of the  line containing the blacklist item. ( eg. a line containing 'blacklist b43' will be changed to '#blacklist b43'),  

Here is how we will do this,
Click the Ubuntu Start Button
Type in 'Terminal' press Enter or Click the terminal icon or find your already opened terminal windows on the left and work with one of them.

In a terminal window type in 'gksudo gedit'
Click on Open 
then go navigate to /etc/modprobe.d/
Open blacklist.conf
As mentioned above put a # in from of the line with Broadcom BM43xx or anything with broadcom in it.. if you are working with another series broadcom chip look for something that seems like your chip. The pounds cant hurt too much, well maybe a little but you are fresh installing anyway so just do it. ;)

Now click File, Click Save.

Go back to Ubuntu Start Button,
Type in 'Synap'
Click Synaptic Package Manager
Type in your Password if asked
In the Quick Filter box type in 'b43'
RIGHT-CLICK on firmware-b43-installer or firmware-b43-lpphy-installer (for the low power version of the firmware)
click on 'Mark for Installation'
RIGHT-CLICK on b43-fwcutter
click on 'Mark for Insallation'

Click on "Apply" at the top.

When finished, reboot and hopefully your snowcone of happiness will be usable upon reboot. If you were plugged in via a LAN cable while following this madness don't forget to unplug it before connecting to wireless as some routers will hate you if you try and hit her up from the two connections at once.

I hope my tutorial helps someone.

Peace.

---

### Post by josephmills on 2011-06-09
Lp-phy

---

### Post by DrPotoroo on 2011-10-08
Wow, thanks! I only had to go as far as the pressing the green button step. I will try the other steps later if required. Interestingly, my blue wireless light was already on, but rfkill list all showed bluetooth and wireless to be hard blocked. I HAD been trying pressing the green button, and holding until the blue light toggled - off, then on again. For some reason that was leaving them hard blocked. Pressing it once for a short time the blue light stayed on, but the rfkill status then listed them as no longer hard blocked.

---


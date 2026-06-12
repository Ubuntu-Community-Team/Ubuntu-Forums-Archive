---
title: "Broadcom Wifi card shows up as eth0, not solved by instructions from ubuntuforums"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by KittyCatHerder on 2013-03-24
Hi. i'm new here. I'm not brand new to Linux or Ubuntu but I'm not experienced enough to know how, or figure out how, to fix this myself. As in this thread -- [http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631), if I issue ifconfig wlan0 up I get a return of 'no such device'. I knew I had a wifi card, because I was using it, so I issued ifconfig, and, to my surprise no wlan card was listed. That is when I came to ubuntuforums and found the aforementioned thread which lists a set of commands, to repair the issue, which I followed. The result was no improvement as well as now I can not connect my machine to my network by WiFi. The small WiFi status icon on the upper dock (I use Gnome Classic) is still there, but it is "empty", as in, there are no little bars inside the field of the icon to indicate connection/signal strength.

Now I have two questions. The first question is; how can I get the wifi working again? The second question is; once I have repaired the WiFi connection, how to I repair the original problem of the Broadcom WiFi card not being recognized when I issue ifconfig?

---

### Post by Hadaka on 2013-03-24
Hi let's start by looking at what your wifi card is
and seeing what drivers you may have loaded.
open a terminal  ctrl/alt/t  then COPY and paste
the following commands.
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
please post the results.
thanks

---

### Post by KittyCatHerder on 2013-03-25
> **Hadaka said:**
> Hi let's start by looking at what your wifi card is
and seeing what drivers you may have loaded.
open a terminal  ctrl/alt/t  then COPY and paste
the following commands.
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
please post the results.
thanks
  
Thanks for the fast response!

-----------------------------------------------------------------------------------------

```
lspci -nnk | grep -iA3 net
```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
Subsystem: Acer Inc. [ALI] Device [1025:0590]          
Kernel driver in use: r8169 Kernel modules: r8169


02:00.0 Network Controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Foxconn international, Inc. Device [105b:e042]
Kernel Driver in use: bcma-pci-bridge
Kernel modules: bcma, brcmsmac

------------------------------------------------------------------------------------------

```
lsmod
```

Module                  Size  Used by
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
psmouse                86520  0 
uvcvideo               67203  0 
serio_raw              13027  0 
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  1 acer_wmi
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             353252  0 
i915                  423466  3 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
b43                   342669  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 

----------------------------------------------------------------------------------------------------------

```
rfkill list all
```

0: acer-wireless: Wireless LAN
Soft blocked: no
Hard Blocked: no

--------------------------------------------------------------------------------------------------------

Immediately after issuing ```
rfkill list all
``` the monitor shut down (or the VGA failed or something) and the machine went into stand-by. It woke fine as usual but I haven't seen the screen act that way before.

So, is there anything to be learned by the results here?

---

### Post by Hadaka on 2013-03-25
Hi, lets toss those drivers into the blacklist file
and load a different driver. open a terminal ctrl/alt/t
then  Please COPY and paste
the following...
```
sudo gedit /etc/modprobe.d/blacklist.conf 
```
add the 2 lines at the very end of the file..
```
blacklist bcma
blacklist brcmsmac
```
proof read carefully. save and close gedit.
then at terminal do..
```
sudo modprobe -r brcmsmac
sudo modprobe -r bcma
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by KittyCatHerder on 2013-03-25
Everything responded as expcted until I tried to ```
sudo modprobe -r bcma
```. I got FATAL: Module is in use. I'm not sure if I should still issue ```
sudo apt-get install bcmwl-kernel-source sudo modprobe wl
``` or not.

I tried ```
sudo modprobe
``` which seems to have worked or, that is, terminal returned to prompt. I don't know what it did though because I am not
familar with modprobe.

As it is very late now, I am going to have to coem back to this tomorrow. thanks for your help so far! Hopefully you will still have time tomorrow to keep 
walking me through the fix!

---

### Post by Hadaka on 2013-03-25
Hi, yes continue with the command..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
the command will blacklist bcma for you.
thanks.

---

### Post by KittyCatHerder on 2013-03-25
> **Hadaka said:**
> Hi, yes continue with the command..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
the command will blacklist bcma for you.
thanks.

I've just plugged in to my network by ethernet and installed bcmwl-kernel-source and, then, I ran the ```
sudo modprobe wl
``` still no WiFi

If I understood the commands that I were running I might be able to help you to figure out why it didn't work but I'm afraid I have very little understanding of what most of these commands do. 

What next, then?

---

### Post by KittyCatHerder on 2013-03-25
Just messing around I found the following Xorg error and, as well, as a result of searching for that error, a related forum thread: b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 10, Type 8, Revision 1)          [https://bbs.archlinux.org/viewtopic.php?id=130806](https://bbs.archlinux.org/viewtopic.php?id=130806)

You will see in the linked thread that the poster, like me, has the BCM4313, which caused the same error I found and reported above. I, myself, can not learn anything form this aside from that it appears that the problem might either be related to a programming error in the kernel, or the 64 addressing bits operating system (I do not know if I am using the 64 bit Ubuntu or another version).

To quote a post from that linked thread, "According to wireless.kernel.org, b43 doesn't support BCM4313 - you can use wl or brcmsmac". If I understand correctly what I have been doing by issuing these commands from the previous posts, then, I am not using the "b43" driver that is known to not work with the BCM4314 but, instead, I am using the "wl" driver. Because of those things I'm making a huge leap and assuming that my problem might not be caused entirely or even partly by the driver I am using. This is mostly guessing by putting things together that don't necessarily go together.

When I look at the "Additional Drivers" GUI I see that it says my machine is using the "Broadcom STA wireless driver". Does that mean I am not using the driver you intended me to be using at this point?

I started using Linux because I wanted to learn new things and Linux has given me a rich environment for that. That said, I have a lot of questions about the commands and techniques we have been discussing here that I would like to address after the WiFi problem is solved. This "driver" as well as "driver kernel" business is a little confusing.

---

### Post by chili555 on 2013-03-25
My colleague Hadaka may be on a short break, so, hopefully not stepping on any toes, allow me to help just a bit.>  If I understand correctly what I have been doing by issuing these commands from the previous posts, then, I am not using the "b43" driver that is known to not work with the BCM4314 but, instead, I am using the "wl" driver.That's what we're trying to do. Please confirm which driver is loaded by LIsting all the MODules:```
lsmod
```Is b43 listed? Is wl?> When I look at the "Additional Drivers" GUI I see that it says my machine is using the "Broadcom STA wireless driver". Does that mean I am not using the driver you intended me to be using at this point?Nope. The Broadcom STA driver provides wl. That's what we want.

Hadaka will, no doubt, probe why the wireless isn't working. What do these tell him?```
iwconfig
sudo iwlist eth1 scan
rfkill list all
```Each different Broadcom device, and there are dozens, has one best way to get it going. Many have two ways and one way is better in terms of performance. In the case of your device:> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="#FF0000"]14e4:4727[/COLOR]]...we believe the STA driver, providing wl, is the best.

You are doing very well, I urge you to keep studying and keep learning.

---

### Post by Hadaka on 2013-03-25
Hi, Chili555 is correrct, the wl driver "should" be loaded
for your card. When i first had you show what modules
were loaded via the lsmod command..b43 driver was loaded.
yet your lspci report on your wireless card showed bcma,and brcmsmac
installed. Running the install broadcom-kernel-source command "should"
remove b43,bcma and other modules the b43 uses. So...Please run those
commands chili555 posted and we shall see where we are.
thanks.

@chili555..Thank you sir.

---

### Post by KittyCatHerder on 2013-03-25
```
lsmod
``` Lists wl (used by 0), b43 (used by 0), and bcma (used  by 1, b43). So, it would seem that wl is not being used.  There are also, of course, many other modules printed in the output but I don't know what else to look for other than what you listed.

```
iwconfig
``` Lists two interfaces. lo - no wireless extensions, and eth0 - no wireless extensions

```
sudo iwlist eth1 scan
``` Interface doesn't support scanning. (I have some idea of what this can be used for, so it sucks that it doesn't support scanning!)

```
rfkill list all
``` 0: acer-wireless: Wireless LAN
Soft Blocked: no
Hard blocked: no

So, it would seem that wl is not in use, and bcma is being used by b43, but b43 is not being used itself. lspci still lists the Broadcom BCM4313. Are we sure this is a problem with the driver and/or module? Or is it possible I screwed something else up by following those instructions from the other thread that I linked to in my original post?

----------------------------------------------------------------------------------------------------------------------------------------------

So now I understand that a driver (driver file? driver package?) provides a module. What else does the driver provide? How, and by what, is each part of the driver used? These are the things I never really had the opportunity to learn during my many years with proprietary operating systems and software.

I did have a pretty good understanding of hardware versions and the fact that some only work at all with very specifically written driver software and others can work well with generic driver software. What I don't yet understand is how driver software interacts with hardware, operating system, user input, variables, etcetera, but I don't expect to be learning all of that right here right now. I just hope I can get a little closer to having the level of understanding of digital logic, OS kernels, programming language, etc, etc, etc, that someone who could write a complete OS and software suite for it would have. Yeah, I was born with the highest level of curiosity. It's about half and half a great thing and frustrating/exhausting.

----------------------------------------------------------------------------------------------------------------------------------------------

Some time in the near future I think I might do a  little research into which model of WiFi card works best under Ubuntu  12.04 and my hardware configuration and replace the BCM4313. The machine in question was very cheap, on sale, when I bought it. I love the machine but it lacks some stuff I would really like to have, namely bluetooth and a GPS receiver (and a backlit keyboard, but it's a netbook). Maybe I could find a mPCIe card that combines WiFi, Bluetooth, & GPS, or maybe one that just combines WiFi and one of the other two if a card with all three doesn't exist?

---

### Post by Hadaka on 2013-03-25
ok, would you be so kind as to share the output of..
```
lsmod
```
by posting said output. :)
thanks.

---

### Post by Hadaka on 2013-03-25
Hi, my good friend chili555 also suggests
we make sure the sta (wl) broadcom-kernel-source
driver does not conflict with any of the b43 driver
modules, so lets do this... open a terminal  ctrl/alt/t
COPY and paste the following commands...
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
add these 3 lines at the bottom of the file..
```
blacklist b43
blacklist bcma
blacklist ssb
```
proof read ...save..and close gedit..
then in terminal..please do..
```
sudo apt-get install --reinstall bcmwl-kernel-source
modprobe wl
```
then boot the computer..
report back please..
thanks

---

### Post by KittyCatHerder on 2013-03-26
For some reason when I "reply with quote" I get a quote from the wrong post. Hmmm. Anyway, here is the output of ```
lsmod
```

Module                  Size  Used by
usblp                  17885  0 
usb_storage            39683  1 
wl                   2906597  0 
lib80211               14040  1 wl
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                86520  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  423466  3 
wmi                    18744  1 acer_wmi
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             353252  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
b43                   342669  0 
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
video                  19115  1 i915
mac80211              436493  1 b43
cfg80211              178877  3 wl,b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0

---

### Post by Hadaka on 2013-03-26
Hi, did you do the commands in post #13?
please do those and post the results.
thanks.

---

### Post by KittyCatHerder on 2013-03-26
> **Hadaka said:**
> Hi, my good friend chili555 also suggests
we make sure the sta (wl) broadcom-kernel-source
driver does not conflict with any of the b43 driver
modules, so lets do this... open a terminal  ctrl/alt/t
COPY and paste the following commands...
```

```
add these 3 lines at the bottom of the file..
```
blacklist b43
blacklist bcma
blacklist ssb
```
proof read ...save..and close gedit..
then in terminal..please do..
```
sudo apt-get install --reinstall bcmwl-kernel-source
modprobe wl
```
then boot the computer..
report back please..
thanks


```
sudo gedit /etc/modprobe.d/blacklist.conf
```

I had already started a 'section' at the bottom of the file with the  comment "#created by me to fix wifi problems", and I had already black  listed and commented out "b43f" which I had done by instruction from an earlier post if I remember correctly. I had already black listed "brcmsmac" and "bcma". I added "b43" and "ssb" to the black list, saved the file. 

I then ran ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` which resulted in a lot of stuff printed in the terminal (which I saved in a text file in case it would be useful). 

```
modprobe wl
``` immediately returned me to prompt so I assume it worked.

I am sorry to say that, after rebooting, I still do not have any wireless interface listed by ```
ifconfig
``` which still only lists eth0 and lo, and I am still unable to connect to my network by WiFi.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

After we have sorted my problem, I would really like to ask some general questions about the terminology used by yourself and your friend so far. Belive it or not, even with the strange problems I've been having, as soon as I started using Linux I felt like 'finally, an operating system that works the way one that is made for humans to oeprate should operate'. After growing up on Windows, I hadn't even fully realized after all that time at just how convoluted and round about it had become to accomplish tasks with it. 

This Ubuntu community, so far, seems to be highly organized and networked. This is a good thing because I am going to have hundreds of questions in the coming months and years haha. As soon as WiFi is working I will be posting several new threads to get help with several others things that I haven't been able to solve/execute by searching here and the rest of the internet. I hope you all are still available then! Thanks for the help.

---

### Post by Hadaka on 2013-03-26
Ok, thanks, Its late here so we shall continue
tomorrow. I may be late getting on so i have
asked chili555 to repond to your post, He is
the best, if anyone can solve your problem it
is him. Either way, i will check in on the progress.
night.

---

### Post by KittyCatHerder on 2013-03-26
A few minutes ago I remembered that I have a micro usb wifi adapter that came with an old bluray player. It would be great if I could use that to help with the diagnosing of this problem. 

Just for fun and experimentation I plugged it in and ran ifconfig, and the terminal hung, giving no output, no promt, and not responding to the "ctrl+C" keyboard input. I ran lsusb which, admittedly, I didn't know existed until I tried it, but the card didn't show up. I don't know how I would go about 'installing' the card to make it useable to connect to my network, which is a VERY strange feeling after having spent over 20 years cruising through Windows. Obviously this is mostly just me using my curiosity to pass time but I am going to have to figure it out now that I wondered if it could be done/how to do it, but that is another matter for another time, I guess.

---

### Post by KittyCatHerder on 2013-03-26
> **Hadaka said:**
> Ok, thanks, Its late here so we shall continue
tomorrow. I may be late getting on so i have
asked chili555 to repond to your post, He is
the best, if anyone can solve your problem it
is him. Either way, i will check in on the progress.
night.

Thanks a lot for your help so far! It's late here as well so nothing more could be accomplished before some sleep anyway. It's really cool that top community experts are donating time here!

---

### Post by chili555 on 2013-03-26
Please run and post:```
rfkill list all
dmesg | grep wl

```Thanks.

---

### Post by KittyCatHerder on 2013-03-26
> **chili555 said:**
> Please run and post:```
rfkill list all
dmesg | grep wl

```Thanks.


```
rfkill list all
``` gives 0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no

```
dmesg | grep wl
```

Gives no output, only returns to prompt.



My machine is now having trouble shutting down as well. I guess I should start another thread for that after the WiFi is working again, though.

---

### Post by Hadaka on 2013-03-26
Hi, please boot your computer and
then do.
```
dmesg | grep b43
```
and again..
```
dmesg | grep wl
```
post the results.
thanks.

---

### Post by KittyCatHerder on 2013-03-26
> **Hadaka said:**
> Hi, please boot your computer and
then do.
```
dmesg | grep b43
```
and again..
```
dmesg | grep wl
```
post the results.
thanks.

```
dmesg | grep b43
```

[    3.300199] b43-phy0: Broadcom 4313 WLAN found (core revision 24)
[    3.301100] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 10, Type 8, Revision 1)
[    3.301132] b43: probe of bcma0:0 failed with error -95

```
dmesg | grep wl
```

Gives no output, returns to prompt.

---

### Post by chili555 on 2013-03-26
Let's try a bit harder:```
sudo modprobe -r b43
sudo modprobe wl
dmesg | grep wl
```

---

### Post by KittyCatHerder on 2013-03-26
> **chili555 said:**
> Let's try a bit harder:```
sudo modprobe -r b43
sudo modprobe wl
dmesg | grep wl
```

```
sudo modprove -r b43
``` gives no output, returns to prompt

```
sudo modprobe wl
``` was interesting. The, now expected, no output return to prompt occured. Then a message appeared on the desktop informing me that a conection to my network had been established. I have no idea what happened, as I don't quite understand what modprobe accomplishes. I hope it will tell you something that can help you! The network connection seems to be stable now but ifconfig still does not list any 'wlan' interface.

```
dmesg | grep wl
``` 
[ 2247.107259] wl: module license 'MIXED/Proprietary' taints kernel.
[ 2247.176357] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2247.176375] wl 0000:02:00.0: setting latency timer to 64
[ 2247.214491] INFO @wl_cfg80211_attach : Registered CFG80211 phy

---

### Post by KittyCatHerder on 2013-03-26
After reboot the WiFi connection didn't return. I tried to repeat the process that seemed to have caused the connection to be established before but it didn't work.

---

### Post by Hadaka on 2013-03-27
Hi, the driver you are using..wl produces eth1 (usually)
not wlan#, wlan0 or wlan1 is usually seen with the b43 driver
so not seeing a wlan# is normal.
please do..
```
sudo modprobe wl
```
then do..
```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf | grep blacklist
lsmod |egrep 'b43|bcma|ssb|wl'
```
thanks.

---

### Post by KittyCatHerder on 2013-03-27
> **Hadaka said:**
> Hi, the driver you are using..wl produces eth1 (usually)
not wlan#, wlan0 or wlan1 is usually seen with the b43 driver
so not seeing a wlan# is normal.
please do..
```
sudo modprobe wl
```
then do..
```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf | grep blacklist
lsmod |egrep 'b43|bcma|ssb|wl'
```
thanks.

```
cat /etc/modules
``` 

lp 
b43

```
cat /etc/modprobe.d/blacklist.conf | grep blacklist
``` 

blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
#blacklist b43f
blacklist bcma
blacklist brcmsmac
blacklist b43
blacklist ssb

```
lsmod |egrep 'b43|bcma|ssb|wl'
``` 
wl                     2906957  0
lib80211           14040      1 wl
cfg80211          178877    1 wl


```
You are some kind of BASH ninja
```

---

### Post by Hadaka on 2013-03-27
ah ha ! 

cat /etc/modules  lp  b43

that is loading the b43 driver,let's fix that
please do..
```
sudo gedit /ect/modules
```
backspace out b43 (remove)
and replace with wl
it should now look like this
lp
wl
click save and close gedit
then boot.

---

### Post by KittyCatHerder on 2013-03-27
> **Hadaka said:**
> ah ha ! 

cat /etc/modules  lp  b43

that is loading the b43 driver,let's fix that
please do..
```
sudo gedit /ect/modules
```
backspace out b43 (remove)
and replace with wl
it should now look like this
lp
wl
click save and close gedit
then boot.

That did the trick! WiFi is working normally now! I would have never figured that out on my own. Well maybe some day but it would have been long after I had reinstalled the entire OS to try to fix the problem! Thanks a lot!

So now my most immediate question has to do with kernels/modules/drivers... I am wondering if I am begining to understand this... A module is a section of the kernel which calls on a driver file and loads it at startup. Is that close? Are modules discrete pieces of software in the kernel, or is the word module just used to identify a generic/common part of the kernel whose job is to load/start things like drivers when the OS boots? I have a lot of other questions too but I will need to go back and read the thread to remember those.

Also, am I correct in thinking that the problem with my wifi boiled down to the fact that a module had been programmed to load a driver that does not work with the broadcom 4313, and that reprogramming the module to load the lp driver in place of the b43 was what got the wifi working again?

I will be looking for instructions on how to do several things with Ubuntu. If I can not find answers for my questions already posted in this forum, I hope you and your friend Chili555 can participate in the solutions!

---

### Post by Hadaka on 2013-03-27
Hi, whew..finally Glad its working !
Yes there is always alot to learn about the operating system.
do this code:lsmod...(which is list-modules) you will see modules
for video,wireless,wired and many other devices and cards within
the computer. these modules are a set of instructions they tell the
code:lspci..(list pci's) those are the hardware items that the modules
control.what to do and of course the modules must be compatable with the hardware
and they must also be able to give and pass information to the kernel
which is the heart of the system.Everything the system does and what it can do
is based on the kernel. Do a search on "How linux works" start small and simple
and build from there.There are also sections on this forum to discuss the how's
and why's. Good luck in continuing your knowledge. and PLEASE, mark this thread
SOLVED.
thanks.

---

### Post by chili555 on 2013-03-27
> Also, am I correct in thinking that the problem with my wifi boiled down to the fact that a module had been programmed to load a driver that does not work with the broadcom 4313, and that reprogramming the module to load the lp driver in place of the b43 was what got the wifi working again?Almost. Your device, 14e4:4727, is claimed by two different drivers, also known in Linux as modules. Fun, fun, fun, eh?

The trick is to find out which module; wl or b43, drives your device correctly. Hadaka and I know from many years and many posts of experience, that it's wl. The problem is made tougher because the sharp guys and gals generally have tried a few things and made the process worse because we have to diagnose and fix the previous attempts. Your problem was two-fold. Your /etc/modules file loaded the wrong driver, b43 and your /etc/modprobe.d/blacklist.conf attempted to blacklist it to *never* load! Very confusing! Once Hadaka and you discovered and corrected it, everything started working smoothly.

Imagine Mrs. Chili and I standing in the grocery aisle and her saying that we will *NEVER* get any chocolate cookies and me saying we will *ALWAYS* get chocolate cookies. We are arguing and, meanwhile, the bananas and milk and cereal aren't being purchased and taken home. We are simply spinning our wheels. In your system, b43 and wl were arguing and meanwhile, the mp3s and emails to Mom and Youtube videos are not being accessed.

I'm glad it's working. We knew you could do it!

---

### Post by KittyCatHerder on 2013-03-27
> **chili555 said:**
> Almost. Your device, 14e4:4727, is claimed by two different drivers, also known in Linux as modules. Fun, fun, fun, eh?

The trick is to find out which module; wl or b43, drives your device correctly. Hadaka and I know from many years and many posts of experience, that it's wl. The problem is made tougher because the sharp guys and gals generally have tried a few things and made the process worse because we have to diagnose and fix the previous attempts. Your problem was two-fold. Your /etc/modules file loaded the wrong driver, b43 and your /etc/modprobe.d/blacklist.conf attempted to blacklist it to *never* load! Very confusing! Once Hadaka and you discovered and corrected it, everything started working smoothly.

I'm glad it's working. We knew you could do it!

That's a good way to explain what was happening. I understand the concept pretty well now, I think. I'm afraid I couldn't do it as you suggest though. I had very little idea of what was happening. I get it now though and I've already learned quite a lot about the way this part of the OS works. 

Does the /etc/modules file contain every module that gets loaded on boot?

As I understand, the wl driver causes the (this) WiFi card to be identified as "eth" instead of "wlan". I am quite OCD about my computers and I would really like to have the wlan card show up as wlan. If wlan shows up as eth by design, and it is not a flaw of some sort, it wouldn't be a big deal but I would like to understand why it happens that way.

Thanks a lot for helping with (solving) my WiFi problem. I've learned quite a lot already and I feel like this is the kind of place I can learn as much as I want. I will be looking for answers to several other issues I'm having in the next day or two and if I can't find solutions already posted here I hope you and Hadaka can help me with those as well.

---

### Post by KittyCatHerder on 2013-03-27
I've been trying to figure out hwo to mark this thread as solved for 6 or 7 minutes. Can someone please tell me how to do that?

---

### Post by chili555 on 2013-03-27
> Does the /etc/modules file contain every module that gets loaded on boot?No, it contains those that are lazy or troublesome and for which we wish to demand that they load no matter what. > If wlan shows up as eth by design, and it is not a flaw of some sort, It is exactly that; by design. It is hard-coded somewhere in the module by the author, Broadcom. This has been a tug of war for years in Linux. When I first started, all wireless was eth1. Then it became wlan0 and in some cases wifi0. Sadly, for those of us that prize uniformity and order in our lives, it is anything but! 

There is a mysterious parameter available in wl and I have been looking for a tester. Are you game?```
chili@Think60:~$ modinfo wl
filename:       /lib/modules/3.5.0-26-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     1C6A0B8B0000A8D58131D83
<snip>
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
[COLOR="#FF0000"]parm:           name:string[/COLOR]
```Intriguing, isn't it??

---

### Post by KittyCatHerder on 2013-03-27
> **Hadaka said:**
> Hi, whew..finally Glad its working !
Yes there is always alot to learn about the operating system.
do this code:lsmod...(which is list-modules) you will see modules
for video,wireless,wired and many other devices and cards within
the computer. these modules are a set of instructions they tell the
code:lspci..(list pci's) those are the hardware items that the modules
control.what to do and of course the modules must be compatable with the hardware
and they must also be able to give and pass information to the kernel
which is the heart of the system.Everything the system does and what it can do
is based on the kernel. Do a search on "How linux works" start small and simple
and build from there.There are also sections on this forum to discuss the how's
and why's. Good luck in continuing your knowledge. and PLEASE, mark this thread
SOLVED.
thanks.

Before yesterday or the day before I wasn't aware that the ls command could be used to list hardware and software. I thought it was only used for files and directories. I'll be using ls quite frequently over the next few days and probably into the future now that I understand it a little more completely.

Thanks for all the help and input so far. I hope you can join in on my future threads!

---

### Post by Hadaka on 2013-03-27
Hi,just to unwind a possible future confusion for you,
the command lspci (list pci;s) doesnt list the actual
hardware but rather the hardware's interface. as in
you can have a pci with no hardware attached to it
but it can accept an appropiate piece of hardware.
for example..lspci lists usb ports,yet no usb is plugged
in. It means the pci accepts usb type equipment-hardware
ls (list ) pci (peripheral Complex interfaces). Then when
a device,card is plugged in,it will pass information about
its self with the lspci query.
hope that helps.
also chili invited you to play with an entry for the wl module
so both you and he learn something new...you game?
 and lastly ..to mark SOLVED ,sign in ..this thread...click edit
then thread tools...thread tools is in the upper right corner...i think.
have fun !

---

### Post by KittyCatHerder on 2013-03-27
> **chili555 said:**
> No, it contains those that are lazy or troublesome and for which we wish to demand that they load no matter what. It is exactly that; by design. It is hard-coded somewhere in the module by the author, Broadcom. This has been a tug of war for years in Linux. When I first started, all wireless was eth1. Then it became wlan0 and in some cases wifi0. Sadly, for those of us that prize uniformity and order in our lives, it is anything but! 

There is a mysterious parameter available in wl and I have been looking for a tester. Are you game?```
chili@Think60:~$ modinfo wl
filename:       /lib/modules/3.5.0-26-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     1C6A0B8B0000A8D58131D83
<snip>
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
[COLOR=#FF0000]parm:           name:string[/COLOR]
```Intriguing, isn't it??

I would love to do any kind of testing related to Linux! I can't say I understand the output of modinfo wl but I am with the Linux community when it comes to this kind of issue. If a hardware company can't open source the driver software for use in open source operating systems then I am all for helping out with trying to find a better way than using their proprietary software. Let me knwo what I can do to help/test.

---

### Post by KittyCatHerder on 2013-03-28
> **Hadaka said:**
> Hi,just to unwind a possible future confusion for you,
the command lspci (list pci;s) doesnt list the actual
hardware but rather the hardware's interface. as in
you can have a pci with no hardware attached to it
but it can accept an appropiate piece of hardware.
for example..lspci lists usb ports,yet no usb is plugged
in. It means the pci accepts usb type equipment-hardware
ls (list ) pci (peripheral Complex interfaces). Then when
a device,card is plugged in,it will pass information about
its self with the lspci query.
hope that helps.
also chili invited you to play with an entry for the wl module
so both you and he learn something new...you game?
 and lastly ..to mark SOLVED ,sign in ..this thread...click edit
then thread tools...thread tools is in the upper right corner...i think.
have fun !

So listing pci shows all the pci's, not the hardware that is attached to the pci's, is there an option to list the hardware interfaced through the pci? Or does lspci list all pci interfaces as well as their connected hardware?

I have responded to Chilis post about the wl module. This is just the kind of thing I am trying to get into by using Ubuntu/Linux.  I ran modinfo wl and got a parm: intf_name:string which is a little different than his output. I'm waiting on some instructions from him to find out what to do to test the wl module.

---

### Post by KittyCatHerder on 2013-03-31
I guess no one is reading this thread any more. When a thread is marked as solved, does something happen that causes it to not be as visible, or do the contributors to the thread stop getting notifications that there are new posts in the thread?

---

### Post by chili555 on 2013-04-01
> **KittyCatHerder said:**
> I guess no one is reading this thread any more. When a thread is marked as solved, does something happen that causes it to not be as visible, or do the contributors to the thread stop getting notifications that there are new posts in the thread?I apologize. Occasionally, one gets away from me, especially when there are two people actively answering. Sometimes we assume the other guy got it.> I have responded to Chilis post about the wl module. This is just the kind of thing I am trying to get into by using Ubuntu/Linux. I ran modinfo wl and got a parm: intf_name:string which is a little different than his output. This is pretty advanced stuff. Very few people on this forum experiment with driver parameters and a few that do I suspect copied my old posts! 

First, let's double-check:```
modinfo wl
```If you confirm in your version the parameter is actually intf_name:string, then create a simple text file:```
gksudo gedit /etc/modprobe.d/wl.conf
```Add a single line:```
options wl  intf_name=wlan0
```Proofread carefully, save and close gedit. Reboot and run:```
iwconfig
```Is your wireless interface now known as wlan0? 

As I said previously, this is all pretty experimental. I will be fascinated to hear your result.

---


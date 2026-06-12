---
title: "new to ubuntu wireless troubles with Intel 3945ABG"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by rowico on 2011-05-03
Hi,

So I'm extremely new to Ubuntu, and I know almost nothing about it.  I installed Ubuntu 11.04 to my laptop (compaq presario v6000) and everything started up great except for the wireless, which may be something with the drivers or I'm just missing something obvious.

I've looked at many guides and threads and tried to follow them, but either get lost in the terminology or it doesn't seem to help. I know the wireless card is the Intel PRO/Wireless 3945ABG, if that helps at all.

Thanks!

---

### Post by chili555 on 2011-05-03
I have a 3945ABG and run 11.04. Let's see what's wrong. We're going to use the terminal (Applications > Accessories Terminal using Classic Ubuntu; or Applications > Terminal using Unity). I like the terminal because you can get a lot of information in a hurry. Anything in the code box is a terminal command. Enter each line one at a time and press Enter. Post the result. First, let's see what position the wireless switch is in:```
rfkill list all
```Next, let's see what interesting messages have been recorded about the driver iwl3945:```
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by rowico on 2011-05-03
> **chili555 said:**
> ```
rfkill list all
```
```
robert@Rowico:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
robert@Rowico:~$
```> **chili555 said:**
> ```
dmesg | grep iwl
```
returned nothing

---

### Post by chili555 on 2011-05-03
Let's load the module and see if that helps:```
sudo modprobe iwl3945
dmesg | grep iwl
lspci -nn | grep -i wireless
```Thanks.

---

### Post by rowico on 2011-05-03
Wow! That worked! It gave me the option in the connections button on the top bar to enable wireless then it automatically detected the network!  Thank you SO much!!!!
:D:D:D:D:D:D

---

### Post by chili555 on 2011-05-04
If it doesn't start automatically on reboot, post back and we'll fix it.

---

### Post by rowico on 2011-05-04
> **chili555 said:**
> If it doesn't start automatically on reboot, post back and we'll fix it.

Yep, it didn't start this morning.  

Thanks for all your help, I really appreciate it.

---

### Post by rowico on 2011-05-04
I just tried to in the same code from yesterday and it worked again, but am i going to have to do this each time?

---

### Post by chili555 on 2011-05-05
Let's see if we can make it persistent:```
sudo su
echo iwl3945 >> /etc/modules
exit
```Now does it start on boot?

---

### Post by rowico on 2011-05-05
> **chili555 said:**
> Let's see if we can make it persistent:```
sudo su
echo iwl3945 >> /etc/modules
exit
```Now does it start on boot?

It works! Thank you so much! :) :) :)

---

### Post by susie94 on 2011-05-10
I have a similar problem to rowico but the solution provided by chili555 does not work for me.  One difference is that the code 
rfkill list all
reveals that Yes is the condition for Hard Blocked

Not sure how to þroceed    Would welcome advice

---

### Post by chili555 on 2011-05-10
> **susie94 said:**
> I have a similar problem to rowico but the solution provided by chili555 does not work for me.  One difference is that the code 
rfkill list all
reveals that Yes is the condition for Hard Blocked

Not sure how to þroceed    Would welcome adviceDo you solemnly swear on my C/C++ Programmers Bible that the hardware switch on your laptop is set to 'ON?' What kind of laptop is it? May we see:```
lsmod
```

---

### Post by el cameleon on 2011-05-22
Hi,
I got the same problem here (Dell 1525 N Laptop with Intel 3945ABG wifi card) but adding **iwl3945** to the file **modules** doesn't help :-(

Here is the output of some commands:
```
vincent@Dell-Inspiron:~$ **rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````

vincent@Dell-Inspiron:~$ **lsmod**
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_intel          24140  1 
snd_hda_codec          90901  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
r852                   17878  0 
sm_common              16737  1 r852
dcdbas                 14054  1 dell_laptop
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
snd                    55295  12 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    26720  2 sm_common,nand
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
coretemp               13283  0 
arc4                   12473  2 
iwl3945               130113  0 
iwlcore               148965  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
cfg80211              156212  3 iwl3945,iwlcore,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
usbhid                 41704  0 
hid                    77084  1 usbhid
drm_kms_helper         40745  1 i915
ahci                   21591  2 
firewire_ohci          31504  0 
drm                   180037  4 i915,drm_kms_helper
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
sky2                   49172  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```Can someone help?

---

### Post by chili555 on 2011-05-22
@ el cameleon--

Please post:```
dmesg -e iwl -e wlan
```Thanks.

---

### Post by el cameleon on 2011-05-22
Unfortunately, it doesn't seems to be valid....

```
vincent@Dell-Inspiron:~$ dmesg -e iwl -e wlan
dmesg : option invalide -- 'e'
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
```

---

### Post by chili555 on 2011-05-22
Well, I'm sorry. I made a slight error. Please post:```
dmesg | grep -e iwl -e wlan
```

---

### Post by el cameleon on 2011-05-22
It's better ;-)
```
vincent@Dell-Inspiron:~$ dmesg | grep -e iwl -e wlan
[   22.195798] iwl3945: Unknown parameter `#'
[   23.473286] iwl3945: Unknown parameter `#'
```

---

### Post by chili555 on 2011-05-22
> iwl3945: Unknown parameter `#'There ought to be way more than that:```
dmesg | grep iwl
ls /etc/modprobe.d
```That's a message I have never seen before, frankly.

---

### Post by el cameleon on 2011-05-22
I am sorry, I have already tried quit a lot of solutions and I am afraid that my installation is now quite a mess. If you think it would be simplier to restart from a fresh install, don't hesitate to tell me, I will try to do it in the week.

Then, to answer your question: 
```
vincent@Dell-Inspiron:~$ dmesg | grep iwl
[   25.859522] iwl3945: Unknown parameter `#'
[   27.345339] iwl3945: Unknown parameter `#'

vincent@Dell-Inspiron:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         iwl3945.conf
blacklist.conf           blacklist-oss.conf           libpisock9.conf
blacklist-firewire.conf  blacklist-rare-network.conf
vincent@Dell-Inspiron:~$ 
```Note that  iwl3945.conf is a file created by myself following some obscurs instruction that I don't remenber and that contain this line:
> alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1   # <-- enables software scanning

---

### Post by chili555 on 2011-05-22
Please amend it to:```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```Then do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945
```Any improvement?> I have already tried quit a lot of solutions and I am afraid that my installation is now quite a mess. If you think it would be simplier to restart from a fresh install, don't hesitate to tell meLet's see if we can't fix it first.

---

### Post by el cameleon on 2011-05-23
Hum...
First, thanks a lot for your kindest help. However, I didn't succeed to fix the issue:
> Please amend it to:     Code:
     alias wlan0 iwl3945 options iwl3945 disable_hw_scan=1
=> This is the same that what was existing in the file, so no changes from that side.

> Then do:     Code:
     sudo rmmod -f iwl3945 sudo modprobe iwl3945
I got some errors:
```
vincent@Dell-Inspiron:~$ sudo rmmod -f iwl3945
ERROR: Removing 'iwl3945': No such file or directory
vincent@Dell-Inspiron:~$ sudo rmmod -f /etc/modprobe.d/iwl3945
ERROR: Removing 'iwl3945': No such file or directory
vincent@Dell-Inspiron:~$ sudo rmmod -f /etc/modprobe.d/iwl3945.conf
ERROR: Removing 'iwl3945': No such file or directory
vincent@Dell-Inspiron:~$ sudo rmmod -f /etc/modprobe.d/iwl3945.conf
ERROR: Removing 'iwl3945': No such file or directory
vincent@Dell-Inspiron:~$ sudo modprobe iwl3945
```The wifi still doesn't work :-( I am currently thinking of a way to be sure to save all my data before engaging a fresh new install.

---

### Post by chili555 on 2011-05-23
> This is the same that what was existing in the file, so no changes from that side.But that's *not* what you said before:> Note that iwl3945.conf is a file created by myself following some obscurs instruction that I don't remenber and that contain this line:
Quote:
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 # <-- enables software scanningSo which is correct? Does your file contain this part or not?>  # <-- enables software scanningPlease do:```
sudo gedit /etc/modprobe.d/iwl3945.conf
```Make sure it reads exactly like this and no more and no less:```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```To be perfectly clear, the # and all parts following must be removed entirely.> sudo rmmod -f /etc/modprobe.d/iwl3945Nobody asked you to do this.> sudo rmmod -f /etc/modprobe.d/iwl3945.confNobody asked you to do this.

You can't just make up new commands at random, execute them and then be surprised that the underlying problem isn't fixed. You will only make your system worse or even unbootable.

Please fix your /etc/modprobe.d/iwl3945.conf file, reboot and let's see:```
dmesg | grep iwl
```

---

### Post by el cameleon on 2011-05-23
> **chili555 said:**
> Please fix your /etc/modprobe.d/iwl3945.conf file, reboot and let's see:```
dmesg | grep iwl
```
Ok, and sorry for the misunderstood. Here is the result:```

vincent@Dell-Inspiron:~$ dmesg | grep iwl
[   22.440642] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   22.440646] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   22.440704] iwl3945 0000:0b:00.0: sw scan support is deprecated
[   22.440731] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.440745] iwl3945 0000:0b:00.0: setting latency timer to 64
[   22.501181] iwl3945 0000:0b:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.501186] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   22.501343] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[   22.700362] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
```

And it is now working!!! =D>
Many thanks, you are my hero (for some minutes at least ;-) !

Hope this will be fixed in the official release of Ubuntu quickly because it is not very easy to fix...

---

### Post by chili555 on 2011-05-23
> And it is now working!!! Great news! Post back if we can help you further.

---

### Post by dwilley on 2011-05-30
I installed Ubuntu 11.04 on a Compaq Presario V6000 and the wireless is not working. i'm also new to the whole Linux/Ubuntu thing.

Here's what i got so far:
[Screenshot]("http://www.northcarolinakia.com/pics/IMG_7511.JPG")

From what i can tell, there's files missing?

---

### Post by chili555 on 2011-05-30
The command is:```
sudo modprobe iw[COLOR="Red"]l[/COLOR]3945
```That's a lower-case L there and not the pipe symbol | that's on my US keyboard with \. If your card and driver are working correctly, it should already be loaded. What kind of trouble are you having?

By the way, I saw the command: sudo apt-get install udo

If you keep running commands randomly that you don't understand, you will soon wreck your system. If in doubt, stop and post a question. I'll try to answer as fast as I can, but I do stop to sleep and eat.

---

### Post by dwilley on 2011-05-30
i clicked on the pie shaped icon in the top right hand corner to access the networking and tried to connect to my wireless network but it's not showing anything in the wireless.

---

### Post by chili555 on 2011-05-30
Please let us see:```
lspci -nn
```That's one command on one line. A screenshot as before is fine.

---

### Post by dwilley on 2011-05-30
[Screenshot 2](http://www.northcarolinakia.com/pics/IMG_7512.JPG)

---

### Post by chili555 on 2011-05-30
> **dwilley said:**
> typed in the command you gave me and nothing happened. it just went to a blank line with "user@user-Presario-V6000-RG390UA-ABA:~$"Are you quite sure you typed it correctly?```
[COLOR="Red"]l[/COLOR]spci -nn
```Again, that's a lower-case L.

---

### Post by chili555 on 2011-05-30
Well, you do not have an Intel 3945ABG wireless card; you have a Broadcom BCM4311 (14E4:4311). Please start a new thread and reference your Broadcom BCM4311. Also tell us if you can temporarily get an ethernet connection. I'll watch for your thread in the morning.

------------
sudo apt-get install b43-fwcutter

---

### Post by Sef on 2011-05-30
> ...you have a Broadcom BCM4311.... 

Read post #1 in this [thread]("http://ubuntuforums.org/showthread.php?t=1604868").

---

### Post by dwilley on 2011-05-30
i was able to get the wired ethernet to connect to the internet. will create a new thread for my issue.

---

### Post by dwilley on 2011-05-30
> **Sef said:**
> Read post #1 in this [thread]("http://ubuntuforums.org/showthread.php?t=1604868").

just tried that and an error came up and said it couldn't be installed.

---

### Post by ghosh_rajk on 2011-06-04
@chili555 : Excellent!!!!Thanks you so much. Your solution has worked out perfectly for me. My Intel 3945 is online again.

---

### Post by hakonst on 2011-07-26
Hi - Im also having trouble with connecting with wireless network connection - I have the Intel 3945ABG  (im quite shore) and running Ubuntu 11.04. I have tried to follow the guidance here above but my wireless connection is not connecting :(

---

### Post by chili555 on 2011-07-26
> **hakonst said:**
> Hi - Im also having trouble with connecting with wireless network connection - I have the Intel 3945ABG  (im quite shore) and running Ubuntu 11.04. I have tried to follow the guidance here above but my wireless connection is not connecting :(Please open a terminal and run and post:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by hakonst on 2011-07-27
Thanks for a quick response chili555

hakonklara@hakonklara-laptop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

and 

hakonklara@hakonklara-laptop:~$ dmesg | grep iwl
[   11.931680] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.931685] iwl3945: Copyright(c) 2003-2010 Intel Corporation
hakonklara@hakonklara-laptop:~$

---

### Post by chili555 on 2011-07-27
The first part is perfect. No hardware switch or software is stopping your wireless. The dmesg part is sparse. Do you have a wireless interface?```
iwconfig
```Does it try to connect and fail? Do networks appear in Network Manager?```
sudo iwlist wlan0 scan
```Is your ESSID hidden?

---

### Post by hakonst on 2011-07-27
Yes I had tried to put those two commands in and the dmesg looked strange, here is the next information

> Do you have a wireless interface?hakonklara@hakonklara-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Something strange here...

> Does it try to connect and fail? Do networks appear in Network Manager?hakonklara@hakonklara-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for hakonklara: 
wlan0     Interface doesn't support scanning.

> Is your ESSID hidden?My SSID is not hidden (is that the same?) but you have to write WEP key to connect

---

### Post by chili555 on 2011-07-27
The dmesg does look strange indeed. However, it gives us a clue as to why when the driver iwl3945 tries to load, it fails and no wireless interface gets created. Please try again and post everything that appears:```
dmesg | grep -e iwl -e 80211
```Something is not right under the hood and the parts that "look strange' are what we need to know to fix it.

---

### Post by hakonst on 2011-07-27
Here are the results for
dmesg | grep -e iwl -e 80211
hakonklara@hakonklara-laptop:~$ dmesg | grep -e iwl -e 80211
[   11.591554] cfg80211: Calling CRDA to update world regulatory domain
[   11.779257] lib80211: common routines for IEEE802.11 drivers
[   11.779260] lib80211_crypt: registered algorithm 'NULL'
[   11.931680] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.931685] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   12.757645] cfg80211: World regulatory domain updated:
[   12.757650] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.757654] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.757657] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.757661] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.757665] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.757668] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
hakonklara@hakonklara-laptop:~$

---

### Post by chili555 on 2011-07-27
I still see no errors that we can fix and so no reason, so far, that it doesn't create a wireless interface and start. Let's take a look at complete logs. Please do:```
rfkill list all > hakonst.txt
lspci -nn | grep 0280 >> hakonst.txt
dmesg >> hakonst.txt
lsmod >> hakonst.txt
modinfo iwl3956 >> hakonst.txt
sudo cat /var/log/syslog | tail -n50 >> hakonst.txt
zip hakonst.zip hakonst.txt
```In your user directory, you will find a file, hakonst.zip. Attach it to your reply using the paperclip tool at the top of the reply box. Thanks.

---

### Post by hakonst on 2011-07-27
Here are the logs,
thanks
Hákon

---

### Post by chili555 on 2011-07-27
> I have the Intel 3945ABG (im quite shore) Your logs say:> 08:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)Would you please try:```
sudo rmmod -f iwl3945
sudo rmmod -f iwlcore
sudo modprobe wl
iwconfig
```Any errors or warnings? May we see:```
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

### Post by hakonst on 2011-07-27
Hmm...

When looking at the computer specs and trying some commands in the terminal I thought I had the Intel 3945ABG...

When running these commands:

sudo rmmod -f iwl3945 sudo rmmod -f iwlcore sudo modprobe wl iwconfig
I get:
hakonklara@hakonklara-laptop:~$ sudo rmmod -f iwl3945
[sudo] password for hakonklara: 
hakonklara@hakonklara-laptop:~$ sudo rmmod -f iwlcore
hakonklara@hakonklara-laptop:~$ sudo modprobe wl
hakonklara@hakonklara-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


####
and then when Í write the other commands
cat /etc/modprobe.d/blacklist.conf
I get:
hakonklara@hakonklara-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
hakonklara@hakonklara-laptop:~$ 

Thanks

---

### Post by chili555 on 2011-07-27
I suspect iwl3945 and therefor some conflicting modules are loading from /etc/modules. Please do:```
sudo gedit /etc/modules
```If you see iwl3945 in there, please remove it. Proofread, save and close gedit and reboot. Then let us see:```
iwconfig
lsmod | grep iwl
```Thanks.

---

### Post by hakonst on 2011-07-27
Mayday-mayday ubuntu crash :) reinstall in progress...

---

### Post by chili555 on 2011-07-27
??? What do you think happened? It surely wouldn't crash from editing /etc/modules.

---

### Post by hakonst on 2011-07-27
Hi - Ubuntu reinstalled (2x :(  ) both times some problems in rebooting but second time Ubuntu started at least...
not shore what happened, I took a photo of the screen after the reboot, see attached.

I ran the complete logs again in txt file, see as well attached as zip file.

Can you see what my next step should be?

thanks,
Hákon

---

### Post by chili555 on 2011-07-27
I don't quite understand. Are you now able to boot normally? I reviewed your logs and they look very good so far. The only thing I see that's suspicious is this:> Jul 27 23:07:50 hakonklara-laptop gnome-session[1219]: WARNING: Application 'compiz.desktop' failed to register before timeoutIt's a warning and not an error. You might Google the warning or ask on Desktop Environments: [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

Is there a wireless interface, eth1 perhaps?```
iwconfig
```Does it scan?```
sudo iwlist eth1 scan
```Substitute your wireless interface if it's not eth1.

---

### Post by hakonst on 2011-07-27
It reboots now because I reinstalled Ubuntu and wiped the hard drive clean... I will take a look at the warning you mentioned.

Here are the results from the commands:

hakonklara@hakonklara-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hakonklara@hakonklara-laptop:~$ sudo iwlist eth0 scan
[sudo] password for hakonklara: 
eth0      Interface doesn't support scanning.

hakonklara@hakonklara-laptop:~$ 

no wireless extensions or scanning :confused:

---

### Post by chili555 on 2011-07-27
How did you install the wireless driver *wl*? Through the Additional Drivers tool? May I see:```
sudo dpkg -s bcmwl-kernel-source
sudo dpkg -s dkms
```We're just interested in the first few lines; ideally:> $ sudo dpkg -s dkms
[sudo] password for chili: 
Package: dkms
Status: install [COLOR="Red"]ok installed[/COLOR]
This is my favorite problem; it looks perfect in every way, except it doesn't work.

---

### Post by hakonst on 2011-07-28
The Broadcom driver was automatically installed and I can see it through the Additional Drivers program.

The commands show that at least that the installation is ok:

hakonklara@hakonklara-laptop:~$ sudo dpkg -s bcmwl-kernel-source
[sudo] password for hakonklara: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3288
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 5.100.82.38+bdcom-0ubuntu3
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
hakonklara@hakonklara-laptop:~$ sudo dpkg -s dkms
Package: dkms
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 476
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2.1.1.2-5ubuntu1
Depends: module-init-tools, gcc, make | build-essential | dpkg-dev, coreutils (>= 7.4), patch
Recommends: fakeroot, menu | sudo, linux-headers-2.6-686 | linux-headers-2.6-amd64 | linux-headers-generic | linux-headers, linux-image
Conffiles:
 /etc/dkms/framework.conf 4e72dd99504978161b561f69256c1696
 /etc/dkms/template-dkms-mkdeb/debian/README.Debian 6707f5716bc3a2d65fa1b05d81ba8add
 /etc/dkms/template-dkms-mkdeb/debian/changelog f14e36c92f14270163eb20fa883d463e
 /etc/dkms/template-dkms-mkdeb/debian/compat 84bc3da1b3e33a18e8d5e1bdd7a18d7a
 /etc/dkms/template-dkms-mkdeb/debian/control 932cd11859c7c153a8c458325e74497f
 /etc/dkms/template-dkms-mkdeb/debian/copyright de471e376ba2c3886424b5c4649c42d6
 /etc/dkms/template-dkms-mkdeb/debian/dirs ea7a90f4a1be2e0054c3d4920c29e33f
 /etc/dkms/template-dkms-mkdeb/debian/postinst 9332e9792ca4b1d4f79a2f79fe32b9a3
 /etc/dkms/template-dkms-mkdeb/debian/prerm e7c0c39003edb2255d22a775efa907e5
 /etc/dkms/template-dkms-mkdeb/debian/rules c385ec9e8f6c6745ad9b9665c38cbd84
 /etc/dkms/template-dkms-mkdeb/Makefile d97acaeba72f667d3eb69695e9018243
 /etc/bash_completion.d/dkms 195bee4c5aa1c561f920d4322b6b8be6
 /etc/kernel/prerm.d/dkms 97139ec74350d65636320b76a11b1f47
 /etc/kernel/postinst.d/dkms a4c83e676c2d02e01eae1c0b94657594
 /etc/kernel/header_postinst.d/dkms a4c83e676c2d02e01eae1c0b94657594
Description: Dynamic Kernel Module Support Framework
 DKMS is a framework designed to allow individual kernel modules to be upgraded
 without changing the whole kernel. It is also very easy to rebuild modules as
 you upgrade kernels.
Homepage: [http://linux.dell.com/dkms](http://linux.dell.com/dkms)
Original-Maintainer: Dynamic Kernel Modules Support Team <pkg-dkms-maint@lists.alioth.debian.org>
hakonklara@hakonklara-laptop:~$ 

the question is... do I have the Broadcom or the Intell device?
thanks (a lot for all your help :) )

---

### Post by chili555 on 2011-07-28
You most certainly have a Broadcom. This is from the zips you've sent me:> Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)In bcmwl-kernel-source, the aliases contain:> modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, 
<snip>Also in your logs, I see:> [    8.920922] eth%d: [COLOR="RoyalBlue"]5.100.82.38[/COLOR] driver failed with code 21The part I highlighted relates to the bcmwl-kernel-source package:> Source: bcmwl
Version: [COLOR="RoyalBlue"]5.100.82.38[/COLOR]+bdcom-0ubuntu3
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headersYour device is also claimed by the other Broadcom driver combination, b43 and ssb. Let's try them instead. Please do:```
sudo su
apt-get remove --purge bcmwl-kernel-source
rmmod -f wl
rm /etc/modprobe.d/blacklist-bcm43.conf
echo  b43 >> /etc/modules
modprobe b43
iwconfig
exit
```Now is it working?

---

### Post by hakonst on 2011-07-28
I think were getting somewhere now....  now at least I'm getting the choice to enable wireless, here is the results - Im not connected yet though

hakonklara@hakonklara-laptop:~$ sudo su
[sudo] password for hakonklara: 
root@hakonklara-laptop:/home/hakonklara# apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 192 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131965 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
root@hakonklara-laptop:/home/hakonklara# rmmod -f wl
root@hakonklara-laptop:/home/hakonklara# rm /etc/modprobe.d/blacklist-bcm43.confrm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
root@hakonklara-laptop:/home/hakonklara# echo  b43 >> /etc/modules
root@hakonklara-laptop:/home/hakonklara# modprobe b43
root@hakonklara-laptop:/home/hakonklara# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@hakonklara-laptop:/home/hakonklara# exit
exit
hakonklara@hakonklara-laptop:~$ ^C

I also ran the scanning command

hakonklara@hakonklara-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

hakonklara@hakonklara-laptop:~$ 

What do you thing chili555?
Thanks.

---

### Post by chili555 on 2011-07-28
Please reboot and give me your report. If it isn't working, let's look at another log. Thanks.

---

### Post by hakonst on 2011-07-28
I have finished rebooting - still not connected...

---

### Post by chili555 on 2011-07-28
Let's see a log, please.

---

### Post by hakonst on 2011-07-28
Here are some logs... hope they are the right ones...
thanks

---

### Post by chili555 on 2011-07-28
We're almost there. Please open a terminal and do:```
sudo apt-get install firmware-b43-installer
```After it finishes, reboot and enjoy your wireless.

---

### Post by hakonst on 2011-07-28
Fantastic!! :) Its working - Thanks a million :popcorn:

---

### Post by chili555 on 2011-07-28
Glad it's working. Have fun!

---

### Post by raiden82 on 2011-09-16
Hi i have also the intel 3945 and doesn't work..on any distro, here's lspci:

[HTML]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
05:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controlle[/HTML]

tried the commands you've posted but only this one gives a result:
[HTML]
dmesg | grep -e iwl -e wlan[/HTML]

[HTML][   14.860438] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.860443] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[  553.937665] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  553.937670] iwl3945: Copyright(c) 2003-2010 Intel Corporation[/HTML]

any idea? thanks

---

### Post by chili555 on 2011-09-16
There is no sign of it in your lspci; I wonder if it's defective. What does this say?```
rfkill list all
lspci -nn | grep 0280
sudo lshw -C network
```Thanks.

---

### Post by wildmanne39 on 2011-09-16
Hi Dr. chili, we have been working on it here also if you want to look or you can just take it from here in this thread.
[http://ubuntuforums.org/showthread.php?t=1845131](http://ubuntuforums.org/showthread.php?t=1845131)
Thank you

---

### Post by siddi on 2011-11-21
Hi,
I have an acer aspire and I also have a terrible problem with the wireless... The main issue is that the wireless connection is getting connected but the connection keeps dropping every few seconds... Am not following the directions from the discussion here....

lsmod gave me the following......  Please help

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  8 
bnep                   17923  2 
binfmt_misc            17292  1 
joydev                 17393  0 
gspca_vc032x           31999  0 
gspca_main             27610  1 gspca_vc032x
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_usb_audio         100880  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
uvcvideo               67271  0 
snd_hda_intel          24262  7 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
pcmcia                 39822  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
tifm_7xx1              12937  0 
videodev               85626  2 gspca_main,uvcvideo
snd_pcm                80468  7 snd_hda_codec_si3054,snd_usb_audio,snd_hda_intel,snd_hda_codec
tifm_core              15040  1 tifm_7xx1
arc4                   12473  2 
iwl3945                73329  0 
snd_seq_midi           13132  0 
iwl_legacy             71499  1 iwl3945
btusb                  18160  2 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
bluetooth             148839  23 rfcomm,bnep,btusb
psmouse                73673  0 
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac80211              272785  2 iwl3945,iwl_legacy
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  25 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 acer_wmi
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0



lspci gave the following

siddharth@siddharth-Aspire-5570:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Coltsfan19 on 2011-12-17
[FONT=Batang][SIZE=3]Please help i cannot get on my wireless ive read forums and tried[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT] 
[FONT=Batang][SIZE=3]trav@trav-HP-Pavilion-dv6000-RG360UA-ABA:~$ sudo modprobe iwl3945[/SIZE][/FONT]
[FONT=Batang][SIZE=3][sudo] password for trav:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]trav@trav-HP-Pavilion-dv6000-RG360UA-ABA:~$ dmesg | grep iwl[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934588] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934593] iwl3945: Copyright(c) 2003-2011 Intel Corporation[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934686] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934702] iwl3945 0000:02:00.0: setting latency timer to 64[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975682] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975687] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975848] iwl3945 0000:02:00.0: irq 43 for MSI/MSI-X[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   14.002439] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   14.947623] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9[/SIZE][/FONT]
[FONT=Batang][SIZE=3]trav@trav-HP-Pavilion-dv6000-RG360UA-ABA:~$ lspci -nn | grep -i wireless[/SIZE][/FONT]
[FONT=Batang][SIZE=3]02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]trav@trav-HP-Pavilion-dv6000-RG360UA-ABA:~$ rfkill list all[/SIZE][/FONT]
[FONT=Batang][SIZE=3]0: phy0: Wireless LAN[/SIZE][/FONT]
[SIZE=3][FONT=Batang]            Soft blocked: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]            Hard blocked: no[/FONT][/SIZE]
[FONT=Batang][SIZE=3]1: hp-wifi: Wireless LAN[/SIZE][/FONT]
[SIZE=3][FONT=Batang]            Soft blocked: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]            Hard blocked: no[/FONT][/SIZE]
[FONT=Batang][SIZE=3]trav@trav-HP-Pavilion-dv6000-RG360UA-ABA:~$ dmesg | grep -e iwl -e wlan[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934588] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934593] iwl3945: Copyright(c) 2003-2011 Intel Corporation[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934686] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.934702] iwl3945 0000:02:00.0: setting latency timer to 64[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975682] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975687] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   13.975848] iwl3945 0000:02:00.0: irq 43 for MSI/MSI-X[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   14.002439] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   14.947623] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   15.019245] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   20.573602] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   20.776084] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   20.976052] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   21.176042] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   28.552810] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   28.752127] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   28.952116] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   29.152116] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   36.516592] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   36.720062] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   36.920067] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   37.120066] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   44.500268] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   44.700084] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   44.900069] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   45.100052] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   52.484230] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   52.684057] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   52.884090] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   53.084074] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   60.460353] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   60.660069] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   60.860074] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   61.060071] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   68.428472] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   68.628129] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   68.828141] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   69.028132] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   76.404744] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   76.604169] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   76.804134] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][   77.004072] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  133.504660] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  133.704123] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  133.904082] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  134.104082] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  141.476367] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  141.676072] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  141.876085] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  142.076097] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  149.453219] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  149.652082] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  149.852061] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  150.052065] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  157.419995] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  157.620049] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  157.820060] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  158.020037] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  165.404505] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  165.604167] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  165.804084] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  166.004084] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  173.380437] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  173.580110] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  173.780130] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  173.980091] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  181.361177] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  181.560139] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  181.760287] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  181.960388] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  189.341249] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  189.540050] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  189.740076] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  189.940057] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  460.536306] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  460.736106] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  460.936090] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  461.136215] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  468.499705] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  468.696171] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  468.896081] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  469.096193] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  476.472833] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  476.672079] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  476.872089] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  477.072070] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  484.457360] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  484.656181] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  484.856144] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  485.056203] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  492.442668] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  492.640234] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  492.840226] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  493.040178] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  500.408902] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  500.608184] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  500.808199] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  501.008098] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  508.373138] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  508.572072] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  508.772203] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  508.972075] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  516.356621] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  516.556184] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  516.756183] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  516.956132] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  527.432409] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  527.636084] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  527.836059] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  528.036070] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  535.417637] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  535.616171] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  535.816140] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  536.016160] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  543.401474] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  543.600219] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  543.800242] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  544.000185] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  551.372644] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  551.572194] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  551.772163] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  551.972160] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  559.337440] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  559.536153] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  559.736189] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  559.936149] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  567.308417] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  567.508120] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  567.708060] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  567.908061] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  575.317209] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  575.516090] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  575.718251] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  575.916114] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  583.300610] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  583.500181] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  583.700240] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  583.900229] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  595.032475] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  595.232103] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  595.432073] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  595.632102] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  603.004187] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  603.208069] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  603.408088] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  603.608065] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  611.009201] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  611.208169] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  611.408218] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  611.608181] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  618.977261] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  619.176167] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  619.376198] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  619.576180] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  626.954525] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  627.152181] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  627.352228] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  627.552444] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  634.940656] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  635.140056] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  635.340074] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  635.540074] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  639.104898] iwl3945 0000:02:00.0: Card state received: HW:Kill SW:On[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  639.124213] iwl3945 0000:02:00.0: Not sending command - RF KILL[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  639.124227] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  639.124236] iwl3945 0000:02:00.0: Error setting new configuration (-5).[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  639.128153] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  693.066568] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  698.628610] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  698.828193] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  699.028189] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  699.228216] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  706.609575] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  706.808094] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  707.008067] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  707.208077] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  714.592659] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  714.792170] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  714.992189] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  715.192164] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  722.564563] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  722.764213] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  722.964243] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  723.164215] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  730.536615] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  730.736190] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  730.936133] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  731.136183] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  738.506629] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  738.704172] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  738.904229] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  739.104141] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  746.472494] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  746.672181] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  746.872196] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  747.072206] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  754.443398] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 1/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  754.643770] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 2/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  754.844070] wlan0: direct probe to f8:7b:7a:4f:8f:56 (try 3/3)[/SIZE][/FONT]
[FONT=Batang][SIZE=3][  755.048066] wlan0: direct probe to f8:7b:7a:4f:8f:56 timed out[/SIZE][/FONT]

---

### Post by chili555 on 2011-12-18
Let's also see:```
sudo iwlist wlan0 scan
iwconfig wlan0
```Actually, so far, things are looking good!

---

### Post by irtehun on 2011-12-30
I'm having issues with this as well. 
Here is a printout of all the commands I have seen and what they do

mint@mint ~ $ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mint@mint ~ $ dmesg | grep iwl
mint@mint ~ $ sudo modprobe iwl3945
mint@mint ~ $ dmesg | grep iwl
[ 1959.812270] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1959.812277] iwl3945: Copyright(c) 2003-2011 Intel Corporation
mint@mint ~ $ lspci -nn | grep -i wireless
mint@mint ~ $ dmesg | grep -e iwl -e wlan
[ 1959.812270] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1959.812277] iwl3945: Copyright(c) 2003-2011 Intel Corporation
mint@mint ~ $ dmesg | grep iwl
[ 1959.812270] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1959.812277] iwl3945: Copyright(c) 2003-2011 Intel Corporation
mint@mint ~ $ ls /etc/modprobe.d
alsa-base.conf             blacklist-framebuffer.conf
blacklist-ath_pci.conf     blacklist-modem.conf
blacklist.conf             blacklist-oss.conf
blacklist-cups-usblp.conf  blacklist-rare-network.conf
blacklist-firewire.conf    blacklist-watchdog.conf

irtehun@irtehun-Precision-M65 ~ $ dmesg | grep -e iwl -e 80211
[  149.885728] cfg80211: Calling CRDA to update world regulatory domain
[  150.002069] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  150.002076] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  150.029384] cfg80211: World regulatory domain updated:
[  150.029392] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  150.029399] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  150.029405] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  150.029411] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  150.029416] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  150.029422] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

Nomatter what i do, i cannot get it to show any wireless connections

---

### Post by chili555 on 2011-12-30
How about letting us see:```
lspci -nn | grep 0280
cat /etc/network/interfaces
```Thanks.

---

### Post by irtehun on 2011-12-30
lspci -nn | grep 0280 

comes back blank.

cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by chili555 on 2011-12-30
> **irtehun said:**
> lspci -nn | grep 0280 

comes back **blank**.That implies you have *no* wireless card! Let's dig deeper:```
lsusb
sudo lshw -C network
```Thanks.

---

### Post by Mayz on 2012-01-17
Hello I have problem with mine wireless connection.

I have Intel 3945ABG etc... Tried all kind of things (I hope that didn't tried to much, I did things what I think that I understood.)
I use Ubuntu 11.10 with Toshiba Tecra A6

In the network thing next to clock, I have wireless networks, but it's unchooseable. And says something like this (mine Ubuntu is Finnish) 

Wireless connections
Device isn't ready

```
olli@Olli-PC:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:9f:9c:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-14-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:d0100000-d0100fff

```

Ah, and I _have_ checked: Use wireless networks...

```
olli@Olli-PC:~$ dmesg | grep iwl3945
[   19.372102] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   19.372107] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   19.372186] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.372202] iwl3945 0000:03:00.0: setting latency timer to 64
[   19.427919] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.427925] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.428121] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
[   20.252699] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   20.520227] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[   20.520239] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   20.520277] iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   20.520285] iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   20.520292] iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[   20.520523] iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000201098 0x008B6 0x00274 0x00320 0x085FE 116
[   20.520660] iwl3945 0000:03:00.0: Start IWL Event Log Dump: display last 20 count
[   20.520706] iwl3945 0000:03:00.0: 0000200783    0x000000d9    0106
[   20.520732] iwl3945 0000:03:00.0: 0000200785    0x00000000    0302
[   20.520759] iwl3945 0000:03:00.0: 0000200820    0x00000ece    0353
[   20.520786] iwl3945 0000:03:00.0: 0000200836    0x000000d9    0106
[   20.520812] iwl3945 0000:03:00.0: 0000200837    0x00000000    0302
[   20.520839] iwl3945 0000:03:00.0: 0000200873    0x00000ecf    0353
[   20.520866] iwl3945 0000:03:00.0: 0000200888    0x000000d9    0106
[   20.520892] iwl3945 0000:03:00.0: 0000200890    0x00000000    0302
[   20.520919] iwl3945 0000:03:00.0: 0000200926    0x00000ed0    0353
[   20.520945] iwl3945 0000:03:00.0: 0000200941    0x000000d9    0106
[   20.520972] iwl3945 0000:03:00.0: 0000200943    0x00000000    0302
[   20.520999] iwl3945 0000:03:00.0: 0000200979    0x00000ed1    0353
[   20.521027] iwl3945 0000:03:00.0: 0000200994    0x000000d9    0106
[   20.521054] iwl3945 0000:03:00.0: 0000200996    0x00000000    0302
[   20.521080] iwl3945 0000:03:00.0: 0000201031    0x00000ed2    0353
[   20.521107] iwl3945 0000:03:00.0: 0000201047    0x000000d9    0106
[   20.521134] iwl3945 0000:03:00.0: 0000201048    0x00000000    0302
[   20.521161] iwl3945 0000:03:00.0: 0000201084    0x00000ed3    0353
[   20.521187] iwl3945 0000:03:00.0: 0000201096    0x00000002    0123
[   20.521214] iwl3945 0000:03:00.0: 0000201099    0x00000100    0125
[   20.521237] iwl3945 0000:03:00.0: Error Reply type 0x00000005 cmd REPLY_RXON (0x10) seq 0x0401 ser 0x00740000
[   20.521254] iwl3945 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   20.521263] iwl3945 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   20.521273] iwl3945 0000:03:00.0: Error setting Tx power (-5).
[   21.020066] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[   21.024436] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[   21.024541] iwl3945 0000:03:00.0: Try to add interface when device not ready
[   21.323762] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[   21.323771] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   21.323808] iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   21.323814] iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   21.323820] iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[   21.324061] iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000201093 0x008B6 0x00274 0x0031C 0x0874C 116
[   21.324210] iwl3945 0000:03:00.0: Start IWL Event Log Dump: display last 20 count
[   21.324251] iwl3945 0000:03:00.0: 0000200779    0x000000d9    0106

```

And that just continues... I just feel like that I have made something wrong, but it have been from the start that way. It tried connect via Wireless during installation.

-Mayz

---

### Post by chili555 on 2012-01-17
It is trying to load the required firmware and then starts reporting errors. Let's see if your firmware is in place and not corrupted in some way. Please run and post:```
md5sum /lib/firmware/iwlwifi-3945-2.ucode
dmesg | grep 03:00
```



--------------

note to Chili: 4df235482ac6c083e2b51cfb4d85c0fd

---

### Post by Mayz on 2012-01-18
```
olli@Olli-PC:~$ md5sum /lib/firmware/iwlwifi-3945-2.ucode
4df235482ac6c083e2b51cfb4d85c0fd  /lib/firmware/iwlwifi-3945-2.ucode
``````
olli@Olli-PC:~$ dmesg | grep 03:00
[    0.231437] pci 0000:03:00.0: [8086:4222] type 0 class 0x000280
[    0.231494] pci 0000:03:00.0: reg 10: [mem 0xd0100000-0xd0100fff]
[    0.232183] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.232197] pci 0000:03:00.0: PME# disabled
[    0.232269] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[   19.585863] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.585879] iwl3945 0000:03:00.0: setting latency timer to 64
[   19.780563] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.780569] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.780726] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
[   20.679341] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   20.949063] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[   20.949070] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   20.949103] iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   20.949107] iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   20.949110] iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[   20.949335] iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000202389 0x008B6 0x00274 0x00320 0x0860E 116
[   20.949464] iwl3945 0000:03:00.0: Start IWL Event Log Dump: display last 20 count
[   20.949505] iwl3945 0000:03:00.0: 0000202074    0x000000d9    0106
[   20.949528] iwl3945 0000:03:00.0: 0000202076    0x00000000    0302
[   20.949551] iwl3945 0000:03:00.0: 0000202111    0x00000ece    0353
[   20.949574] iwl3945 0000:03:00.0: 0000202127    0x000000d9    0106
[   20.949596] iwl3945 0000:03:00.0: 0000202128    0x00000000    0302
[   20.949619] iwl3945 0000:03:00.0: 0000202164    0x00000ecf    0353
[   20.949642] iwl3945 0000:03:00.0: 0000202179    0x000000d9    0106
[   20.949665] iwl3945 0000:03:00.0: 0000202181    0x00000000    0302
[   20.949688] iwl3945 0000:03:00.0: 0000202217    0x00000ed0    0353
[   20.949710] iwl3945 0000:03:00.0: 0000202232    0x000000d9    0106
[   20.949733] iwl3945 0000:03:00.0: 0000202234    0x00000000    0302
[   20.949756] iwl3945 0000:03:00.0: 0000202269    0x00000ed1    0353
[   20.949779] iwl3945 0000:03:00.0: 0000202285    0x000000d9    0106
[   20.949802] iwl3945 0000:03:00.0: 0000202286    0x00000000    0302
[   20.949825] iwl3945 0000:03:00.0: 0000202322    0x00000ed2    0353
[   20.949847] iwl3945 0000:03:00.0: 0000202337    0x000000d9    0106
[   20.949870] iwl3945 0000:03:00.0: 0000202339    0x00000000    0302
[   20.949893] iwl3945 0000:03:00.0: 0000202375    0x00000ed3    0353
[   20.949915] iwl3945 0000:03:00.0: 0000202387    0x00000002    0123
[   20.949938] iwl3945 0000:03:00.0: 0000202390    0x00000100    0125
[   20.949958] iwl3945 0000:03:00.0: Error Reply type 0x00000005 cmd REPLY_RXON (0x10) seq 0x0401 ser 0x00740000
[   20.949978] iwl3945 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   20.949984] iwl3945 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   20.949989] iwl3945 0000:03:00.0: Error setting Tx power (-5).
[   21.448140] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[   21.452425] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[   21.452516] iwl3945 0000:03:00.0: Try to add interface when device not ready
[   21.771713] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[   21.771723] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   21.771760] iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   21.771766] iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   21.771772] iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[   21.772001] iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000201145 0x008B6 0x00274 0x00320 0x08602 116
[   21.772168] iwl3945 0000:03:00.0: Start IWL Event Log Dump: display last 20 count
[   21.772209] iwl3945 0000:03:00.0: 0000200830    0x000000d9    0106
[   21.772232] iwl3945 0000:03:00.0: 0000200832    0x00000000    0302
[   21.772255] iwl3945 0000:03:00.0: 0000200867    0x00000ece    0353
[   21.772278] iwl3945 0000:03:00.0: 0000200883    0x000000d9    0106
[   21.772300] iwl3945 0000:03:00.0: 0000200884    0x00000000    0302
[   21.772323] iwl3945 0000:03:00.0: 0000200920    0x00000ecf    0353
[   21.772346] iwl3945 0000:03:00.0: 0000200935    0x000000d9    0106
[   21.772369] iwl3945 0000:03:00.0: 0000200937    0x00000000    0302
[   21.772392] iwl3945 0000:03:00.0: 0000200973    0x00000ed0    0353
[   21.772414] iwl3945 0000:03:00.0: 0000200988    0x000000d9    0106
[   21.772437] iwl3945 0000:03:00.0: 0000200990    0x00000000    0302
[   21.772460] iwl3945 0000:03:00.0: 0000201026    0x00000ed1    0353
[   21.772483] iwl3945 0000:03:00.0: 0000201041    0x000000d9    0106
[   21.772506] iwl3945 0000:03:00.0: 0000201043    0x00000000    0302
[   21.772529] iwl3945 0000:03:00.0: 0000201078    0x00000ed2    0353
[   21.772551] iwl3945 0000:03:00.0: 0000201094    0x000000d9    0106
[   21.772574] iwl3945 0000:03:00.0: 0000201095    0x00000000    0302
[   21.772597] iwl3945 0000:03:00.0: 0000201131    0x00000ed3    0353
[   21.772620] iwl3945 0000:03:00.0: 0000201143    0x00000002    0123
[   21.772643] iwl3945 0000:03:00.0: 0000201146    0x00000100    0125
[   21.772660] iwl3945 0000:03:00.0: Error Reply type 0x00000005 cmd REPLY_RXON (0x10) seq 0x0401 ser 0x00740000
[   21.772671] iwl3945 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   21.772676] iwl3945 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   21.772681] iwl3945 0000:03:00.0: Error setting Tx power (-5).
[   21.777034] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[   21.777140] iwl3945 0000:03:00.0: Try to add interface when device not ready
[   22.043913] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[   22.043924] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   22.043960] iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   22.043966] iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   22.043972] iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[   22.044202] iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000201149 0x008B6 0x00274 0x0031C 0x086F6 116
[   22.044343] iwl3945 0000:03:00.0: Start IWL Event Log Dump: display last 20 count
[   22.044384] iwl3945 0000:03:00.0: 0000200834    0x000000d9    0106
[   22.044407] iwl3945 0000:03:00.0: 0000200836    0x00000000    0302
[   22.044430] iwl3945 0000:03:00.0: 0000200872    0x00000ece    0353
[   22.044452] iwl3945 0000:03:00.0: 0000200887    0x000000d9    0106
[   22.044475] iwl3945 0000:03:00.0: 0000200889    0x00000000    0302
[   22.044498] iwl3945 0000:03:00.0: 0000200924    0x00000ecf    0353
[   22.044521] iwl3945 0000:03:00.0: 0000200940    0x000000d9    0106
[   22.044543] iwl3945 0000:03:00.0: 0000200941    0x00000000    0302
[   22.044566] iwl3945 0000:03:00.0: 0000200977    0x00000ed0    0353
[   22.044589] iwl3945 0000:03:00.0: 0000200992    0x000000d9    0106
[   22.044611] iwl3945 0000:03:00.0: 0000200994    0x00000000    0302
[   22.044634] iwl3945 0000:03:00.0: 0000201030    0x00000ed1    0353
[   22.044657] iwl3945 0000:03:00.0: 0000201045    0x000000d9    0106
[   22.044679] iwl3945 0000:03:00.0: 0000201047    0x00000000    0302
[   22.044702] iwl3945 0000:03:00.0: 0000201083    0x00000ed2    0353
[   22.044725] iwl3945 0000:03:00.0: 0000201098    0x000000d9    0106
[   22.044747] iwl3945 0000:03:00.0: 0000201100    0x00000000    0302
[   22.044770] iwl3945 0000:03:00.0: 0000201135    0x00000ed3    0353
[   22.044793] iwl3945 0000:03:00.0: 0000201147    0x00000002    0123
[   22.044815] iwl3945 0000:03:00.0: 0000201150    0x00000100    0125
[   22.044834] iwl3945 0000:03:00.0: Error Reply type 0x00000005 cmd REPLY_RXON (0x10) seq 0x0401 ser 0x00740000
[   22.044851] iwl3945 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   22.044855] iwl3945 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   22.044860] iwl3945 0000:03:00.0: Error setting Tx power (-5).
[   22.049176] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[   22.049268] iwl3945 0000:03:00.0: Try to add interface when device not ready

```

I have just yesterday installed Ubuntu to this computer, should I just reinstall it now when I won't lose anything else than time? And I feel like that I would have reinstalled this allready with the time I tried to get WLAN work.

---

### Post by chili555 on 2012-01-18
I have been researching your issue extensively and will continue to do so. You have the latest firmware version, 15.32.2.9: [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

The md5sum is correct, suggesting that at least the firmware is not corrupted.

I suggest you try two things. First, from a terminal, do:```
dmesg
```Note the timestamp at the end so that, after the next steps, we can see what happens *after* the change.```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 disable_hw_scan=0
dmesg | grep -i iwl
```Is the firmware still not starting the card?

The other thing I suggest is to run your install CD as a live CD. Does the card work? If so, please re-install.

This exact card is near to my heart. Mine works perfectly every day.

---

### Post by AcidLauncheR on 2012-01-30
I tried running through the steps with no result, my wireless adaptor still shows device not ready. 

below are the outputs I'm getting:

> 
acidlauncher@AcidLauncheR:~$ rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
acidlauncher@AcidLauncheR:~$ dmesg |grep iwl
[   26.112178] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.112185] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   26.112271] iwl3945 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.112289] iwl3945 0000:0b:00.0: setting latency timer to 64
[   26.167007] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.167013] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.167171] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[   26.189240] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.549731] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   27.549953] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   28.650698] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   28.650948] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  127.192429] iwl3945 0000:0b:00.0: PCI INT A disabled
[  143.263750] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  143.263755] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  143.263861] iwl3945 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  143.263884] iwl3945 0000:0b:00.0: setting latency timer to 64
[  143.303928] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  143.303932] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  143.304136] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[  143.304621] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  143.335690] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[  143.335894] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  143.338846] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  143.338976] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
acidlauncher@AcidLauncheR:~$ 
acidlauncher@AcidLauncheR:~$ sudo modprobe iwl3945
[sudo] password for acidlauncher: 
WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: /etc/modprobe.d/iwl3945 line 2: ignoring bad line starting with 'iwl3945'
acidlauncher@AcidLauncheR:~$ dmesg |grep iwl
[   26.112178] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.112185] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   26.112271] iwl3945 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.112289] iwl3945 0000:0b:00.0: setting latency timer to 64
[   26.167007] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.167013] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.167171] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[   26.189240] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.549731] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   27.549953] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   28.650698] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   28.650948] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  127.192429] iwl3945 0000:0b:00.0: PCI INT A disabled
[  143.263750] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  143.263755] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  143.263861] iwl3945 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  143.263884] iwl3945 0000:0b:00.0: setting latency timer to 64
[  143.303928] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  143.303932] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  143.304136] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[  143.304621] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  143.335690] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[  143.335894] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  143.338846] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  143.338976] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
acidlauncher@AcidLauncheR:~$ lspci -nn | grep -i wireless
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
acidlauncher@AcidLauncheR:~$ 




I assume the problem lies with the line:

WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: /etc/modprobe.d/iwl3945 line 2: ignoring bad line starting with 'iwl3945'


ideas? Still blundering my way around Ubuntu and it's not pretty :)


thanks

---

### Post by siddi on 2012-01-30
mine connects, but drops every few minutes only to reconnect again.....and it keeps happening

---

### Post by chili555 on 2012-01-30
> I assume the problem lies with the line:

WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: /etc/modprobe.d/iwl3945 line 2: ignoring bad line starting with 'iwl3945'
Probably just a minor issue; let's have a look at:```
cat /etc/modprobe.d/iwl3945  
```The real problem is here:> Radio disabled by HW RF Kill switchThat means the little switch on your laptop that enables wireless is set to "Off." Can you flip it to "On?"

---

### Post by AcidLauncheR on 2012-01-30
> **chili555 said:**
> Probably just a minor issue; let's have a look at:```
cat /etc/modprobe.d/iwl3945  
```The real problem is here:That means the little switch on your laptop that enables wireless is set to "Off." Can you flip it to "On?"

> 
acidlauncher@AcidLauncheR:~$ cat /etc/modprobe.d/iwl3945
alias wlan0 iwl3945
iwl3945 disable_hw_scan=1
acidlauncher@AcidLauncheR:~$ 



I have the wireless switch on, I swear :D

Though I'm not going to rule out it being broken :(

---

### Post by chili555 on 2012-01-30
> acidlauncher@AcidLauncheR:~$ cat /etc/modprobe.d/iwl3945
alias wlan0 iwl3945
iwl3945 disable_hw_scan=1Please do:```
sudo mv /etc/modprobe.d/iwl3945 /etc/modprobe.d/iwl3945.conf
sudo gedit /etc/modprobe.d/iwl3945.conf
```Change the file to read:```
options iwl3945 disable_hw_scan=0
```The parameter 1 is default; if you are trying to *change* behavior, and I'm not sure I understand why, use 0. Proofread carefully, save and close gedit.

Let's see:```
rfkill list all
lsmod
```

---

### Post by AcidLauncheR on 2012-01-30
> **chili555 said:**
> Please do:```
sudo mv /etc/modprobe.d/iwl3945 /etc/modprobe.d/iwl3945.conf
sudo gedit /etc/modprobe.d/iwl3945.conf
```Change the file to read:```
options iwl3945 disable_hw_scan=0
```The parameter 1 is default; if you are trying to *change* behavior, and I'm not sure I understand why, use 0. Proofread carefully, save and close gedit.

Let's see:```
rfkill list all
lsmod
```

I'm seeing this right now:

> 
alias wlan0 iwl3945
iwl3945 disable_hw_scan=1


should I change it to read the options line exactly? add it? or replace only one line


figure I'd ask before I do

---

### Post by chili555 on 2012-01-30
> I'm seeing this right now:

Quote:
alias wlan0 iwl3945
iwl3945 disable_hw_scan=1
should I change it to read the options line exactly? add it? or replace only one line

To hopefully not be too blunt, please change it to exactly what I previously asked; no more and no less:```
options iwl3945 disable_hw_scan=0
```In order for it to take effect, the easiest way that's foolproof is to reboot.

---

### Post by AcidLauncheR on 2012-01-30
> **chili555 said:**
> [COLOR="Red"]To hopefully not be too blunt[/COLOR], please change it to exactly what I previously asked; no more and no less:```
options iwl3945 disable_hw_scan=0
```In order for it to take effect, the easiest way that's foolproof is to reboot.

not at all! 

here are the results:

> 
acidlauncher@AcidLauncheR:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
acidlauncher@AcidLauncheR:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
tpm_infineon           13200  0 
snd_hda_codec_idt      60049  1 
binfmt_misc            17292  1 
joydev                 17393  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
tpm_tis                14002  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509487  3 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
panasonic_laptop       13194  0 
sparse_keymap          13658  1 panasonic_laptop
arc4                   12473  2 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
iwl3945                73360  0 
drm_kms_helper         32889  1 i915
iwl_legacy             71499  1 iwl3945
mac80211              393459  2 iwl3945,iwl_legacy
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
psmouse                73673  0 
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
sky2                   49317  0 
acidlauncher@AcidLauncheR:~$ 



---

### Post by chili555 on 2012-01-30
Now that you've rebooted, are the RF switch messages still present?```
dmesg | grep -i switch
```Interestingly, rfkill list all looks perfect and there don't seem to be any driver or wmi issues.

Off to sleep; see you tomorrow.

---

### Post by AcidLauncheR on 2012-01-30
> **chili555 said:**
> Now that you've rebooted, are the RF switch messages still present?```
dmesg | grep -i switch
```Interestingly, rfkill list all looks perfect and there don't seem to be any driver or wmi issues.

Off to sleep; see you tomorrow.


RF switch messages are still the same

> 

acidlauncher@AcidLauncheR:~$ dmesg |grep -i switch
[    0.476248] Switching to clocksource hpet
[    0.479256] Switched to NOHz mode on CPU #0
[    0.479381] Switched to NOHz mode on CPU #1
[    0.672979] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.682579] ACPI: Lid Switch [LID]
[   27.345938] Console: switching to colour frame buffer device 128x48
[   27.896257] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   29.026287] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   29.026539] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
acidlauncher@AcidLauncheR:~$ 


I wouldn't put it past the switch or something on the inside being broken, this computer has been around the world and I haven't been all that gentle with it (it IS a toughbook, of course)

I appreciate the help, have a good night... I may just end up having to get a USB wifi adapter

---

### Post by chili555 on 2012-01-31
> **AcidLauncheR said:**
> 
I wouldn't put it past the switch or something on the inside being broken, this computer has been around the world and I haven't been all that gentle with it (it IS a toughbook, of course)

I appreciate the help, have a good night... I may just end up having to get a USB wifi adapterIf so, be sure to blacklist iwl3945. Also, if it were me, I'd get out my screwdriver.

---

### Post by AcidLauncheR on 2012-01-31
> **chili555 said:**
> If so, be sure to blacklist iwl3945. Also, if it were me, I'd get out my screwdriver.

I may do that, if it's just the switch I should be able to fix it pretty easy (it's an actual switch)


Thanks again for the help.... I'll post up results if I get them

---

### Post by chili555 on 2012-01-31
> I may do that, if it's just the switch I should be able to fix it pretty easy (it's an actual switch)I'd also re-seat the card and the antenna wires. If it's the switch itself, you can probably bypass it by shorting the connectors. It's clumsy but might save an old laptop. I love my old laptops! My machine containing an Intel 3945 is the *newer* of my current two!

Good luck!

---

### Post by MikeLeong on 2012-04-18
Hi, I am new to Ubuntu 11.10, just install it.

My wireless LAN intel 3945ABG doesn't want to be switched on, it's there in the network list, having hardware addreee, but Unavailable. Not possible to switch on and front indicator is also off. The toggle (both) for BT and Wireless LAN is on, and only BT light is on.

mariointas@mariointas-LENOVO3000-N200:~$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
mariointas@mariointas-LENOVO3000-N200:~$ 

Please help to identify this problem and thanks a lot!

---

### Post by chili555 on 2012-04-18
> Not possible to switch on and front indicator is also off.> 2: [COLOR="Red"]acer-wireless[/COLOR]: Wireless LAN
Soft blocked: yes
Hard blocked: noI suspect your answer is here: [http://ubuntuforums.org/showthread.php?t=1959458&highlight=Ideapad](http://ubuntuforums.org/showthread.php?t=1959458&highlight=Ideapad)

---

### Post by denP on 2012-09-17
I have fujitsu siemens amilo pro v3505 laptop.

I have two systems installed. They are:
- Ubuntu 12.04;
- Windows 7.

I do not have a special button to switch on / off the Wireless adapter. The button can be supported by drivers.

Case 1.

When I start Win7 WiFi is enabled (I had to install the driver to be able to switch it on automatically). I reboot and then WiFi is enabled for Ubuntu. It is not switched off during the reboot procedure.

Case 2.

I start Ubuntu. WiFi is switched off.

I have Intel PRO/Wireless 3945ABG [Golan]

Could you help me?

---

### Post by chili555 on 2012-09-17
Please start a new thread and with the wireless *NOT* working, post:```
rfkill list all
```Thanks.

---

### Post by denP on 2012-09-17
[http://ubuntuforums.org/showthread.php?p=12245186#post12245186](http://ubuntuforums.org/showthread.php?p=12245186#post12245186)

---


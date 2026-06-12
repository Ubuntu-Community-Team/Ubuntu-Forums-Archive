---
title: "dpkg error w/ troubleshooting Broadcom 43xx firmware issue"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by cj88 on 2011-07-24
Attempting solutions to Broadcom 43xx issues (described at [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868) and elsewhere).

I keep running into error messages with dpkg when I attempt to install suggested files:
"read error in '/var/lib/dpkg/triggers//File':input/output error"

Main problem is "wireless network device not ready (firmware missing)"

Laptop is Dell D610

Running Natty Narwhal 11.04

My expertise with Ubuntu is minimal

Suggestions on getting past the dpkg blockage?
thanks

---

### Post by nm_geo on 2011-07-24
> **cj88 said:**
> Attempting solutions to Broadcom 43xx issues (described at [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868) and elsewhere).

I keep running into error messages with dpkg when I attempt to install suggested files:
"read error in '/var/lib/dpkg/triggers//File':input/output error"

Main problem is "wireless network device not ready (firmware missing)"

Laptop is Dell D610

Running Natty Narwhal 11.04

My expertise with Ubuntu is minimal

Suggestions on getting past the dpkg blockage?
thanks
  I run a D620 and can not get the STA (wl) driver running.
There is another driver if you want to try it.

In terminal do the following commands and paste results here.
```

lspci -nn | greg 0280
```

```
lsmod
```

```
rfkill list all
```

copy and paste those is easiest no typo maybe ... :)

---

### Post by cj88 on 2011-07-24
> **nm_geo said:**
> I run a D620 and can not get the STA (wl) driver running.
There is another driver if you want to try it.

In terminal do the following commands and paste results here.
```

lspci -nn | greg 0280
```no greg found

```
lsmod
```lsmod
Module                  Size  Used by
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
i915                  450934  3 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
b43                   296610  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  0 
joydev                 17322  0 
drm                   180037  4 i915,drm_kms_helper
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            13213  1 
cfg80211              156212  2 b43,mac80211
dell_laptop            13515  0 
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
parport_pc             32111  1 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
ssb                    45942  1 b43
tg3                   131476  0 


```
rfkill list all
```0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


copy and paste those is easiest no typo maybe ... :)


thanks

---

### Post by nm_geo on 2011-07-24
```
lspci -nn | grep 0280
```

One more time with that one.. please ..

or just do 

```
lspci -nn
```

We need the pci number of your wireless card.
It looks like you have b43 installed that is good. 
I will review the lsmod a bit more.

---

### Post by cj88 on 2011-07-24
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

---

### Post by nm_geo on 2011-07-24
Question is your natty updated & upgraded

in terminal

```
sudo apt-get update

``````
sudo apt-get upgrade
```Some time here for things to get up-to-date

```
sudo apt-get install firmware-b43-installer
```Or add it from Synaptic package mananger  

Okay go to Synaptic do a search on_ bcm_
You need the firmware-b43-installer

---

### Post by nm_geo on 2011-07-24
Reboot with out ethernet cable connected..
Setup wireless in Network Manager
Let us know ..

---

### Post by cj88 on 2011-07-24
previously used update manager (and ran terminal cmd again) so should be latest and greatest.

attempted firmware installer
got the dpkg error message again

"read error in '/var/lib/dpkg/triggers//File':input/output error 
E: Sub-process /usr/bin/dpkg returned an error code (2) ""




rebooted laptop w/o ethernet (while typing on XP desktop)
Network connections / wireless shows nothing

---

### Post by nm_geo on 2011-07-24
Have you tried to read that file?

You may not have all the Source Lists (Repositories) you need
Go to Synaptic> Settings> Repositories> Click on all but source code
Check the Download location  mine is Server for United States
Next Tab Other Software I have independent checked & Canonical Partners
Next Tab Updates top two important security & Recommended

If you change anything Reload...

In Synaptic
Search for _bcm_
find firmware-b43-installer and apply install

---

### Post by cj88 on 2011-07-24
Added Canonical Partners *including source) repositories

after reload got this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by wildmanne39 on 2011-07-24
Hi, I have seen that problem before and it is one of the harder ones to fix, it can be caused by problems with bad sectors on the hard drive. 

I am going to give some commands run them one at a time and make sure that synaptic and the software center are closed first.

```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f
``` 
Thank you

---

### Post by nm_geo on 2011-07-24
Do you have the Natty connected to ethernet cable?  When you try to update & upgrade?

---

### Post by cj88 on 2011-07-24
all right, good.

BTW would there be efficiency in instead doing a low level format of the drive and reinstalling Natty from scratch?

And yes, ethernet cable is attached to the laptop

---

### Post by wildmanne39 on 2011-07-24
Hi, I would run those commands I gave you first and post back the results before reformatting or reinstalling natty.

Also open disk utility and run smart test on your driver then look at the smart data collected.

---

### Post by cj88 on 2011-07-24
sudo rm var/lib/dpkg/status
[sudo] password for :
rm: cannot remove `var/lib/dpkg/status': No such file or directory
cjr@cjr-Latitude-D610:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
cjr@cjr-Latitude-D610:~$ sudo rm -rf /var/lib/apt/lists/*
cjr@cjr-Latitude-D610:~$ sudo dpkg --configure -a
dpkg: error: read error in `/var/lib/dpkg/triggers//File': Input/output error
cjr@cjr-Latitude-D610:~$ sudo aptitude update
sudo: aptitude: command not found
cjr@cjr-Latitude-D610:~$ sudo aptitude upgrade
sudo: aptitude: command not found
cjr@cjr-Latitude-D610:~$ sudo aptitude install -f
sudo: aptitude: command not found



disk utility shows warning in 
Current Pending Sector Count
34 bad sectors

---

### Post by wildmanne39 on 2011-07-24
Hi, I am sorry I copied the commands I have on my computer and did not notice that it used aptitude and not apt-get here is how it should look, to run it with aptitude you would have to install it first and that is not possible until this is fixed.
```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```

---

### Post by cj88 on 2011-07-24
okay

getting updates now

updates completed 

Got the same error message as before after cmds for:
dpkg configure -a
upgrade
and get install -f

---

### Post by wildmanne39 on 2011-07-24
Hi, thats great please keep a check on your hard drive and I am going to let nm_geo help with the connection problem he is very good with these issues.

---

### Post by cj88 on 2011-07-24
thank you

---

### Post by wildmanne39 on 2011-07-24
Your are welcome!

---

### Post by cj88 on 2011-07-24
just tried again
apt-get install firmware-b43-installer

got same error message

---

### Post by nm_geo on 2011-07-24
> **cj88 said:**
> just tried again
apt-get install firmware-b43-installer

got same error message

Try it through Synaptic I don't think it will go but maybe...

---

### Post by cj88 on 2011-07-24
package failure again
(sounds painful)

What do you think about reinstalling ubuntu?
Would using format in Disk Utility be suitable beforehand?

---

### Post by wildmanne39 on 2011-07-24
Hi, if you are going to reinstall from the livecd you can choose to reformat during installation you do not want to try it from disk utility in ubuntu.

---

### Post by wildmanne39 on 2011-07-24
Hi, did the updates finish successfully? then only fail trying to install the wireless driver?

If you want you can post the entire output of this command 
```
sudo apt-get update && sudo apt-get upgrade
```
and I will take a look at it.

Also post the output of
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d/
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by cj88 on 2011-07-24
since it appears a couple of bad disc sectors could be a culprit, that seems like the logical step, unless you have a suggestion.

Is it correct that there is a format option after clicking on Install Ubuntu (not Try It Out)?

---

### Post by wildmanne39 on 2011-07-24
Yes after you click install and it goes to the partitioning section you click on the button called something else and you can format your partitions and resize them, or you can open gparted from the livecd and do it that way. 

Do you have windows installed or just ububntu?

---

### Post by cj88 on 2011-07-24
I saw the Advanced partioning tool, but the format button for the hard drive seemed to be greyed out.  

I will attempt to open CD and run gparted


Natty had been working fine last week; then I attempted to install XP again; it required formatting of the disc, I allocated half--so that's likely where the bad sectors came into it.

When some of its features did not work, I ran a low level format, and installed Natty again
I will research dual booting at another time

---

### Post by wildmanne39 on 2011-07-24
Hi, ok and just so you know it is not going to fix the bad sectors by reformatting but it will wipe out ubuntu completely so you can do a clean install. It will block those bad sectors so no more data is put into them.

---

### Post by cj88 on 2011-07-24
Thanks for your efforts

wish me luck

---

### Post by cj88 on 2011-07-25
Mark this SOLVED


I reinstalled Windows XP (which required formatting of disk).  Used Partition Magic to create an unused area of disc.  

Installed Ubuntu, letting it automatically partition remaining disc area.  

Installed all updates (after enabling previously suggested repositories in Synaptic Package Manager under settings tab).

Used Synaptic package manager to locate firmware-b43-installer;  this time it installed okay.

Disconnected ethernet cable; restarted computer; wireless network became available.


thanks again

links:  Broadcom drivers info

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

and

[http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)

---

### Post by wildmanne39 on 2011-07-25
Hi, I am glad you got it working, you are the only one that can mark the thread solved by going to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by nm_geo on 2011-07-25
> **cj88 said:**
> Mark this SOLVED
 
 
I reinstalled Windows XP (which required formatting of disk). Used Partition Magic to create an unused area of disc. 
 
Installed Ubuntu, letting it automatically partition remaining disc area. 
 
Installed all updates (after enabling previously suggested repositories in Synaptic Package Manager under settings tab).
 
Used Synaptic package manager to locate firmware-b43-installer; this time it installed okay.
 
Disconnected ethernet cable; restarted computer; wireless network became available.
 
 
thanks again
 
links: Broadcom drivers info
 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)
 
and
 
[http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)
 
Hope the hard drive bad sector info was just a burp.  Glad you got it going and that the firmware was correct. Enjoy and marked Solved please.

---


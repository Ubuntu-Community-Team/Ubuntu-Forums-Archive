---
title: "help setup qam time warner kworld 110"
date: 2007-12-20
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-20
I am trying to scan for unencrypted digital cable channels.  My local CATV is Time Warner Hudson Valley NY.  I was able to find channels 1.1 through 1.9 as major network and some local channels.  These were found on an HDTV television.  I would like to add just these few channels to a separate line up on my kworld 110 tuner card.  The problem is the auto scan starts at channel 2 which misses all the  qam channels I can receive without a cable set top box.

How do I force this detection.  I entered start at channel 1.1 but that is not utilized by the scan utility.  It must only be used when viewing live tv.

Any ideas where to start?

---

### Post by volkswagner on 2007-12-27
Bump

anyone know how to manually add a frequency 1.2?  This is how it appeared on an HDTV set on autoscan.  These are mostly local channels and broadcast in HDTV.  How can I get my kworld 110 accept these channels?

---

### Post by volkswagner on 2007-12-27
Any advice is greatly appreciated.  Maybe I am not asking the question correctly.  Can I manually add these few channels?  Do I need to know the frequency?  I discovered these channels performing a scan with a television set equipped to accept ntsc, atsc and qam.  These lower channes (1.1-1.9) were found without using any set top box.  Yet when I try to auto scan with the kworld 110 card in mythbuntu it does not pick up any qam channels.  I have tried all the qam variations, qam64, qam 256, etc.

To note the tve while it did pick up these lower channels it also picked up more than 300 digital channels, although all but the 1.1-1.9 were not viewable, the higher channels were just black screen.  Yet I get zero tuned with the card.  Could the card be defective?  How can I test the card better?

---

### Post by newlinux on 2007-12-28
Have you tested the card works using dvb-utils for QAM, or tvtime for analog? Have you tried scanning with cable connected to the other input on the card? Have you downloaded and installed the firmware into the right directory for this card? What frequencies are you using to scan (HRC, IRC, standard cable, etc.)? Try those different frequencies with the different modulations (QAM 256 and QAM 64), if you haven't already.

---

### Post by volkswagner on 2007-12-29
I am trying seems way over my head dvb-utils.  I installed it and researched how to use it yet I do not understand.  I have tried to verify the firmware is intalled it seems it is not.

The card it installed and recognised

```
eric@Bedroom:~$ dmesg | grep -i saa7133
[   31.008942] saa7133[0]: found at 0000:02:01.0, rev: 240, irq: 21, latency: 64, mmio: 0xfbffe800
[   31.008950] saa7133[0]: subsystem: 17de:7350, board: Kworld ATSC110 [card=90,autodetected]
[   31.008963] saa7133[0]: board init: gpio is 100
[   31.143966] saa7133[0]: i2c eeprom 00: de 17 50 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   31.143979] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.143991] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.144002] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.144014] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.144025] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.144037] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.144049] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.202858] tuner 0-0061: chip found @ 0xc2 (saa7133[0])
[   31.210935] saa7133[0]: registered device video0 [v4l2]
[   31.211093] saa7133[0]: registered device vbi0
[   31.342681] DVB: registering new adapter (saa7133[0]).
[   31.467201] saa7133[0]/alsa: saa7133[0] at 0xfbffe800 irq 21 registered as card -2
```


Following mythtv install I am stuck at step one.


> 1. Download the firmware

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

2. Place a copy of the firmware file (dvb-fe-nxt2004.fw) in your /lib/firmware directory.

3. Edit your /etc/modules file and insert an 'saa7134-dvb' right after the saa7134 entry that should already exist in the file. This will cause the module to load during boot.

4. Load the module

# modprobe saa7134-dvb

I do not know where the Kernel source directory resides.  My research turned up empty some say it shold be in /usr/src but that is empty.  Some say Ubuntu does not inlude it as part of the install.

Do I need it?  

when I 
```

eric@Bedroom:~$  perl get_dvb_firmware nxt2004
Can't open perl script "get_dvb_firmware": No such file or directory
```

I looked in /lib/firmware/2.6.22-14-generic.  I did not find dvb-fe-nxt2004.fw.

So I do need the firmware but I do not know how to get it.

---

### Post by newlinux on 2007-12-29
You need the firmware. To get the linux source you have to install it, ubuntu does not have it by default:

```

sudo aptitude install linux-source
cd /usr/src
sudo tar xvjf linux-source-[INSERT YOUR KERNEL HERE- just do an ls].tar.bz2
cd linux-source-[INSERT KERNEL VERSION]/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/

```

Then reboot.

```

dmesg | grep nxt2004

```

should give you output the firmware was loaded after a reboot if all is well.

---

### Post by volkswagner on 2007-12-30
Thanks for the help.  I am almost there.  Firmware is loaded and I can now scan in qam.  It locked several channels including the ones I was looking for, HD major network channels.  I did have to move the coax input. 

The card does not play TV though.  If I go to live TV it uses the tuners on the master backend.  If I make all the tuners on the backend busy recording my slave machine with the kworld 110 when going to live TV it says all tuners are busy.  

On the master backend what would I need to do to make sure it sees the tuner on the slave machine?  When adding a tuner it seems only local tuners can be added this way.

To get the card to work I did the following.  Add tuner>CARD TYPE=DVB DTV capture card 9v3.x)>DVB Card Number=0>Frontend ID: Nextwave NXT200X VSB/QAM frontend Subtype: A.....

Is this correct?  It seems to me anything that said Kworld 110 was analog only.  The following card types did not work pcHDTV DTV capture card (w/V4L drivers), HDHomeRun DTV tuner box.  I did not try firewire box, nor Ip based choices.

---

### Post by newlinux on 2007-12-30
In any frontend go to Information Center->System Status.

Are all your tuners listed? Really all you need to do is make sure the the slave backend is connecting to the master backend. Then the master backend will know what tuners the slave has (you don't have to explicitly add tuner cards on slave backends to the master backend). If the tuner is properly added to the slave backend, and the slave backend can communicate with the master backend, then all you probably need to do is restart mythbackend on the slave machine, then restart the mythbackend on the master machine, and they should communicate in a few seconds. In the system status screen above you can see what the status of all the tuners the master backend knows about are. So just make sure your slave machine is communicating with your master machine. And make sure you have selected and video source input for Kworld card. If this doesn't work, you'll probably need to look at your backend logs to see what is going wrong.

Setting up your kworld card as a DVB card is the right thing to do for QAM and ATSC.

---

### Post by volkswagner on 2007-12-30
EDIT:  Card is working.  I think the problem it is not loading on startup.  When I perform 

dmesg | grep nxt2004
modprobe saa7134-dvb

Restart backend all works.  So my entry in /etc/modules must be inaccurate or incomplete.



The slave backend machine with the kworld 110 system status says tuner 3 unavailable.

/etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
saa7134-dvb
```

I added the saa7134-dvb manually.

Intructions on mythtv site show
> 
Lastly, edit your /etc/modules file and insert an 'saa7134-dvb' right after the saa7134 entry that should already exist in the file.

I must be missing somthing, although I was not interested in analog capture so I did not set it up.  Must I add the analog as another tuner to get this to work?

```
eric@Bedroom:~$ sudo tail /var/log/mythtv/mythbackend.log
2007-12-30 11:59:47.773 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-12-30 11:59:47.775 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2007-12-30 11:59:48.795 Connecting to master server: 192.168.1.107:6543
2007-12-30 11:59:48.797 Connected successfully
2007-12-30 11:59:54.827 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-12-30 11:59:54.833 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2007-12-30 12:01:46.137 EITScanner: Now looking for EIT data on multiplex of channel 9.1
2007-12-30 12:03:45.775 EITScanner: Added 161 EIT Events
2007-12-30 12:07:04.448 EITScanner: Now looking for EIT data on multiplex of channel 1.13
2007-12-30 12:08:25.173 EITScanner: Added 27 EIT Events
```

When viewing system information no log info sayst to change to 1-8

All the above is on slave.  The master backend status says all three tuners not recording so seems to be available

---

### Post by newlinux on 2007-12-30
So I'm confused at what you are asking at this point. Is everything working? First you say it all works, then you say it says tuner 3 is unavailable. Then you say the master backend says all three tuners are available. This is through system status in the frontend, correct? I'm just not sure what you are saying is and isn't working.

Let me make sure I understand your architecture correctly. You have 2 tuners in your master backend and one in your slave (tuner 3)? in mythfrontend (it shouldn't matter whether you are running mythfrontend on your master or slave backend or any other machine -- they should all report the same thing since they are all supposed to be setup to connect to the master backend) it says all 3 tuners are available? So is everything working properly?

Is the problem just that everything is not working at reboot? You can see if that is a module problem by running lsmod after a reboot. If saa7134_dvb is not loaded something is going wrong, as that is listed in your /etc/modules. If it is loaded, it isn't a module problem. Perhaps the backends just need to be restarted just to make sure they are talking to each other after a reboot.

 What do you mean by add an analog tuner - do you mean add another tuner in mythtv-setup? If so, no you don't need to do that.

---

### Post by volkswagner on 2007-12-30
Sorry for the confusion.  You are correct the only problem now is after a reboot.  So after reboot I have to manually restart mythbackend to get the tuner active,

Here is a portion of lsmod

saa7134_dvb            18188  0 
dvb_pll                15492  2 saa7134_dvb
video_buf_dvb           7812  1 saa7134_dvb
dvb_core               82216  1 video_buf_dvb
tda1004x               17028  1 saa7134_dvb


I will leave things alone for a while and see If the master catches up with the slave on subsequent reboots.  Should not be a problem once I get evrything set up as reboots should be rare. I hope.

---

### Post by newlinux on 2007-12-30
Yeah, for me, I have 3 backends. After reboots, sometimes the master picks up the slave backends automatically, sometimes it does only after I restart the master and sometimes the slaves too... Not sure why. But I rarely ever reboot my myth machines either. I've had uptimes in excess of 9 months straight.

---


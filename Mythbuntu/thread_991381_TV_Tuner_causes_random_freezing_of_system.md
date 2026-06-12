---
title: "TV Tuner causes random freezing of system"
date: 2008-11-23
forum: Mythbuntu
---

### Post by gdselzer on 2008-11-23
I have Mythbuntu 8.04 installed and working very well with the exception that my USB TV Tuner causes the system to randomly freeze up.  The Tuner is a Hauppauge 850.  I installed it using the instructions [here]("http://www.avsforum.com/avs-vb/showthread.php?t=1057089").  It loads well, gets good reception and records well in Myth.  However, I have been unable to keep the system solid for more than 8 or 9 hours.  I have not been around when it freezes.  When I come back to it the keyboard and mouse do not respond and SSH does not respond either.  I have to hard reboot.  When the system restores, there are no messages in /var/log/messages or the myth logs that lead me to anything.  I have isolated the Tuner, since without it plugged in, I have had the system up for a week without any problems.

I would really appreciate some help hunting down the exact issue with an eye toward solving it.  It'd be nice to be able to record TV too...

Relevant lines from dmesg for the card:
> Nov 16 15:10:52 cheshire kernel: [285930.739828] usb 5-3: new high speed USB device using ehci_hcd and address 4
Nov 16 15:10:52 cheshire kernel: [285930.894264] usb 5-3: configuration #1 chosen from 1 choice
Nov 16 15:10:53 cheshire kernel: [171525.757145] au0828 driver loaded
Nov 16 15:10:53 cheshire kernel: [285932.627549] au0828: i2c bus registered
Nov 16 15:10:53 cheshire kernel: [285932.726600] tveeprom 4-0050: Hauppauge model 72301, rev B3F0, serial# 4996881
Nov 16 15:10:53 cheshire kernel: [285932.726613] tveeprom 4-0050: MAC address is 00-0D-FE-4C-3F-11
Nov 16 15:10:53 cheshire kernel: [285932.726621] tveeprom 4-0050: tuner model is Xceive XC5000 (idx 150, type 4)
Nov 16 15:10:53 cheshire kernel: [285932.726630] tveeprom 4-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Nov 16 15:10:53 cheshire kernel: [285932.726638] tveeprom 4-0050: audio processor is AU8522 (idx 44)
Nov 16 15:10:53 cheshire kernel: [285932.726645] tveeprom 4-0050: decoder processor is AU8522 (idx 42)
Nov 16 15:10:53 cheshire kernel: [285932.726652] tveeprom 4-0050: has no radio, has IR receiver, has no IR transmitter
Nov 16 15:10:53 cheshire kernel: [285932.726660] hauppauge_eeprom: hauppauge eeprom: model=72301
Nov 16 15:10:53 cheshire kernel: [114406.765280] xc5000 4-0061: creating new instance
Nov 16 15:10:53 cheshire kernel: [114406.767642] xc5000: Successfully identified at address 0x61
Nov 16 15:10:53 cheshire kernel: [114406.767645] xc5000: Firmware has not been loaded previously
Nov 16 15:10:53 cheshire kernel: [114406.767650] DVB: registering new adapter (au0828)
Nov 16 15:10:53 cheshire kernel: [114406.767653] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
Nov 16 15:10:53 cheshire kernel: [114406.767938] Registered device AU0828 [Hauppauge HVR850]
Nov 16 15:10:53 cheshire kernel: [114406.767974] usbcore: registered new interface driver au0828
Nov 16 15:10:53 cheshire kernel: [114406.920494] usbcore: registered new interface driver snd-usb-audio
Nov 16 15:12:28 cheshire kernel: [286030.489886] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
Nov 16 15:12:28 cheshire kernel: [286030.522611] xc5000: firmware read 12332 bytes.
Nov 16 15:12:28 cheshire kernel: [286030.522619] xc5000: firmware upload

My system, if it matters:
Pentium M 715 (1.5G)
Aopen i915GMm-N
1 GB RAM
160 GB WD HD

Thanks

---

### Post by ian dobson on 2008-11-24
Hi,

Try plugging the card into a different slot.
Then try running the system with mythtvbackend active.
Then try disabling EIT so that the card isn't always active.

Can you include a lspci here.

Regards
Ian Dobson

---

### Post by gdselzer on 2008-11-24
I've already tried plugging the tuner into a different USB port.  However, disabling the EIT is a good idea that I have not tried yet.  I'll turn off EIT and see if that makes a difference.

I don't know what running the system with mythtvbackend active means.  Don't I always do that?

lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
Thanks for the help.

Geoff

---

### Post by gdselzer on 2008-12-03
I disabled EIT a week ago and the system has been up and solid for the whole time.  I'm not exactly sure what this means (other than I get no listings in my Program Guide.)  What is my next step here?  I liked using EIT to get the listings as it is free and simple.  Is there anyway to get EIT sporadically?  Any help on next steps is appreciated.

---

### Post by gdselzer on 2008-12-20
bump

---

### Post by gdselzer on 2008-12-21
Can anyone help me figure out why the whole system randomly freezes when I have EIT enabled?

Thanks

---

### Post by gdselzer on 2008-12-23
bump

---

### Post by jaakan on 2008-12-25
I wonder if you have a hard drive with bad sectors on it.

---

### Post by ian dobson on 2008-12-25
Hi,

EIT puts your system under load (Tuner changing channels every X minutes, MySQL updating database with EIT data).

Maybe you can try slowing down the EIT scanner by changing the EITTransportTimeout in mythtv setup or directly in the database.

Regards
Ian Dobson

---

### Post by gdselzer on 2008-12-27
Don't think it's bad sectors.  I ran badblocks on it and it didn't find anything.

As for modifying the EIT settings, I could use a little help on this.  It looks to me like the EIT Transport Timeout determines how long the backend will wait on each channel to get the EIT, not how often it checks.  Right?  I set this to 2 minutes (down from 5) but it is still randomly freezing.

The other setting, Backend Idle before EIT Crawl, looks like it might be what determines the frequency of checking.  I increased this to 1200 seconds from (60).  Still getting the random freezes.

Any thoughts on what appropriate settings for these may be?  Any thoughts on how to test which is causing the problem?

Thanks

---

### Post by ian dobson on 2008-12-28
hi,

The Backend Idle before EIT Crawl is the length of time after a recoding is finished before the EIT scanner starts up.

The EIT Transport Timeout is how log the scanner will stay on one channel grabbing EIT data. If the problem you're haveing is with channel changing try increasing this value to maybe 10 (minutes) and also try increasing the tuning delay for each tuner.

I set the tuning timout to 3000 (3 seconds) on my tuners and have alot less problems with the tuner not getting a lock on the channel.

Regards
Ian Dobson

---

### Post by gdselzer on 2008-12-28
I'm not having issues with channel changing.  The issue I'm having is that having EIT enabled causes random system freezing.  While I have narrowed it down to EIT (when it is disabled, there is no freezing), I am unable to figure out which part of EIT is causing the problem and how to solve it.

Given that, can you recommend how I should change the EIT settings to fix this (or at least troubleshoot it further)?

Thanks

---

### Post by ian dobson on 2008-12-28
> **gdselzer said:**
> I'm not having issues with channel changing.  The issue I'm having is that having EIT enabled causes random system freezing.  
Thanks

So how does the EIT scanner download the EPG from the various multiplex's on your system? The tuner has to tune into each multiplex in turn and read the EPG data for that multiplex before moving on to the next one. Here's a dump from my backend log with EIT debug messages enabled:-

```

2008-12-28 16:09:02.261 EITScanner (5): Added 684 EIT Events
2008-12-28 16:09:02.268 EITScanner: Rate limiting reschedules..
2008-12-28 16:11:55.123 EITCache: Wrote 277 modified entries of 350 for channel 32409 to database.
2008-12-28 16:11:55.129 EITCache: Wrote 2 modified entries of 222 for channel 32410 to database.
2008-12-28 16:11:55.150 EITCache: Wrote 160 modified entries of 345 for channel 32411 to database.
2008-12-28 16:11:55.165 EITCache: Wrote 107 modified entries of 245 for channel 32412 to database.
2008-12-28 16:11:55.190 EITCache: Wrote 135 modified entries of 272 for channel 32413 to database.
2008-12-28 16:11:55.192 EITCache: Wrote 2 modified entries of 224 for channel 32414 to database.
2008-12-28 16:11:55.194 EITCache: Wrote 2 modified entries of 208 for channel 32415 to database.
2008-12-28 16:11:55.847 EITScanner (5): Now looking for EIT data on multiplex of channel 30417
2008-12-28 16:11:55.848 EITCache: Pruning all entries that ended before UTC 2008-12-27T16:16:06
2008-12-28 16:11:55.878 EITCache: Deleting old cache entries from the database
2008-12-28 16:11:56.565 EITScanner (5): Started passive scan.
2008-12-28 16:16:07.189 EITCache: Wrote 3 modified entries of 241 for channel 32416 to database.
2008-12-28 16:16:07.197 EITCache: Wrote 2 modified entries of 204 for channel 32417 to database.
2008-12-28 16:16:07.416 Scheduled 39 items in 0.2 = 0.17 match + 0.06 place
2008-12-28 16:16:07.780 EITScanner (5): Now looking for EIT data on multiplex of channel 33001
2008-12-28 16:20:19.115 EITCache: Wrote 2 modified entries of 43 for channel 2090 to database.
2008-12-28 16:20:19.134 EITCache: Wrote 3 modified entries of 93 for channel 32434 to database.
2008-12-28 16:20:19.140 EITCache: Wrote 2 modified entries of 55 for channel 35005 to database.
2008-12-28 16:20:19.770 EITScanner (5): Now looking for EIT data on multiplex of channel 30601

```

Note the "Now looking for EIT data on multiplex of channel" ie. it's tuning to a new channel/multiplex.

Please try what I say, I'm trying to help you and as a good friend once said:- There's a method to my madness

Regards
Ian Dobson

---

### Post by gdselzer on 2008-12-28
OK, sorry, I got confused and felt like maybe we had gotten onto different tracks.  I shall follow you through the madness.  :)

I set the EIT Transport Timeout to 10 mins.  Set the Backend Idle Before EIT Crawl back to 60 secs.  I also changed the Tuning Timeout from 5500 to 3000, as you suggest.  We'll have to wait to see if that fixes it.

How do I enable the EIT debugging?  I would assume that might give some hint as to what is causing this, no?

---

### Post by ian dobson on 2008-12-28
Hi,

To enable EIT debugging edit the file /etc/default/mythtv-backend and change the line 
EXTRA_ARGS=" --noupnp -v eit "

adding -v eit.

You might need to try different values for the tuner delay, 3000 works for me on my DVB-c cards. Maybe you need to  try lower or higher values. Try playing about with the tuner related values to see if any make any difference to your lockup problem.

Maybe it's a good idea to keep a log on changed this parameter, system crashed after x hours.

Regards
Ian Dobson

---


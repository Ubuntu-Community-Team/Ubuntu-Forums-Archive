---
title: "Wintv Nova Hd S2"
date: 2008-11-06
forum: Mythbuntu
---

### Post by LinuxDude... on 2008-11-06
Hi Guys,

I am having a issue scanning for channels on Mythtv with my Wintv Nova Hd S2 card. I have setup the card with firmware and its all working correctly as i can watch sat tv in Kaffiene.

I captured the card in the Capture Card Setup as a DVBS Card set to 0 and I set the Signal timeout to 60000 and the tuning timeout to 62500

The problem occurs when i try and scan for channles in MythTv, i enter in the frequency 10714000 as specified in [http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite]("http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite"). I can see the channel sat signal is 85% and it scans for about 60000 msec and then i get a timeout scanning frequency - no signal, message.

Has anybody here got a  Wintv Nova Hd S2 card work with Mythtv?

Thanks
LinuxDude...

---

### Post by Modiford on 2008-11-15
Hello LinuxDude...,

I too have the Hauppauge Nova-HD-S2 which seems to be the only thing readily available in the UK for Freesat use yet getting it working in Mythbuntu remains impossible due to the lack of documentation online.

By all accounts it's supported by the [latest drivers]("http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw") as card #69 or "Hauppauge WinTV-HVR4000(Lite) DVB-S/S2" but alas my installation of Mythbuntu 8.10 x86-32 doesn't recognise it.

I see your post has gone unanswered so I wonder if you'd share with me how you got your HD-S2 working and I'll see if I'm any more successful getting it to work - and if so, post back my results for your reference.

Kind regards,

Modiford.
More a FreeBSD guy than Linux, but absolutely loving the Mythbuntu experience with my PVR-250.

---

### Post by ianhaycox on 2008-11-17
I've got the same card, WinTV Nova HD S2 and after much fiddling I have got it working on MythTv.

```

ian@ian-desk:~$ dmesg | grep -i haup
[   16.903668] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   17.083100] tveeprom 0-0050: Hauppauge model 69100, rev B2C3, serial# 3277801
[   17.083128] cx88[0]: hauppauge eeprom: model=69100
[   17.085541] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.1/input/input5
[   17.139386] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]

```

As you can see it's reported as a HVR4000(Lite)

```

ian@ian-desk:~$ dmesg | grep -i firm
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[  134.530761] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  134.530768] firmware: requesting dvb-fe-cx24116.fw
[  134.552477] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  138.396254] cx24116_load_firmware: FW version 1.20.79.0
[  138.396275] cx24116_firmware_ondemand: Firmware upload complete
ian@ian-desk:~$ 

```

From memory I grabbed the firmware from the supplied Windows install disk via,

```

dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522 

```

On Intrepid I used the latest DVB/V4L sources without any patching and it created all the correct devices in /dev and I was able to watch TV via mplayer.

Scanning was a little more hassle. Following the instructions on linuxtv.org I used an initial scan file for Astra 28.2 and Eurobird on 28.5 cobbled together from sources on the web, thus:

[http://www.brittanyholidaycottage.com/Astra](http://www.brittanyholidaycottage.com/Astra)

then created a channels.conf file with scan -n 0 to get the FTA channels and imported into MythTv.

Hope that helps, if you have any specific questions then ask.

---

### Post by Modiford on 2008-11-20
Hello LinuxDude...,

I have now got my HD-S2 working in Mythbuntu following the various forum posts here and found the same time-out issue.

As a work-around I selected the "Full Scan of Existing Transports" option and ticked the "Ignore Signal Timeout" option.  It took about 20-25 minutes to complete and came up with all sorts of channels (main-line BBC, ITV et al and other test and data ones).

I then entered into MySQL and simply renumbering the meaningful channels into an order I liked.

I tried messing with xmltv but found scheduling had already began populating for main channels like BBC and ITV but none yet for Five or other music stations.  Guess this is from the EIT.

Kind regards, and thanks to all,

Modiford.

---

### Post by parker13 on 2009-01-30
I, too have a WINTV-Nova-HD-S2. On Intrepid, I used the following guide to get the drivers and firmware working:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

I scanned for channels using:

scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E | tee channels.conf

After importing the chennels.conf into mythtv-setup, I can watch Satellite TV fine.

My problem is that there's no BBC HD channel.

Even if a do a "Full Scan of Existing Transports" and tick the "Ignore Signal Timeout" option, BBC HD is not found.

Am I missing something? To be honest BBC HD the the one reason why I bought the card and I'd happily trade a hundred rubbish channels for one decent one!

---

### Post by ianhaycox on 2009-01-30
I have the same card and can watch BBC HD,

My channels.conf had the following line:-

```

BBC HD:10847:v:0:22000:0:2330:6940

```

---

### Post by parker13 on 2009-01-30
> **ianhaycox said:**
> I have the same card and can watch BBC HD,

My channels.conf had the following line:-

```

BBC HD:10847:v:0:22000:0:2330:6940

```

Thanks, I'll try adding that manually tonight.

---

### Post by parker13 on 2009-01-31
Even if I import that line into mythtv-setup as a channels.conf, when it does the scan it doesn't find BBC HD. Weird. I just get "Timeout scanning 0 -- no signal".

---

### Post by ianhaycox on 2009-02-01
As a test try stopping the myth backend and putting your channels.conf into ~/.mplayer/channels.conf then try $ mplayer dvb://"BBC HD" and see what happens.

I just tried it and got,

```

ian@ianh:~$ mplayer dvb://"BBC HD"
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://BBC HD.
dvb_tune Freq: 10847000
TS file format detected.
NO VIDEO! AUDIO MPA(pid=2330) NO SUBS (yet)!  PROGRAM N. 0
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:55037.7 (15:17:17.6) of -0.6 (unknown)  4.2% 

MPlayer interrupted by signal 2 in module: play_audio

```

Now oddly I didn't get any video but I get get audio. It's definitely BBC HD cos I recognised the voice of Rick Spleen from the preview.

It's possible the channels.conf I posted is not quite right, or mplayer can't cope with the HD Video.

I could try extracting the channel data from my sql database for you to import to see if that helps.

---

### Post by parker13 on 2009-02-02
> 
Now oddly I didn't get any video but I get get audio. It's definitely BBC HD cos I recognised the voice of Rick Spleen from the preview.

It's possible the channels.conf I posted is not quite right, or mplayer can't cope with the HD Video.

I could try extracting the channel data from my sql database for you to import to see if that helps.

I'm at work now, but I'll try the mplayer stuff tonight when I get home. 

Yes, if you could please dump the channel data for BBC HD from the channel table, that would be very helpful.

---

### Post by ianhaycox on 2009-02-02
Hope this helps,

```

mysql> select * from channel where callsign='BBC HD';
+--------+---------+--------+----------+----------+--------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+----------+---------+---------------+---------------+---------+-----------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
| chanid | channum | freqid | sourceid | callsign | name   | icon | finetune | videofilters | xmltvid | recpriority | contrast | brightness | colour | hue   | tvformat | commfree | visible | outputfilters | useonairguide | mplexid | serviceid | atscsrcid | tmoffset | atsc_major_chan | atsc_minor_chan | last_record         | default_authority | commmethod |
+--------+---------+--------+----------+----------+--------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+----------+---------+---------------+---------------+---------+-----------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
|   7940 | 14      | NULL   |        1 | BBC HD   | BBC HD |      |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |        0 |       1 |               |             1 |      76 |      6940 |      NULL |        0 |               0 |               0 | 0000-00-00 00:00:00 |                   |         -1 | 
+--------+---------+--------+----------+----------+--------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+----------+---------+---------------+---------------+---------+-----------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
1 row in set (0.00 sec)

mysql> select * from dtv_multiplex where mplexid = 76;
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | sistandard | serviceversion | updatetimestamp     |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
|      76 |        1 |        2050 |         2 |  10847000 | a         |   22000000 | 5/6  | v        | qpsk       | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | dvb        |              0 | 2009-01-23 15:54:10 | 
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
1 row in set (0.00 sec)

```

---

### Post by parker13 on 2009-02-02
Hi,

Thanks again for your help.

Unfortunately, I cannot tune in mplayer or MythTV. In mplayer I get:
```

$ mplayer dvb://"BBC HD"
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://BBC HD.
dvb_tune Freq: 10847000
Not able to lock to the signal on the given frequency, timeout: 30
dvb_tune, TUNING FAILED
ERROR, COULDN'T SET CHANNEL  0: Failed to open dvb://BBC HD.


Exiting... (End of file)

```

In myth I just get "no_lock" on the OSD.

Other channels work fine.

Maybe it's my dish or cable, but I get 80% signal on the scan.

---

### Post by ianhaycox on 2009-02-02
If you've got a spare Sky/Freesat box you should be able to check that the dish/cable is OK.

Check for errors in dmesg/syslog or mybackend log files, apart from that I'm out of ideas

---

### Post by parker13 on 2009-02-03
> **ianhaycox said:**
> If you've got a spare Sky/Freesat box you should be able to check that the dish/cable is OK.

Check for errors in dmesg/syslog or mybackend log files, apart from that I'm out of ideas

Thanks again for your help. I'll be sure to post if I get anywhere.

---

### Post by jazz452 on 2009-02-19
> **parker13 said:**
> Thanks again for your help. I'll be sure to post if I get anywhere.

I found it a lot easier to use kaffeine for scanning and watching although im using kde4 it just does the lot.Including recording.

---

### Post by parker13 on 2009-02-23
> **jazz452 said:**
> I found it a lot easier to use kaffeine for scanning and watching although im using kde4 it just does the lot.Including recording.

Thanks, I tried Kaffeine last night and got the same result - loads of channels but no BBC HD. However, I did make a breakthrough...

The machine I'm using to test the card dual boots Ubuntu and XP, so I forced myself to try the software which came with the Hauppauge card, PowerCinema 5.1. I didn't expect it to work, but after a channel scan there it was, BBC HD in all its glory! I quickly booted back into Ubuntu and scanned using "scan", MythTV and Kaffeine - no BBC HD.

So, there's nothing wrong with my feed or card, it's either something to do with Linux or something I'm doing wrong.

---

### Post by parker13 on 2009-02-24
I've finally, finally sorted this issue! The fact that it worked in Windows, but not Linux narrowed it down to software. Because I'm on Intrepid with a 2.6.27 kernel I'd previously compiled the latest DVB drivers as described here:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000#Kernel_.2F_v4l-dvb_driver](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000#Kernel_.2F_v4l-dvb_driver)

This takes a snapshot of the development tree for v4l-dvb. I went through the process again with the latest snapshot and now everything works! All transponders scan OK, including transponder 50 which has BBC HD.

Someone must have broken the v4l-dvb driver at the point I downloaded and compiled it the first time. A lot of effort wasted due to a bit of bad luck!

---

### Post by jazz452 on 2009-02-24
Nice to see you sorted it i use arch Linux and had none of these problems.Didnt need any drivers just worked out the box. 
Booted into Ubuntu jaunty and couldn't get it to work I can see why you had problems.
If anyone else has problems follow this great how to 


        [http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681](http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681)

---


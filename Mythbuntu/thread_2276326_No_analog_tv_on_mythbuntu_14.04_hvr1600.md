---
title: "No analog tv on mythbuntu 14.04 hvr1600"
date: 2015-05-01
forum: Mythbuntu
---

### Post by stevecartermo on 2015-05-01
I had a working mythbuntu 12.04 backend with two HVR 1600 Cards inside.. They were working but I had a couple of small problems (intermittant no sound on analog side after powerdown) so I took the plunge and started with a fresh 14.04 mythbuntu. Install went ok Mythtv .27 mythbuntu repos enabled all updates applied. But now my analog encoders do not record TV just black screen and when I try to switch to the analog input I get a partial lock and then myth times out. I tried all analog inputs composite svideo same inability to lock on. The digital tuners work great in fact better than under 12.04.

It looks like the firmware is being loaded correctly. I looked at the permissios and they seem to be different for the DIGITAL and ANALOG tuners....
steve@mythbackend1404:~$ ls /dev/video*
/dev/video0  /dev/video24  /dev/video32
/dev/video1  /dev/video25  /dev/video33
steve@mythbackend1404:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 Apr 30 20:10 /dev/video0
crw-rw----+ 1 root video 81, 5 Apr 30 20:10 /dev/video1
crw-rw----+ 1 root video 81, 3 Apr 30 20:10 /dev/video24
crw-rw----+ 1 root video 81, 8 Apr 30 20:10 /dev/video25
crw-rw----+ 1 root video 81, 1 Apr 30 20:10 /dev/video32
crw-rw----+ 1 root video 81, 6 Apr 30 20:10 /dev/video33
steve@mythbackend1404:~$ ls -l /dev/dvb*
total 0
drwxr-xr-x 2 root root 120 Apr 30 20:10 adapter0
drwxr-xr-x 2 root root 120 Apr 30 20:10 adapter1
steve@mythbackend1404:~$ 


Any Ideas ???

Thanks

Steve

---

### Post by stevecartermo on 2015-05-02
had tw0 HVR 1600 installed but I only neeeded one mpeg encoder so I installed an old Adaptec AVC2410 Video Oh I had lying around. Same results.

 lsmod | grep cx
cx18_alsa              13730  1 
snd_pcm               104112  5 cx18_alsa,snd_hda_codec,snd_hda_intel,snd_hda_controller,ivtv_alsa
cx18                  131723  2 cx18_alsa
videobuf_vmalloc       13589  1 cx18
dvb_core              121659  1 cx18
tveeprom               21216  2 cx18,ivtv
cx2341x                28230  2 cx18,ivtv
videobuf_core          26023  2 cx18,videobuf_vmalloc
v4l2_common            15681  8 cx18,ivtv,cx2341x,tuner,saa7115,cs53l32a,cs5345,msp3400
snd                    79468  22 cx18_alsa,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,ivtv_alsa
videodev              153793  11 cx18,ivtv,cx2341x,tuner,saa7115,cs53l32a,cs5345,msp3400,v4l2_common,ivtv_alsa
i2c_algo_bit           13413  3 cx18,ivtv,nouveau
steve@mythbackend1404:~$ dmesg | grep cx
[   10.733317] ivtv0: Autodetected Adaptec VideOh! AVC-2410 card (cx23416 based)
[   10.736869] cx18:  Start initialization, version 1.5.1
[   11.619077] cx18-0: Initializing card 0
[   11.619081] cx18-0: Autodetected Hauppauge card
[   11.619421] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   11.619605] cx18-0: cx23418 revision 01010000 (B)
[   11.865745] cx18-0: Autodetected Hauppauge HVR-1600
[   11.865747] cx18-0: Simultaneous Digital and Analog TV capture supported
[   12.427212] cs5345 9-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.460707] cx18-0: Registered device video1 for encoder MPEG (64 x 32.00 kB)
[   12.460712] DVB: registering new adapter (cx18)
[   13.088461] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   13.105852] cx18 0000:01:04.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   13.106482] cx18-0: DVB Frontend registered
[   13.106486] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   13.106630] cx18-0: Registered device video33 for encoder YUV (20 x 101.25 kB)
[   13.106888] cx18-0: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   13.107082] cx18-0: Registered device video25 for encoder PCM audio (256 x 4.00 kB)
[   13.107284] cx18-0: Registered device radio1 for encoder radio
[   13.107286] cx18-0: Initialized card: Hauppauge HVR-1600
[   13.107895] cx18:  End initialization
[   13.411131] cx18-alsa: module loading...
[   13.559688] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   14.000388] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   14.007917] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   15.403380] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   15.423509] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
steve@mythbackend1404:~$

---

### Post by gordintoronto on 2015-05-03
Where do you live? Are you trying to capture over-the-air analog TV?

Where I live (Toronto, Canada), all over-the-air broadcasts are now digital.

---

### Post by stevecartermo on 2015-05-04
Hi

I also live in Toronto. I have a Scientific Altlanta cable box that converts the digital cable signal to either a channel 3 coax output a composite output with left and right audio on RCA jacks or an svideo connection. I have connected all these outputs to a Pinnacle USB TV tuner and I can see the output of the cable box. When I plug the output of the cable box into either the HVR 1600 or the Adaptec AVC2410 Video Product my recordings are blank under Mythtv. I then tried the additional drivers option to use the LINUX NONFREE DRIVER for the Conexant tuner. Same result I received the same results on another machine running 15.04


... A little stumped ... considering this all worked under 12.04

---

### Post by gordintoronto on 2015-05-04
Sorry, I have no suggestions.

---

### Post by stevecartermo on 2015-05-05
So the plot thickens...

I Type

mplayer /dev/video0

into a teminal
I get a screen with snow

Into a second terminal I type
scantv -c /dev/video0 -C /dev/vbi0

I say NTSC us broadcast ( I am trying to capture the output of my digital cable box in Mythtv)

The progam cycles through all the channels

I can see the output channel 3 is correct

I enter

ivtv-tune -c3

and I see the cable box output  in a window...

and yet mythtv still does not like the card.

???????

---

### Post by aelfric55 on 2015-05-06
In the backend setup, in Input Connections, check whether the input connection that you have bound to the analog card at /dev/video0 (and/or /dev/video1 as the case may be) is set to always start on channel 3. The card, cable box, and cx18 driver all work, since you can manually tune the card to ch. 3 and receive viewable input through the cable box and the card. But it doesn't look like mythtv is bothering to tune the card to ch.3 when it initializes the card.

---

### Post by stevecartermo on 2015-05-06
That tune to channel 3 and start on channel 3 was a good idea ... I got there about half way through my attempts ... still the same result though. NOT WORKING.

I was thinking that under mythbuntu 12.04 and earlier the HVR 1600 had to be initially set to either an IVTV or V4L device and then after the backend was setup I had to go in and change the card to a PVR150 MPEG device. I tried to do that this time but the IVTV or V4L devices are no longer listed..

Anyone know why or why that card needed to be configured that way ?

Thanks

---

### Post by aelfric55 on 2015-05-06
Hauppauge never bothers with drivers for their cards, and it took a long time before the cx18 driver was developed from the ivtv code to the point of being usable on analog (with some really annoying glitches that persist today). Longer still for the  digital half to be usable. Some versions of mythtv had a backend setup and scan routine that didn't play nicely with the cx18 driver, particularly since channel scan has been broken in mythtv more frequently than it has worked since about 2009. Then, too, 0.24 and some versions of 0.25 simply would not recognize /dev/videoX that was newly set up for one of these cx18 cards, even when the output of dmesg showed the device node was properly registered and cat /dev/videoX along with mplayer showed that the card was processing video. This problem appears to have been corrected with 0.26 and following as has as the old problem of having to register the 1600 as an V4l analog card and then edit the setup to mpeg2.   I had no problem simply adding the 4 1600s I still use as mpeg cards when I moved to 0.27.3-4.

Since your driver is loading properly and your card has /dev/videoX node and is functional outside of mythtv on that node, and since mythtv seems to recognize that card (which you set up as "Analog to MPEG-2 Encoder Card (PVR-150/250/350 etc.) and not as "IVTV Recorder" or "Analog", or whatever (it's odd if IVTV or Analog really are no longer listed in your backend setup, since I still have them in 0.27.3), and since you have Input Connections set properly to init the card on ch.3, the question then moves to how you have the Channel Editor set to invoke that card starting on ch.3.

If you're just capturing whatever stream comes over the cable box, then you'd likely have a dummy Video Source set up with a single dummy channel in the channel editor that actually doesn't tune the card to anything, since it's already starting up on ch. 3. If, however, you're watching various channels, through your cable box, then you'll have a real Video Source for analog channels set up (separate from the Video Source for digital channels) Since the card itself will always be locked onto ch3., the analog channels visible in the Channel Editor would be tuning the cable box through a lirc setup of some sort.

So in sum, since your card is functional and added properly as Analog to MPEG2, then it would seem the chain must be breaking down somewhere in the tuning phase, because of how you have the Video Source/Channel Editor/lirc script set up, and whether the data entered in the Channel Editor is causing the card to be retuned away from ch.3 (which you don't want).

---

### Post by stevecartermo on 2015-05-07
Good Points...

First time through the setup I did try to scan  for these cable channels but in hindsight that was wrong. So I deleted all the channels for the cable source and instead fetched the channels from schedules direct. I have the same channel-change.pl script that I used under my Mythbuntu 12.04 setup. Although I see the LED pulsed when the machine is restarted but never afterwards. Maybe time to dig into some LOGS.

---

### Post by stevecartermo on 2015-05-07
OK SO ...

I take one of the HVR 1600s put it in another machine running Studio Ubuntu 15.04 I setup a secondary backend and myhfrontend using MYTHBUNTUs control centre.

I get all the same symptoms I saw on the primary backend with the 1600 namely no Analog

on the secondary backend when I try to watch Live analog TV starting channel 3 I get


steve@steve-System-A10:~$ mythbackend
2015-05-07 14:05:18.295751 C  mythbackend version: fixes/0.27 [v0.27.4-58-g45d2d51] [www.mythtv.org](www.mythtv.org)
2015-05-07 14:05:18.295766 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2015-05-07 14:05:18.295770 N  Enabled verbose msgs:  general
2015-05-07 14:05:18.295797 N  Setting Log Level to LOG_INFO
2015-05-07 14:05:18.306796 I  Added logging to the console
2015-05-07 14:05:18.307467 I  Setup Interrupt handler
2015-05-07 14:05:18.307474 I  Setup Terminated handler
2015-05-07 14:05:18.307481 I  Setup Segmentation fault handler
2015-05-07 14:05:18.307487 I  Setup Aborted handler
2015-05-07 14:05:18.307495 I  Setup Bus error handler
2015-05-07 14:05:18.307501 I  Setup Floating point exception handler
2015-05-07 14:05:18.307510 I  Setup Illegal instruction handler
2015-05-07 14:05:18.307520 I  Setup Real-time signal 0 handler
2015-05-07 14:05:18.307556 N  Using runtime prefix = /usr
2015-05-07 14:05:18.307565 N  Using configuration directory = /home/steve/.mythtv
2015-05-07 14:05:18.307616 I  Assumed character encoding: en_CA.UTF-8
2015-05-07 14:05:18.307855 N  Empty LocalHostName.
2015-05-07 14:05:18.307859 I  Using localhost value of steve-System-A10
2015-05-07 14:05:18.307882 I  Testing network connectivity to '192.168.0.127'
2015-05-07 14:05:18.309217 I  Starting process signal handler
2015-05-07 14:05:18.309358 I  Starting IO manager (read)
2015-05-07 14:05:18.309355 I  Starting process manager
2015-05-07 14:05:18.309447 I  Starting IO manager (write)
2015-05-07 14:05:18.409083 I  New Client:  (#1)
2015-05-07 14:05:18.465580 N  Setting QT default locale to en_CA
2015-05-07 14:05:18.465678 I  Current locale en_CA
2015-05-07 14:05:18.465739 N  Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2015-05-07 14:05:18.643928 I  Current MythTV Schema Version (DBSchemaVer): 1317
2015-05-07 14:05:18.663906 I  Loading en_ca translation for module mythfrontend
2015-05-07 14:05:18.682580 I  Using protocol version 77
2015-05-07 14:05:18.721669 N  MythBackend: Running as a slave backend.
2015-05-07 14:05:20.070980 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:05:20.071030 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
			while disabling streaming (v4l v2)
			eno: Invalid argument (22)
2015-05-07 14:05:20.074672 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:05:20.074712 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
			while disabling streaming (v4l v2)
			eno: Invalid argument (22)
2015-05-07 14:05:20.087754 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:05:20.087834 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
			while disabling streaming (v4l v2)
			eno: Invalid argument (22)
2015-05-07 14:05:20.087846 E  V4LChannel[21](/dev/video0): SetInputAndFormat() failed
2015-05-07 14:05:20.100385 I  Registering HouseKeeperTask 'JobQueueRecover'.
2015-05-07 14:05:20.100409 I  Registering HouseKeeperTask 'HardwareProfiler'.
2015-05-07 14:05:20.118336 I  Starting HouseKeeper.
2015-05-07 14:05:20.138463 I  Listening on TCP 127.0.0.1:6544
2015-05-07 14:05:20.138513 I  Listening on TCP 192.168.0.13:6544
2015-05-07 14:05:20.138590 I  Listening on TCP [::1]:6544
2015-05-07 14:05:20.138648 E  Failed listening on TCP [fe80::e291:f5ff:fe43:7ebd%wlan0]:6544 - Error 9: The address is not available
2015-05-07 14:05:20.138682 E  Address [fe80::e291:f5ff:fe43:7ebd%wlan0] no longer exists - ignoring
2015-05-07 14:05:20.642347 I  Main::Registering HttpStatus Extension
2015-05-07 14:05:20.668864 I  Listening on TCP 127.0.0.1:6543
2015-05-07 14:05:20.668924 I  Listening on TCP 192.168.0.13:6543
2015-05-07 14:05:20.669013 I  Listening on TCP [::1]:6543
2015-05-07 14:05:20.669079 E  Failed listening on TCP [fe80::e291:f5ff:fe43:7ebd%wlan0]:6543 - Error 9: The address is not available
2015-05-07 14:05:20.669119 E  Address [fe80::e291:f5ff:fe43:7ebd%wlan0] no longer exists - ignoring
2015-05-07 14:05:21.543989 I  Bonjour: Service registration complete: name 'Mythbackend on steve-System-A10' type '_mythbackend._tcp.' domain: 'local.'
2015-05-07 14:05:21.669533 N  Connecting to master server: 192.168.0.127:6543
2015-05-07 14:05:21.671504 N  Connected successfully
2015-05-07 14:06:20.125429 I  Queueing HouseKeeperTask 'JobQueueRecover'.
2015-05-07 14:06:20.139675 I  Running HouseKeeperTask 'JobQueueRecover'.
2015-05-07 14:06:20.149281 I  HouseKeeperTask 'JobQueueRecover' Finished Successfully.
2015-05-07 14:07:39.725930 I  MainServer::ANN Playback
2015-05-07 14:07:39.725938 I  adding: steve-System-A10 as a client (events: 0)
2015-05-07 14:08:05.153607 I  MainServer::ANN Playback
2015-05-07 14:08:05.153622 I  adding: steve-System-A10 as a client (events: 0)
2015-05-07 14:08:05.184680 I  TVRec[21]: Changing from None to WatchingLiveTV
2015-05-07 14:08:05.222305 I  TVRec[21]: HW Tuner: 21->21
2015-05-07 14:08:05.279065 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:08:05.279084 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
			while disabling streaming (v4l v2)
			eno: Invalid argument (22)
2015-05-07 14:08:05.298036 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:08:05.298067 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
			while disabling streaming (v4l v2)
			eno: Invalid argument (22)
2015-05-07 14:08:05.298079 E  V4LChannel[21](/dev/video0): SetInputAndFormat() failed
2015-05-07 14:08:05.298089 E  TVRec[21]: Failed to set channel to 3. Reverting to kState_None
2015-05-07 14:08:05.298121 I  TVRec[21]: Changing from WatchingLiveTV to None

Just get a black screen.

When I scanned for DVB channels on this machine it said that it found about 9 DVB channels and 1 NTSC or Analog I can't remember the phrase.. Should I edit my channel list to just have channel 3 ?

Thanks

---

### Post by aelfric55 on 2015-05-08
> 2015-05-07 14:05:18.721669 N  MythBackend: Running as a slave backend.
2015-05-07 14:05:20.070980 I  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
2015-05-07 14:05:20.071030 E  V4LChannel[21](/dev/video0): SetInputAndFormat(30, NTSC) 
            while disabling streaming (v4l v2)
            eno: Invalid argument (22)
indicates the problem is happening right when the backend loads, and not when livetv is started --so it seems potentially to be a backend setup misconfiguration issue of some sort. There's not much in the way of documentation or information hereabouts.

Make sure sure the analog 1600 card is installed as "Analog to MPEG-2 Encoder Card (PVR-150/250/350 etc.)" and not as anything else.

Make sure you have two separate Video Sources set up --one Video Source to handle only the DVB channels, and one Video Source to just handle Analog. DVB and analog can't be on the same Video Source.

For the sake of testing, configure the Analog Video Source with "No grabber". Bind the Analog Video Source with No Grabber to the 1600's /dev/video0 in Input Connections. Set it to start on channel 3; don't scan for anything. Nothing it can see, anyway. Make sure there is NO channel changing script listed or selected.

In Channel Editor, there should be NO channels yet under your Analog Video Source. Manually "Add Channel" in your Analog Video Source that you can name "Test" or something. Where the entry on the second or third page of the "Add Channel" dialog asks for "frequency or channel" just put 3. Save this solitary analog channel, exit the backend setup and start the backend(s). Now live tv being started should capture whatever is coming out of the cable box. 

Maybe progress if it happens.

---


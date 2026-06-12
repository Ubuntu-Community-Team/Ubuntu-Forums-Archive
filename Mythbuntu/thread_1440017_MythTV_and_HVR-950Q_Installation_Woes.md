---
title: "MythTV and HVR-950Q Installation Woes"
date: 2010-03-26
forum: Mythbuntu
---

### Post by markackerman8@gmail.com on 2010-03-26
Perhaps I can ask for some troubleshooting help. You might see from my previous threads that I am really trying hard, (for 1 1/2 years and now with a new card) but I am still a stupid newbie it seems.  The basic problem is trying to watch live TV with MythTV and my new card; the HVR-950Q, (it works with TVTime!)  It seems to have time-out issues though that should be solved with the fact that I stopped it from powering off.  Up to this point in my many attempts I have unwittingly recorded live TV and viewed the recordings, can peruse channel listings, but NEVER have been able to watch Live TV.  And right now nothing is working!

Just recently
- I re-installed Ubuntu (migrated to Opensuse for 2 months and am back to Ubuntu now) as I was having driver and vdpau issues. Now
I have NVidia 195.xx drivers, vdpau, and myth all installed seemingly
happy (not an easy task).

1/And what the heck is vdpau anyway? (in layman terms?)

- I re-installed v4l-dvb and FINALLY did so without error. (a common
problem with a bug in one of the drivers - removed it and it compiled)
(not my distros fault!)

- I set-up mythfrontend and backend and mysql as before (my tuner card
settings were and are fine I think), though my local name had issues
and I have reverted to the 127.0.0.1, though eventually I want it to
be my IPaddress as I want to use another computer as frontend as well)

- and after receiving errors as mentioned below I changed my
mythconverg user/password from mythtv/mythtv to my login name and
password: (ack/##) - though I don't know if this was smart...

2/ Is that ok or should I put it back to user/password: mythtv/mythtv

- anyway that is where I am at; Could anyone please help this
troubleshooting nightmare with any suggestions ... at this point I am
bamboozled! and a little guidance would go a long way!!

3/ Please ask some questions, and I will reply!

This is the frontend complaints when selecting "Watch LiveTV"

2010-03-26 16:33:09.439 MythContext: Connecting to backend server:
127.0.0.1:6543 (try 1 of 1)
2010-03-26 16:33:09.440 Using protocol version 50
2010-03-26 16:33:09.570 Spawning LiveTV Recorder -- begin
2010-03-26 16:33:16.570 MythSocket(298d190:50): readStringList: Error,
timed out after 7000 ms.
2010-03-26 16:33:16.570 RemoteEncoder::SendReceiveStringList(): No response.
2010-03-26 16:33:16.570 Spawning LiveTV Recorder -- end
2010-03-26 16:33:16.571 GetEntryAt(-1) failed.
2010-03-26 16:33:16.572 EntryToProgram(0@Wed Dec 31 16:00:00 1969)
failed to get pginfo
2010-03-26 16:33:16.572 TV Error: HandleStateChange(): LiveTV not
successfully started
2010-03-26 16:33:16.572 We have a RingBuffer
2010-03-26 16:33:16.623 TV Error: LiveTV not successfully started
2010-03-26 16:33:16.626 ScreenSaverX11Private: DPMS Deactivated 1
2010-03-26 16:33:16.626 ScreenSaverX11Private: DPMS Reactivated 1

---

### Post by iponeverything on 2010-03-27
vdpau capable hardware is something that I am going to looking at soon for my backend..

From: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)
> API for GPU-accelerated decode of MPEG-1, MPEG-2, H.264, and VC-1 bitstreams

---

### Post by markackerman8@gmail.com on 2010-04-05
Thanks I now understand Vdpau much btter. 

Can anyone help me with watching live tv (NTSC analog cable) with my tuner card (HVR950Q)?

---

### Post by dfarin on 2010-04-09
Mark,

You have been very patient about seeking this solution. Thanks from a true newbie who has been sitting on the sidelines, rooting you on.:popcorn:

I feel like you are getting close in spite of the most recent roadblocks. Where did you learn the basics of modifying code so that I can start trying as well. I do have a son who can help me, but he is so quick about it, I need something that I can look at and step by step or a slow motion camera to use for replays.:confused:

Good luck!

---

### Post by markackerman8@gmail.com on 2010-04-09
> **dfarin said:**
> Mark,

You have been very patient about seeking this solution. Thanks from a true newbie who has been sitting on the sidelines, rooting you on.:popcorn:

Where did you learn the basics of modifying code so that I can start trying as well. 
Good luck!

Thanks soo much for a response ... new optimism!!!

I am sorry I cant help you with changing code as I don't know how other than patching.  For you or anyone who is patient enough to follow this I will give some new details.

I have yet again reinstalled my computer this time with MythBuntu.  It has seemingly brought me to the same spot, which is:
1/ the card is recognized and even works with TVTime and Analog Cable!.
2/ MythBuntu is seemingly setup right though times out when trying to "Watch LiveTV" with abnalog cable.

please remember I am sadly ignorant of many details (struggling for 1 mo. with this card and 1 year with my hvr-1500c (gave up on it for analog).

Here is some more info ... please help troubleshoot! :confused:


1/ From the dropdown list I chose "Analog V4l Capture Card", dev/video1, and it shows "Probed Information" as "Hauppaugge HVR-950Q [au0828]", so I assume it is right.

2/w.r.t. the firmware I have downloaded and compiled the latest from v4l-dvb. and here is my dmesg that may confirm it and help troubleshoot.

Thank you very much for any help troubleshooting this!

19.822691] tveeprom 0-0050: Hauppauge model 72101, rev B3F0, serial# 6793570
[ 19.822699] tveeprom 0-0050: MAC address is 00-0D-FE-67-A9-62
[ 19.822705] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[ 19.822711] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x8
[ 19.822717] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[ 19.822721] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[ 19.822727] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 19.822732] hauppauge_eeprom: warning: unknown hauppauge model #72101
[ 19.822736] hauppauge_eeprom: hauppauge eeprom: model=72101
[ 19.840159] au8522 0-0047: creating new instance
[ 19.840161] au8522_decoder creating new instance...
[ 19.951461] alloc irq_desc for 22 on node -1
[ 19.951465] alloc kstat_irqs on node -1
[ 19.951474] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 19.951558] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 20.305151] tuner 0-0061: chip found @ 0xc2 (au082
[ 20.611022] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[ 20.798873] xc5000: xc5000_attach(0-0061)
[ 20.798877] xc5000 0-0061: creating new instance
[ 20.803810] xc5000: Successfully identified at address 0x61
[ 20.803814] xc5000: Firmware has not been loaded previously
[ 20.804237] au8522 0-0047: attaching existing instance
[ 20.811747] xc5000: xc5000_attach(0-0061)
[ 20.811750] xc5000 0-0061: attaching existing instance
[ 20.816420] xc5000: Successfully identified at address 0x61
[ 20.816422] xc5000: Firmware has not been loaded previously
[ 20.816425] DVB: registering new adapter (au082
[ 20.816428] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 20.818900] Registered device AU0828 [Hauppauge HVR950Q]
[ 20.818981] usbcore: registered new interface driver au0828
[ 20.837187] xc5000: xc5000_sleep()
[ 21.552816] usbcore: registered new interface driver snd-usb-audio

[ 40.034460] xc5000: xc5000_is_firmware_loaded() returns False id = 0x2000
[ 40.039196] xc5000: xc5000_is_firmware_loaded() returns False id = 0x2000
[ 40.039199] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 40.039204] usb 1-3: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 40.069452] xc5000: firmware read 12401 bytes.
[ 40.069455] xc5000: firmware uploading...
[ 40.069457] xc5000: xc5000_TunerReset()
[ 43.189500] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 47.060030] xc5000: firmware upload complete...
[ 47.060046] xc5000: xc_initialize()

[ 51.380042] xc5000: xc5000_set_analog_params() frequency=6400 (in units of 62.5khz)
[ 51.380049] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 53.673929] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 53.673933] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC

---

### Post by markackerman8@gmail.com on 2011-08-24
If anyone is still reading this thread, I am still trying to get mythtv working with the hvr-960q.

It just doesn'y work with mythtv anymore and I am quite certain it has something to do with mythbackend/card/sound settings or myhtfrontend Sound Settings.  Has anyone got it working with mythtv and NTSC analog cable?????

Thanks in advance

Mark

---

### Post by satkins on 2011-09-24
If you have ever found out anything about why analog doesn't work in Myth please let me know also.

---

### Post by thatguruguy on 2011-09-24
[http://ubuntuforums.org/showthread.php?t=1634328](http://ubuntuforums.org/showthread.php?t=1634328)

---


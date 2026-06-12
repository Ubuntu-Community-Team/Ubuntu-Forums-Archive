---
title: "Issues with channel changing"
date: 2009-03-23
forum: Mythbuntu
---

### Post by spotslayer on 2009-03-23
Good day folks, 

I am having an issue with a new install of mythtv. Here is a list of my hardware.

64b AMD athlon processor 2800mhz single core
512k RAM
Two Hauppauge pvr-150 capture cards
Phillips mceusb ir receiver
Harmony880 remote
Scientific Atlanta 4250 stb

Mythbuntu Intrepid Ibex 8.10

Absolutely everything is working with the exception of changing channel. I can swap inputs,
see the menu, play videos using mplayer(pause, rewind, stop, all this works from the remote and keyboard). I am able to record whatever channel is chosen via the stb. I have tried using the provided changing scripts, change-channel-lirc.pl, change-channel-lirc.sh and one I found in mythbuntu wiki.That one is change-channel.py. Remote variable has been set in each. I have tried these from the command line as well as placing them in the input connections screens. My lircrc is using standard numeric numbers, 1,2,3 and irw output matches the codes in my lirc.conf. I have sucessfully run mythfilldatabase. Irsend from the command line works for all features except channel change. That returns this.

david@mythbox:~$ irsend SEND_ONCE Harmony880 5 4
irsend: command failed: SEND_ONCE Harmony880 4
irsend: repeating interrupted
david@mythbox:~$


The numbers appear at the top left, the new channel banner shows at the bottom of the screen. Then the screen freezes for several seconds and retuns to playing live TV on the same channel.
Here are the last few lines of my frontend log.

2009-03-23 16:51:34.542 Using protocol version 40
2009-03-23 16:51:38.773 DPMS Deactivated 
2009-03-23 16:51:39.610 AFD: Opened codec 0x34da830, id(MPEG2VIDEO) type(Video)
2009-03-23 16:51:39.610 AFD: codec MP2 has 2 channels
2009-03-23 16:51:39.610 AFD: Opened codec 0x3548d00, id(MP2) type(Audio)
2009-03-23 16:51:39.731 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-23 16:51:39.731 Opening ALSA audio device 'default'.
2009-03-23 16:51:39.808 mixer set channel 0 err -22: Invalid argument
2009-03-23 16:51:39.808 mixer unable to find control Master 1
2009-03-23 16:51:39.872 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-03-23 16:51:40.226 OSD Theme Dimensions W: 640 H: 480
2009-03-23 16:51:40.791 TV: Changing from None to WatchingLiveTV
2009-03-23 16:51:40.800 Realtime priority would require SUID as root.
2009-03-23 16:51:40.927 Video timing method: USleep with busy wait
2009-03-23 16:52:34.620 NVP: prebuffering pause
2009-03-23 16:52:36.303 NVP: Prebuffer wait timed out 10 times.
2009-03-23 16:52:37.953 NVP: Prebuffer wait timed out 10 times.
2009-03-23 16:52:55.398 NVP: prebuffering pause
2009-03-23 16:52:58.228 NVP: prebuffering pause
2009-03-23 16:53:46.548 TV: Attempting to change from WatchingLiveTV to None
2009-03-23 16:53:46.826 TV: Changing from WatchingLiveTV to None
2009-03-23 16:53:46.858 DPMS Reactivated.


Again this is a fresh install of mythbuntu and all the features work except channel changing.
I thank you for looking at this and truly hope someone has seen this and is able to help me.
I will provide any further information that is needed.

I just want in on the mythtv goodness.

Thank's
David

Believe me I have googled extensivly but have not found a solution.

---

### Post by volkswagner on 2009-03-24
How are you getting the signal to 4250?
Blaster or direct IR cable?

Have you tried firewire?

---

### Post by spotslayer on 2009-03-24
> **volkswagner said:**
> How are you getting the signal to 4250?
Blaster or direct IR cable?

Have you tried firewire?

I am using the blaster that plugs into the back of the mceusb. I have tried firewire using majoridiot's mythchanger program. When using fire wire and hve something set to record and I am watching TV using only the stb the tv channel will change. I also have a problem when watching live tv on one card and trying to record on the other card. The live tv will change from the input I am watching to the record input. 

Thanks for you input I would really like to get my mythbox up and running.

David

---

### Post by spotslayer on 2009-03-27
I have still not been able to make my ir change channel. I was able to remedy my issue with mythchanger with the help of majoridiot. I had ignorantly put a channel change script in both capture cards. It was not needed in the card connected directly to the coax.

I would still like to solve the lirc issue. So if you have any ideas, please let me know.

David

---


---
title: "Help with Secondary Backend"
date: 2008-10-09
forum: Mythbuntu
---

### Post by sgtstadanko on 2008-10-09
Hey All,

I am having trouble setting up mythbuntu 8.04 as a secondary backend.  I am using a PVR-150 with cable box plugged into the composite ports.  I can cat /dev/video0 > file.mpg and get picture and sound with mplayer. I can see the secondary connect to the primary mythbackend in its logs.  I can also see the new input in Myth when watching live tv and pulling up the list of inputs.  When I select it however it doesnt switch the input and the screen locks up and times out back to the menu.

I filled out sections 1-4 of mythtvsetup as per the on screen install instructions.  Is there something I need to go back and check or fill out?

thanks,
sgtstadanko

---

### Post by newlinux on 2008-10-09
look in your backend logs (on the secondary backend with the card) and see if there are some errors. (should be in /var/log/mythtv/).

Beyond that, we could double check what you put in the setup screens if you tell us how you filled them out, specifically the capture card settings and input connection settings.

---

### Post by sgtstadanko on 2008-10-10
Ok Here's the log from the secondary backend:
```
2008-10-09 14:35:01.093 Current Schema Version: 1214
Running as a slave backend.
2008-10-09 14:35:01.111 mythbackend: MythBackend started as a slave backend
2008-10-09 14:35:01.119 New DB connection, total: 3
2008-10-09 14:35:01.121 Connected to database 'mythconverg' at host: 192.168.1.1
14
2008-10-09 14:35:01.370 Channel(/dev/video0) Warning: You have not set an extern
al channel changing
                        script for a composite or s-video input. Channel changin
g will do nothing.
2008-10-09 14:35:01.990 Main::Registering HttpStatus Extension
2008-10-09 14:35:01.991 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-10-09 14:35:01.992 Enabled verbose msgs:  important general
2008-10-09 14:35:03.001 Connecting to master server: 192.168.1.114:6543
2008-10-09 14:35:03.003 Connected successfully
2008-10-09 14:35:11.119 mythbackend: Running housekeeping thread
2008-10-09 14:35:58.431 MainServer::HandleAnnounce Playback
2008-10-09 14:35:58.437 adding: osx as a client (events: 0)
2008-10-09 14:35:58.441 TVRec(8): Changing from None to WatchingLiveTV
2008-10-09 14:35:58.454 TVRec(8): HW Tuner: 8->8
2008-10-09 14:35:58.732 Channel(/dev/video0) Warning: You have not set an extern
al channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
2008-10-09 14:35:59.820 SG(Default) Error: FindNextDirMostFree: '/mnt/store/tv' does not exist!
2008-10-09 14:35:59.821 SG(Default) Error: FindNextDirMostFree: '/var/lib/mythtv' does not exist!
2008-10-09 14:35:59.906 TFW, Error: Opening file '/var/lib/mythtv/1039_20081009143558.mpg'.
                        eno: Permission denied (13)
2008-10-09 14:35:59.907 TVRec(8) Error: RingBuffer '/var/lib/mythtv/1039_20081009143558.mpg' not open...
2008-10-09 14:35:59.908 TVRec(8) Error: CreateLiveTVRingBuffer() failed
2008-10-09 14:35:59.908 TVRec(8) Error: Failed to create RingBuffer 2
2008-10-09 14:35:59.911 TVRec(8): Changing from WatchingLiveTV to None
2008-10-09 14:38:14.962 MainServer::HandleAnnounce Playback
2008-10-09 14:38:14.965 adding: osx as a client (events: 0)
2008-10-09 14:38:14.969 TVRec(8): Changing from None to WatchingLiveTV
2008-10-09 14:38:14.982 TVRec(8): HW Tuner: 8->8
2008-10-09 14:38:15.246 Channel(/dev/video0) Warning: You have not set an external channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
2008-10-09 14:38:16.321 SG(Default) Error: FindNextDirMostFree: '/mnt/store/tv' does not exist!
2008-10-09 14:38:16.358 TFW, Error: Opening file '/mnt/store/tv/1039_20081009143815.mpg'.
                        eno: Permission denied (13)
2008-10-09 14:38:16.358 TVRec(8) Error: RingBuffer '/mnt/store/tv/1039_20081009143815.mpg' not open...
2008-10-09 14:38:16.359 TVRec(8) Error: CreateLiveTVRingBuffer() failed
2008-10-09 14:38:16.360 TVRec(8) Error: Failed to create RingBuffer 2
2008-10-09 14:38:16.363 TVRec(8): Changing from WatchingLiveTV to None

```

Both /mnt/store/tv and /var/lib/mythtv exist on the secondary backend.

---

### Post by newlinux on 2008-10-10
Yoou still didn't give us your settings but my first guess is a permissions issue. Are those directories readable and writable by the mythtv user?

what do:
```

ls -l /mnt/store/ | grep tv

```
and 
```

ls -l /var/lib/ | grep mythtv

```

return?

---

### Post by newlinux on 2008-10-10
also, if either of these is a mounted filesystem make sure they mounted correctly.

---

### Post by sgtstadanko on 2008-10-10
yeah /mnt/store is is not writable and /var/lib/mythtv is owned by root for some weird reason.  The weird thing is I didnt setup any storage groups on the second backend.  It pulled the /mnt/store/tv from the primary. When I saw that in the logs i created a /mnt/store/tv like the dir structure on my primary.   I can nfs mount that directory but then I lose the extra disk space that I can get on the secondary.  /var/lib/mythtv is the default location and has the correct perms so I am not sure why it isnt able to write there.  I have reset perms on both /mnt/store/tv and /var/lib/mythtv and will check them after work.

here are my settings from mythtvsetup:

1. General
local backend
[INDENT]IP Address 192.168.1.106 Port 6543 status port 6544[/INDENT]
master backend
[INDENT]IP Address 192.168.1.114 Port 6543[/INDENT]
tv format - NTSC
VBI Format - none
Channel Freq. - us-cable
Your Local timezone - auto
File Management Settings
x Master Backend Override
HD Ringbuffer Size (KB) 9400
--The rest is the defaults

2. Capture Cards
[MPEG: /dev/video0 ]
Card Type - MPEG-2 encoder card (PVRx50, PVR-500)
Video Device - /dev/video0
Probed info - Hauppage WinTv PVR-150 [ivtv]
Default Input - Composite 1

3. Video Sources - this is pulling from the primary it appears
cable
Listings Grabber - North America (Schedules Direct)
User ID - xxxxx#xxxx.com
pAssword - XXXXXXX
Data Direct Lineup: AL01494:X
Channel Freq Table - Default

4. Input Connections
[ MPEG : /dev/video0 ] (Composite 1) -> cable 
Capture Device: [ MPEG : /dev/video0 ]
Input: Composite 1
Display Name : Cable-Secondary
Video Source - cable
External change channel command -  blank (this is a whole other issue...i have aMCE USB blaster and a SA3250 so not sure if that will work without using fw changer)
Preset Tuner to Channel: 3
Starting Channel : 39
Input Priorty ; 0

5 & 6 I did not touch.


Thanks for the help all.

---

### Post by ian dobson on 2008-10-10
Hi,

I think your problem is that you haven't setup an external channel changer script (Think IR-Blaster)

```
2008-10-09 14:35:01.370 Channel(/dev/video0) Warning: You have not set an external channel changing                        script for a composite or s-video input. Channel changing will do nothing.^
```

Regards
Ian Dobson

---

### Post by sgtstadanko on 2008-10-10
yeah.  i have a sa3250 cable box and a MCE USB IR blaster and havent been able to find a channel change script for that combo. Dont need to use the MCE remote as this is jsut a backend so not worried about that...just the blasting to the cable box.

Still though, shouldnt it just pull up whatever channel the cable box is manually tuned to?

was gonna tackle that beast after i got picture going.

---

### Post by newlinux on 2008-10-10
Yeah I think you should still get a picture even if the channel change script doesn't work (not sure - but it does just give you a warning around that one)... I figured you were getting to that one later... Have you considered using firewire to change the channel? I found it extremely reliable (on a motorola box, but others have it working on the SAs).

---

### Post by sgtstadanko on 2008-10-10
yeah.  i have used it before from a notebook when capturing HD.  I will need to buy a card for my desktop though.  Getting away from the no picture but if I were to use Firewire to change channels i believe i would need an external script as the internal Myth Changer for firewire can only be called if you are using that card to capture.

---

### Post by newlinux on 2008-10-10
Yeah I used a separate script, but it was readily available in the contrib folder (/usr/share/doc/mythtv-backend/contrib/channel_changers/). I found it much more reliable than the ir blaster. But if you need to buy a firewire card and already have a blaster...

---

### Post by sgtstadanko on 2008-10-10
success.  it was permissions!  now to get the MCE IRblaster working on a SA3250...or to buy a firewire card.  any good firewire recommendations?

---

### Post by newlinux on 2008-10-10
Glad you got that working.

sorry, no recommendations. Just try to get a cheap one and verify it is supported in Linux...

---


---
title: "Video gone, only audio"
date: 2012-05-31
forum: Mythbuntu
---

### Post by Sctmon on 2012-05-31
My wife was watching a recording from the library the other day and when it finished she tried to watch another program but this time just got a blank screen with audio. Every other program she tried was the same.
I fiddled about with it and changing the playback settings from VDPAU High quality to CPU++ sorted it. This is not ideal as I cannot play HD stuff I have on Myth video properly on the front end without it.
There were no updates or changes to the system, she just stopped watching something and strated another recording.

From the log extract below 'Failed to enable deinterlacing' looks like it may be thge problem.

Any suggestions as to why this is happening and how I can resolve it?


2012-05-30 07:18:30.773 Pulse: PulseAudio suspend OK
2012-05-30 07:18:30.810 AO: Opening audio device 'hdmi:CARD=NVidia,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-05-30 07:18:30.844 AudioPlayer: Enabling Audio
2012-05-30 07:18:31.056 VDPAU: Created 2 output surfaces.
2012-05-30 07:18:31.056 VDPAU: Created VDPAU render device 1920x1080
2012-05-30 07:18:31.202 Player(7): Forcing decode extra audio option on (Video method requires it).
2012-05-30 07:18:31.363 Player(7): Video timing method: USleep with busy wait
2012-05-30 07:18:31.364 TV: Changing from None to WatchingPreRecorded
2012-05-30 07:18:31.399 ScreenSaverX11Private: DPMS Deactivated 1
2012-05-30 07:18:31.399 Player(7): Failed to enable deinterlacing
2012-05-30 07:18:31.409 VDPAU: Added 2 output surfaces (total 4, max 4)
2012-05-30 07:19:13.840 TV: Attempting to change from WatchingPreRecorded to None
2012-05-30 07:19:13.911 VDPAU Painter: Clearing VDPAU painter cache.
2012-05-30 07:19:13.911 MythPainter: 16 images not yet de-allocated.
2012-05-30 07:19:14.214 Pulse: PulseAudio resume OK

---

### Post by Sctmon on 2012-06-02
Anyone?

---

### Post by anonymousdog on 2012-06-02
I would tend to create a VDPAU playback profile that uses no de-interlacing (just to rule out the de-interlacing filter).

---

### Post by Sctmon on 2012-06-02
The primary and fallback deinterlacers are set to none in the vdpau profile anyway if that is what you mean. I have tried other settings but it doesn't change anything.

It tried playing an hd movie using mplayer and it played but not well and mplayer gave a warning that my system is too slow to play the file. I suspect that vdpau acceleration is not working for some reason but I really don't know where to start to fix it.

---

### Post by nickrout on 2012-06-02
have you restarted X or rebooted?

---

### Post by Sctmon on 2012-06-03
Ha, reboot is the first thing I try! Sadly didn't help.  

I am not sure myth is at fault so suppose I need to look at potential hardware or  driver problems. The motherboard is an Asus AT3IONT

---

### Post by nickrout on 2012-06-03
try  running mythfrontend -v playback and see if you get any more clues.

---

### Post by Sctmon on 2012-06-03
Well, this is the output attached, hopefully it may make some sense to someone. I tried to keep it as short as possible.

The only part that jumped out at me was 
2012-06-03 06:56:35.310 VSYNC: DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2012-06-03 06:56:35.310 VSYNC: RTCVideoSync: Could not open /dev/rtc, Permission denied.

I cant really see what change on the system from stopping one recording which was working and trying to play another.

---

### Post by nickrout on 2012-06-03
> **Sctmon said:**
> Well, this is the output attached, hopefully it may make some sense to someone. I tried to keep it as short as possible.

The only part that jumped out at me was 
2012-06-03 06:56:35.310 VSYNC: DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2012-06-03 06:56:35.310 VSYNC: RTCVideoSync: Could not open /dev/rtc, Permission denied.

I cant really see what change on the system from stopping one recording which was working and trying to play another.

What playback profile are you using? 

Try slim and vdpau slim and see if it helps.

Also check your nvidia drivers are OK - /var/log/Xorg.0.log is a long read but will tell you what driver is running.

---

### Post by Sctmon on 2012-06-03
I will have a read throught the log today. I was using vdpau high quality and have tried vdpau normal and slim and none of them work now so have switched to cpu++ which does. I just can't play high def movies from the backed smoothly using that profile.

---

### Post by nickrout on 2012-06-03
> **Sctmon said:**
> I will have a read throught the log today. I was using vdpau high quality and have tried vdpau normal and slim and none of them work now so have switched to cpu++ which does. I just can't play high def movies from the backed smoothly using that profile.

sounds very much like nvidia drivers are not working

---

### Post by Lester_Burnham on 2012-06-03
What happens when you run
sudo nvidia-settings or select it from system menu.

Lester

---

### Post by Sctmon on 2012-06-03
> **Lester_Burnham said:**
> What happens when you run
sudo nvidia-settings or select it from system menu.

Lester
X server setting opens and seems to be normal - driver version 195.36.24


couldnt see any errors or warnings in the xorg log that seemed relevant, all related to the TVs EDID

The current driver version seems to be installed and active. Is there a way to install an older version?

Edit: Desktop effects seem to be working which makes me think the driver is ok but for some reason vdpau is not

---

### Post by Lester_Burnham on 2012-06-03
What is the video card?
Depending on what it is, I'd be installing something newer.

I though it was better to have desktop effects disabled. Not really sure though. Wait for Nick.

Lester

---

### Post by Sctmon on 2012-06-03
O scop> **Lester_Burnham said:**
> What is the video card?
Depending on what it is, I'd be installing something newer.

I though it was better to have desktop effects disabled. Not really sure though. Wait for Nick.

Lester

It is a small mini itx motherboard with onboard intel atom and nvidia ion so no scope really to replace it. It has been working fine for about a year now something on the system must have changed suddenly

---

### Post by Sctmon on 2012-06-03
Ok, I just tried this option in mplayer
mplayer  -vo vdpau -vc ffh264vdpau 
And it works fine playing video using hardware acceleration so seems that the problem is in myth or the player it uses. I checked all the profile settings for vdpau against the backend which does work and they are the same.

---

### Post by Lester_Burnham on 2012-06-03
> **Sctmon said:**
> O scop

It is a small mini itx motherboard with onboard intel atom and nvidia ion so no scope really to replace it. It has been working fine for about a year now something on the system must have changed suddenly

Hi, 

Hmmm. Interesting...
If you run hardware drivers or additional drivers, under settings, accessories or system. Does it give you the option to update to nvidia-current?

What version of mythbuntu are you running?

Lester

---

### Post by Sctmon on 2012-06-03
> **Lester_Burnham said:**
> Hi, 

If you run hardware drivers or additional drivers, under settings, accessories or system. Does it give you the option to update to nvidia-current?

What version of mythbuntu are you running?

Lester
This front end is running 10.04 and the nvidia-current drivers are the drivers in use.
I just posted to say I got mplayer to work and play video using vdpau acceleration but still cannot get myth to do it.

---

### Post by Lester_Burnham on 2012-06-03
> **Sctmon said:**
> This front end is running 10.04 and the nvidia-current drivers are the drivers in use.
I just posted to say I got mplayer to work and play video using vdpau acceleration but still cannot get myth to do it.

My stab in the dark, is part of Mythtv needs reinstalling. To re-configure it.

Lester

---

### Post by Sctmon on 2012-06-03
OK I seem to have solved but but not sure why it happened in the first place.

Editing the VDPAU high quality profile shows vdpaucolorspace=auto in the custom filters field. It is not present on the profile on the backend so I removed it and it works again! Same custom filter is also in VDPAU normal and slim (only on frontend) so removing them also works.

I have no idea how they appeared in there or if they were always there and stopped working.

---

### Post by nickrout on 2012-06-03
> **Sctmon said:**
> OK I seem to have solved but but not sure why it happened in the first place.

Editing the VDPAU high quality profile shows vdpaucolorspace=auto in the custom filters field. It is not present on the profile on the backend so I removed it and it works again! Same custom filter is also in VDPAU normal and slim (only on frontend) so removing them also works.

I have no idea how they appeared in there or if they were always there and stopped working.

I don't think you have said what version of mythtv you are using. Some of thos opotions have gone in 0.25.

---

### Post by Sctmon on 2012-06-04
Sorry, 0.24

Just happy it is working again!

---


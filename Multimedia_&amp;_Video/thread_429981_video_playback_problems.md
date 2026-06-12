---
title: "video playback problems"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by super.rad on 2007-05-01
When i try to play any type of video file its really slow and unwatchable and now when i double click on any video file it opens totem which just crashes and i have to force quit. i've downloaded and installed vlc and that'll play the videos but i get no sound.
I also have MPlayer but if i try to open any file in that i get an error saying

Error opening/initializing the selected video_out (-vo) device.

i think i've installed all the codecs needed for playback of all the file types.
If anyone has any suggestions/solutions that would be great. Thanks

---

### Post by super.rad on 2007-05-01
could it be my graphics card driver doing this? i have an ati card and i went to System>Administration>Restricted Drivers Managemer and ticked to use it

---

### Post by WinterWeaver on 2007-05-01
I'm having a similair problem.

I've installed all 4 gsreamer stuff, as well as the medibuntu things.

I have VLC installed.

When I play my avi's or mpegs in Totem, the video stutters, and the audio is out of sync.

When I play them through VLC, the audio stutters.

When I play them on Windows (dual boot) they are perfect.
On my previous install (EDGY) they were perfect.

I've every tried re-installing all the drivers.

Anyone know how to fix this?

Thanks,

WW

---

### Post by super.rad on 2007-05-01
i added 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
to my /etc/X11/xorg.conf and it'll play videos fine now. 

next problem, the sound is really bad in all the videos? any suggestions

---

### Post by super.rad on 2007-05-01
Found some errors from vlc aswell
oss error: cannot open audio device (/dev/dsp)
main error: couldn't find a filter for the conversion
main error: couldn't create audio output pipeline
oss error: cannot open audio device (/dev/dsp)
main error: couldn't find a filter for the conversion
main error: couldn't create audio output pipeline
oss error: cannot open audio device (/dev/dsp)
main error: couldn't find a filter for the conversion
main error: couldn't create audio output pipeline

for sound i use a sony usb audio device
can someone please help me to get vlc working with sound or sort out the sound in other programs

---

### Post by FuturePilot on 2007-05-01
> **super.rad said:**
> When i try to play any type of video file its really slow and unwatchable and now when i double click on any video file it opens totem which just crashes and i have to force quit. i've downloaded and installed vlc and that'll play the videos but i get no sound.
I also have MPlayer but if i try to open any file in that i get an error saying

Error opening/initializing the selected video_out (-vo) device.

i think i've installed all the codecs needed for playback of all the file types.
If anyone has any suggestions/solutions that would be great. Thanks
Open MPlayer and right click and go to Preferences.

Go to the Video tab and select the xv X11/Xv driver. Click ok then close MPlayer and then try opening a video with it.

---

### Post by super.rad on 2007-05-02
thanks that worked great. The sound on totem is still really bad but mplayer and vlc both seem to work fine now so i'll just stick with them.

---

### Post by TheWama on 2008-05-26
> **super.rad said:**
> i added 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
to my /etc/X11/xorg.conf and it'll play videos fine now. 

next problem, the sound is really bad in all the videos? any suggestions

This worked for me too.  I was having super-slow, unwatchable video playback, and no audio from CDs, MP3s, or any other media file.  Only flash video was working alright.

So I followed the directions above, but more specifically, those lines should go in the "Device" config section of that xorg.conf.

---


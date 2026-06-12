---
title: "ubuntu, please get my dvd playback stable?!"
date: 2008-12-20
forum: Multimedia Software
---

### Post by heapy on 2008-12-20
Hey there Ubuntu!
Please help me to get my laptop m1530 to play a DVD without it freezing after 5-10 mintues!

I have been re-installing xubuntu hardy 8.04.1 every evening, dloading the OS updates and trying both VLC and totem without joy. I have tried installing libdvdcss2, and that does allow me to view the films, but just as i settle down to watch, after a bit the system simply locks up with the sound of the film repeating over, and over, and over!!!

i dont know how to fix this problem, and it has really annoyed me so could youse help me out to fix this.

Also, if you need some more info to diagnose this, could you text back how i can.

Thanks in advance,

>heapy

---

### Post by heapy on 2008-12-21
... can anyone shed some light to this issue please,

---

### Post by xc3RnbFO8P on 2008-12-21
> Last edited by heapy; 21 Minutes Ago at 03:26 PM.. Reason: i did notice something to do with pulse audio not running when running VLC from terminal. I am new to linux
Then you should show the output here ;)

---

### Post by heapy on 2008-12-21
here you go ringi lad. does this help?

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 57169D1D2D3
libdvdnav: DVD Serial Number: 26FD6895
libdvdnav: DVD Title (Alternative): 57169D1D2D3
libdvdnav: Unable to find map file '/home/thomas/.dvdnav/57169D1D2D3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000174
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000da2e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0029ef23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0029ef29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002acaf1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002acaf7
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[00000352] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000353] pulse audio output error: Failed to connect to server: Connection refused
[00000353] pulse audio output error: Pulse initialization failed

---

### Post by heapy on 2008-12-21
oh c'mon, does anyone have a clue for me ?

---

### Post by xc3RnbFO8P on 2008-12-21
I found this:
> elgilicious
September 6th, 2008, 04:25 AM
I figured out the problem after checking out a Fedora forum.

"Settings" -> "Preferences" -> tick "Advanced Options" -> "Output Modules" -> select audio output module from the dropdown menu (I use ALSA) -> expand "Output Modules" and select the subcategory that matches your output module -> "Refresh List" -> select your sound device

Now, every video I throw at VLC plays perfectly. VLC was just telling me that I hadn't selected the sound card yet.

---

### Post by heapy on 2008-12-21
thank you , am trying that right now.. have done exactly what elgilicious has done with alsa.. fingers crossed..

---

### Post by heapy on 2008-12-21
well, i selected ALSA as the output module... and : HDA Intel: STAC92xx Analog (hw:0,0) as the ALSA device name..

ran VLC, & got this after 3 minutes of DVD playback, followed by the same style lockup.

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 57169D1D2D3
libdvdnav: DVD Serial Number: 26FD6895
libdvdnav: DVD Title (Alternative): 57169D1D2D3
libdvdnav: Unable to find map file '/home/thomas/.dvdnav/57169D1D2D3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000174
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000da2e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0029ef23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0029ef29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002acaf1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002acaf7
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[00000352] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)
[00000353] alsa audio output error: write failed (Broken pipe)

---

### Post by xc3RnbFO8P on 2008-12-21
In Volume Control try to change device.

---

### Post by heapy on 2008-12-21
i just changed the device in volume control to #0 HDA intel ... (the only other option, from default)

it hasn't made a difference mate, still getting the locking up problem just as before :(

VLC media player 0.8.6e Janus
[00000301] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000307] alsa audio output error: write failed (Broken pipe)
[00000307] alsa audio output error: write failed (Broken pipe)
[00000307] alsa audio output error: write failed (Broken pipe)
[00000307] alsa audio output error: write failed (Broken pipe)

---

### Post by heapy on 2008-12-22
last night i had a poke around, and noticed that in 'services' the alsa mixer service wasnt ticked. so i enabled it, and the dvd movie did play for 30 minutes perfectly, then locked up again.

I have selected ALSA from the menu's in VLC, and selected the HDA intel output device in vlc also. 

And if i hover over volume control on the top taskbar of the desktop, it does say HDA intel.

Is there anything else I can try? - oh, and i have done apt-get remove alsa, apt-get install alsa..

thanks ubuntu
ho-ho-ho

---

### Post by heapy on 2008-12-22
OK just ran vlc -vv from terminal , & got this..
[00000307] main audio output debug: using audio mixer module "float32_mixer"
[00000307] main audio output debug: removing module "float32_mixer"
[00000307] main audio output debug: looking for audio mixer module: 3 candidates
[00000307] main audio output debug: using audio mixer module "float32_mixer"
[00000307] main audio output debug: removing module "float32_mixer"
[00000307] main audio output debug: looking for audio mixer module: 3 candidates
[00000307] main audio output debug: using audio mixer module "float32_mixer"
[00000307] main audio output debug: removing module "float32_mixer"
[00000307] main audio output debug: looking for audio mixer module: 3 candidates
[00000307] main audio output debug: using audio mixer module "float32_mixer"
[00000340] main private debug: decoded 105/106 pictures
[00000304] main video output warning: late picture skipped (149285)
[00000304] main video output warning: late picture skipped (109315)
[00000304] main video output warning: late picture skipped (69325)
[00000304] main video output warning: late picture skipped (29333)
[00000304] main video output warning: late picture skipped (29472)
[00000304] main video output warning: late picture skipped (44552)
[00000304] main video output warning: late picture skipped (4582)
[00000340] main private debug: decoded 106/108 pictures
[00000340] main private warning: dts != current_pts (-279377)
[00000307] main audio output warning: PTS is out of range (-38636), dropping buffer
[00000307] main audio output warning: audio drift is too big (-311377), clearing out
[00000307] main audio output warning: mixer start isn't output start (-119569)
[00000307] main audio output debug: audio output is starving (325575), playing silence
[00000307] alsa audio output debug: recovered from buffer underrun
[00000307] main audio output debug: audio output is starving (38985), playing silence
[00000307] alsa audio output debug: recovered from buffer underrun


..does this help ??

edit:
[00000307] main audio output debug: audio output is starving (38186), playing silence
[00000307] alsa audio output debug: recovered from buffer underrun
[00000307] alsa audio output error: write failed (Broken pipe)
[00000307] alsa audio output debug: recovered from buffer underrun
[00000307] alsa audio output error: write failed (Broken pipe)
[00000307] alsa audio output debug: recovered from buffer underrun

---


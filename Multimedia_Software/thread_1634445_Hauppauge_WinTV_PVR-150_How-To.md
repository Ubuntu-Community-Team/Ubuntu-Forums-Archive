---
title: "Hauppauge WinTV PVR-150 How-To"
date: 2010-11-30
forum: Multimedia Software
---

### Post by InkyDinky on 2010-11-30
This is a little write up on my experience getting a Hauppage PVR150 that I bought off of Craigslist up and running. 
I know this is old hat but I still fumbled a bit and figured this still might help somebody.
The little guy has the family of Conexant chips that has a driver developed for it over at [http://www.ivtvdriver.org](http://www.ivtvdriver.org).
It seems that Hauppage even supports this Linux development (or at least doesn't mind it as it points Linux people to ivtvdriver.org.)
Anyway head over to ivtvdriver.org and download the appropriate driver for your chipset. 
I picked up mine using ```
wget http://dl.ivtvdriver.org/ivtv/archive/1.4.x/ivtv-utiils-1.4.0.tar.gz
``` since I was having problems with getting the file via my browser.
Follow the directions on the ivtvdriver.org website to perform your extraction and make install of the drivers.
I didn't have to install any other dependencies as the webpage warned about (using depmod -a .)
You may want to reboot just to keep yourself sane although modprobe is supposed to take care of reloading the appropriate things.
You'll also want to pick up xawtv.
xawtv can be picked up from the repositories.
At this point if you ```
dmesg | grep ivtv
``` you should see some helpful output. If not then go back and take a look and try to figure out what you missed.
This is what I get:
```

nicky@nicky-desktop:~/Shared$ dmesg | grep ivtv
[   16.903917] ivtv: Start initialization, version 1.4.1
[   16.904165] ivtv0: Initializing card 0
[   16.904170] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.908163] ivtv 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.142602] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   17.355918] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   17.468905] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   17.566536] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   17.595020] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   17.698122] IRQ 17/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.698863] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   17.699043] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   17.699194] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   17.699330] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   17.699473] ivtv0: Registered device radio0 for encoder radio
[   17.699478] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   17.700803] ivtv: End initialization
[   18.341012] ivtv 0000:00:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   18.356401] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   18.556133] ivtv0: Encoder revision: 0x02060039
[  322.118242] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[  322.118250] ivtv0: Cause: the application is not reading fast enough.
[59192.471004] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[59192.471012] ivtv0: Cause: the application is not reading fast enough.
[59235.130814] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[59235.130821] ivtv0: Cause: the application is not reading fast enough.

```
The lines that state "Registered device XXX for encoder XXX " are important.
They tell me that my MPG video stream is on /dev/video0 and my audio stream is on /dev/vbi0.
Now we need to tune the card to a usable channel.
We'll use scantv to find which channel(s) have signals on them.
If you are getting your signal from a cable box it is probably coming in on channel 3 since that is what channel most cable boxes output their signal on. 
However, if you have a antenna hookup you might want to scan for your channels.
```
scantv -c /dev/video0 -C /dev/vbi0
```
Check out the man pages for more options.
You'll get a menu as to what type of system you are on. 
I chose NTSC and us-cable although I did try multiple combinations.
It will then go about jumping from frequency to frequency looking for usable signals.
Here is some of the output I received with my coax pluggged into the card from my ATT uverse cable box.
```

scanning channel list us-cable...
1    ( 73.25 MHz): no station
2    ( 55.25 MHz): no station
3    ( 61.25 MHz): CARTOON NETWORK
[CARTOON NETWORK]
channel = 3

```
Now that we have a signal on a given channel we need to tune the card to that channel so we can pick up and play that signal.
We'll use ivtv-tune for that.
```
ivtv-tune -c 3
``` or ```
ivtv-tune -f 61.25
``` will get the job done.
Now that we have things set up we can capture the signal.
```
cat /dev/video0 > test.mpg
```
This will capture signal until we stop the cat process with Ctrl-C.
Now play that stream with your favorite video player.
I used vlc but anything should work as long as it has the appropriate codecs.
My videos came out a bit large, ~ 1.25GB for 1/2 hr show, due to the old MPG2 HW encoder in the PVR150.  
The videos also had a bit of annoying interlacing effects.
The interlacing is tolerable in live action tv, but in animation is very noticeable.
I then ran the output videos through mencoder using the x264 codec and this shrank the files to a more manageable ~200MB size and also got rid of the interlace problem.
```
mencoder input.mpg -oac copy -vf pp=ci -ovc x264 -o output.avi
```
The only problem here is that all of my computers can play old school mpeg-2 video but only one of my computers can play x264 :(

For live viewing there are supposedly two ways although I've only been able to get one to work: mplayer (didn't work) and vlc (did work).
```
mplayer /dev/video0
``` would pick the signal up for a second and then completely freeze my computer. 
Maybe you'll have better results.
In VLC, Ctrl-C to open the capture device dialog. 
Select PVR for the Capture Mode.
Device name: /dev/video0
Radio device name: /dev/vbi0
Frequency: 61250 (since we are in kHz and not MHz)
Now just hit play! 
You should connect to the stream and be watching live tv!

---

### Post by saedelaere on 2010-12-03
If anyone wants to use a complete frontend to watch and record TV, have a look at [TV-Viewer]("http://tv-viewer.sourceforge.net/"). Please note, 64bit Tcl/Tk shipped by Ubuntu is buggy, consider installing ActiveTCL as described [here]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl").

Regards

---

### Post by joama on 2011-01-04
Hi,
Thanks for the post, it did make my life easier. Every thing worked except for audio:( whether it was recorded or live tv. I have been searching for hours with no luck. The computer plays sound fine, so I really don't know what to do.

Thanks

---

### Post by saedelaere on 2011-01-04
> **joama said:**
> Hi,
Thanks for the post, it did make my life easier. Every thing worked except for audio:( whether it was recorded or live tv. I have been searching for hours with no luck. The computer plays sound fine, so I really don't know what to do.

Thanks

Do you ask for TV-Viewer? If so, state your question [here]("http://ubuntuforums.org/showthread.php?t=763698") and attach the logfiles you can find in ~/.tv-viewer/log

---


---
title: "HOWTO set up a Hauppauge HVR-950Q on myth .24 and mythbuntu 10.10"
date: 2010-11-30
forum: Mythbuntu
---

### Post by thatguruguy on 2010-11-30
This is how I set up my Hauppauge HVR-950Q so that I can watch and record live tv on myth .24.  I don't cover how to set up a remote or storage groups, etc.  This set up works for me, but YMMV.

**Preliminary Steps**

If you have mythbuntu 10.10, I'm going to assume you have pulseaudio installed. You should also install the helper utilities:
```
sudo aptitude install pavucontrol paprefs pavumeter
```

If you are going to use remote frontends, you need to set up your backend box so that it has a fixed address on your network.

If you live in the US or Canada, I strongly suggest that you pay the $20 (US) and get a one-year subscription to [Schedules Direct]("http://www.schedulesdirect.org/").  It's by far the easiest way to get programming information for the analog channels on the card, and I use it to get programming information for the digital channels as well (for reasons detailed below).  

I installed mousepad as my text editor on mythbuntu.  You can use whatever you're comfortable with.

**Step 1: Getting Audio to Work**

In my experience, the thing I had the most trouble with was getting audio to work.  Until audio was sorted out, my mythtv would hang and/or crash randomly. Although most of the information I'll give in the rest of this how-to came from [Mark Ackermans's comments]("http://www.kernellabs.com/blog/?p=1388") on the [Kernel Labs blog]("http://www.kernellabs.com/blog/"), his suggestion to use /dev/desp1 as the audio device for the analog card doesn't work on mythbuntu 10.10, since OSS was removed from the kernel.  Therefore, following the information [here]("http://pulseaudio.org/wiki/PerfectSetup"), we're going to set up or modify an asound.conf file:

```
sudo mousepad /etc/asound.conf
```We're going to add the following to the file:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```That makes pulseaudio the default sound driver for alsa, which is what we want.  NOTE: **It will NOT work to create this file as ".asoundrec" in your home directory**, since it needs to be system-wide. You should also be aware that, unlike earlier incarnations of mythtv, it is NOT necessary to pass "EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1" to the environment if you are using mythtv .24, since the audio system of mythtv was re-written to include pulseaudio support.

Go to your mixer settings, which should be accessible by clicking the appropriate icon (it looks like a speaker) on the top panel of the mythbuntu screen.  Under "Sound card", choose "HVR-950Q (Alsa Mixer)". If that tab is blank, click on the "Select Controls..." button. The only control I have is "Digital In"; click it to make it active.  Check the box for "Digital In".

**Step 2: Dealing with the Time-Out Issues on the 950Q**.

You'll need to edit or create two files, and put the same information in both.

```
sudo mousepad /etc/modprobe.d/local.conf
sudo mousepad /etc/modprobe.d/xc5000.conf
```In each file, place the following:
```
options xc5000 no_poweroff=1 debug=1
```[B]
Step 3: Testing[/B]

Now is a good time to re-boot your computer to make all of the above-mentioned changes take place.  After re-booting, I used tvtime (which you can get through synaptic) to see if I could tune analog channels.  It worked without a hitch, so I moved on to setting up the mythtv backend.

**Step 4: Setting up the MythTV Backend**

First, open the "General Settings" section. If you set up a fixed ip for your mythbox on your network, you need to enter it in the "IP address" sections for both Local Backend and Master Backend.  I left the rest of the settings on the first page of the General Settings section untouched. Since I'm using cable, I chose "us-cable" for the "Channel frequency table" part of Locale Settings (the second page of the "General Settings" section). I left the rest of the settings under General Settings alone. Now, we can start setting up the digital and analog parts of the tuner.

**Step 5: The Digital Tuner**

Choose "Capture Cards" to start setting up the tuners.

Assuming you don't have any tuners set up, choose "New capture card." (If you already tried to set up the tuners and it didn't work, you may consider deleting all tuners first. The "Card type" for the digital part of the 950Q is "DVB DTV capture card (v3.x)."

Click on "Recording Options" and change "Max Recordings" to 1. Although the card supports up to 2 recordings on the digital side, I've had it lead to weird hangs.

I also unclick the "Use DVB card for active EIT scan", due to occasional hangs when it is checked.

Click on the "Finish" button, and then go to "Video Sources."

Since my cable carrier (Insight) has two different sets of listings for digital and analog cable, I set up two different listings within my Schedules Direct account (you can have up to four within one S.D. account).  Likewise, I set up two different video sources for the card in mythtv.  

For the digital part of the card, I entered "insight-digital" (you can call it whatever you want) in the section for "Video source name."  Then I provided my Schedules Direct information, and made sure that it pointed to the digital listing for my cable carrier when I clicked on the "Retrieve Lineups" button.  Then, it was time to hit "Finish" and move on to "Input Connections."    

Click on the DVB listing to set it up. I gave it the name, "digital" (without the quotes, of course) in the section "Display name."  Then I pointed the "Video source" to the "insight-digital" source I had created. I chose "Never" for "Use quick tuning" and un-checked the "Use Dish-Net long-term EIT data" since I'm using Schedules Direct for my listings.  Then, click on the "Scan for channels" button.  The only way I could get myth to reliably find all available channels was to choose the "Scan of all existing transports" option under "Scan Type."  In fact, I scanned for channels twice to make sure all channels were captured.  After the scans were done, I closed the backend setup.

**DO NOT RUN "mythfilldatabase" at this point!**  You're not done, yet.

**Step 6: Setting up Sound on the Front End**

Open mythfrontend.  Go to "Utilities / Setup".  Choose "Setup", then "General".  First, make sure your "Hostname" points to the same ip address noted in your backend setup. then, click "Next" a few times until you get to "Audio System."  Click the "Scan for audio devices" button.  Choose "ALSA: Pulse" for your device.  On the next page, click the box for "Use internal volume control". Under "Mixer device" choose "ALSA:default". For "Mixer controls" choose "Master". Set the volume for both the Master mixer and PCM mixer to 100.  Click "Next" a few times, then exit.  Close down mythfrontend to allow the changes to take effect.  

**Step 7: Setting up the Channels for the Digital Tuner**

You should now be able to open mythfrontend and watch tv on the digital tuner.  At this point, I went through all the channels and decided which ones I wanted to keep, and made a note of the corresponding channels on the Schedules Direct listing.  For example, AMC has two listing on my Schedules Direct lineup for digital cable: channel 26 and channel 610.  In order to avoid conflicts with the analog listings (which only go from 2-99), I chose the upper listing for each channel I wanted to keep (e.g., I chose 610 for AMC, above).

After going through each channel, I closed mythfrontend and re-opened mythbackend. Then I went to Channel Editor. First, I deleted the channels I knew I wasn't keeping (the half-dozen shopping channels, etc.).  For the remaining channels, I edited each entry to make sure that the channel number corresponded to the listing in Schedules Direct, making sure that there would be no conflicts with my analog listings.  Again, as an example, I changed the listing for AMC from "1-3" to "610" (rather than "26", which would have conflicted with the analog listing). I also used the "Channel Name" and "Callsign" given by Schedules Direct.  I left the "Use on air guide XMLTV ID" checkbox unchecked, since I'm using Schedules Direct for my listings.

After editing each entry appropriately, it was time to set up the analog tuner.

**Step 8: The Analog Tuner**

Choose "Capture Cards" to begin.

Choose "New capture card."  The "Card type" for the analog part of the card is "Analog V4L capture card."  The "Video device" is "/dev/video0"" on my system. The "Audio device" is "ALSA:default".  I set the "Force audio sampling rate" to 48000. Click "Finish"

Now, set up a video source to be used by the card. Click on "Video sources" in the main menu.  Choose "New video source".  After choosing a name for this source ("insight-analog", in my case), I again added my information for Schedules Direct, but made sure that this entry pointed to the analog listing I had set up on the Schedules Direct site.  After that was finished, I moved on to "Input connections" in the main menu.

Choose the "[V4L:/dev/video0]" listing under the Input connections menu. In the "Display name" box I wrote "analog".  I pointed the "Video source:" to the newly-created "insight-analog" video source I created.  This time, instead of choosing to scan for channels, I clicked on "Fetch channels from listing source".  After that ran for a moment, I clicked "Next", then "Finish".

At this point, you can close mythbackend setup.  **This time, you DO want to run "mythfilldatabase"**.  You can go make yourself some coffee or a sandwich while it runs, because it takes a while.

**Step 9: Setting up Recording Profiles**

This is particularly important if you're going to stream your tv to other devices. When mythfilldatabase finishes, re-open mythfrontend.  Go back to "Utilities / Setup". Click on "Setup", then "TV Settings".  Scroll down to "Recording Profiles".

You shouldn't have to make any changes to the settings under Hardware DVB Encoders.  For Software Encoders (V4L based), make the following changes:

Go to each profile (Default, Live TV, High Quality and Low Quality) and make the following changes:

- Change the "Width" from "480" to "720".
- On the next page, choose "MPEG-4" for the Codec.
- On the next page after that, choose "MP3" for the audio Codec.  Again, I set the Sampling rate to 48000.

Once you've updated all four profiles, you may want to shut down and then restart mythfrontend.

You should now be able to re-open mythfrontend, and watch/stream/record live TV.  Good luck.

---

### Post by brianmay27 on 2010-11-30
Great guide!!!
Im reinstalling a fresh copy now and will step through this in a few min. 

Thanks for taking the time to post this!

Brian

---

### Post by brianmay27 on 2010-11-30
> **brianmay27 said:**
> Great guide!!!
Im reinstalling a fresh copy now and will step through this in a few min. 

Thanks for taking the time to post this!

Brian

Ok, I have went through the guide and I have a question before I go too far, I don't have digital cable at all, the school still uses all analog, do I have to still setup the capture card to have a digital side or can I just setup the analog card?

---

### Post by thatguruguy on 2010-11-30
You can certainly run the analog part of the card without setting up the digital part.

Also, I just realized that I had left out step 6 on setting up audio on the front end.  That's now been fixed.

---

### Post by brianmay27 on 2010-11-30
> **thatguruguy said:**
> You can certainly run the analog part of the card without setting up the digital part.

Also, I just realized that I had left out step 6 on setting up audio on the front end.  That's now been fixed.

Hmm, having problems then. I went back and updated the audio on the frontend but when I go to watch live tv, It shows the first station fine, but when i try to change the channel it goes black and exits out back to the home screen. 
I tried the tuner in tvtime and all the channels work find there. 

Any idea of whats wrong?

---

### Post by thatguruguy on 2010-11-30
That happened to me the first time. A reboot solved it.

You may also have better luck if you change channels by first pulling up the program guide (hit the "S" key) and choosing the next channel from there.

---

### Post by brianmay27 on 2010-11-30
> **thatguruguy said:**
> That happened to me the first time. A reboot solved it.

You may also have better luck if you change channels by first pulling up the program guide (hit the "S" key) and choosing the next channel from there.

Still nothing, tried both.

my log is at [http://mythbuntu.pastebin.com/YMNcWy4t](http://mythbuntu.pastebin.com/YMNcWy4t) 
```


[LIST=1]
[*]2010-11-30 13:45:59.249 TVRec(1): Changing from None to WatchingLiveTV
[*]2010-11-30 13:45:59.318 TVRec(1): HW Tuner: 1->1
[*]2010-11-30 13:46:01.015 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:01.127  NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings,  Recording Profiles and setup the four 'Software Encoders' profiles.   Assuming RTjpeg for now.
[*]2010-11-30 13:46:01.174 NVR(/dev/video0) Error: Unknown audio codec
[*]ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused
[*] 
[*]2010-11-30 13:46:01.376 AudioInALSA(default) Error: pcm open failed: Connection refused
[*]2010-11-30 13:46:01.426 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2010-11-30 13:46:01.468 NVR(/dev/video0) Error: Failed to init audio input device
[*]2010-11-30 13:46:01.542 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]ALSA lib pulse.c:229:(pulse_connect)  2010-11-30 13:46:01.597 ProgramInfo(): Updated pathname '':'' ->  '1002_20101130134600.nuv'
[*]PulseAudio: Unable to connect: Connection refused
[*] 
[*]2010-11-30 13:46:01.795 AudioInALSA(default) Error: pcm open failed: Connection refused
[*]2010-11-30 13:46:01.870 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2010-11-30 13:46:01.868 RecBase(1:/dev/video0): GetKeyframePositions(0,9223372036854775807,#1) out of 1
[*]2010-11-30 13:46:01.798 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:02.129 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:02.192 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:02.244 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:04.499 TVRec(1): HW Tuner: 1->1
[*]2010-11-30 13:46:11.556 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:11.649 MainServer::ANN Playback
[*]2010-11-30 13:46:11.698 adding: DVR as a client (events: 0)
[*]2010-11-30 13:46:11.750 ProgramInfo(): Updated pathname '':'' -> '1002_20101130134600.nuv'
[*]2010-11-30 13:46:11.799 TVRec(1): Changing from WatchingLiveTV to None
```
[/LIST]
Also when it exits it gives the error irrecoverable recorder error

---

### Post by thatguruguy on 2010-11-30
It looks like pulseaudio isn't set up correctly.  Did you follow the instructions in step 1?

Also, make sure you have libasound2-plugins installed in synaptic.

Your post reminded me that I didn't include set up instructions for Recording profiles.  Give me a second and I'll correct that omission.

---

### Post by thatguruguy on 2010-11-30
Also, open the ALSA volume control on your top panel. You should have "HVR-950Q" as an option under Sound card. Make sure that the box for "Digital In" is checked.

---

### Post by brianmay27 on 2010-12-01
> **thatguruguy said:**
> Also, open the ALSA volume control on your top panel. You should have "HVR-950Q" as an option under Sound card. Make sure that the box for "Digital In" is checked.

Hmm well I had a problems there, I had to make sure the mac mini drivers for audio were installed correctly, even then the volume indicator never showed up so I installed the gui alsa and the audio output showed up as well as the hvr. I ensured the digital in was selected. I never got the volume to work either in the tvtime or on the one channel in mythtv.

Its weird that it seems to work with what ever channel It open to but it just cant change. I removed the install to try something else but I plan on reinstalling it and re-following the instructions. 

Could it be that the drivers for the mac sound are not working and thats causing all the problems? In anycase I dont need the audio to work on this computer, I plan on using a remote frontend most of the time (If i can get that to work)

Thanks again for your time! Its really helping.

Also Im going to try it in a vm to see if I get a different outcome. Fingers crossed

---

### Post by thatguruguy on 2010-12-01
> **brianmay27 said:**
> Hmm well I had a problems there, I had to make sure the mac mini drivers for audio were installed correctly, even then the volume indicator never showed up so I installed the gui alsa and the audio output showed up as well as the hvr. I ensured the digital in was selected. I never got the volume to work either in the tvtime or on the one channel in mythtv.

Its weird that it seems to work with what ever channel It open to but it just cant change. I removed the install to try something else but I plan on reinstalling it and re-following the instructions. 

Could it be that the drivers for the mac sound are not working and thats causing all the problems? In anycase I dont need the audio to work on this computer, I plan on using a remote frontend most of the time (If i can get that to work)

Thanks again for your time! Its really helping.

Also Im going to try it in a vm to see if I get a different outcome. Fingers crossed

Actually, sound sometimes dies when changing between analog channels on my setup, as well.  I had forgotten about it because I usually stick to the digital side of the tuner. I think it may be a glitch in the analog sound processing within the unit itself.  When it happens, I usually just exit watching live tv and then click on "Watch TV" again, and the sound will be back on.

FWIW, I usually don't use the mythbackend (which is hooked up to my main TV) for watching TV. If I want to watch TV on that set, I just use the regular tuner from the cable company.  I use the computer that hosts the backend to A) stream TV to the other computers in the house, B) watch movies, and C) play video games, particularly with the various emulators I have installed in Mythgame.

Good luck with whatever you end up doing.

---

### Post by Lone_Joker on 2010-12-01
Hey do you have the remote for the 950Q running? If you do was there anything special that you had to do to get it to work?

By the way, if I connected this to an STB it would be picking up digital right?

---

### Post by brianmay27 on 2010-12-01
> **thatguruguy said:**
> Actually, sound sometimes dies when changing between analog channels on my setup, as well.  I had forgotten about it because I usually stick to the digital side of the tuner. I think it may be a glitch in the analog sound processing within the unit itself.  When it happens, I usually just exit watching live tv and then click on "Watch TV" again, and the sound will be back on.

FWIW, I usually don't use the mythbackend (which is hooked up to my main TV) for watching TV. If I want to watch TV on that set, I just use the regular tuner from the cable company.  I use the computer that hosts the backend to A) stream TV to the other computers in the house, B) watch movies, and C) play video games, particularly with the various emulators I have installed in Mythgame.

Good luck with whatever you end up doing.
Well I think Im SOL on this one. Ive been messing around for hours with no success.

I forgot to mention (dont know if its important) but when I watch tv on windows, both the blue and green ligh come on. However on mythtv, I only get the blue. 

Either way, im calling this a problem with mythtv as the card works fine in tvtime. Im not sure what is wrong with it.

Thanks for the guide tho, Wish my setup went as flawlessly as yours.


Last min thought, did you start off with a fresh install of 10.10 or did you upgrade from another version?

---

### Post by thatguruguy on 2010-12-01
> **brianmay27 said:**
> Well I think Im SOL on this one. Ive been messing around for hours with no success.

I forgot to mention (dont know if its important) but when I watch tv on windows, both the blue and green ligh come on. However on mythtv, I only get the blue. 

Either way, im calling this a problem with mythtv as the card works fine in tvtime. Im not sure what is wrong with it.

Thanks for the guide tho, Wish my setup went as flawlessly as yours.


Last min thought, did you start off with a fresh install of 10.10 or did you upgrade from another version?

My setup was hardly flawless; it took over a week to get it to work when I upgraded to 10.10 and myth .24.

I originally had mythbuntu 10.04 and myth .23.1 on this computer, and did a fresh install when I moved up to 10.10.

---

### Post by thatguruguy on 2010-12-01
Lone_Joker, I'm going to answer your questions in reverse order.

> **Lone_Joker said:**
> If I connected this to an STB it would be picking up digital right?

If I'm not mistaken, a set-top box converts digital cable to analog, rather than the other way around.  Before televisions had built-in digital tuners (which has only been the norm here in the US for the past few years), digital HAD to be converted to analog for it to be viewable on TV.  If you're running the signal through a set-top box first, you'll need to have an IR blaster on your mythbox in order to change the channel on the STB.  I don't have the kind of set-up, because I want the kids to be able to watch one thing on the TV to which my mythbox is hooked up while I stream another channel to my laptop.

> **Lone_Joker said:**
> Hey do you have the remote for the 950Q  running? If you do was there anything special that you had to do to get  it to work?

No, I don't, and I don't intend to use the bundled remote.  About a year ago (before I even started using mythtv), I built a home-brew IR serial port receiver. Unfortunately, the computer I bought for my mythbox doesn't have serial ports, and I haven't gotten around to installing one, although I intend to do that eventually. Right now, I'm using a wireless keyboard and mouse on the mythbox, and the receiver I built is used occasionally with my laptop.  

Here's a picture of the receiver, which I sometimes call "Homebrew R2" or "Ir2-D2":

---

### Post by webbles1 on 2010-12-02
I just tried to follow this walkthrough and was not successful in getting sound to work.  I have a hd5500 and only use it for analog.  It used to use /dev/dsp1 on 10.04.

In step 1, in my mixer settings, I see the Conexant CX8801 sound card that is part of the hd5500.  "Select Controls" shows me "Playback" and "Capture".  I tried selecting one and/or the other.  Playback gives me a tab with volume control.  Capture gives me a tab with a checkbox labeled "Capture".

I skipped step 2 as it is dealing with a different card.

In step 3, tvtime worked fine (just no sound)

In step 4, I already had that setup.

I skipped step 5, as I don't use digital.

In step 6, when I click "scan for audio devices", I don't see a "ALSA: Pulse".  I see a bunch of "ALSA:*:CARD=Intel,DEV=0" which is the normal sound card on my box.  I don't know what I did wrong for that is causing the "ALSA: Pulse" to not show.  Is there something I need installed?

I skipped step 7.

I did step 8 and step 9.

LiveTV doesn't have any sound and I can't change channels without it crashing.  I'm guessing it is the missing "ALSA: Pulse" in step 6, but I don't know why it isn't showing up.

---

### Post by thatguruguy on 2010-12-02
> **webbles1 said:**
> 
In step 3, tvtime worked fine (just no sound)


If you don't have sound, tvtime is not working fine.  Have you tried rebooting since making the change to asound.conf?

Have you tried running tvtime from a terminal to see what kind of messages are generated?

> In step 6, when I click "scan for audio devices", I don't see a "ALSA: Pulse".  I see a bunch of "ALSA:*:CARD=Intel,DEV=0" which is the normal sound card on my box.  I don't know what I did wrong for that is causing the "ALSA: Pulse" to not show.  Is there something I need installed?
Again, you may need to reboot to get the changes you made to /etc/asound.conf to take effect.  After doing so, could you run the following in a terminal, and post the results here?
```
aplay -L
```

---

### Post by webbles1 on 2010-12-02
> **thatguruguy said:**
> If you don't have sound, tvtime is not working fine.  Have you tried rebooting since making the change to asound.conf?

Have you tried running tvtime from a terminal to see what kind of messages are generated?


I've tried rebooting the box, but I don't think tvtime has ever had sound for me.  Also, when I boot with my kernel that has OSS enabled (and /dev/dsp1), tvtime still doesn't have sound but mythtv does.

Running tvtime -v, I get:

```

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/webbles1/.tvtime/tvtime.xml
cpuinfo: CPU Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz, family 6, model 7, stepping 10.
cpuinfo: CPU measured at 2593.587MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10900000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 800x600.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Xfwm4 and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 73: Intel(R) Textured Video.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/webbles1/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'cx8800', card 'pcHDTV HD5500 HDTV' (bus PCI:0000:03:02.0).
videoinput: Version is 8, capabilities 5010011.
videoinput: Width 768 too high, using 720 instead as suggested by the driver.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (60).
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 732x549 window inside 768x549 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
tvtime: Cleaning up.
Thank you for using tvtime.

```I don't see anything in there about sound not working or working.

> **thatguruguy said:**
> 
Again, you may need to reboot to get the changes you made to /etc/asound.conf to take effect.  After doing so, could you run the following in a terminal, and post the results here?
```
aplay -L
```

```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
default
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Hardware device with all software conversions

```

---

### Post by thatguruguy on 2010-12-02
> **webbles1 said:**
> I've tried rebooting the box, but I don't think tvtime has ever had sound for me.  Also, when I boot with my kernel that has OSS enabled (and /dev/dsp1), tvtime still doesn't have sound but mythtv does.

Running tvtime -v, I get:
[snip]
I don't see anything in there about sound not working or working.


I don't see anything in there about sound at all.  Which is strange, because mine shows:

```
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 1024x576 window inside 1024x576 space.
Found "HVR-950Q : USB Audio (hw:1,0)"
```

Do you have a /dev/mixer?  You actually shouldn't, if you don't have OSS.

It looks like "pulse" is listed as a device under ALSA.  I'm surprised that myth doesn't see it.  Have you tried to scan for audio devices again?

---

### Post by webbles1 on 2010-12-02
I realized that the tvtime output was when I was using my custom kernel with OSS built in.  This is the output for the normal Ubuntu kernel.

```

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/webbles1/.tvtime/tvtime.xml
cpuinfo: CPU Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz, family 6, model 7, stepping 10.
cpuinfo: CPU measured at 2593.589MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10900000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 800x600.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Xfwm4 and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 73: Intel(R) Textured Video.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/webbles1/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'cx8800', card 'pcHDTV HD5500 HDTV' (bus PCI:0000:03:02.0).
videoinput: Version is 8, capabilities 5010011.
videoinput: Width 768 too high, using 720 instead as suggested by the driver.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (60).
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 732x549 window inside 768x549 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
tvtime: Cleaning up.
Thank you for using tvtime.

```

I see the "Can't open device /dev/mixer" but it doesn't find another audio device.

I've attempted to rescan for devices in MythFrontend multiple times and I do not see anything different.

---

### Post by webbles1 on 2010-12-04
I've figured out why I didn't have alsa: pulse.  I somehow didn't have pulseaudio completely installed.  I was reading [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup) and decided to install some of the helper packages just in case (sudo aptitude install pavucontrol paprefs pavumeter) and that installed pulseaudio with them.

So, I've got the frontend using pulse and changing channels has started to work.  But I don't have any sound from LiveTV or from new recordings.

If I run "sox -c 1 -t alsa default -t alsa default", I hear the tv channel fine.  If I do "pactl load-module module-loopback" (from [http://www.pulseaudio.org/ticket/665](http://www.pulseaudio.org/ticket/665)) I hear the TV while in MythTV but it isn't synced up correctly (because of the picture buffering).  And opening pavucontrol shows sound coming from the card.

So, I'm almost there.  I just don't know why MythTV and tvtime are not getting the sound.

---

### Post by brianmay27 on 2010-12-07
Hot damn!!! That did it! I can now change channels. Im having a problem where past a certian channel it just shoes static. Ill look into it in the AM. Thanks Webbles1!!

---

### Post by thatguruguy on 2010-12-07
Thanks, I'll make sure to mention that in the how-to.

---

### Post by markackerman8@gmail.com on 2011-01-15
I am struggling yet again with sound and my HVR-950Q when watching/recording analog cable with mythtv .... HELP

It is definitely  narrowed down to a setting in mythtv's backend for the card (I think), why
because it's working in tvtime, my "other pvrusb2 card is working which shows the frontend setup is fine (I think), and in the past it was a change in the backend capture card audio device that worked (presently it is at ALSA:default - the only option.

Any help would be appreciated

and just for laughs I am the guy "Mark Ackerman" mentioned in the first post on "how not to do it" :o

Thanks, Mark

---

### Post by Adamal on 2011-01-19
I noticed in your post you said the HVR-950Q card supports up to 2 recordings on the digital side.  I thought the card only supported 1.  Where did you find the information that it can record 2?

Your guide is great by the way, I used with Ubuntu 10.10 and Mythbuntu 10.10.  The sound settings were easier to get working in Ubuntu, but following your guide I got everything working.

---

### Post by Adamal on 2011-01-19
Duplicate post, ubuntu forums are having issues at the moment I guess.  I don't see a delete option.

---

### Post by LazyDad on 2011-02-20
Anyone hear about the HVR-950Q resulting in deleted Input connections?

I was rebuilding my mythbuntu box, Previous build was with 1 PVR-150 and had been done a while back with vr. 9 something.  I had an 950Q that I never got working with the old build, so I tried under the new build, Mythbuntu 10.10.    I found this guide from thatguruguy when it came to hooking things up.  I was looking forward to having the 950Q working and another analog input.


Other than skipping the PulseAudio stuff because the ASLA was working fine, I was doing great and everything was working.   Until a reboot.    After a reboot, all of the sudden I showed error status on the tuners and the a message that both tuners were in use but Myth wasn't recording or something to that effect.   Lots of frustration and troubles later, I reinstalled from scratch (again) and all was working, again... Until a reboot.


Total frustration.    I configured the PVR-150 first, then the 950Q (VL4).  (Only analog because I wasn't worried about the digital side yet.  I have an HDHomerun that I was planning on using for that.)   Before reboot, TVTime worked with the 950Q also, and no problems with sound as long as I didn't change anything.  It didn't last long.


On the reboot, I finally figured out the INPUT CONNECTIONS were being blanked.   The card showed up, but with no input connection associated.   At first I thought it was a fluke until lots of changes and finally getting it corrected and running.  Figured I'd reboot just to make sure and they were instantly deleted again.


 It was not deleting just the 950Q's Input connection, but also the one for the PVR-150.   I unplugged the 950Q, and found another PVR-150 I had salvaged from a previous setup and the Input connection doesn't disappear.   In an effort to cover all bases, I reinstalled the 950Q and configured it and had all 3(!) Working.    Then I did a reboot and found that the 950Q Input Connection was deleted and ONE of the PVR-150's were deleted also.    SOO...  I guess the lesson learned is to warn you not to use the 950Q with the PVR-150's. 


Sure, I'm probably the only nut that would still have these, right?  I dunno.    Btw, unplugged the 950Q and reconfigured the PVR-150's (after deleting cards) and again they worked even after reboots.  Don't know if anyone had ever seen this type of issue before where the 950Q will result in Input Connections being deleted if used with the PVR-150, but it does.

---

### Post by cnickl on 2011-03-03
Stupid newbee question: How do I display my Back and Frontend log?

Also: I waked though the entire process described here and I still get the "Please Wait..." and then redirect to the main menu when I click on Watch live TV.

I know my Hauppage HVR-850 works, because I can watch TV using ME-TV and it works great with picture and sound.

Using MythTV I can not get any digital channels.  Scanning for Analog channels works and it find them, but like I said above "Please wait..."  I'm waiting since 4 days for this to work and its frustrating.

---

### Post by cnickl on 2011-03-03
OK, I'm totally confused.  Here is the readout of my logs:

```
home:~$ tail -f /var/log/mythtv/mythbackend.log

2011-03-03 20:23:23.231 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 20:38:23.302 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 20:53:23.377 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 21:08:23.442 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 21:23:23.505 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 21:38:23.570 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 21:53:23.639 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 22:08:23.717 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 22:23:23.802 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-03 22:38:23.880 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

home:~$ tail -f /var/log/mythtv/mythfrontend.log

2011-03-03 19:12:22.128 Spawning LiveTV Recorder -- end
2011-03-03 19:12:22.129 GetEntryAt(-1) failed.
2011-03-03 19:12:22.130 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2011-03-03 19:12:22.130 TV Error: HandleStateChange(): LiveTV not successfully started
2011-03-03 19:12:22.130 We have a RingBuffer
2011-03-03 19:12:22.186 TV Error: LiveTV not successfully started
2011-03-03 19:12:22.198 ScreenSaverX11Private: DPMS Deactivated 1
2011-03-03 19:12:22.199 ScreenSaverX11Private: DPMS Reactivated 1
2011-03-03 19:12:28.710 AudioPulseUtil: Resume Success
2011-03-03 19:12:28.710 Deleting UPnP client...
```

Anybody have any idea what going on?

---

### Post by amblinn on 2011-09-08
Just wanted to say THANK YOU for this very helpful guide.  I'm a total Linux and MythTV newbie, and have been trying to get back & front end running for analog cable on a System76 Meerkat Ion Net-top (Ubuntu 11.04), using an HVR-850 (same chipset as the 950Q).  The two additional things I had to do to get this working were to (a) make sure I had the latest packages for Mythbuntu from Synaptic (the ones that installed automatically from the Mythbuntu control center were a version old), and to change my audio in backend capture card setup to use "ALSA:hw:1,0" instead of "ALSA:default".  The "default" setting kept giving me PulseAudio errors in mythbackend.log.

---

### Post by markackerman8@gmail.com on 2011-09-13
I am trying yet again to get this card working with mythtv (6 months with no luck)

You can see 2 previous unanswered posts from me, I hope this one gets a response and I will promptly reply and once figured out, I will post my solution for others with the same problem.

Please help me trouble shoot this, I don't know what else to try.

Like others, it works well in tvtime, sound and video, in mythtv nothing, just recorder failed message after it says tuning for a few seconds.  My pvrusb2 is working in mythtv so that says a lot, suggesting it is something in the backend.  The only thing to change there is in the capture card setup/Audio Device, and I have tried,
1/ ALSA:Default
2/ ALSA:hw:2,0, and 
3/ ALSA:plughw:2,0

Could someone please ask me some questions to troubleshoot this, I don't know what else to try?

Please and thanks,  

Mark Ackerman

---

### Post by thatguruguy on 2011-09-13
My cable carrier no longer carries analog cable signals, so I'm only using the digital side of the card now.  In fact, there's no way for me to check anything here regarding analog setups.

What is the backend log saying?  Is there anything at all about sound?  Do you have pulseaudio installed?

---

### Post by markackerman8@gmail.com on 2011-09-15
I finally got it working, and here is how, and it should help others.

Mythtv has compatibility issues and kernell labs (Kevin) has solved it, fewwww. So until Myth 0.25 comes out use this alternative repository for mythtv 0.24

sudo add-apt-repository ppa:mythbuntu/0.24
(from launchpad with fixes for the HVR950Q)

also I did a complete uninstall of mythtv and re installed, and no synaptic or purge commands don't work... 

you need to also remove all contents in:

/var/lib/mythtv & mysql
/usr/share/mythtv & mysql
/home/myhtv

reinstall
Done Solved
and for sound,
  To use ALSA, in the backend/card type set Audio Device to  HVR950Q's device numbers (not ALSA:default)
• cat /proc/asound/cards ...
&#8728; if the card index specified is index=2, set it to ALSA:plughw:2,0
&#8728; try ALSA:hw:2,0       (worked for me To use ALSA, in the backend/card type set Audio Device to  HVR950Q's device numbers (not ALSA:default)
• cat /proc/asound/cards ...
&#8728; if the card index specified is index=2, set it to ALSA:plughw:2,0
&#8728; try ALSA:hw:2,0       (worked for me! - without the "plug")

I sure hope this helps others.  Now I started this thread (in a way and now finish it - for now) - thanks for your efforts

---

### Post by thatguruguy on 2011-09-15
It strikes me that if you had installed the Mythbuntu Control Center and set up the updates properly, that would have installed the correct ppa for you.  The complete wipe of mythtv from your system seems to be overkill, since the updates would have corrected the error.

---

### Post by jcobban on 2011-09-15
Thank you for the effort you have put into trying to straighten out the confusion about using this device.

I still cannot get anywhere.

[LIST=1]
[*]No matter what I set as the card type for the Hauppage 950Q I never get the channel scan enabled.
[*]Using the setting you suggest if I try to manually add a channel I am not given the option of specifying ATSC.  I am using rabbit ears and there are no longer any NTSC OTA channels in North America.
[*]When I try to run MythTv frontend at the points in your process where your suggest, I get the error "Could not connect to the master backend server."  When I look through the various panels the only "IP Address" I can see is, as expected "localhost".
[/LIST]

---

### Post by markackerman8@gmail.com on 2011-09-15
> **thatguruguy said:**
> It strikes me that if you had installed the Mythbuntu Control Center and set up the updates properly, that would have installed the correct ppa for you.  The complete wipe of mythtv from your system seems to be overkill, since the updates would have corrected the error.

Guruguy, you don't give me enough credit, haha perhaps that's fair with my history double haha. BUT this repository (though seemingly simple - is a repository WITH a FIX for a KNOWN issue with the hvr950q and has been patched by devin - so COOL.

and with all I tried nothing is overkill at this point.  For others, problems with mythtv that seem odd, and out of the ordinary, are often solved with a COMPLETE!(only as outlined previously - works - strange I know) reinstall of mythtv (not the OS Mythbuntu).

I hope that helps others, and clarifies the previous post. AND THANKS Guruguy for all our ongoing efforts.

Mark Ackerman

---

### Post by thatguruguy on 2011-09-15
> **jcobban said:**
> Thank you for the effort you have put into trying to straighten out the confusion about using this device.

I still cannot get anywhere.

[LIST=1]
[*]No matter what I set as the card type for the Hauppage 950Q I never get the channel scan enabled.
[*]Using the setting you suggest if I try to manually add a channel I am not given the option of specifying ATSC.  I am using rabbit ears and there are no longer any NTSC OTA channels in North America.
[*]When I try to run MythTv frontend at the points in your process where your suggest, I get the error "Could not connect to the master backend server."  When I look through the various panels the only "IP Address" I can see is, as expected "localhost".
[/LIST]


I'm recording some stuff right now, so I can't turn off my back end to look at settings. w/r/t your first two issues.

As to issue number 3, you need to find out the ip address of your backend on your network.  You can do that by opening a terminal on your backend and typing the following:
```
ifconfig
```
Once you know the ip of your backend, you need to enter it in both places on your backend setup.  Then your frontend will be able to see it.

---

### Post by thatguruguy on 2011-09-15
Also, you need to make sure you're using the correct frequency tables when you're scanning.  Read [this]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_%28For_ATSC/QAM_Tuner_Cards_--_USA/Canada%29#Scanning_for_channels") and [this]("http://www.mythtv.org/wiki/Dvbscan"). The tuner should be set to DVB in the setup before trying to scan.

---

### Post by thatguruguy on 2011-09-15
> **markackerman8@gmail.com said:**
> BUT this repository (though seemingly simple - is a repository WITH a FIX for a KNOWN issue with the hvr950q and has been patched by devin - so COOL.

I get that.  However, I already had that repository in my sources list, by simply going to [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) and following the instructions.  I guess I assumed everyone does that when they first set up Mythbuntu, but I recognize what happens when one [ASSUME]("http://www.youtube.com/watch?v=6hrLj8QEAgI")s something.

---

### Post by markackerman8@gmail.com on 2011-09-16
> **thatguruguy said:**
> I get that.  However, I already had that repository in my sources list, by simply going to [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) and following the instructions.  I guess I assumed everyone does that when they first set up Mythbuntu, but I recognize what happens when one [ASSUME]("http://www.youtube.com/watch?v=6hrLj8QEAgI")s something.

It is NOT the same repository, I am quite sure, read this ...from my friend Mike whoe solved this thru
[email]micalizzi2k@yahoo.com[/email] Mike Micalizzi to me
show details Sep 14 (2 days ago)
Steven said,

June 9, 2011 at 11:10 pm

On a suggestion from a Mythbuntu developer, I tried the PPA version of the package **libmyth-0.24-0, version 2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3** from the PPA referenced at [http://www.ubuntuupdates.org/ppas/69](http://www.ubuntuupdates.org/ppas/69) . Also had to update mythtv-backend from the PPA to match that).

That one worked for me. Apparently the V4L2/V4L patch that seemed to be the cause of my problem was removed (see revision 442 at [https://code.launchpad.net/~mythbuntu/mythtv/mythtv-fixes](https://code.launchpad.net/~mythbuntu/mythtv/mythtv-fixes)).

So, I guess my saga is at an end  . I’ll just use the PPA until the main repo gets updated

 
So problem is likely an update to v4l that breaks this card, which makes sense.  It seems the PPA stream has this removed, probably so does the daily builds of mythbuntu, but I'd go with the PPA.  Just set the repository up for this.
 
Mike

but perhaps I don't get something, 

Mark
p.s. if this wasn't the fix then it was my **complete** reinstall of mythtv and mysql

---

### Post by hansdown on 2011-09-16
Thanks for your work with this, [email]markackerman8@gmail.com[/email].

You are very helpful.

---

### Post by markackerman8@gmail.com on 2011-09-16
> **hansdown said:**
> Thanks for your work with this, [email]markackerman8@gmail.com[/email].

You are very helpful.

Hansdown,

Thank you VERY much much for your kind words,  you are very welcome.

[email]markackerman8@gmail.com[/email]

and jcobban I sent you a private mail thru this website, as would be happy to help a fellow Canadian, haha.

---

### Post by thatguruguy on 2011-09-16
> **markackerman8@gmail.com said:**
> It is NOT the same repository, I am quite sure

I'm even more sure that it IS the same repository.  As a test, I tried to apt-get-install it, and apt told me that it was the same one that was already installed.  Here's the result:

```
executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 427BA16F0EC4E54037AD4C3F13551B881504888C
gpg: requesting key 1504888C from hkp server keyserver.ubuntu.com
gpg: key 1504888C: "Launchpad PPA for Mythbuntu Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

See the lines that say, "gpg: key 1504888C: "Launchpad PPA for Mythbuntu Developers" not changed" and "gpg:              unchanged: 1"?  That's because the repository was already installed on my system. Considering the fact that I know that I didn't install the repository by hand previously, the only way that could happen is if the repository you mentioned is the same one available through the mythbuntu web site.  And really, why would there be two different ***official*** ppas for the mythtv team?

Again, it was an error for me to assume that you had gone to the mythbuntu site and followed the instructions there to set up the fixes repository. I should have suggested that you do that from the beginning, but since that advice is pretty common in numerous threads in this forum, I assumed that everyone does it already.

---

### Post by markackerman8@gmail.com on 2011-09-17
Hey Guru, if I may call you that,

Thanks for the reply, as I sure would like to know why my 950q wasn't working with mythtv for 6 months.  Was it my COMPLETE purging and reinstall of mythtv and mysql, or the repository thing I did that day, hmm?

Either way it's now working with mythtv- but why wasn't it??????

Thanks
p.s I went to the mythbuntu website and installed the repo from there to see if it would change anything, and it just installed mythbuntu-control-center repo, I think. double hmmm:?::?:

---

### Post by nickrout on 2011-09-17
Mark, I beg to differ.

The repo you pointed to at [http://www.ubuntuupdates.org/ppas/69](http://www.ubuntuupdates.org/ppas/69) is the same as you get from mythbuntu-repos. In lucid both add the line:

deb [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu) lucid main

to your software sources.

I suspect the error is to do with the removal of v4l1 from ubuntu kernel sources, which pretty well destroyed all analogue recoding in mythbuntu because the myth packages were compiled against v4l1. This has been fixed in the mythbuntu repo and the ppa (which are the same) and that's why your card works with the updated packages.

---

### Post by thatguruguy on 2011-09-24
> **markackerman8@gmail.com said:**
> Hey Guru, if I may call you that,

Thanks for the reply, as I sure would like to know why my 950q wasn't working with mythtv for 6 months.  Was it my COMPLETE purging and reinstall of mythtv and mysql, or the repository thing I did that day, hmm?

Either way it's now working with mythtv- but why wasn't it??????

Thanks
p.s I went to the mythbuntu website and installed the repo from there to see if it would change anything, and it just installed mythbuntu-control-center repo, I think. double hmmm:?::?:

It's working now because you have the correct repository installed, and didn't before.  There isn't a "mythbuntu-control-center repo" independent of the mythtv repo that you install from the mythbuntu site.  The problems you had were because you didn't do the very basic step of installing the correct repo from the mythbuntu site.

The COMPLETE purging you did was completely unnecessary, since that has nothing to do with getting the correct packages from the daily fix builds.  You created your own problem by not doing the basic stuff you should have done in the beginning, and then you did a lot of unnecessary stuff when you finally did the right thing.

Summary for anyone else having problems with the analog portion of the HVR-950Q:
1. Go to [http://www.mythbuntu.org/](http://www.mythbuntu.org/)
2. Click the "Download" button to get to the [Download page of mythuntu.org]("http://www.mythbuntu.org/download-type")
3. Click the "Enable bug fix update via Mythbuntu Repos" link, and follow the instructions.

---

### Post by williamtdr on 2012-03-10
Great tutorial! Very detailed. However, when following your instructions, I run into the following two errors after trying  the first scan for channels in mythtv: A dialog stating "Error tuning to transport". Pressing enter displays the second error dialog : "Programmer error: Failed to handle tune complete". Is there something I'm doing wrong? I have till tommorow to get this tuner working and an worried. Help will be greatly appreciated. I'm using Mythbuntu 11.10, downloaded yesterday. I don't know what kernel, sorry!

---


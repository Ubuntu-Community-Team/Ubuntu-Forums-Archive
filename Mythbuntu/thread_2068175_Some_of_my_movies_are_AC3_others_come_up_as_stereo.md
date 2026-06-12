---
title: "Some of my movies are AC3 others come up as stereo So no sound sometimes"
date: 2012-10-08
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-08
So here is the problem on my old raid I have 3.9 TB of movie VOB files , when played back in myth or xbmc these movies playback with either AC3 or stereo obviously stereo is not going to output out of a coax/optical output  so I have to change the setting on the output device for each movie that is different otherwise I wont hear anything. The only way around this I can see is to have two simultaneous analog and digital outputs on the playback machines, or batch convert the whole lot into a different format?

Thoughts?  :confused:

---

### Post by TheFu on 2012-10-08
No real answer.  Much more specifics about your hardware, codecs, and equipment is probably needed to "know" the answer.

VOB files are huge. Why not convert them all to about 1/3rd the size and drop all the non-extras?  
Handbrake-CLI at 19.5R doesn't show any artifacts that I notice.  It can transcode pretty easily at about an hour per 2hr movie for the conversion to h.264 with audio copies (I retain English, French and Spanish audio) and subtitles included in the resulting MKV file. Of course, the CPU and RAM available will matter. Don't bother transcoding if your XBMC machine is an Atom-based or low end CPU and you probably want to pull the VOB directory over to the physical machine, even on a GigE LAN.

I don't keep any intermedia VOB files around (deleted when I box up the DVD to the attic), but I can say that AC3 or Stereo doesn't seem to matter for playback through HDMI connections.  I don't have optical or coax audio connections. Sorry.

My xbmc box has nvidia hardware and MPEG + h.264 codec support built-in.  I suppose the drivers could be handling the audio conversion to PCM for me, but I know that a WD TV Live HD never had sound issues before I switched to XBMC either.

I also record TV shows and retain whatever audio channels were included in the broadcast. PBS often has 3+ audio tracks, which makes it fun to find the correct one to mark as "main" during playback.

---

### Post by nickrout on 2012-10-08
> **RTIInstaller said:**
> So here is the problem on my old raid I have 3.9 TB of movie VOB files , when played back in myth or xbmc these movies playback with either AC3 or stereo obviously stereo is not going to output out of a coax/optical output  so I have to change the setting on the output device for each movie that is different otherwise I wont hear anything. The only way around this I can see is to have two simultaneous analog and digital outputs on the playback machines, or batch convert the whole lot into a different format?

Thoughts?  :confused:ay stereo won't play out your coax/optical out? It does on my system.

What bitrate is the audio on the the files that do not play properly. mediainfo helps you to find out.

---

### Post by RTIInstaller on 2012-10-09
[SIZE=2]I am looking at replacing the video card as the best solution. 
[/SIZE]**[SIZE=2]Looking at this card because it has HDMI audio out. its silent and has a low profile which I need  ASUS GeForce 210 1GB 64-bit DDR3 PCI Express [/SIZE]**

 [SIZE=2]http://www.amazon.com/EN210-SILENT-DI-1GD3-V2/dp/B004I8W4VI 

It is also on XBMC's list of working cards for future updates [http://wiki.xbmc.org/index.php?title=AudioEngine](http://wiki.xbmc.org/index.php?title=AudioEngine) [/SIZE]

---

### Post by nickrout on 2012-10-09
> **RTIInstaller said:**
> [SIZE=2]I am looking at replacing the video card as the best solution. 
[/SIZE]**[SIZE=2]Looking at this card because it has HDMI audio out. its silent and has a low profile which I need  ASUS GeForce 210 1GB 64-bit DDR3 PCI Express [/SIZE]**

 [SIZE=2]http://www.amazon.com/EN210-SILENT-DI-1GD3-V2/dp/B004I8W4VI 

It is also on XBMC's list of working cards for future updates [http://wiki.xbmc.org/index.php?title=AudioEngine](http://wiki.xbmc.org/index.php?title=AudioEngine) [/SIZE]

Replacing the video card will not solve this problem. Why don't you respond to my previous reply?

---

### Post by RTIInstaller on 2012-10-09
> **nickrout said:**
> Replacing the video card will not solve this problem. Why don't you respond to my previous reply?

I have not checked the bit rate but its an old winfast px 8600gt tdh card from 2007. 

The sound does however play great.. pcm, ac3 and so forth through the Zotac zbox id41 I am using as  the other front end

The digital audio is coming off the old msi motherboard.

I would much rather come up with a single hdmi solution to the situation 

Thanks

:wink:.

---

### Post by BicyclerBoy on 2012-10-09
The GT210 was rubbish when it was released..

Better choices:
The GT620 (rebadged 530) or 520 (==610) or 430

note: none of the 600 series cards are kepler, just badge re-engineering..

The HD4000 GPU in latest intel iCPUs would be a match for some of the above.
The intel drivers (with vaapi) is getting close to being a good option.

---

### Post by nickrout on 2012-10-09
> **RTIInstaller said:**
> I have not checked the bit rate but its an old winfast px 8600gt tdh card from 2007. 

The sound does however play great.. pcm, ac3 and so forth through the Zotac zbox id41 I am using as  the other front end

The digital audio is coming off the old msi motherboard.

I would much rather come up with a single hdmi solution to the situation 

Thanks

:wink:.sounds to me like your spdif to 48kHz, it is possibly sending analogue at 44.1kHz. There is a setting in advanced audio in mythtv's frontend setup screens.

---

### Post by RTIInstaller on 2012-10-10
> **BicyclerBoy said:**
> The GT210 was rubbish when it was released..

Better choices:
The GT620 (rebadged 530) or 520 (==610) or 430

note: none of the 600 series cards are kepler, just badge re-engineering..

The HD4000 GPU in latest intel iCPUs would be a match for some of the above.
The intel drivers (with vaapi) is getting close to being a good option.

Yeah but from what I have been told they are lower power consumption. I wanted to go with a 430 but I have a very small chassis and power supply.  A lot of guys on line have said good things when using the 210 with myth buntu. That all said see my reply to nick below.

---

### Post by RTIInstaller on 2012-10-10
> **nickrout said:**
> sounds to me like your spdif to 48kHz, it is possibly sending analogue at 44.1kHz. There is a setting in advanced audio in mythtv's frontend setup screens.

Well I did a stupid thing and put the 210 video card in my machine and guess what?

Now it wont boot into the Gui, it just drops into a command line asking for a user name and password.  I did all the usual recommended stuff such as a command line update of the nividia drivers and so forth trid to load gnome from a comand line but nothing, it is just plain detrumined to boot to the comand line and stay there  

:mad:

---

### Post by RTIInstaller on 2012-10-10
Oh well its just a front end machine, there is nothing on it anyway so I am just going to reinstall and hope for the best................

---

### Post by RTIInstaller on 2012-10-10
Hey is there a way around the myth tv front end screen that pops up and demands to be filled out before letting you go to the desktop?

Never mind, I hit alt f2 which let me access the drop down menus so I could un-check myth front-end from the boot up list :-)

---

### Post by RTIInstaller on 2012-10-12
The reinstall coupled with the new 210 video card and  plughw:1,7   Fixed my audio problems completely :guitar:

---

### Post by dev678 on 2012-10-18
Set speakers mode in Control Panel - Sounds and Multimedia - Audio - Sound Playback - Advanced. Furthermore, audio card drivers often have their own utilities for switching of speakers configuration. It is necessary to set the proper configuration at both locations - within audio card driver settings and within the Control Panel.For Creative audio card it is necessary to switch off all sound effects and equalizers, otherwise there can be a loss of central/rear channels.SPDIF mode is required only in case of digital connection to external decoder/receiver exist. It is important previously to ensure whether the receiver connected correctly (refer to audio card and receiver documentation).It is necessary to check “SPDIF” box in filter settings to switch the SPDIF mode on.
-------------------------------------------------------------------------------------------
[software company in bhubaneswar]("http://www.alphaconfig.com/"),[software companies in bhubaneswar]("http://www.alphaconfig.com/")

---

### Post by BicyclerBoy on 2012-10-18
answering post #9
```

Model    TDP (W)
GT210    30.5
GT510    25
GT520    29.5
GT430    49
GT610    29
GT620    49 (retail)
(data from wikipedia)

```
The GT610 has same shader performance as GT520..

The TDP is the max design dissipation; does not means this is the actual dissipation under normal use.
The VDPAU decoder only burns 5-10W.
The OpenGL/shader programs (de-interlace/sharpen etc) burn more.

GT520,610,620 can decode 2 HD streams (stereo).

The GT210 is old junk.
The GT520 can not run 2xadv. deinterlacer (vector de-interlace).
The GT610 must be very similar.
All nVidia cards run at full clock speed if 2 or more monitors are attached.

So the best bottom end low power card is GT610 esp if you do not use TV broadcast for playback.

---

### Post by anthony67 on 2012-11-22
Replay gain volume adjustments
    When enabled, XBMC will read the Replay Gain information encoded in your audio files by a program such as MP3Gain and normalize the sound levels accordingly. You have the option of either using track levels or album levels. 
PreAmp Level - Replay gained files
    level in dB - default is 89dB per standard 
PreAmp Level - Non replay gained files
    level in dB - default is 89dB per standard 
Avoid clipping on replay gained files reduce volume of the file if clipping is likely to occur 
-----------------------------------------------------------------------------------------------
[website templates]("http://pepdeal.com/")

---


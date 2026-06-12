---
title: "trouble with vlc streaming audio"
date: 2010-08-14
forum: Multimedia Software
---

### Post by cnbiz850 on 2010-08-14
I tried to set up on a server computer to send an audio stream and on a client computer to receive the stream, but have no luck.

Basically, what I did was this:

On the server:

1) on VLC, select Media->Streaming, then add an audio file, then click Stream;
2) then in the popup window, click Destination, then choose MMS and click on Add, then in the Path field, I put in "10.0.0.3/stream" (10.0.0.3 is the address of the server), and kept the default port to be 8080.
3) on transcoding, I select "Audio - MP3", then click on Stream.

On the client, with VLC, basiclly choose Open Network Stream, select MMS, put in Path as "10.0.0.3:8080/stream".

It seems the client is trying to connect to the server for like 30 seconds or so, then popup a message saying failed.

I also tried mplayer and audacious as the client, and also no luck.

Anyone please tell me what is wrong.

---

### Post by cnbiz850 on 2010-08-14
Well, tried a few different ways and the following setting works:

> 
On the server:
1) on VLC, select Media->Streaming, then add an audio file, then click Stream;
2) then in the popup window, click Destination, then choose **HTTP** and click on Add, then in the Path field, I put in "10.0.0.3" _(no "/stream")_ (10.0.0.3 is the address of the server), and kept the default port to be 8080.
3) on transcoding, I select "Audio - MP3", then click on Stream.

On the client, with VLC, basiclly choose Open Network Stream, select **HTTP**, put in Path as "10.0.0.3:8080" _(no "/stream")_.


With the "/stream", it does not work.

The MMS works also, but the connection takes very long - for the two computers on my LAN, it takes about 2 minutes to establish a connection (Why?!?!?)  Once the connection is on, the initial buffering and the subsequent playing are smooth.

mplayer on the client side appears to open the mms faster - about 10 seconds including buffering, but after the connection, it pops up a message saying "Can't resolve name for AF_INET6:10.0.0.3".  Anyone know what is happenning?  The music keeps playing, though.

Audacious2 on the client side crashes when asked to open "mms://10.0.0.3:8080"

That is what I know at the moment.  I appreciate very much anyone's sharing the experiences.

---

### Post by cnbiz850 on 2010-08-16
Also tried to receive the mms stream from my media player (based on "Linux Venus 2.6.12.6-VENUS #3 Sat Apr 24 10:07:50 CST 2010 mips unknown").  Basically time out during connection.

Anyone can comment on how to best stream mms audio from Ubuntu machines?  I really would like my media player to receive it and it only receives mms (not http etc) streams.

---

### Post by charcaroth on 2010-08-18
Not to be obtuse, but does it have to stream the file?  I use VLC or Boxee ([www.boxee.tv](www.boxee.tv)) to play music and video files directly from my NAS across my home network on an older PC (only nominally an HTPC with cobbled-together hardware: AMD 2000+ proc, 2gb PC3200 RAM, gigabit ethernet card, Siig Soundwave 7.1 audio card, Nvidia GeForce 6800 graphics card) connected to my receiver and HDTV setup and I never have the slightest stutter.  Granted, it's a wired gigabit connection, but I've pretty much given up on the idea of real streaming (especially outside my internal network) without a hardware solution for the time being (e.g. Slingbox, Hava, etc.) because I can never seem to find enough documentation to set it up on Ubuntu.  Hopefully there will be more folks interested in this use for Ubuntu soon that frequent the forums.  To me, an Ubuntu box is SO much more flexible than a dedicated hardware device, and isn't limited by annoying DRM issues or limitations on container formats.  I wish I could be of more help.

---

### Post by lidex on 2010-08-19
It may help you to get pulseaudio preferences involved.
To run:
Alt + F2 run dialog
```
paprefs
```
If not installed:
```
sudo apt-get install paprefs
```

---

### Post by cnbiz850 on 2010-08-21
> **charcaroth said:**
> Not to be obtuse, but does it have to stream the file?  
The media server (a nice little hardware with a simple Linux system) that is connected to my hifi stereo actually can access the music files on the Ubuntu server via samba and play the music that way.  But the thing I don't quite like is that it doesn't have a playlist feature.  It only plays everything one-by-one in a directory and when finished with the directory, I have to go change manually to play something else.  The reason I was thinking to stream from my Ubuntu server is that I want to use the nice playlist features of Ubuntu's media applications to play out to the media player.  Also, the media server only support mms (no http) streams.

> I use VLC or Boxee ([www.boxee.tv](www.boxee.tv)) to play music and video files directly from my NAS across my home network on an older PC (only nominally an HTPC with cobbled-together hardware: AMD 2000+ proc, 2gb PC3200 RAM, gigabit ethernet card, Siig Soundwave 7.1 audio card, Nvidia GeForce 6800 graphics card) connected to my receiver and HDTV setup and I never have the slightest stutter.  Granted, it's a wired gigabit connection, but I've pretty much given up on the idea of real streaming (especially outside my internal network) without a hardware solution for the time being (e.g. Slingbox, Hava, etc.) because I can never seem to find enough documentation to set it up on Ubuntu.  Hopefully there will be more folks interested in this use for Ubuntu soon that frequent the forums.  To me, an Ubuntu box is SO much more flexible than a dedicated hardware device, and isn't limited by annoying DRM issues or limitations on container formats.  I wish I could be of more help.

Can you be more specific how you play the music on the server and how to receive it on the client?  Do you use PauseAudio as the other reply mentioned?

I have tried to use my old Ubuntu laptop (the server mentioned above) to connect to my stereo directly through a USB sound card.  One thing is that the sound is not very satisfactory - particularly having a low noise.  See my other [thread]("http://ubuntuforums.org/showthread.php?t=1533563"), which also says why I wanted to use this little nice media player.

> It may help you to get pulseaudio preferences involved.
To run:
Alt + F2 run dialog
Code:

paprefs



Thanks for the suggestion.  I still try to understand what it can do to help my situation.  Will pauseaudio work if the client does not support pauseaudio (maybe a dumb question)?

---

### Post by charcaroth on 2010-08-23
Sure.  My operation of the home theatre PC (HTPC) running Ubuntu (10.04LTS at the moment but was upgraded from 9.10) is fairly straightforward and simple.  I've got a NAS with some media files connected to a gigabit switch, which is connected to the router (an Asus RT-N16 running Tomato firmware) which is in turn connected to a cable modem. On the other end, I've got my HDTV and HTPC connected to my receiver, an old Yamaha, which has speakers connected for the living room.  I've connected an HDMI cable from the Nvidia 6800GS card (using a DVI-HDMI adapter) to the HDTV (a Sony Bravia) and all the video pipes directly to this input.  For reference, I make sure the tv is on the correct HDMI input by the time the GRUB boot loader appears or I'll have problems with the video appearing. 

The HTPC has a Siig Soundwave 7.1 card that I got last week to replace the onboard sound in hopes of adding DTS sound to the setup (and of course NOW I've discovered my receiver doesn't support HD-DTS sound, just DTS).  Previously, I had been using the analog 1/8" jack to pipe the audio directly to an analog input on the receiver using a Y cable that ends in a red and white RCA connector.  Now since I've added the Siig sound card, I'm using a digital cable to connect to another input on the receiver (though I'm not getting any sound at all on the digital connection) but the analog cable puts out 5.1 to the receiver just fine.  That's actually a separate issue I wouldn't mind some help on myself since I've gone through the gamut of sound selections under the pull-down menu for settings (using the ALSA driver) at SYSTEM-->PREFERENCES-->SOUND-->HARDWARE but none of the options produce digital sound at all through my receiver.  I'm beginning to wonder if that port is bad on the card...

In any case, I have my NAS device (a QNAP TS-239) with a dedicated IP on the network and I browse the shared directory (Samba) using VLC then play ripped video and audio files of my DVDs and CDs through the HTPC and only within my home network.  Alternately, I'll use Boxee and its interface (which automatically scans and keeps tabs on changes to files on my NAS) to pull up Hulu video, Pandora, MLB broadcasts, or audio and video from my NAS.  Both play through the speakers hooked to my receiver.  The only non-standard part of this is the "remote control" that I use for the system, a Logitech DiNovo mini which connects to a bluetooth USB receiver that has both a miniature keyboard (1/3 netbook key sized) and a mouse onboard.  (This keyboard/mouse device has PS3 as well as PC support so the D-pad acts as either a touch pad mouse or a true D-pad that navigates through Boxee/PS3 menus with up/down/left/right movement and really makes a difference in feeling as though I'm using a set-top box and not using a wireless mouse to navigate onscreen.  There's also an Android remote control for Boxee that I've used occasionally on my phone to navigate within Boxee.)  I don't stream using any software in Ubuntu as I'd mentioned; I could probably set up gnump3d on a server but I can't run it on my NAS where the media is stored.  The NAS has Twonkyvision (which is DLNA compatible), but I haven't quite put together how to connect VLC (or Amarok or whatever) on the HTPC and I don't know that it's a superior method of listening to music over what I've got, especially since Boxee is free.  

I have a Slingbox that I've had for many years that I use to stream video outside my home network from my DVR to my netbook (and only the XP side, not the Ubuntu load) but since there are no Linux drivers it's worthless to connect to the HTPC.  I have a friend with a Hava player, which does have Linux (as well as Windows) support, in the form of a client software player to receive the stream. Both streaming boxes, though, depend on either component or composite connections for the audio/video source and infrared pass-throughs that send the signals from your remote to an IR extender that's stuck to the front of the box being controlled and physically hands off the signal.  It's a bit of a kluge, but I'm a hardware guy so I tend to stick with that sort of solution.  

I hope this helps to clarify how my solution works, at least how it works for me.

---

### Post by cnbiz850 on 2010-08-25
Wow!  Thanks very much for the detailed intro.  That is a very remarkable total system.  Guess your HTPC is a traditional desktop, right?  Because then you have the benefits of getting high quality video and audio cards.  Is there a way for a laptop to serve as your HTPC by any chance?  The laptop doesn't have HDMI.  For sound, I tried a good USB sound card and the sound quality was great except for the AC noise, which is not acceptable.  I connected through the RCA connectors to the hifi amplifier (which doesn't have optical input).

My current setup (using a dedicated media player) satisfies me in terms of video and audio quality.  Too bad the playlist feature is very rudimentary.  There might be a way to install a more sophisticated player software on the media player, but I am not that familiar with that distro of Linux (called Venus or BusyBox?) to know how to install one.  So maybe a better choice for that part is to find a way for me to control the thing on my Ubuntu laptop server.

---

### Post by charcaroth on 2010-08-26
I'd originally tried to use an old laptop as the media center/HTPC (an old Compaq with about a 1.8 ghz AMD Turion and 512 mb PC2100 RAM that was abandoned by a family friend) but I ran into the same problems you'd described.  Sound options were very limited to just the headphone out jack; I've never trusted USB sound to be reliable so didn't try any external audio cards.  I guess some hiss is expected with lower end analog equipment like I've been using.  Power management was a continuous problem as the lousy Compaq motherboard chipset driver sometimes wouldn't let the laptop come back out of suspend mode to wake it up (this also happened regularly in Windows XP).  The onboard video card couldn't support a video resolution high enough for the HDTV through the VGA port--the video ghosted enough that I abandoned the idea quickly.  I thought about using a VGA-DVI adapter and then a DVI-HDMI adapter for video input, but the video card ghosting was even worse.  I liked the idea of using a laptop as an HTPC due to its being low power, which is why I'm using a NAS instead of a dedicated server for my audio and video files, but it just had too many limitations.  Maybe a newer laptop with HDMI onboard might work okay, but from what I'd read, I didn't want to go below a 2 ghz processor at the time (a P4/Athlon chip 2ghz) or it would be too slow to run standard Ubuntu 9.04 on the network (for playing video/audio from the NAS, stream from Hulu through Boxee, deal with the bluetooth mouse/keyboard, etc.) so a laptop, especially a netbook with an Atom processor, wasn't going to be a viable option.  I also didn't want to buy something new, just add as few parts as possible to whatever junk I had lying around the workshop.  I ended up re-purposing an old AMD socket 939 processor, slapping in 2 gb of RAM and just lying it on its side in the entertainment center in an old beige desktop case.  Yeah, it's not pretty, and I have to push the big power button on the front to power it up, but the opaque doors close and the cabinet is big enough that I haven't had any heat problems.  

That being said, I also have an EeeTop PC (model ET1602), which is an all-in-one PC that I got for my wife to check email, browse recipes, and check Facebook in the kitchen.  She loves it and uses it often.  It came with an 1.6 ghz Atom processor, 512 mb RAM, 802.11n wireless, and Windows XP.  I dual-loaded Ubuntu netbook edition on it to see how it would run and to see if she could use Boxee to act as a jukebox for mp3s in the kitchen.  It works pretty well for pulling music from the NAS through VLC or Boxee and she sometimes uses the Android remote for Boxee from her phone to change to a new set of files or to navigate to the Pandora app that Boxee serves up when she's not near the mouse and keyboard.  Touchscreen support does not work on this machine in Ubuntu.  The wireless stutters with video, as expected, but with the lower overhead of the Ubuntu 10.04 netbook edition it works pretty well for everything else.  You might try switching to the netbook edition of Ubuntu if you have problems with the server machine slowing down when streaming files.  I'd wager that one of the new all-in-one HP touchscreen PCs would be an awesome solution for an Ubuntu media streamer client (with a real desktop processor, HDMI video/audio out, and plenty of RAM) but I'm not spending that kind of cash on one, especially given what I've seen of Ubuntu's touchscreen support on the EeeTop.  

I'd looked at BusyBox before I decided to abandon the idea of a server in favor of a NAS, but I never got very far so I can't help much in that direction.  It looked needlessly complex for my limited skillset which helped me to forego streaming in lieu of simply playing from a remote source.  Boxee is based on XBMC, aka Xbox Media Center.  I'd played around with XMBC, too, before discovering Boxee, and it even works from a bootable CD to demonstrate to others.  You might find some usefulness in some derivatives of that project.  I've messed around with MythTV and with Linux MCE (media center edition) but never been very satisfied configuring them to work as a digital jukebox since they're more attuned to work as a TV capturing live video from cable/satellite/digital broadcast signals as well being as an audio/video player.  Of course, I'd been trying to use an old Plextor ConvertX tuner that is supported but is rather old instead of a Silicon Dust or more modern equipment that got better reviews with those Linux derivatives.  

Good luck with the server/client streaming solution.  Maybe the introduction of Google TV and the Boxee Box this fall will outmode all our efforts anyhow.

---

### Post by cnbiz850 on 2010-08-26
Many thanks for the kind intro of experience.  I experienced similarly on a few things: the VGA to HDTV (ghosted video), and video stuttering via wireless.  I haven't tried NAS.  What would you say about the advantages/disadvantages of it over disks USB'ed to a server, like perhaps in my way described in more detail below?

Moved to [a new thread]("http://ubuntuforums.org/showthread.php?p=9770919#post9770919")

---


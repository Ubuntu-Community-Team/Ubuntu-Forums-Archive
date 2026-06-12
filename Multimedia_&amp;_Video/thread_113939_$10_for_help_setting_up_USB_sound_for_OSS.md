---
title: "$10 for help setting up USB sound for OSS"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by joeljkp on 2006-01-07
I'm willing to send $10 to anyone who can sit down with me (on IM or something) and help me set up my sound system.

I have a laptop with built-in sound, plus a USB soundcard. The built-in sound is shot, so I need to use the USB to hear anything. The ALSA portion is set up correctly (I believe), but anything that uses OSS either doesn't play at all, or plays very noisily.

Thanks in advance. PM me if you think you can help.

---

### Post by stratotak on 2006-01-07
maybe its the trashed laptops  built in sound causing some conflicts??have you tried to  unload the modules for your sound card and seeif helps?as its a laptop im assuming you cant disable built in sound in bios?if its the built in sound causing problem then i think you should be able to add them to hot pluds black list ..???also have you installed alsa-oss??

---

### Post by mpvano on 2006-01-07
What kind of laptop & how fast?
What kind of USB adapter?
What software are you trying to use?
What ports are you telling the software to use?
Is the USB adapter set as default audio card or not?
Is esound daemeon enabled in system:preferences:sound?
Is esd process loaded when you have trouble?

If you provide this info, some of us may be able to help you for free !

Mario

---

### Post by joeljkp on 2006-01-08
This is a Dell Inspiron 5150 with a P4 3.06 GHz processor and USB 2.0. The built-in sound is a SigmaTel STAC9750 that died over the course of a couple days last month.

The USB card is a [Turtle Beach Audio Advantage Micro](http://turtlebeach.com/site/products/audioadv/micro/), with a single headphone-out jack.

The OSS software I would most like to use is RealPlayer 10, or the Rhapsody.com plugin. I also play an OSS game or two.

The 9750 is detected as the first card, and is assigned to /dev/dsp by the ALSA OSS emulation. The USB is assigned /dev/dsp1.

I've set the USB card to the default in the GNOME settings panel, but this only seems to apply for ALSA apps, as all it does is add a line to my .asoundrc.

When playing an mp3 with Totem, the sound comes through perfect and clear. When playing with RealPlayer, nothing comes through at all, with esd running and without.

---

### Post by mpvano on 2006-01-08
Sounds like you have most of it under control.

The real player, however, has no settings for sound card and doesn't read the alsa default card setting. In some versions Its sound card choice comes from an environment variable called $AUDIO.

On an earlier notebook where I had a similar problem I used to launch it from a menu with the following line (the line requires that a shell execute it, so I don't know if it will work with gnome menus - you may need to wrap it in a shell command like I used to have to do).

 exec sh -c 'export AUDIO=/dev/dsp1; exec /usr/bin/realplay'

hope something like this works for you - It definitely was the answer for older versions, but there have been a great many builds of the real player since then....

Mario

---

### Post by joeljkp on 2006-01-08
[QUOTE=mpvano]The real player, however, has no settings for sound card and doesn't read the alsa default card setting. In some versions Its sound card choice comes from an environment variable called $AUDIO.[/QUOTE]

Wow, thanks a lot! That did the trick beautifully.

But that brings me to my second problem:

When an app successfully uses the right sound card with OSS, the sound quality is very poor, with clicking and stuff in the sound. This doesn't happen with ALSA apps. The Rhapsody.com plugin (OSS), even plays the audio in slow motion!

My initial thoughts were that it's trying to use the wrong sample rate for the card, or that it's not able to do any sample-rate conversion whatsoever, but I have no idea how to fix that.

---

### Post by joeljkp on 2006-01-08
Fixed it (I think)! There's also a /dev/mixer device, with /dev/mixer1 as the USB counterpart. I tried setting MIXER=/dev/mixer1 for realplayer, and it's working fine!

mpvano, I'll gladly send you the $$, if you PM me and request it.

---

### Post by mpvano on 2006-01-08
That can be a problem with USB sound cards. Unfortunately, they work much better for recording than for playback because the incoming audio is usually configured to use the only available "guaranteed delivery" service in USB, leaving the playback to go to less reliable channels.

You can help the situation by minimizing what else the machine is doing while outputting audio, and by avoiding the use of 24 bit audio. If the application has a configuration option for the "buffer size" or "output buffer size" (they may not be the same thing) try increasing it -- A LOT --- a megabyte or two may not be too much if the delay it introduces is not a problem.

Another big problem seems to be that many sound cards only support a single playback rate and frormat and rely on the driver and your application program to convert the samples as needed. They do this with varying degrees of success!

In fact, some programs can't handle this at all. I've found this to be a problem with several MP3 playing programs - but those programs usually have trouble playing MP3 files with unusual bit rates as well. The symptom is what you've seen - they skip regularly or they play back at the wrong speed.

In many cases, you can work around  these problems by experimenting with different output drivers. For example, some players work best with the old OSS drivers because the OSS emulation layer in ALSA sound covers up for many of these sample rate problems. But others work much better with the native OSS drivers if properly configured.

In extreme cases, you may need to switch applications or drivers - for example I find the "helix" open source sound player much worse than the closed source "real player 10" for skips on output. The popular mpg321 player (often named mpg123 in many distributions) doesn't work nearly as well as the non-gnu licensed mpg123 player it emulates. Many players like videolan and xmms have a choice of output drivers but you may need to download and install some of the less popular drivers.

In fact, if you can find the documentation (look inside the alsa source package) it describes how you can fine tune the OSS emulation internal settings to solve a lot of problems.

Some sound players take command line options to change drivers, others handle it from preferences dialogs. You may need to experiment - some authors do a better job with their OSS output, others really do a good job with their ALSA output.

Another issue is that the ALSA devices exist in several different layers for each device. If you select the devices named "hw:n" where n is the device number, you get the lowest level drivers most prone to skipping and sample rate problems, but best for low latency and professional use. This is rarely what you want for a player or other casual audio use.

Try switching to the devices with similar names prefixed with "plug" as in "plughw:0" or "plughw:1" - these go through an internal resampling and buffering plugin built into ALSA, and are probably the correct devices for most uses other than pro-audio applications that really know what they're doing.

I generally have had excellent results recording on machines 500mhz and up with the following devices I own: iMic, M-Audio Transit, SoundBlaster MP3, Edirol UA30, and also with a number or others I've occasionally borrowed for testing.

Nearly ALL of them however skip occasionally on playback when complicated windowing operations take place (like resizing a window or switching workspaces). Usually this isn't much of a problem for me since it seems to happen infrequently, but it's quite annoying when I'm previewing a recording I just made - I often have to backspace and replay sections to make sure the click was in the playback and not the recording.

If you're getting more than the occasional click on playback, however (usually when X-windows is very busy), you may need to experiment some more with the settings described above.

hope this was educational, but you'll have to do a lot of this on your own. If you're happy with this advice and really meant your original subject line, send your $10.00 to a tsunami or flood relief charity...

Mario

---

### Post by joeljkp on 2006-01-08
$10 sent to [World Emergency Relief](http://www.charitynavigator.org/index.cfm/bay/search.summary/orgid/4759.htm).

Thanks again for your help.

---


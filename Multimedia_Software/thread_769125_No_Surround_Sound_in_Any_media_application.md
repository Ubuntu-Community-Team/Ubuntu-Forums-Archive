---
title: "No Surround Sound in Any media application"
date: 2008-04-26
forum: Multimedia Software
---

### Post by ITAndrew on 2008-04-26
Hello,

My experience in getting 5.1 sound in ubuntu has been a rocky road here is my problem.

Just installed Hardy (keep in mind this problem also had occoured in gutsy as well) and works fine. Set all sound options in alsa mixer to

Jack mode: Independent
Channel Mode: 6ch
Turned up Surround, Center, and Master to full.

I run the speaker test "speaker-test -Dplug:surround51 -c6 -l1 -twav " and it works fine, get announcements from all channels loud and clear.

The problem is, when I want to play a 5.1 audio file (I have many that I use tested it windows and it plays true 5.1 audio) it only plays out of the two front channels. The applications that I have used and the settings used are:

VLC - Only has stereo option for all media and I am unable to find an option (other than Detect Dolby surround ON/OFF) and that always plays in 2ch stereo

Totem-gstreamer and Totem-xine and Gxine: In totem, I have tried to use the 5.1 option, still only 2 ch, also tried AC3 Passthrough and only plays on the front 2 channels.

The moral of the story is, using the speaker test I DO get all 6 channnels announced, but how the heck do you get an application to utilize 5.1. If anyone has any ideas or is stuck with the same problem let me know.

Thanks all!

---

### Post by ITAndrew on 2008-04-26
Also, I am sing ubuntu x64. Mobo is A8N-SLI Delux nforce 4 board, using onboard analog 5.1. Thanks

---

### Post by ITAndrew on 2008-07-29
bump, ongoing issue.

---

### Post by Sandern on 2008-11-11
Same issue here,

Ubuntu 8.10, the test thing using the prompt works fine but I I'm always getting just stereo thru any app in gnome.

All settings are put on ALSA.


Edit: already tried to patch it with this:

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

---

### Post by ITAndrew on 2008-11-12
I wanted to update this post since I do believe I have solved my problem. I can get true 5.1 surround sound output using the pulseaudio sound server. Documentation can be found:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

Also, a quick and dirty fix for just duplicated rear channel sound is >> Double click on the gnome-volume applet >> Select edit, then preferences >> Check Center, surround, and Duplicate Front >> Adjust volume levels for surround and ensure that the channel is unmuted >> Click on the advanced tab, select duplicate front.

You should now have duplicate sound coming from the front and rear channels, but probably not from the center.

Now, if only I could get pulseaudio to work on FreeBSD....

---


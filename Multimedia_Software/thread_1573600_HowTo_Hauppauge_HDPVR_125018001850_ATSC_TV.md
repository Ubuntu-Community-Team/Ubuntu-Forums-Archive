---
title: "HowTo: Hauppauge HDPVR 1250/1800/1850 ATSC TV"
date: 2010-09-13
forum: Multimedia Software
---

### Post by roop_s on 2010-09-13
I'm seeing a lot of misinformation on the internet about these cards being *unable* to work. They do work, at least for ATSC which will be a long term format. See the bottom for NTSC. Here is a complete guide for how to be able to at least watch TV:

Below you see the hardware that I have. The cx88 driver is built into 10.04:

```

lspci
03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f)

lshw -C multimedia
       description: Multimedia video controller
       product: Hauppauge Inc. HDPVR-1250 model 1196
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:19 memory:dfe00000-dfffffff

```

If your card is the same, this should work. If it's slightly different, it may still work.

Before you can watch anything you need to do a channel scan: 

sudo apt-get install w-scan mplayer
sudo w_scan -ft -c US -X >> /etc/mplayer/channels.conf

I found the above command [here]("http://ubuntuforums.org/showthread.php?t=1162641") and modified it for mplayer. Scanning takes a couple minutes. If you live in Ottawa, you may see an output like this in your channels.conf:

```

CKXTDT3:509000000:VSB_8:65:67:2
HDTV RADIO-CANADA OTTAWA:521000000:VSB_8:49:52:11
HDTV CBC OTTAWA:539000000:VSB_8:49:52:10
CRC:665000000:VSB_8:49:4100:1

```

Once the channel data is there, you can now watch TV:
mplayer dvb://
Keyboard H and K letters change channels.

If you just want NTSC analog, this could work but I haven't tested it.
mplayer tv:// -tv driver=v4l2:chanlist=us-cable:alsa:adevice=hw.0,1:amode=1:audiorate=48000:forceaudio:volume=10:immediatemode=0:norm=NTSC-M

---

### Post by roop_s on 2010-09-13
if you prefer to use VLC:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB -o zap | tee channels.conf

vlc channels.conf

---

### Post by hayhursm on 2010-11-05
> **roop_s said:**
> if you prefer to use VLC:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB -o zap | tee channels.conf

vlc channels.conf

Hello and thank you for this post!  I was having a difficult time finding anything in the Wiki's regarding this card.  I read here and there that the other analog inputs do not work (S-Video, Composite, etc...) were you able to get these to work?  I just want to put some old family VHS and 8MM video tapes on my PC before they deteriorate.

---

### Post by roop_s on 2010-11-06
> **hayhursm said:**
> Hello and thank you for this post!  I was having a difficult time finding anything in the Wiki's regarding this card.  I read here and there that the other analog inputs do not work (S-Video, Composite, etc...) were you able to get these to work?  I just want to put some old family VHS and 8MM video tapes on my PC before they deteriorate.

Sorry - I don't even have anything to test the analog inputs with, I don't own a dvd player and certainly not a vcr.

you can try this:

ls /dev/vid*
I see video0 and video1

if i go in vlc - I can go to open a capture device -> specify video as /dev/video0. When I do this I get a green screen in VLC, I imagine this may be a valid input with nothing connected. give it a try, I just don't know which connector this could be and have nothing to test it with.

specifying /dev/video1 causes vlc to crash.

---

### Post by hayhursm on 2010-11-07
> **roop_s said:**
> Sorry - I don't even have anything to test the analog inputs with, I don't own a dvd player and certainly not a vcr.

you can try this:

ls /dev/vid*
I see video0 and video1

if i go in vlc - I can go to open a capture device -> specify video as /dev/video0. When I do this I get a green screen in VLC, I imagine this may be a valid input with nothing connected. give it a try, I just don't know which connector this could be and have nothing to test it with.

specifying /dev/video1 causes vlc to crash.

Is this what you did: Open VLC> Media> Open Capture Device> Select PVR (Under Capture Mode> Advance Options> Device= /dev/video0 ?  Nothing happens when I do that (not even a green screen).  Also, how did you install the drivers for the card?  I used this: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) from the LinuxTV Wiki...is that the correct way?

---

### Post by hayhursm on 2010-11-10
> **hayhursm said:**
> Is this what you did: Open VLC> Media> Open Capture Device> Select PVR (Under Capture Mode> Advance Options> Device= /dev/video0 ?  Nothing happens when I do that (not even a green screen).  Also, how did you install the drivers for the card?  I used this: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) from the LinuxTV Wiki...is that the correct way?

Bump

---

### Post by petesbbq on 2011-06-16
Unable to configure this card.  After days of trying I upgraded to Ubuntu 11.04 to see what it would give... sees the card only called it something different.  Still says it is unsure of the card and lists the choices.  Compiled new kernel 2.6.39.1 to no avail.  Unable to scan channels because /dev/ entry not created.  lspci and dmsg attached. HELP!

---

### Post by poe503 on 2011-06-16
You didn't say what your card is supposed to be.

Check out my tutorial: [*http://ubuntuforums.org/showthread.php?t=1648472*]("http://ubuntuforums.org/showthread.php?t=1648472")

Please note a subsequent comment on that thread which states that newer kernels need to use GIT not HG.

I can't say for sure if this is so.

---

### Post by maxbur on 2011-09-30
Thanks to roop_s for the concise guide to viewing ATSC TV in mplayer, and a small correction:

most users will want to write the channels.conf file to ~/.mplayer/channels.conf (i.e. in their home directory) NOT /etc/mplayer/channels.conf.

The corrected terminal command for North American users: ```
w_scan -ft -c US -X >> channels.conf

```
See the "Digital TV (DVB input module)" section of the online [mplayer manual]("http://www.mplayerhq.hu/DOCS/HTML/en/mpeg_decoders.html") for some tips on overcoming choppy video/audio.

---

### Post by jcoles on 2011-10-29
Hi roop_s,

I live in Ottawa too.

Your instructions have given me the best results so far. 
I have both a HVR-1250 and a HVR-950Q (USB). I've never been able to use Ubuntu for HDTV, but I'm trying again with v11.10.

With the HVR-950Q, after launching mplayer, it takes a full minute to get a blocky blurry smeary still picture, 15 seconds to change channels. 

VLC looked like it might work as it has an Open Capture Card function. But I couldn't find device name it would accept. I tried your trick of "vlc channels.conf" and got a clear and recognizable still frame of video on some channels. There were plenty of errors, such as:
> libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 10) for PID 0
I suspect the biggest problem is Ubuntu's poor USB performance. It cannot sustain data transfer at USB 2.0 rates. If you  transfer a large amount of data to a USB hard drive, the transfer rate gets slower and slower. 

I tried your suggestions with the HVR-1250 card in my HP xw4300. Using Me-TV, the video hesitates and stalls every few seconds. But VLC works really well. Thanks for the tip!

---

### Post by roop_s on 2012-01-07
thanks for the feedback, i'm glad I could help. I wanted to share this tidbit as an extension of this card and vlc. Using Crontab and cvlc (commannd line vlc, it has not visual output) you can time and record stuff off of ATSC. Here's an example of a crontab -l output:

00 10 * * 1-5 cvlc /home/roop/cbc.conf --sout=file/ts:/home/roop/Downloads/Super/`date -I`.ts & sleep 900; kill $!

cbc.conf is a channels.conf file with all channels removed except cbc:
OTTAWA  CBOT-DT:539028615:8VSB:49:52:3
cvlc tunes to this channel and dumps the uncompressed 1080p file to a ts formatted file with today's date. After 900 seconds, cvlc will gracefully close with the sleep 900 followed by kill $! command.

later on at night, i run another scrip to compress the typical 2GB uncompressed 1080p file:

00 02 * * 2-6 bash /usr/local/bin/super_enc.sh

the script must be in that directory and here's what the script looks like. I am downscaling to 720p but ffmpeg is a huge subject and you can do absolutely anything with that. here's an example of what i'm doing. the script will look for all .ts files and compress all of them in a directory, one after the other. my AMD phenom ii X4 3.4ghz takes about 5-10 minutes for this task:

#!/bin/bash
for file in /home/roop/Downloads/Super/*.ts
do
/usr/local/bin/ffmpeg -i "$file" -s 1280:720 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre medium -b 2500k -bufsize 3500k -maxrate 3000k -threads 0 ${file%.*}.mkv
rm $file
done

---

### Post by dandow on 2013-01-28
I am a newbie to Ubuntu/Mythbuntu, but I was able to get a Hauppauge 1850 to work for the system I put together with a little help from a friend.  I have a AMD II X3 450 on an AsRock 880 MBoard with 4GB ram.  So far the only thing I do not have working is the audio, and I have a soundcard coming.  MythTV setup did not identify the 1850 specifically as a Hauppauge card, which is what confused me for a while, but it works!

---


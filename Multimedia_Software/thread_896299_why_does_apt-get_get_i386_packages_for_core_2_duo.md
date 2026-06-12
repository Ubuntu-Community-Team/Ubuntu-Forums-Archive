---
title: "why does apt-get get i386 packages for core 2 duo"
date: 2008-08-21
forum: Multimedia Software
---

### Post by cdoss on 2008-08-21
I have a thinkpad t61 with intel's core 2 duo processor.  It is 64bit; as far as i can tell, the packages i install should be labelled 'amd64' not 'i386' since the IA64 instruction set is ~= the amd64 one (right? i am not certain of this).  I'm confused because the packages that apt-get installs are all the i386 variants and when i download the amd64 ones i get install messages saying that i have the wrong architecture.  

I post this in multimedia because the packages i'm dealing with in particular are all video related, i.e. libdvdcss2, etc.  I'm having trouble with playing back DVDs which seems to somehow be related to encryption even though libdvdcss2&libread3&libdvdnav4 are definitely installed, so I wondered if this might be the problem.

I am running 8.04 ubuntu, hardy.  



Thanks for your help,
-newbie

---

### Post by MindFlayer on 2008-08-21
Maybe you didn't install the 64-bit version of Ubuntu? :) Type "uname -a" in terminal and see if you've got x86_64 in the output.

---

### Post by cdoss on 2008-08-21
Thanks:

>~$ uname -a
Linux cdoss-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

That's the output; i presumed i686 means I've got 64 bit ubuntu?

---

### Post by MindFlayer on 2008-08-21
> **cdoss said:**
> Thanks:

>~$ uname -a
Linux cdoss-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

That's the output; i presumed i686 means I've got 64 bit ubuntu?

Nope, I'm afraid that's still 32 bit. Look [here]("http://www.ubuntu.com/getubuntu/download") for the 64 bit version.

---

### Post by cdoss on 2008-08-21
Ahh.  Ooops.  Thank you very much.  But running 32 bit ubuntu on a 64 bit architecture shouldn't actually cause any bugs, should it?  As in, the decoding of dvds should still be fine, VLC should still be able to stream video from the internet, etc?   I.e. is it worth the trouble to do a reinstall?  (I did install pretty recently...).

---

### Post by MindFlayer on 2008-08-21
> **cdoss said:**
> Ahh.  Ooops.  Thank you very much.  But running 32 bit ubuntu on a 64 bit architecture shouldn't actually cause any bugs, should it?  As in, the decoding of dvds should still be fine, VLC should still be able to stream video from the internet, etc?   I.e. is it worth the trouble to do a reinstall?  (I did install pretty recently...).

No problem at all (in fact, I'd say 64-bit Ubuntu still has some quirks here and there). Basically, you should be fine as long as you don't want to use more than 4GB of RAM. :)

As for your original problem, which program are you trying to use for DVD playback? I for myself find vlc to be the easiest to get working.

edit: If you already were using vlc, did you also install all the necessary codecs, i.e. ubuntu-restricted-extras package?

---

### Post by cdoss on 2008-08-21
I've got VLC, totem, and xine&gxine all installed right now.  I have ubuntu-restricted-extras installed.  Some DVDs play fine.
For other DVDs, On totem and VLC when I try to play them, the DVDs open, but playback is horrendous in that the image is distorted and blocky.

When I play in gxine, it shows the "the views expressed here are not those of 20th century fox ..." and the big red "ATTENTION ..." screen, but then gives "encrypted media stream detected; media stream scrambled/encrypted" error.  As i said above, i've installed all the packages I know of.  I also spent a long time realizing I needed to set my region; I used regionset to set my region to 1.  This allowed me to play some dvds (previously i could play none), but not all.  

Also, i recently tried sudo gxine; it actually worked, although video output was totally whitewashed.  Why would root privileges help?


I tried to sudo vlc; it didn't help, playback was as messed up as ever.  If i open disc /dev/dvd, with or without title, i get 
"Unable to open 'dvd:///dev/dvd/'".  I have to use /media/cdrom0, which is linked to VIDEO_TS.

If i sudo totem, I can open and start to play the dvd, but I only get spanish audio.

I ran gxine -vvv and opened DVD; i think the following may be the problem (can give the rest if needed).  This is WITHOUT sudo. 


libdvdcss error: no key but found encrypted block
libdvdcss error: no key but found encrypted block
demux_mpeg_block: warning: PES header indicates that this stream may be encrypted (encryption mode 1)
video discontinuity #6, type is 2, disc_off 16642
waiting for audio discontinuity #6
audio_decoder: error, unknown buffer type: 02000000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: suggested switching to stream_id ffffffff
audio discontinuity #6, type is 2, disc_off 16642
waiting for in_discontinuity update #6
vpts adjusted with prebuffer to 2441761
input_cache: read calls: 705, main input read calls: 705
input_cache: seek_calls: 0, main input seek calls: 0
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'image'
xine: found demuxer plugin: image demux plugin
video_out_xcbxv: VO_PROP_INTERLACED(0)
load_plugins: plugin image will be used for video streamtype 3d.
video_out_xcbxv: VO_PROP_INTERLACED(0)
xine_play
play_internal ...done


I presumed the libdvdcss error is what the problem is.  


I will gladly give output if it will help.  I guess my questions are: why do i need sudo to play; can i configure it to play without sudo; and why won't the other players function?


Thank you very much for any help.

---

### Post by Kyle1981 on 2008-08-21
you can install 32bit software into 64bit system, but can't install 64bit software into 32bit system

and now, they are not different for you. because I think you will not install more than 4GB memory in your notebook.

---


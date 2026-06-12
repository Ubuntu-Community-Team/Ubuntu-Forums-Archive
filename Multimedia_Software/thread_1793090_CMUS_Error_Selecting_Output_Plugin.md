---
title: "CMUS Error Selecting Output Plugin"
date: 2011-06-29
forum: Multimedia Software
---

### Post by laeuferman on 2011-06-29
Hi. I've had CMUS installed for a while, and I haven't had any problems until today.  After I initiate it, I'm given the error:
```
Error: selecting output plugin '': no such plugin
```

After some searching, I tried the "set output_plugin=" command with several arguments, but each time it tells me the same original error, only with 'oss' or 'alsa' instead of ''.  

I also tried "cmus --plugins," and the only output plugin listed oss under output plugins.  How do I configure CMUS so that it works?  (Sorry, I don't really know how else to word the question)

---

### Post by VolatileMember on 2011-07-10
Hello!

do you have installed the latest version of cmus (2.4.1)? It should select the default output plugin far better than the old versions (2.3.x). You can install it using this ppa:
```
sudo add-apt-repository ppa:jmuc/cmus
sudo apt-get update
sudo apt-get install cmus cmus-plugin-ffmpeg
```To see valid output_plugin options, try: ```
cmus --plugins
``` (under "Output Plugins:"). The best choice for a modern Ubuntu system is "pulse".

Does this solve your problem?

(I posted the same reply to the forum post [http://ubuntuforums.org/showthread.php?t=1780208](http://ubuntuforums.org/showthread.php?t=1780208))

---

### Post by laeuferman on 2011-07-10
Thanks for the reply, but the only output plugin listed is oss.

---

### Post by VolatileMember on 2011-07-10
What version of cmus are you using (cmus --version)? Are you using the cmus package from the PPA? What output does this command have:

```
ldd /usr/lib/cmus/op/pulse.so /usr/lib/cmus/op/alsa.so
```

?

---

### Post by laeuferman on 2011-07-10
Version 2.4.1

Output for "ldd /usr/lib/cmus/op/pulse.so /usr/lib/cmus/op/alsa.so":

```
/usr/lib/cmus/op/pulse.so:
	linux-gate.so.1 =>  (0xb784b000)
	libpulse.so.0 => /usr/lib/libpulse.so.0 (0xb77f0000)
	libc.so.6 => /lib/libc.so.6 (0xb7693000)
	libX11-xcb.so.1 => /usr/lib/libX11-xcb.so.1 (0xb768f000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7572000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7559000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7550000)
	libXtst.so.6 => /usr/lib/libXtst.so.6 (0xb754a000)
	libxcb-atom.so.1 => /usr/lib/libxcb-atom.so.1 (0xb7545000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb752a000)
	libpulsecommon-0.9.21.so => /usr/lib/libpulsecommon-0.9.21.so (0xb74e0000)
	librt.so.1 => /lib/librt.so.1 (0xb74d7000)
	libdl.so.2 => /lib/libdl.so.2 (0xb74d3000)
	libm.so.6 => /lib/libm.so.6 (0xb74ad000)
	libpthread.so.0 => /lib/libpthread.so.0 (0xb7493000)
	/lib/ld-linux.so.2 (0xb784c000)
	libuuid.so.1 => /lib/libuuid.so.1 (0xb748d000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb747d000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb746f000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb746b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7465000)
	libwrap.so.0 => /lib/libwrap.so.0 (0xb745b000)
	libsndfile.so.1 => /usr/lib/libsndfile.so.1 (0xb73f3000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0xb73b7000)
	libnsl.so.1 => /lib/libnsl.so.1 (0xb73a0000)
	libFLAC.so.8 => /usr/lib/libFLAC.so.8 (0xb7354000)
	libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb71db000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb71b3000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0xb71ac000)
/usr/lib/cmus/op/alsa.so:
	linux-gate.so.1 =>  (0xb76f2000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb7613000)
	libc.so.6 => /lib/libc.so.6 (0xb74b6000)
	libm.so.6 => /lib/libm.so.6 (0xb748f000)
	libdl.so.2 => /lib/libdl.so.2 (0xb748b000)
	libpthread.so.0 => /lib/libpthread.so.0 (0xb7471000)
	librt.so.1 => /lib/librt.so.1 (0xb7468000)
	/lib/ld-linux.so.2 (0xb76f3000)
```

---

### Post by VolatileMember on 2011-07-11
Ok, this is very strange! Do you think you can compile cmus yourself with debug enabled to see if there are any error messages?

A guide is here:
[http://cmus.sourceforge.net/#download](http://cmus.sourceforge.net/#download)

("Bleeding Edge"). If you need any help, please post!

---

### Post by laeuferman on 2011-07-11
Alright, will do.  But how do I enable debugging while compiling?

---

### Post by VolatileMember on 2011-07-11
Oh, sorry, you need to specify DEBUG=2 to ./configure!

```
./configure prefix=$HOME/cmus DEBUG=2 CONFIG_ALSA=y CONFIG_PULSE=y
```

You need to install all development packages before calling ./configure, e.g.:

```
sudo apt-get build-dep cmus cmus-plugin-ffmpeg
```

If everything works out, can you post the cmus-debug.txt file in your home directory (after starting the self-compiled version of cmus and exiting again)?

---

### Post by laeuferman on 2011-07-11
Alright, I've done all of that.  How do I view the error log? (Sorry for being such a newbie with this)

---

### Post by VolatileMember on 2011-07-11
No problem :-), this is a help forum. The debug file should appear in your home directory: ~/cmus-debug.txt

It only appears if you start the self-compiled version, e.g. by $HOME/cmus/bin/cmus  (depends what prefix you have specified when calling ./configure). You can post it here or send it to me as private message!

---

### Post by laeuferman on 2011-07-11
Ah, found it.
```

main: charset = 'UTF-8'
player_init: using real-time scheduling
player_init: setting priority to 99
player_set_op: setting op to ''
player_error: ERROR: 'selecting output plugin '': no such plugin'
TIMER: worker job:           0.000009
TIMER: worker job:           0.000006
init_curses: Number of supported colors: 8
init_curses: ts: 0 fs: 0
error_msg: Error: selecting output plugin '': no such plugin

```

---

### Post by VolatileMember on 2011-07-11
And ```
$HOME/cmus/bin/cmus --plugins 
``` still doesn't show anything other than "oss"? This is indeed a strange...

Does PulseAudio work on your system? Can you try this:
```
paplay some-file.wav
```

(paplay is from the pulseaudio-utils package)

---

### Post by laeuferman on 2011-07-11
I think I've figured out the problem, and it's a simple silly error. Running cmus from the cmus folder in my home directory with the --plugins command shows pulse, alsa, oss, and ao for output plugins.  Just running "cmus" yields only oss as the output plugin.  Sooo I guess I need to delete the original cmus and replace it with the one in my home directory? :P

---

### Post by VolatileMember on 2011-07-11
Great that it works with the self-compiled version of cmus! But the error is not "simple silly" :-(

This could indicate a serious problem with the Ubuntu package of cmus, especially since you are not the only person with this problem. What version of Ubuntu are you using (11.04, etc.)? Does is happen only with the PPA-version or with the official version (or both)?

I can't reproduce it with 11.04 (natty)...

---

### Post by laeuferman on 2011-07-11
I'm actually on Elementary OS Jupiter :o
CMUS used to work, so some update must've messed it up.  The important thing is that the bleeding edge cmus works, so future versions will be compatible.  Many thanks for all your help.

---

### Post by VolatileMember on 2011-07-12
Hmm, if you are not using Ubuntu but a derivate distribution this could be a reason... maybe the PulseAudio server is picky about the library version the program was compiled against...

---


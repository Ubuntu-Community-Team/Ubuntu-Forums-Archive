---
title: "Help saving a stream from the web... :)"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by fparri on 2007-02-20
Hello everybody,

Just a question, can you guys watch the following streamed video in this page using linux?

<[http://carnaval.globo.com/Carnaval2007/0,,CVC22-8052,00.html]("http://carnaval.globo.com/Carnaval2007/0,,CVC22-8052,00.html")>

I can watch it using windows and using a particular program, I can also save it.
With linux, instead, I can't watch it and also, I can't save the stream. I tried using mplayer -dumpstream etc... but I probably do something wrong.

PS. The vid is from Sao Paulo Carnival, it's the official hymn of my cousin's samba school this year. So be advised... ;)

---

### Post by jrib on 2007-02-20
> **fparri said:**
> Hello everybody,

Just a question, can you guys watch the following streamed video in this page using linux?

<[http://carnaval.globo.com/Carnaval2007/0,,CVC22-8052,00.html]("http://carnaval.globo.com/Carnaval2007/0,,CVC22-8052,00.html")>

I can watch it using windows and using a particular program, I can also save it.
With linux, instead, I can't watch it and also, I can't save the stream. I tried using mplayer -dumpstream etc... but I probably do something wrong.

PS. The vid is from Sao Paulo Carnival, it's the official hymn of my cousin's samba school this year. So be advised... ;)

Works here in my browser using mplayer plug-in.  It only worked after I installed w32codecs (I grabbed them from mplayer's site but they are also packaged at [http://wiki.ubuntu.com/SeveasPackages)](http://wiki.ubuntu.com/SeveasPackages)).  This worked to save the stream:

```

mplayer -dumpstream 'mms://windowsmedia.globo.com/_fechado/globocom/entretenimento/1/carnaval_2007/2007/01/18/EFWEBSP_T_622701_wmbl.wmv?url=0100003611443328256dEtDpi25%2FPqHq%2FQx2wVR5g%3D%3D&WMBitrate=200000&WMContentBitrate=200000'

```

I'm on feisty, but I'm pretty sure this should work on previous versions of mplayer too.  If it doesn't, paste the error output from ```
mplayer 'mms://windowsmedia.globo.com/_fechado/globocom/entretenimento/1/carnaval_2007/2007/01/18/EFWEBSP_T_622701_wmbl.wmv?url=0100003611443328256dEtDpi25%2FPqHq%2FQx2wVR5g%3D%3D&WMBitrate=200000&WMContentBitrate=200000'

```

---

### Post by fparri on 2007-02-20
Ahhh I understand, I'll try as soon as I get home tonight and let you know. Thank you meanwhile ;)

---

### Post by fparri on 2007-02-20
Uhm, it doesn't work...

Here's the log I get:

> mplayer 'mms://windowsmedia.globo.com/_fechado/globocom/entretenimento/1/carnaval_2007/2007/01/18/EFWEBSP_T_622701_wmbl.wmv?url=0100003611443328256dEtDpi25%2FPqHq%2FQx2wVR5g%3D%3D&WMBitrate=200000&WMContentBitrate=200000'MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:         Intel(R) Pentium(R) M processor 1.73GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing mms://windowsmedia.globo.com/_fechado/globocom/entretenimento/1/carnaval_2007/2007/01/18/EFWEBSP_T_622701_wmbl.wmv?url=0100003611443328256dEtDpi25%2FPqHq%2FQx2wVR5g%3D%3D&WMBitrate=200000&WMContentBitrate=200000.
STREAM_ASF, URL: mms://windowsmedia.globo.com/_fechado/globocom/entretenimento/1/carnaval_2007/2007/01/18/EFWEBSP_T_622701_wmbl.wmv?url=0100003611443328256dEtDpi25%2FPqHq%2FQx2wVR5g%3D%3D&WMBitrate=200000&WMContentBitrate=200000
Resolving windowsmedia.globo.com for AF_INET6...
Couldn't resolve name for AF_INET6: windowsmedia.globo.com
Resolving windowsmedia.globo.com for AF_INET...
Connecting to server windowsmedia.globo.com[201.7.180.132]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving windowsmedia.globo.com for AF_INET6...
Couldn't resolve name for AF_INET6: windowsmedia.globo.com
Resolving windowsmedia.globo.com for AF_INET...
Connecting to server windowsmedia.globo.com[201.7.180.132]: 80...
Resolving windowsmedia.globo.com for AF_INET6...
Couldn't resolve name for AF_INET6: windowsmedia.globo.com
Resolving windowsmedia.globo.com for AF_INET...
Connecting to server windowsmedia.globo.com[201.7.180.132]: 80...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   Ahhhh, stream_chunck size is too small: 4
Error while parsing chunk header
Cache fill: 14.93% (9783 bytes)   
ASF file format detected.
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [dshow] Win32/DirectShow decoders
Creating new registry
AUDIO: 8000 Hz, 1 ch, s16le, 4.9 kbit/3.85% (ratio: 616->16000)
Selected audio codec: [acelp] afm: dshow (ACELP.net Sipro Lab Audio Decoder)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/1 channels/2 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  11.2 (11.1) of 11.0 (11.0)  1.2% 0% 
alsa-uninit: pcm closed

Exiting... (End of file)

---

### Post by jrib on 2007-02-20
the url for the stream seems to change... I tried the command that worked for me before and noticed that it no longer worked.  However, I revisited the site and obtained the url again (right click -> copy location in mplayer-plugin) and used the correct new url and was able to stream fine with mplayer on the command line again.

So try obtaining the url using mplayer plugin, and then using that...

---


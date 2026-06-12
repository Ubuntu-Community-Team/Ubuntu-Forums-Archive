---
title: "MPlayer Cannot Stream Video"
date: 2009-02-25
forum: Multimedia Software
---

### Post by ProNux on 2009-02-25
Hi All,

I have installed MPlayer including the Firefox plugin but I cannot play LIVE Streaming using with Windows codecs.  I have installed the codecs as described here ([http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)), but I used MPlayer, not xine/totem.

The Firefox plugin can play RECORDED Video, but not LIVE.  Any ideas?

Thanks.

---

### Post by opscure on 2009-02-25
Did you install the binary codecs from mplayer's site?
[http://www.mplayerhq.hu/design7/dload.html#binary_codecs]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs")


Here's the list of the working codecs:
[http://www.mplayerhq.hu/DOCS/codecs-status.html]("http://www.mplayerhq.hu/DOCS/codecs-status.html")

---

### Post by ProNux on 2009-02-25
Yes I already installed the binary codecs, sorry, I forgot to mention.  I tried also installing the MPlayer-no GUI and it said something like I need a codec avisynth.dll, which I also installed.

Bro, is there any other media player to use in watching Windows (r) Media Live Streaming?

Thanks again.

---

### Post by opscure on 2009-02-25
Yes, you can try VLC or Totem.  You will need to download the binary codecs for windows based formats from their respective sites.  Ubuntu cannot put these codecs into the main repositories due to legal issues.  These are applications and the url of the streaming video would have to be opened through the gui interface as opposed to your browser (i believe).

You aren't talking about silverlight are you????  There is a linux based port of Sliverlight here: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by andrew.46 on 2009-02-25
Hi ProNux,

> **ProNux said:**
> I have installed MPlayer including the Firefox plugin but I cannot play LIVE Streaming using with Windows codecs.

Can you give an address of a stream that you are trying to play?

Andrew

---

### Post by jimmyhacker on 2009-02-25
open mplayer by console and check if it gives an error about LiRC

---

### Post by ProNux on 2009-02-25
Hi, sorry for the late reply as it was around 2:00 AM and I had to sleep.
Anyway, here is the url link of one of the Live streams.


[http://www.hayag.com/w/nasatv](http://www.hayag.com/w/nasatv)

There is an option for Windows Media and Silverlight.  So I choose Windows Media.

Here are the scenarios:

1.Using Mplayer and manually entering the URL link,

There is an error that it CANNOT RESOLVE the name AF_INET6:Hayag.com.
Has it something to do with it?

2.  Playing the stream direclty at Firefox with MPLayer plug-in

It can play "recorded videos", but cannot play most "LIVE" streams.
I can see it buffering but just stops at the end.

I tried other LIVE streams like the one below, NO VIDEO, But Sound is okay.

    [http://hayag.com/w/mytvko](http://hayag.com/w/mytvko)


Hope you can help me make it work.

---

### Post by ProNux on 2009-02-25
Here is the output after opening a url from mplayer using the console..

```
wong@wong-laptop:~$ mplayer http://www.hayag.com/w/nasatv
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://www.hayag.com/w/nasatv.
Resolving www.hayag.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.hayag.com
Resolving www.hayag.com for AF_INET...
Connecting to server www.hayag.com[216.240.133.138]: 80...
Cache size set to 320 KBytes
Cache fill: 19.02% (62338 bytes)   


Exiting... (End of file)
wong@wong-laptop:~$ 

```

If I use the Mplayer with the GUI (after uninstalling the mplayer-no gui), there is an error.

---

### Post by andrew.46 on 2009-02-26
Hi,

Sorry the stream does not work for me either....

Andrew

---

### Post by ProNux on 2009-02-26
> **andrew.46 said:**
> Hi,

Sorry the stream does not work for me either....

Andrew

Thanks.  At least there might be other reasons.  I'll gonna search other Live Streams to isolate the issue.

---

### Post by manoynmonic on 2009-06-19
Did you ever resolve the silverlight/hayag.com issue?  So far I have tried the FF mplayer plugin, moonlight and FF moonlight plugin - still no dice for my Xubuntu Jaunty install.

Edit: I also added the w32codec pack from the medibuntu repo, as well as the [Novell moonlight FF addon]("http://www.go-mono.com/moonlight").  Still nothing for the website in question.  :-?

---

### Post by manoynmonic on 2009-06-19
Ah ha.  The site requires silverlight 2.0.  I removed libmoon and all the 1.0 related repo stuff and tried [the preview version of moonlight 2.0]("http://go-mono.com/moonlight-preview/") - still not working right (crash).  Many thanks to the dev guys at #moonlight for getting me at least that far though.  Maybe just a little time 'til things move closer to a release version of 2.0.

---


---
title: "Real media streams in Xubuntu/gxine"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by febrile on 2007-06-08
Getting real media streams to play properly in gxine is an old problem: lots of posts and solutions that work for some & not for others, including me. I mainly want streamed video and audio from the BBC websites, including their 'listen again' radio feature. 

The problem:
I have Xubuntu feisty (gxine installed by default) and added libxine-extra-codecs and w32codecs. I use the MediaConnectivity firefox add-on rather than gxineplugin from the repos. With this setup, BBC video streams work fine, but audio streams never get past the buffering stage. Using the test files on [http://service.real.com/test/](http://service.real.com/test/), I found that video was fine for G2 and rv8 video streams, but had no sound for rv9/rv10 formats. The audio formats all failed to get through the buffering stage. 

The fix:
What finally worked for me is a variation of [https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/91500/comments/6](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/91500/comments/6):
I increased gxine's engine.decoder_priorities.realadec to 10, either by directly editing ~/.gxine/config (don't forget to uncomment the changed line) or through gxine's preferences gui: choose expert experience level, then engine->decoder_priorities->realadec, change value to 10 & save.

Warning: I'm a relative newbie & don't know what else this might break. Values other than 10 may also work.

---

### Post by Abdoun on 2007-06-09
Hi febrile,

Have similar problems, your solution worked fine for me. I think you may enter any value greater then 0 and it works somehow. 

However one radio stream still behaves strange. It did not work before at all but now the sound is distorted as if I have something like two streams being received with a little time delay. Tried several options but could not figure out a solution. It is a pity because it is my favourite station and I can receive it only on the internet.

Anyhow, thanks for your advice.

Abdoun

;);)

---

### Post by febrile on 2007-06-10
Hey Abdoun
> **Abdoun said:**
> ... Have similar problems, your solution worked fine for me. ...
Nice.

> **Abdoun said:**
> ... However one radio stream still behaves strange. ...
Can you post a link to it?

---

### Post by Abdoun on 2007-06-10
Yes sure, here it is

rtsp://stream1.rbb-online.de/broadcast/radioeins-live.ra

Greatful for any assistance

Regards

---

### Post by Abdoun on 2007-06-10
And, by the way, cannot play streaming windows media, no input plugin found 

???

---

### Post by febrile on 2007-06-10
Yep, that stream also gives me the same problem - the 1st 1-2 seconds are fine but then it gets increasingly jumpy like it's jumping between 2 streams. wierd. I assume it plays ok for you on other platforms. May be best to open up a new thread for that to catch attention.

Windows media seems ok for me... post an example link?

---

### Post by Abdoun on 2007-06-10
Yes, exactly same behaviour.

I could not find the WMA streaming  link but you can go to

[http://www.wdr.de/radio/wdr2/](http://www.wdr.de/radio/wdr2/)

Click on the little loudspeaker icon, in the pop up window you can choose between real and wma, real works fine with me, wma I get error message.

Thanks

---

### Post by febrile on 2007-06-11
Ok, the error I get for that stream is:

The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

The xine engine log (gxine menu: view->engine log) shows
> 09:59:44: xine: found demuxer plugin: image demux plugin
09:59:44: xine: found input plugin  : file input plugin
09:59:44: xine: cannot find input plugin for MRL [mms://202.125.167.86/ASF/KETTLE/32-KETTLE-FADING-Deviations%20{4}.asf]
09:59:44: xine: input plugin cannot open MRL [mms://202.125.167.86/ASF/KETTLE/32-KETTLE-FADING-Deviations%20{4}.asf]
09:59:44: libmmsh: http status not 2xx: >400 Bad Request<
09:59:36: xine: found input plugin  : mms streaming input plugin

I'm no expert by any stretch, but the fact that it's trying http connection suggests that mms over tcp has failed for some reason. Maybe this is the sort of error you'd see if the remote server doesn't accept http fallback. Someone wiser than me might be able to shed some light on this ...?

---

### Post by andrew.46 on 2007-09-03
Hi,

 Read your problem with the following stream:

> **Abdoun said:**
> Yes sure, here it is

rtsp://stream1.rbb-online.de/broadcast/radioeins-live.ra

Greatful for any assistance

Regards

 Cannot help you with your software but the stream plays perfectly in mplayer:

```
mplayer rtsp://stream1.rbb-online.de/broadcast/radioeins-live.ra
```

        Andrew

---


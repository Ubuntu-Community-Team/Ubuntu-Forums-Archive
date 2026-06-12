---
title: "Quicktime needs mpeg-4 aac decoder"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by dgermann on 2008-02-23
Hi--

Trying to get quicktime to run on Gutsy. I have done all these:
```
sudo apt-get install w32codecs
sudo apt-get install ubuntu-restricted-extras
sudo apt-get autoremove
sudo apt-get install faac faad

```

I have also rebooted in between, but still cannot get videos from [http://www.quicktime.com]("http://www.quicktime.com").

I did run firefox from the command line and when I shut down, found these error messages:
```
** Message: Viewer state: PLAYING
** Message: don't know how to handle video/x-h264, codec_data=(buffer)014d400dffe10014274d400da9182826f2e00d418041adb0ad7bdf0101000428de0988, width=(int)320, height=(int)136, framerate=(fraction)2997/125
** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, rate=(int)44100, channels=(int)2
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2215): prepare_output (): /play

** Message: Viewer state: STOPPED
** Message: totem_embedded_set_error: 'An error occurred', 'The playback of this movie requires the following decoders which are not installed:

MPEG-4 AAC decoder
H.264 decoder'
** Message: totemPlugin dtor [0x9234e90]
** Message: NP_Shutdown
** Message: totemNarrowSpacePlugin dtor [0x90b6eb0]
doug@doug2:~$
```

Any ideas how to trouble-shoot this?

Thanks!

---

### Post by wolfen69 on 2008-02-23
i went to quicktime.com and videos work for me. install mozilla-mplayer to see if this helps.also, if it still does not work, you will have to remove totem and everything with totem in the name.(totem conflicts with mplayer) do this in synaptic. vlc is a good alternative for totem.

---

### Post by dgermann on 2008-02-23
wolfen69--

Well, something is happening!

I did have mozilla-mplaye, so I uninstalled all totem stuff.

The buffering is taking forever--hope that's just the first time. Will report back when it is done.

Thanks!

Back again:

Well, it works on the quicktime website. That is fantastic progress! Many thanks!

Now here is what I want to play, but it does not work for me: [http://www.royalcaribbean.com/findacruise/cabinclass/home.do]("http://www.royalcaribbean.com/findacruise/cabinclass/home.do")

(Click on any of the 360 degree tours.)

Any hints? Firefox says a plugin is needed, but gives no clue as to what it might be....

Thanks!

---


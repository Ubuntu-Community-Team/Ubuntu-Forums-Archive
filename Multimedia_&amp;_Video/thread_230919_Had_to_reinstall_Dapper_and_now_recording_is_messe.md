---
title: "Had to reinstall Dapper and now recording is messed"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Grog140 on 2006-08-06
My system had to be reinstalled yesterday and recording isn't working properly.

In skype V1.3 beta I was getting aprolem with sound device error. I then wanted to test it in sound recorder but that gave me an error wile opening it. The error said my multimedia settings were incorrect and I should fix it in multimedia system selector.

In the Media selector input and output were set to also (I expect this is what it should be) But when I set the input to OSS I am able to open and record in Sound Recorder. I still get the skype error though.

In order to get skype working I need to set skype to use OSS instead of ALSA which is absolutely not what I want! 

I am thinking it is an Ubuntu problem since sound recorder was messed as well as skype when they are both usually configured properly right off the bat.

Thanks

EDIT: There are a few other sound related things that are off from when I had Ubuntu set up yesterday. One such thing is that when I do get sound recorder working I can't select capture as the device. And in the terminal if I hit backspace when there is nothing typed then it will beep at me like a system beep but through my headphones/speakers. The same beep happens when I try and tab to complete at the terminal.

EDIT2: The error I get for skype is:

```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

```

---


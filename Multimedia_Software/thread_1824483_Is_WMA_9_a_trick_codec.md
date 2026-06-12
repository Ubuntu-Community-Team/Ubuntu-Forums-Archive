---
title: "Is WMA 9 a trick codec?"
date: 2011-08-13
forum: Multimedia Software
---

### Post by bliffle on 2011-08-13
I tried viewing a certain movie with VLC and got a blurb about going to Microsoft for a special codec (which turned out to be WMA 9). I couldn't get the codec anyplace and even WinXP/WMP couldn't handle it. What's the story? Is this a DRN problem? Is there a VLC codec for this?

---

### Post by andrew.46 on 2011-08-14
Mplayer should be able to play this with an external codec:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i 'Windows Media Video 9'[/COLOR]**
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]

```

and a similar story for the audio versions, some with codecs and some from libavcodec. On 32 bit installation though. Do you have a link to this file?

---


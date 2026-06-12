---
title: "Help with playng music from CD"
date: 2015-07-30
forum: Multimedia Software
---

### Post by ymurti2 on 2015-07-30
Hi 

I tried to play a CD with wav format music and attached is what I hear. I tried to copy the file to the computer and then play it but still it do not play properly. Other music files that I have in my computer play nicely. Does someone knows how to solve this problem????
Here in this address you can hear what I am hearing when I try to play the file:
[https://drive.google.com/file/d/0B-nrS5WTQ60oNWxkQlpqRVd6M2M/view?usp=sharing](https://drive.google.com/file/d/0B-nrS5WTQ60oNWxkQlpqRVd6M2M/view?usp=sharing)

Thank You in advance.

Ymurti

---

### Post by slickymaster on 2015-07-30
*Moved to the ***Multimedia Software*** sub-forum*

What media player are you using to play the file?

You're maybe hitting this really ancient, and unresolved, bug: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1124408](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1124408)

---

### Post by ymurti2 on 2015-07-30
> **slickymaster said:**
> *Moved to the ***Multimedia Software*** sub-forum*

What media player are you using to play the file?

You're maybe hitting this really ancient, and unresolved, bug: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1124408](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/1124408)


Dear [COLOR=#000000]slickymaster,  thank you for your reply. I tried play it with totem, VLC and Rhythmbox but without good result. Just now I tried converting the wav file to MP3 but did not change the result of the music.

[/COLOR]

---

### Post by slickymaster on 2015-07-30
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2245379") and see if the solution provided at post #2 helps you.

Or you could try audacious```
sudo apt-get install audacious
```

---

### Post by ymurti2 on 2015-07-30
Audacious did not work :(  and what does it mean FF and how I get there (in the link that you gave).

---

### Post by slickymaster on 2015-07-30
> **ymurti2 said:**
> Audacious did not work :(  and what does it mean FF and how I get there (in the link that you gave).

FF refers to the Firefox browser.

---

### Post by andrew.46 on 2015-07-30
> **ymurti2 said:**
> Dear [COLOR=#000000]slickymaster,  thank you for your reply. I tried play it with totem, VLC and Rhythmbox but without good result. 

[/COLOR]

Try MPlayer from the commandline and you might get some useful error messages at least:

```

mplayer -cache 2048 -cache-min 80 cdda://

```

and maybe decent playback as well :)

---

### Post by ymurti2 on 2015-07-30
Thank you Andrew but it did not work, well has played the CD but the sound is not good.

---

### Post by mc4man on 2015-07-30
Is this a normal audio cd or a cd with some .wav files on it?

---

### Post by ymurti2 on 2015-07-31
Dear mc4man,

It is a normal CD that I bought long time ago, with some music in wav format.

---

### Post by mc4man on 2015-07-31
> **ymurti2 said:**
> Dear mc4man,

It is a normal CD that I bought long time ago, with some music in wav format.

Then it's more likely a hardware or physical media issue. If other audio cd's play fine then something with the cd itself. 
Maybe try using a ripper rather than copy a 'wav' file from the media, maybe it'll report some errors, ect.

---

### Post by ymurti2 on 2015-08-01
Thank You very much [COLOR=#000000]mc4man. I have used Asunder and now I can hear the beautiful music from my CD.    [/COLOR]):P


> **mc4man said:**
> Then it's more likely a hardware or physical media issue. If other audio cd's play fine then something with the cd itself. 
Maybe try using a ripper rather than copy a 'wav' file from the media, maybe it'll report some errors, ect.

---


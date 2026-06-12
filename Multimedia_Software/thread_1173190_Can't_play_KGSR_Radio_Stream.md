---
title: "Can't play KGSR Radio Stream"
date: 2009-05-29
forum: Multimedia Software
---

### Post by jonno on 2009-05-29
I've been trying to get the url to stream my favorite local radio station KGSR. I can't get it to play on my Ubuntu or Mythbuntu systems either through accessing [www.kgsr.com](www.kgsr.com), via [Reciva]("https://www.reciva.com/index.php?searchBar=KGSR&option=com_cloud&action=search#") or trying various url's directly in vlc or mplayer.
KGSR.com and the reciva link work in windows.
This url used to work, [http://uni1.emmis.streamaudio.com/KGSR_FM?](http://uni1.emmis.streamaudio.com/KGSR_FM?) directly in vlc or mplayer but now they don't.
If I try that link now in Windows Media Player it asks for a user name and password.
If anyone knows how to get this working, preferably with a direct url that a media player will play without having to use a browser then I would really appreciate the help. I don't know why they make it so difficult.

---

### Post by jonno on 2009-05-29
FYI I used URL Snooper when playing the stream via the Reciva link and got this as one of the url's:
mms://2.uni1.emmis.streamaudio.com/KGSR_FM?SAT=ac837765132474fe23b31e7cef458a0a&ts=1243605378949&s=1369&y=2009&m=5&d=29&hh=13&mm=56&ss=15&hip=www_streamaudio_com
It seems to have the date & time embedded into it so maybe they are using that to limit access for some reason.
I launched another stream 18mins later and got this:
mms://2.uni1.emmis.streamaudio.com/KGSR_FM?SAT=064e2c4a4e561a027a968984dc92ad78&ts=1243606476945&s=1369&y=2009&m=5&d=29&hh=14&mm=14&ss=26&hip=www_streamaudio_com
I tried modifying the time in the original url after 15mins and it didn't work so obviously the SAT= number has some bearing. What a pain.

---

### Post by hansdown on 2009-05-29
Hi jonno.

Just so you know, it plays for me.

Do you have flashplugin-nonfree installed? I hope that is the right one.

It's in synaptic package manager.

---

### Post by jonno on 2009-05-29
> **hansdown said:**
> Hi jonno.

Just so you know, it plays for me.

Do you have flashplugin-nonfree installed? I hope that is the right one.

It's in synaptic package manager.

Pretty sure it's not using flash. Did you use the Reciva site or the KGSR site? What player was used? In both cases it gives me a .asp file containing similar mms url's.

---

### Post by hansdown on 2009-05-29
The KGSR site.Here's a screenshot.

I see from the data stream that you likely need to install

ubuntu-restricted- extras from synaptic.

---

### Post by jonno on 2009-05-30
> **hansdown said:**
> The KGSR site.Here's a screenshot.

I see from the data stream that you likely need to install

ubuntu-restricted- extras from synaptic.

Hmm that didn't work on its own. Looks like it played for you with a plugin. Do you know which plugin it is using? My browser doesn't know what to do with the .asf file so it asks me and I've tried MPlayer and vlc.

---

### Post by hansdown on 2009-05-30
You're right jonno.

It's playing in firefox.I'll check my plugins.

Click tools>addons> plugins in firefox.

My installed plugins are:```
QuickTime Plug-in 7.2.0, Shockwave Flash,

Totem Web Browser Plugin, VLC Multimedia Plugin, 

and Windows Media Player Plugin 10
```

---

### Post by xc3RnbFO8P on 2009-05-30
Works in **Epiphany Web Browser (Gecko)**

---

### Post by jonno on 2009-05-30
Not sure what exactly was missing but I got it working using the MPlayer plugin. Thanks for the help.

---

### Post by hansdown on 2009-05-30
Good work jonno. Glad you fixed it.

---


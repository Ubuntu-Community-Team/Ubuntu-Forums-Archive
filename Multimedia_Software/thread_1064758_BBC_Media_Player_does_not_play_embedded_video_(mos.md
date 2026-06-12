---
title: "BBC Media Player does not play embedded video (mostly)"
date: 2009-02-09
forum: Multimedia Software
---

### Post by ianhaycox on 2009-02-09
I'm having problems playing some videos on the BBC news web site in Firefox.

For example, [http://news.bbc.co.uk/2/hi/asia-pacific/7878123.stm](http://news.bbc.co.uk/2/hi/asia-pacific/7878123.stm)  works

whereas, [http://news.bbc.co.uk/2/hi/uk_news/7874998.stm](http://news.bbc.co.uk/2/hi/uk_news/7874998.stm)  does not work. I just get a spinning circle.

Right clicking on both shows the BBC Media Player with a codec of vp6 but they differ in that one has a service id of AK (works) and the other DC (doesn't work).

MPlayer plays the One Minute News link at the top of the page in a pop-up OK. Flash (V10) plays OK.

I've tried loads of links suggesting installing and removing various combinations of mplayer/totem/realplayer etc. but no joy.

Can anyone else (I'm outside the UK) can view all these videos ? If so what plugins/config do you have.

BTW - Ubuntu 8.10

This is very frustrating so thanks for any help,

---

### Post by itang sanjana on 2009-02-09
No problem here. I use 64 bit Ubuntu. I live outside UK too. The picture below is my Firefox plugins list.

---

### Post by redroad55 on 2009-02-09
This guide gives a list of all necessary things for streaming..If you have any problems post back ..Best to you
 [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by ianhaycox on 2009-02-09
itang sanjana - Thanks for that. I removed/installed various plugins to get my list also identical to your, except my totem plugins version was 2.24 no 2.22. However no change.

redroad55 - I went through the HOW TO very carefully and updated all the packages without error but it has made things worst. The One Minute news no longer works and the two links are the same.

Any more ideas anyone ? or someway of diagnosing the problem ?

---

### Post by itang sanjana on 2009-02-09
Sometimes Java could be the problem.
You can test it by going to:
[http://www.javatester.org/version.html](http://www.javatester.org/version.html)
Checking for the pink box and line of text.
HTH

---

### Post by redroad55 on 2009-02-09
Just to make sure you have medibuntu repository enabled in software sources applications > system > admin. > software sorces > third party tab .. real player 9 and the java plugin are not present in list above are they on your list? Post back

---

### Post by ianhaycox on 2009-02-09
Re:-2 I have the pink rectangle for Java.

Re:-1

So far I've got

Installed plugins

```

Java(TM) Plug-in 1.6.0_10-b33

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

Default Plugin

Demo Print Plugin for unix/linux

DivX Browser Plug-In

    File name: gecko-mediaplayer-dvx.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

QuickTime Plug-in 7.4.5

    File name: gecko-mediaplayer-qt.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

RealPlayer 9

    File name: gecko-mediaplayer-rm.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

Windows Media Player Plug-in

    File name: gecko-mediaplayer-wmp.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

gecko-mediaplayer 0.7.0

    File name: gecko-mediaplayer.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

```


```

ian@ianh:~$ ls /usr/lib/mozilla/plugins/
flashplugin-alternative.so  gecko-mediaplayer-dvx.xpt  gecko-mediaplayer-qt.xpt  gecko-mediaplayer-rm.xpt  gecko-mediaplayer-wmp.so   gecko-mediaplayer.xpt  nphelix.so
gecko-mediaplayer-dvx.so    gecko-mediaplayer-qt.so    gecko-mediaplayer-rm.so   gecko-mediaplayer.so      gecko-mediaplayer-wmp.xpt  libjavaplugin.so       nphelix.xpt

```

The mediabuntu repo was enabled and in all cases I've restarted Firefox and also deleted pluginreg.dat to make sure.

Any other pointers or advice ?

---

### Post by redroad55 on 2009-02-09
Give this a read it addresses the problem I believe particularly post # 13 .. If this does not resolve post back .. Best to you
[http://ubuntuforums.org/showthread.php?t=1061381&highlight=bbc]("http://ubuntuforums.org/showthread.php?t=1061381&highlight=bbc")

---

### Post by ianhaycox on 2009-02-09
Thanks for you help guys.

Unfortunately it wasn't a Flash version issue.

Good news (almost). On a hunch I used firefox --ProfileManager to create a new profile. Using that profile I could view all the BBC video links and the One Minute News.

I'm guessing it's either a 'corruption' in the firefox settings to do with plugins, or some clash with an extension etc.

Both firefox profiles listed the same plugins, but the default didn't play the video and the new test profile did.

I'll try an isolate the exact cause and report back and/or file a bug.

---

### Post by Morm on 2009-04-17
Thanks to ianhaycox, I've resolved this. I tried playing BBC video in a new profile and noticed Firefox was contacting Doubleclick - aha! So it was Adblock Plus that was preventing the video from playing. I added news.bbc.co.uk to the whitelist and now the video plays just fine - with ads. Better than nothing.

---


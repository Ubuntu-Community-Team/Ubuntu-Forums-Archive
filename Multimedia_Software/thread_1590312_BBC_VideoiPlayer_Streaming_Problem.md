---
title: "BBC Video/iPlayer Streaming Problem"
date: 2010-10-07
forum: Multimedia Software
---

### Post by Nuskrad on 2010-10-07
A few weeks ago I started getting an issue watching videos on the BBC website. This includes any short clips, such as on the news pages, as well as full programmes on the iPlayer. Basically, videos start playing fine. Then after a few minutes, it appears they are buffering (the video dims and the buffering icon appears over it), however there is no pause in the video. Then a second audio stream starts up, which is a few seconds out of sync with the video and the normal audio stream. Pausing the video stops it and the first audio stream, but the second stream carries on until I navigate away from the page or close the tab.

I've tried everything I can think to solve this, including tracking down older builds on the flash plugin, and even formatting the drive and installing Ubuntu 10.10 (I was previously using 10.04). Nothing has worked, the bug manifests in exactly the same way.

This is incredibly infuriating because it makes it impossible to watch videos on the BBC website, but from my web searches I've found no one else who seems to be suffering the same issue. I'm at a complete loss as to what has caused this to start happening and what to do to fix it :confused:

Edit: This may not be an Ubuntu issue, because I've found someone else describing the same problem on XP and OSX - [http://www.bbc.co.uk/dna/mbiplayer/NF13735685?thread=7650406](http://www.bbc.co.uk/dna/mbiplayer/NF13735685?thread=7650406)
Oddly, I am fine if I boot into my W7 partition which would seem to rule out a network issue or anything like that.

---

### Post by Illusion989 on 2010-10-21
I am having exactly the same issue. I am using 10.04. Hopefully, someone can help us out with this problem.

Everything seems to be working on XP.

Also, I tried various browsers, but, apparently the problems still exists.

---

### Post by vinceg0orc on 2010-10-23
Hi all,

To add my five bobs worth, I listen a lot to BBC radio (especially R7) and the same problem of multiple streams playing occurs there too. At times I believe I can hear 3 separate streams of the same programme playing, all are a few seconds apart which make listening almost impossible.  This only occurs on "play it again" content, live streaming is fine.  Yesterday I installed the BBC iplayer desktop, hoping this may be a cure but there is no change.

This problem has existed over several Ubuntu releases from when I first starting using it at version 9.10.  Currently using v.10.10.  I know friends who have the same problem too, people who I have encouraged to move to Ubunto but are now disappointed when things don't work out.

I suspect the problem is with the BBC iplayer, as other streaming audio from other radio stations works fine.  I don't know what we can do, e-mailing the BBC either evokes nil response or the response that we are forwarding the e-mail to someone who can help which is where it ends.

Vince

---

### Post by Stormx on 2010-10-27
I'm having the same issue. I was originally on 32-bit flash but I've upgraded to the 64-bit alpha with no effect.

Problem also exists on chrome.

I'm stumped as to what the problem could be!

---

### Post by Ray Hamilton on 2010-10-28
Yes I too have this problem using 10.04. It only appears to have happened relatively recently.  It also happens with Google Chrome and Firefox.  It does not happen with XP.  It does not appear to happen with anything else e.g YouTube.  As an additional clue, I get a frequent message that indicates there is a bandwidth problem and today it was so bad that it stopped with message something like "sorry the content is not usable, try again later".  It was okay in XP a few minutes later when I booted into it.

Again I am not sure if it is related but I have been getting problems with ITV player also. (All checks on bandwith/speed seem ok.)

To add another update: This appears more on my laptop because that is where I watch TV more, but my desktop does it also - however it is less prominent and (significantly because it has 3 GB of RAM?) I got to 12 mins of a 28 min program before seeing a problem.

---

### Post by achinton on 2010-11-06
+1

Anyone found any solutions?

---

### Post by Stormx on 2010-11-12
[http://www.guardian.co.uk/technology/blog/2010/mar/01/bbc-iplayer](http://www.guardian.co.uk/technology/blog/2010/mar/01/bbc-iplayer)

> The BBC has reportedly started using the SWF Verification routine -- aimed at protecting copyright content -- with its iPlayer streaming video service. It could be an attempt to stop third-party software from downloading videos, which usually only last for seven days. However, it has the side effect of dropping the video stream after one or two minutes when used with unauthorised players. This includes open source media players such as XBMC.

It seems like a remote possibility that some network setting is stopping these verification pings. Maybe it's an adblock thing?

BTW, get_iplayer works fine.

---

### Post by pjcdawkins on 2010-11-14
> **Stormx said:**
> It seems like a remote possibility that some network setting is stopping these verification pings. Maybe it's an adblock thing?

On that cue I've disabled Adblock for bbc.co.uk, and I haven't had the problem again so far...

---


---
title: "Firefox extensions/script suggestion for YouTube HTML5 player"
date: 2011-12-11
forum: Multimedia Software
---

### Post by Virus666 on 2011-12-11
Hi all,

As some of you know **YouTube** has launced **HTML5** video support on January 2010. If we enample HTML5 option in the first of following adresses, supported videos begin to play in HTML5 Player instead of **Flash Player**.

[http://www.youtube.com/html5](http://www.youtube.com/html5)
[http://youtube-global.blogspot.com/2010/01/introducing-youtube-html5-supported.html](http://youtube-global.blogspot.com/2010/01/introducing-youtube-html5-supported.html)

Actually, that is a great news for Free Software community to get rid of proprietary Flash Player... However, as some of you have experienced, HTML5 Player of YouTube does not fully support **fullscreen** videos; once you clicked "**full screen**", the video expands as **windowboxed** insted of fullscreen:

***See attached screenshot***

Of course it is possible to make it actual fullscreen by pressing **F11**. However, as you can imagine, it is a bit emberessing to press 4 keys to watch and close a video; "full screen", F11, ESC, F11.

There are several explanations from YouTube and **Google** that explains why HTML5 player does not support actual fullscreen as default:

- Fullscreen is not an accepted specification of HTML5 yet. It may be vulnerable to explotations.
[http://apiblog.youtube.com/2010/06/flash-and-html5-tag.html](http://apiblog.youtube.com/2010/06/flash-and-html5-tag.html)

However, some other people assert that Firefox **Aurora** and **dev** channel of Chrome has the capability of fullscreen HTML5 YouTube video play as default:
[http://googlesystem.blogspot.com/2011/11/youtubes-html5-player-gets-better.html?showComment=1322072944484#c3707728724378655185](http://googlesystem.blogspot.com/2011/11/youtubes-html5-player-gets-better.html?showComment=1322072944484#c3707728724378655185)

By the way, I have no plan to switch to **Google Chrome** or **Chromium**; same as for the instable releases of Firefox. I have no skill of coding nor scripting, but I thing it should not be that hard to prepare a script or an extension which automaticly presses F11 once we click "full screen" button of HTML5 player of YouTube and automaticly presses the F11 button when press ESC button the exit the fullscreen. Since the player is HTML based, it should not be so complicated...

Any ideas or suggestions?...

Thank you...

---

### Post by lovinglinux on 2011-12-12
I thought there was an extension to maximize html5 videos, but I couldn't find it.

Have you tried [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)?

I could try to implement such feature on FVR, but I am extremely busy this end of year. So I won't be able to take a look at this until next year.

---

### Post by Virus666 on 2011-12-12
> **lovinglinux said:**
> I thought there was an extension to maximize html5 videos, but I couldn't find it.

I think that you mentioned [Full Screen Video]("https://addons.mozilla.org/tr/firefox/addon/full-screen-video/"). However, as it appears, it has not been updated since Firefox 3.5. I tried to edit "install.rdf" in order to make the extension campatible with Firefox 8; however, it had no effect on YouTube's HTML5 player.

Anyway, I will try Chrome's dev channel and Firefox Aurora and Firefox Nightly to see whether rumors true or not. Thank you...

---

### Post by Virus666 on 2011-12-12
Update:

I have just tried **Google Chrome**'s dev channel on my Ubuntu 10.10 **Maverick Meerkat** (x86). It really supports fullscreen YouTube HTML5 player.

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

Version: **17.0.963.6-r113986** (google-chrome-unstable)

I found "**Official PPA for Firefox Aurora builds**"; however, since I do not desire to break my stable Firefox 8, I am postponing that try for another time.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora")

Later...
</div>

---

### Post by Virus666 on 2011-12-13
Another update:

I have just installed Firefox **Aurora** (10) and it really supports fullscreen **HTML5** player of **YouTube**. It seems that if we wait until **January** 2012, we will have fullscreen HTML5 support for YouTube without needing an extension or a script.

Current Firefox **Aurora** PPA package for Ubuntu 10.10 **Maverick Meerkat** (x86):
** 10.0~a2~hg20111210r80756-0ubuntu1~umd1~maverick**

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---


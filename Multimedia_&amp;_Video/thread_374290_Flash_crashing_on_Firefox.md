---
title: "Flash crashing on Firefox"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-03-02
I have the same problem as the guy in [this thread]("http://www.ubuntuforums.org/showthread.php?t=320227"). When I move away from a page that has a Flash applet on it, Firefox crashes.

I already tried these things:> I heard that this is a bug with flash and 16bit colour depthI'm using 24bit color depth.> Start firefox and in the address field, see which flash plugin you have!I have *Shockwave Flash 9.0 r31*, so that shouldn't be a problem.

Anything else I can try? Thanks in advance!

---

### Post by deadgobby on 2007-03-03
If you run Dapper 6.02 LTS FF it love to crash when flash player sites come up. Try installing Falsh Blocker from Mozilla site. All so have you up graded to FF 2.0? 
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
 I know the song of FF crashing on Dapper. How ever when I upgraded from Dapper to Eft. It does not crash.
Gobby

---

### Post by elreteipos on 2007-03-03
> **deadgobby said:**
> If you run Dapper 6.02 LTS FF it love to crash when flash player sites come up.I'm using Kubuntu 6.10, so that can't be the problem.> **deadgobby said:**
> Try installing Falsh Blocker from Mozilla site.I already downloaded that tool, but it's just a temporary solution. I just want to be able to view Flash applets without Firefox crashing. :)> **deadgobby said:**
> All so have you up graded to FF 2.0?Yup, I'm running 2.0.0.2 (downloaded via apt-get, with Dutch language pack).

---

### Post by elreteipos on 2007-03-17
I fixed my own problem. Turns out that the coComment or Clipmarks extension was conflicting with Flash. I don't know which one since I disabled both of them at the same time.

[Update] I thought it was fixed, but it isn't. Too bad.

---


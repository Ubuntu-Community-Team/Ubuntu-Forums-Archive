---
title: "Tivo software on ubuntu 20.04 or any linux, help?"
date: 2020-04-27
forum: Multimedia Software
---

### Post by jebi on 2020-04-27
hi,

My Tivo box is acting up and has a load of stuff that I have not seen yet.  I think it is a problem on my providers side but in any case, they are saying that I have to do a factory reset.

I was looking using kmttg to temporary transfer to spare HDD, then re-upload to the Tivo after reset.

But I'm having a major problem even getting kmttg to launch.

kmttg needs oracle java 1.8 and 1.8 only, I think I have worked out that Java 8 is 1.8.  But I get an UncaughtExceptionHandler error when launching.

I know this is not a kmttg support forum but there does not seem to be an active forum where anyone even responds, so I thought I'd give it a try on the ubuntu multimedia forum, maybe someone uses kmttg and could help, I would be extremely grateful if someone could help?

I don't understand why no one has done a youtube video on how to get this app working, which is a real shame as it looks awesome.

Failing that anyone know an easy-ish alternative to use, preferably on ubuntu but at this point I'd settle for Windows or Mac.  really needs to free but I might pay for an app that works if it was cheap-ish even then I don't really have the money.

Many thx to anyone who has any suggestions.

*[https://sourceforge.net/projects/kmttg/](https://sourceforge.net/projects/kmttg/)

---

### Post by TheFu on 2020-04-27
Haven't touched my tivo S2 in a very long time, but used kmttg to pull recordings off it all those years ago.  it wasn't java based at the time.  it was a tk and perl program.  The main trick is to have the tivo MAK - media access key - that is a unique identifier for the tivo to remove the DRM wrapper after the xfer and save as an mpeg2 file.  Just had to put it into the config.ini file.  There was a *tivodecode* program.  i don't have a copy of that anymore, it seems. Sorry.  [https://sourceforge.net/projects/tivodecode/](https://sourceforge.net/projects/tivodecode/) looks like that might be it.

The xfers were really slow.  I’d run them overnight.

i doubt there'd be any way to upload the files after.  That wasn't the purpose for any of those programs.  My goal was to remove all DRM possible ASAP.

---


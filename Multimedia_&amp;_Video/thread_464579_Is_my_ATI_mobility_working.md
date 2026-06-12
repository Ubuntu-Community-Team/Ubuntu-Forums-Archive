---
title: "Is my ATI mobility working?"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by daniel_victoria on 2007-06-04
Hi all, 

I have a Toshiba Satellite with the following graphics card:
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

The laptop is a Pentium 4, 3 Ghz with 512 Mb RAM.

The thing is, everything looks OK, the graphics card is working BUT, I don't know if it's "giving all it's got". When I issue glxgears -info I get speeds close to 700 FPS and the following output:
GL_RENDERER   = Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 NO-TCL
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc.

Also, I just noticed that if I put another window on top of the gears the FPS increases a lot, up to 1700 FPS, BUT a small humming sound can be heard :shock:

I'm using the display driver that came with Ubuntu 7.04. Actually I upgraded from Dapper the Edgy and now to Fawn

thanks

---

### Post by mister_doctor on 2007-06-05
Are you by chance running a Satellite A70? I'm about to drop 7.04 onto one in the next hour or so, once my colleague finishes trying to put Mac OS x86 on it...

The last time I tried to install Ubuntu was 6.1, and it just sat there after logging in using X. Lame.

---

### Post by Rocket2DMn on 2007-06-05
Older versions of ATI cards have limited support with linux, and from what i understand, the upgrade to feisty has resulted in some loss of functionality.  For example, I cannot dual head correctly with my Radeon Mobility 9000 Pro.

---

### Post by daniel_victoria on 2007-06-05
> **mister_doctor said:**
> Are you by chance running a Satellite A70? I'm about to drop 7.04 onto one in the next hour or so, once my colleague finishes trying to put Mac OS x86 on it...

The last time I tried to install Ubuntu was 6.1, and it just sat there after logging in using X. Lame.

I have a A75 and Feisty is working more or less. It was freezing every now and them and, from what I read in the forum, a bunch of people are complaining about it. But apparently the noacip flag at boot time fixed the issue.

---


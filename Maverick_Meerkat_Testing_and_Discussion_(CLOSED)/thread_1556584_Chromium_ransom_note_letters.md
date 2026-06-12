---
title: "Chromium ransom note letters"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by hugmenot on 2010-08-19
Chromium renders letters with an off-white background on my screen.
It looks like a ransom note when you tilt your LCD backwards to look at it from below.

I need someone to confirm this. I&#8217;m guessing it could be Intel graphics only.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167108&d=1282395258[/IMG]

---

### Post by fluteflute on 2010-08-19
[Report a bug]("http://code.google.com/p/chromium/issues/list"), they're normally quite good at fixing stuff.

---

### Post by hugmenot on 2010-08-19
I did, I want to know if what I’m seeing on my screen is widespread. I find them swamped with bug reports contrary to your statement.

---

### Post by phillw on 2010-08-20
Not seen it here,

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


I'm using Chromium 7.0.500.0 (56798) Ubuntu 10.04 which is the latest daily build```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main

```So, you may see something different in different versions ?
I've not heard of it the lubuntu area, which defaults to 'standard' released Chromium as the browser for 10.04 and 10.10 (unless you add the daily ppa, but heck - it's a testing cycle).

Regards,

Phill.

---

### Post by hugmenot on 2010-08-21
> **phillw said:**
> Not seen it here,


I’m using 7.0.500, too.

I have light hinting and subpixel filtering on.

This is what it looks like from below on my display:

---

### Post by phillw on 2010-08-21
> **fluteflute said:**
> [Report a bug]("http://code.google.com/p/chromium/issues/list"), they're normally quite good at fixing stuff.

+1

I've found the the people looking after the ubuntu version of Chromium to be very good at replying to & fixing bugs. 

hugmenot, please do file a bug to them. I cannot do so as I do not have the problem on my computer.

Regards,

Phill.

---

### Post by hugmenot on 2010-08-21
As I said, I have filed it, and a guy I know confirmed. But there was no response otherwise.

---

### Post by ktp on 2010-08-21
> **hugmenot said:**
> As I said, I have filed it, and a guy I know confirmed. But there was no response otherwise.

can you post a link to the bug so if someone does run into the issue can update it also?

---

### Post by hugmenot on 2010-08-22
[http://crbug.com/52242](http://crbug.com/52242)

---

### Post by ktp on 2010-08-22
> **hugmenot said:**
> [http://crbug.com/52242](http://crbug.com/52242)

thanks

---


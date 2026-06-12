---
title: "Cannot play DVDs"
date: 2010-12-05
forum: Multimedia Software
---

### Post by JustSteph on 2010-12-05
Hi, I recently installed Ubuntu 10.04 and am having trouble trying to play DVDs. I'm using vlc and have installed the ubuntu restricted extras but I still can't get any DVDs to play. Any idea what's causing this?

Thanks
Steph

---

### Post by drew2222 on 2010-12-05
I had problems playing DVD's and had to install several other files, as well as unrestricted extras, including some libdvd files and codecs. Some dvd's would play others would not. Have a look at:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by JustSteph on 2010-12-05
Thank you.

I tried the instructions in the link you gave me, but when running "sudo /usr/share/doc/libdvdread4/install-css.sh" I get:

```

--2010-12-05 14:47:43--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.
Dynamic fetch failed; Falling back to static fetch
--2010-12-05 14:47:52--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: Connection timed out.
Retrying.

--2010-12-05 14:48:14--  (try: 2)  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.
```

I applied the proxy I am behind system-wide in preferences, but is it likely that this is still the problem?

Thanks again.

---

### Post by mc4man on 2010-12-05
Well just get the package directly, go here, pick your arch (32 or 64 bit) and d. click on link.
[http://packages.medibuntu.org/lucid/libdvdcss2.html](http://packages.medibuntu.org/lucid/libdvdcss2.html)

---

### Post by JustSteph on 2010-12-05
Thank you! Works perfectly now =D

---

### Post by jimmers on 2010-12-05
JustSteph,
Greetings, I am running Lucid, it is my only O.S, I use Kaffeine to play DVD's with no worries, but I have to install Gxine as well.
But saying that I have watched DVD's using VLC, Totem and SM Player and have had no worries.

Give one a try it wont hurt, and it just may work.

Luck

---


---
title: "no sound from amarok and Rhythmbox, but audacious plays perfectly"
date: 2010-10-30
forum: Multimedia Software
---

### Post by jringoot on 2010-10-30
I have since a while (after problems with beid which corrupted my qt4, which appears now corrected. Since Kate and k3b work again) no sound in amarok nor rhythmbox.

In audacious, everything plays nicely.

I tried to find (with ldd and kompare) which libraries amarok and rhythmbox use and audacious not.

I got this list:

	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x1c830000)
	libnsl.so.1 => /lib/libnsl.so.1 (0x00c6d000)
	libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x0be9c000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x013f3000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00455000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x11ea8000)
I tried to find, in which package they come via this site: 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And reïnstalled all packages involved.

Still no sound in amarok nor rhythmbox but still in audacious.

Any help or suggestion is welcome.

---


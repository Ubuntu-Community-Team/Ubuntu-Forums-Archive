---
title: "S-video TV output quality"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by gapplewagen on 2007-03-14
I recently set up a mythtv frontend box.  Everything works, looks, and sounds great when I have it hooked up to a monitor.  However, when I move it to my tv and switch over to the S-video ouputs on my video card (Nvidia FX5200) the video quality is HORRIBLE.  The colors are washed out and there is a criss-cross pattern throughout any solid color.  It gives me a headache instantly.  It does this while running MythTV and while just sitting at my Gnome desktop.  I'm thinking this my be a refresh rate issue but I'm not sure how to forcibly change this and not harm my tv.  If I use the Screen Resolution app it shows that it's refresh rate is 50Hz which seems low to me (but TV's may be different, not sure).  I'm outputting to a 50" Toshiba Cinema series.

Any ideas?

---

### Post by omockler on 2007-03-14
You could manually edit the /etc/X11/xorg.conf file:

[http://www.linuxhardware.org/article.pl?sid=01/05/29/2147241&mode=thread]("http://www.linuxhardware.org/article.pl?sid=01/05/29/2147241&mode=thread")   or
[http://mysite.verizon.net/kraussa/nvidia_linux_tv_out.html]("http://mysite.verizon.net/kraussa/nvidia_linux_tv_out.html")

Both of the links walk through setting up an S-video out

---

### Post by gapplewagen on 2007-03-19
The second link worked.  Thanks!

---

### Post by denis_std on 2007-03-19
> **gapplewagen said:**
> The second link worked.  Thanks!

Could you paste me your xorg.conf. I'm having the same card and I get only black and white at my tv.

---

### Post by gapplewagen on 2007-03-19
My xorg.conf for that system is available here:

[http://mweller.blogspot.com/2007/03/pvr-xorgconf-file.html]("http://mweller.blogspot.com/2007/03/pvr-xorgconf-file.html")

I also have docs for getting my SnapStream Firefly remote to work with lirc and mythtv

---


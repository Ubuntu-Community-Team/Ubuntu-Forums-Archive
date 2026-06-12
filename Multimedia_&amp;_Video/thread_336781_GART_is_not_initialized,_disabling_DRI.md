---
title: "GART is not initialized, disabling DRI"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by [Jen0] on 2007-01-12
Hello,

I just installed the newest ATI driver ( 8.33.6 ) but after reboot I had 'GART is not initialized, disabling DRI' this message in Xorg.0.log. I dont know whats going on, I havent found any information about this error message. I got a Sapphire X1900XT card, xorg is the newest found in edgy ( updated today morning ).

Any ideas what to do? How to enable 3D acceleration and so?

Thanks,

J.

---

### Post by didu on 2007-01-20
anyone have any idea?

help please?

---

### Post by dp_wiz on 2007-02-14
Got same message on feisty with 8.33.6 drivers from repos. (dell 6400 / ATi X1300)

Just looked up a bit and seen that in /var/log/Xorg.0.log:
> 
No DRM connection for driver fglrx.


---

### Post by nihilocrat on 2007-02-14
I also got the exact same message with a Sapphire X700 pro. It also complained about not being able to allocate the 128mb of memory on the card. I was in the middle of installing Xgl with Beryl when I noticed all of this, and when I restarted everything mysteriously worked (albeit that I can't run 3d-accelerated applications in Beryl).

You could at least make sure that the agpgart module is installed in the kernel by running `lsmod | grep agpgart`.

---

### Post by fragmental on 2007-03-29
[google is your friend(sometimes)]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=Ti6&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+gart+is+not+initialized&spell=1")

More specifically [This was the second entry for my search.(this forum thread was the first)]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Missing_fglrx.ko")

---


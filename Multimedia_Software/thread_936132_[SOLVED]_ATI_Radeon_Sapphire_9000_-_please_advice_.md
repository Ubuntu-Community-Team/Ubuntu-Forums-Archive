---
title: "[SOLVED] ATI Radeon Sapphire 9000 - please advice with tv-out"
date: 2008-10-02
forum: Multimedia Software
---

### Post by megamania on 2008-10-02
I have recently upgraded to a not-so-new computer, and my older box is unused at the moment. It's an AMD Barton with 512MB ram and a ATI Radeon 9000 Sapphire. It's still fast enough to do almost anything with Linux.

I was wondering if I could use it to set-up my first multimedia box. The primary, basic use would be to watch movies on tv.
I read through the forums and on the web, and as far as I can see there are mixed results with TV-OUT, which is my primary need in this situation.

Do you have any experience with this, and can you point me to a solution that is likely to work for my Radeon 9000 Sapphire? 
I'm not being lazy, :) but as I said I found dozens of solutions and don't know which one to start with.

I think I'm going to fresh-install 8.10 when it is out, so hopefully starting with a clean system will make things easier. Speaking of which, would you suggest to start directly with Mythbuntu?

Thanks is advance for you help.

---

### Post by megamania on 2008-10-04
Can anybody give advice, please?

---

### Post by steefjeqv on 2008-10-05
Hi,

You should be able to use the tv out like this (terminal) :

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

The tv out quality is not that good but it should work.

If you want better quality you can use a vga to scart (rgb) cable.

[http://www.nada.kth.se/~feldt/vgascart/lodning.html]("http://www.nada.kth.se/~feldt/vgascart/lodning.html")

You'll need to configure your xorg.conf when using the above cable to avoid damaging your tv.

If you want to watch digital tv (dvb-t, dvb-s, dvb-c) you may want to consider using VDR.

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

[http://vdr.spaghettilinux.org/index.php?title=Pagina_principale]("http://vdr.spaghettilinux.org/index.php?title=Pagina_principale")

Greetings,
Steven

---

### Post by megamania on 2008-10-09
thanks, and sorry for the belated reply.

Since you tell me that the tv out quality is not good unless I use a vga to scart cable, I'll try the second option.

I need to find a proper cable though.

Thanks again!

---

### Post by robusat on 2008-10-11
I would advice you to use an s-video cabel if your tv has s-video socket.

---

### Post by megamania on 2008-11-03
After realizing I'd never find the time to build the cable myself, I took a look on ebay and found this:

[http://cgi.ebay.it/ws/eBayISAPI.dll?ViewItem&item=130261740644](http://cgi.ebay.it/ws/eBayISAPI.dll?ViewItem&item=130261740644)

It's very cheap and I'm wondering if I can expect it to work with my Ati Radeon 9000.

Can anybody please take a look and share their experience?  :-)

---

### Post by steefjeqv on 2008-11-03
Hi,

Difficult to say if it's going to work for sure.

In order to work you'll need to edit your xorg.conf so that it uses a compatible PAL signal with a low dot pixel clock. Otherwise your TV may get damaged.


One other thing, there's a known bug in radeon driver which causes the breakage of interlaced modes (which you need).
This may be solved in Ubuntu 8.10 (I'm not sure), but the bug was present in Hardy.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/144322]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/144322") 

Greetings,
Steven

---


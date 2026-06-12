---
title: "usb mic jack"
date: 2011-03-26
forum: Multimedia Software
---

### Post by oleink on 2011-03-26
I have a usb mic and i wanted to use it in jack but I cannot use it with my soundcard as the output device.  Why would this be?

---

### Post by oleink on 2011-03-28
*bump*

---

### Post by cchhrriiss121212 on 2011-03-28
Jack only works with one card at a time, unless you start using alsa_in/alsa_out:
[http://manpages.ubuntu.com/manpages/natty/man1/alsa_in.1.html](http://manpages.ubuntu.com/manpages/natty/man1/alsa_in.1.html)

I wouldn't expect great things from a USB mic though, so you may need to bump up the latency.

---

### Post by oleink on 2011-03-28
> **cchhrriiss121212 said:**
> Jack only works with one card at a time, unless you start using alsa_in/alsa_out:
[http://manpages.ubuntu.com/manpages/natty/man1/alsa_in.1.html](http://manpages.ubuntu.com/manpages/natty/man1/alsa_in.1.html)

I wouldn't expect great things from a USB mic though, so you may need to bump up the latency.

USB mic im getting 8.7 latency.  Pretty good and the sq is good enough until i can afford the mic i want (its about 2.5k used)  I managed to get the usb mic to work with a usb interface as the output without changing any settings.  I'd like to get my pci card involved so I'll take a look at those pages.

---


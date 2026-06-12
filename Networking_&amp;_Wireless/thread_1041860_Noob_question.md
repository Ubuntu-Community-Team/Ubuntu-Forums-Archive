---
title: "Noob question"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by joelwhrs on 2009-01-17
i am running ubuntu 8.1 and have a dell inspirion e1505 and have been trying to set up a dial up internet connection so that i can install some programs and codecs because. without any internet connection ubuntu is kind of useless to me. i have been doing as much research as i could to get it to work but am still stuck. i am trying to connect with aol or a verizon wireless blackberry curve. i will attach the txt file of  the modem data. thanks alot.

---

### Post by ieee488 on 2009-01-17
Do not keep starting a new post for the same problem.
When you reply to your own post, it will automatically bump it up to the top of the forum again.

It looks like to me you have a softmodem with Conexant chipset.
[www.linuxant.com]("http://www.linuxant.com")
You'll have to pay for drivers faster than 14.4 is what I have read on here.

Even if you get your modem working in Linux, connecting to AOL using dialup is not easy to do and requires even more work.

As for tethering your Blackberry, Google brings up
[http://henry.sage-vision.com/blog/2008/10/25/ubuntu-blackberry-tether/](http://henry.sage-vision.com/blog/2008/10/25/ubuntu-blackberry-tether/)

---

### Post by Iowan on 2009-01-17
[Here]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer") is a help page for dial-up. A Google search for "help.ubuntu.com dial-up" revealed a couple more that may be of interest.

---

### Post by joelwhrs on 2009-01-17
What dialup service is easiest to use with linux? And is it possible to use a blackberry with it?

---

### Post by joelwhrs on 2009-01-17
Ok i tried downloading and installing the files but when i try to install it it tries to connect to the internet to download something but i am obviously not connected to the internet. Is there something that i am doing wrong or what?

---

### Post by ieee488 on 2009-01-17
I have no experience with that type of modem since my modem works with what was installed with Ubuntu from the CD. I did not have to install anything else to get it to work.

I don't have a Blackberry. Did you read the linked page?

I know that AT&T Worldnet works with Linux, but you have to get your modem working first.

If I were you, I'd either buy a truly Linux-compatible PCI modem and they can be found cheap on eBay starting at $0.99 or by an external modem to connect up to your serial/COM port.

---

### Post by joelwhrs on 2009-01-17
Yea i read all the linked pages but i cant get my modem drivers installed so i cant do anything else until that works :(( Do those modems work with a laptop or not?

---

### Post by ieee488 on 2009-01-17
Sorry, about that, I forgot that you have a laptop. 

The Inspiron e1505 has the newer ExpressCard slot instead of the PCMCIA card slot so the PCMCIA card modems that do work with Linux you can't use. And your laptop has no serial port, so an external modem is also out of the question.

I'm afraid that you are out of luck if you can't get the internal modem to work.

You'll have to find a way to get the drivers onto a flash drive at a different computer and take it to your Inspiron to use.

---


---
title: "black screen after dual monitor attempt"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by 1yen on 2007-12-02
Hello,

I am new to ubuntu, so imagine I will be making many mistakes...so here is my first big one (that I cant figure out)...

some info:
fresh install of ubuntu 7.10
graphics card: ati radeon 9800 pro

what I was trying to do:
I wanted to make my hdtv a second monitor.  In windows, this is easy to do...I have a dvi-component video converter.
I followed the  HOWTO: Install the ATI driver on ANY stable version of Ubuntu to set up dual head.  Then I went to Screen&Graphics, and selected my second monitor to be a widescrean TV (phillips), but I could not set the resolution.  After rebooting, I see the ubuntu bootup screen, but then everything goes black, both monitors (although the tv doesn not seem to receive a real signal).  I cant log on because I can:t see anything...

any ideas??

much thanks...

dan

---

### Post by d3ni5 on 2007-12-03
same situtation with ati 9600 xt and ubuntu gutsy.

my ati9600 card has 2 output - vga for lcd monitor and dvi for panasonic plasma.

with fglrx proprietary driver - system is unstable and very often gives me a black screen even without option to switch to terminal (ctrl+alt+f1 etc...). so i have to boot in safe mode and fix my /etc/X11/xorg.conf manually to switch off fglrx driver. By the way, with only one screen attached it seems to work fine.


with ati open source driver system starts with 2 monitors.

---


---
title: "XAWT not working after Suspend?!"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by LFS-Nr-3305 on 2007-07-01
Hi,

For about 4 years, I have watched TV with my Hauppauge Win-TV Go and xawtv, on an debian-based system with kernel 2.4. It was working very good and has become part of my home office organisation - for example, watch weather forecast if internet is down, or watch local news on cable. Even if I were willing to afford a separate TV set, there would be no room for it.

Furthermore, I am accustomed to working with my PC any time. As energy cost amounts to surprising amounts, I am using suspend mode ("apm -s") between sessions. If I get a call from a customer, for example, I might just re-animate my PC; can't afford to wait for booting.

Now I changed to Kubuntu 7.04 and installed xawtv. (The following problem is the *same* with kdetv and motv!).
Everything is fine if I start xawtv the first time after booting.

But after using suspend mode, I only can hear the audio from the tv station. The screen is staying black, or has one funny color, or has two funny colors, one at the top and one at the bottom.

This is the same if I finished xawtv before suspend or if I leave it running and type "apm -s" on a console.

There is no difference if I start xawtv as root from a console or if I start any tv software from the KDE menu.

I am sure it is no xawtv programming bug, because it's working after boot ... but only until next suspend. I am sure it is no (K)ubuntu bug but it might has to do with the way the the x server is set up. Searchfunction in this forum did not bring a solution. But I need my pc for working and, as I have stated above, it would be a big loss for me not to be able to use it for TV also.

Question: what is (K)ubuntu starting on boot to enable xawtv, which should be re-started after suspend.

The log states the following:

eb@TOWER:~$ tail -f /var/log/messages
Jul  1 10:07:10 TOWER kernel: [86351.412000] bttv0: SCERR @ 1825d000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul  1 10:07:10 TOWER kernel: [86351.572000] bttv0: SCERR @ 1825d000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul  1 10:07:11 TOWER kernel: [86351.692000] bttv0: timeout: drop=0 irq=65866/276897, risc=1825d000, bits: VSYNC HSYNC OFLOW FBUS
Jul  1 10:07:11 TOWER kernel: [86351.776000] bttv0: reset, reinitialize
Jul  1 10:07:11 TOWER kernel: [86351.776000] bttv0: PLL: 28636363 => 35468950 . ok
Jul  1 10:07:11 TOWER kernel: [86351.892000] bttv0: SCERR @ 1825d000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul  1 10:07:11 TOWER kernel: [86352.052000] bttv0: SCERR @ 1825d000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul  1 10:07:11 TOWER kernel: [86352.212000] bttv0: SCERR @ 1825d000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul  1 10:07:11 TOWER kernel: [86352.300000] bttv0: timeout: drop=0 irq=65871/276902, risc=1825d000, bits: VSYNC HSYNC OFLOW FBUS

I tried fbtv but it's not working either, and I am not experienced enough to make framebuffer work, even though I had no problems using it in previous installations like Debian or even Linux from Scratch (I tried by appending vga=0x314 in /boot/grub/menu.list).

The error message is:
root@TOWER:~# fbtv
can't find console font file
unable to open server "unix/:7100"
no font available

Regards, Hannes

---


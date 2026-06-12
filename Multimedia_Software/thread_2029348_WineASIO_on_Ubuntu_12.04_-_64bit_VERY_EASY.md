---
title: "WineASIO on Ubuntu 12.04 - 64bit VERY EASY"
date: 2012-07-19
forum: Multimedia Software
---

### Post by mensur87 on 2012-07-19
Hello, I want to share my results how I got working Reaper with wineasio on 64bit Ubuntu 12.04 in couple easy steps:
1.sudo apt-get -y install wine wine-dev libjack0:i386 \qjackctl build-essential
2.WINEARCH=win32 winecfg - after instaling wine
3.Install WineAsio_Ubuntu_12.04_x64.deb which is in Wineasio.zip
4.regsvr32 wineasio.dll
5.Install 32Bit Reaper
6.Start QjackCtl and change interface to your soundcard(in my case M-Audio Audiophile 192 as default),and turn off Realtime in parameters).
7.Start Jack and stop.
8.Start Reaper and chose WineASIO drivers.

I hope in near future we'll have 64bit wineasio drivers.

[IMG]http://img254.imageshack.us/img254/1972/reaperm.png[/IMG]

---

### Post by Wrictu on 2012-07-20
Oh my goodness! an incredible article dude. Thanks However I'm experiencing situation with ur rss . Don’t know why Unable to subscribe to it. Is there anybody getting similar rss downside? Anyone who knows kindly respond. Thnkx

---

### Post by psychok7 on 2012-09-25
NICE ONE!! can i get my windows plugins working there also? or i would have to reinstall them all in wine? (if possible)

---

### Post by NodeEndo on 2012-12-20
:KS
For anyone still having trouble installing and configuring WineASIO 0.9.0 with Wine 1.5 on Ubuntu 12.10 (amd64), I've started a dedicated blog on blogger.com to host a complete tutorial that I've written on how to accomplish this. 
*Tell me what you think, feedback on my blog will be very much appreciated.
-Enjoy!
[http://linuxmusiciansunite.blogspot.com/](http://linuxmusiciansunite.blogspot.com/)

---

### Post by DaniRancid on 2013-01-24
Hi,
any suggestions on how to comply this on 32 bit Ubuntu Quantal Quetzal? I tried several time following every guide, but I continue to get the same message: Failed to load DLL wineasio.dll
It's gettin me mad. Any ideas? I even tried to copy/paste the precompiled wineasio.dll into my wine folder and then give the command regsvr etc, but nothing happened...

---

### Post by tarik2cyprian on 2013-03-13
I found a 64 bit driver for wineasio and installed it but when I open up terminal and enter command regsvr32 wineasio.dll it does not
register the 64-bit wineasio driver. Is there another command to use for 64-bit?

---

### Post by HarryUP on 2013-04-12
> **tarik2cyprian said:**
> Is there another command to use for 64-bit?
```
wine64 regsvr32 wineasio.dll
```

---

### Post by chillinchill on 2013-08-09
Hello i m new to linux world and tryin to reduce my latency on Ableton live which i installed through playonlinux; i followed all the steps you wrote, but i don' t have any external audio interface yet; In Jack, i didn t find the realtime parameters and when i tried to start it, that said 

JACK is running in realtime mode, but you are not allowed to use realtime scheduling.Please check your /etc/security/limits.conf for the following line
and correct/add it if necessary:
  @audio          -       rtprio          99
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
[COLOR=#999999]17:16:52.147 JACK a été arrêté avec statut de sortie=255

[/COLOR]The only thing that ableton proposes is MME direct x, i don' t know if you can help me or if my knowledge is too limited for that but i  would love to reduce my latency in order to play live on Live....Thanks

---

### Post by tj-201 on 2014-03-29
Thanks a bunch, but to get jack started, I had to disable pulseaudio.

---

### Post by lowdx1 on 2014-07-27
omg worked great. thank you very much!

---

### Post by osirisgothra on 2015-06-01
I can verify that this works also for 15.04 with some very minor alterations

---


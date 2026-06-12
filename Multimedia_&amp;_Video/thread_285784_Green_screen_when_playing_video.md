---
title: "Green screen when playing video"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by jb007 on 2006-10-27
My first post!:)
Just installed edgy 6.10 today. I'm running on a VIA SP13000 MB with VIA CN400 Unichrome Pro video. Playing any video ie avi mpg's xvid's etc using gxine totem etc, I get no video just sound, and a green area where the video should be. Any ideas?](*,)

---

### Post by handy on 2006-10-28
Welcome... :KS 

You have come in right at the beginning of a *development release*, when everything is at its buggiest & most unknown! 

So be careful how you judge Ubuntu.   If you have instability problems you may be better off using the Dapper LTS (long term support) stable release.  Or even dual booting with Dapper & Edgy.

Anyhow have fun with it all. :)  

I think that Totem has a bug in it which ***may*** be responsible for your troubles.

[http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364)

Have a look at [*_**Automatix2**_*]("http://www.getautomatix.com/"), it is what I use after a clean install.

Automatix will give you the option to install codecs & libraries so you can access multimedia that you would other wise be unable to, due to US legalities, this in itself may be your problem.
 
All the best! :D

---

### Post by jb007 on 2006-10-28
Thanks for the reply. I did use Automatix2 to load all the codecs etc, but no go. What did fix it was changing the line from libXvMC.so.1 to libXvMCPro.so.1 in the file /etc/X11/XvMCConfig! Go figure! Now to fix the broken USB Wireless, and lirc...

---


---
title: "Some genreal iPod questions"
date: 2008-05-08
forum: Multimedia Software
---

### Post by employeeno5 on 2008-05-08
Currently using Hardy Heron.

So I have a 5G Ipod Video that works great.

I've been using it successfully with Ubuntu for 6 months now. 

There are a couple small issues though that I never worked out and today I'm wondering if anyone here can help me out.

Rhythmbox does not transfer album artwork to my ipod. Or rather, it does, but only for the first track on an album, not every track. That also isn't consistent. Sometimes I just don't get any artwork.

Is this a normal problem or something that can be fixed?

Next, due to album artwork being important to me, I usually use Amarok for my ipod management as it's always done a perfect job in the album art department. It's a great player with lots of great features, but I usually prefer the simplicity of Rythmbox and the speed boost of using a native GTK app.

However, if I am using Amarok for it's album art support or another one it's great features, I would like to be able to correctly remove my ipod.

I've searched and found several forum and blog posts with several different commands claiming to be what you should put in to correctly eject your ipod in GNOME. However, none of them have worked for me. Granted most of them seemed rather old and were referring to older releases of Ubuntu/GNOME. 

Does anyone know a correct sequence of commands to put into your ipod settings in Amarok that will eject an ipod correctly in Hardy?

One last thing. If I want to change my default app to open when an iPod is plugged in, I no longer know where to do that in Hardy. I used to know how to do it in Gutsy but that option appears to have been moved or removed. 

Just some random questions that have been on my mind. If anyone has any advice on any of them, that's fantastic. If not, no biggie. Me and iPod management are still getting by just fine. 

Thanks!

---

### Post by soxs on 2008-05-10
Will eject the iPod and remove any possible querk(for gnome):
```
rm %m/iPod_Control/iTunes/iTunesLock;rm "%m/iPod_Control/iTunes/Play Counts";gnome-eject -t -d %d 
```
[http://ubuntuforums.org/showthread.php?t=497201&highlight=iPod+gnome+eject](http://ubuntuforums.org/showthread.php?t=497201&highlight=iPod+gnome+eject)

Standard Launch App on iPod connect:
Open a nautilus window.
Goto: Edit -> Preferences -> Last Tab (don't know proper name, running a german localized box)

---

### Post by Jordinho on 2008-05-10
That all worked for me (the last tab is media by the way). The only problem is that under "Music Player" I cannot choose Amarok, only Rhythmbox or the option "ask what to do".

---

### Post by soxs on 2008-05-11
You are rigth, there is atm no option to choose Amrok or exaile (I have those 2 installed). Odd.

---


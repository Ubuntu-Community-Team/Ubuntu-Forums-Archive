---
title: "Very choppy 3D graphics"
date: 2010-05-15
forum: Multimedia Software
---

### Post by Krsnajinana on 2010-05-15
Hi,

I've been browsing through the forums and tried several things, but I haven't found a solution to my problem yet. I have an Acer Aspire 5520 laptop, with an NVIDIA GeForce 7000 M graphics card. For a year I've been using Ubuntu, and with all the versions I've had, through Gutsy to Lynx, I've always found that 3D graphics are extremely choppy. I wouldn't say they are slow...it's more like they move for a couple of seconds, then stop, then move again, then stop. I didn't really care, because I hardly play games: I had initially noticed it trying to get Warcraft 3 to work on Wine, which obviously is an old game, and it runs perfectly on windows...I thought it was just a problem of Wine. But now I've installed Celestia and Flightgear, and with both of them I have this same problem. Flightgear is the worst, it's basically unusable.

I have done several things based upon what I read in the forums. I removed all the NVIDIA drivers, and manually installed the latest propietary driver 195.36.24. I turned off all my desktop effects. I turned on Sync to Vblank to see what would happen. The desktop itself runs very quickly, even the Desktop cube effect, if I turn it on. Like I said before, the problem seems to be this jerkiness with games, with Celestia, and with flightgear.

Please help!!! If I get this working, then I'll actually have Ubuntu working completely perfectly, for the FIRST TIME!!! :P

---

### Post by Krsnajinana on 2010-05-18
BUMP!!!

I haven't had any luck. On the forums, I sometimes see people talking about the NVIDIA splash screen. I never see it when I log in, I don't know if it just passes too quickly for me to see, or if it means something is wrong with the drivers. But then, like I said before, my 3D desktop effects are working perfectly. It's when I try and run Flightgear or a game on Wine that I get jerkiness.

Also, I noticed just now, I don't know if it's related, that video playback can be jerky too. I was watching a film in movie player, and a couple of times the image stayed still, with the sound still going, and then the image came back in sync. And sometimes Youtube can be quite jerky too, a similar issue, although not all the time.

I don't know if they are all related or not. Will some nice person please help me?

---

### Post by jkxx on 2010-05-18
Having used both Ubuntu and Kubuntu (10.04) I discovered that only Kubuntu is good enough for multimedia on my system, which is also based on an Nvidia card (GeForce 8800) with Nvidia's drivers.

Upon installing Ubuntu I was presented with choppy graphics and really poor video playback quality which would not be fixed by any means (I also found out Gnome just ignores various changes you make though this is not related to your inquiry..)

So here is the setup I'm using which does handle graphics great, along with 3D games and playback:

- get Kubuntu and use KDE with its own Kwin compositing engine, you can set it up any way you like, including with GTK+ widgets so your apps look as if they were all Gnome apps.

- make sure you disable Compiz as the current version will cause problems, Kwin will give you all the effects you want

- disable and remove Pulseaudio if you will be playing any games or experience lagginess. Several of my game emulators were struggling to get 15-20 fps but got to 60 fps once Pulse was gone.

...and that's really it, now you have a very modern, very responsive system. :)

---

### Post by wiebeest on 2010-05-18
> **jkxx said:**
> Having used both Ubuntu and Kubuntu (10.04) I discovered that only Kubuntu is good enough for multimedia on my system, which is also based on an Nvidia card (GeForce 8800) with Nvidia's drivers.

That's funny and quite in contradiction with Phoronix's findings: [http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1")
But then again, I'm a lot of time surprised by the different experiences with (K)Ubuntu between users.

---

### Post by Krsnajinana on 2010-05-22
Well, thanks for the suggestions....perhaps I can try Kubuntu on another partition to see if it works better, because I finally had everything working like I wanted in Ubuntu...or at least I did!!! It seems like after the last update, all my sound has gone away, and Alsamixer has disappeared!!! Ah well, it was nice while it lasted...back to the forums to sort it out....

---


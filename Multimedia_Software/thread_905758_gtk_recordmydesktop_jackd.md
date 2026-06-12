---
title: "gtk recordmydesktop jackd"
date: 2008-08-30
forum: Multimedia Software
---

### Post by Master-of-None on 2008-08-30
When trying to record my desktop with sound, it gives me an error numbered "768" and says "could not open/configure soundcard" WITHOUT jackd.

It says in the sound pannel in the advanced options that "jacklsp returned no channels, make sure jackd is running" to which, typing in "jackd" in the terminal brings up a set of options(which makes me believe jackd is running) And gives me an "exited with status 256 error while parsing the arguments"

When I open the program in the terminal, no additional information comes up, so I don't know what to do to remedy this.

Help?

---

### Post by Master-of-None on 2008-08-31
bump

---

### Post by lvlo on 2008-09-01
Try to use Qjackctl (user interface for controlling the JACK sound server). I've used GtkRecordMyDesktop with Qjackctl and have no problem :)

To install run in terminal:
```
sudo apt-get install qjackctl
```

---

### Post by Master-of-None on 2008-09-03
Now I got this error:

```
recordMyDesktop has exited with status: 3584
Description:Cannot load the Jack library(dlopen/dlsym error on libjack.so
```

---

### Post by lvlo on 2008-09-03
Does Jack server start when you use Qjackctl?

Also you can do this:
1. Reinstall "jackd" package via Synaptic.
2. Install new version GtkRecordMyDesktop from [GetDeb.net]("http://www.getdeb.net/app/RecordMyDesktop")

---

### Post by lvlo on 2008-09-03
> **lvlo said:**
> Does Jack server start when you use Qjackctl?

Also you can do this:
1. Reinstall "jackd" package via Synaptic.
2. Install new version GtkRecordMyDesktop from [GetDeb.net]("http://www.getdeb.net/app/RecordMyDesktop")

Sorry, my bad: I just run GtkRecordMyDesktop and have the same error.

Here several links that give you right direction:

1. [pulseaudio-module-jack package]("http://debian.fastbull.org/pool/main/p/pulseaudio/") - you need install it to use Jack and Pulse Audio together.

2. [Howto: Route all sound to Jack via Pulse Audio in Feisty (finally EQ in all audio!)]("http://ubuntuforums.org/showthread.php?t=548178&page=2")

3. [Jack with Pulse Audio]("https://tango.0pointer.de/pipermail/pulseaudio-discuss/2007-March/000330.html")

The last 2 link is very similar. I've tested methods - it seems work fine. 

Good luck :)

---

### Post by Master-of-None on 2008-09-05
Those options don't work for me, and installing the package you told me to still produces the same error in GTK-RMD.

---

### Post by eyax on 2009-04-20
> **Master-of-None said:**
> Now I got this error:

```
recordMyDesktop has exited with status: 3584
Description:Cannot load the Jack library(dlopen/dlsym error on libjack.so
```

Hi,
find your libjack whith running this command in terminal
ls -l /usr/lib/libjack*

and after create a soft-link named libjack.so that point to your libjack.so.x.xx.etc location.

This command solve for me (ubuntu8.10)
sudo ln -s /usr/lib/libjack.so.0.0.28 /usr/lib/libjack.so
--
Lazzaro

---

### Post by markbuntu on 2009-04-20
Go here

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

---


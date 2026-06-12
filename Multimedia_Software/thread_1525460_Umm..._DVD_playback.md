---
title: "Umm... DVD playback?"
date: 2010-07-06
forum: Multimedia Software
---

### Post by uRabbit on 2010-07-06
Ugh... So I have to add "packages" to watch DVD's? What? Someone said to just try VLC Player (which I use on XP), but that requires some weird stuff too.

What the hell do I do? :popcorn:

---

### Post by hansdown on 2010-07-06
Welcome to the forum, uRabbit.

You need to install a few things for dvd.

Click system> administration> synaptic package manager.

Search for, and install these.

```
ubuntu-restricted-extras
```

```
libdvdcss2
```

```
gstreamer0.10-ffmpeg
```

```
gstreamer0.10-plugins-ugly
```

```
gstreamer0.10-plugins-bad
```

```
libdvdread3
```

---

### Post by WinterRain on 2010-07-06
> **hansdown said:**
> Welcome to the forum, uRabbit.

You need to install a few things for dvd.


```
libdvdcss2
```



You need the medibuntu repos before you can download libdvdcss2.

Just do (you can copy and paste):
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by hansdown on 2010-07-06
Thanks WinterRain.

I completely missed that.

---

### Post by uRabbit on 2010-07-06
> **hansdown said:**
> ```
libdvdread3
```

libdvdread4 was available. No '3'. So I opted for that one. 

Winter, where do I paste those?

I'm downloading 68 files associated with those that hansdown mentioned. When I clicked one, it listed files that needed to be downloaded with it.

---

### Post by hansdown on 2010-07-06
Copy and paste WinterRain's command in the terminal.

Click applications> accessories> terminal.

---

### Post by uRabbit on 2010-07-06
Awesome. Got that going. Was about to try to use Software Sources to do so. 

Is it okay that I installed those after your suggestions, hansdown?

edit: Yup, it worked. :)

Love this forum already. And Ubuntu. Now I just gotta get The Sims 3 running (if possible). :)

---

### Post by hansdown on 2010-07-06
For Sims 3, go to synaptic package manager, and install 

```
playonlinux
```


Here's a good read.

[http://www.hardestlevel.com/705818753/sims-3-on-ubuntu-linux/](http://www.hardestlevel.com/705818753/sims-3-on-ubuntu-linux/)

---

### Post by uRabbit on 2010-07-06
> **hansdown said:**
> For Sims 3, go to synaptic package manager, and install 

```
playonlinux
```
Here's a good read.

[http://www.hardestlevel.com/705818753/sims-3-on-ubuntu-linux/](http://www.hardestlevel.com/705818753/sims-3-on-ubuntu-linux/)

Got that downloaded. Can't open Sims3 installer.

How do I do it?

---


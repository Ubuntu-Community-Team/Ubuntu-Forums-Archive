---
title: "Can not play DVD"
date: 2008-12-27
forum: Multimedia Software
---

### Post by dphoenixa on 2008-12-27
I figured it would start up right away...of course can't be that easy. So I did some research installed libdvdread3 and the css.sh command, the ubuntu restricted extras, as well as w32codecs and everything else you can find on the internet for anytype of getting it to play. I also tryed many different players such as Totem, Gnixe, VLC....ect.  They either freeze or see the movie put 2hrs on the counter and then go back as if i never even loaded to that player.

I am trying to watch Iron Man on my laptop, but it's seems that it just won't work. Little help would be nice.

---

### Post by 2hot6ft2 on 2008-12-27
Maybe this will help
> **Toshibawarrior said:**
> Then for playback type this on a terminal:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```

These lackages are also necessary...:) Hope this helps!

---

### Post by dphoenixa on 2008-12-27
It has already been installed, I just put int totem (xine) and it's saying it's encrypted and I am trying to watch it without libdvdcss even though like I said it's already installed. All the other players are still doing the same thing.

Thanks for the help, but it didn't work.

---

### Post by 2hot6ft2 on 2008-12-27
My old laptop wouldn't read HD DVD's but standard ones worked fine. Maybe you'll fine something useful here then [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Come to think of it Iron Man was the one it wouldn't read. Tried it at my brothers before giving him that laptop.

---

### Post by MarblePanther on 2008-12-27
Try installing libdvdnav4 from the repos

Also I find Kaffeine to be the best at DVDs, idk just a preference

---

### Post by dphoenixa on 2008-12-27
Good advice, but I have that installed already. I doubt it's just the player I haven't tried kaffeine since 7.10, but I'll give it another go.

---

### Post by MarblePanther on 2008-12-27
Is the DVD standard definition?  Is the region the same as your device?

---

### Post by dphoenixa on 2008-12-27
that thread 2hot did not help. Sadly :(

I am not sure if it's standard or not. I would believe so and I would have to believe it's the same region.

---

### Post by mc4man on 2008-12-27
Do you know if a region has been set on the drive? (if you ever played a commercial dvd movie in windows on your laptop it would have been.

If your not sure 
```
sudo apt-get install regionset
```

Then with a disk in the drive run from terminal
```
regionset
```
ck. on line 4 to see if it says 'set'

If it was set start vlc from a terminal, open the disk and post errors if any.

What release of ubuntu are you using?

---

### Post by dphoenixa on 2008-12-27
I am not quite sure what region to set it to.

---

### Post by dannytatom on 2008-12-27
When I try and install libdvdcss4 I get

```

Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

---

### Post by ultima on 2008-12-27
[QUOTE=MarblePanther;6445795]Try installing libdvdnav4 from the repos

This may seem strange but I would suggest removing libdvdnav4

It's been nothing but trouble for me. I had heaps of problems playing dvds on Intrepid, they would mount but not play. Every time I remove libdvdnav4 everything works fine and everytime it's installed with another media program. No more DVD playback.

---

### Post by ultima on 2008-12-27
You can install libdvdcss2 by running

sudo /usr/share/doc/libdvdread3/install-css.sh

---


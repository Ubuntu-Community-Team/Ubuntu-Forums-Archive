---
title: "Unable to play dvd in Jaunty"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Jacroe on 2009-05-08
I put in a dvd and tell the dialog box that pops up to play it in totem. Totem opens, waits a second, then closes. What's up?

---

### Post by khelben1979 on 2009-05-08
My guess is that your system is lacking the [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") library.

Also try and opening DVD through the VLC program to see if it gives you the same result.

```
sudo apt-get install vlc
```
if it's not in the system already.

Also, adding the [medibuntu]("http://en.wikipedia.org/wiki/Medibuntu") to your sources.list file will also be something you'll want to do.

---

### Post by VMC on 2009-05-08
> **Jacroe said:**
> I put in a dvd and tell the dialog box that pops up to play it in totem. Totem opens, waits a second, then closes. What's up?

Type the following:
```
lspci -nn | grep VGA
```

If it's an Intel chip then follow one of the stickies on this forum.

---

### Post by Jacroe on 2009-05-08
```
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7000M (rev a2) [10de:0533] (rev a2)
```

looks like nVidia from my unexperienced eyes. ;)

---

### Post by axel206 on 2009-05-09
Check this:

[Ubuntu 9.04 Post Installation Guide](http://www.my-guides.net/en/content/view/158/26/)

---

### Post by Jacroe on 2009-05-09
> **axel206 said:**
> Check this:

[Ubuntu 9.04 Post Installation Guide](http://www.my-guides.net/en/content/view/158/26/)

I've already checked that. It didn't help a bit.

---

### Post by xc3RnbFO8P on 2009-05-09
Try this:
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

---

### Post by Jacroe on 2009-05-09
Thanks. That worked!

---

### Post by emeraldgirl08 on 2009-06-07
> **Ringi said:**
> Try this:
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

Thanks Ringi!!!

---

### Post by garethfoxwilliams on 2009-06-11
Thanks! That worked for me too. Given I had already installed some of the dependencies, did this work because things were done in the right order, or might I just have been missing one vital link? 
Why would the distro not have these apparently essential elements to make the DVD work 'out of the box' as one might expect with a user-friendly distro?

As a linux noob, I am intrigued as to where you obtained such wisdom and knowledge??

Gareth

---

### Post by skydiving85 on 2009-06-13
That did not work for me any suggestions?

---

### Post by bebops_lost on 2009-08-20
> Try this:
[http://ubuntuforums.org/showpost.php...10&postcount=5](http://ubuntuforums.org/showpost.php...10&postcount=5)

Thanks Ringi 
worked like a charm! (for me at least, good luck everyone else.)

---


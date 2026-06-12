---
title: "Stupid video players are not working!!"
date: 2010-07-30
forum: Multimedia Software
---

### Post by lukeiscool on 2010-07-30
I am trying to run a DVD and absolutly NO video player is playing then. I'm damn sick of ubuntu because it always does something like this to me!!

---

### Post by jerenept on 2010-07-30
Applications>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

then enter password

```
sudo bash /usr/share/doc/libdvdread4/install-css.sh
```

PS you need a working internet connection

---

### Post by kerry_s on 2010-07-30
> **lukeiscool said:**
> I am trying to run a DVD and absolutly NO video player is playing then. I'm damn sick of ubuntu because it always does something like this to me!!


come on, use the honey, you'll catch more with the right bait.

you need to add the medi repos & install libdvdcss2.

go to accessories-> terminal

for the repo copy & paste:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

you can use synaptic gui after that.

install all these, to cover all media:

libdvdcss2
w32codecs
ubuntu-restricted-extras

---

### Post by ActionParsnip on 2010-07-30
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Did you even read that??

---

### Post by NFblaze on 2010-07-30
> **ActionParsnip said:**
> [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Did you even read that??

Hah! Of course not.

Hey, if Ubuntu always "does this to you". Make a break for it back to Windows. You might not be cut out for Ubuntu, yet.

---

### Post by frogo on 2010-07-30
> **lukeiscool said:**
> I am trying to run a DVD and absolutly NO video player is playing then. I'm damn sick of ubuntu because it always does something like this to me!!

a useful thread and a subject that has the merit of sweeping large, but you're not alone if that's a recomfort

I could play some dvds with Movie Player in ubuntu 10.04. But lately most returned errors. Tried Gnome Mplayer and also VLC. The first two detect the tracks but no more, VLC opens folders whatever I ask it to do...

Solutions along the lines of #2, #3 and #4 provided a partial fix. I've used only one DVD to try out but that one only played to a point in Media Player and then got stuck on the title page and I lost the mouse. GNome Player was far worst, the image was all scrambled and anything else froze after a few secs. I was not patient enough to see whether it'd magically go away without a hard reboot. I've uninstalled and haven't reinstalled VLC, but that's just because I got annoyed with something about accessing the Web for finding art work or whatever. 

I've looked at a lot of threads and some documentation. Something must escape me or it's just too much to digest. But there's progress overall... Fortunately I have other means of playing DVDs, just not on the ubuntu box at the moment. So solution #5 indeed does work.

---


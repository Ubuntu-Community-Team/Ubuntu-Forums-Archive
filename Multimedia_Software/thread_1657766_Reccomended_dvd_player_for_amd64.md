---
title: "Reccomended dvd player for amd64 ?"
date: 2011-01-01
forum: Multimedia Software
---

### Post by grey1beard on 2011-01-01
I am trying to set ubuntu10.10 to play commercial dvds etc.
When the movie player opened, is said I need to install "the appropriate plugins" .
The link takes me to the gstreamer site, but there's no indication of what plugins I need.
Synaptic lists many packages, some installed, some not.

I'd be most grateful if someone could tell me which I'm likely to need, first for UK sold commercial dvds, and secondly for showing slideshows created in windows using "Proshow_DVD"(brother-in-law's Christmas creation!)

John
EDIT
I've just installed Tweak.

---

### Post by solar george on 2011-01-01
AFAIK Using tweak is not recommended by the ubuntu devs, you can get everything you need for dvds and other media from [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by grey1beard on 2011-01-01
Thanks for the link, solar george.
Would you recommend I download the whole medibuntu repository ?
Being a old newbie, I have a bit of a problem taking all the variations on that page in !
Many thanks
John

---

### Post by davec64 on 2011-01-01
Hi,

you just need to install the LIBDVDCSS2 package. This package contains the necessary code to un-encrypt commercial DVD's to allow you to play them on your computer. Unfortunately this package isn't included in default installations due to licensing issues.

---

### Post by solar george on 2011-01-01
You'll want to run the following commands in a terminal (copy and paste);
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```
which that will make the software centre aware of the medibuntu repo (so that it will offer you applications from there and display updates in the update manager)

To play dvds you probably only need [libdvdcss2]("apt://libdvdcss2") (click on the link when you've run the above commands to launch the package installer) though I personally prefer to use [vlc]("apt://vlc") rather than ubuntu's default media player.

---

### Post by grey1beard on 2011-01-01
Thanks Dave. I was hoping it might be as simple as that.
I'll sort out the brother-in-law's slideshow later, if need be !!!

John

Thanks Solar george. I'll try the simple package first, then go the whole hog if it proves to be necessary.
Anything for the simple life. :)
I notice many people seem to prefer vlc - any particular reason for you ?

---

### Post by davec64 on 2011-01-02
I too like VLC i also like SMPlayer. Out of the box both will play just about any file you can download from the internet without having to tinker with additional plugins etc! :)

---

### Post by grey1beard on 2011-01-02
THanks Dave and solar george.
I now have vlc running happily, not only on this 64 bit desktop, but also on my wife's 32 bit laptop.

Happy New Year both, and on to the next problem !! :)

---


---
title: "can't see video files"
date: 2009-07-24
forum: Multimedia Software
---

### Post by lavikl on 2009-07-24
Hey everybody
I've just installed Xubuntu 9.04 on an old Dell latitude D500.
I've also installed Gstream codec pack.
I'm trying to view some mpeg files and all I get is sound with no video...
one more thing, I suspect that the slow performances of the window manager (opening folders, starting up etc.) has to do with something mis-configured, I don't want to believe that Xubuntu is slower than winXP on this computer...
Any kind of help will be very appericiated !

Adi

---

### Post by pro003 on 2009-07-24
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by lavikl on 2009-07-24
Thanks pro003...
I'm trying it now.

Do you have any suggestions on how to improve the overall performances such as loading the softwares more quickly (even calculator takes too much time) ?

---

### Post by lavikl on 2009-07-24
Nope didn't work.
I did all the apt-get  that were suggested, I still get sound with no video.
I should mention that I can see video (jumpy and still video) through the net such as youtube, so I guess it has to do with codecs issue. still I can't figure it out. any other suggestions ? please?

---

### Post by pro003 on 2009-07-25
> **lavikl said:**
> Nope didn't work.
I did all the apt-get  that were suggested, I still get sound with no video.
I should mention that I can see video (jumpy and still video) through the net such as youtube, so I guess it has to do with codecs issue. still I can't figure it out. any other suggestions ? please?

I once had to install intel graphic driver in ubuntu and I followed [this page]("http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/"), it may help you so go [try it]("http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/")

Overall performance, that's a kinda tricky question in ubuntu, I have my own ways of tweaking, let's say you take out some startup points in System > Preferences > Startup Applications, you get [Ubuntu Tweak]("http://ubuntu-tweak.com/downloads") and it can do some thing for you, all in all man you gotta check that by yourself, and sometime look at forums such this one find some nice worthy threads and that's how I did it and I'm [still doing it]("http://img265.imageshack.us/img265/4302/screenshotrad.png")...

---


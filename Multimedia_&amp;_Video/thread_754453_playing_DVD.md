---
title: "playing DVD"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by X_CheshireCat_x on 2008-04-13
i wanted to watch a dvd so searched the forums and found the following codes which claimed to allow me to do so:




sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdcss2

sudo apt-get install w32codecs

sudo apt-get install vlc






i have entered all of these code into the terminal

the result is that totem wont open and VLC plays white noise with no video....

---

### Post by X_CheshireCat_x on 2008-04-14
I uninstalled VLC then reinstalled it. Now when i play a dvd i get a picture with sound but the picture is really jumpy and stuttering...(in VLC)

---

### Post by rcatman on 2008-04-14
Check out the Ubuntu Community Documentation on installing Restricted Formats to play DVDs
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

If you're on gutsy, make sure to execute the shell script (install-css.sh) after installing the required libraries.

here's the excerpt from the how-to for gutsy users
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.

---

### Post by X_CheshireCat_x on 2008-04-15
I did as you said but after i enter the 2nd command i get:

sudo: /usr/share/doc/libdvdread3/install-css.: command not found

i have also installed xine. 
xine, vlc and totem wont play dvds either...

---

### Post by X_CheshireCat_x on 2008-04-15
i have managed to get a picture. Are the lines across the screen just because the codec is not as good as the ones i am use to or something changeable?

---


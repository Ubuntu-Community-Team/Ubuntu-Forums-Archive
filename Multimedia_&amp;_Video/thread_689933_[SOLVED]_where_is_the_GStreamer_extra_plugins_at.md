---
title: "[SOLVED] where is the GStreamer extra plugins at?"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by luckymoonboy1 on 2008-02-06
ok i'm trying to play a dvd but it tells me i need the GStreamer extra plugins package, i don't have internet on my ubuntu computer and i can't find it in the archives. can sombody please give me the url to get it. thankyou.

---

### Post by wolfen69 on 2008-02-06
open terminal and copy and paste:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then:
```
sudo apt-get install libdvdcss2
```

Edit: sorry, i missed the part about no internet.

---

### Post by wolfen69 on 2008-02-07
here [http://downloads.videolan.org/pub/vlc/0.8.6d/vlc-0.8.6d.tar.gz](http://downloads.videolan.org/pub/vlc/0.8.6d/vlc-0.8.6d.tar.gz) is the download for VLC player. it will play DVD's.

if you dont know how to install from tar.gz, post back.

---

### Post by luckymoonboy1 on 2008-02-07
uh i don't know how to install from a  tar.gx sorry i don't know if i should know how i'm still new at this. ;)

---

### Post by luckymoonboy1 on 2008-02-18
ok i got it. thanks.

---


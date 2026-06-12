---
title: "amorak"
date: 2008-05-13
forum: Multimedia Software
---

### Post by mithritades on 2008-05-13
when i try to play in amorak is says that decoder is not found,what decoder do i need?

---

### Post by vdawg on 2008-05-13
What kind of a file are you trying to play?

If you install the GStreamer extra plugins app, you should have everything you need. You can find it by clicking on the applications menu -> "Add/Remove" then type gstreamer in the search.

good luck!

---

### Post by mithritades on 2008-05-13
i wanted to play WMA files

---

### Post by mc4man on 2008-05-13
Try installing the w32codecs - medibuntu

---

### Post by mithritades on 2008-05-13
there's no w32(win32?)codecs on either synaptis manager or any medibuntu

---

### Post by mc4man on 2008-05-13
You should ck. admin -> software sources -> third party -> and see if you have medibuntu and if it's checked. If there update your sources
here is direct
[http://packages.medibuntu.org/pool/non-free/w/w32codecs/](http://packages.medibuntu.org/pool/non-free/w/w32codecs/)
13-oct-2007 for gutsy, 20-apr-2008 for hardy  (32 bit versions)

---

### Post by mithritades on 2008-05-14
i don't have medibuntu in my third party apps section

---

### Post by NightwishFan on 2008-05-14
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just paste the command in the terminal for your Version of Ubuntu. Then with a similar method after the first is done add the GPG key. For Hardy:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Then run:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mithritades on 2008-05-14
i am washing my hands of this amarok,it keeps saying it cannot detect a decoder...what do i need to play beep music player?

---


---
title: "DVD help"
date: 2009-10-15
forum: Multimedia Software
---

### Post by Waldvogel on 2009-10-15
I have installed Ubuntu this week and cannot play DVDs at all. I installed VLC thinking that would do the trick but it hasn't. I try to open with VLC but it doesn't.

I can play videos from an SD card and from DVD-Rs...

Vat kann I do?

---

### Post by diesch on 2009-10-15
See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Waldvogel on 2009-10-15
Danke sehr!

I understand how to open a terminal window but really have no idea how to:


'Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line'

---

### Post by diesch on 2009-10-15
Either open Synaptic (with German locals that's System&#8594;Systemverwaltung&#8594;Synaptic-Paketverwaltung), search the package **libdvdread4** and install it or type```
sudo apt-get install libdvdread4
``` at the command line.

---

### Post by ajgreeny on 2009-10-15
You probably also need libdvdcss2, which is available from medibuntu repos.

See here:  [http://www.medibuntu.org/](http://www.medibuntu.org/) for all the info you need.  They also have better versions of one or two other applications which you may wish to include after you have enabled the repos.

---

### Post by Waldvogel on 2009-10-16
I have no idea how to open Synaptic.

---

### Post by Waldvogel on 2009-10-16
I installed the 1st thing with Synaptic thanks.



 libdvdcss2?

I don't know how to install that, the instructions on medibuntu are simply gibberish to me.

---

### Post by ajgreeny on 2009-10-16
OK, go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and then copy text in the grey box into a terminal (Programs-> Accesories ->Terminal).  The text is here as well:-

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

then enter your password when asked (it will not show, but it will be entered, don't worry) and a lot of text should scroll through and then go back to your terminal prompt.  Now open synaptic again and search for upgrades or just libdvdcss2.

---

### Post by Waldvogel on 2009-10-26
I'm very grateful for the help and I have acted upon all the advice given but unfortunately the problem remains.

---

### Post by vinutux on 2009-10-26
If you install ubuntu-restricted-xtras and libdvdcss2 from medibuntu normally this thing is fixed ........ anyway try Mplayer

```
sudo apt-get install mplayer
```

---

### Post by Waldvogel on 2009-10-27
I can play DVDs now thanks and I'm using VLC.

Is there another programme recommended? The reason I ask is that VLC Is a bit dodgy towards the end of one of the DVDs (it's 3:27 long so I think it might me to do with the length).

---

### Post by vinutux on 2009-10-27
Try Mplayer or Xine

---


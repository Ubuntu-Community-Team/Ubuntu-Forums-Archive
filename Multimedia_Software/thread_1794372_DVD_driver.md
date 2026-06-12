---
title: "DVD driver"
date: 2011-06-30
forum: Multimedia Software
---

### Post by TimmyK. on 2011-06-30
I just found out to my great envy that Linux Mint plays DVDs with no problem. So I was wondering, does Ubuntu Studio do the same? And if so, can it play ''all'' DVDs like mine does, or just ones that aren't restricted?

---

### Post by Pablo_F on 2011-07-01
With regards to this question US is not different than plain ubuntu. That said, it is very easy to achieve what you want. Search the ubuntu help.

---

### Post by TimmyK. on 2011-07-01
So I have to download all those drivers and other troublesome things that only let you play old, non-restricted DVDs? And how about 64 studio, can it play DVDs out of the box?

---

### Post by TimmyK. on 2011-07-01
Hi, I've tried to get a DVD driver on this thing before, and got libdvdread4, VLC, and Ubuntu Restricted Extras. So then to my great delight I found this: [http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands](http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands). So I used the commands, and the following message came up:
```
E: Unable to locate package libxinel-ffmpeg
E: Unable to locate package libdvdread3
```
So what do I do? And which player will this let me play DVDs with, VLC?

---

### Post by wolfen69 on 2011-07-01
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
and then vlc will play dvd's.

---

### Post by TimmyK. on 2011-07-01
I want libdvdread_3_, not 4 (libdvdread4 does not allow you to play restricted DVDs). And when I typed in your command with three instead of four it told me 'Command not found'. What now?

---

### Post by cariboo on 2011-07-01
The install script in /usr/share/doc/libdvdread4 installs  libdvdcss2, I haven't had a problem playing any DVDs with it. You can't play Blu-Ray DVDs though.

---

### Post by TimmyK. on 2011-07-01
Pardon my excitement but I have to say it: **[SIZE="4"]YAHOO!!!!! I FINALLY WATCH DVDS ON HERE!!!!!!![/SIZE]** I just used the terminal command, and now it works fine! Just one last question, can I rip or copy DVDs or just watch them?

---

### Post by TimmyK. on 2011-07-02
I suppose that this question is different enough to call for a new thread. Thanks for the help with the driver!

---


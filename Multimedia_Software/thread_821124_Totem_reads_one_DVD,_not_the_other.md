---
title: "Totem reads one DVD, not the other"
date: 2008-06-06
forum: Multimedia Software
---

### Post by FiremothPilot on 2008-06-06
I have a Compaq F750 notebook with a pretty fresh installation of Hardy on board. I have one DVD that will play fine in Totem, but another DVD that seems to confuse Totem.

If I try to run the latter DVD in VLC, the program simply shutdown.

Anybody have any idea on how to fix this?!

---

### Post by mc4man on 2008-06-07
When you get the chance open vlc from the terminal, try your problem dvd and post terminal output.

---

### Post by FiremothPilot on 2008-06-07
```
$ vlc
```

returns

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BAND_BROTHERS_D3
libdvdnav: DVD Serial Number: 2d29ac12
libdvdnav: DVD Title (Alternative): BAND_OF_BROTHERS
libdvdnav: Unable to find map file '/home/gdb/.dvdnav/BAND_BROTHERS_D3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[00000283] main playlist: nothing to play
[00000283] main playlist: stopping playback
```

---

### Post by mc4man on 2008-06-07
Go here and add medibuntu repo, add repo for hardy, run the GPG key and update sources line
then install libdvdcss2
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by FiremothPilot on 2008-06-07
Works like a charm. Thanks very much.

---

### Post by mc4man on 2008-06-08
If your inclined to use totem (totem-gstreamer is the default in hardy) I'd install totem-xine and then switch the default totem to it.
```
sudo update-alternatives --config totem
``` choose option 2

---

### Post by cirorodrigues on 2008-06-08
it worked for me also. Thanks.

---


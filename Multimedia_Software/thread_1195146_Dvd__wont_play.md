---
title: "Dvd  wont play"
date: 2009-06-23
forum: Multimedia Software
---

### Post by numbness05 on 2009-06-23
Hey there.

Could any one tell me why it is that I am not able to play DVD's on my laptop any more. Yesterday my laptop refused to even boot up so I have reloaded Jaunty back on from the live CD (I was using Jaunty before)
but this time round it wont allow me to view any of my DVD's in VLC TOTEM or Mplayer???..
Here are a list of the things i am told by each media player

VLC= Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

TOTEM= An Error occured Could not read from resource. and at one point was telling to me to go find the correct plugins although it wasn't telling me which plugins I needed and where to grab them from..

Mplayer well forget it it just freezes as soon as you ask it to read the disc and then refuses to close down unless you kill the process off

any ideas please its really starting to bug me now.

many thanks in advance

---

### Post by Therion on 2009-06-23
Start with ```
sudo apt-get install ubuntu-restricted-extras
```

See where that gets you.

---

### Post by numbness05 on 2009-06-23
Ok thank you for the advice but unfortuantly that doesnt seem to make any difference...

Any other ideas please?

many thanks once again.

---

### Post by Therion on 2009-06-23
```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
```

---

### Post by numbness05 on 2009-06-23
Sorry should have mentioned I have also loaded Xine and gxine too....they seem to make no difference... although if it helps gxine tells me it has an error reading nav packet...? :(

---

### Post by numbness05 on 2009-06-23
ok have been messing about to see if it will even open in thoggen just in case i ever wanted to copy a DVD and it tells me i might not have libdvdcss2 installed...so just looked through synaptic and cant seem to find it although the restricted extras you advised me to install does mention libdvdcss2 but says that it will not be installed as part of that package...any ideas how else i might grab it I have tried sudo apt-get install liddvdcss2 but am told it may be obsolete...

---

### Post by numbness05 on 2009-06-24
excellent have it solved by running

sudo /usr/share/doc/libdvdread4/install-css.sh

---


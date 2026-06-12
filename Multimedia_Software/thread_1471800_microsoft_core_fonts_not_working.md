---
title: "microsoft core fonts not working"
date: 2010-05-03
forum: Multimedia Software
---

### Post by moveright on 2010-05-03
when I go to software center, it shows the ms core fonts but there is no install button.  I have loaded the restricted extras and medibuntu repos.  not sure why it is not working.  any ideas?

ubuntu version 10.04 btw.

---

### Post by jerrrys on 2010-05-03
i never found them in 10o4; i imported my truetype (i like bitstream) from 8o4

---

### Post by steveneddy on 2010-05-03
mmttcorefonts are in the "multiverse" repos

Just add the multiverse software sources to your install then in terminal:

```
sudo apt-get install msttcorefonts
```

If not DL them from here:

[https://launchpad.net/ubuntu/lucid/+source/msttcorefonts/3.2](https://launchpad.net/ubuntu/lucid/+source/msttcorefonts/3.2)

There are also endless free font sites on the internet - Google - where you can find your favorites anytime.

Remember that if you manually install fonts in your **.fonts** folder, perform this action in terminal:

```
fc-cache -fv
```

---

### Post by moveright on 2010-05-04
but why do they show up in software center, just without any download button?

---

### Post by peterroots on 2010-05-07
good question - I have no answer but for what it is worth, on Kubuntu....
On a 64 bit install I added ttf-mscorefonts-installer and got the ms fonts installed with not hassel
On a 32 bit install I did the same and the installer installed but did not install the fonts

I have no idea why - I tried removing the installer and reinstalling it but still no fonts

then I purged the installer
sudo apt-get remove ttf-mscorefonts-installer --purge
reinstalled it
sudo apt-get install ttf-mscorefonts-installer
and none of the fonts got installed - checksum error
sudo dpkg-reconfigure ttf-mscorefonts-installer
got the same error with all the fonts again

---


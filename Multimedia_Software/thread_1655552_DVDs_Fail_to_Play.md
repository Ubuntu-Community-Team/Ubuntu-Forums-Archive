---
title: "DVDs Fail to Play"
date: 2010-12-29
forum: Multimedia Software
---

### Post by Gnome1984 on 2010-12-29
I am new to Linux, when trying to play a DVD movie on computer through MOvie Player I get the following error:

An Error Occured:

Can not read from source!

The movies will not play with VLC or SMC player either, but will play on windows.  I believe it might be the driver.

---

### Post by Rodney9 on 2010-12-29
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by SteamWolf on 2011-01-03
Hi,
I have the same problem.  I followed the link above but it didn't solve my problem.
I can see the DVD in the places/computer and it shows the title.  It even tries to read it, but movieplayer says "could not read from resource"

I have the restricted formats installed already.

when I run:
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```it seems to install everything but the last line says:
```
dpkg: status database area is locked by another process
```could this be part of the problem?

the next step calls for:
```
sudo apt-get install ubuntu-restricted-extras
```which results in this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```it plays an original Kaiser Chiefs CD ok but won't play any DVD's even stuff burnt from my hard drive.

Drive is a SATA Liteon DVD burner.
help!  the whole point of this build is to play media on my TV!!  Google tells me this is a widespread problem but I haven't seen any solutions yet.

---

### Post by BicyclerBoy on 2011-01-03
Those errors look like you had synaptic package manger open while you were fiddling at the terminal with dpkg..

Can you not see that nothing was completed successfully ?

Can't do package manageement stuff at terminal with synaptic open..

Try again...

What software player are you using for DVDs ?

---


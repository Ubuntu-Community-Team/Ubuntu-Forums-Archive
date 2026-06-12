---
title: "unable to play commercial DVDs even after fluendo purchase"
date: 2010-11-07
forum: Multimedia Software
---

### Post by xaegis on 2010-11-07
Like the title says, I thought I'd support Ubuntu and buy the Fluendo add-on  from the app store. (I am running a fresh install of 10.10.)
Whenever I put in a commercial DVD I get an "an error has occurred" message. How do I go about fixing this?
I was under the impression that the ubuntu restricted extras would break fluendo, which is why I did not install them. Although during the install I did tell it to download the extra software there.


What should I do?

---

### Post by ajgreeny on 2010-11-07
None of that installs the libdvdcss2, which is what you probably need.

Either install that from the medibuntu repos, or if you have libdvdread4 already installed, simply run the shell script /usr/share/doc/libdvdread4/install-css.sh from terminal.  See:-
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by deanjm1963 on 2010-11-07
You don't need libdvdcss2 to run Fluendo DVD player - I use it myself. I had a problem very early on with Maverick as libdvdread4 and libdvdnav4 weren't installed.

Which version of Fluendo DVD? 1.012-1 or earlier?

Hope this helps.

---

### Post by xaegis on 2010-11-07
Version:

Fluendo DVD Player 1.0.10


Should I install those libs?

---

### Post by deanjm1963 on 2010-11-07
It wouldn't hurt to install them if they're not installed already. Open synaptic and search for livdvd - you will see the files there to install if they're not installed already.

---

### Post by xaegis on 2010-11-07
> **deanjm1963 said:**
> It wouldn't hurt to install them if they're not installed already. Open synaptic and search for livdvd - you will see the files there to install if they're not installed already.

they are both installed already. :(

---

### Post by deanjm1963 on 2010-11-07
Lets see ... have you played commercial dvd's on the drive before installing Fluendo? Fluendo will only let you play one region per DVD drive, that's why I have two drives, one each for Regions 4 and 1.

You might need to insert a dvd and go to "setup" on the menu, and select the region for playback.

---

### Post by Yellow Pasque on 2010-11-07
> **xaegis said:**
> they are both installed already. :(
You should still run the script to get libdvdcss as suggested above.

---

### Post by deanjm1963 on 2010-11-07
> **Temüjin said:**
> You should still run the script to get libdvdcss as suggested above.

Fluendo DVD ignores libdvdcss2 completely as it has it's own commercial CSS built in.

---

### Post by xaegis on 2010-11-07
> **deanjm1963 said:**
> Lets see ... have you played commercial dvd's on the drive before installing Fluendo? Fluendo will only let you play one region per DVD drive, that's why I have two drives, one each for Regions 4 and 1.

You might need to insert a dvd and go to "setup" on the menu, and select the region for playback.

It is a new computer. I had to play a DVD in windows for it to set the region code so that it would play in linux. Problem solved. 

Thanks!:)

---


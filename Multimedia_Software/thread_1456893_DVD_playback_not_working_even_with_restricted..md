---
title: "DVD playback not working even with restricted."
date: 2010-04-17
forum: Multimedia Software
---

### Post by doyleman on 2010-04-17
I have libdvdcss, libdvdread (i think it was called), and restricted extras - i even followed the instructions on the documentation. they still wont play. I run 9.10 64bit on my laptop, and 10.04 on my desktop. any suggestions i can try? :/

---

### Post by wojox on 2010-04-17
You should be able with:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Yellow Pasque on 2010-04-17
What player are you using and what kind of file are you trying to view? Start the player from the terminal and post the output...

---

### Post by doyleman on 2010-04-17
@wojox- already did and tried no dice.

Temüjin - using vlc, and its standard commercial DVDs. The current one in question is - The Last Samurai. Others fail to load as well, the file format is VOB. "VLC media player 1.0.2 Goldeneye
[0x1a36888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface."

---

### Post by doyleman on 2010-04-18
bump.

---

### Post by mc4man on 2010-04-18
Could be several reasons - to start somewhere do this

Insert a dvd and hold down the shift button, in the pop up click cancel. (may take several seconds

Then open your home folder, find the .dvdcss folder and delete it.

(.dvdcss is a hidden folder, if you don't see it then Ctrl+h on keyboard or view -> show hidden files.

Then open a terminal and use this - post complete terminal output

```
vlc dvd://
```

---

### Post by doyleman on 2010-04-19
i didnt have that folder... :(

VLC media player 1.0.5 Goldeneye
[0x25894b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: THE_LAST_SAMURAI_D2
libdvdnav: DVD Serial Number: 305991CB
libdvdnav: DVD Title (Alternative): THE_LAST_SAMURAI_D2
libdvdnav: Unable to find map file '/home/nathan/.dvdnav/THE_LAST_SAMURAI_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0x7f3994002758] main input error: ES_OUT_RESET_PCR called
[0x7f3994002758] main input error: ES_OUT_RESET_PCR called
[0x7f3994002758] main input error: ES_OUT_RESET_PCR called
[0x7f3994002758] main input error: ES_OUT_RESET_PCR called

---

### Post by Yellow Pasque on 2010-04-19
> **doyleman said:**
> ************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
Are you sure you have libdvdcss installed correctly? Does this show naything?
```
sudo ldconfig -v | grep css
```

---

### Post by mc4man on 2010-04-19
> No css library available.See **
** /usr/share/doc/libdvdread4/README.Debian **
** for more information. **

You need libdvdcss2.
The typical way is to get from medibuntu - but as luck would have it their server is down for a bit - you can download a deb directly from here and install

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/](http://download.videolan.org/pub/libdvdcss/1.2.10/deb/)

3rd listed for your 64 bit, 4th listed for your 32 bit (you don't need the -dev packages,


If medibuntu was up then this command would install libdvdcss2 for you (putting in context part of the error mess. "See **
** /usr/share/doc/libdvdread4/README.Debian **"
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by doyleman on 2010-04-19
oh gosh i'm a tard. i forgot i used a lynx beta 2 dvd and installed it, removing my support :oops:. thanks all for the help :)

---


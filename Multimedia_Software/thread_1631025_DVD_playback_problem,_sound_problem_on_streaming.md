---
title: "DVD playback problem, sound problem on streaming"
date: 2010-11-26
forum: Multimedia Software
---

### Post by bva123 on 2010-11-26
Installed 10.04, movie player (and VLC)  unable to play DVD's previously done on Windows. Upgraded to 10.10, same problem and youtube type videos have have visual but no sound. Did check sound settings and options. Any advice please?

---

### Post by Jahid65 on 2010-11-26
Did you add the medibuntu repo? To do this
This command should be run in the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal") (Applications &#8594; Accessories &#8594; Terminal): 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then ```
sudo apt-get install libdvdcss2
```

If you use 32 bit edition you can also install 32codecs (for 64bit 64codecks)
```
sudo apt-get install w32codecs
```

---

### Post by bva123 on 2010-11-26
Thank you, but panel refuse to accept password, will not even display any digits. Am i missing something?

---

### Post by mc4man on 2010-11-26
> will not even display any digits.
When typing your password into a terminal nothing is displayed - so just type it correctly and press enter on the keyboard.

---

### Post by bva123 on 2010-11-26
Kept on hammering password and eventually accepted

Thank you, problem seems to be sorted. VLC plays where movie player fails.

Thanks again

---

### Post by Smallwheels on 2010-11-26
This worked for me too. I have 10.04. Getting videos to play was one of the problems I needed to solve. I got the same results. The first movie I tried playing with Movie Player worked but it was very jerky. I then played it with VLC media player and it worked, though the controls were a bit odd. For instance I would get to the main menu and it would take a while for the cursor to react to a link. Eventually the cursor would change and the link could be selected. 

I then tried a different movie disc and it worked fine in Movie Player. 

My computer is an HP 32 bit AMD 2.3 GHz Sempron LE 1300 with 2 GB RAM. I'm eager to get everything working. I've got several more things that aren't working yet and I hope they get fixed this week so that I can use Ubuntu as my primary computer instead of my Mac or Vista.

---

### Post by bva123 on 2010-11-27
Upgraded to 10.1 and problem was mostly solved with advice posted on this thread but finally resolved with last update on 10.10. However, same installation (and updates) on other laptop allows better playback of DVD's. ( More consistent with different types but still VLC gives better results). The newer laptop proved better, must be a hardware/technology thing.  Keep in mind some DVD's will not play on PC, copyright protection, nothing to do about that. 

Good luck!

---


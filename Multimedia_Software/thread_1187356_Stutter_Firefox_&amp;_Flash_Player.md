---
title: "Stutter Firefox &amp; Flash Player"
date: 2009-06-14
forum: Multimedia Software
---

### Post by sandman3838 on 2009-06-14
Hey has any of you had issues playing Flash Movies?

I have:
Ubuntu 904
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
4Gb memory
Geforce GeForce 9800 GT 500mb
Firefox

Although the videos do play there is some chop?
I just tried to watch Harpers Island (Skull Island) that CBS series where everyone is getting killed and there was that chop.  It's also viable on you-tube.  

1.  So far I have removed Adobe Flash and installed swfdec-mozilla.
2.  Altered Firefox with [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
3.  Installed FASTERFOX as a alternate to Firefox.

Still the paging!

At the moment the only fix I have is to open Vbox and use Winxp with IE!

Suggestions anyone.

---

### Post by UmeshAawte on 2009-06-17
I have same problem.

I could not see any flash on my firefox.

---

### Post by sandman3838 on 2009-06-17
This might fix it for you!
It looks like it did it for me, anyway!

After posting this issue, sometime later I tried to watch a DVD movie.
It failed.  So after some looking around I found this from another posting:

 GETTING DVD TO PLAY

In terminal Install:

Quote:
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Quote:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Quote:
sudo apt-get install libdvdcss2

Quote:
sudo apt-get install w32codecs

Quote:
sudo apt-get install libdvdread4

Quote:
sudo /usr/share/doc/libdvdread4/install-css.sh

Quote:
sudo apt-get install ubuntu-restricted-extras 

And finally:
sudo apt-get install mozilla-mplayer

Now I can play DVD movies.  
Next, I was curious if this might fix my movie playing in Firefox.
I just got back from YOUTUBE and the videos played just fine.
Perhaps you should give it a shot?
So far I have had no more issues.

Good luck

---

### Post by pyutaros on 2009-06-19
This reply doesn't seem to have anything to do with a Flash issue.

---

### Post by sandman3838 on 2009-06-19
Actually it does!

Originally I have two issues.

1.  Firefox failed to play Flash movies.
2.  I couldn't play DVD movies.

As I wasn't getting where with the Flash issue I concentrated on getting the DVD issue resolved!  I did.... in the steps I listed.

However along the way I found this, as a fix for the Flash issue, it was my final step!

And finally:
sudo apt-get install mozilla-mplayer

I just gave you the whole thing as I suspect that getting the right drivers installed for the DVD player probably affected the performance and installation of the Flash Player.

Hey just try the final step and see if it fixes your problem?
You can always do the other stuff later.

Can you play DVD's on your system now?

Best of luck.

---


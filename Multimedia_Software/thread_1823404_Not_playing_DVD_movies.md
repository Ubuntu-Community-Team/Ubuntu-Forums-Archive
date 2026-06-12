---
title: "Not playing DVD movies"
date: 2011-08-12
forum: Multimedia Software
---

### Post by davethewave83 on 2011-08-12
I can't get my sisters Ubuntu to play some movies off DVD. I google searched for how to play dvds on ubuntu, and a site says basically "just install Totem" and the dvdlib3 (it already has dvdlib4 installed) so I went ahead and installed totem. 

I launched totem, but there is no option for opening a DVD, there's only Open File. which would mean I'd have to open the vob files, which are very confusing to navigate. 

I tried VLC and VLC couldn't run it, so I tried VLC(Windows32 under Wine) and although it worked in the past, it couldn't read the movie either (the movie is Casino Royale and I watched it just fine on my Windows machine) 

is there an easy method to just install some proprietary software that can play movies with a single click? :D  like with the package manager perhaps? I couldn't figure anything out. It seems like Ubuntu should come pre-ready for DVDs and I don't understand why it isn't. 

Thanks!!

---

### Post by Elfy on 2011-08-12
Try this

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%2010.04%20%28i386,%20amd64%29,%2010.10%20and%2011.04%20%28i386,%20amd64%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%2010.04%20%28i386,%20amd64%29,%2010.10%20and%2011.04%20%28i386,%20amd64%29)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Troubleshooting](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Troubleshooting)

---

### Post by Duncan Williams on 2011-08-12
If your still stuck. Try this:
[http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/](http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/)

---

### Post by davethewave83 on 2011-08-12
thanks all. I've tried all that. In VLC I tried opening it with no menu even and it says 
Playback failure:
DVDRead could not read block 0.

also during an update in the past Gnome completely changed. There's a sidebar on the left with bubbly icons and everything is harder to find. It just changed it's self. 

I tried totem again too... it doesn't give any errors, just fails.

---

### Post by wazupwiop on 2011-08-12
You are now using the unity desktop, the new interface.  I haven't experienced that error with DVD reading personally, but here are some troubleshooting tips that might help you out a little:

1. Try different DVD's, something could be wrong with the disk itself.
2. If you are dual-booting, see if the other OS's can play DVD's.  If they can't, my suspicion would be hardware issues.
3. Make sure your system is updated.
4. If you haven't installed the restricted extras packages, follow the directions here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by davethewave83 on 2011-08-12
> **wazupwiop said:**
> You are now using the unity desktop, the new interface.  I haven't experienced that error with DVD reading personally, but here are some troubleshooting tips that might help you out a little:

1. Try different DVD's, something could be wrong with the disk itself.
2. If you are dual-booting, see if the other OS's can play DVD's.  If they can't, my suspicion would be hardware issues.
3. Make sure your system is updated.
4. If you haven't installed the restricted extras packages, follow the directions here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks all! it's working :) Unity eh? When did they do that? It's actually kinda neat, just not what I'm used to. I like the searchable programs feature but it'll just take time to get used to.

---

### Post by wazupwiop on 2011-08-12
The devs released unity in 11.04.  It has some major issues though......  You will find them as you use it.  I switched back to gnome classic.

---

### Post by davethewave83 on 2011-08-13
> **wazupwiop said:**
> The devs released unity in 11.04.  It has some major issues though......  You will find them as you use it.  I switched back to gnome classic.

I see. Is there by any chance a command line method of editing the login screen to choose classic over unity? I know how to do this GUI but at the moment, my sister is watching a movie and I'd like to do it from my machine. :popcorn:

---

### Post by wazupwiop on 2011-08-13
After you select or enter your username at the login screen, there will be three pop-up bars at the bottom of the screen.  One of them will say unity, you want it to say "Ubuntu Classic".

---


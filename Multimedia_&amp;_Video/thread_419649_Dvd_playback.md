---
title: "Dvd playback"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by dioon on 2007-04-23
Tried almost everything to play a dvd in Feisty but no luck,used Totem xine, gxine, Kaffeine.
Here are the plugins I have installed:
 Libdvdcss2
 Libdvdcss2-dev
 Libdvdnav4
 Libdvdnav4-dev
 Libdvdplay0
 Libdvdplay-dev
 Libdvdread3
 Libdvdread-d
 
Would appreciate any help before I go completely bald.
Followed Adamants Sticky and installed the plugins and codecs o/k.

---

### Post by tbg58 on 2007-04-23
I had the same problem -- loaded the same codecs with no joy.
In my case, had to apt-get install xine-ui and DVDs started to play.
Hope this works for you as well.
Good luck!
- Rob

---

### Post by janbockaert on 2007-04-23
You have to install totem-xine (in synaptic) this will uninstall totem-gstreamer. If you have installed libdvdcss2, you will be able to watch dvd's in totem.

---

### Post by Cadmium on 2007-04-23
After I installed the totem-xine and libdvdcss2, I couldn't play the DVD I already had inserted until I ejected it.  I guess libdvdcss2 had to be installed before the DVD is mounted.

---

### Post by dioon on 2007-04-24
Thanks Janbockaert and Cadmium,I did install Totem Xine,and as you say it uninstalled Totem-gstreamer,I do have Libdvdcss2 installed,but no go,still pulling my hair out.

---

### Post by darkmane on 2007-04-24
If you're still having problems with DVD playback try installing 'Xine extra plugins' 

Applications > Add/Remove

Go to the 'Sound & Video' section, do a search on 'libxine' (You may need to ensure that 'All available applications' is selected in the 'Show' box - it may work for for one or two of the other options, I didn't try any of the others)

Or search for 'libxine-extracodecs' in Synaptic.

This worked for me using Totem-xine.

[Edit: this works for Feisty (7.04), there are several guides on the forums for Dapper/Edgy which work]

---

### Post by Steve H on 2007-04-24
I had DVD playback issues for a while, but then i found this thread

> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It talks you through installing the restricted (non-oss/non-free) modules for multimedia. My DVD  / streaming media playback works a treat now.

---

### Post by littlekidlover on 2007-08-09
I installed Automatix2:

[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

and it solved all my dvd playback porblems... 
and i had serious porblems.

straight .deb downloads for etch, edgy, dapper, and feisty
with 64 bit versions for all but etch

[it comes with some pretty cool extras]

---

### Post by ferd on 2007-08-15
> **tbg58 said:**
> I had the same problem -- loaded the same codecs with no joy.
In my case, had to apt-get install xine-ui and DVDs started to play.
Hope this works for you as well.
Good luck!
- Rob

Thank you for this. After a two day search, you have the solution to my DVD play problem.:guitar:

---


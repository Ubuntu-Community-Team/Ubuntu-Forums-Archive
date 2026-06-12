---
title: "Lost in Codecs"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by jazzyphonic on 2007-11-01
Hi im an absolute newbie to linux and im using gutsy gibbon.  Cool Os but a nightmare to stabilise.  Take that with a pinch of salt im straight from xp.  I cant paly dvds ive tried intsalling xine codecs, libdvdcss, xmms, w32 codecs etc etc.  I just cant please help.  I eventually installed Ogle that managed to play the dvds but with no sound.  I have roamed on all blogs i could get my hands on to no avail.  Pliz help im in ova my head.

---

### Post by taurus on 2007-11-01
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jazzyphonic on 2007-11-02
Hi there i visited the link u provided twas pretty helpful, however im stuck on this part.  It says

"If you are using Ubuntu 7.04 or later:

    *

      Install the libdvdcss2 package after adding the unsupported third-party repository Medibuntu.

Your DVD player should now play back encrypted DVDs."
 
Where do i find this ive tried synaptic package manager, software sources and add remove programs.  I cant find it.  help pliz

:(

If you are using Ubuntu 7.04 or later:

    *
I also used the following command on the terminal

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine.

Im getting an error saying ldconfig deffered processing taking place.  This never ends.  Is this a bug

Help

---

### Post by charlesreid1 on 2007-11-02
This may be another brick wall, but this guide looks like it's a step-by-step on how to enable Medibuntu and add the right repositories (places where Ubuntu looks for packages) for Ubuntu to find libdvdcss2 and w32codecs (sounds like those are what you need, right?)

Hope this helps

---

### Post by charlesreid1 on 2007-11-02
[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by jazzyphonic on 2007-11-03
Hi guys 

Thank you for all your help, i had installed some stuff that i think was causing conflicts to the playing.  I cna now play dvd's.  I uninstalled all media players and installed VLC and im having a blast.  I also installed w32codecs and libdvdcss2.  Everthing works great, i have a long movie night ahead of me.  

Cheers guys 

Linux rocks:guitar::):guitar:

---


---
title: "DVD Playback Issues"
date: 2008-09-29
forum: Multimedia Software
---

### Post by jsnelli2 on 2008-09-29
I have been unable to get dvd playback working correctly on Hardy.  I've been able to get dvds to play in VLC, but whenever I try to advance a chapter it goes back to the menu.  Also, with VLC I am unable to go fullscreen on my external monitor, it always wants to go fullscreen on my laptop monitor.

Having said this, I would much rather use Totem or Mplayer to play the dvds.

With Totem all I get is an error saying I don't have the required plugins to play the dvd.  I have libdvdcss2 and ubuntu-restricted-extras installed.  If I try to play a single vob file off of the dvd I get it to play but it is garbled and I can only see sections of the picture.

In Mplayer I get a message stating: "couldn't find matching filter/ao format" and I believe that it is running slower than it should.  It plays only the very first intro clip and the sound is loud clicking.

Any ideas on how to get either one of those to work? I would much rather have totem working if that is possible.

Thanks

---

### Post by Steve1961 on 2008-09-29
> **jsnelli2 said:**
> I have been unable to get dvd playback working correctly on Hardy.  I've been able to get dvds to play in VLC, but whenever I try to advance a chapter it goes back to the menu.  Also, with VLC I am unable to go fullscreen on my external monitor, it always wants to go fullscreen on my laptop monitor.

Having said this, I would much rather use Totem or Mplayer to play the dvds.

With Totem all I get is an error saying I don't have the required plugins to play the dvd.  I have libdvdcss2 and ubuntu-restricted-extras installed.  If I try to play a single vob file off of the dvd I get it to play but it is garbled and I can only see sections of the picture.

In Mplayer I get a message stating: "couldn't find matching filter/ao format" and I believe that it is running slower than it should.  It plays only the very first intro clip and the sound is loud clicking.

Any ideas on how to get either one of those to work? I would much rather have totem working if that is possible.

Thanks

Try sudo apt-get install totem-xine

Then run this:

sudo update-alternatives --config totem

and choose totem xine from the options

Hope this helps

Oh yes, just remembered an important extra.  Make sure you add the medibuntu repo and install w32codecs as well

---

### Post by jsnelli2 on 2008-10-02
I knew that was a possibility, but last time I did that I was unable to view embedded videos through firefox.  Is there anyway to get that working whenever using xine plugin.

---

### Post by jsnelli2 on 2008-10-02
Also, I want to make sure that I wouldn't lose ability to play any files with certain codecs that I already have..such as xvid, divx, etc.

---

### Post by jsnelli2 on 2008-10-05
Is there anyway to do this?

---

### Post by Steve1961 on 2008-10-06
> **jsnelli2 said:**
> I knew that was a possibility, but last time I did that I was unable to view embedded videos through firefox.  Is there anyway to get that working whenever using xine plugin.

Yes, just uninstall the totem-mozilla plugin and install mozilla-mplayer instead.  I've always found that this works well.

---

### Post by iDragula on 2008-10-06
would you mind PM your MSN to me? thanks._______________________________________________________________________________ I want to know [what is my ideal weight](http://www.beidu.info/weight-loss/slimming-mistakes/76-what-is-my-ideal-weight) and [how much weight has star jones lost](http://www.beidu.info/slimming-methods/celebrity-weight-and-height/71-how-much-weight-has-star-jones-lost) and [what is jennifer lopez's weight](http://www.beidu.info/slimming-methods/celebrity-weight-and-height/70-what-is-jennifer-lopezs-weight), hehe, they are also fat. can you give me the [weight loss plans for teens](http://www.beidu.info/weight-loss/weight-loss-tips/72-weight-loss-plans-for-teens) and [juice recipes for weight loss](http://www.beidu.info/diet-books/fruit-diet/73-juice-recipes-for-weight-loss)?

---

### Post by Steve1961 on 2008-10-06
> **iDragula said:**
> would you mind PM your MSN to me? thanks._______________________________________________________________________________ I want to know [what is my ideal weight](http://www.beidu.info/weight-loss/slimming-mistakes/76-what-is-my-ideal-weight) and [how much weight has star jones lost](http://www.beidu.info/slimming-methods/celebrity-weight-and-height/71-how-much-weight-has-star-jones-lost) and [what is jennifer lopez's weight](http://www.beidu.info/slimming-methods/celebrity-weight-and-height/70-what-is-jennifer-lopezs-weight), hehe, they are also fat. can you give me the [weight loss plans for teens](http://www.beidu.info/weight-loss/weight-loss-tips/72-weight-loss-plans-for-teens) and [juice recipes for weight loss](http://www.beidu.info/diet-books/fruit-diet/73-juice-recipes-for-weight-loss)?

Sorry dont use MSN.  If you have questions just post them on the forum

---


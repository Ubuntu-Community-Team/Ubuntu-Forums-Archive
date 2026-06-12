---
title: "Gtkpod Issues"
date: 2009-10-27
forum: Multimedia Software
---

### Post by Andumi on 2009-10-27
I'm using a 4th or 5th-generation Ipod Nano Video (the 4GB variety), and generally, I use Gtkpod to update and manage my songs without too much trouble. However, I have suddenly encountered an issue that I have never seen happen before with this program. I mount the drive, and suddenly a warning appears, saying something along the lines of "Cannot read iTunesDB. The file does not exist" or something to that effect. So, quite naturally, I eject it and try again. Only to  find the same issue occuring. So then I take a look at the iPod itself. It hasn't shown any particularly odd behavior, so I write it off as a simple mistake and that I must've done something to wipe the blasted thing. I open it up as a digital audio device and start browsing around for the files, seeing if they are indeed still there. And they are. Which is confusing to me, to say the least. I then try to bring the music backup database back on to the iPod, thinking I'm going to have to replace all of my music song by song, but that, too, suffers and error, and will no longer add songs. So then I check the free space on the iPod. It registers as having only 48KB left or so. Previously, I'd had somewhere in the area of 400+MB of free space. 

EDIT: It attempted to use SHA1 checksums, but then just went to plaid with a bunch of squares.

So, my question is simply "WTF is going on with this thing?"

---

### Post by dummy910 on 2009-10-27
Have you tried connecting that iPod to another program, say Rhythmbox to see if it gives the same error? 

*On a side note:*
I just had an iPod project a couple of weeks ago where there was about 7gigs of data on a 4th gen 8gig nano and the Nano player would not play anything outside of displaying album art, but this Nano would play on gtkpod-rhythmbox-etc, huh?

I ended up removing all the songs to an Ubuntu Linux Desktop, then went over to an Imac Workstation(you could use the Windoze version too in Wine), plugged in the Nano and let Apples Itunes for Mac program reset the Nano to factory defaults, then updated it to their latest firmware version. 

I then took the unit back over to Ubuntu and reloaded(imported) all the songs back to the Nano with gtkpod and bam!, Houston, we now have a Nano that plays on it's own.

---

### Post by Simian Man on 2009-10-27
I'm assuming you're using a 4th generation iPod nano because the 5th generation should never have worked right under Linux (yet anyway).  Apple changed the encryption scheme on the new models to further try to squelch competition to their crappy iTunes software.

Have you been using this iPod with iTunes lately?  Because it's possible that the new version of iTunes broke your iPod in the same way that Apple broke the new iPods.  I'd try refreshing the iPod under gtkpod with the "Create iPod's Directories" option.

---

### Post by dummy910 on 2009-10-27
> I'm assuming you're using a 4th generation iPod nano because the 5th generation should never have worked right under Linux (yet anyway).

The aforementioned project I did WAS a 4th generation Nano and I did updated it with Apples latest software via Itunes, figuring it was worth rolling the dice as I could always restore it to original with another couple of clicks.

I've read the horror stories about their latest offering, and it might be worthy of just restoring the Ipod back to it's original state, as they offer several different restore-update options in the Itunes program.

---

### Post by Andumi on 2009-12-03
Thanks for the input, guys. Rythmbox and several other programs refused to deal with it, so I did in fact have to use a Windows machine with iTunes on it to reset it to factory defaults. The problem occurred completely out of the blue, you see, when I had been using Gtkpod quite nicely and singularly with my iPod for a while. Either way, problem solved. 

~Thanks.

---


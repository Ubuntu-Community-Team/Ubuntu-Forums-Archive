---
title: "Need Simple app to record live audio to CD"
date: 2007-10-24
forum: Multimedia Production
---

### Post by sgaskins on 2007-10-24
There are times when I will need a powerful, multi-track recording option and I am planning to use either Audor (for the really complex stuff) or Audacity (for the somewhat simpler tasks), but most of the time I am in need of an application that can record live audio and then burn it to a CD for archival purposes.

All I want to do here is basically replicate the interface of something like the [Yamaha CDR-HD1500]("http://www.yamaha.co.jp/english/product/av/products/hf/cdrhd1500.html").  
I want to:
* Record stereo audio to the hard drive during a live performance of up to 2 hours duration
* I need to mark the individual tracks, preferably with a single button press, 
* Then at the end of the performance it needs to be written to an Audio CD in a 'disc at once' fashion so that the individual tracks have no silence gap between them.

Can anyone here point me to some simple scripts (or even better a dead simple GUI) that could do this?

I realize that I'd have some work to do if the performance extends more than 80 minutes in order to decide where to pick a 2nd disc, but even that could be assisted....

---

### Post by sgaskins on 2007-10-24
I suppose since I'm new here, I should note that I'm just getting a new recording setup going using:
Ubuntu Studio
Lexicon Omega USB audio interface
Generic Thinkpad Laptop PC

And, you guessed it ... my Yamaha CDR has died, so this project has bumped up somewhat in priority recently. :)

---

### Post by Stochastic on 2007-10-26
to my knowledge no program like that exists for linux.  It does sound like it would be a useful tool but for the time being I think you'll be stuck doing things one step at a time.  Record into Ardour, Rezound, Jokosher, Audacity, or your other favorite app, split the tracks, save, and burn.  As for a burning application that can do disc-at-once, I seem to recall K3b doing that, there's probably others too.  Please post back if you find any better solutions.

---

### Post by UbuWu on 2007-10-26
Audacity + brasero would probably do the job.

---

### Post by sgaskins on 2007-10-26
A bit of seaching and playing around, and I found a program called "Audio Transcriber" 
[http://stlouis-shopper.com/cgi-bin/transcriber-wiki/mozdev-wiki.pl?TranscriberWiki](http://stlouis-shopper.com/cgi-bin/transcriber-wiki/mozdev-wiki.pl?TranscriberWiki)
It uses  a combination of Sox, CDrecord, glued together with Perl-Tk.  Very hackable!  I really hope to be able to start from here to make a super simple app for my purposes.

But it seems that the sox recorder has some kind of problem with skipping when recording from a USB audio source.  I'm experiencing the same issue that was noted here;
[http://sourceforge.net/mailarchive/message.php?msg_id=Pine.LNX.4.64.0702231108530.13086%40rhama.deepcore.ngn](http://sourceforge.net/mailarchive/message.php?msg_id=Pine.LNX.4.64.0702231108530.13086%40rhama.deepcore.ngn)

Basically, when I try to record from the USB Lexicon input (sox -r 48000 -t alsa hw:1,0 ....) with the sox tools, it sounds horrible.  Skipping or sound cutting out at a fast, continuous rate.  The alsa command line recorder works just fine, though.  (arecord -D hw:1,0 file.wav)
So maybe I can get this to work with a little bit of re-programming.  And if I do, then I'll post the results here!

---


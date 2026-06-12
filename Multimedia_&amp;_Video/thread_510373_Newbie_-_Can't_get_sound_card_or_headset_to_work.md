---
title: "Newbie - Can't get sound card or headset to work"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by damphoux on 2007-07-26
I have Ubuntu loaded and running on a Gateway.  All is fine other than I can't seem to get any sound devices working.  I've tried just speakers hooked into my sound card (Soundblaster Augdigy), and I've also tried a USB Headset.  Both to no avail.

Any pointers?

I also was looking to see if there was any paid support out there other than Canonical for $250.  Any thoughts there?

Mike

---

### Post by SPQQKY on 2007-07-26
Check alsa mixer and be sure Audio-analog/digital output jack is unchecked.

---

### Post by kyphi on 2007-07-28
You do not say which version of Ubuntu you are using nor which machine you are using (other than Gateway).  
The Creative Audigy should work.

It is of course quite likely that you still have your motherboard sound chip still activated.  If you are using a soundcard, onboard sound should be disabled.

If you go to the System menu at the top of your screen and then to Preferences and then Sound, on the dropdown screen you must enable the top two boxes by placing a tick in them.  At the bottom of the screen, where it says 'Default Sound Card' you should see an entry for your Creative Audigy.  You might have to toggle that to select the sound system that you want to use.

To disable the onboard sound you need to go into the BIOS.  If you need help with that just say so.

As for paid support, why would you want that?  The whole Ubuntu world will gladly help you.

---

### Post by bahdom on 2007-07-28
i would like to know how to disable on board sound please :D

---

### Post by kyphi on 2007-07-28
> i would like to know how to disable on board sound please 

If damphoux were to ask this question I would answer it here, this is his post.

bahdom, please post your request as a new post.

---


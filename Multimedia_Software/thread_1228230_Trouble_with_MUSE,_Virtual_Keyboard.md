---
title: "Trouble with MUSE, Virtual Keyboard"
date: 2009-07-31
forum: Multimedia Software
---

### Post by Kbalz on 2009-07-31
I was really looking to do some midi creation and mixing, with no midi keyboard. 
 
I'm runing 9.04 UbuntuStudio
 
I started JACK Control, then Hydrogen for drum beats. I was able to setup Hydrogen and when I hit play within Hydrogen I hear the drum perfectly.
 
Then I wanted some instruments, I choose to use MusE. I started Virtual Keyboard, then MusE. Yesterday I could hear the Virtual Keyboard by clicking the keys, and within MusE, I added a track, and used the pencil tool to scribble all over the place. I hit play inside of MusE, and I could hear my drum track playing from Hydrogen, but could hear nothing else.
 
I did not manual configuration to JACK. I ran out of time and had to call it a night.
 
This morning I fired everything back up in the same order. I when I play within MusE, I can no longer hear my drum tack, and Virtual Keyboard plays no sound, and my MusE pencil track plays no sound. When I play the drum track within Hydrogen, it outputs sound. I opened up JACK to connect, one by one connecting device to device, but never can get sound from MusE
 
The documentation is not very complete, and I can't find any guide on how to do this.
 
 
I'm running Ubuntu in a VirtualBox (Sun), on a laptop (Asus M50Sr, only a year old).
 
What do I do to diagnose all these issues? Thanks.

---

### Post by Kbalz on 2009-08-01
OK I got a little farther with MusE, I added some Midi instruments and assigned them, and I could hear my output.
 
Now the big question is, I still don't hear Hydrogen when I hit play within MusE, even though I did the other day.
 
How can I get both Hydrogen and MusE to play at the same time? Does anyone have experience meshing everything together? Do I use one of the other Audio tools provided?
 
Too drunk to test right now, I'll try tomorrow - kb w/ jb

---

### Post by Kbalz on 2009-08-01
HA I got it - Hydrogen has a button at the bottom 'JACK TRANS' - every time you press it a warning comes up which is confusing but it actually hooks in/out of JACK.. So I'm all set now and off to have fun with it.

---


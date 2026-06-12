---
title: "Warning Noob: Advanced Audio / Synth Emulators"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by Brendt2 on 2006-09-15
This question is short and simple:

What is a good solution for virtual music apps ( IE Pro Tools ), and synth emulators ( IE Rebirth, Reason, Reaktor, Ect )?

Also how is Ubuntu's hardware support for MIDI I/O devices? Is there a prefered device?

How does Ubuntu support 24bit audio? Better than windows?

Sorry that I am such a noob!

:-\" 

Thanks!

---

### Post by dolson on 2006-09-15
1) This is covered all over the net, and every person you ask will give you different answers. Some people might prefer LMMS because it might be easier to use than say, seq24 and ZynAddSubFX, but then others prefer seq24 because of flexibility and featureset and so forth. Personally, my choice is seq24 + whatever synths I like to hear. For a tutorial, check on the wiki on the Application Tutorials page. I wrote one there a week ago, and it works well for me, and I will indeed be using seq24 for my album.

2) MIDI I/O devices meaning what, exactly? USB MIDI keyboards? MPU-401 devices? Again, everyone has their opinion. My SoundBlaster Live! 5.1 and Audigy2 ZS cards both work like a charm as far as MIDI input and output go. Most MPU-401 inputs like this should work just fine with any external MIDI gear... I also have a USB MIDI keyboard that I love (16 knobs, one slider, two wheels, good reviews for the keybed quality (most important aspect, IMHO), etc). I use the E-MU Xboard49. Both the mailing lists and Creative/E-MU told me this board would not work in Linux, but clearly someone has fixed it since then, because I bought it and plugged it into my USB port (for power) and lo and behold, it appeared in JACK Control, and works perfectly.

3) That will depend on your sound card model and what ALSA drivers exist for it, just as it does in Windows.

---

### Post by majutsu on 2006-09-15
there are many choices, but these are great synth languages/environments that work very well in ubuntu in my experience:

supercollider
pd
chuck
alsa mod synth


midi works well with anything as long as you have it connected right to alsa or jack whichever is required.  my usb midi keyboard is even auto-recognized by alsa.  my jack recognition of some keyboards is a problem.

you can use fst (with wine and steinberg vst SDK) to play vsts like z3ta, albino, crystal, absynth, etc to play in linux now.  

i would probably use pd or supercollider to sequence, but some have had luck with rosegarden or seq, but i haven't.

that's just some thoughts.  there are many points of view.

---

### Post by zettberlin on 2006-09-16
> **majutsu said:**
> 

supercollider
pd
chuck
alsa mod synth



well comeon! Brendt2 is searching to replace reason and reactor - both graphical Programs with rich intuitive user-interfaces. 

The closest thing to this is Zynaddsubfx, mx44 can do some interesting synthstuff also, ams is of course absolutely worth the effort to learn how to use it and so is OM. You will probably want to have a decent sequencer also, seq24 is fast and intuitive, Muse and Rosegarden are more powerfull-cubasestyle beasts.

Protoolslike is Ardour, the next Version(2.0) will have Miditracks also, the recent stable already has everything one needs in the audiodomain.

---

### Post by Brendt2 on 2006-09-16
Well thank you all so much for your responses!

This ought to make my transition that much easier!

Man... does Ubuntu and it's community rock!

-Brendt

---

### Post by majutsu on 2006-09-16
ps jack now recognizes my keyboards as well as alsa!!!

go ubuntu!  ubuntu rules!

i now have full midi in pd, chuck, everything, jack and alsa.  as well as cecilia (csound), etc.  good stuff.  you have to go a little "under the hood" but you can make good music at a deep level in ubuntu.  just takes more work, but i think you get a little something for it.

---


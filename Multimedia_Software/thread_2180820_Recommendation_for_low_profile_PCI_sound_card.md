---
title: "Recommendation for low profile PCI sound card"
date: 2013-10-14
forum: Multimedia Software
---

### Post by Stan_Meissner on 2013-10-14
Someone is giving me a used Dell Optiplex 760 from his business. Dell uses onboard sound and one of the things I use my PC for is recording my instrumentals.  I need to know a few suggestions for Ubuntu compatible low profile PCI sound card.  I am limited to what I am able to spend to around $50 to $100 USD.  

My Compaq desktop crashed and exhibits the same behavior when attempting to reload the W and Ubuntu Studio so it's obviously some kind of hardware issue.  I'm guessing a bad video card or perhaps the battery on the board.  It's about six or seven years old so I'm not going to throw money at the old one.  It's got two working hard drives that can be transferred to the Dell so I'll be good to go but just a little concerned about the amount of memory and how good the onboard sound will perform.  Business computers usually skimp on sound quality.  Also, if anyone knows how to bypass the onboard sound when I install the new sound card please let me know.  I'm assuming it's probably a choice in the bios but if anyone has added a sound card to a Dell business model let me know how it went for you.

P.S.  Typing this on my wife's old Gateway laptop with Ubuntu installed.  This thing was unusable with Vista choking on itself and a broken optical drive but has been brought back to life by installing Ubuntu 12.04 with a USB drive.  I used Ubuntu seven years ago for about a year and am very pleased by how for it has come since then.

---

### Post by tgalati4 on 2013-10-15
Older M-Audio cards might work.  You might need a right-angle adapter or look for a 1/2 height PCI adapter to connect to an external sound card.  USB sound cards (M-Audio, PreSonus, and others) might work as well.  But do your research on specific models for linux compatibility.  And yes, most on-board sound chips are noisy.  But test it first with some recordings to be sure.  The biggest factor to quality are your transducers (microphones, guitar pre-amps, etc).  If you have decent (external) preamps, then you can get a fat signal to the onboard sound chip that will overwhelm any motherboard noise.  But only testing will tell.  Most Dell's have Intel onboard sound chips, and they are not bad when driven with a fat signal from external preamps and mixers.  Using the onboard chip as a microphone boost is not useful for studio use.

---

### Post by M7CPn4b on 2013-10-15
Hey,

Asus Xonar cards work well in Linux, and they are (at least most) low profile PCI cards. They are said to have a very natural sound in playback. There are different versions, not sure what kind of connectors you need.

About disabling the onboard sound you're right, if you can turn it off, it's usually in the BIOS. In rare cases, you'll have a jumper on the board.

-Emily

---


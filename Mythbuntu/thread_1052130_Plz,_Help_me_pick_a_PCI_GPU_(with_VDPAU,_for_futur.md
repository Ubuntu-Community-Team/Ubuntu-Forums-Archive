---
title: "Plz, Help me pick a PCI GPU (with VDPAU, for future release)"
date: 2009-01-27
forum: Mythbuntu
---

### Post by BassKozz on 2009-01-27
I am building a MythTV system on the cheap using old used parts I purchased:
2xCompaq Evo D510s - 2.4Ghz P4, 1.5GB of RAM, 500GB IDE HD
1xHDHomeRun - To record HD QAM over cable

Now all I need is to purchase a PCI video card that will support VDPAU. 
*Yes I realize that VDPAU is still in beta, and I would have to build MythTV in order to take advantage of it now (which is not my intentions), but I would rather purchase a card with VDPAU support now so when MythTV .22 is released w/ VDPAU support I will be ready to take advantage of it.*

So I've narrowed it down to these cards: (click on the image to go to the NewEgg.com comparison page)
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/mythbuntu/newegg-video-cardcompare.jpg[/IMG]]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=2000380048%201069609642%20106791921&bop=And&CompareItemList=N82E16814187059%2CN82E16814130451%2CN82E16814133245%2CN82E16814187041%2CN82E16814187042")
They are all similarly priced, 4x8400GS's & 1x8500GT.
Can someone please help me with this one, I don't know which to choose.

One important factor that is going to play into this is the fact that the Compaq Evo D510s's PSU is only rated for 220watts, and 2 of these video cards list 300watts or better PSU required.  I plan on disconnecting the D510s's CD & Floppy drives once I get Mythbuntu installed, hopefully this will free up some room for me to run one of these GPU's.
There is a review posted on the PNY card that states that someone is using a 250Watt PSU and it runs fine for them, so I guess I could use that?
Because of this limitation, I will only buy 1 GPU for now to test on one of the machines, and if it works I'll buy a second.

p.s. this is a continuation of this thread: [Building Myth System on the cheap, recommendations?]("http://ubuntuforums.org/showthread.php?t=1048967")

---

### Post by newlinux on 2009-01-27
Between those, I'd go with one of the fanless ones. Either will probably do with VDPAU.

---

### Post by BassKozz on 2009-01-27
> **newlinux said:**
> Between those, I'd go with one of the fanless ones. Either will probably do with VDPAU.
Thanks for all your help newlinux, you've been a great help throughout this entire barrage of questions, and I really appreciate it...

Does the memory size make a noticeable difference, or should I save the extra $10 and go with the 256MB model (vs. the 512MB)?

---

### Post by newlinux on 2009-01-27
You know, normally I would say it doesn't make a difference in Linux, but with the advent of VDPAU Ithink it might help...

---

### Post by jyavenard on 2009-01-28
BTW, VDPAU supports is now available on 0.21-fixes with my backport available there:

[http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)

Ubuntu packages provided, fully compatible with mythbuntu ones

---

### Post by newlinux on 2009-01-28
> **jyavenard said:**
> BTW, VDPAU supports is now available on 0.21-fixes with my backport available there:

[http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)

Ubuntu packages provided, fully compatible with mythbuntu ones


I was not aware of this - very cool! Wish my best GPU wasn't a 7100 and I could take advantage of this instead of waiting for .22.

---

### Post by jyavenard on 2009-01-28
> **newlinux said:**
> I was not aware of this - very cool! Wish my best GPU wasn't a 7100 and I could take advantage of this instead of waiting for .22.

Waiting for 0.22 won't do anything regarding your video card and the fact that it will never support VDPAU...

So not sure why you are talking about waiting for 0.22

---

### Post by newlinux on 2009-01-28
> **jyavenard said:**
> Waiting for 0.22 won't do anything regarding your video card and the fact that it will never support VDPAU...

So not sure why you are talking about waiting for 0.22

Yes, I know - I probably wasn't clear - that's when I *was* planning on upgrading my hardware (when .22 came out and was stable). Now I don't have to wait. That's why I was talking about waiting for .22. I didn't think the hardware would magically morph into a purevideo HD 2 card.

---


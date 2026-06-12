---
title: "robust error detection and correction"
date: 2010-05-11
forum: Multimedia Software
---

### Post by csab on 2010-05-11
Hi Folks,

this what I'm wondering. I have some important data that I want to store on a set of DVDs. I have n DVDs (n is typically around 4 or 5), and I'm willing to use n+2 DVDs, such that if one DVD is scratched (has a few unreadable sectors) and one DVD is destroyed, I can still recover the data.

In the past, I used a technique that is basically taking all the ISO images and XOR them together (after some padding with zeros of the shorter ones) to create the n+1st DVD, then use dvdisaster to create recovery files for all n+1 DVDs and store them on the n+2nd. This is very cumbersome, because I have to do the XORing manually, (I wrote a very user unfriendly program for that), then storing all the ISO sizes, remembering how all this works and trusting that I don't make a mistake.

Is there a better way? RAID for DVDs? Any other ideas?

---


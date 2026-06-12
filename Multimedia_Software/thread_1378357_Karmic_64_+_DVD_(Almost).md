---
title: "Karmic 64 + DVD? (Almost)"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Tourdog on 2010-01-11
See below  Sorry

---

### Post by Tourdog on 2010-01-11
This is a continuation of the thread "Can not get DVD's to play" .

Do to the outstanding efforts of Uberdog, HappyFeet and HoweField on this forum my Totem will almost get the job done.  Howefield, was a huge help discovering that I did not know the "Tab" key enabled the <ok> at the bottom of the Sun Micro Java release document which showed up after using Uberdog's sudo.  I also used both of HappyFeet's sudo's plus 2 more sudos recommended by the resultant diagnostic .

Uberdog:
sudo apt-get install ubuntu-restricted-extras

Totem should be capable of playing a personally paid for movie like "You've Got Mail".  Progress has occurred however!  Totem acknowledges the DVD and attempts to play it now.  The audio is fractured and is at best hard to understand.  The video is visible on screen but totally scrambled............  in both cases displays more than before.  (Totem wouldn't play the disk at all)  Before getting the, "Totem cannot play the DVD because a required Plugin is missing" it did flash this for a few seconds..........   "Need GStreamer 
Element dvdspu"

HappyFeet:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

HappyFeet:
> sudo apt-get install libdvdcss2I have tried through "Synaptics" and the other programs to find that file/program (GStreamer Element dvdspu) but to no avail.  
What is next?   I may be just one Plugin short of success?!   Suggestions?!  TIA  !!!

---

### Post by HappyFeet on 2010-01-11
It seems as though something may be wrong with your install. (it happens) The 2 lines of code I gave you is **the** way to get DVD's to play. On every install of ubuntu that I have done, (more than a few) that method works. I'm going to sign off on this and wish you luck. Hopefully someone else will be able to help you short of reinstalling.

---


---
title: "NVidia HDMI audio not going so well with a Vizio 1080: HDTV"
date: 2010-10-31
forum: Multimedia Software
---

### Post by hamptonids on 2010-10-31
This subject has been discussed all over the place, but from what I can read I don't think I fit into one of the handy little how-tos. I have researched the heck out of this, but it still isnpt going so great, so I figured I would stop and get some assistance and advice from the community, while I still have a little sanity left.
     I have a dual boot Windows 7/Pinguy (Ubuntu based) install(_Everything works fine in windows, do it isn't hardware)_. I have the follwing notable components in my new machine:

Processor:    Intel® Core™ i7 950 Processor
Memory:        12 GB [2 GB X6] DDR3-1800
Video Card:    NVIDIA GeForce GTX 470
Motherboard:    Gigabyte GA-X58A-UD3R

     Long story short I have a nice Vizio 1080 HDTV as a monitor. It is attached to my Nvidia card with HDMI through a DVI adapter. 
     All the fixes that I thought would apply I have done:
Upgraded ALSA to .23
Unmuted the S/PDIF option in alsamixer
Shut down Pulseadio

           If anyone has any suggestions or has the patience to get a thread going to assist me in getting this resolved I would really appreciate it. Been away from Linux for a while (Mac laptops are issued at my work).

     If there is any other data or info needed, please just ask.
     

TIA

---

### Post by efflandt on 2010-11-02
"It is attached to my Nvidia card with HDMI through a DVI adapter. "

DVI may be able to do both digital (DVI or HDMI) and analog (VGA) **video**, but DVI does NOT do audio.

Although, I am trying to figure out how to get audio working over HDMI in Maverick with a regular HDMI cable (nVidia GT 220).  In Sound Preferences I do see Digital Stereo (HDMI) Output under Hardware tab, but Test Speakers does not produce any sound, and selecting it as Output does nothing.

---


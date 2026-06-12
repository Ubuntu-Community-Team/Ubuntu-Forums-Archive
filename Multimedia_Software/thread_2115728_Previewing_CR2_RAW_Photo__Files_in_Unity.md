---
title: "Previewing CR2 RAW Photo  Files in Unity?"
date: 2013-02-13
forum: Multimedia Software
---

### Post by Stoob on 2013-02-13
Hellllo.  Thanks for reading.

I have a fresh install of Ubuntu 12.04 with the Unity desktop and am using Shotwell to manage my Canon photo RAW CR2 files.  Shotwell is pretty good, but my import dialogue looks like this (attached).  In addition my Unity file browser doesn't show preview thumbnails.

I have "libraw5" the raw image decoder library installed already.

I tried installing gnome-raw-thumbnailer but this had no effect in Unity, or maybe I don't have the dependencies - I don't know how to check.  I'm not interested in switching to the Gnome desktop.

Any advice to get preview working in Shotwell - at least?   Desktop would be nice but Shotwell is a must to see those previews before I import them.

Thanks!

---

### Post by eric-yorba on 2013-02-14
It all depends how you're importing the images.

Shotwell can only show previews if GPhoto has support for fetching RAW previews off your camera.  If you've plugged in a memory card without using the camera, Shotwell has no way to fetch the previews for those images.  (That said, it's usually a lot faster to download from a memory card reader than through a camera, so there's a trade-off.)

---

### Post by Stoob on 2013-02-16
Thanks!

outside of Shotwell, but just in my normal file browser (it's "Nautilus"), is there a way to preview CR2 RAW files?

---

### Post by mike acker on 2013-02-16
> **Stoob said:**
> Thanks!

outside of Shotwell, but just in my normal file browser (it's "Nautilus"), is there a way to preview CR2 RAW files?

i fussed around with that . tried out RawTherapee as well as UFRaw and RawStudio

I still have RawTherappee installed . and it does read .cr2  but so did the others 

however:  none of these appear to be calibrated for the Canon cameras. this means adjusting every image manually and means it is not usable as a general import tool to replace Canon's DPP

I generally don't shoot RAW so this isn't really a Big Deal to me .  But If I were an RAW format fanboi then I would look at running DPP under WINE

it's really a bit of a shame . if anyone has found an answer to this let us know .
~~~
Amendment 1 :
Image 1 : this is what RawTherapee produced from .cr2
[IMG]http://ubuntuone.com/7JJFlQ2vH5GIk2MUgYQFYQ[/IMG]

Image 2: this is what Canon DPP Produced:
[IMG]http://ubuntuone.com/5hIIG5Rx1owHkp1hFLHcwa[/IMG]

Image 2 is correct . the camera was set on + 2/3 EV in order to compensate for the snow

Amendment 2
note: I wasn't able to link images from Flickr but they are fine from our Ubuntu1 service .

---

### Post by eric-yorba on 2013-02-18
The reason the Canon software produces a very different JPEG is that it's reading "secret" metadata in the CR2 file recorded by the camera.

UFRaw, RawTherapee and other RAW developer software that don't have Canon's proprietary software won't be able to read and interpret those fields.  Of course you *can* adjust all the parameters manually in the free/open RAW developer software, it just takes more work.

---

### Post by ORF1000 on 2013-03-05
I think it takes a lot more work.  I have only had some moderate success with one or two raw files using the available linux programs for working with RAW images.  I feel stuck with Windows and Canon's DPP software.  Is there any hope that the situation will improve?

---

### Post by eric-yorba on 2013-03-05
> **ORF1000 said:**
> I think it takes a lot more work.  I have only had some moderate success with one or two raw files using the available linux programs for working with RAW images.  I feel stuck with Windows and Canon's DPP software.  Is there any hope that the situation will improve?

If enough people complain to Canon they might release software for Linux.  Other than that, it's very unlikely given the quantity of work involved.  Parsing dozens of undocumented file formats is a huge undertaking.

---


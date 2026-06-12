---
title: "A Good VCR to digital converter?"
date: 2017-02-28
forum: Multimedia Software
---

### Post by cybrsaylr on 2017-02-28
Have a dozen old home VHS tapes that I want to convert and save to digital on my PC HDD. 

Have this link to capture devices needed to hookup PC to VCR: [https://www.google.com/search?client=opera&q=VCR+to+digital+converter&sourceid=opera&ie=UTF-8&oe=UTF-8#q=VCR+to+digital+converter&tbm=shop&*](https://www.google.com/search?client=opera&q=VCR+to+digital+converter&sourceid=opera&ie=UTF-8&oe=UTF-8#q=VCR+to+digital+converter&tbm=shop&*)
Still have to figure out which device will work best.

Question is what software program/app is needed and works best with Ubuntu 16.04 that will save them at the best quality?

---

### Post by walterav on 2017-03-18
What works best in terms of ease is try to find a Composite/S-video based DV-in (mind the "in") FireWire camcorder or VCR (JVC has VCR with VHS, DV Firewire and TBC) and pci/pci-e FireWire adapter (aliexpress/ebay). Both can be found reasonable cheap in secondhand stores (Netherlands). The software package that would capture all footage in DV codec/native container is "dvgrab", no fiddling with drivers or difficult software, just capture. This DV codec depending on the container will play/edit with all reasonable NLE in Windows and Mac/linux, playback will work with VLC.

Best quality is get a seperate TimeBaseCorrector, Analog Uncompressed USB3/TB/PCI-E video capture devices (BlackMagicDesign Intensity/Decklink/Shuttle) capture in uncompressed (270/360Mbit's) with the bundled BlackmagicDesgin MediaExpress util or capture using "ffmpeg" / "melt" to proress (50Mbit) or other compressed formats (vp9, mpeg2, x264 etc). For this solution you have to tune your PC requirements since these IO cards (dumb) work in uncompressed size and ask a lot from your HDD/SDD CPU /GPU if doing uncompressed or compressed recordings?

Cheapest is indeed a v4l2 capture device which might directly record to h264 or other compressed signals from the usb bus but I have no experience with that.

I would call it overkill to capture lowress VHS to uncompressed codecs, DV can be sufficiant at 25Mbit's and is easy storage requirements and editing. If you capture raw DV container, you can go to any NLE from there! For Broadcast terms of quality/archiving SD Compressed 8bit mpeg2 yuv422 @ 50Mbit's is called a standard MPEG-imx sd10 in a MXF container.

---


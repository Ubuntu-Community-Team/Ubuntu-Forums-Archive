---
title: "Can't download from firewire DV camcorder"
date: 2009-03-06
forum: Multimedia Software
---

### Post by utherpendragonfly on 2009-03-06
I have a Canon ZR800 camcorder. I want to download the video and use Kino or KdenLive to edit it. But when I turn on the camcorder and plug in the firewire cable, nothing happens. I had KdenLive open, then tried Kino. No icon appears on desktop and nothing happens in editing software. 
So I searched around and found I need dvgrab installed. I checked in Synaptic and I have it installed, along with other packages which it looks like I should have.
So I opened a terminal and typed <sudo dvgrab> and got this:

davey@davey-desktop:~$ sudo dvgrab
[sudo] password for davey: 
Found AV/C device with GUID 0x00008500016e5670
Capture Started

The camera screen showed the cassette wheels turning for a couple of minutes, then came to end of tape. But terminal still says "Capture Started" and nothing seems to be happening after 40 minutes!

Then I opened Kino again and looked in Preferences and got this image below.
I found the file /dev/raw1394, and permissions are root.
Do I need to gain root access to this file, or is my problem something else altogether. Right now I haven't a clue what to do get this video on my computer!
Help!

---


---
title: "Question's"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by Spenser_Gilliland on 2006-11-08
Is it possible to capture multiple video devices at the same time in Linux?  (using multiple firewire devices)

Is it possible to capture mutliple audio soruces at the same time in Linux?  (firewire again)

Also is it possible to turn around and output this video/audio in realtime or damn close?

---

### Post by Jussi Kukkonen on 2006-11-08
I have no experience on firewire devices, but that shouldn't matter (as long as there are drivers for the devices). I do have experience on this setup:
* two DVB-C (digital cable television) receiver cards 
* an old matrox dual-head card connected to a TV
* VDR running as my "set-top box"

The system can capture at least six channels (from two different channel groups) simultaneously, while watching a channel or a recording. I'm not sure how useful information is to you (DVB is basically just MPEG, so it's probably quite different from what you are thinking). I also do not know how close to real-time the playback is as I have no other digital TV receivers (not that VDR was written with that purpose anyway)...

On the topic of real time: did you know 2.6.18 kernel has / will have real time support built-in? That should mean millisecond scale response times for any apps that are written to take advantage of that.

---

### Post by Spenser_Gilliland on 2006-11-08
I didnt know that I'll have to look into it some more.  Where would I find the drivers for a Canopus ADVC110 or a Sony DVCAM VTR.  These would both connect over firewire.

---

### Post by Rhubarb on 2006-11-08
The Canopus ADVC110 is just an analogue to DV capture box.
No drivers are needed, you just need software that can read a normal firewire DV stream.  VLC I know can do this, Kino would work too.

Edit: You can open up multiple instances of VLC, so you should be able save / view / stream / re-encode multiple videos at the same time.

---

### Post by Spenser_Gilliland on 2006-11-08
would the VTR's act the same way?

Alright I guess I should explain what I want to do.

My first goal for this year maybe begining of next year.  Is to make a server for replays at the stadium.  I would want this to be a local server for all of the press to draw from.  If this is successful (charge a small fee for access to pay for server).  

Next cool device that could add flavor to a game would be to add multichannel audio effects.  I've looked into the stadiums wiring and all of the speakers are tied to indvidual amps.  Which means i could give outs to each of the speakers indvidually and have moving sound throughout the building for a cool effect.    

After this I'd like to develop a system for live video production that would be prototyped to hell on webcast.  This would involve creating a clip server program, creating a replay program, and creating the video switcher and all its effects.   

Then finally I'd like to creating a shading algorithm.  That can Auto Iris all of our cameras.  I'd also need control of the camera's iris digitally somehow. 

Thats the cool things i wanna do or help do.  Can anyone help me?

---

### Post by Rhubarb on 2006-11-08
> **Spenser_Gilliland said:**
> would the VTR's act the same way?

Yeah I think they would, if it spits out DV, VLC and a host of other programs should be able to work with it.

There's already a few filters that VLC can apply to video.
It's in the repositories, check out:
[http://www.videolan.org/](http://www.videolan.org/)

You've got big plans there!  I'd make sure to get a raid setup there, as multiple video streams could be quite taxing for just one hard disk.

For multichannel audio, there's a few external sound cards you could use:
[http://www.hercules.com/showpage.php?swcty=UK&p=91&b=1&f=1](http://www.hercules.com/showpage.php?swcty=UK&p=91&b=1&f=1)
I don't know if this'll work in linux or not.  It should do.
Using JACK might help you out with patching audio to the right outputs.

---

### Post by Spenser_Gilliland on 2006-11-08
sata raid so 3.3g/s max on the hard drive,  1gps through network max about 400mbps 4-5mbps per stream, 20-25 mpbs per person 16 conections max?  Is that about right?

---


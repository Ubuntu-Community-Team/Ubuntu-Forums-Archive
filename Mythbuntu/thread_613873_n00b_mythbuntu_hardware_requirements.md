---
title: "n00b mythbuntu hardware requirements"
date: 2007-11-15
forum: Mythbuntu
---

### Post by ZY15 on 2007-11-15
I have an old HP Pavilion 7855 lying around the house, and I was considering installing Mythbuntu to use it to only run MythTV, i.e. I would like to hook up the ol' HP to watch (OR record) live TV and output to the TV.  The specs for the HP from their website are:
Base processor and speed: Intel Pentium (R) III / 1 GHz Processor,133 MHz FSB
Chipset: Intel 810E
RAM:  128 MB RAM PC100 
Video Memory:  11 MB shared, integrated graphics, not upgradeable 

I am looking for opinions on whether my HP hardware will be sufficient or not. I'd have to buy a TV Tuner card and I've been looking at the Hauppauge PVR-350 because it has the TV out,  but I don't know if it's worth the investment or if the computer is too underpowered for this type of application.  The MythTV page for the Hauppauge PVR-350 says the unit is "Also well-suited for underpowered systems, since the onboard mpeg encoding and decoding mean your CPU has very little to do. As a single data point, consider that the utilization on 750 Mhz PIII is only 20% while watching live tv." 

I appreciate any insight, opinions, etc.!!!!!

---

### Post by newlinux on 2007-11-15
With a PVR-350 your system should be fine, from a processor perspective. What about hard drive space? I'm not sure about the RAM needs.

---

### Post by ZY15 on 2007-11-15
The HP has a 60GB HD; I think this will be enough if all I am doing is running MythTV...again, opinions are welcome if I am wrong!

---

### Post by uopjohnson on 2007-11-15
I would consider that they absolute bare minimum for running myth and only with the pvr-350.  The reason the 350 is such a good idea is that it has hardware encoding AND decoding so your processor doesn't have to handle any of the decoding.  You probably won't be able to transcode and commercial detection is going to take forever, but it will run.  
That is really not enough ram, I would consider going up to 512 at least.  with only 128mb or ram you are going to be swaping out to the hard disk like crazy which is goign to slow down your whole system and cause recording problems as your PVR-350 tries to write to the disk at the same time.  This is going to cause a whole bunch of errors that will be impossible to diagnose. 
60gb of disk space will net you about 50gb or recording space once the OS and swap are added which will give you less that 25 hours of recordings.  Which sounds like a lot, but you will probalby max out pretty quick once you start recordings re-runs of That 70s show. 
I would consider getting this setup with a 350 and seeing how you like it.  If you decide myth is for you then make some small investments in upgrading this system.

Edit:
Took a look at my systems and my frontend is currently siting idle using about 400mb of ram, same with the backend.  I would consider 512 about the minimum for a combined system with at least a 1gb swap partition.

---


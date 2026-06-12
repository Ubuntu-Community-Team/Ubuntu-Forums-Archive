---
title: "Terratec Cinergy C pci HD not working in Ubuntu/Mythbuntu 12.04"
date: 2012-10-01
forum: Mythbuntu
---

### Post by netfreedom on 2012-10-01
I've just tried to scan for DVB-C channels on MythTV, but it returns with no channels found.

The OS is Ubuntu 12.04 32 bit with MythTV package added and also tried a Mythbuntu 12.04 64 bit and 32 bit install, but the same issue.

Could only locate one earlier thread regarding this similar issue: 

[http://ubuntuforums.org/showthread.php?t=857524](http://ubuntuforums.org/showthread.php?t=857524) 

But the files mentioned here is not available anymore (site not found) and also not sure, that this solution would work for ver. 12.04, since the thread is from 2008.

The Terratec Cinergy C pci card works great, if I boot up into Windows 7, so I'm sure about the card is working, frequencies, symbol rate aso. but in MythTV nothing can be found, it completes really quick and says no channels could be found.

I've follwed the guide on how to set up the card in MythTV, choosing the capture card aso. (it will display Philips as mentioned in the guide) so it seems the card isn't recognized proberly.

Looking at the Linux TV page, the particular DVB-C card should work "out of the box" since the firmware/driver should be included into the kernel, but this doesn't seem to be the case..

Has anyone experienced a similar issue with this particular DVB-C card and found a work around?

Thanks,

/Mike

Medion Mediacenter MD 8822
Intel® Core™2 CPU 6320 @ 1.86GHz × 2
 2,0 GiB RAM
Intel® 945G x86/MMX/SSE2 Video

(Ubuntu 12.04 32bit / Mythbuntu 12.04 64bit)

---

### Post by netfreedom on 2012-10-01
Update to thread:

I now got the card to show up correctly in MythTV backend, it now says DVB-C and I'm able to search for TV channels and add them.

However the HD performance is not good compared to DVBViewer in Windows 7, but it could be my hardware (the media center is from 2007)..

I uninstalled all MythTV packages, restarted and then followed the command giving in the other thread mentioned above.

Open Terminal and gave the following commands:


sudo apt-get install mercurial linux-headers-$(uname -r) build-essential

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

make all

sudo make install


Then I restarted the PC and reinstalled the MythTV packages. After setting up the MythTV backend correctly, I was able to do a channel search and add the channels.

As mentioned, the channels can be watched, but the HD channels are a kind of crappy..

I have no idea what the above package does, since the firmware should have been included into the kernel (acc. to Linux TV) and work "out of the box" which however, is not the case.

Nothing mentioned in help or not able to locate such information than the earlier thread.

/Mike

---

### Post by alien878 on 2012-10-04
I've got the Terratec Cinergy S2 PCI HD which should be the same thing except it is sat instead of cable.

In 12.04, you (finally) don't need the mercurial vl4-dvb.  My card works fine without them and is actually now working better then when I was using them.

I suspect your problem is playback.  You can test by downloading an HD recording and seeing if it skips too.  The solution is probably to tweek the playback profile.  It depends on the HW you have, but in my case VDPAU with medium quality worked fine (I only have an Atom 330 with nvidia onboard).

---


---
title: "Tuner Card not feeding sound through onboard sound"
date: 2011-08-09
forum: Multimedia Software
---

### Post by beartums on 2011-08-09
I'm new to Linux and am setting up a mythtv/xmbc box on Ubuntu 10.10 (natty does not install on my hardware).  I have a Sabrent TV PCIRC tuner card, which seems to work fine with the proper card and tuner settings.  My on-board sound is HDA-Intel surround sound, which I have configured as analog duplex.  

Currently the sound works fine through my speakers plugged into any jack on the back of the PC (two speakers, one jack).  I can watch ripped movies and listen to music.  The TV tuner is pumping sound from its external jack -- if I hook it up directly to the speakers it works fine.  I can feed the Tuner's sound to the line-in on my motherboard, but nothing comes out.  In the sound manager, i have the input device selected and the input level shows that the sound is coming in through the connector, and I can test the speakers and they work fine, but they don't seem to be communicating that the sound coming in needs to be pumped out through the speakers.

What am I missing?  Any help would be greatly appreciated.

thanks.

---

### Post by beartums on 2011-08-13
More Information:

Oddly enough, When I booted the day before yesterday, the sound was not working in TVTime, the video is not working in VLC (through the sound usually does if it is opened through the media | Open Capture Card menu), and neither work in MythTV.  Sound is still getting to the sound card (the line-in levels are still jumping around appropriately and not when I unplug the jumper).

I fiddled around with the CARD and TUNER settings a lot without much change (sometimes it doesn't work as well, but seldom better).  Then I tried using VLC to open the Playlist Device which gave me Video and no sound (just like TVTime) whereas it had been giving me sound and no video.  Then I opened the capture device again under the Media menu (using the defaults) and not VLC works fine -- both Video and Audio through the Media | Open Capture Device menu.  MythTv still does not even open the tuner card (watch live tv says "please wait" for several second and then dumps back to the menu), and TVTime shows Video and no Audio.

Any thoughts?  I could sure use some help.

Thanks

---

### Post by beartums on 2011-08-17
Well,  thanks to a 2009 post ([http://ubuntuforums.org/showpost.php?p=8308073&postcount=3](http://ubuntuforums.org/showpost.php?p=8308073&postcount=3)) I finally managed to get it working.  I'm not sure why the operation was intermittent previously, but probably some of the fiddling I did caused the loopback module to not be loaded any more.

---


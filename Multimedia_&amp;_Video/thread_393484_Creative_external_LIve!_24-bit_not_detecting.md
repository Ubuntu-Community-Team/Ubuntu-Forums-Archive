---
title: "Creative external LIve! 24-bit not detecting"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by Bunnykun on 2007-03-25
Hi, I have a problem with my dreaded USB Live! 24-bit card.  I've read around the forums and see that lots of people have problems, but their problems always start with "I get half sound, this isn't working."  I, however, can't get Ubuntu to detect my card at all.  aplay-l doesn't list the device.  

I do have onboard audio and i have used the steps in this thread to enable the subwoofer: [http://help.ubuntu.com/community/HdaIntelSoundHowto](http://help.ubuntu.com/community/HdaIntelSoundHowto)

also I was looking at this page related to gentoo, but i'm too much of a linux noob to understand how to convert those directions for ubuntu use:  [http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb](http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb))

while I was writing this it occured to me to reinstall all of the alsa-packages with the USB card connected.  think that would help?  and if not, 

please help!

---

### Post by ssavelan on 2007-03-25
This is a usb device?  No PCI card?

---

### Post by sdgreen on 2007-03-25
Hmmm same problem here except I have the Creative Extigy. Worked quite well under Dapper, however the Extigy is not detected at all under Edgy 6.10.

I too followed the detailed how to's on this forum resulting in failure. Can't understand why Dapper sound was easy and Edgy so flaky.

The Gentoo stuff seems simple, but like you noobyitis makes me pause. 

Perhaps someone has an answer to deal with the usb sound external sound cards.

---

### Post by Bunnykun on 2007-03-25
Yes, it is an USB device.

the gentoo howto seems to directly specify the card is a USB device.  The files it references to alter are in different places in Ubuntu, I believe though.  I don't know where the analog for "make.conf" is in Ubuntu.  

It also looks like to me that that Howto will make the USB device the only sound device.  I prefer my onboard sound to still function. 

aand bump. heh

---


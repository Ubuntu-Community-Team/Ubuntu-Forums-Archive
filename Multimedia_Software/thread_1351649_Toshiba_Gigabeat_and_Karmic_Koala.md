---
title: "Toshiba Gigabeat and Karmic Koala"
date: 2009-12-10
forum: Multimedia Software
---

### Post by danixeddu on 2009-12-10
I have succesfully setup a Toshiba Gigabeat with Ubuntu Karmic Koala 9.10 and thought I would share my experience.

1. The Gigabeat is an MTP device. Make sure libmtp and mtp-tools is installed

2. When the device is plugged in make sure you "Unmount it" (there must be no icon on desktop) otherwise mtp believes the device is being used elsewhere.

3. Rhythmbox, Amarok and Gnomad2 automatically detect the Gigabeat if item 2 above is done.

4. Files can be transfered to the device using Rhythmbox, Amarok, Gnomad2 and the command line. I like Gnomad2 and the command line "mtp-sendfile". Rhythmbox is a good music organiser but I cannot transfer video files. Amarok on Karmic is a nightmare to understand. 

5. Gigabeat requires .wmv video files with combined audio and video bit rates of less than 800k

6. To convert Video to Gigabeat compatable .wmv files I found ffmpeg to work:
[I]
    ffmpeg -i INPUTFILE.mp4 -vcodec wmv2 -acodec adpcm_ima_wav -s 320x240 -ab 64k -b 600k OUTPUTFILE.wmv
[/I] 
7. Before unplugging the Gigabeat always make sure the unit is ejected and Rhythmbox, Amarok or Gnomad2 are closed.

If anyone has anything else to add then please feel free..............

---

### Post by sideaway on 2010-04-12
Media Player Device Error.

Unable to open the Toshiba Gigabeat MEGF-40 device

Is what happens when I try and use my Gigabeat with Rhythmbox... Any ideas?

---

### Post by Chronon on 2010-04-12
Change the USB mode and use it as a UMS device.  Check out Rockbox too. 
[http://www.rockbox.org/wiki/WhyRockbox](http://www.rockbox.org/wiki/WhyRockbox)

The Gigabeat F40 makes quite a nice device for running Rockbox.

---


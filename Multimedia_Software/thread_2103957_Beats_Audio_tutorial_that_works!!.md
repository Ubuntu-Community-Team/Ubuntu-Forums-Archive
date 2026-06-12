---
title: "Beats Audio tutorial that works!!"
date: 2013-01-11
forum: Multimedia Software
---

### Post by lunerceli on 2013-01-11
Ok, so for those of you who have Beats Audio (or the infamous HDA INTEL Cougar Point HDMI w/ Codec IDT 92HD81 series) and want to get better sound, then follow this little tutorial and have fun.

First off open up terminal (Ctrl + Alt + T, or through menu) and type the following:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```Scroll all the way down to the bottom where you will see the section that looks like this: 

```
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
```Now you want to add a line below the last options line to make the whole thing look like this:

```
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-hda-intel model=ref
```Notice the snd-hda-intel line at the bottom? That is the line that you add. After you add that line, just save the file, then reboot the computer. Now after you reboot, your sound might sound kind of low and sound like it has too much bass to it. The front speakers and the subwoofer are the only speakers that are working. How do you fix this you ask? Just open up sound properties (however you want to get there) and in the output tab (first tab that it opens), just change the connector to headphones. Upon doing this, you will notice the big change in sound and almost makes it sound like the IDT brother driver in Windows.  Now I know this isn't perfect, but it does work wonders. Now if only the Alsa guys would update their drivers to support new hardware, then we would be in business ...  Hope this helps someone. 

P.S. I am still trying to make things work a little better by trying to get more settings within the sound properties to adjust the sound settings of the rear speakers. No luck so far, but still getting on it though.

---

### Post by conromia on 2013-04-30
Hey,
Any luck in getting 4.1 sound working properly? :)
I have a HP Pavilion DV7-7008tx and only the sub and bottom speakers are working from your fix, but the small speakers at the bottom of the screen dont do anything.
Thank you for this 

James

---


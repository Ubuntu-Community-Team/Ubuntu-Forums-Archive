---
title: "nVidia low resolution."
date: 2009-12-28
forum: Multimedia Software
---

### Post by aboud on 2009-12-28
hey every one ... 
looking around, a lot is said about this, but there is no clear answer.
after several days trying to configure this FX 5500 I failed to get the right resolution on it .., I understood the the lack of Geforce cooperation with GNU is the bottom line problem.., mean while I noticed that there is a workaround , but there isn't guide to this solution.. 
after install the card, I tried the next:
first:   - clear installation of new Karmic.
       -- running 173 nVidia driver, with auto config at the end.
          => I got : 'input not supported'.
       after playing around with xorg.conf, i got no where. 

second: - clear installation of Karmic.
       -- running 173 nVidia driver, without auto config. 
     then I installed the driver from system menu > Admistration > hardware . every thing look fine but max res is 640x480 . 
    adding the 1024x768 to xorg.conf didn't work neither xrandr --newmode helped. 

third: - clear installation of karmic. 
       -- installing the driver with envyng. 
          still max res 640x480. 
I thought with Geforce I will get better Ubuntu, now I am about regret buying it. 

can any one put me on the beginning of the right way to solve this ?

---

### Post by aboud on 2010-03-05
I gave trying with 5500 ,and got new video card with nvidia 9500 GT on MSI, the resolution is definetly better but isn't what I want, 

after using both cvt gtf to create and add modeline to xrand with various refersh rates.. 

```

xrandr -s 1280x1024
failed to change the screen configuration

```

any idea ?

---

### Post by 23dornot23d on 2010-03-05
Have you installed Nvidia-settings

Should look like this ,,,,,, or similar .....

Sytem - Administration - Nvidia Settings

[IMG]http://i45.tinypic.com/ineseb.jpg[/IMG]



A good place to check before getting hardware for linux is here too .....

[http://www.ubuntuhcl.org/browse/search?offset=0&category=6&manufacturer=201&rating=&price=&os=1&order-by=&reviews=on&worksoutofthebox=on&keywords=](http://www.ubuntuhcl.org/browse/search?offset=0&category=6&manufacturer=201&rating=&price=&os=1&order-by=&reviews=on&worksoutofthebox=on&keywords=)

---

### Post by aboud on 2010-03-06
Yes I did, but it dosen't contain the required resolution.

---

### Post by 23dornot23d on 2010-03-06
Ok its probably the xorg.conf then that needs modifying .....

You can show the contents of the xorg.conf file ..... by doing this ....

gedit etc/X11/xorg.conf

save the file to your desktop and post it if you can .....

If not ...... (or if its empty) .....

I tend to go through the same things - here was the last thread
where someone had a problem .... the last link is probably what
you need to look at but reading through it - may answer some
questions too ........ 

[http://ubuntuforums.org/showthread.php?t=1414405](http://ubuntuforums.org/showthread.php?t=1414405)

The resolution you need should appear in the xorg.conf for it to be
available -   for when you log in ......... 

here is a link to a good way to go about setting it up .......

[http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125)

One more of my previous links ,,,,

[http://ubuntuforums.org/showthread.php?t=1402049](http://ubuntuforums.org/showthread.php?t=1402049)

---

### Post by aboud on 2010-03-14
many choices to try .., I will feedback my experience

---

### Post by BiggoCharley on 2010-03-14
> **aboud said:**
> Yes I did, but it dosen't contain the required resolution.

Are you using an analog cable or a DVI cable? what resolution are you trying to get?

---

### Post by aboud on 2010-03-15
I am using VGA cable, this is the analog one ? preferred resolution is 1280x1024

---

### Post by aboud on 2010-03-16
I am using a 5m VGA because the case is away from my desk so it wont make noise, accedently I used 1.5m VGA today, and somehow with little xrandring I applied the resolution I looked for for long time. when reconnect with the long VGA the xrandr list shrunk and big resolutions disappeared. could the cable be damaged or is it because it is long .. i wonder.

---

### Post by realzippy on 2010-03-16
...maybe your resolution disappeared after a reboot?
Do you have a file named "monitors.xml" in your /home/yourusername/.config folder?

(maybe you have to enable "show hidden files" in nautilus first)

---

### Post by aboud on 2010-03-16
It looks like it's all about the cable .. I tried another 1.5m VGA but it didn't work, now with that first 1.5m it worked  out of the box.

---

### Post by aboud on 2010-03-16
probably it is all about the cable, using this short cable it worked and while it's working i replace the cable and it still working, but when restart it didn't.

---

### Post by BiggoCharley on 2010-03-16
> **aboud said:**
> I am using VGA cable, this is the analog one ? preferred resolution is 1280x1024

Well that shoots my theory.  I had a similar problem.I was using a DVI cable and found that the nvidia software would not "see" the monitor and my list of available resolutions was limited.  I had found a post on this forum regarding this problem and following its instructions I changed to a VGA cable and all of a sudden I had a list of available resolutions as long as your arm-- 28 to be exact ranging from 320 x 240 to and including 1920 x 1200.  Your preferred resolution is among them. Wish I could have been of some help.

---

### Post by realzippy on 2010-03-16
> **BiggoCharley said:**
> Well that shoots my theory.  I had a similar problem.I was using a DVI cable and found that the nvidia software would not "see" the monitor and my list of available resolutions was limited.  I had found a post on this forum regarding this problem and following its instructions I changed to a VGA cable and all of a sudden I had a list of available resolutions as long as your arm-- 28 to be exact ranging from 320 x 240 to and including 1920 x 1200.  Your preferred resolution is among them. Wish I could have been of some help.


Thats really interesting.Lots of threads here in the forum about limited resolutions....so have a look at:

[http://en.wikipedia.org/wiki/Display_data_channel](http://en.wikipedia.org/wiki/Display_data_channel)

..seems there are physically changes concerning the "edid" channel pin:

[I]"The most common version, called DDC2B, is based on I²C, a serial bus. Pin 12, ID1 is now used as the data pin from the I²C bus, and the formerly-unused pin 15 became the I²C clock; pin 9, previously used as a mechanical key, supplied +5V DC power up to 50mA to drive the EEPROM, this allows the host to read the EDID even if the monitor is powered off..."
[/I]

---

### Post by BiggoCharley on 2010-03-16
> **realzippy said:**
> Thats really interesting.Lots of threads here in the forum about limited resolutions....so have a look at:

[http://en.wikipedia.org/wiki/Display_data_channel](http://en.wikipedia.org/wiki/Display_data_channel)

..seems there are physically changes concerning the "edid" channel pin:

[I]"The most common version, called DDC2B, is based on I²C, a serial bus. Pin 12, ID1 is now used as the data pin from the I²C bus, and the formerly-unused pin 15 became the I²C clock; pin 9, previously used as a mechanical key, supplied +5V DC power up to 50mA to drive the EEPROM, this allows the host to read the EDID even if the monitor is powered off..."
[/I]

This is interesting but I still don't understand how this relates to the DVI cable vs the VGA.  This is somewhat beyond me, technolically  --I'll just have to live with it for a while, at least.

---

### Post by realzippy on 2010-03-16
Yes,wrong quoting,it is interesting for
VGA vs VGA cable.

---

### Post by aboud on 2010-03-16
I hope a good quality 5m vga will solve my issue.

---

### Post by BiggoCharley on 2010-03-16
I'm told that the difference between VGA and DVI is dramatic --the quality with DVI is superior I'm told.. I have no first hand experience but wanted to try it , which is what got me involved with this problem in the first place.

---

### Post by aboud on 2010-04-03
I bought the most expensive 3m VGA i found, but it didn't do the job. 

I have to boot with my old 1.5m vga then replaced, and try not to reboot ..

---

### Post by aboud on 2010-04-09
interesting the cable problem appear only on Ubuntu, the long cable dosen't work while the short do it, on windows however cable dosen't make any difference. it is just working fine on both cables there.

---

### Post by aboud on 2010-04-10
bump

---


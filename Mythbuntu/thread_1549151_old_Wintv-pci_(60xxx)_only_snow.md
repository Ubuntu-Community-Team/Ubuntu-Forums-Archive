---
title: "old Wintv-pci (60xxx) only snow"
date: 2010-08-09
forum: Mythbuntu
---

### Post by Armarr on 2010-08-09
I have a Athlon XP 2000+ pc with 512Mb memory and a 320Gb HD
and I'm trying to set up mythtv with a pretty old tv tuner:
Hauppauge Wintv-pci Pal (60104) which is a BT848 based card so it should work (right?)
It has these connections: composite, S-video, TV-cable (pal), line-in and -out (sound I guess)
 
So right now I have Ubuntu installed and updated and mythtv running.
in the backend setup the card is recognised as "BT848A (UNKNOWN/GENE bttv"
and I have set the card type to "analog V4L capture card"
 
At input connections 4 things are shown:
Composite0
Composite1
S-video
Composite3
and I have tried scanning for channels on every one of them but don't get anything.
 
The program TvTime shows snow on composite0 (TV?) and a blue screen on the others.
But when I turn on my wii that's connected to the composite video the  video (on composite1) is flickering in a strange way, it's like it  displays the image 20% too high every other frame.
 
I hope I can get this solved, I already wasted a whole day trying to get this working on windows.

---

### Post by LowSky on 2010-08-09
Hi welcome to the forums.

This page should help with that card.

[http://www.mythtv.org/wiki/Bttv#What_are_the_modprobe_settings_for_the_STB_Gateway_OEM_Bt848_TV.2FFM_Tuner.3F](http://www.mythtv.org/wiki/Bttv#What_are_the_modprobe_settings_for_the_STB_Gateway_OEM_Bt848_TV.2FFM_Tuner.3F)

I'm not really sure what your expecting this card relies heavily on your Processing power. Be warned if you can't get a stable picture.

---

### Post by Armarr on 2010-08-09
> **LowSky said:**
> Hi welcome to the forums.

This page should help with that card.

[http://www.mythtv.org/wiki/Bttv#What_are_the_modprobe_settings_for_the_STB_Gateway_OEM_Bt848_TV.2FFM_Tuner.3F](http://www.mythtv.org/wiki/Bttv#What_are_the_modprobe_settings_for_the_STB_Gateway_OEM_Bt848_TV.2FFM_Tuner.3F)

I'm not really sure what your expecting this card relies heavily on your Processing power. Be warned if you can't get a stable picture.
My card doesn't have an fm tuner so it isn't that model.
But I'l try it after backing up modprobe
And shouldn't 1.6Ghz be sufficient for software rendering?
The flickering wii video only uses 3-12%

EDIT: I didn't know that Ubuntu doesn't use the regular modprobe.conf but a folder.
In what file do I add those lines?

---

### Post by zjunkie on 2010-08-09
You say this is an older card so that leads me to believe that it won't tune digital stations. That may be your problem, is there still analog broadcasting in your area?

If you're using video signal from a modulating device (cable box, digital tuner, vcr etc.) then you should be able to pick that up on whatever channel they're set to.

---

### Post by Armarr on 2010-08-09
> **zjunkie said:**
> You say this is an older card so that leads me to believe that it won't tune digital stations. That may be your problem, is there still analog broadcasting in your area?

If you're using video signal from a modulating device (cable box, digital tuner, vcr etc.) then you should be able to pick that up on whatever channel they're set to.
Out cable box spits out a analog signal for the vcr and the vcr strengthens the signal and sends it out again, it was connected to an old tv before this.
I hope that makes sense because I'm not sure about the correct terminology.
Thanks anyway for the responses

EDIT: 
After googling for the exact model number it seems that I'm the only one that is having problems with this card aside from getting sound over pci.
So that would probably mean that this one is just broken...
It didn't cost much but that was also why I was really exited since this pc has only cost me 15 euro (20$) so far.
Thanks for the help :)

---

### Post by ian dobson on 2010-08-10
> **Armarr said:**
> Out cable box spits out a analog signal for the vcr and the vcr strengthens the signal and sends it out again, it was connected to an old tv before this.
I hope that makes sense because I'm not sure about the correct terminology.
Thanks anyway for the responses

EDIT: 
After googling for the exact model number it seems that I'm the only one that is having problems with this card aside from getting sound over pci.
So that would probably mean that this one is just broken...
It didn't cost much but that was also why I was really exited since this pc has only cost me 15 euro (20$) so far.
Thanks for the help :)

Hi Armarr,

Where abouts are you? I have an old PVR500 (dual PVR150) gathering dust, are you interested?

Regards
Ian Dobson

---


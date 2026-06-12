---
title: "USB Stereo Audio Adapter not working"
date: 2009-08-14
forum: Multimedia Software
---

### Post by 982000971 on 2009-08-14
I purchased a "Syba SD-CM-UAUD USB Stereo Audio Adapter, C-Media Chipset, RoHS" ( [http://www.amazon.com/gp/product/B001MSS6CS/](http://www.amazon.com/gp/product/B001MSS6CS/) ).

My goal is to never hear another sound emitted from my laptop speakers again, I only want sound emitted through this USB Audio Adapter.

I can adjust Settings > Preferences > Sounds to select the USB Audio Adapter, but this only works for sound from Rythmbox and Mplayer (not Mplayer xine, VLC, and anything played in Firefox -which all emit sound through my laptop speakers-).

I have also tried typing "asoundconf set-default-card default" ['default' being the USB Audio Adapter] but this has had no effect?

Any advice on what I can try doing? I'm still fairly new to Ubuntu. Version used in sig ;)

---

### Post by matthewbpt on 2009-08-14
Type this in terminal

```
sudo apt-get install padevchooser
```

then hit Alt+F2 and type in 'padevchooser' and run, you should get a new applet in the systray with what looks like a headphone plug. Left click it and select volume control. Under output devices you should see two sound cards and a little dowward pointing arrow next to each, if you click on that next to the soundcard you want to be default you can tick it and make it the default sound device. Also in Settings > Preferences > Sound make sure Sound Events and Music and Movies are set to 'Autodetect'. padevchooser is quite a cool program, if you go to the playback tab in volume control you can see what applications are playing sound, change the volume between them independantly, and change what soundcard each application is playing from on the fly, try it =D

Matt

---

### Post by 982000971 on 2009-08-15
Very cool program Matt! Can't thank you enough. Solved all my problems and I even prefer it to Ubuntu's default volume control utilities :P

---

### Post by anduril11 on 2009-08-15
Worked beautifully for me as well. (I had a lindy audio USB 2.0 adaptor)

Cheers :)

---


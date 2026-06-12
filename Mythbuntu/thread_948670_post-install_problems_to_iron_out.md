---
title: "post-install problems to iron out"
date: 2008-10-15
forum: Mythbuntu
---

### Post by sir_inferno on 2008-10-15
hi guys,

i'm not sure how much of this is mythbuntu specific stuff, and how much is just beginner's teething problems, but i'm sure the moderators will use their discretion.

i've just installed mythbuntu, and so far so good. but i've run into a few snags. i'll give a bit of background in case it'll turn out to be pertinent. i have an msi mobo with a built in ati xpress 200 graphics card. i have this plugged into my hdtv via a component cable (which plugs into a header on the mobo) so i was expecting to have some major problems with this, but it seems to be acting as a "normal" monitor, so no specific problems there. i installed the proprietary ATI drivers via the handy dandy menu, and although i could set different resolutions thanks to that, when i selected "watch tv" the screen went black and that was the end of that. mplayer gave a nice error about not finding any screens, whilst vlc played things at around 90% smoothness. i then ran "sudo aticonfig --overlay-type=Xv" based on some google searches, and mplayer then worked, and i could go into the tv watching screen, but it was hideously slow and jerky. however when i reset my pc, and selected "watch tv" the screen would go blank and i'd be brought to the mythbuntu login screen. i _then_ changed my display to 1152*648@60 and i can now quite a fair few at full speed/smoothness, and the interface itself is nice and swish.

problems remaining,

1.) how does one boost the volume past the maximum set in mythtv? (i have to increase the volume on my tv a ridiculous amount to compensate)

2.) my tv capture card is the HVR-1100 from hauppauge (dvb-t), which has a remote built in. whilst the remote *does* work, only the arrow keys and play/rewind/stop buttons and what not are set. since i've seen quite a few places to change the remote settings, where should i go to change these?

3.) whilst watching tv, there's an intermittent problem where the video seems to bounce up and down by about 3 pixels at a rapid speed...any idea what this is?

4.) all of my channels show 30-35% signal strength, and quite a few that were viewable jerk-free on vista/xp, are suffering from very poor reception...again, any ideas concerning this?

many thanks!

---

### Post by Eric Boring on 2008-10-16
> **sir_inferno said:**
> hi guys,

4.) all of my channels show 30-35% signal strength, and quite a few that were viewable jerk-free on vista/xp, are suffering from very poor reception...again, any ideas concerning this?

many thanks!

Can't help with the other stuff, but I built a great antena following this video:
[http://www.metacafe.com/watch/762088/coat_hanger_hdtv_antenna_better_than_store_bought_amazing/](http://www.metacafe.com/watch/762088/coat_hanger_hdtv_antenna_better_than_store_bought_amazing/)
You build out of metal coat hangers and a piece of wood (1 by 4 or whatever). The only thing I had to buy was the UHF/VHF converter (about 3 bucks) and a few screws and washers. 
I mounted mine on the roof, below the 1950's-era aerial antenna. My neighbor says the aerial is acting as a reflector, bouncing the signals back to my coathangers. I don't know. His antenna has cooling racks for a reflector. He sent me these instructions too:
[http://www.dealandship.com/Visio-diyHDTV_Antenna.pdf](http://www.dealandship.com/Visio-diyHDTV_Antenna.pdf)
and
[http://www.hackaday.com/2007/02/01/diy-hd-antenna/](http://www.hackaday.com/2007/02/01/diy-hd-antenna/) 

Anyways, it seems like a lot of work, but it takes about an hour if you take your time. My reception went from 30% to 90% on almost all my channels.

Good luck!
-josh

---

### Post by Eric Boring on 2008-10-16
deleting duplicate posting

---

### Post by Andrew U.K. on 2008-10-16
Hi,

For the sound problem you need to run alsamixer. Type alsamixer in a terminal which then runs the program. I just turned everything up to 100% and it works fine.

Goodluck 
Andrew

---

### Post by Andrew U.K. on 2008-10-16
Same problem Duplicate

---

### Post by sir_inferno on 2008-10-20
> **Eric Boring said:**
> Can't help with the other stuff, but I built a great antena following this video

[...]

Anyways, it seems like a lot of work, but it takes about an hour if you take your time. My reception went from 30% to 90% on almost all my channels.

thanks, and looks pretty cool, however the reception isn't the problem (as in, the aerial signal being provided isn't), since both my TV, and the very same tuner when running in windows receive those channels with no problem.

> **Andrew U.K. said:**
> For the sound problem you need to run alsamixer. Type alsamixer in a terminal which then runs the program. I just turned everything up to 100% and it works fine.

cheers, i'll try that shortly

---

### Post by amphibem on 2008-10-20
> **sir_inferno said:**
> 
1.) how does one boost the volume past the maximum set in mythtv? (i have to increase the volume on my tv a ridiculous amount to compensate)

More specifically how to do this using amixer: go to the command line and try:

```
amixer -c 0 --sset Master 100%
```

That should set master playback volume of card 0 (the first card installed, I assume you only have one) to 100%.  Hopefully that syntax is right, I am going from memory. If not, type 'amisxer --help' and try and suss it out.


> **sir_inferno said:**
> 
2.) my tv capture card is the HVR-1100 from hauppauge (dvb-t), which has a remote built in. whilst the remote *does* work, only the arrow keys and play/rewind/stop buttons and what not are set. since i've seen quite a few places to change the remote settings, where should i go to change these?


The correct location is ~/.mythtv/lircrc. So at the command line type:

```
sudo nano ~/.mythtv/lircrc
```

and enter your password if required. That will bring up your lirc config file, if you need help editing it look [here]("http://www.lirc.org/html/configure.html#lircrc_format").

> **sir_inferno said:**
> 
4.) all of my channels show 30-35% signal strength, and quite a few that were viewable jerk-free on vista/xp, are suffering from very poor reception...again, any ideas concerning this?


I have a Nova T 500 and to get decent reception I need to turn on the Low Noise Amplifier. The command, from the wiki, is:

```
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 

```

Now I cannot find out if your card has the same amplifier, or if it is the same option to enable it. But I would try the above, and then go from there. For example, 'dvb-usb-dib0700' may need to be different. 

Hope that helps.

---


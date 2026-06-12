---
title: "HOWTO: microphone input on ASUS M2NE (k)ubuntu 7.10"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by wackston on 2008-01-03
Just to save anyone plodding through the same trial-and-error process I just spent an hour or two on...

The onboard audio  on an ASUS M2N-E seems to work perfectly 'out of the can' under 7.10.  Except... microphone input.   To get this working you need to:

- switch set the right card 'model' option for the driver (snd-hda-intel ) for MCP55 controller's and its connections on the ASUS board.

    options snd-hda-intel model=6stack-digout

I put this in /etc/modprobe.d/alsa-base but /etc/modprove.d/options or even a new
file in /etc/modprobe.d should work fine too.

- Switch the 1st input source to the correct microphone input (Mic and Front Mic are support) and enable capture on the 1st capture channel.

  I found KDE's kmixer worked well for this.  I ound the rear panel microphone input to work significantly better.  It might be worth trying model=6stack or even something else (see [http://alsa.opensrc.org/index.php/Hda](http://alsa.opensrc.org/index.php/Hda)) to see if the front can be brought up properly.  

- Set the microphone boost for the select microphone input to a level that suits your 'micro.


I found turning on analog mix and to enable the microphones as sources for output to allow interactive tweaking of the options was helpful for initial tuning / experimentation with switch settings.


-Andrew

---

### Post by DREMA on 2008-02-18
Woaa! Thanks dude! This also works with the Asus M2N32 SLI Deluxe/Wifi Mobo.
Finally I can use my skype :D

---

### Post by faultier on 2008-02-20
Wow!! It works!!! =)) thank u!
(laptop Fujitsu-Siemens AMILO)
but i have no "boost" option and i can hardly hear my voice in Skype. 
I'v looked 4 it  in Mixer--Edit-Preferences-.... 
How can i get it?

---

### Post by dikarst on 2008-03-21
I'm a newbie at assembling a PC from parts. Just now building a gaming PC with Asus M2N32 Deluxe SLI Wifi mobo (sounds like Drema's system), and can't get rear mic input to work. Front panel mic in works fine. I confess I don't understand Wackston's shorthand instructions but suspect he's running linux and I'm on WinXP, so not sure it'd apply in my case. More detailed help?

thanks!

---


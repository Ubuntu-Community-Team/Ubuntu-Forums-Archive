---
title: "USB Sound Card Doesn't Like DVDs"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Gen Beagle on 2008-07-17
Toshiba Satellite A135
Intel Celeron CPU
Integrated mobo HDA Intel sound
Ingegrated mobo Intel graphics

Ubuntu 8.04 Hardy

I did a clean install of Hardy on my laptop and everything appeared to work. I installed all the Gstreamer plugins and whatnot, followed the different Multimedia HowTo's on the support forums here.  The sound sounded good, and the ALSA volume control worked.  But then I tried to plug in some headphones to the built in port on the front of my laptop, and sound continued to pour out the built in speakers, ignoring the headphones.  I went back to the ALSA mixer and unmuted the headphone deal thing.  Tried again, and still the sound came out the speakers.

So I bought me a USB sound card, plugged it in, blacklisted the HDA Intel card so the USB card would always get the -0 spot.  (The speakers on the laptop don't sound with this one, I have to use headphones)  Everything works with the USB sound card except for DVD movies. At first, the didn't sound at all.  But then as I started playing around with the Preferences -> Sound options, the sound would start to play out the built in speakers, meaning that the DVD movies were using the HDA Intel card I blacklisted.

I uninstalled and reinstalled the w32 and libdvd codices, installed as many different media players as I could, like Ogle, VLC, and a couple more generic ones, but they all vomit the sound out the integrated card, rather than the USB card that everything else uses.

So what I would like to know is 

A) Is it possible for me to use the integrated sound card, but tell Hardy to find the audio ports on the front of the laptop

B ) if A isn't possible, is it possible to make the DVD movie sound come out the USB card like everything else?

Edit #1) Its not just DVDs anymore.  I logged in and out, and the system sounds played out the regular speakers, with the integrated card.  But the music, the internet, and Pidgin still use the USB card, which is the default card.

---

### Post by Gen Beagle on 2008-07-19
I am finding more and more that it is DVD's and KDE based applications like Amarok and Konversation that won't work, but the Gnome based ones do.  This isn't a huge problem, I use mostly the Gnome ones, but I prefer Amarok to Rhythmbox and it would be nice to get it, and the DVDs working correctly.

Does anyone know how to manually detect the headphone jacks on my onboard card?  That would still be the most convenient.

---

### Post by warp99 on 2008-07-19
Depending on your soundcard you can add a parameter when the module is loaded to manually choose the correct model so your headphones work. I would read the ALSA-Configuration file located in the '/usr/share/doc/alsa-base/driver' folder for more information.

Edit:

Here is an example:

I have an Asus Eee 701 that uses the hda-intel soundcard. In order for the headphones to work I have to specify the model. So in my '/etc/modprobe.d/alsa-base' file I have the string 'options snd-hda-intel model=3stack-dig'.

---

### Post by Gen Beagle on 2008-07-19
Thanks for the response :)

I had already tried that actually, to no avail.  But I tried it again for good measure, and noticed that in the drivers set to index=-2, that there was an "options snd-intel8x0m index=-2"

If I were to set all the rest to =-2, and then un set that one, might it work?

---

### Post by warp99 on 2008-07-19
> **Gen Beagle said:**
> Thanks for the response :)

I had already tried that actually, to no avail.  But I tried it again for good measure, and noticed that in the drivers set to index=-2, that there was an "options snd-intel8x0m index=-2"

If I were to set all the rest to =-2, and then un set that one, might it work?

Well snd-intel8x0m is a different module for a fax modem which is blacklisted, check the blacklist file and you'll see. The numbers -2 -1 0 1 2 are index number conventions so if you have multiple cards other modules don't steal the focus. Anything with a minus sign is very low priority.

If you're having trouble with setting the cards set the USB module to index=0 and the integrated card module to index=1 that way the first card has the focus. With this setup all you have to do is change the mixer device in the sound control dialog under 'System > Preferences' and pick the device you want.

Now KDE apps won't follow the Gnome settings, but by using 'alsamixer -c' to set the card the KDE apps would then work. Type 'man alsamixer' to see some more info.

And finally I found a bug listed for your particular laptop and the headphones issue with a possible workaround:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109838](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109838)

The workaround is to use 'options snd-hda-intel model=lenovo' as the parameter.

Edit:

For this to work both the USB and integrated alsa modules must not be blacklisted.

---

### Post by Gen Beagle on 2008-07-19
That bug was actually the problem, and the workaround worked to perfection!  Thanks for the help, Ubuntu is on my hard drive for good now :p

---


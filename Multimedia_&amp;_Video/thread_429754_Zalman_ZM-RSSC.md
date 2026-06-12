---
title: "Zalman ZM-RSSC"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by KeitaroBR on 2007-05-01
Hi,


Did anybody have success setting up a "Zalman ZM-RSSC External 5.1 Sound Card" with Alsa? I've been able to make it work but without the 5.1 support, only basic stereo. I've followed the docs on Alsa project's page, but had no success. 

It is an USB card with a Sonix chipset.


Regards,
Rodrigo

---

### Post by silverballer47 on 2008-01-04
Hey Rodrigo,

Could you link me to the instructions you followed on ALSA's page? I have exactly the same problem.

I'll try those out and give you my input. My SB card works perfectly on a desktop machine running Ubuntu, but I really want to get this Zalman card to work.

Regards,

Varun

---

### Post by silverballer47 on 2008-01-04
Success!!!!!!

Attached is my asoundrc file. Check the "hw:1,0" line for your settings. In my case, my USB Zalman card was my second sound card.

Good luck, Rodrigo. Tell me how it goes.

I'm not sure if it's truly Dolby 5.1 (as in, whether it would stand up to surround sound effects in a 5.1 movie), but it is duplicating the stereo channel to all other channels now, which is really all I needed.

Let me know how it goes!

Varun

---

### Post by jodydewey on 2008-01-05
Could you guys send me the link to the ALSA file?  I have the Zalman RSSC and it works in stereo but I have no idea if it works in 5.1

---

### Post by askewtos on 2008-05-06
I have this very same sound card and it seems to detect fine, however no sound comes out when I play any sound or video on it.

The speakers definitely are plugged in (I'm a linux noob but not a tech noob) and the usb has powered the external soundcard but no love on the actual sound front.

I'm running Ubuntu 8.04 LTS Hardy Heron on a Dell Poweredge SC440. 

Any assistance would be much appreciated. 

Cheers,

Askew

---

### Post by Louis XVI with a gun on 2008-06-06
Please, Can you do a how to, to make the 5.1 working please ? 

I' ve used the silverballer47 's asoundrc but the card doesn' t work anymore after that :(

---


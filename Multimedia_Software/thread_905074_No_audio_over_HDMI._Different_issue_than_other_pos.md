---
title: "No audio over HDMI. Different issue than other posts"
date: 2008-08-30
forum: Multimedia Software
---

### Post by wfeltmate on 2008-08-30
I have an ATI card, presently a mobility 3200, in my new HP dv5 laptop and while ubuntu installs fine, fglrx installs with no problems, audio over hdmi does not work.

It recognizes the card fine, aplay -l lists the card and device, a driver is loaded for it and it shows up as an option in System > Preferences > Sound and in the volume control app. The problem is that no volume slider exists.

This isn't limited to just this laptop, as it also happened on my desktop as well, which had a Gigabyte motherboard, using the 690 chipset as well as a HD2600 XT PCI-e card I installed, and the same issue occurred with both the card and the onboard chipset.

I believe this may have something to do with Hardy, as when I was using 7.10 I was able to have sound over HDMI perfectly. When I upgrade from 7.10 to 8.04 it worked fine, too, but each time I did a clean install of 8.04, this issue has always appeared and I have found no way to solve the problem.

Has anyone else experienced this, and if so, has anyone found a solution?

---

### Post by hobo89 on 2008-10-07
I also have this problem. After finally managing to install the driver for my 4850 card, I have dual monitor set up. But there is no sound through the HDMI connected to my TV. I have gone into 'System > Preferences > Sound' and selected ATI HDMI under Sound Playback, click Test and get no sound. The other options work fine.
Anyone have any ideas yet?
Thanks

---

### Post by stromdal on 2008-10-07
No real help from me, but I have a few questions:

Does the computer come with a HDMI output, or are you using a DVI output with DVI->HDMI adapter?

Assuming you have an actual HDMI output:
Is the HDMI output really a video+audio output, and not just a video output? Isn't the HDMI output on a graphics card? Does the graphics card also function as a sound card, or does the graphics card pipe the sound from the sound card to present a video+audio HDMI signal?

Regards
/stromdal

---

### Post by hobo89 on 2008-10-07
> **stromdal said:**
> No real help from me, but I have a few questions:

Does the computer come with a HDMI output, or are you using a DVI output with DVI->HDMI adapter?

Assuming you have an actual HDMI output:
Is the HDMI output really a video+audio output, and not just a video output? Isn't the HDMI output on a graphics card? Does the graphics card also function as a sound card, or does the graphics card pipe the sound from the sound card to present a video+audio HDMI signal?

Regards
/stromdal

The 4850 has 2 DVI outputs, so the HDMI cable is connnected to the graphics card by a DVI>HDMI adapter. I'm card does not have any audio ouputs, so i guess it doesn't function as a sound card, just pipe the sound from the sound card?
When I was using Windows Vista the HDMI sound output worked fine, just had to change the default sound output to HDMI. But I can't seem to find any option like this in Ubuntu.

---

### Post by stromdal on 2008-10-07
> **hobo89 said:**
> The 4850 has 2 DVI outputs, so the HDMI cable is connnected to the graphics card by a DVI>HDMI adapter. I'm card does not have any audio ouputs, so i guess it doesn't function as a sound card, just pipe the sound from the sound card? When I was using Windows Vista the HDMI sound output worked fine, just had to change the default sound output to HDMI. But I can't seem to find any option like this in Ubuntu.

AFAIK, a DVI output does not deliver sound. Ever. Period. So if you're using DVI output and a DVI->HDMI adapter to connect your computer to a TV you should not be able to use the HDMI cable as a sound transmitter, you WILL need a separate audio cable. If you are certain that you used this setup with Windows Vista before and it delivered sound then I am baffled and can offer no further assistance.

Regards
/stromdal

---

### Post by hobo89 on 2008-10-07
> **stromdal said:**
> AFAIK, a DVI output does not deliver sound. Ever. Period. So if you're using DVI output and a DVI->HDMI adapter to connect your computer to a TV you should not be able to use the HDMI cable as a sound transmitter, you WILL need a separate audio cable. If you are certain that you used this setup with Windows Vista before and it delivered sound then I am baffled and can offer no further assistance.

Regards
/stromdal

I've just checked to make sure it is a DVI connection on the graphics card (it is) and checked every single cable to make sure there is nothing else going to the TV that could be carring the audio that I might have forgotten about (there isn't). Also booted into Vista to test the sound through the HDMI, and it is still working. Doing a google search it would seem you're right about DVI not carrying audio. So now I'm even more confused myself. There is really no way the audio is going from the DVI port on the graphics card, through the adapter and to the HDMI cable? I am positive there is no other connection to the TV.

Edit: Just been searching google, it seems DVI cables are actually capable of carrying audio, but DVI devices generally don't output audio. Apparently the DVI to HDMI adapter provided with the 4850 card is different to other adapters in that it tells the graphics card to send audio with the video. I've yet to find an official source for this but it is mentioned on various forums.

---

### Post by stromdal on 2008-10-08
Cool. I didn't think it was possible for any DVI device to output audio, I guess there are exceptions to the rule...

Would be interesting to see if you could get this to work in Ubuntu. If it works in Vista it SHOULD be able to work in Linux, but I guess you'll need some expert help with this one.

---


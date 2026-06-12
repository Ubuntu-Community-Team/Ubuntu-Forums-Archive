---
title: "Help getting a Hauppage Nova t-500 working"
date: 2008-08-05
forum: Mythbuntu
---

### Post by hellaid on 2008-08-05
Ok so i've got myth installed and working on my system, the problem is that I can't get it to recognise the card properly, the remote works pretty well (not perfect but not complaining atm) the problem is getting the card to work properly, i've tried following the page on linuxtv.org about geting it install but some of it just throws up errors, I can set it scanning channels but not find any, I live in the UK so trying to get it picking up freeview.

Can anyone help me get it working properly please?

---

### Post by wyliecoyoteuk on 2008-08-05
You need to enable the onboard LNAs

enable LNAs
Enabling the LNA (Low Noise Amplifiers)
open a terminal:  open “applications menu”, select “accessories” , then “terminal”

Type:
sudo nano /etc/modprobe.d/options

This opens the text editor called “nano”, and opens the “/etc/modprobe.d/options” file for editing

add this at the end of the text file:

#enable LNA
options dvb-usb-dib0700 force_lna_activation=1
#disable 2nd tuner suspend
options usbcore autosuspend=-1 

Press CTRL-O to save it, hit “y”, then CTRL-X to exit.

Then reboot.

---

### Post by hellaid on 2008-08-05
Ok i've managed to make it start scanning for channels (didn't before) and its not picking any up, just comes up with no signal or no tables.

Anything i'm missing here?

---

### Post by SniperKIng on 2008-08-05
Well is your ariel good enough? I couldnt pick up any channels with my previous arial even though it works with the tv in the same location

---

### Post by wyliecoyoteuk on 2008-08-06
Have you enabled the LNAs as shown above?
Without that, I only got 4 channels, and none worked.
After that and a reboot I got 96 (including a load of audio)

Can you get freeview on anything else?
Until recently I had to use 2 signal boosters to get freeview- now they have boosted it, if I use any, the signal is blown away
Have you set the frequency to europe-west and the country to uk?

---

### Post by Nikas on 2008-08-06
I had to add 6 muxes myself (manually) before my cards could find any channels. But that's in Sweden. ;)

---

### Post by SiHa on 2008-08-06
Now, this may be a stupid question, but bear with me.

Have you set the card type to "DVB 3.1 (something or other)". I ask because I stupidly set mine as a V4L (Analogue) type, Mythtv gets a response to the probe, and happily accepts it as a valid card. When attempting a scan, it finds nothing (not surprisingly) after a very long time.

With the on-board LNA activated as above, and card type correctly set mine works fine.

---

### Post by wyliecoyoteuk on 2008-08-06
> **SiHa said:**
> Now, this may be a stupid question, but bear with me.

Have you set the card type to "DVB 3.1 (something or other)". I ask because I stupidly set mine as a V4L (Analogue) type, Mythtv gets a response to the probe, and happily accepts it as a valid card. When attempting a scan, it finds nothing (not surprisingly) after a very long time.

With the on-board LNA activated as above, and card type correctly set mine works fine.

Good point, I did that too, mainly because the firmware is only loaded on a cold boot, so first install doesn't show the card. On rebooting, I could select the correct card.

---


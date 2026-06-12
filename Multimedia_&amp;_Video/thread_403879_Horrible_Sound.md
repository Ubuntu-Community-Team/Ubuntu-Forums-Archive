---
title: "Horrible Sound"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Navyblue on 2007-04-07
I just got a Creative Sound Blaster Digital Music SX. I am running Edgy.

Only the right channel has sound, and it is cracky, distorted and soft. In Windows it sounds alright (although it keeps popping when playing CD).

I only get the mixer to show the full correct set of slider once, other time it would show my SB Live slider (which is still on the machine), or a partial set of the slider that doesn't work (no volume change when slider is dragged).

Please let me know what information to provide.

Thanks.

---

### Post by mgmiller on 2007-04-07
A lot of people report problems with soundblaster cards.  They do not support linux very well.  The right channel only sound is a common complaint.  I think you would have better luck with a turtle beach or other brand card.  Search these forums about sound cards to get a better idea on hardware compatibility.

---

### Post by deadgobby on 2007-04-07
>>A lot of people report problems with soundblaster cards. They do not support linux very well. The right channel only sound is a common complaint. I think you would have better luck with a turtle beach or other brand card. Search these forums about sound cards to get a better idea on hardware compatibility.

 What are you talking about. A lot of people use Creative Labs Sound Blaster.  I have one and never had a problem with them running any type of Linux O/S. Most like can be the ALSA. To install ALSA to get more full control for your SB.  
1.st check to see if your disable your one board sound card in the BIOS. This will have all sound going through the sound card.
2. Install ALSA mixer. You can install it through synaptic or through the terminal. You can install GNOME ALSA Mixer through Synaptic.
Or you can install the Terminal one by opening up the terminal and type in 
sudo aptitude install alsamixer

Once installed. Type in the terminal

alsamixer

Here is what the two look like 


Gobby

---

### Post by Navyblue on 2007-04-08
The board sound card is disabled in the BIOS. But I have another PCI sound card that is not disabled, that one is working well.

I have alsamixer installed, but currently it is showing the PCI sound card's sliders. At time, the alsamixer would display the sliders of this intended sound card, which is a USB external sound card.

I wish to keep the PCI sound card installed if possible as it has a hardware midi processor.

Thanks for all the replies. :)

---

### Post by deadgobby on 2007-04-08
That is why you are haven problems. The usb and the pci sound card. You only can use one. It confuses the O/S and so it may split up the sound between the two. Just right click on the spearker icon and choose what ALSA mixer to use. Either the CA******  or the other.  Can you can select  at the down arrow tab key.

---

### Post by Navyblue on 2007-04-08
There is another complication. I tried uninstalling and installing ALSA again. Now I get this:

```

$ alsamixer
ALSA lib conf.c:1587:(snd_config_load1) /home/navyblue/.asoundrc.asoundconf:8:23:Unexpected char
ALSA lib conf.c:2827:(snd_config_hook_load) /home/navyblue/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2691:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3054:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument

```

---


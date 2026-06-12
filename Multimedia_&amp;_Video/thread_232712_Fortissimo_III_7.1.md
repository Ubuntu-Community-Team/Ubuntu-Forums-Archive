---
title: "Fortissimo III 7.1"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by Cyfr on 2006-08-09
Hello I have a server which i'd like to be controled remotly from my laptop to play music when im in my bedroom.

Both the laptop and the server are running Ubuntu. The server originaly had server edition but i've done a full install with Gnome etc for now while I try and sort this problem out as I find it much easier to solve something with a GUI.

The problem is, I have my card plugged in, and my speakers all wired in to the card, but I seem to get no sound output. I can't really explain any further :p

Thankyou.

ps. If you give me commands to produce outputs that you require, then I can do that no problem. :)

---

### Post by Cyfr on 2006-08-09
When I change my device to onboard sound and plug my front cable in to it, it works fine and plays back. If i change the device to "Sound Fusion CS46xx (Alsa mixer)" I get no sound. I've unmuted everything in alsamixer.

When I do mute and unmute stuff I can hear a buzz as I click the button which shows there is power going to it... and my system seems to detect it alright, theres just no sound being outputted.

---

### Post by Cyfr on 2006-08-09
I dont know how, but sound is suddenly working after a reboot. However the playback only seems to be through the front speakers and not the rear.

Do I plug the rear wire into the 'surround' socket on the sound card? Thats where it is now and my music playback is only through front.

---

### Post by Cyfr on 2006-08-09
After rebooting again it refuses to work, and I changed no settings its just not outputing sound anymore..

---

### Post by Cyfr on 2006-08-09
I reinstalled alsa and it started working again, for a brief period, and now its not working again.

I dont know what the problem is, but it seems like its not being default selected when the computer starts up?

---

### Post by Hasen_A on 2006-11-05
Hello I have the same sound card ( Fortissimo III 7.1 ) and am noticing bad sound quality. The quality with my speakers under Windows XP with Winamp is way better and has more bass. Hercules isn't distributing any Linux drivers :(. So I was wondering, is there any better driver than the default one?

I don't know where I can readout the driver (settings) for my sound card in order to paste it here.

Also, the output signal seems to be really low under Ubuntu. Under Windows my  a volume setting of "-40 dB" is loud enough. To achieve the same thresh hold in Ubuntu I have to crank it up to "-20 dB" and the background noise of the speakers is hearable -> bad sound quality. Is there any way to uppen the output signal via software?

Thanks in advance for any help

---

### Post by kino13 on 2006-12-12
> **Cyfr said:**
> I reinstalled alsa and it started working again, for a brief period, and now its not working again.

I dont know what the problem is, but it seems like its not being default selected when the computer starts up?

Hello, I had a similar issue with my computer(s). The problem that you may have is that the motherboard in your computer already have an integrated sound card. Ubuntu detects and enable that one randomly when you reboot. Look in google for "ubuntu two sound cards" for more info.

In my case I disabled the loading of the modules of the integrated card in the blacklist file under /etc/modprobe.d. 

Hope that helps!

---


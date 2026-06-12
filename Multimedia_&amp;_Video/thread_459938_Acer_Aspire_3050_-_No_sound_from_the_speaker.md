---
title: "Acer Aspire 3050 - No sound from the speaker"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by iska3 on 2007-05-31
I have installed Ubuntu 7.04 but I do not have sound from the speaker.
Could anyone helps me ?

---

### Post by crispy_420 on 2007-06-02
Did you check your sound setup by right clicking the volume icon in panel. Also is there a hardware switch to adjust volume. It may be hidden be a key combo like the FN key (on bottom right near CTRL and ALT) plus one of the F keys (F1, F2, etc.). The key should a speaker icon on it.

---

### Post by rmucc01 on 2007-06-03
I'm also using ubuntu 7.04 and having the same issue. I have the sound icon on the panel bar but no sound out of the speakers. I updated but no luck with the sound.

---

### Post by vkrmsv on 2007-06-05
i run feisty on acer 5583.
i have the same problem.
my webcam is also not being detected.
any solutions?

---

### Post by squeeky on 2007-06-07
Yep this seems to be some sort of global problem with this model of acer laptop and posibly the sound chipset. I think its possible that acer laptops use some kind of software switch to recognise when headphones are pluged in. When in linux this software switch just defualts to jack out and there is no way to change it. Ill look in to this over the next few days and ask acer what they say.


PS you can still use headphones
Squeeky

---

### Post by kijjaz on 2007-06-10
I've found out that enabling the "Surround" channel in the volumn control
will send audio to the notebook's speaker.

Just check out the Preferences in volumn control and place a check mark at [ ] Surround.

---

### Post by rmucc01 on 2007-06-11
I looked under Sound - Edit - Preferences but do not see Surround. I think I'm looking in the wrong location.  

I also looked under  system - preferences - sound  but still no Surround. 

Any help would be appreciated

---

### Post by carnytom on 2007-06-23
After fresh install I had 2 sound adapters.  

1 being Conexant ID 2bfa (OSS Mixer) 

I also had an Alsa one which is now gone after doing the 77 updates that were waiting. 

the surround sound option WORKED on the Alsa device when it was there..... 

But now i'm back to square 1 with the sound.

---

### Post by rob-acer on 2007-07-01
I have an Acer Aspire 3050-1150 and I had the same problem.  The sound worked fine when using the 7.04 LiveCD and right after installing it (I had to unmute Surround in the Volume Control menu), but after running the auto updates, the sound went dead except when hooking up headphones.  The Surround option also disappeared from the Volume Control menu.

After some research, I found that clearing the contents of the asound.state file in /var/lib/alsa and then rebooting fixed it (I had to unmute Surround again), but after rebooting again, it reverted back.

Anyway, I found the fix at: [http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/]("http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/").

I added two lines to the end of the alsa-base file using sudo gedit.  This file is located in /etc/modprobe.d/alsa-base.  Here are the two lines:

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

I now have full sound after reboot and I didn't even have to manually unmute Surround in the Volume Control panel.  Hopefully, this will work for anyone else with an Acer 3050 having this problem.

- Rob

---

### Post by carlao2005 on 2007-07-05
Hello people,
 
Very sorry for this off-topic, but seeing people discussing about the sound problem, it seems that you did not have any problem connecting this notebook on the internet... I use adsl, but pppoeconf says it found eth0, but none adsl modem... At university (where there is dhcp), other notebook (hp pavilion) I can just plug it and it on the net. But this acer not...

Lspci says there is a realtek network card.

Any hint?

Thanks in advance, and sorry again for the off topic. But this problem is driving me crazy! :o

Best regards.carlos

---

### Post by newpants2003 on 2007-07-24
> **rob-acer said:**
> I have an Acer Aspire 3050-1150 and I had the same problem.  The sound worked fine when using the 7.04 LiveCD and right after installing it (I had to unmute Surround in the Volume Control menu), but after running the auto updates, the sound went dead except when hooking up headphones.  The Surround option also disappeared from the Volume Control menu.

After some research, I found that clearing the contents of the asound.state file in /var/lib/alsa and then rebooting fixed it (I had to unmute Surround again), but after rebooting again, it reverted back.

Anyway, I found the fix at: [http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/]("http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/").

I added two lines to the end of the alsa-base file using sudo gedit.  This file is located in /etc/modprobe.d/alsa-base.  Here are the two lines:

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

I now have full sound after reboot and I didn't even have to manually unmute Surround in the Volume Control panel.  Hopefully, this will work for anyone else with an Acer 3050 having this problem.

- Rob

which part did you followed from the link you post?
thanks.

---


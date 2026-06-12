---
title: "Sound trouble on Dell Latitude D630"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Admiral_deLorei on 2008-12-05
I'm new to Ubuntu and Linux in general, so forgive a newbie his lack of knowledge. I'm learning.

I'm dual-booting Ubuntu 8.10 and Windows XP on my Latitude D630, and I've noticed some sound issues, mainly being that it doesn't work all of the time. A quick scan of these forums shows I'm not the only one, so I tried to fix it using the myriad of ways described in different topics. They didn't work however.

The first problem with the sound was that it would work upon startup, but after a certain amount of time it stopped. This was easily fixable by rebooting. Not convenient, but at least I knew what was wrong.

However, after using some fixes in the topics, my sound doesn't work at all, and every time I click on the speaker icon on the panel, I get an error saying that it can't pick up my sound card. I've scowered the topics since then to try and find a fix, but there doesn't seem to be a topic quite like my issue.

I've checked whether my card is supported by ALSA, and it doesn't have it listed. However, since the sound worked before, it must have some support for it.

Also, I'm sorry for no specifics, but I'm currently working in Windows because I need a program off of it for school. After I boot into Linux I'll repost whatever information you require.

Thanks!

---

### Post by psyke83 on 2008-12-05
> **Admiral_deLorei said:**
> 
The first problem with the sound was that it would work upon startup, but after a certain amount of time it stopped. This was easily fixable by rebooting. Not convenient, but at least I knew what was wrong.

Since the release of Hardy, Ubuntu uses the PulseAudio sound server by default. It does not replace ALSA (i.e. the ALSA kernel modules are still used), but it does replace ALSA's software mixing device (dmix). Unfortunately, PulseAudio is not configured fully on a default installation, and some applications need tweaking to ensure that they work with PulseAudio correctly - if not, then applications will conflict and sound mixing will break.

Please read (and if you're willing, follow) [this]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by Admiral_deLorei on 2008-12-06
So, after scowering the forums even more (and trying the above link), I think I realize the problem. For some reason, Ibex won't recognize the sound card in my Dell. It's an Intel 82801H card, if that means anything. The above link requires my sound card to be recognized.

It seems other people have had trouble with this card, and the ALSA support wiki says it's not supported by ALSA. However, as stated in my last post, it has to have at least some support because I originally had sound for the inital few minutes after boot.

I really want to have sound on my linux partition, as I don't really use my XP partition that much. Unless I want to sync my ipod, though I know that there are programs for that for linux.

Please, I really want to get this to work. If anyone needs any output from the terminal posted, just give me the command and I'll repost it.

Again, thank you from a linux newbie.

---

### Post by Admiral_deLorei on 2008-12-06
So, just another update. I rebooted into the last kernel version (ending in a .7, I think) and the sound works. However, it doesn't automatically connect me to the wireless internet. I have seen topics about fixing wireless cards, so I shall check those out as well. For the time being, though, it's a cruel choice. Sound in one kernel version, and internet in another...

---

### Post by Tweak42 on 2008-12-08
I also have a D630 but have not had any sound drop out problems in 8.04 or 8.10.  I don't use sound that much except watch the occasional youtube vids. 

I do sometimes have the wireless detection problem at school, but not at home so I believe it has more to do with the school network hardware than my laptop.

---


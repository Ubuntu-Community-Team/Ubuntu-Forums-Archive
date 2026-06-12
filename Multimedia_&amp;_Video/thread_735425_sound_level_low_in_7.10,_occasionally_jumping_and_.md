---
title: "sound level low in 7.10, occasionally jumping and breaking"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by sp3ctum on 2008-03-25
Hi. I've only recently started using Ubuntu, and am slowly catching up to it.
Now I have a problem with my audio. I see a lot of people have complained about a sound level too low here, and I've tried to follow those threads, but I feel I have a different problem.
In a nutshell, I have two cases that occur: (I'm yet to figure out a pattern, for now it seems to me they occur randomly, though one is always present)

- my sound level is too low
     - I tried to set it using alsamixer, but I can't change the master level at all.
- occasionally I hear (on the computer :) ) clicks, and when this case happens the sound level keeps boosting up to being real loud for a split second.

I'd really appreciate any help! I'm more than willing to post info about my computer, but please tell me how I can fetch it.
I'd have posted useful stuff beforehand, but I didn't really know what to post. :confused:

edit: for starters, my laptop is a Toshiba Equium A100-147. I have a dual-boot configuration with win xp media center edition, and the sound works perfectly in win xp.
In alsamixer, I only have five bars, of which 2 work. The working ones are PCM and Mic, the non-working ones Master, Caller I and <Off-Hook>.
Alsamixer reports my card as "HDA Intel" and my Chip as "Realtek ALC861".

---

### Post by sp3ctum on 2008-03-26
I just started my laptop for the day, and surprisingly the sound was perfect. I was amazed at this randomness, so I decided to test it.
Now I'm in case #2 again. The sound seems like it's on a low level, and it keeps on jumping to a higher level for a short while, and then going back to being low.
I'll keep on trying to comb online solutions, and waiting for replies.:confused:

edit: after 2 hours, I've reinstalled my alsa drivers, and went over the entire comprehensive sound problems guide with no result.
At the moment the sound is very low, but no jumping is present. I plead replies of help :(

---

### Post by sp3ctum on 2008-03-26
I think I've found a [SIZE="7"]solution[/SIZE]. Here's how you can trace my steps if you need to know:

1. I followed the guide here: [https://answers.launchpad.net/ubuntu/+question/18144](https://answers.launchpad.net/ubuntu/+question/18144)

2. which in turn told me to follow the guide here: [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
    - this can be found here forever, in case it's lost: [http://www.google.com/search?q=cache:U-0bmqtCwx8J:linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/+http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/&hl=en&ct=clnk&cd=1&client=opera](http://www.google.com/search?q=cache:U-0bmqtCwx8J:linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/+http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/&hl=en&ct=clnk&cd=1&client=opera)

3. The guide told me (after reading all of it) to enter this command in the terminal:

sudo apt-get install linux-backports-modules-generic

4. I rebooted, and my heart filled with joy as I heard the drum at the logon screen with full volume.
 I tested playing some mp3s, and they worked perfectly.
5. After three more restarts I concluded the problem is no longer persistent.

edit: should this thread be marked with the [solved] tag ? By whom?

---


---
title: "Possible HOWTO: headphone support in Asus A6 series"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Anvilfolk on 2007-03-21
Hi everyone! First post :)

I've been trying to get headphone support for my Asus A6VM for a long time. Normal sound works perfectly normal, but I had no Headphones slider in alsamixer (or Gnome Volume Control). Whenever something was plugged into the out-jack, no sound would come out at all. I tried alsa-utils + alsa-driver + alsa-lib versions 1.0.14RC3, 1.0.13 and 1.0.12.

I am currently running 1.0.12 - but do not change/recompile another version unless you've tried this with your current version, it might just save you a lot of work.

If you do not have sound support, try adding:

options snd-hda-intel model=z71v position_fix=1

to /etc/modprobe.d/sound, altough I believe you can probably also append it to /etc/modprobe.d/alsa-base. Position_fix is optional, apparently it can increase sound quality in some cases.

That's it, plus a reboot, and it should work.

If anyone else with the same problem could try this, and let me know if it worked - and with which alsa version, I'm sure it'd be appreciated. Right now I'm too scared to even try upgrading back to the latest version of alsa!

Hope it helps someone!

Also, check out [this]("http://ubuntuforums.org/showthread.php?p=2310616") thread for more information.

---

### Post by T-Mic on 2007-03-24
It works!  I had the exact same problem as you.  

My system is an Asus F3JM, and I'm running ALSA 1.0.14c3.  I added that line to /etc/modprobe.d/alsa-base and now everything is working fine.  

I'm also curious if you know why that line works, and what those arguments actually do.

Anyway, thanks a lot.

---

### Post by Anvilfolk on 2007-03-25
Great! It helped someone! Heheh.

I noticed something here though. There's a lot of background noise with the headphones, which I thought I had on Windows too, but it turns out I don't. So if anyone knows how to solve THAT problem, I'd appreciate any tips.

Could you check if you have that too?


As for the line, I'm not sure about position_fixr, but I think model tells alsa what kind of specifications your sound card can handle. There are a LOT of models you can set there - I might just try them all out. Check [here]("http://ubuntuforums.org/showthread.php?p=2310616"), for example. Also, position_fix isn't necessary, I'll have to try that out without it too, to see if it improves the sound I get.

There should definitely be a standard resource for these kinds of problems.

If you find out anything interesting, let me know :)

---

### Post by T-Mic on 2007-03-25
No background noise on mine.  I can't think what the problem could possibly be.

As for the parameters, I don't think I'm going to toy around with them for a while.  I'm too happy to be listening to my music library again.  Thanks for the info though.

---

### Post by Anvilfolk on 2007-03-26
Just found out what the background noise was: the CD mixer was set too loud. I turned it down to 0, and now I have perfect sound.

Also, I tried without position_fix=1, and it yielded the same results, and I couldn't get any audio output with w810 as the model, so z71v seems to be the best choice so far :)

---


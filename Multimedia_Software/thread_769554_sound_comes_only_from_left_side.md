---
title: "sound comes only from left side"
date: 2008-04-26
forum: Multimedia Software
---

### Post by brazzmonkey on 2008-04-26
hello there,
i recently upgraded to hardy and encountered a few troubles. one of them is that sound seems to come out from left speakers only.

sound card is ```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

``` on an ACER laptop
it used to work fine on edgy, feisty and gutsy, but in hardy i have much fewer controls available in kmix and alsamixer.

as far as i remember, on previous releases i could tune the sound balance using 2 sliders (i.e. one would set the volume on the left side, the other on the right side).

now in hardy i have no sound coming from the right side, and i can only set left side volume using PCM and/or Front slider.

any hints ?

---

### Post by brazzmonkey on 2008-04-27
no idea ?

---

### Post by wieman01 on 2008-04-28
Same problem here... Odd.

---

### Post by rysh on 2008-04-28
I have the same problem with Kubuntu 8.04

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

You already made a bug report?

---

### Post by curtis1552 on 2008-04-28
Has anyone checked their alsamixer settings to make sure that the right channel is engaged? (not muted or reduced volume)

---

### Post by wieman01 on 2008-04-28
Yes, first thing I did. Negative. Both channels engaged.

---

### Post by rysh on 2008-04-28
> **curtis1552 said:**
> Has anyone checked their alsamixer settings to make sure that the right channel is engaged? (not muted or reduced volume)

Hehe, lazy me did not do this. I replied on this forum, because i did see another person had the same problem as i had, and because i had no problem with sound under the 7.10  version, i thought it was a bug in (k)Ubuntu 8.04. (Also because i heard there was a new sound system)

Now i have sound on both sides again ... thanks ... 

Still strange and annoying to find out this is not as it should be, although a very minor problem for me. 

In Alsamixer "Front", "Surround" and  "Center" only had one side enabled. 


Thanks anyway.
greetz

---

### Post by wieman01 on 2008-04-28
In fact sound is OK in Amarok for instance, it's just that Skype does not want to play along.

---

### Post by brazzmonkey on 2008-04-28
ok, so
rysh solved his problem,
wieman01's issue only happens with skype.

mine is a general issue, affecting any multimedia app. I still don't understand why i have fewer controls than i had with Gutsy. see screenshot. i can't seem to find a way to control sound balance.

---

### Post by wieman01 on 2008-04-28
Strange thing, really. My card is a:
> ICH4 - Intel 82801DB-ICH4
Weird, weird, weird... problem only appears in connection with Kubuntu and Intel sound devices?

---

### Post by brazzmonkey on 2008-04-28
well, the same happens using GNOME on my computer...
imho it's alsa-related so i don't think this is kde/kubuntu specific.

btw, i noticed my front speakers don't work either. it's like my sound system is now considered as mono.

i need to find my headphone to check if headphone output is affected as well.

---

### Post by brazzmonkey on 2008-04-28
our fellow Rysh found this
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202361](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202361)
this has some common points with our issue.

---

### Post by wieman01 on 2008-04-29
Thanks, brazzmonkey. We're getting closer.

---

### Post by brazzmonkey on 2008-04-29
fyi i recompiled alsa modules and tried to change snd-hda-intel options in /etc/modprobe.d/alsa-base. didn't help.

---

### Post by wieman01 on 2008-04-29
I wish I could help you a little, but this is not my field I am afraid... Thanks for you support, mate, a lot of people will appreciate it.

---

### Post by Zorael on 2008-04-29
Mine is an Acer 9815 and I had the same issue on my Kubuntu 8.04, but adding options to /etc/modprobe.d/alsa-base fixed it. [http://ubuntuforums.org/showthread.php?t=773497](http://ubuntuforums.org/showthread.php?t=773497).

---

### Post by brazzmonkey on 2008-04-29
damn, i should try again tonight then, but "options snd-hda-intel model=acer" was already set when i first notice the issue. i also tried "acer-aspire", but to no avail.
you bring me hope, though. i'll let you know.

---

### Post by brazzmonkey on 2008-04-29
ok, so tonight i came back home, started my computer and realised i got all my controls back again.
yesterday, in my last attempt to solve the issue, i added ```
options snd-hda-intel model=6stack-dig
``` to my alsa-base. although it didn't work yesterday, it now does&#8230; i guess it's sorted out then.

thanks everyone for support !

---


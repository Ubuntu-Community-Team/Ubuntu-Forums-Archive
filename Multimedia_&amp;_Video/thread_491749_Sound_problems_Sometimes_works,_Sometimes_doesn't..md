---
title: "Sound problems: Sometimes works, Sometimes doesn't."
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by Metric on 2007-07-04
Hello friends,
Sometimes, when I start my computer up, it boots without sounds, and I have to restart it(sometimes multiple times) to get it to work again. I have no clue what the problem is, it's been like this for a while. I'd appreciate it if anyone could help me, thanks in advance.

I have a Sound Blaster Audigy sound card.

---

### Post by phansiizwe on 2007-07-05
Have you got an onboard sound card on your motherboard as well? If so, you might try disabling it in the BIOS.

---

### Post by Bastaard on 2007-07-06
I'm having similar problems (also Audigy 2) and I found that Ubuntu seems to decide which sound card to use (onboard or Audigy) in what seems to me a completely random way. The first couple of Ubuntu boots the sound worked just fine, then it stopped working but I found that it used my onboard card so I plugged my stereo into that one and I had sound. But this last reboot the Audigy is suddenly the preferred sound card again. At sound settings the Audigy has been the standard device all the time.

I noticed that the sound card that is being used is the sound card that is listed as 0 when I doubleclick the sound speaker icon and click file->change device.

But no solution...

---

### Post by Metric on 2007-07-07
> **phansiizwe said:**
> Have you got an onboard sound card on your motherboard as well? If so, you might try disabling it in the BIOS.

I believe this is my problem. Can anyone help me on how I'd go about disabling the soundcard on my Motherboard?

---

### Post by phansiizwe on 2007-07-08
Hi Metric,

Could you tell us what motherboard you have? Maybe I can download the manual somewhere to point you in the right direction.

When you want to try accessing the BIOS yourself, the first thing you have to find out is how you enter the BIOS on your motherboard. While your computer boots, can you see any messages like "Hit Esc to enter setup..." or "F2 to enter setup..."?
This will tell you which key to press during boot to enter the BIOS.
When you successfully enter the BIOS, **be careful**, only change something when you know what you are doing.

Now navigate the BIOS menus and search for something like "onboard devices", it should list your onboard soundcard/chip, then set the option to "Disable" or "Disabled".

Save the settings and exit (should be a menu option somewhere), your computer will reboot and the onboard soundcard should be disabled.

---

### Post by Bastaard on 2007-07-09
Alright I seem to have fixed my problem! The thing I did was just setting the default device through asoundconf, in the following way:

$ sudo asoundconf list

This will list your audio devices. Then:

$ sudo asoundconf set-default-card DEVICENAME

Ofcourse, you have to change DEVICENAME to the name of the card you want to be working with, using the name from the list you got with the first command.

You'd think this is what system->preferences->sound should be doing when you select the default mixer device, but apparently that does not seem to be the case. Hope this works for you as well!

---

### Post by martincho90 on 2007-09-20
> **Bastaard said:**
> Alright I seem to have fixed my problem! The thing I did was just setting the default device through asoundconf, in the following way:

$ sudo asoundconf list

This will list your audio devices. Then:

$ sudo asoundconf set-default-card DEVICENAME

Ofcourse, you have to change DEVICENAME to the name of the card you want to be working with, using the name from the list you got with the first command.

You'd think this is what system->preferences->sound should be doing when you select the default mixer device, but apparently that does not seem to be the case. Hope this works for you as well!:lolflag:Excellent! This is what I was looking for.

---


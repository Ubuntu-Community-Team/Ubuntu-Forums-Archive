---
title: "How to get USB headphones to work in Amarok using Xine and ALSA"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by Chaoticwhizz on 2007-05-09
I figured I would post this info since Googling it on my own found nothing. I was trying to get Amarok to output to my USB headphones. I initialy set my mono and stereo settings to /dev/dsp0 This did not work because aparently this only works in OSS. SInce I also use the 1.4 Alpha version of Skype which also uses ALSA I noticed that Skype listed the USB headphones as hw:Headset,0. I plugged this info into The mono and stereo settings for Amarok and it actually worked! The documentation for this issue is either misleading or nonexistent. Also could anyone clarify any info on this? Does /dev/dsp0 only work on OSS and not ALSA? Also is there a terminal command that list ALSA device mount points? Thanks in advance.

---

### Post by rodneygeorgez on 2007-05-18
Hey there,

I installed amarok about two weeks ago and loved it, but I had the same problem as you in that I could not get my USB headphones to work with amarok which was really annoying as it is a great media player/organizer. I tried everything from the amarok site and much more besides, but your trick worked a treat. Like you say there seems to be no documentation in the right places on this error and a couple of people who were having similar problems with their USB devices. I did have to put the exact same command in the configure alsa space as you which is a bit strange as my headset is number 1 when I run the "alconfig" in the terminal. Anyway, thanks heaps for the tip.

rodneygeorgez

---

### Post by issya on 2007-10-27
Just wanted to give my input on this in case anyone is searching for it. I am using Kubuntu Gusty and I had problems getting Amarok to recognize my Logitech USB headphones. I installed asoundconf-gtk (Default Sound Card under Adept) and set it to my headphones and made sure that Amarok was using alsa as the playback. Works like a charm but I wish it would have just did it all itself.

---

### Post by DavidMIRV on 2008-02-27
Am I missing something or can you guys please provide more details on getting USB headphones to work in linux. I am having same problem. Device shows up in alsa and can see in kmix I just cannot get any output from it

---

### Post by phonicboom on 2008-04-21
i had to go to skype (which was a pain to setup) and look for the setting there which worked, it was;

plughw:Headset,0

i then went to Amarok - settings > configure Amarok > Engine
And changed 'output plugin' to ALSA

Then I entered plughw:Headset,0 into the boxes for mono and for stereo

i left 4 channels and 6 channels blank

hit apply, ok.

hit play :)

---

### Post by sg3524 on 2008-04-28
> **phonicboom said:**
> i had to go to skype (which was a pain to setup) and look for the setting there which worked, it was;

plughw:Headset,0

i then went to Amarok - settings > configure Amarok > Engine
And changed 'output plugin' to ALSA

Then I entered plughw:Headset,0 into the boxes for mono and for stereo

i left 4 channels and 6 channels blank

hit apply, ok.

hit play :)

Awesome :)

Worked like a champ.  That was frustrating the crap out of me. 

I run an external stereo system with amarak as well, so when I want to use the headphones I switch amarok to alsa, for external stereo switch back to oss.  Awesome solution.

Thanks for taking the time post it!

---

### Post by Glaxed on 2008-05-19
Nice [Chaoticwhizz]("http://ubuntuforums.org/member.php?u=71577").

In your debt.

---


---
title: "Has any one come up with a fix for the apparent ALC269 bug?"
date: 2012-03-02
forum: Multimedia Software
---

### Post by ydeardorff on 2012-03-02
I have a lenovo ideapad that I use for college.
After installing Ubuntu 11.10 in it (which was the best install Ive ever had from a linux distro so far-kudos to the team!) I noticed no sound, at all. Everything is apparently installed, yet no sound devices of any kind. Only the Dummy stereo output shown in the audio properties.
After many days of tries I finally went to AskUbuntu and posted a topic.
Come to find out this is a major bug for anyone having this ALC269 chipset. And several cases on this chipset have been reported. Is the only solution going back one distro? I really do like 11.10.

Is there anyone that has this chipset and it works? perhaps some file code sharing? 
Has anyone found a solution or workaround for it?

I dont need home theater, but being able to make presentations, listen to online class professors while they talk would be nice. Its what I bought this for, college. 

Is there possibly an older distro that doesnt have the ALC problem?

I have tried just about everything command line related, but Id be willing to try anything else.

Im not a superuser, but I can follow directions, so post the codes for me to run and I'll post them.

aplay -l shows no sound card ata all

---

### Post by BicyclerBoy on 2012-03-02
The original atom powered ideapads with ALC269 worked okay (subjective)..
[http://en.gentoo-wiki.com/wiki/Lenovo_Ideapad_S10e](http://en.gentoo-wiki.com/wiki/Lenovo_Ideapad_S10e)

Does the h/w show up (Audio):
lspci -nn

Are you sure this computer uses that audio codec ?

---

### Post by Yellow Pasque on 2012-03-02
Make sure that the audio codec is enabled in the BIOS, because it's not showing up in lshw. Resetting the BIOS might be a good idea too.

Relevant Links:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/944298](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/944298)
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/189362](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/189362)

---


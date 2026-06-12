---
title: "Ubuntu studio and Echo Layla 20"
date: 2007-12-10
forum: Multimedia Production
---

### Post by gtrman79 on 2007-12-10
Hello all.  I just downloaded the Ubuntu Studio.  NICE PACKAGE!!  But, I have an Echo Layla 20 (yeah, the old one) and I'm wondering the first step in getting it to work with the multi-track software.  I see in the harware list that it is in there and it's labeled as Echo being the OEM and having a Motorola 56*** chip (can't remember).  But, no driver.  I am kinda new to the Ubuntu scene (I have tried Ubuntu and Kubuntu but don't use them much).  I guess the recording hobbie is the only thing keeping me looped into the Mcro$oft world.  It's plug and play. 

But I would like to get more into the open source world.  So if anybody can explain how I would get the proper drivers loaded, that would be great!!  Thanks for any comments.

---

### Post by pulsewidth on 2007-12-10
I guess the first question to ask is could you show us the output of the lsmod command? This will show if the driver is indeed loaded. If all is going well you should see snd-layla20 somewhere in the listing. 

The other showstopper could be (and is very likely) that the alsa firmware is not loaded. I have and Echo IndigoIO card for my laptop and it definitely needs to have firmware loaded. The unfortunate problem is that there is no alsa-firmware package in the regular repositories. There is a repo that is listed in the UbuntuStudioPreparation guide found here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Add this line to your Software Sources Third-Party Software tab:
[B]
deb [http://ppa.launchpad.net/tsmithe/ubuntu](http://ppa.launchpad.net/tsmithe/ubuntu) gutsy multiverse[/B]

After installing the alsa-firmware package, I believe that a reboot is in order.

Good Luck!

---

### Post by gtrman79 on 2007-12-12
OK I have Layla20 in the lsmod listing.  And I installed the apt-get for the alsa firmware that was on that page u sent me the link for.

But where is the 3rd software sources that I would paste the 

deb [http://ppa.launchpad.net/tsmithe/ubuntu](http://ppa.launchpad.net/tsmithe/ubuntu) gutsy multiverse

??

Thanks.

---

### Post by gtrman79 on 2007-12-12
OK, nevermind.  I found the software sources.  Now i Just need to find where to choose the recording device

---

### Post by veggiebenz on 2007-12-23
Hi, I have Ubuntu working with Layla 20. 

I've had it working for a couple years now.  I've done quite a bit of recording using JACK and Ardour.

It's served me well.

Let me know if you're having a specific problem and I'll do what I can to help.

---


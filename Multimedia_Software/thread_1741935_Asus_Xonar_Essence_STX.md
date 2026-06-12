---
title: "Asus Xonar Essence STX"
date: 2011-04-28
forum: Multimedia Software
---

### Post by Tomdarkness on 2011-04-28
Hey,

I'm running 11.04 and using a Asus Xonar Essence STX. This sound card features a build in headphone amp and when I switch over to headphones and the amp clicks in (including when booting ubuntu) I get a very loud click from my headphones (n.b the sound card clicks anyway when the amp kicks in, but this is actually coming from the headphones) and since the headphones are quite expensive I'm concerned that this might damage the headphones.

If I boot into Windows then then the amp on the sound card "clicks" but there is no sound produced through the headphones.

Anyone any ideas what is causing this and how I can prevent it?

Thanks :)

---

### Post by jamaas on 2011-05-13
Mine does the same, suspect it is just changing the current. I just make sure to turn it down before making any changes.

Do you know what drivers you are using?  I know very little about this but apparently the sampling rate of the card can be adjusted, but I don't see a control anywhere to adjust this.  I'm assuming that higher sampling rates are better???  Anyone care to enlighten me?

Thanks

Jim

---

### Post by srinivasmurty on 2011-07-31
Getting enlightened on this subject is perhaps the most wasteful exercise one can indulge in. I've searched high and low, both on the ASUS website (fat chance of getting anything helpful there!) as well as on various Linux and Ubuntu forums. All that you get is various wildly crazy suggestions such as downgrading "alsa" or mysterious people claiming that it worked clean as a whistle after installation of the 11.04 OS. My weird situation is that the card is recognized among a myriad of others that are on my machine (unfortunately). I have turned off the on-board card but I have two others, one from my ATI display controller and the other is a USB audio controller that is connected to my PC. Perhaps I should disable these other two as well but I am not convinced I will get anything to work even then.

Perhaps my frustration is very evident here but I would humbly submit that if the card shows up in the recognized list and, if as per the Alsa website, this chipset is supported, then I am mystified as to why my card doesn't work.

---

### Post by ikt on 2011-08-28
> **srinivasmurty said:**
> Perhaps my frustration is very evident here but I would humbly submit that if the card shows up in the recognized list and, if as per the Alsa website, this chipset is supported, then I am mystified as to why my card doesn't work.

Just to confirm that you do have the card plugged in using the 4 pin molex connector on the back.

For anyone else who made the mistake of not having it plugged into the card, it has now come alive and is awesome.

---

### Post by ikt on 2011-09-30
I just installed Ubuntu 11.10 and found I was having the same issue, where the sound card was clicking on boot up but not working in the audio panel.

I knew this was a software issue because the sound card was working on my Ubuntu 11.04 install but not 11.10.

I ended up installing alsamixer and from there I found manually changing the output to headphones it worked.

---

### Post by oooverclocker on 2011-10-14
Thank you for the solution ikt.
[https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/873558](https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/873558)

---

### Post by Rubbiroid on 2011-10-29
ups.. wrong language..

Is anybody was able to solve this problem?
I can switch the output ports with latest pulseaudio server from git (with pacmd command), but all pulse clients can't establish a connection to the server.

---

### Post by Pahanilmanlintu on 2011-11-04
Hey, anything new regarding this? I'm also affected with Xonar Essence STX on Ubuntu 11.10 64bit.

I try to avoid compiling stuff as much as possible, so does anyone know if there will be a pulseaudio update pushed before Precise?

Also, @ Rubbiroid: How well does it work after the steps you listed on 2nd november on Launchpad ("So, I had found solution --")? Meaning, does "-- but all pulse clients can't establish a connection to the server." still apply, and does the menubar applet for changing output source work?

---

### Post by jamaas on 2011-11-06
Mine changed with upgrade to 11.10 as well.  Now can only change speakers -> headphones or back with the linux alsa mixer, Pulse audio volume control will not work.  The jacks for the headphones and mic (for skype) on the front of the box no longer work as well.

Hope we can get it sorted, great card, great sound, just need to control it!

Thanks

Jim


> **Rubbiroid said:**
> ups.. wrong language..

Is anybody was able to solve this problem?
I can switch the output ports with latest pulseaudio server from git (with pacmd command), but all pulse clients can't establish a connection to the server.

---

### Post by cuby on 2012-02-06
Same problem here.
The alsamixer trick worked for me.
I've subscribed the bug report.
Let's see if this is corrected in the next LTS.

---

### Post by oooverclocker on 2012-04-26
It works perfectly in 12.04 LTS for me!

---


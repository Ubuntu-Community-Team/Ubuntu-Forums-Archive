---
title: "Headphones don't seem to be recognized"
date: 2011-04-22
forum: Multimedia Software
---

### Post by erget on 2011-04-22
Hi there,

I'm working with a recent fresh install of Kubuntu on a Lenovo G560. When I plug in headphones to the laptop, nothing happens - the laptop's internal speakers continue to produce sound like nothing's happened. This is strange because:
- As a long-time SUSE user (also KDE) on the same machine, I was always able to solve the problem by installing pulseaudio. pulseaudio is installed here, but it doesn't help.
- I could have sworn that headphones worked on Ubuntu on the same computer too.

I've tried the following (sounds really similar to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226), pretty old bug report):
- Booting with headphones plugged in
2. Adding "options snd-hda-intel model=lenovo" to /etc/modprobe.d/alsa-base.conf and rebooting
3. Deleting that line and adding "options snd-hda-intel model=laptop" and rebooting
4. Deleting that and adding "options snd-hda-intel" and rebooting

"aplay -l" shows my audio card, so that doesn't seem to be the problem either.

Does anyone have an idea what else I can try? Thanks a lot!

---

### Post by dabl on 2011-04-22
Try installing alsa-base, alsa-utils, and alsamixergui.

Alt-F2 "alsamixergui"

Look for the little "locks" for the headphones, and click it, then raise the volume.

Now go back to pavucontrol and look at the input device and output device.  You should be able to pick the headphone off the drop-down list.

Play around with these, and also the Kmix mixer settings.  Usually there's a combination that works.

---

### Post by erget on 2011-04-23
Alright, installed all the alsa stuff. No dice, although the alsagui only recognizes pulseaudio as my audio chip, perhaps that's the reason. I don't have any controls for headphones, although headphones are plugged in, and all the locks are unlocked.

pavucontrol doesn't recognize the headphones either in the audio controls. I tried playing around with the audio profiles and tried every one of them, but the only thing that did was turn off my audio entirely. I turned it on by switching the profile back.

kmixer is the same story - there is no audio output that would go to the headphones. I have all the channels turned on and nothing muted. Still nothing though. I think that Lenovo laptops might generally be problematic, because I used to have problems with my old Lenovo too. But SUSE was always able to get it.

I'm rather confused because, as I said, SUSE could always get the audio to function correctly using pulseaudio, so it can't be a KDE thing, but it doesn't seem to be an Ubuntu thing either because Ubuntu with the normal GNOME environment worked fine too, if I remember correctly.

---

### Post by dabl on 2011-04-23
Are those headphones conventional audio headphones with the 1/8 inch plug, or are they USB headphones?

---

### Post by erget on 2011-04-23
They're normal, conventional headphones, not USB. I've also tried other ones and even attaching analog external speakers with a male-to-male audio cable. In each case the internal laptop speakers stay on and no signal is sent to the external audio device. The problem's been there since I installed the computer about six weeks ago, I just haven't had time to really take care of it until now.

---

### Post by dabl on 2011-04-23
In alsamixergui, I have found that my desktop system needs me to click the "front mic" and "front mic boost", but my netbook needs me to click "internal mic" and "internal mic boost", both need to be adjusted up part way.  Then in pavucontrol the internal mic volume seems default to about 20%, and needs to be moved up to 80%.  Finally, the Kmix volume for the "capture device" seems to be muted by default, and has to be unmuted.

---

### Post by Yellow Pasque on 2011-04-23
There is some useful info here: [http://www.linlap.com/wiki/lenovo+g560](http://www.linlap.com/wiki/lenovo+g560)

---

### Post by dabl on 2011-04-23
> **erget said:**
> 

 SUSE could always get the audio to function correctly using pulseaudio



IIRC, Kubuntu does not install all of the pulseaudio packages by default.  You might want to try this in a terminal:

```
sudo apt-get update && sudo apt-get install paman padevchooser pavucontrol pavumeter
```

Then open Alt-F2 "pavucontrol" with no quote marks and see what you can learn about the "input device".

---

### Post by erget on 2011-04-24
Alright, tried that. Unfortunately it also didn't have an effect. With the additional packages pavucontrol didn't recognize anything it hadn't before - whether or not I plug in an audio cable, only the internal audio analog stereo device shows up. Changing the profile doesn't change that either :(

---

### Post by dabl on 2011-04-24
With the headphones plugged in, when you go to System Settings > Multimedia > Music, do the headphones appear on the list of devices in the right-hand window pane?

TBH, this is looking like a Lenovo "options" with the driver thing to me -- it looks like you have tried the logical ones.  Maybe look more at other Lenovo options, if there are some you haven't tried.

---

### Post by erget on 2011-04-25
Hmm... No, I don't have the headphones. These are the ones I have:

Internal Audio Analog Stereo
Internal Audio Digital Stereo (IEC958)
Internal Audio Digital Stereo (HDMI)
Dummy Output

Only Internal Audio Analog Stereo is selectable, the rest is all grayed out.

What do you mean with Lenovo "options"? I'm not familiar with the term. The headphones worked with the same hardware, different distro before, so it doesn't seem like it'd be a fundamental problem with the laptop itself, as difficult as it is to get the hardware running right with this one ;)

Thanks by the way for the help, I really appreciate it :)

---

### Post by dabl on 2011-04-25
Unless you know you need the digital IEC958 and/or the HDMI, you should set that to "Off" on your pavucontrol "Configuration" tab.  Then just leave the "Internal Analogue Audio" enabled.

Intel options database: [http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database](http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database)

Ubuntu's guidance: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by erget on 2011-04-26
Oh... Yeah, I'd found and used those before, the options don't help. And in the configuration tab of pavucontrol I've had digital and HDMI turned off the whole time - the setting's on Analog Stereo Duplex.

---

### Post by dabl on 2011-04-27
OK, my last shot at this strange little problem:

Try (if you haven't already) System Settings > Multimedia > Phonon > Audio Capture and move the Pulseaudio Sound Server to the top of the list, and click "Apply".  Now go back to pavucontrol > Input Device and see if the volume sliders, in combination with alsamixergui "front mic" or "mic" channels, can get the mic to respond.

---

### Post by Yellow Pasque on 2011-04-27
Based on the comments from link I posted above, updating to latest alsa might help: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by erget on 2011-04-28
Hey there,

I think there might be some confusion as to the nature of the problem itself. My mic works fine, the problem is that I can't get headphones to work. On the same note, external microphones don't work either - no external audio devices are recognized. Up till this point I've always been trying to use the standard audio output port on my laptop, no USB, with standard 3.5" audio plugs. Although audio capture with an external mic would be kinda cool, the bigger problem is more that I can't get external headphones or speakers to work with the laptop.

As a side note, in the multimedia settings I don't see a pulseaudio server, even though I've got pulseaudio installed and the daemon is already running.

Temüjin, thanks for the link, but I think that doesn't apply for me too well - I'm using the latest version of Kubuntu (10.10, since 11.04 isn't released yet).

---


---
title: "PulseAudio Problems - Ninja needed."
date: 2010-07-16
forum: Multimedia Software
---

### Post by mlhudson on 2010-07-16
So, I can't find a helpful answer in previous threads to this...

I'm in Ubuntu 10.04 and on an Acer Aspire 7736Z. I've had plenty of sound issues already, but most are whittled down to a manageable few. The one that's giving me the biggest headache is that PulseAudio will not let more than one app deliver sound at a time. Surely someone knows of a quick ninja move on a config file to fix this...

Any suggestions?

---

### Post by HotshotGG on 2010-07-16
> Any suggestions? I don't have the exact answer to your question, but I do have a few suggestions. It appears as though your laptops chipset may or may not support hardware mixing? If so you are going to need to modify the **asound.conf **file to do software mixing as a work around if it in fact does not support hardware mixing. This page in the ALSA wiki gives some hints as to how to go about doing that. 

This is for using dmix instead of PulseAudio: 
[http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing](http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing)

The first thing you should always do is check what audio hardware you have on your machine open a terminal and type **$cat /proc/asound/cards**.  This will give you some idea of what audio chipset or card ALSA is using by default.  You may want to consider also modifying the **asound.conf **so that looks like this... 

first type **$sudo gedit "/etc/asound.conf"**

When the window opens up copy and paste the code below into the editor and click "save". This may or may not work, but it's worth a shot. If it does not work open up the file again and remove the snippet below all together!. What it does is it maps all the audio from different apps in Linux through the PulseAudio SoundServer. The only drawback is on some media applications you need to switch the audio ouput to PulseAudio like with VLC for instance. Rhythmbox should be fine if I am not mistaken. 

[B]pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}[/B]


That's not guaranteed to work it's just a suggestion. I for instance use an external hi-end M-Audio Revolution 5.1 soundcard with ICE1724 chipset. It does external hardware mixing so playing audio through multiple apps and streams in ALSA is much easier to do. I hope this helps somewhat or at least puts you on the right track! :o

---

### Post by lidex on 2010-07-18
With pulseaudio it's either "Duh, why didn't I think of that?" or "That doesn't make any sense at all!"
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")

---


---
title: "[SOLVED] Turning off onboard sound on a laptop"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by duvalt on 2008-03-17
Hello,

I have recently switched from Mandriva to ubuntu as ubuntu is far superior for performance and the ability to have all of my onboard hardware function properly.

There is one thing that I am stuck with, I have a logitech usb headset. What I'd like to do is either forcefully default all applications to use the headset. In mandriva I simply edited the /etc/modprobe.d and added the lines: 
options snd_usb_audio index=0 
options snd_hda_intel index=1

this defaulted the apps to go through my headphones and not the speakers.

In ubuntu there is a gui app to select this, but for things like xwin, wine, and firefox the sound still comes out the speakers. I am using this as a business laptop in my office as an IT tech, so i can't have loud noises as im sure the user over the phone dosen't wan't to hear whats on the speakers. 

the one thing I tried was going to the /etc/modprobe.d/alsa-base file and changing the index value besides the usb audio to 0 (hopefully to force the audio through the headset) but when I rebooted it would just tell me they werent connected...when they really were.

I am not looking for an easy way to turn on the onboard speakers as they are used maybe once a month at the most, so whatever the easiest way to force the usb audio this would be best.

Any help would be greatly appeciated. 

Thanks.:popcorn:

---

### Post by kpkeerthi on 2008-03-18
You may want to check this out [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by duvalt on 2008-03-18
Well it seems what i had done in ubuntu (changed index to 0 not 2) seems to of worked. It just seems that sometimes the headset will not load on boot. Not really sure why but eventually it works again. I've heard talk about the next release of ubuntu, or any distro that carries Pulse audio should fix most of the usb to external speaker issues. 

Re-compiling of the alsa configs and all that is simply too much,There really should be no reason for that type of thing at this stage. I'd rather just buy a standard headset. :lolflag:

I found this site for anyone needing it, its what helped me: 

[http://ubuntuforums.org/archive/index.php/t-402293.html](http://ubuntuforums.org/archive/index.php/t-402293.html)

and

[http://alsa.opensrc.org/index.php/MultipleCards](http://alsa.opensrc.org/index.php/MultipleCards)

---


---
title: "Fresh install of 16.04LTS, no audio"
date: 2016-04-23
forum: Multimedia Software
---

### Post by lesyalouky on 2016-04-23
EDIT 7/May/2016

EDIT: I finally got the sound working, though it's probably a temporary solution, I'll have to set it everytime I reboot my PC. Pavucontrol still says the audio jack is unplugged so that's never good.
How I did it:

Install pavucontrol, start it. Go to the last menu(settings), and turn OFF HDMI Audio.
Then below that choose whatever output works for you. I use Analog stereo output.
Now it should output sound through analog audio jack by default.
You can always change individual application to this output if it doesn't work.

Sorry if anybody here suggested this, I didn't get it until now.





I'll leave the original post here for anyone to help.



> 

I've installed fresh Ubuntu 16.04 and I got no audio whatsoever. At  first was using audio out through HDMI, now using classic audio jack.
Note that I do hear audio through the command line, but I'm unable to set the audio out through internal sound card.

What I've tried:
- reinstalling pulseaudio, after that didn't even see the volume icon at the top right.
- using daily ALSA builds
- Padoka PPA - newest drivers
- clean reinstallation with audio connected through 3.5 mm audio jack (front and back)
-trying to mess around with the default playback device
- pavucontrol, alsamixer, ...


My setup:
Dual monitors (HDMI/DVI)
AMD R9 380 (2GB)
AMD FX-8300.

Is there anything I can try to get sound?
WIth the radeonsi driver I had issues with the monitors, only one working.(on ubuntu 15.04)
Now monitors work, but no audio.


---

### Post by jimmy-frydkaer on 2016-04-23
You might need to install **alsamixergui **and then turn up the volume from there

```
sudo apt-get install alsamixergui
```

---

### Post by lesyalouky on 2016-04-23
OK I installed alsamixergui, everything is at maximum volume. You can view the image in attachements.
Still no audio.

EDIT: OK, so since nobody's been able to help me and because I need a working desktop computer tomorrow. I am returning to Ubuntu 14.04. Please keep this topic online, so anyone can see it, if experiencing the same issue.
Hopefully the drivers' developers can get it fixed soon.
I think it's the amdgpu graphics card driver's fault.

Anyways, if anyone thinks they found a solution, feel free to post it here, but I will try it in a LIVE boot mode first, before reinstalling my system.

---

### Post by ajgreeny on 2016-04-23
Check that you still have the pavucontrol package installed, which is the pulseaudio-volume-control.
Once installed you get to it from clicking the volume icon in the panel -> Sound Settings in all (I think) of the different DEs available.

---

### Post by lesyalouky on 2016-04-23
the issue is not in pavucontrol, pulseaudio or anything else. I am almost sure in that. It must be the amdgpu driver's bug.
On Ubuntu 14.04 with fglrx in sound settings, I have 2 outputs - HDA ATI HDMI and analogue output.
On 16.04 there is only HDA ATI HDMI, which is not outputting any sound. The other one, analogue output, is shown only in alsamixer, but doesn't work either.
The actual sound on 14.04 works with HDA ATI HDMI selected.

---

### Post by raynys on 2016-04-24
I have the same problem. No sound with a fresh install of Ubuntu 16.04. Installed pavucontrol, switched to duplex analog stereo and then it works but...when i reboot my pc, i can't hear nothing again. Pavucontrol don't remember the settings. 
This is a screenshot of my sound panel:

[IMG]http://s19.postimg.org/l11no93fn/screen.png[/IMG]

---

### Post by lesyalouky on 2016-04-24
raynys: I tried to switch to what you call duplex analog stereo, or in other works S/PDIF, but it was all at 0 volume and didn't work at all.
Maybe you have sound connected through S/PDIF(optical cable), but I have it through HDMI audio.

---

### Post by raynys on 2016-04-25
I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.

---

### Post by SuperFreak on 2016-04-29
> **raynys said:**
> I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.

Thanks for this it helped me. Will the front headphone jack not work after this though?

---

### Post by Bucky Ball on 2016-04-29
*Thread moved to **Multimedia Software**.*

---

### Post by lesyalouky on 2016-05-03
Unfortunately your advice didn't work for me. It's pretty weird. The audio works before I login, the welcome sound does ring.
But after loging in, in sound settings, there is only HDMI, S/PDIF isn't there. And in alsamixer the motherboard audiojack says (unplugged).
It works(when changing the volume in alsamixer, there is the ringing sound actually), but Ubuntu just can't use it as default.

PS: Yes, I no longer use HDMI audio output, that I abandoned completely. But audio doesn't work even through audio jack. Not even the front one.

---

### Post by yarosh on 2016-05-19
> **raynys said:**
> I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.

This also helped for my problem. Description of the issue below:

First I installed 16.04 and could see SPDI/F output. Switched to it, and tested for sound through optical cable to external amplifier - it was working fine. Then I installed some updates (it was a fresh install), enabled proprietary drivers (also for NVidia) and installed some basic software (mainly console programs).
Then, after a reboot I lost sound on optical output and I could only see (except the analog output) the HDMI digital output. Only because I also have a TV connected through HDMI, I could hear the sound through TV speakers when switched to it.

After applying the above solution and a reboot, the SPDIF option showed up and it's working now :)

Thank you very much!

---

### Post by salemboot2 on 2017-01-01
pavucontrol should be integrated into Unity.

I have the Azelea Intel HD Audio chipset
What works for me is:
From the command line, run the command "pactl load-module module-detect&"
That will cause you analog to show up in the built-in Pulseaudio control of Unity.

Ultimately, I just run pavucontrol and set it manually.

What didn't work, was running "alsactl restore" from the "etc/rc.local"



#references
[https://www.marcus-povey.co.uk/2016/10/27/ubuntu-16-04-sound-fixes-for-intel-hda-azalia/](https://www.marcus-povey.co.uk/2016/10/27/ubuntu-16-04-sound-fixes-for-intel-hda-azalia/)

[http://askubuntu.com/questions/636081/analog-sound-output-does-not-appear-in-sound-settings](http://askubuntu.com/questions/636081/analog-sound-output-does-not-appear-in-sound-settings)

---


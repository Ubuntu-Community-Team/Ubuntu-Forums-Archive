---
title: "Loud pop on speakers when disconnecting headphones (using soundcard)"
date: 2022-10-03
forum: MINT
---

### Post by alexubn on 2022-10-03
Hi,

I installed a sound card in order to deal with an issue I was having with my motherboard's built-in sound. (Creative Soundblaster Audigy Fx.)

I'm having the same issue that some users experience when unplugging headphones from the front panel of the computer while speakers are connected to the back AND a bit of time has passed since the audio sub-system was used: a loud pop on the speakers. (Front panel jacks are connectd to the card's hdaudio connector.)

Before installing the sound card, I resolved this with the following changes:
[LIST]
[*]Edit /sys/module/snd_hda_intel/parameters/power_save and change the value from 1 to 0. 
[*]Edit /sys/module/snd_hda_intel/parameters/power_save_controller and change the value from Y to N. 
[*]Added the following line to /etc/modprobe.d/alsa-base.conf:
[LIST]
[*]/etc/modprobe.d/alsa-base.conf 
[/LIST]
   
[/LIST]

Now that I added the new sound card (Creative Labs' Audigy Fx), apparently the above changes no longer work.

I'm pretty sure that the source of the problem is a module that goes into sleep, but I can't see anything other than snd_hda_intel.

I uploaded my entire audio configuration to [https://termbin.com/55jj](https://termbin.com/55jj)

Thanks

---

### Post by TheFu on 2022-10-03
Mute the output before changing the plug.
For speakers, it might be easier to just power them off.

---

### Post by alexubn on 2022-10-03
I wish I could remember to unplug and/or mute stuff, but that's never the case, and I'm afraid of damaging the speakers, which happen to be quite expensive.

I appreciate your suggestions, but unfortunately this won't work. There has to be a fix for this.

Thanks!

---

### Post by him610 on 2022-10-03
What happens if you just leave the headphones connected?

Back in the day when we had (sort of) expensive stereo systems, we were advised to turn down the volume before (dis)connecting headphones or speakers. Same probably applies to your expensive speakers today. If you insist on (un)plugging headphones or speakers while volume is turned up, be prepared to replace your speakers before their predicted end-of-life.

---

### Post by alexubn on 2022-10-03
Yes. I remember those days. And I have tried to do this, however, mint remembers the individual volume settings of the speakers and the headphones.

I don't unplug the speakers ever. Never had to and they're not located in a way that powering them off or unplugging them is practical.

This means that if my headphones are connected, I have to go through the hassle of opening sound settings and play with the levels there, and then unplug the headphones.

I get a loud pop even with the volume of the speakers at 35%, not loud, level.

I do a lot of plugging and unplugging of the headphones because I use the computer to make calls as well as listen to music while working. Having to remember a whole ritual in order to do something that normally doesn't require ANY thinking edges on the absurd.

I guess I'm going to have to spend umpteen hours studying all I never wanted to learn about pulse and alsa in order to solve a problem I shouldn't be having in the first place (and never had).

---

### Post by deadflowr on 2022-10-04
*Thread moved to **MINT***

---

### Post by TheFu on 2022-10-04
Or just use the same tool that Mint uses to manage audio devices, if that's your preference.
Pulse has lots of plugins. The defaults are probably different between different distros.  I have 3 microphones and 2 or 3 headphones/speakers connected concurrently. Using 'pavucontrol', I can choose which application audio out goes to which output devices and which inputs are sent to which applications.  Of course, we can control these things using pactl or pacmd too, if we prefer, so it can be automated.  Your skill with automation would determine how easy that is to accomplish.  

When I'm going to join a video conference, I change the default sink and source, then start a browser in a strictly confined sandbox that doesn't allow direct access to any system storage and opens the specific location in the browser for that specific video conference.  Instead of having to remember all those settings, the script does that for me.  I think I set the gain on the microphone, speaker output, and zoom level on the video camera in that script too.  Lots of things can be automated.  I find it 1000x easier to automate from CLI programs than through GUI programs.  Wayland is making automation for GUIs even harder and blocking it in many situations.  Same for snap packages.  Many automations simply do not work with snap packages, because of the per-process constraints, though they work well with the non-snap package versions of the exact same programs.

---


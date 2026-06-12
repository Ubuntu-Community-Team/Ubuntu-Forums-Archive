---
title: "Sound stopped working"
date: 2009-11-20
forum: Multimedia Software
---

### Post by daemon512 on 2009-11-20
Alienware m17
new install of Kubuntu 9.10

I had to do some things with the alsa driver to get it to work in the first place, but it has been working.  A friend was streaming video online, the sound was working fine, then my internet crashed (it does about 1 time an hour), freezing the video, so I refreshed.  From that point on, I have had no sound and do not know why (I didn't update anything or mess with any settings).  

bash> aplay -l
lists the following:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1                                                 
  Subdevice #0: subdevice #0                                      
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0                                        
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]          
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0  


Any ideas/what other information do you need?  Thank you!

---

### Post by daemon512 on 2009-11-20
All sound levels are unmuted and turned up.  Just found out that "Beep" does in face make noise, but I can't make anything else work.

---

### Post by RedSingularity on 2009-11-20
I assume you have already restarted the computer.  Do you have pulseaaudio installed?

---

### Post by daemon512 on 2009-11-20
I have tried restarting.  I do not have pulseaudio, its using kmix by default (which was working before).  Should I get rid of kmix and use pulseaudio?

---

### Post by RedSingularity on 2009-11-20
Well you could try that.  If it doesn't help you can always go back to kmix.

---

### Post by daemon512 on 2009-11-20
That worked, for whatever reason. However...

After the restart I needed, a window came up asking:

 p, li { white-space: pre-wrap; }  KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Output: HDA ATI HDMI, ATI HDMI (HDMI Audio Output)
[/LIST]
Yes/No/Manage devices

I believe this is a result of removing kmix, but I'd rather not mess something up so Im asking before I answer, should I not remove them?

---

### Post by HuaiDan on 2009-11-20
Check which kernel version is running. At terminal type


uname -r

Should return

2.6.31-14-generic


This should also be the version loaded by /boot/grub/menu.lst if you're using original grub. Check your startup menu if you're using grub2.

If it's not the right kernel, then you'll need to run

sudo update-grub

and find which kernel you're running, and edit your menu.lst to reflect this, or if you're using grub2,

sudo apt-get remove --purge grub-pc

then 


sudo apt-get install grub-pc

and BE SURE TO SELECT A DRIVE TO INSTALL GRUB2 ON when asked.
Be absolutely sure not to miss this last part, it's very easy to just click through without noticing that you didn't select a drive to install grub on.





Most of these karmic sound issues with hda intel sound have to do with the wrong kernel running. Further remedy won't be possible until you have the right kernel running.

---

### Post by daemon512 on 2009-11-20
HuaiDan, thanks, I have tried that already, I am on the correct Kernel.  I attempted to go through a few different posts on issues before posting one myself, but I appreciate the attempt :).

---

### Post by RedSingularity on 2009-11-21
> **daemon512 said:**
> That worked, for whatever reason. However...

After the restart I needed, a window came up asking:

 p, li { white-space: pre-wrap; }  KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Output: HDA ATI HDMI, ATI HDMI (HDMI Audio Output)
[/LIST]
Yes/No/Manage devices

I believe this is a result of removing kmix, but I'd rather not mess something up so Im asking before I answer, should I not remove them?

Answer "no" to that question just to be safe.

---


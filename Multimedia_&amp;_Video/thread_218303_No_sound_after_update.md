---
title: "No sound after update"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by avatar3 on 2006-07-18
Hi.

I updated my ubuntu. And after the required restart no sound works. Before updating all sounds were working perfect, but now i can hear anything, not even the system sounds

What should i do? Please someone help me ](*,) 

-Av

---

### Post by alohre on 2006-07-18
Second that. Seems like some sort of ALSA problem.

---

### Post by lj269 on 2006-07-18
I had this same problem after upgrading to Dapper, I followed the instructions in this post [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) . When I had purged and reinstalled everything I noticed in alsamixer that only the front channel was not muted, changing all the other chanels fixed the sound problem. Don't know if this would have worked before rinstalling everything so might be worth trying that first...

---

### Post by buckethead27 on 2006-07-18
I updated this morning and have the same problem.

---

### Post by avatar3 on 2006-07-19
lj269:

Ive done everything said in that thread. It detects my soundcard, etc. But it just doesnt play any sounds.. 

Could this program have been caused by my USB speakers? :o 

-Av

---

### Post by LordRaiden on 2006-07-19
Look if you have a .asoundrc file in your home directory. Since you have USB speakers, try removing them, rebooting, then plugging them back in. Also, try playing an MP3 and see if you get visualizations/track timer to move. If they are moving then you have *sound* but something is muted/disabled.

---

### Post by avatar3 on 2006-07-19
LordiRaiden:

No i dont have a *.asoundr*c file in my Home directory. All the .mp3 files "go on" but i dont get any sound.. 

Ive tried that re-plugging them, and i get sometimes "someusbthingy plugged in, go "System - > preferences - > sound to make it your default.

Ive done that many times, but it just doesnt "stay" as default.. [-( 

Any idea how to get it to stay as default or something? 

-Av

---

### Post by LordRaiden on 2006-07-19
Does it work when plugged made default? if it does, that is a good thing. I would not know how to make them the default since I do not use GNOME.

---

### Post by avatar3 on 2006-07-19
I cant make it default.. I go to the sounds panel and goto the "Select default" thingy, and choose "UAC3553B" to it. 


Then it needs to be "closed" to those options to take part, nothing happens. And when i go back to the Sound thingy, "VIA 8237" is again set as default. 


-Av

---

### Post by LordRaiden on 2006-07-19
VIA 8237 is your soundcard, so it is no surprise that it gets set back. Your USB speakers should have a soundcard built-in. So what you need to do is load up the snd-usb-audio module

So let's try these steps

1) Plug your USB speakers in. Press OK to any dialog box.

2) Type this into a console

```
snd-usb-audio
``` 
3) Now type this into a shell
```
aplay -l
``` 
Paste the output here.

I think you will eventually have to disable your chipset soundcard in your BIOS to get your USB speakers.

---

### Post by avatar3 on 2006-07-19
LordRaiden:

I tried that "snd-usb-audio" Command, but it just gives: "Command not found."

And the output for "aplay -l" is : 


**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UAC3553B [UAC3553B], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any ideas? Im gonna try that chipset thingy in a soon 

-Av

EDIT:

Just rebooted and went to BIOS, didnt find anything that would allow me to "shutdown" the chipset sounds.. 

-Av

---

### Post by LordRaiden on 2006-07-19
sorry the command was 
```
sudo modprobe snd-usb-audio
``` (getting a bit sleepy)

however, the second test verifies what I needed yo know. The usb audio driver is being loaded.

Your should be able to disable the audio (try looking for onboard devices or controllers and navigate around). It will be much easier since you won't have to any of the things I tell you to now.

If you can't do that, then I just want a few things.

1) Paste the output of ```
 dmesg | grep snd
``` If there is no output, there are no errors so then don't paste. If there are errors, paste them and stop at this step.

2)  Do ```
alsamixer -c 1
``` Hit F1 for a list of commands (only left/right, up/down, and the M key really matter)

make sure that all the master and PCM channels are not muted. PCM should be set to 80 while master should be 100.

3) I cannot help you with system sounds since that is a GNOME issue and outside my expertise. What I can help you is with things like Mp3 players and video players. All of these players have some sort of configuration. On mine, it is Settings -> Configuration ...

4) Now look for the a tab or menu that has Engines. Find a menu that lets you select output type and then select 'alsa' from the list. Now look  for a menu like 'ALSA device configuration'. For both mono and stereo (if you have them) type in "hw:1,0".

5) Select 'OK' then try to play something. It *should* work.

---


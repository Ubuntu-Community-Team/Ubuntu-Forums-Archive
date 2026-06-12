---
title: "Bluetooth headset setup with pulseaudio"
date: 2010-02-23
forum: Multimedia Software
---

### Post by hcm0 on 2010-02-23
I'm having trouble getting sound in a bluetooth headset.  I'm running ubuntu 9.10 (karmic koala).  

I'm using a USB bluetooth adapter, and everything with the pairing seems to work fine.  When I plug the adapter in, the bluetooth icon appears, I could set up a new device, my headset was recognized, and I can connect/disconnect from it.  "hcitool dev" and "hcitool con" return the addresses of my adapter and headset.  

However, in pulseaudio volume control/ manager, the headset is not seen as a device.  I don't know if this is supposed to happen automatically in the latest version of pulseaudio, so I also tried following the instructions in this guide: 

[https://help.ubuntu.com/community/BluetoothHeadset]("https://help.ubuntu.com/community/BluetoothHeadset")

I set up a .asoundrc file in my home directory, and followed the other steps until the command

```
pactl load-module module-alsa-sink device=btheadset
```

This returns "Failure: Module initalization failed" 

Ignoring that for now, and going on to the test step, using aplay, 

```
aplay -f s16_le /usr/share/sounds/alsa/Front_Center.wav
```

plays the file fine over the computer speakers, then returns to the prompt, but

```
aplay -D btheadset -f s16_le /usr/share/sounds/alsa/Front_Center.wav
```

says that the file is being played, but hangs until the command is aborted.  

If anyone has any suggestions about how to get the "pactl" command to work, or what else I might be missing, they would be greatly appreciated!

---

### Post by juliobahar on 2010-03-17
Try using ubuntu's preinstalled Gnome Bluetooth Manager (the icon that shows in the system tray) to connect your headset. You might need to remove the headset and connect it again as if you are doing it from the very beginning. I had the same problem resolved by removing the device and discovering it once more.

After that 
```
pactl load-module module-alsa-sink device=btheadset
```

inform me of any success.

I still have a problem try to figure out how to setup the source module to use my headset microphone. But unfortunately sill no luck.

---

### Post by juliobahar on 2010-03-17
Few minutes after I submitted the above post, I solved my problem.

I replaced Gnome-Bluetooth Manager with Bluez. It detected my bluetooth mic on my headset and I was able to record voice. Great!!!

Love Ubuntu and starting to love PulseAudio.

---

### Post by hcm0 on 2010-03-19
Glad you fixed your problem, Julio!  I meant to update this thread, because my problem was apparently the cheap hardware -- I bought a new bluetooth dongle and Pulseaudio now automatically recognizes the headset and can send audio to it.

The only problem now is that when I make calls with Skype, the bluetooth headset works for a few seconds, then turns itself off.  I'm planning on trying a different headset, in case it's also a hardware problem. Pulseaudio does seem like it's a better way to control sound, but I really wish I understood audio in linux better!  Someday...

---

### Post by juliobahar on 2010-03-19
I'm even more glad that you've solved your bluetooth headset connection issue, hcm0. 

Btw I have also experienced problems with btheadset setting. As I was able to sink stereo (A2DP) audio to my headset but when I switch to the headset telephony service the microphone produces an utterly annoying buzzing sound that never goes off unless turned off. Same thing used to occur with MS Windows. At that time I never suspected the bt dongle could have been faulty, yes it was a very cheap one, since everything else was working (like connecting to mobile phones, sending files, remote control ... etc) That problem was solved after I got it working on my brother's laptop. Voila! it was because of the terrible adapter (dongle). Strange, isn't it?!

Well, back to your issue. IMO Bluetooth connection should not drop after few seconds unless the headset turns itself off, the bluetooth dongle could be faulty (like warms up), or probably skype isn't providing the correct signal code to sustain the telephony service of your headset (yet I'm totally unfamiliar with skype). 

The best ways to track down the problem, in my opinion:

1- try the headset with your mobile phone (which should have bluetooth facility) can you make a long call (not a long-distance call of course) failure means a problem with the headset itself
2- but if that went fine the try the dongle with the headset in ubuntu sound recorder (Applications->Sound and Video -> sound recorder). See whether you can record long periods of your own lovely voice.
3- if that fails then try the dongle and headset on another computer running an OS system which you are familiar with.
4- if that also fails try another dongle.
5- failure of the above necessitates asking an expert... I'm not a genius 

Hope that was fruitful, and yes, I'd like to listen from you again.

Btw, I also hope I can understand pulseaudio better. still very new in the ubuntu world.

---

### Post by taecha on 2010-03-20
I've got the same problem with a Logitech BT headset. The headset turns itself off after some time (sometimes a few seconds, sometimes a couple of minutes). The same headset works fine under Windoze and with my mobile. So it's not a hardware issue. Must have something to do with pulsesound ...

---

### Post by juliobahar on 2010-03-21
> **taecha said:**
> I've got the same problem with a Logitech BT headset. The headset turns itself off after some time (sometimes a few seconds, sometimes a couple of minutes). The same headset works fine under Windoze and with my mobile. So it's not a hardware issue. Must have something to do with pulsesound ...

Wait a minute, me clear that point, do you mean the bluetooth connection turns off after an undetermined period of time, or sound don't seem to sink into your bluetooth headset? 2 different things.

I'm asking since I've noticed that after a period of latency, at some instances, you might experience sound delays. Like if watching a movie audio will lag behind video. What I do to solve this I turn the video off and press the headset connect button a couple of times until I get the sound synchronized back again. Yes, that is weird. I really don't know why.

---

### Post by taecha on 2010-03-21
> **juliobahar said:**
> [...] do you mean the bluetooth connection turns off after an undetermined period of time, or sound don't seem to sink into your bluetooth headset? 

Actually, the headset gets powered off. Don't ask me how, I don't have a clue. I can only tell you that's what's happening and it only happens under Ubuntu.

---

### Post by juliobahar on 2010-03-23
> **taecha said:**
> Actually, the headset gets powered off. Don't ask me how, I don't have a clue. I can only tell you that's what's happening and it only happens under Ubuntu.

Really strange. I don't have a clue either. Let's see what happens if you just turn on the headset with out pairing nor connecting it to anything - I do mean absolutely anything - does it also power off by itself?

-I guess if you yes, that would mean ubuntu Btooth isn't sending a signal to actively sustain power-on to the headset. and for that I don't have any answers sorry.

---

### Post by taecha on 2010-03-26
> **juliobahar said:**
> does it also power off by itself?.

No it doesn't. It stays on until it runs out of power ...

---

### Post by creepa1982 on 2010-07-28
I had the same problem and used the troubleshooting tipps (especially 5) from this thread. Worked for me: 

[http://forums.debian.net/viewtopic.php?t=12497](http://forums.debian.net/viewtopic.php?t=12497)

---

### Post by dmar0 on 2010-10-23
<post deleted>

---


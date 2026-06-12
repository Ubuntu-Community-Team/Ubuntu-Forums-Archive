---
title: "No sound from pulseaudio?"
date: 2011-06-07
forum: Multimedia Software
---

### Post by xz124 on 2011-06-07
I seem to be having a problem with my sound. Every time I start my computer, I hear the sound played at the login screen and the sound played when I login. Right then, every time, the sound cracks up and stops before it finishes. Running "ubuntu-bug audio" shows that ALSA works fine but pulseaudio does not. Anyone have an idea about how to fix this? For reference, "pacmd list" says that there are 0 sinks, 0 sources and 0 caches.

**Edit**: Solved by a really stupid mistake: loose 3.5mm audio cable. Don't do that. Please. If you're looking for help on your sound and you're on a desktop computer, go, right now, and check to make sure that you haven't made the same mistake as me.

---

### Post by lidex on 2011-06-07
> **xz124 said:**
> I seem to be having a problem with my sound. Every time I start my computer, I hear the sound played at the login screen and the sound played when I login. Right then, every time, the sound cracks up and stops before it finishes. Running "ubuntu-bug audio" shows that ALSA works fine but pulseaudio does not. Anyone have an idea about how to fix this? For reference, "pacmd list" says that there are 0 sinks, 0 sources and 0 caches.

Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Then Re-install Pulse
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**

---

### Post by xz124 on 2011-06-08
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Then Re-install Pulse
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**

I didn't have an .asound file or an /etc/asound.conf file, but completed all the commands, rebooting twice in the process. I still don't have sound. Re-running `ubuntu-bug audio` says that it's now an ALSA problem as the first test sound doesn't play. `aplay test.wav` does nothing. MPlayer with a wav file outputting to pulse does nothing. I'm at a loss here :confused:. I've cleared configuration files, re-installed almost all packages relating to sound, but to no avail.

---

### Post by lidex on 2011-06-09
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by xz124 on 2011-06-09
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

I ran the script and chose to upload the information. The link is: [http://www.alsa-project.org/db/?f=cec7324a373f0223bc5e921cb3d9972c4b9517bf]("http://www.alsa-project.org/db/?f=cec7324a373f0223bc5e921cb3d9972c4b9517bf"). I also want to note that yesterday morning, while I did not hear the sound played when it was time to login, I did hear *parts* of the  sound played as the desktop loaded. The parts that played were clear without distortion, but mostly towards the end, the sound dropped out. After that, I couldn't play a wav file using any of my multimedia players, including aplay. I rebooted throughout the day and I heard the sound (never the full sound) maybe half the time.

---

### Post by lidex on 2011-06-09
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd_intel8x0 ac97_quirk=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

If the sound cuts out again run aplay -l while it's out and post results.

---

### Post by Yellow Pasque on 2011-06-10
It seems like sound cuts out when pulseaudio starts. Try going to System -> Preferences -> Startup Applications and disabling pulseaudio starting. See if you can get sound in a Flash site (like youtube).

---

### Post by xz124 on 2011-06-11
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd_intel8x0 ac97_quirk=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

If the sound cuts out again run aplay -l while it's out and post results.

Nothing changed. For reference, an Ubuntu live usb correctly plays sound, using both pulseaudio and straight ALSA. I also no longer hear the start-up sound, not even half the time, no crackling or distortion; it simply does not play.
aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```> **Temüjin said:**
> It seems like sound cuts out when pulseaudio  starts. Try going to System -> Preferences -> Startup Applications  and disabling pulseaudio starting. See if you can get sound in a Flash  site (like youtube).

Didn't change anything. I verified that pulseaudio didn't start using ps -ef | grep pulse. I do not get sound from youtube or a direct pulse audio player (mplayer).

---

### Post by xz124 on 2011-06-15
Bump? Sorry, this is just annoying me very much. ](*,)

---

### Post by lidex on 2011-06-15
Post this output please:
```
modinfo snd_intel8x0
```

---

### Post by xz124 on 2011-06-16
Well, this is embarrassing. The real reason that my sound wouldn't play was because the 3.5mm stereo audio cable connecting my computer to my monitor was loose. :o I am an idiot. Anyway, thank you guys for your help. If anyone stumbles upon this thread, hopefully the procedures shown before will help them. But please, please, to anyone asking for help with an audio problem, don't be like me; check the obvious things: connections, cabling, volume, mixers...first, before asking for help. Don't be like me wasting other people's time because I was too stupid to check the basics. Okay, I'm done. Have a nice day everyone.

---


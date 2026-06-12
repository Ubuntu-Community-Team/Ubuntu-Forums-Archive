---
title: "Internal microphone on Compaq laptop"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Dipdip on 2008-08-10
Hello, 

This is my first time using Ubuntu, I'm a complete newbie so go easy on me. By some miracle I got dual boot to work and everything runs just fine EXCEPT for the internal microphone I have on my Compaq Presario F700. Neither Skype nor Sound Recorder work. I have a Compaq AMD Athlon 64 X2 Dual Core TK-57 1.9GHz Laptop (F764CA) with Conexant High Definition Audio Chip 22. I've combed the forums and I've tried following up on help threads but to no avail. Help please! Thanks in advance.

---

### Post by cdtech on 2008-08-10
You could try running "alsamixer" on the command line. Use the arrow keys to select the input device and the m key to select. The up down arrow keys will adjust your volume.

Hope this helps......

---

### Post by Dipdip on 2008-08-10
cdtech, thanks for the reply. Unfortunately, I maxed everything out and also tried different combination of things and it still doesn't work. I got some extra info about the hardware though if it helps:

Card: HDA NVidia                                                 
Chip: Conexant CX20561 (Hermosa)

---

### Post by zachalekos on 2008-08-10
I have the same lappy running in Linux Mint with no issues.

---

### Post by Dipdip on 2008-08-10
What are your sound settings like?

---

### Post by Dipdip on 2008-08-10
Anyone have any ideas?

---

### Post by halln on 2008-08-10
> **Dipdip said:**
> Anyone have any ideas?

This is what I did, right click the speaker icon on top panel/open volume control/edit/preference/tick master,digital,digital input source,input sources,headphone as line out, then on the volume control window, go to option/ Digital input source: Analog Inputs  Input sources: Front mic . If ever this will not work, try to change Analog Inputs to digital. Hope this helps, pls. tell us if this works.

---

### Post by Dipdip on 2008-08-10
> **halln said:**
> This is what I did, right click the speaker icon on top panel/open volume control/edit/preference/tick master,digital,digital input source,input sources,headphone as line out, then on the volume control window, go to option/ Digital input source: Analog Inputs  Input sources: Front mic . If ever this will not work, try to change Analog Inputs to digital. Hope this helps, pls. tell us if this works.

Thanks, but some of those options do not even show up for me. The title bar says HDA NVidia (Alsa Mixer) in Volume Control. When I click Edit->Preferences, I have 7 check boxes, Master, PCM, IEC958, Digital, Docking Mic, External Mic and Internal Mic. That's it. When I change devices under File, all the other options will not give me the preferences you have outlined either. I can't even find an option menu in the Volume Control Window.

---

### Post by halln on 2008-08-10
I think this is something to do with your sound card mine is intel but I sorted it out with this fix, on the volume control, I've got: Playback,Recording,Switches and Option. Have you enable your restricted driver? System/Administration/Hardware Drivers. I'm not sure if this help you.

---

### Post by Dipdip on 2008-08-10
> **halln said:**
> I think this is something to do with your sound card mine is intel but I sorted it out with this fix, on the volume control, I've got: Playback,Recording,Switches and Option. Have you enable your restricted driver? System/Administration/Hardware Drivers. I'm not sure if this help you.

The hardware for my sound doesn't show up in Hardware Drivers window. The laptop speakers, headphone jack, built in webcam all work. Only the internal microphone doesn't work which is very puzzling to me.

---

### Post by OnigiriKing on 2008-08-11
I have the same model laptop, same problem! If anyone has any insight into this I'd like to solve this ASAP.

---

### Post by cdtech on 2008-08-11
Use this command in a terminal to record:
```
arecord -f cd -D hw:0,0 -d 20 test.wav
```
This will create a 20 second wav file in your current directory.
Then playback the recorded sound with:
```
aplay test.wav
```
and see if it recorded any sound.

Let me know..........

---

### Post by cdtech on 2008-08-11
This is the way I have mine setup and maybe it can help you to set yours up as well. If not then maybe it will give some direction to troubleshooting your setup.

The first thing you need to check is the sound settings - goto **"System > Preferences > Sound"** and make sure that all of the selections are set to **ALSA** (sound events, music and movies, audio conferencing). Under the **Sounds** tab be sure that the **"Enable software sound mixing (ESD)"** is checked (enabled).

See if ALSA detects the Internal Mic by using one of the following:

$ cat /proc/asound/cards
 **0** [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6480000 irq 21

$ cat /proc/asound/pcm
**00-01**: Conexant Digital : Conexant Digital : playback 1
**00-00**: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1

or

$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
**card 0**: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If ALSA see's the card then run **alsamixer**. In a terminal type:
$ alsamixer
then press the **"f5"** key which will take you to the capture settings.
Use the left and right arrow keys to move to the **"IntMic"** line (on mine it's the furthest to the right) and press the space bar to enable it. Use the gain adjust to the left of the **"IntMic"** (you'll see "Int Mic" label), adjust to your liking.

Hope this helps........

[ATTACH]81120[/ATTACH]

---

### Post by Dipdip on 2008-08-11
Well it seems like it's recording something when using arecord. But it's a few seconds of absolutely nothing. The rest I get:

$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6480000 irq 22

$ cat /proc/asound/pcm
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1

$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I run Alsamixer, there is no IntMic anywhere. What the heck is wrong?!?

---

### Post by cdtech on 2008-08-11
did you hit your "f5" key and look all the way to the right of the screen with your arrow keys?

---

### Post by Dipdip on 2008-08-11
Sure did! When I pressed f5 and went all the way to the right with the right arrow key, I get <Internal>.

---

### Post by cdtech on 2008-08-11
do you have any of these selections:
1.) Double-click the volume control icon in the top right of the screen.
2.) Select Edit / Preferences.
3.) Add "Digital" and "Digital Input Source" to the list of visible tracks.
4.) On the Options tab, select "Digital Mic 1" for "Digital Input Source".
5.) On the Recording tab, set the volume for the microphone.

---

### Post by Dipdip on 2008-08-11
> **cdtech said:**
> do you have any of these selections:
1.) Double-click the volume control icon in the top right of the screen.
2.) Select Edit / Preferences.
3.) Add "Digital" and "Digital Input Source" to the list of visible tracks.
4.) On the Options tab, select "Digital Mic 1" for "Digital Input Source".
5.) On the Recording tab, set the volume for the microphone.

On the list of tracks, I do not have a Digital Input Source option.

---

### Post by cdtech on 2008-08-11
You have Internal Mic checked, but it doesn't show up in alsamixer.

---

### Post by Dipdip on 2008-08-11
> **cdtech said:**
> You have Internal Mic checked, but it doesn't show up in alsamixer.

Well, the screenshot of alsamixer has Internal on the very right, which I assumed was Internal Mic in Volume Control.

---

### Post by cdtech on 2008-08-11
Try again with "sudo alsamixer -V -a"

---

### Post by Dipdip on 2008-08-11
> **cdtech said:**
> Try again with "sudo alsamixer -V -a"

Nope, nothing changes, it looks exactly the same as before. Thanks for all the help by the way!

---

### Post by Dipdip on 2008-08-12
Argh! I've been at this for a few days and I still haven't figured it out. I've kinda messed up the system a bit with no adverse effects trying to fix the mic. Is there anymore info I could give you guys that might help you/me?

---

### Post by sylvaticus on 2008-08-22
..exactly same situation as dipdip here (and same screenshots)... plugging a microphone works fine, ma no way to have the internal microphones to works..

---

### Post by Dipdip on 2008-08-22
Still hoping there's a solution...

---

### Post by firefly07 on 2008-12-03
I have the same lap... It's unbelievably bad that the webcam works flawlessly but the built-in mic won't work... Guess we'll have to wait for a new sound driver or else

---

### Post by nediceyuva on 2009-12-16
I have exactly the same laptop and the same problem as dipdip, but using ubuntu 9.10. Looks like there is still no solution.

---

### Post by erdalronahi on 2010-02-02
I have the same problem in Debian Lenny. The internal microphone shows up in alsamixer, but cannot be used.

---

### Post by nediceyuva on 2010-02-02
After weeks of searching for a solution on various ubuntu forums, I ended up buying an external microphone.

---

### Post by wilsontp on 2010-03-28
I have an HP tx2525nr...and everything works except my internal mic's, which is crappy because the webcam works beautifully.

---

### Post by wilsontp on 2010-03-28
> **cdtech said:**
> do you have any of these selections:
1.) Double-click the volume control icon in the top right of the screen.
2.) Select Edit / Preferences.
3.) Add "Digital" and "Digital Input Source" to the list of visible tracks.
4.) On the Options tab, select "Digital Mic 1" for "Digital Input Source".
5.) On the Recording tab, set the volume for the microphone.
 
cdtech, i don't have the ability to do this.  I guess I'm missing some software on my computer?
 
hp tx2525nr
ubuntu 9.10

---


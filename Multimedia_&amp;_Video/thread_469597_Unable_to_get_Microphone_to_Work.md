---
title: "Unable to get Microphone to Work"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by lillypilly on 2007-06-10
Using 7.04 fully updated on an Intel 945 Motherboard. Sound is working perfectly but I am unable to get the microphone to work.
Having read many threads on this subject and having looked at alsamixer and the Volume Control: HDA Intel(Alsa mixer) gui I note that I do not have a Capture Tab nor do I have any microphone indications in the Preference of the Volume Control
alsa-base and alsa-utils both installed

---

### Post by morty11 on 2007-06-11
i got the exact same problem and the exact same motherboard!! i have a Sigmatel STAC9227 built in my motherboard.. All sounds working absoultely great, however there's no "MIcrophone" or Microphone Capture in the Volume Preferences Panel.. I've tried updating the driver, and it still didn't work..

any help would be really appreciated..
morty

---

### Post by ridgeland on 2007-06-11
I recognized the STAC9227.  I have that in my Dell-Ubuntu.  But on mine when I double click on the volume to open the control panel under the menu option File I have Change Device.  There I can choose HDA Intel (Alsa Mixer).  The Alsa Mixer has options for Mic, Front Mic and Line.

Also try Menu -> System -> Preference -> Sound and try the settings there. Test all the option+Test choices.

I do have another issue I'm searching though.  The mic works great but I cannot record what I'm listening to.  Leads point to Jack, Ardour etc.....

---

### Post by morty11 on 2007-06-12
thanks for the reply.. i have already tried all of the tips you provided.. It still doesn't work.. I tried altering the original sound text file in the directory, pasting options snd_hda_intel mode=ref..i tried EVERY possible solution, and googled for hours.. still no solutions.. :(

It Still refused to work... looks like my sound card is a bit more stubborn than i thought..
Morty

---

### Post by rabideau on 2007-06-13
Hi Morty,

I had the same problem. 

I performed a double-click on Volume Master (which is apparently part of gstreamer).  The Volume Master was located in my gnome tray (I start the volume master upon login).

Once I did that I had to change my defaults by selecting Edit>>Preferences. In there I was able to enable all my mic functions and levels (testing them was impossible -- odd 'feature', maybe someone will enhance that)

My test was to use the Skype Test feature in Skype (oddly enough...)

Everything now works fine!

I hope this helps.

---

### Post by satellite360 on 2007-06-24
I had the same problem with the microphone and STAC9227.  Resolved it by adding
```
options snd-hda-intel model=3stack
```
to /etc/modprobe.d/alsa-base
rebooting then opening up the volume control and pushing capture up to 100% and changing the Input Source to Front Mic.

---

### Post by rumli on 2007-07-12
> **satellite360 said:**
> I had the same problem with the microphone and STAC9227.  Resolved it by adding
```
options snd-hda-intel model=3stack
```
to /etc/modprobe.d/alsa-base
rebooting then opening up the volume control and pushing capture up to 100% and changing the Input Source to Front Mic.

Thanks!  This worked perfectly for me on a Dell Dimension E521 with a Labtec (regular, non-USB) microphone.

---

### Post by ShyamSundar on 2007-07-18
Hi Guys,

I have  Intel Desktop Board DG965 RY model, I have similar problem that the Microphone is not recognized in the hardware list and in ControlPanel -> Sound & Audio Device -> the Audio & Voice tabs -> Sound Recording Advanced Option button is disabled. 

These are the followind Hardware & Software drivers I have in the PC.

Audio Device is STAC9227
Drivers Installed are SigmaTel Audio 

whereto set the string "options snd-hda-intel model=3stack" to over come this problem.

Is it in System -> Hardware -> DeviceManager or some other place...!

Help me to solve the problem

TY
Shyamn

---

### Post by satellite360 on 2007-07-18
> **ShyamSundar said:**
> 
whereto set the string "options snd-hda-intel model=3stack" to over come this problem.

```
sudo gedit /etc/modprobe.d/alsa-base
```
then add the string to the end of the file

---

### Post by mbdiego on 2007-09-04
Thank you satellite360. It worked for me. But I still wonder why if I have NVidia chipset not Intel. Dell Dimension E521 w/Athlon HDA NVIDIA, chip SigmaTel STAC9227, Ubuntu 7.04 Fawn Feisty

---

### Post by jcottier on 2007-11-20
I have a Dell E521with HDA Nvidia sound in Kubuntu Gutsy and the mic did not work in Feisty either. This fix worked for me :). The gnome sound test:capture gave a lot of broken pipe streaming errors, but sounded fine on the PC speakers. I tested with sound recorder and skype (as the sound is not output to the PC speakers except for the gnome sound test) and its works great. But why intel? Does this mean the hda-nvidia alsa driver is broken?.

---


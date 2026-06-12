---
title: "Can't use headphones."
date: 2011-07-15
forum: Multimedia Software
---

### Post by Jamsers on 2011-07-15
Hi everyone, my problem is very simple.

I can't use my headphone jack.

The laptops speakers work fine (in fact they're clearer and stronger than ever), but I can't use audio equipment that I plug into the audio jack (headphones, speakers, ect.).

I checked System/Sound, looked into the Output tab, and found that there are two devices for sound output displayed: Internal Audio Digital Stereo (HDMI, cause my laptop has an HDMI port), and Internal Audio Analog Speaker (default sound output). No "Headphones" or "3.5mm Jack" or something like that. Even when I have something plugged in the jack.

So when I plug in my headphones, no sound comes from them, and the laptop speakers are still playing. It's like Ubuntu doesn't detect anything plugged into the audio jack at all.

I own an Acer Aspire One 522.

---

### Post by Jamsers on 2011-07-16
Help please?

---

### Post by SomeGayDude on 2011-07-16
1) Open a Terminal="Applications->Accessories->Terminal"
 
 2) Open this file using root. 
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
 
 3) Add this line after the last line of the file
   ```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
 
 4)  Reboot your laptop and it should work.  
 
 Let me know if you have any other problems.  I think this is the only issue you laptop will have on a new intall.

---

### Post by Jamsers on 2011-07-20
Thanks for the help SomeGayDude, but it doesn't work. Plus, it made my sounds scratchy, so I had to remove the line.

So the problem still persists.

---

### Post by SomeGayDude on 2011-07-21
I am so sorry.  I was helping someone else with the same exact problem but a different laptop.  I got you two mixed up.  So, can you tell me what sound card you have.  In the meantime I will do some research.

From what I have been reading, its a Conexant sound chip.  Also, Gentoo Linux had no audio issues.  I'm still searching.

---

### Post by .... on 2011-07-22
model=dell-vostro trick seems to work: [http://ubuntuforums.org/archive/index.php/t-1680348.html](http://ubuntuforums.org/archive/index.php/t-1680348.html)

---

### Post by Jamsers on 2011-07-25
Yup. It's a Conexant sound chip. I think it's the only unfixed issue I have on this netbook - I fixed the "freezing on bootup" by enabling PXE from the BIOS, and everything else works flawlessly (well, except for suspend when proprietary drivers are installed). I'll try scouring through the linked forum post, see if maybe one of the posted fixes works.

Anyways, thanks so much for the help you guys.

---

### Post by Jamsers on 2011-08-06
I SOLVED IT! YEHEY! HAHAHA!

Open a terminal, and punch these in:

1> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
2> sudo apt-get update
3> sudo apt-get install linux-alsa-driver-modules-$(uname -r)

Then restart, and whala! HAHAHA! YES!

---

### Post by pashaespinosa on 2011-09-25
YEEAAHHH Thanx Jamsers  !!!!

---


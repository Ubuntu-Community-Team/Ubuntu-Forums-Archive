---
title: "Sound only from one speaker, other beeps"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by Rayko on 2007-02-26
Hello all! i love ubuntu i just installed it yesterday but already stumbled upon some problems!!!

At first i had sound coming only out of 1 speaker! the right! and if i'd adjust my volume through that speaker icon in the lower right hand corner i'd just lose all my sound!

after a couple of reboots, my left speaker still doesn't work, right still works, but now i have the problem too that my left speaker gives this continuous high-tone beep whenever a sound is supposed to be played from it! the problem with adjusting the volume remains the same however!

i followed some troubleshooting things, but before i give info on those, here's some info on my soundcard

soundcard is onboard soundcard on my asus P5VDC-X mobo, when i type into the terminal: aplay -l i get this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

note: both my speakers AND my headphones give me the same problem: left not working with beep, right working normally, i never had this problem before either and i just installed ubuntu yesterday

any help please???

---

### Post by Rayko on 2007-02-26
i now followed the explanations at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Background_.2F_Notes_.2F_Warnings](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Background_.2F_Notes_.2F_Warnings)

i'm at this now!
```
mkdir src
cd src 
mkdir alsa 
cd alsa 
sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2
tar -xvjf alsa-driver-1.0.12.tar.bz2
cd alsa-driver-1.0.12
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes
sudo make
sudo make install
```

but when i do sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes

i get this at the end
checking for which soundcards to compile driver for... configure: error: Unknown soundcard VT82xx

(ps i'm POSITIVE that's my soundcard cause when i type "aplay -l" i get
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Rayko on 2007-02-26
sorry for triple post but i really need help, oh and to update

i got the thing from my second post to work but sound still has same problems!!!!

---

### Post by Rayko on 2007-02-26
^bumb^ sorry i had to do this but i really need my problem solved :(

---

### Post by FunnyLookinHat on 2007-02-26
Rayko,
The problem is that your system is most likely trying to use ALSA to play sound, and the current version of ALSA in edgy (1.0.11) does not play well with your graphics card.

You should check out this post:
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=AD198x](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=AD198x)

Try following it through, especially the part that talks about compiling a new ALSA from the source found at the ALSA website (alsa-project.org).  You will want to get version 1.0.13 of the code.

Hope this helps!

-FunnyLookinHat

---

### Post by Rayko on 2007-02-27
i did that, thanks, but now everything is out, now i get this:
```

rayko@rayko-desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
```

so yeah

---

### Post by mitchej123 on 2007-03-06
Have you had any luck resolving this issue? I'm having the same problem you've described.

---

### Post by mitchej123 on 2007-03-06
Blah...looks like I actually found the fix for this a few days ago, however I typed it wrong when entering it in.

I just switched it, and it appears to be working now, but haven't had much time to test it.

Here's a quick rundown:

This is the listing of aplay -l 
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

After doing a little more looking around, I noticed it's using the snd-hda-intel module, I thought that might be the problem so tried using the vt82xx module instead, but then it said I had no sound cards (which looks like what you had). 

To fix the problem I went back to the snd-hda-intel module and added this to /etc/modprobe.d/alsa-base
```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```
(I had originally entered snd-intel-hda and that's why it didn't work since the module is snd-hda-intel)

If you haven't fixed it already, I'd suggest trying to go back to the default alsa libraries (or try the new version with the intel-hda driver) and see if that fix works.  

I can't tell you why that fixes it, just that it did for me and at least one other person I read about online, perhaps someone more knowledgeable could chime in :)

---

### Post by BigCommieNat on 2007-03-06
> **mitchej123 said:**
> 
To fix the problem I went back to the snd-hda-intel module and added this to /etc/modprobe.d/alsa-base
```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```
(I had originally entered snd-intel-hda and that's why it didn't work since the module is snd-hda-intel)


TOTALLY WORKED FOR ME!!!!
Thanks man... you're a lifesaver... I was just about to start compiling the via driver. PHWEW!

The sound... to me, reminds me of the auto jack sensing that kicks in in windows... dunno if that's it or not... but I'm happy to have sound back :)

---

### Post by mctk on 2007-03-10
Worked here as well.  Thank you very much.

---

### Post by micheleongaro on 2007-04-05
Hi everybody!

Worked here as well but... for just one boot. :confused: 
My conf:
motherboard: asus p5ld2 se 
sound card: audigy2 zs [sb0350]

in short: after adding the suggested line ( options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0 ) and rebooting, everything works ( in the sound card list appears only the audigy but it works very well ).
The problem appears at the second reboot ( and successive ones ). The "HDA Intel" appears again in the list but.. no sound at all ( both devices ).

any idea please? :) 

thank you very much!

michele

---

### Post by micheleongaro on 2007-04-05
Solved:
just disabled the onboard audio from the bios... anything simplier? ;)

---


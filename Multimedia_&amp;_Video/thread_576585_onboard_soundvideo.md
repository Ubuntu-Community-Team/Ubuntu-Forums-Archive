---
title: "onboard sound/video"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by doKtor_hallam on 2007-10-15
hello everyone. i am completely new to linux. i dont know unix at all, or any command line stuff. i have wanted to get into it for some time, so i just got kubuntu installed. (newest 7.10 version). i have a win2000/kubuntu dual boot setup with grub, which is working very nicely. it did a great job of auto-detecting hardware, except for my onboard sound. i am running an old acer aspire (currently with a pentium 2 333mhz soon to be upgraded to a celeron 1.3ghz.) i have 512k ram. my onboard audio is crystal, and the kernel did not recognize or install any support. i have looked up web tutorials galore, and they all tell me to add a driver package for my sound chip and then recompile the kernel, or make it as a module, and i dont know how to find my kernel config, i dont know how to add anything to it if i did find it, i dont know how to recompile it, really i dont know much. and they tell me this and that and this and that. since i know nothing, they all sound chinese to me. they assume more working knowledge than i have. can anybody patiently give me very simplified, step by step help to identifying, installing, and configuring my onboard sound PLEASE? (possibly even write out for me any command line stuff so i may just copy/paste it)  the only other issue i have at this point is that i run onboard video (ati 3d rage pro agp) and i cannot make my screen resolution greater than 800x600. is there any way to switch it to a greater size? (the display config in my system settings is set already at max size at 800x600).
any help with these two items would be HUGELY appreciated.

on the plus side, i love kubuntu otherwise so far and avidly work to learn it more and more (like an addiction) so that one magical day my hatred of the redmond project can be fully realized and i can finally do away with this dual boot issue! ;)

and on a side note, i have over 10,000 songs on one of my hard drives, but unfortunately mostly in .wma format. (a holdover from those sad, old, soon to be over days). does anybody know a utility to convert .wma to .mp3? or any other format that i can work with here in kubuntu? and i realize that converting this many files will take awhile, but i am willing.

thanks again everybody, and i am very happy to be here!
chris

---

### Post by doKtor_hallam on 2007-10-15
anybody? plz?

---

### Post by Vantskruv on 2007-10-15
I think you should specify in more detail which motherboard you have and which sound-chipset. I probably can't help you all the way. but maybe only the first steps.

---

### Post by doKtor_hallam on 2007-10-15
thank you!!!!!!!!!!
i dont really know how to id the board. the box is open and next to me right now. i dont see anything marking it really. (maybe some generic piece of yoyo that acer threw into a cheap box ? the only chip on the board that i can positively id as being for sound says:

CRYSTAL
CS4235-KQ EP
ZTAJVD9821

it is small, maybe 1/2 inch square

---

### Post by doKtor_hallam on 2007-10-15
does this help? i hope? or can you tell me what to look for to help id the board/sound chipset?

---

### Post by doKtor_hallam on 2007-10-15
i have just gotten hal device manager installed and running. 

it shows everything unknown for the system board. it shows two 440LX/EX - 82443LX/EX bridges, one Host and one AGP.
it shows a couple ALSA items1 sequencer device and 1 timer device) and a couple OSS items(2 sequencer devices).  it lista AT style speaker sound, with all properties marked unknown.  it shows a PC speaker and lists it as a Legacy Device, all other info unknown.  

thats all i see it list in regards to the board or sound.
does any of this help?

---

### Post by Vantskruv on 2007-10-15
I hope this I found works for you:

[http://ubuntuforums.org/showthread.php?t=24877](http://ubuntuforums.org/showthread.php?t=24877)

> **Zipslack said:**
> This is a quick-and-dirty hack to get the Alsa modules to load the cs4236 drivers (since the developers decided to leave-out alsaconf....)  This same technique should work with other Alsa drivers...just substitute the proper driver in place of "snd-cs4236"

1. Open a console and change to root
          sudo sh  (enter your password - prompt should change from "$" to "#")

2.  change to /etc/init.d
          cd /etc/init.d

3.  edit the file "bootmisc.sh"
          nano bootmisc.sh

4.  add a new line at the bottom that reads
          /sbin/modprobe snd-cs4236

5.  save the file
         ctrl-x, y, <Enter>

When you reboot, the sound will be initialized properly.  To get sound without rebooting first, (still at the console as root) enter :
       modprobe cs-4236
       /etc/init.d/alsa restart
You may need to restart the desktop to get all the sound server and mixer to respond properly.  

DIsclaimer:  There's a probably a better/safer way to fix this properly, but I was interested in getting it done quickly, and this is what works for me.  YMMV.

---

### Post by Vantskruv on 2007-10-15
Note! I'm getting a little confused of editing the bootmisc.sh. It doesn't look right.

I think you should edit the *modules* file in /etc

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by doKtor_hallam on 2007-10-15
i edited the bootmisc.sh and i substituted the xx35 for the xx36 that was listed because of the difference to my chip and it didnt work. so i went back in and changed it back and EUREKA!!! problem solved.  im not sure what the diff would be to do it in the module instead like you mentioned, but it is not needed.
THANK YOU so much for your help!!!!!!!!!!!!!

---

### Post by Vantskruv on 2007-10-16
Congratulations! I'm glad you got it working! :guitar:

---


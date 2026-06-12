---
title: "no sound on ubuntu 10.04  with &quot;soundMAX integrated Digital HD Audio&quot; soundcard"
date: 2010-11-02
forum: Multimedia Software
---

### Post by envis on 2010-11-02
i would like some help, i wanted to setup a ubuntu 10 desktop on some amd64 comp to make it a comp to watch movies and listen to music, but no luck cos i cant get the sound working.

i noticed lots of ppl with same soundcard than me having the same problem. ("soundMAX integrated Digital HD Audio" its an onboard video card on my 64 bits nvidia motherboard thats about 5 years old..)

old thread about this: [http://ubuntuforums.org/archive/index.php/t-179322.html](http://ubuntuforums.org/archive/index.php/t-179322.html)

unfortunately the fix suggested in there does not seem to work for me.

> -Update BIOS (not even sure if that is required step, but it generally always good idea to do that).
-Get latest ALSA drivers ([http://www.alsa-project.org/](http://www.alsa-project.org/)). I got "1.0.12rc1" but "1.0.11 final" should also do.
-Put "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base".
-Worked for me after reboot.

i skipped all the parts about *updating, i downloaded that ubuntu install from ubuntu.com yesterday im pretty sure the alsa drivers should be up to date.

i dont have a file alsa-base in /etc/modprobe.d but i have a alsa-base.conf i assume its the same thing i see theres already a bunch of "options" listed in there so it looks like its the right place to add the "options snd-hda-intel position_fix=1 model=3stack" option, which i did and rebooted, but still no sound.

also when i go in system/preferences/sound i see my sound card in hardware.
also i have a windows xp partition on there and when i boot in windows xp i have sound so i know its not a connection problem or speakers are off or something like that.


ok i guess ill watch my movies on the windows partition just for now cos i got work to do, cant spend all day trying to get the sound working!! but it would be nicer if i could use the ubuntu partition... anyone has any advice on how i could solve this problem? thanks in advance!

---

### Post by lidex on 2010-11-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Sirocco01 on 2011-07-21
Help guys!!!

No sound on Toshiba Satellite U200 running UBUNTU 11.04

[http://ubuntuforums.org/showthread.php?p=11072612#post11072612](http://ubuntuforums.org/showthread.php?p=11072612#post11072612)

---


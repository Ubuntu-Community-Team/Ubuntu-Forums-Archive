---
title: "3,5mm combo jack (ASUS X550VB)"
date: 2015-09-24
forum: Multimedia Software
---

### Post by Jan_Strek on 2015-09-24
Hello,

firstly i want really apologize for my techical skills and for my English, but i want to use ubuntu for personal reasons, but sound from jack (headphones) doesnt work properly, but from internal spekaers its everything OK. 

I have 3,5mm combo jack, on my laptop ASUS X550VB. 

I already tried reinstall different packages of alsa, alsa-mixer and other programs about sound (pavucontrol, etc.). I also tried many forums, many pages. 

I tried other linux distributions (like for example mint, open-suse, etc.). On every linux based system is the same result. Speakers works great but headphones (jack) no.

I have dual-boot with Windows. On windows everythink works great (W7, W8.1 and W10).

I really dont know, what I do wrong. With my bad English I even dont know, if I write to right place. If you know more information about my system, or some debug info, please write how can i do it, and i will do it :) 

I have also run some script for Alsa debug info (src: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh))
Result: [http://pastebin.com/HV5kK53m](http://pastebin.com/HV5kK53m)

Thank you in advance!

---

### Post by Bucky Ball on 2015-09-24
Welcome. You have been up every gum tree! If this is a fresh install, everything should have been fine. We'll keep our fingers crossed that none of the tweaks has confused the issue and is now blocking audio. Try this.  

Play some music through the speakers> Open Pulse Audio Volume Control> Output Tab> set the port for 'Analogue Stereo' to headphones. 

In the 'Playback' tab you will see the audio stream of the music playing (if you are using VLC to play the music, for instance, the stream will be 'VLC Audio Stream ...'. Set that to 'Built in Audio Analogue Stereo'.

Which release and flavour of Ubuntu are you using?

---

### Post by Yellow Pasque on 2015-09-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366639)

---

### Post by Jan_Strek on 2015-09-25
Hi,

yesterday I reinstall Ubuntu with clean installation. After installation sound works perfect (both from speakers and headset), but today again sounds from headphones doesnt work. It stopped work immediately after Ubuntu update (i do not anything else). 

**Update log (cat /var/log/apt/history.log)**
[http://pastebin.com/uHtZpSdr](http://pastebin.com/uHtZpSdr)

**Alsa-info**
[http://pastebin.com/CUYCdP11](http://pastebin.com/CUYCdP11)

Nothing what did you post dont help. Version of Ubuntu is in Alsa-info log. 
When i plug Headphones to my notebook (laptop), in Sound Settings it will switch that one only output's name from Speakers to Headphones.

Any other idea? Which update it can do it? I can unnistal it, but i dont know which one :( 

Many thanks in advance, guys :)

---

### Post by Jan_Strek on 2015-09-25
**uname -a**
Linux lucky-X550VB 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

---


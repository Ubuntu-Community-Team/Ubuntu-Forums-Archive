---
title: "Sound in 10.04 worked yesterday, not today."
date: 2010-05-20
forum: Multimedia Software
---

### Post by IanPallton on 2010-05-20
Sound was working until yesterday, but today nothing. 

> aplay -l
aplay: device_list:223: inga ljudkort hittades...
(It says no soundcards found) 
but if run with sudo: 

> sudo aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: ALC889A Analog [ALC889A Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: ALC889A Digital [ALC889A Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0


Any tips ? And, what happened over night ? Listening to music was the 
last thing I did before shutting down for the day.

(I use Ubuntu 10.04)

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

Now this output please: 
```
aplay -l
```

---

### Post by DanCar on 2010-05-20
The reinstall seemed to fix the issue.  Although I also went to system -> preferences -> sound settings and raised the volume from zero.  Not sure which one fixed it.

Thanks!  :-)

---

### Post by lidex on 2010-05-20
Do you regularly use ubuntu as root?

---

### Post by IanPallton on 2010-05-21
Thanks for all the answers.

The wierdness continues. A few reboots later the sound works again 
and has since. 

It seems very random and related to the issue people are having with not
being able to shutdown ubuntu. When I had no sound, I was also unable to shutdown. 

I'm guessing devs are working on this shutdown issue and that it will be resolved soon. The web and forums are full of people complaining about it 
and proposing really "hacky" fixes to it. 
I will wait for an update that solves it at the root cause. 

Have a nice day!

---

### Post by megadesign on 2010-05-21
Same problem here. No sound + unable to reboot/shutdown. It always returns to login screen after restart or shutdown confirmation.

---

### Post by MDCCCX on 2010-06-17
Same here. Is there an issue on launchpad?

---

### Post by Lokiii on 2010-06-17
Exact same issue. If I just reboot enough times, sound the suddenly works. Next reboot though, its usually not working again. And when the sound isnt working the shutdown/reboot doesnt either..

---

### Post by Lokiii on 2010-06-20
Anyone been able to solve this issue?

---

### Post by MDCCCX on 2010-06-20
[Lokiii]("http://ubuntuforums.org/member.php?u=661305"): Thats the exact problem that I get. The only thing I've managed to do which seemed to work. I did sudo nano /etc/group and changed the aduio:x29:pulse to aduio:x29:pulse,username I don't know if this is the right thing to do. Have you had problems mounting media and shutting down also?

---

### Post by nss0000 on 2010-06-20
> **MDCCCX said:**
> [Lokiii]("http://ubuntuforums.org/member.php?u=661305"): Thats the exact problem that I get. The only thing I've managed to do which seemed to work. I did sudo nano /etc/group and changed the aduio:x29:pulse to aduio:x29:pulse,username I don't know if this is the right thing to do. Have you had problems mounting media and shutting down also?

Mebby your sound-issue is related to deeper kernel issues; there's a <bug> that randomly assigns/de-assigns printer-function as well ... and vidcams I suspect. It's months-old , being worked on and no solution yet.

---

### Post by Lokiii on 2010-06-21
> **MDCCCX said:**
> [Lokiii]("http://ubuntuforums.org/member.php?u=661305"): Thats the exact problem that I get. The only thing I've managed to do which seemed to work. I did sudo nano /etc/group and changed the aduio:x29:pulse to aduio:x29:pulse,username I don't know if this is the right thing to do. Have you had problems mounting media and shutting down also?

Dont know about mounting media, but when I dont have sound I cant shut down or reboot either (have to use sudo shutdown -h / -r now)

---

### Post by lkjoel on 2010-06-21
Click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

Let me know if it works!

---


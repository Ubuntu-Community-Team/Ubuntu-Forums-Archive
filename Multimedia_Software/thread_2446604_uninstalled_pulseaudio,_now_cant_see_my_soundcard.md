---
title: "uninstalled pulseaudio, now cant see my soundcard"
date: 2020-07-03
forum: Multimedia Software
---

### Post by devdlp on 2020-07-03
so i installed mixxx to braodcast music, and noticed my music or mic stopped working. so i looked into it and people suggested to use jackd and either get rid of pulseaudio or use it with jackd. 
i wanted to only use jack. thats the first mistake because i uninstalled pulseaudio and dont know how jack works completely just watched a few videos and now in my settings and pulse volume doesnt show my sound card or blue snowball mic that is usb.
so basically i need my sound back with jack and my mic to work with it aswell what do i do because i installed alot of stuff DO NOT want to reinstall the entire os. im using ubuntu 20.04 btw

---

### Post by devdlp on 2020-07-03
now i kinda want pulseaudio back because if thats the best way to get my soundcard recognized and mic im all for it so please someone help with this

---

### Post by devdlp on 2020-07-03
so i have sound back now from this link [http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/](http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/) i have sound again and it recognizes the sound card and the snowball mic but still dont know if i can use mixxx without it cutting off other apps

---

### Post by devdlp on 2020-07-03
so as soon as i got sound i wanted to restart the pc to see if it worked. now there is no devices to play sound not even my monitor shows
now i have sound just using alsa and jack but youtube videos dont have sound and my mic is not working please please help with this
if someone would walk me thru this it would be apprciated

---

### Post by devdlp on 2020-07-03
im just gonna reinstall ubuntu, thnx

---

### Post by uninvolved on 2020-07-03
> **devdlp said:**
> im just gonna reinstall ubuntu, thnx

LOL I've used that solution countless times!

 Did you at least learn the trick of partitioning your drive so that you can preserve /home between new/re-installs? That'll save you some time. Another is to image your freshly installed & updated OS, as it's easy to just restore and save some time that way.

---

### Post by Yellow Pasque on 2020-07-04
Do not uninstall pulseaudio. You can suspend it if you have to.

Required reading: [https://www.mixxx.org/manual/latest/en/chapters/preferences.html#gnu-linux](https://www.mixxx.org/manual/latest/en/chapters/preferences.html#gnu-linux)
In other words, the easiest way is to route everything through pulseaudio. You need to choose "pulse" for your device(s) in mixxx's preferences. Make sure you have the correct devices selected in pavucontrol. Also make sure you have libasound2-plugins package installed (I think it's installed by default, but double check it.)  If this method works/performs acceptably, problem solved.

The other way is to use the ALSA device directly, but note that this will block other programs from using audio while you are running mixxxx.
First, you need to make sure your user is in the "audio" group
```
sudo usermod -a -G audio yourusername
```
Reboot to make sure the change takes effect. Then you have to suspend pulseaudio when you run mixxx:
```
pasuspender -- mixxx
```

---

### Post by devdlp on 2020-07-18
i just reinstalled then used pulseeffects

---


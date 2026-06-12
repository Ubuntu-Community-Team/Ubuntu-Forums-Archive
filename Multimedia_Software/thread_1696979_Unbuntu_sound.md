---
title: "Unbuntu sound?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by Dominator_X on 2011-02-28
Hello! Does anyone notice how poor is sound playback in Ubuntu? I don't know if this is a general problem in all distros, but as a beginner i decided to install Ubuntu as its popular for users with minimalistic or not much knowledge about Linux at all. So in Windows playback sound quality is great, but in Ubuntu it is terrible, why is that? My soundcard is motherboard integrated - Asus M4A77TD PRO. 

In other forums someone give me advice to write this

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

 in terminal, each one individually, then restart but no improvement at all. SO what can i do to get really nice and pleased sound playback :guitar:?

---

### Post by cascade9 on 2011-02-28
Ugh, the Asus M4A77TD PRO uses a VIA1708S sound chip. Those things are horrible. 

I havent noticed any major differences between the sound quality on windows and linux with that chip, but I didnt install any software that could affect the quality, but I really didnt spend much time with the sound either (my housemates machine uses the same chip, and I setup windows + *nix for them). 

As for how to make it sound better, get a soundcard. ;)

---

### Post by mastablasta on 2011-02-28
can you do 
 
[FONT=Courier New]sudo alsaconf[/FONT]
 
? it might configure the card a bit better. also try to type 
 
alsamixer 
 
in terminal and set volume levels. perhaps the output is too high or too low on certain channel.
 
VIA chips have crappy sound in linux - ofcourse they work nice in Windows as the manufacturer provided windows drivers for them. we need to wait for community to get us better drivers.

---

### Post by Dominator_X on 2011-02-28
> **mastablasta said:**
> can you do 
 
[FONT=Courier New]sudo alsaconf[/FONT]
 
? it might configure the card a bit better. also try to type 
 
alsamixer 
 
in terminal and set volume levels. perhaps the output is too high or too low on certain channel.
 
VIA chips have crappy sound in linux - ofcourse they work nice in Windows as the manufacturer provided windows drivers for them. we need to wait for community to get us better drivers.


Ok, I will try this later and will post here.;-)

---

### Post by Dominator_X on 2011-03-01
Here is the commands i wrote, is there anything wrong?

```


unix@unix-System-Product-Name:~$ cat /proc/asound/pcm
00-00: VT1708S Analog : VT1708S Analog : playback 2 : capture 2
00-01: VT1708S Digital : VT1708S Digital : playback 1
01-03: HDMI 0 : HDMI 0 : playback 1
unix@unix-System-Product-Name:~$ 


unix@unix-System-Product-Name:~$ uname
Linux
unix@unix-System-Product-Name:~$ sudo apt-get install linux-backports-modules-alsa-2.6.35-25-generic[
[sudo] password for unix: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-alsa-2.6.35-25-generic[
E: Regex compilation error - Invalid regular expression
E: Couldn't find any package by regex 'linux-backports-modules-alsa-2.6.35-25-generic['
unix@unix-System-Product-Name:~$ 


Linux unix-System-Product-Name 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
unix@unix-System-Product-Name:~$ 


cat /proc/asound/version


unix@unix-System-Product-Name:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Feb 14 2011 for kernel 2.6.35-25-generic (SMP).
unix@unix-System-Product-Name:~$


```

Also this ```
 sudo alsaconf
```  show error when run it?

---

### Post by lidex on 2011-03-01
Try this as it may help - it definitely won't hurt. Using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

BTW, alsaconf doesn't work with ubuntu patched alsa.

---

### Post by Dominator_X on 2011-03-02
> **yehaocan said:**
> Ugh, the Asus M4A77TD PRO uses a VIA1708S sound chip. Those things are horrible. 

I havent noticed any major differences between the sound quality on  windows and linux with that chip, but I didnt install any software that  could affect the quality, but I really didnt spend much time with the  sound either (my housemates machine uses the same chip, and I setup  windows + *nix for them).

Sorry, but your post doesn't help a lot. I read it already. You just copy and paste the previous post of @cascade9.

---

### Post by lidex on 2011-03-02
> **Dominator_X said:**
> Sorry, but your post doesn't help a lot. I read it already. You just copy and paste the previous post of @cascade9.
I just realized you have compiled 1.0.24 alsa. That is the latest version. You don't want to use backports with that. If you want to use backports or updated driver modules go back to your default alsa install.

---

### Post by Dominator_X on 2011-03-02
> **lidex said:**
> I just realized you have compiled 1.0.24 alsa. That is the latest version. You don't want to use backports with that. If you want to use backports or updated driver modules go back to your default alsa install.

I already reinstall Ubuntu. The sound seem a bit more nicer, when i type in terminal alsamixer and turn down CD volume. Now the sound distortion seem gone.

---


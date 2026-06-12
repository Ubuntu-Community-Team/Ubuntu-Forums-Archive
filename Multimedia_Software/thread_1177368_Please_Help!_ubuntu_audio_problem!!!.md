---
title: "Please Help! ubuntu audio problem!!!"
date: 2009-06-03
forum: Multimedia Software
---

### Post by iceguggles on 2009-06-03
[SIZE=3]please help me, ive already reinstalled ubuntu 3 times...

i have this sound problem, and its going on my nerves, ive already tried everything, every guide ... looked in every thread but no use.:(

im on HP pavilion tx2670 : AMD turion x2 64 ultra 2.2; 3GB ram; ATI radeon 3200 HD, Realtek HDA; Ubuntu 9.04

Please help me :(

thnx in advance
[/SIZE]

---

### Post by jerrrys on 2009-06-03
maybe you should tell us what the sound problem is, what media player and which ubuntu you are using...

---

### Post by iceguggles on 2009-06-03
> **jerrrys said:**
> maybe you should tell us what the sound problem is, what media player and which ubuntu you are using...


[SIZE=2]ubuntu 9.04 i386 - jaunty

and the sound problem is that it doesnt work at all...
that includes playing music files and etc ... 
i just get this loud bip sound when i want to restart or shutdown or w/e.
ive also tried the unmuting process and just wont work.
once i tried to install the realtek driver (alsa-driver, alsa-lib, alsa-util) through the terminal and it totaly removed everything including all the alsa mixer and drivers!!!

** aplay -l : **

[/SIZE]```


**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by Favux on 2009-06-03
Hi iceguggles,

To get sound working for a TX2500 (at least in Hardy and Intrepid and I think Jaunty) to the bottom of the file "/etc/modprobe.d/alsa-base" you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
To edit the file you would use in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base

```
Since you have to be root when you edit it gksudo (the graphical version of sudo) will do that. It will ask for your password. Gedit is gnome-edit, a graphical editor.  Which is why you use them together.

If you want to determine your soundchip:
```
aplay -l
```

Hope this helps.

---

### Post by iceguggles on 2009-06-03
[SIZE=2]**wow... finally it worked; Thnx Alot Mate**:KS

ive already tried that b4 too but, idk maybe in the end of the line was '0' instead of '1' i dont recall well... i have tried it b4 and it wouldnt save ... i mean after i ran it again it was again empty; but anyway now its working, **but there is still a little issue, and that is the sound isnt strong, comparing to my windows. any suggestions on this?**

- After reboot i tested the sound and it was very weak so i ran 'alsamixer' and maximized all the volumes, and noticed something and thougtht it might help others:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116341&stc=1&d=1244076066[/IMG]

As shown above in the picture there were no bars b4 only the little squares indicating the mute 'MM' and the unmute '00'
[/SIZE]

---

### Post by danebramaged on 2009-06-03
I was running just fine up until a few weeks ago.  Sound-wise that is.  Now when I turn on my computer I hear a bit  of an intial "bump" from the speakers and then nothing.  No drums and no crickets.  I thought I was one of the lucky ones with no sound problems but now, after a month of sound, nothing but silience.

My mobo is an nforce 250 gigabyte, my cpu an amd semperon 3100+, my sound card is a creative labs 24-bit.  I am on 9.04.

What is the equivalent info that i need to type in to get my sound back?

...help me, ...please, ...and thanks.

---

### Post by Favux on 2009-06-03
Hi danebramaged,

Sorry to hear that.  I am far from a sound guru.

Assuming an alsa-base option line is what you need basically you want to use "aplay -l" to get your card.  Then you look it up in "ALSA-Configuration.txt" and see what the line is.  Sometimes there's multiple options and you just try them, one after the other.  It should be on your system somewhere, probably in "/usr/share/doc/alsa-base".  But here is a site with it:  [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)  And some more info.:  [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and  [http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

Good luck!

---

### Post by danebramaged on 2009-06-03
> **Favux said:**
> Hi danebramaged,

Sorry to hear that.  I am far from a sound guru.

Assuming an alsa-base option line is what you need basically you want to use "aplay -l" to get your card.  Then you look it up in "ALSA-Configuration.txt" and see what the line is.  Sometimes there's multiple options and you just try them, one after the other.  It should be on your system somewhere, probably in "/usr/share/doc/alsa-base".  But here is a site with it:  [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)  And some more info.:  [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and  [http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

Good luck!


Thank you for your prompt response.  I will scan through all of the above and let everybody know how it turns out.  It will probably be in a couple of days.  Maybe less.

tayl

---

### Post by joneseyrocks on 2009-06-04
i too had sound for a while after switching to ubuntu and due to other problems with jaunty i am using intrepid. i have installed nearly every alsa package and thought i had sound for a minute but to no avail. i have gotten the restricted files or whatever they are called per another thread suggestion and i try unmuting everything but nothing helps i did the aplay thing and got this

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
christopher@christopher-desktop:~$ 

i am a major noob when it comes to linux and all of the command lines and whatnot so any help would be great i already cant play perfect world until i get a new video card now i cant even listen to music i am going nuts ](*,)

---

### Post by joneseyrocks on 2009-06-04
ok nevermind and thanks anyway i just restarted the system and bada bing i got sound. i happen to use headphones as i watch movies through hulu while my daughter is sleeping and so when it restarted and made its initial noises i nearly blew an eardrum lol

---


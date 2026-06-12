---
title: "How to enable 5.1 in mobo with only 3 jacks"
date: 2011-12-26
forum: Multimedia Software
---

### Post by vaah on 2011-12-26
Hi, I have the same as this guy but no solution. [http://askubuntu.com/questions/54265/how-to-configure-5-1-surround-sound-through-three-3-5-mm-jacks](http://askubuntu.com/questions/54265/how-to-configure-5-1-surround-sound-through-three-3-5-mm-jacks)
I've been searching the internet and i havent found a solution.
My motherboard is gigabyte ga-z68ma-d2h-b3 which only has 3 jack at the back panel, line in (blue), line out(green), mic (pink). In windows I can configure the function of each jack thorugh audio driver.

I'm at lost now, please help me out. Thanks.

---

### Post by Lampi on 2011-12-26
I had a quick look at the online manual of your board and the askubuntu post:

There's no way you can use the rose/blue jack to get surround sound, the manual of your board has a detailed explanation how to connect the onboard pins in chapter 5. There's also an SPDIF header if your soundsystem supports it.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> I had a quick look at the online manual of your board and the askubuntu post:

There's no way you can use the rose/blue jack to get surround sound, the manual of your board has a detailed explanation how to connect the onboard pins in chapter 5. There's also an SPDIF header if your soundsystem supports it.
hmmm...really? I must have missed it then... Could you tell me on which page? so i can have another look at the manual..btw my soundsystem is logitech z5500, pretty sure it supports spdif but i lost my optical cable so if i'm already at dead end now. I'll buy a new optical cable then.

---

### Post by VanR on 2011-12-26
Don't know if your board can do this , but if it works in Windows like mine does here is what I did to get surround sound in Ubuntu. I only have 4 speakers .
Click on the volume control and select Sound Preferences
Go to the Hardware Tab and select 5.1 surround and analog stereo input. edit: I didn't have the option to choose 4.0 surround until I installed 3.0 kernel so you may not even have this option depending on what kernel you have installed. 
Open a terminal and type alsamixer
Now maximize the terminal so you can see all the choices.
Use right arrow key to scroll over to channel and select 6ch (I use 4ch here)
Make sure the volumes are up on the surround, center and LFE sliders and check to see if all your speakers are working now.
This worked for me. Hope it works for you.

---

### Post by Lampi on 2011-12-26
Guess I was wrong there ... Page 91 in Chapter 5.2 shows it for a 7.1 system!

Rose is center/subwoofer out
Blue is Rear out

I guess the windows driver will make sure to disable mic/line-in and configure it for output, don't hold your breath alsa/pulse can do the same in linux :)

Keep me posted, never knew one could connect it like that ...

---

### Post by vaah on 2011-12-26
> **VanR said:**
> Don't know if your board can do this , but if it works in Windows like mine does here is what I did to get surround sound in Ubuntu. I only have 4 speakers .
Click on the volume control and select Sound Preferences
Go to the Hardware Tab and select 5.1 surround and analog stereo input. edit: I didn't have the option to choose 4.0 surround until I installed 3.0 kernel so you may not even have this option depending on what kernel you have installed. 
Open a terminal and type alsamixer
Now maximize the terminal so you can see all the choices.
Use right arrow key to scroll over to channel and select 6ch (I use 4ch here)
Make sure the volumes are up on the surround, center and LFE sliders and check to see if all your speakers are working now.
This worked for me. Hope it works for you.
Does you mobo also have 3 jacks at the back panel? I might try your suggestion after i got home.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> Guess I was wrong there ... Page 91 in Chapter 5.2 shows it for a 7.1 system!

Rose is center/subwoofer out
Blue is Rear out

I guess the windows driver will make sure to disable mic/line-in and configure it for output, don't hold your breath alsa/pulse can do the same in linux :)

Keep me posted, never knew one could connect it like that ...
YEah, I reread my manual again after you mention about connecting pin onboard, but couldn't find what you said. :) I just did a bit searching and found this [http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm](http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm) I'll try this after i got home.
Question is how do i know if i'm running alsa or pulse? I'm a bit noobs here.

---

### Post by VanR on 2011-12-27
> **vaah said:**
> Does you mobo also have 3 jacks at the back panel? I might try your suggestion after i got home.

Yep my motherboard has 3 jacks on the back. Green. Blue and Pink I believe. I use the Green for Front R/L and the Blue for the Rear R/L. I don't have a center speaker  or subwoofer (LFE)

---

### Post by VanR on 2011-12-27
> **vaah said:**
> YEah, I reread my manual again after you mention about connecting pin onboard, but couldn't find what you said. :) I just did a bit searching and found this [http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm](http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm) I'll try this after i got home.
Question is how do i know if i'm running alsa or pulse? I'm a bit noobs here.

Just try the steps I gave you and see if you get surround sound.

---

### Post by vaah on 2011-12-27
> **VanR said:**
> Just try the steps I gave you and see if you get surround sound.
Yeah I will, I'm still at work now btw cheers for the help. Will keep you guys posted.

---

### Post by vaah on 2011-12-28
> **VanR said:**
> Just try the steps I gave you and see if you get surround sound.
Hi vanr, tried your suggestion and it didn't work.

---

### Post by vaah on 2011-12-28
> **vaah said:**
> YEah, I reread my manual again after you mention about connecting pin onboard, but couldn't find what you said. :) I just did a bit searching and found this [http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm](http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm) I'll try this after i got home.
Question is how do i know if i'm running alsa or pulse? I'm a bit noobs here.
The solution from [http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm](http://www.rdeeson.com/weblog/114/enable-51-linux-audio-on-motherboards-with-only-3-jacks.htm) works for me! YAY!!

I added "options snd-hda-intel model=3stack-6ch" to both /etc/modprobe.d/options and /etc/modprobe.d/alsa.conf because i don't know if i use alsa or pulse, but hey it works. so no worries. Thank you guys for all the help!! :)

---


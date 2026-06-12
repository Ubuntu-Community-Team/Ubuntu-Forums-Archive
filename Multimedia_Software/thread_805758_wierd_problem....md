---
title: "wierd problem..."
date: 2008-05-24
forum: Multimedia Software
---

### Post by Bailey321 on 2008-05-24
Bit of a wierd one here tbh....Im using ubuntu gutsy and my codecs keep failng. I play a video, it will work fine but after a while the screen just goes pink and i cant view the video all i can hear is the audio, this is with vlc and mplayer so gotta codecs. If i do a reboot it will go back to normal and work until it decides to go wierd again. I followed this guide ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)) for my codecs and all my multimedia programs that i use so maybe theres something in there thats doin it but im at a total loss at the moment,this my third installation of ubuntu and this time i have it perfect for what i need id hate to have to mess around and screw it up again, hopefully sombody out there has had some experience with this or knows what needs configuring/removing.

Cheers!

---

### Post by overdrank on 2008-05-24
> **Bailey321 said:**
> Bit of a wierd one here tbh....Im using ubuntu gutsy and my codecs keep failng. I play a video, it will work fine but after a while the screen just goes pink and i cant view the video all i can hear is the audio, this is with vlc and mplayer so gotta codecs. If i do a reboot it will go back to normal and work until it decides to go wierd again. I followed this guide ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)) for my codecs and all my multimedia programs that i use so maybe theres something in there thats doin it but im at a total loss at the moment,this my third installation of ubuntu and this time i have it perfect for what i need id hate to have to mess around and screw it up again, hopefully sombody out there has had some experience with this or knows what needs configuring/removing.

Cheers!

Hi and it maybe a graphics issue also, what is the model of the graphics card?

---

### Post by Bailey321 on 2008-05-24
Leadtek WinFast GeForce 7600 GS 256MB DDR2 PCI-E

I have the nvidia driver installed and have also manually confugred my resolution if that helps.

---

### Post by overdrank on 2008-05-24
> **Bailey321 said:**
> Leadtek WinFast GeForce 7600 GS 256MB DDR2 PCI-E

I have the nvidia driver installed and have also manually confugred my resolution if that helps.

Ok, have you used the nvidia-settings to check the temp of the graphics card? I have seen users in the forum with a similar issue on the video but I have no solution.

---

### Post by Bailey321 on 2008-05-24
Nope, cant say i no how and after my abismal last attempt at messing with the nvidia settings lol....Would you mind explaing how i do that plz?


Found them its sitting at 45c which is resonable so i doubt thats causing the problem, its so dam frustrating, dont tell me i need to reinstall AGAIN :(

Any suggestions would be helpful....

---

### Post by overdrank on 2008-05-24
> **Bailey321 said:**
> Nope, cant say i no how and after my abismal last attempt at messing with the nvidia settings lol....Would you mind explaing how i do that plz?


Found them its sitting at 45c which is resonable so i doubt thats causing the problem, its so dam frustrating, dont tell me i need to reinstall AGAIN :(

Any suggestions would be helpful....

Hi and you do not have to make any changes that will effect your system, just view the thermal settings. Just a thought to see if you graphics is overheating when the video changes.
I do not think you will need to reinstall, you may look at Envy and roll back to a older driver. I had to do this on my son's system for his PNY 7300

---

### Post by Bailey321 on 2008-05-24
Yay i believe its fixed, i went to System > Administration > Screens and Graphics > Garphics Card....I changed the driver to the geforce 7 series (think it was on some default one) logged out, back in and straight away i noticed a big difference and everything seems fine now ;)

---

### Post by overdrank on 2008-05-24
> **Bailey321 said:**
> Yay i believe its fixed, i went to System > Administration > Screens and Graphics > Garphics Card....I changed the driver to the geforce 7 series (think it was on some default one) logged out, back in and straight away i noticed a big difference and everything seems fine now ;)

Great good luck! :KS

---


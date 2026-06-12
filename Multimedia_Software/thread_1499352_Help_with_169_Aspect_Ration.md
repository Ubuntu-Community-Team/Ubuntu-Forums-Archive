---
title: "Help with 16:9 Aspect Ration"
date: 2010-06-01
forum: Multimedia Software
---

### Post by britishfish on 2010-06-01
Hello,
I just downloaded Ubuntu 10.4 and love it.  The only thing that I have a problem with is that I cannot change my aspect ration to 16:9 which is what my monitor is (its a flat screen in my media room).  I hope that someone can help me!  Thanks again!

---

### Post by britishfish on 2010-06-02
I know its not my graphics card because it works great in Windows 7

---

### Post by smittie46 on 2010-06-02
sorry im new also but i had problems similar and had to install dedicated ATI drivers and rebooted and then everything worked great also I messed with the  monitors app already install under system then preferences sorry If you know this already I also am new to Ubuntu community and I love it so  just trying to help and hope you resolve your issue

---

### Post by cchhrriiss121212 on 2010-06-03
To do what smittie did, go to System>Hardware Drivers and install the recommended driver for your card.

---

### Post by britishfish on 2010-06-03
Thanks both of your for your responses!  I have already looked for the friver...its an Intel G31 Express chipset family...it doesn't seem to have one fo rlinux and the appropriate ones are already installed.

---

### Post by cchhrriiss121212 on 2010-06-03
What is listed in System>Display?

---

### Post by varunendra on 2010-06-03
> **britishfish said:**
> Thanks both of your for your responses!  I have already looked for the friver...its an Intel G31 Express chipset family...it doesn't seem to have one fo rlinux and the appropriate ones are already installed.

Sounds strange to me because I have used 16:9 ratio on G31 chipset. I didn't even have to install any alternate drivers. The only difference is that I used Karmik (Ubuntu 9.10).

---

### Post by britishfish on 2010-06-03
it only says xorg...etc and what version.  It doesn't specifically list my display hardware.  I also have trouble watching HD vids on youtube which is also strange.  

Varunendra:  I'm using Lucid...it worked on Karmic :(

---

### Post by varunendra on 2010-06-03
> **britishfish said:**
> it only says xorg...etc and what version.  It doesn't specifically list my display hardware.  I also have trouble watching HD vids on youtube which is also strange.  

Varunendra:  I'm using Lucid...it worked on Karmic :(

It seems quite certainly to be a driver compatibility issue then. Can you try figuring out the driver used by Karmik then force-install it on Lucid?
If something goes wrong you can always boot with safe graphics mode & uninstall the driver.

---

### Post by britishfish on 2010-06-03
Yeah, could I possibly just install Karmic on a flash drive and boot that way or would I need to full install? ANd idk about force installing LOL....sorry I'm dumb when it comes to linux LOL

---

### Post by britishfish on 2010-06-03
Ok it still isn't working...I booted Karmic and it stuck with the same aspect ration...which it didn't do last time.  I have no idea how I would go about installing the driver since the intel website onyl provides drivers in exe (windows) format...I think.

---

### Post by varunendra on 2010-06-04
Have you got the CD or iso of Karmik that worked earlier? Maybe it is a problem with updated kernel/drivers.
You can try booting off the older CD (with kernel 2.6.31-14-generic, gnome 2.28.1) that you said worked earlier. See if still works.

This was the kernel that I last tried successfully with 16:9 ratio. Currently I don't have a monitor with that aspect ratio.

---

### Post by britishfish on 2010-06-04
I don't have an old Karmic CD...but I do have ubuntu 7. something lol...its old.  do you think it is too old?  OH well just copied it to my flash drive and we will see ...lol

---

### Post by britishfish on 2010-06-04
Apparently I do not have that version :(  eh this is not good.  I wonder why it seems like I am the only one having this problem?

---

### Post by varunendra on 2010-06-05
> **britishfish said:**
> Ok it still isn't working...I booted Karmic and it stuck with the same aspect ration...which it didn't do last time.

> **britishfish said:**
> I don't have an old Karmic CD...but I do have ubuntu 7.

How did you boot Karmik as you said in above post? Is it installed on some other PC, a newer CD or what? What version of kernel is it showing?

If it (Karmik) is installed on some other PC, press & hold 'Shift' key while booting. It'll bring up the Grub2 Menu in which all the older & updated kernels would be listed. You can select any of them to boot.

Please mention if your current monitor is a different one to that you last used with Karmik successfully getting 16:9 aspect ratio.


Edit: You can get Karmik's iso [here]("http://releases.ubuntu.com/9.10/"), but I'm not sure about its kernel or driver versions.

---

### Post by abhisekparichha on 2010-06-05
Download proprietary drivers of ur graphics card.

---

### Post by britishfish on 2010-06-05
I just downloaded it and copied it to my flash drive (Karmic that is).  

@abhisekparichha:  I don't know where to do that.  It says that I have the Xorg driver installed for intel graphics....but under the hardware drivers listing...there is nothing.

---

### Post by tealio on 2010-07-12
I have a similar problem.  I have :

```
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```

I have the recommended nVidia Drivers.  My TV (Vizio 32" 1080p) worked fine in 16:9 under windows with a different nVidia onboard graphics... so i dont think it's the TV.

Under the nVidia X Server Settings, there are a ton of listed resolutions, only one of which is greater than 4:3 ratio.  It seems that it may be slightly lower than 16:9 because it doesn't quite fit on the screen.  

16:9 = 1.777 ...
the only wide resolution available is 1360x768 = 1.7708333 ...

either the ratio is off enough to lose the edges, or it's too wide for my display. anyway, the edges get cut off... is there another way to force a different ratio that's not available in the dropdown list? would different resolutions be available using DVI or S-Video?

---


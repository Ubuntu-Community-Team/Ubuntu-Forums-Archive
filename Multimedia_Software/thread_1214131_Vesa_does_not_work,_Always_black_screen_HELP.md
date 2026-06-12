---
title: "Vesa does not work, Always black screen HELP"
date: 2009-07-15
forum: Multimedia Software
---

### Post by zonemikel on 2009-07-15
Hello everyone, please help me with this. I hate using windows, ubuntu is a wonderfull product and i have nothing but good things to say about it. I have learned about xconfig and stuff, and have already searched everywhere. I have taken the time to write this in detail, please read it once over before replying. Sorry for the lack of printouts, i cant get gui on my ubuntu partition so unless i log in and save the output to a file then boot windows i cant really do printouts. But if anyone requests printouts i will do just that.
 
[B]
Abstract[/B]
Just upgraded to 9.04 and everything was working ok, except my video card drivers. I had a ATI x1550. I tried to install the proprietary drivers and screwed up something. So i started in recovery mode and tried the fixX thing and restarted. I still got a black screen or sometimes garbled colored screen. I know it has froze because i cant shutdown or change to another terminal. I blamed it on my ATI video card and ordered a Nvidia 8300GS, so please forget the ATI card it is no longer a issue. 

**The Problem**
Every time i restart my computer and go into ubuntu i see the ubuntu progress bar then where the login screen should be it is either black or garbled colors, sometimes flashing colors. The only way to turn off the computer is holding down the power button till it turns off, this makes me think it is compleatly frozen. 

Ctrl-alt-f2, ctrl-alt-backspack, alt-printscreen-k, ctrl-alt-del none of those work.

**Attempts at Fixing**
I have logged in in the root console and tried the xfix option, it didnt do anything. I have also logged in as root and edited the /etc/X11/xorg.conf, it is the default one the driver is listed as vesa. I tried making some .so's executable in the .../modules/drivers file, like vesa_drv.so etc.
[B]
What I think is wrong[/B]
Whatever it is it is my fault. It was working with the default drivers after i upgraded to 9.04 so i know it can work. I was reading texts on how to install drivers and such and i made and edited files, i think thats what messed it up. The thing is i dont remember all the stuff i edited, i remember one site had me doing all this stuff and im sure thats what messed it up, but i cant find that site again. The default configuration that was running after upgrading from intrepid to jaunty was working. 
[B]
My Hardware[/B]
os          : Ubuntu Jaunty 9.04 x64
Vid Card : Nvidia 8300GS (now) just installed it today, before it was ATI x1550
dual core intel processor

**Other stuff that might help**
When everything was working my grub menu used to show 2 different kernels and their recovery modes. After restarting a bunch of times it only shows one kernel could it be a hard disk problem ? 

I tried installing the proprietary drivers for the ati x1550 before and edited some files and made some new ones as instructed by a webpage i think that messed stuff up. 

[B]What I think i need 
[/B]Please give me instructions on how to uninstall and reinstall the gui "x" portion of the ubuntu operating system. I think if i reinstalled it would wipe out all the messed up files and go back to default, I think that would make it work. 


THANK YOU !
Thanks for your help, I hope I get some. I have tons of programs installed and several different accounts set up just right and i dont want to have to start from scratch again. :p

---

### Post by zonemikel on 2009-07-15
AWESOME, fix'd it. 

I was downloading the nvidia driver for windows, so i went ahead and downloaded it for linux also. Then I went into ubuntu recovery mode and navigated to my windows drive via the cli. Then i copied the driver over to my ubuntu drive and ran it. 

After it installed it worked great !! So i guess it fixed whatever i messed up. In the end buying a nvidia card was still the solution to my problems. 

thanks anyway, hope this helps somone.

---


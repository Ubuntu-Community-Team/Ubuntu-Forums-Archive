---
title: "Jetway J7F2 (VIA CN700 Graphics Driver)"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by Cas07 on 2006-08-23
Just purchased a jetway j7f2 1.5ghz motherboard thats based on the VIA EN15000 with a CN700 chipset. I installed Xubuntu 6.06 and everything was fine except that i needed graphics drivers so i downloaded the drivers from viaareana.com (Linux-FBDev-kernel-src_20050726) and followed instructions in readme. 

all went ok after gettin some missing packages and correct directories. i built the modules, fbcon and viafb resulting in files fbcon.ko and viafb.ko in the /lib/modules/.../video  directory

i was then instructed to do a 'modprobe viafb' then a 'mobprobe fbcon'. however nothing happened other than returning to a prompt. 

but the following was found in /var/log/messages

> Aug 23 23:59:58 stewie kernel: [17196446.392000] viafb: no version for "struct_module" found: kernel tainted.
Aug 23 23:59:58 stewie kernel: [17196446.392000] VIA Graphics Intergration Chipset framebuffer 0.9 initializing


im out of my depth now and not sure how to proceed so i turn to the forum gurus for help

---

### Post by Cas07 on 2006-08-24
found a reference on google that suggests i may have built against wrong kernel source, ill double check and do it again with a fresh source download

---

### Post by Cas07 on 2006-08-24
i actually have the correct source for my kernel but the via drivers were quite old so i tried latest versions from source folder on viaarena but this time did not even get an error in the logs! 
i can only imagine that theres something more to it than using modprobe. 

but i have got it working with openchrome drivers and was totally painless thanks to this webpage with exact details for an ubuntu install

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

after this i now have accelerated 2d drivers installed

my only question is what funtionallity does this have (or not have) compared to Via's driver.

---

### Post by kmori on 2006-08-30
> **Caos said:**
> i actually have the correct source for my kernel but the via drivers were quite old so i tried latest versions from source folder on viaarena but this time did not even get an error in the logs! 
i can only imagine that theres something more to it than using modprobe. 

but i have got it working with openchrome drivers and was totally painless thanks to this webpage with exact details for an ubuntu install

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

after this i now have accelerated 2d drivers installed

my only question is what funtionallity does this have (or not have) compared to Via's driver.

Chaos,
Did you test your setup with mplayer or xine on HD content yet?  I have the 1.5GHz version of your system and can't get it to decode HD without maxing out hte CPU.](*,)

---

### Post by Cas07 on 2006-09-05
tbh i had to give up after problems with both sound (v low volume) and wifi (belkin usb hell) and installed Win MCE. Still not perfect with MCE and cant use the MCE part for DVD or videos without problems even though its fine in other apps. 

I can test HD content on windows to see the CPU usage but i have another hard driver and i will install ubuntu again this weekend and post results as i do want to get it working with the view of running MythTV

---

### Post by Cas07 on 2006-09-08
Edit: After discovering a hard drive issue where CPU would hit 100% when transfering files, i thought id retest the HD content on the off chance it might work, and to my suprise it played perfect. So ignore my comments below :redface: 
I will try to dl the types listed in the review i read and test them too.

Also found these two links basically saying that HD content is supported by the chipset but drivers are not forthcoming for linux.
[http://www.epiacenter.com/forums/viewtopic.php?t=1675&postdays=0&postorder=asc&start=15](http://www.epiacenter.com/forums/viewtopic.php?t=1675&postdays=0&postorder=asc&start=15)
[http://www.sudhian.com/index.php?/forums/viewthread/91361/](http://www.sudhian.com/index.php?/forums/viewthread/91361/)


i realised when playing an HD vid on windows that its not the cpu but the gpu  that cannot handle HD content. I can get perfect audio but slideshow video. 

i think i read somewhere there is a newer version of via motherboard that will support HD content.

---


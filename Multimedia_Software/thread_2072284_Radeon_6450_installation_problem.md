---
title: "Radeon 6450 installation problem"
date: 2012-10-17
forum: Multimedia Software
---

### Post by ersuforum on 2012-10-17
I'm trying to install an HIS Radeon 6450 graphics card into my 32 bit Ubuntu 12.04 Dell Inspiron 530 system and am having problems.  Upon power-up, the system starts to boot, some text goes across the screen, a light purple background shows for a few seconds followed by garbled video.  After a minute or so, the screen goes black and the monitor goes to sleep. I tried booting from an Ubuntu 12.04 live CD and the results were the same.  Ctrl-alt-F1 doesn't get me to a console so I'm not sure what to do from here.  I was able to get to a grub console through the boot menu but I'm not sure what to do from there either.  Was wondering if video parameters need to be changed to be compatible with my monitor but not sure how to accomplish this from the grub console.  To verify the live cd as good I tried booting an old windows machine with it and that worked fine.

Any help would be much appreciated.

---

### Post by ersuforum on 2012-10-19
I'm still struggling with getting my ubuntu machine video working.  Since my original post, I've tried to modify the boot parameters to get the system to boot into text mode but have been unsuccessful.  The boot command lines I can edit from the boot menu prior to the boot process commencing are as follows:

root (hd0,2)
Kernel /vmlinuz-3.2.0-29 generic root=UUID=2409df43-c026-4b1F-b0d8-1->
initrd /initrd.img-3.2.0-29-generic
quiet

I tried changing quiet to text but it didn't change the end result of the card going into graphics mode and not working.

I'm ready to return the video card and try to rig a new fan on my old card as that was the reason I was replacing it in the first place.  I thought a newer card might improve performance but I can't get it to work.  My only options appear to be to try a different card or repair the old fan.  

Does anyone have a suggestion on a video card that will be less trouble to get working?  I don't need anything real fancy.  Price range under $50. 16 channel PCIe bus, vga/DVI outputs. nvidia or ati? 

Please let me know if I should be posting to a different area of the forum.  Since I didn't receive any responses I'm concerned I may be in the wrong place.

Thanks for any help you can give.

ed

---

### Post by pme 72 on 2012-10-27
That is sad news. No issues yet with my older Radeon HD4550 using the default drivers but I have a 300 watt power supply which meets that cards minimum system requirements. A quick search suggested that the Dell Inspiron 530 system may have a 250 watt PS and the AMD website recommends a minimum 400 watt power supply for that card. Could that be an issue?

There are a couple of posts about 6450's on askubuntu.com. You could try posting your question there too. Wish I could be more help.

---


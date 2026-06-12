---
title: "ati radeon 9500 -&gt; 9700 soft mod &amp; other questions: fglrx"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by Cuppa-Chino on 2005-10-31
Hi all, am a total newbie and have searched the forums to see if this has been covered but did not find it - apologies if i missed it. I am running breezy - just barely at that spent the weekend getting wireless up and now am looking at the next project...

is there a way to soft install the radeon 9700 drivers for my 9500 card (before you ask I have the right PCB layout and the card has worked wonderfully well while softmodded in the Vole's XP) - this would obviously help performance an awful lot

in other threads reference was made fglrx - I have just seen that this an upgrade option in synaptic to the ati driver. shall I run it from synaptic (currently NONE but the linux-restricted-modules-2.6.12-9-386 are installed)?

thanks

---

### Post by Cuppa-Chino on 2005-11-01
managed to get the radeon driver installed - still keen to find out if possible to "*softmod*" the card to get the last for pipes open... 
thanks

also managed to get the softmod working with ChipID

---

### Post by ViGiLnT on 2006-01-05
Sorry for the revive of this thread.

I've got a Saphire ATI Radeon 9500 that in windows using the Omega drivers I'm able to softmod to 9700.

Is there any way of getting the same thing done in linux?

I'm using Breezy. Hope anyone can help me...

---

### Post by stratotak on 2006-01-05
i have a x800pro that i bios flashed to unlock the pipelines to get 16..but im assuming if you use a tweaked  driver to unlock the other pipelines on yours then a linux driver would have to support that..

---

### Post by ViGiLnT on 2006-01-05
My card can be modded by sofware, on windows this is not a problem...

Anyway, just found this forum:
[http://http://www.driverheaven.net/archive/index.php/t-50894.html]("http://http://www.driverheaven.net/archive/index.php/t-50894.html")

How can I do this? Is there a better way?

---

### Post by stratotak on 2006-01-05
just did a little google search..you can alwise try the hardware mod rather then the soft mod way.heres a  page i founf out about it..covers both soft and hard mod..but im pretty sure that unles someone comes out with a linux patch to the driver  it aint going to happen,,,because from what i read..the softmod patches the driver..and you would need a linux patch to the linux driver to do the same thing....

[http://reviews.designtechnica.com/guide13.html](http://reviews.designtechnica.com/guide13.html)

---

### Post by ViGiLnT on 2006-01-05
:\ OK...

Thanks anyway.

---

### Post by Cuppa-Chino on 2006-01-10
I have solved the issue it is here:

[Softmod]("http://ubuntuforums.org/showpost.php?p=541135&postcount=402")

actually easier than in Windows, just force the driver to accept your card as a different Radeon with ChipID and you are done, simple you might have to test several different ones see the instructions linked above

---


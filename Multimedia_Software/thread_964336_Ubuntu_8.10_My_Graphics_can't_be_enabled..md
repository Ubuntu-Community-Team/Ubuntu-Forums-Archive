---
title: "Ubuntu 8.10 My Graphics can't be enabled."
date: 2008-10-30
forum: Multimedia Software
---

### Post by Khuezy on 2008-10-30
i remember doing some 'sudo apt-get nvidia....' to install the graphics card.
When I go into system>admin>hardware driver and try to enable my video card, it says downloading and installing driver....
but is stuck @ 0%

Thanks

---

### Post by Khuezy on 2008-10-30
Hi, I just installed 8.10 and I can't get my Nvidia card to enable, it won't let me enable the card for my compiz.
Anyone know what's wrong?

---

### Post by overdrank on 2008-10-30
Hi and what is the model of the graphics card?
Merged and moved :)

---

### Post by Khuezy on 2008-10-30
nVidia Go 7400 graphics card
now it says it's "in use"
but I still can't get my special effects to work.
I'm installing compiz from the add/remove right now

---

### Post by irishdunn on 2008-10-30
I cant get my GTX260 to work either, I know that the 177 driver doesnt support it. but I cant get the nvidia bin driver installed and working :(

---

### Post by Khuezy on 2008-10-30
okay, my driver still isn't working!!

---

### Post by Bender2k14 on 2008-10-31
I have a 8600 gts, and I got mine working by going to System->Administration->Hardware Drivers.  However, the two options presented to me are the 173 and 177 drivers, so that might not help you.  The 177 driver, which was also recommended, worked.  After activating that driver, I edited the display setting with System->Administration->NVIDIA X Server Settings and then clicked Apply.

---

### Post by Khuezy on 2008-10-31
Okay, I got it to work, but i can't find the compiz program! is it under systems? i don't see it

---

### Post by apoch632 on 2008-11-01
Can someone help
Have a 8600 gts
I tried using system->admin->hardware drivers and to install the 177 driver

When I click activate it just says 0% and does nothing.

Thanks

---

### Post by Manz Luthor on 2008-11-01
Hello guys.
This program may help you installing the proper driver for your graphics card (it worked for me) be it ATI or Nvidia.

--> [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

I used it with Ubuntu 8.04 and it properly installed under "System Tools" and managed to get and install the proper driver for my ATI X700 mobile.

Under 8.10 it installs but you have to run it manually after installation,

(sudo envyng -t)

because I didn't find it were it used to be under 8.04. Last but not least, the "wobbling windows" effect ran slowly, so I decided to go back to 8.04 where it all worked as it did earlier.

Anyway, I was able to turn all the 3D-transparent-rotating-mirroring effects on.

Give it a try.

M

---


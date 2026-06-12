---
title: "Help with installing ATI X1100 video driver on Ubuntu 10.10"
date: 2010-11-23
forum: Multimedia Software
---

### Post by coreymas on 2010-11-23
I am having difficulty installing a ATI video driver for my laptop on Ubuntu 10.10
 
Here are my specs.
 
Ubuntu 10.10 64 bit
Acer Aspire 5100
4GB RAM
Video Card ATI X1100
 
Would someone please be kind enough to post a step by step guide on how to install the best driver for this machine?
 
All attempts so far get me to the point where the Open source packages are installed... but the ATICONFIG command does not see the card (nor is the xconf file found or show up in the etc/x11 directory).
 
Please be very specific with the instructions. I am not afraid to use terminal.
 
Thanks,
 
Corey

---

### Post by Yellow Pasque on 2010-11-23
aticonfig is from the proprietary driver, which doesn't support your card.

Do this: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
Then see: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by coreymas on 2010-11-23
I followed the first link last night right up until the point of the Generate a new config file.
 
When i go to do the backup of said file.. it does not exist on my system (okay i guess)
 
Then i go and do the Generic Config section .. then i get ... cannot find an adapter.
 
When i look in the etc/x11 folder .. i find no config file.
 
So where do i go from there?

---

### Post by Yellow Pasque on 2010-11-23
You don't need an xorg.conf. Just follow directions here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by coreymas on 2010-11-23
Sorry but maybe i am just dense but...

All i see on that page is something called register PPA

I did that following the instructions..

What next?

---

### Post by kanazky on 2010-11-23
Dude install the ATI Catalyst 10 Driver from ATI's website :D Just go download and put your card info in and select linux as OS and they give u a .run file you permit to execute and it will install :D

---

### Post by coreymas on 2010-11-23
> **kanazky said:**
> Dude install the ATI Catalyst 10 Driver from ATI's website :D Just go download and put your card info in and select linux as OS and they give u a .run file you permit to execute and it will install :D

My card is an older card that is not supported by the 10.X catalyst driver set

---

### Post by kanazky on 2010-11-23
Oh did nothing come up to install flgx in the restricted drivers section?

---

### Post by coreymas on 2010-11-23
i dont even have this option in my System menu

Go to the Restricted Drivers Manager (System -> Administration -> Hardware Drivers)

I have no hardware drivers option... never did

---

### Post by Yellow Pasque on 2010-11-23
Yeah, I think you're being dense ;)

---

### Post by coreymas on 2010-11-23
What am i not getting right.. i am new to Ubuntu and I dont have the menu items that i should have nor is it appearing in additional drivers

I installed the packages... what am i supposed to do next... the instructions are not clear for me.

Please help.

---

### Post by Yellow Pasque on 2010-11-23
what instructions are you following?

---

### Post by fixerdave on 2011-04-17
> **Temüjin said:**
> You don't need an xorg.conf. Just follow directions here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Worked great for me... Acer Aspire 5100 laptop with the ATI Radeon Xpress 1100 chipset - running Ubuntu 10.10

Just installed the PPA, ran update, then let the update manager do it's thing.  Didn't even need a restart and Google Earth worked just fine afterwards (near useless screen before).

Thanks for the pointer,

   David...

---


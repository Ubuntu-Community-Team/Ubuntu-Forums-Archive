---
title: "How do I install this new nvidia 7950?"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by saturnine fei on 2006-12-16
After getting help from these forums with installing ubuntu on my dell dimension 8400 with an ATI 300X(?) (or some such desigination/model number) I have taken the advice of several people and purchased an Nvidia card in the 7xxx series. 

My new GeForce 7950 GTOC has arrived and so I cracked the case and took out the old "ATI bugger you special" I had and pluged in the Nifty New Nvidia, turned on the system and all was well for a few seconds... then it made funny text characters on the screen and said something about not being able to start X.  So I held in the power button until the thing turned off.  

I restarted it and pressed f12 and chose to boot in some mode or other.  After lots of fast scrolling messages I saw the request that I enter the root password to get a login, so I did.

I now have an old fashion command prompt (on the console?) and no idea how to go about installing (or for that matter getting) the drivers for this new card.

HELP!  What do I do?  Please use simple language as I am not a computer person, I just have come to hate windows over the years (enough to spend money on a new graphics card before giving up on linux, at any rate).

Thanks in advance

---

### Post by _simon_ on 2006-12-16
Give this a try, from your command prompt:

```

sudo apt-get install nvidia-glx

```

then to configure your xorg.conf

```

sudo nvidia-xconfig

```

---

### Post by saturnine fei on 2006-12-16
Thank you.  So far those two simple commands have worked.  Nvidia cards need those put into their installation doc's

I appriciate the help.

---

### Post by Mike'sHardLinux on 2006-12-16
> **saturnine fei said:**
> Nvidia cards need those put into their installation doc's


Installing these drivers is not the same among the different distros. So they'd have to have a bunch of different instructions, and they'd have to say this works for these distros, and that works for those distros, etc.....

---


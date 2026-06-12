---
title: "ATI TV out and Control Panel"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by Gru001 on 2007-03-04
Hello,

I've been using Ubuntu for few days now and there are only few more things that I need to set up and I have replaced Windows..

First, and most important for me is TV-Out capability. Ubuntu did detect my card which is ATI 8500 LE, however I do not have control panel nor the ability for TV out. Does anyone know if installing the drivers as specified on the following page will install TV out support as well:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Also, do I need to follow Method one or Method two?

Thank you!!

---

### Post by Gru001 on 2007-03-05
Well, it didn't work out well. I followed those steps and ended up with black screen on boot, so basically I couldn't revert back to previous driver.

So I reinstalled Ubuntu and lost everything.

I then tried steps from the official Ubuntu help, and after reading from whoever wrote that document how ATI 'sucks' the same thing happened after following the steps.

Here is the 'official' page: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This is what the problem was I think:

[I]If fglrxinfo gives you the following, your installation is not completed correctly:

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/I]

The above is what I get, so something goes wrong. Their first suggestion is to restart comp, which makes Ubuntu unusable.

I didn't reinstall Ubuntu for the second time as it was 3am, and I needed to work the next day..

Any suggestions on how to properly install ATI Radeon 8500 drivers would be greatly appreciated. I also need to control panel so that I can have TV Out.. Is easyubuntu worth a try?

Thanks!

---

### Post by ikey on 2007-03-06
The binary drivers do not support your card anymore since version 8.30.3. The last version that support your card is 8.28.8. The open source driver does not support tv-out out of the box. There is a solution but then you need to compile the driver yourself using the patch at
[http://www.ece.auckland.ac.nz/~wsun013/tvout/index.html](http://www.ece.auckland.ac.nz/~wsun013/tvout/index.html) .

Another solution, if you are using only the tv-out and not also a monitor, is using the vesa driver. It is a lot slower so it depends on what you want to achieve.

---

### Post by Gru001 on 2007-03-06
Thank you for the reply! I had to reinstall Ubuntu 4 times so far due to messed up driver installations. I have tried easyubuntu, Envy, wiki page and even official ATI drivers. All 4 have caused a black screen on restart, and reinstalling of Ubuntu...

The weird thing is that I was installing 8.28.8 drivers which are supposed to support my R200 chipset (Radeon 8500).

Also, the driver that Ubuntu automatically installs works quite well, and it supports 3D already. The only problem is that it does not have TV-out (I think they should add that, if possible).  I use it to watch dvd's on my TV, as I do not have a DVD player.

Unfortunately I am Linux noob, and I can't follow the instructions from the site you suggested, too complex for me - don't understand 80% of stuff they are talking about :(

I will however try GeForce 4 4200 as I can get it for free. I will try installing drivers through Automatix2 and hope for the best. If even that doesn't resolve my TV-out issue I will have to wait for the next release of Ubuntu and hope that it will address some of the issues with hardware.

Thanks again.

---


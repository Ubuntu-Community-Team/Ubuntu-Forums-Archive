---
title: "graphics help with ati saphhire 4850 1GB gdd3 card"
date: 2009-07-06
forum: Multimedia Software
---

### Post by cosndaws on 2009-07-06
Hi there, im new in the community since i just started using ubuntu, and i just finished building my computer. My setup is as follows.

1. CPU: Phenom X4 9850 2.5 GHZ
2. 4GB (2GBx2) G skill RAM 6400 latency
3. Sata 2 500 GB harddrive 
4. Saphire Ati 4850 (1GB gddr3) graphics card
5. Foxconn 790GX motherboard 

Ok, anyway this is not my first time using computers but it is using ubuntu so please be patient with me :).

My problem has been that I cannot find a driver for my card that will work in ubuntu and that i cannot enable the cool "special effects" that are so sought after in it. does anyone know where or how i can configure it (i know for a fact that it is certified for vista, does that make a difference?).

thanks!

cos

---

### Post by shabazzk on 2009-07-06
Please tell us you have at least tried to download and install the driver from ATi/amd website. I hear if you want decent 3D acceleration, that is the only option.

Current version is 9.6 as of 07/06/2009

---

### Post by cosndaws on 2009-07-07
unfortunately i have and it gets an error while loading the archive.

---

### Post by shabazzk on 2009-07-07
Since you still have NOT said which system you're using here is a clue:

Install ATi driver using Envy-core, does all the hardwork for you:

1. Activate the ATI driver by going to System > Administration > Hardware driver. Select ATi and click activate.

2 Open synaptic package manager and search for envy-core and install it. If you don't see it, then restart your computer and search again.

3. Run envy and uninstall any ati drivers you might have and restart your system.

4. Now use Envy to properly install the Ati drivers for you.

If this does not get the driver installed correctly for you then I don't know what to say, as this is the easiest method for most I think. I personally learned to install them manually by downloading and building the driver. Which you don't even have to do anymore, as long as you have a cart above Radeon 2400. I may even start using Envy myself...Nah :)

---

### Post by markbuntu on 2009-07-10
Envy has never worked for me with ati drivers. It trys to install old drivers that do not work, it often fails to install the kernel modules.....on and on.

The easiest way to install the ati poprietary driver is to download it from ati and then just run the installer.

sudo sh /.ati-driver-installer.......

This will not work if you are using the rt kernel or the 2.6.29 or 2.6.30 kernel but should work just fine for a stock jaunty install. Be sure to read the release and install notes.

---

### Post by shabazzk on 2009-07-11
Well cosndaws has not relayed any info about his which Version OS he's running or the kernel. SO I guess there is no way to truly help him.


markbuntu, When is the last time you tried Envy, and with what video card. 

I have installed all ATi 9.1 - 9.5 drivers with an ATI 2400HD Pro, they have worked each time, and since I wrote down what steps I tried every time I installed, I was able to skip common mistakes on each install. 

My newer system uses the ATi drier 9.6, and the installer natively supports Ubuntu, so I don't need to do it manually anymore. Thanks ATI. 

The ATi 9.6 drivers should install and run smoothly for his setup. Don't know what could be wrong, without more info. Of course he's NOT replied in a while, so maybe he got them working.

---


---
title: "problem with ati radeon 4850"
date: 2010-01-27
forum: Multimedia Software
---

### Post by MagnusTP on 2010-01-27
hello guys i have a little problem with my video card, when i activate it, the skreen just turns black afetr one reboot, and it woud be awesome if some one know the problem and know a selution=)

MagnusTP

---

### Post by MagnusTP on 2010-01-28
anyone know? pritty lame witout it^^

MagnusTP

---

### Post by sports.car.guy on 2010-01-28
I don't want to sound like a jerk here, but, have you set it in your xorg.conf? Or are you just installing it and expecting it to come up and work? You don't give us any information like that. You just go I activate it and get a black screen. That really doesn't help us and you want us to help you.

How can we with vague information like that?

---

### Post by MagnusTP on 2010-01-28
> **sports.car.guy said:**
> How can we with vague information like that?

you can ask:P hehe. yea i just activated the driver-and it got black. im new to ubuntu so if i need to do somthing more tell me?:D

thnx
MagnusTP

---

### Post by sports.car.guy on 2010-01-28
> **MagnusTP said:**
> you can ask:P hehe. yea i just activated the driver-and it got black. im new to ubuntu so if i need to do somthing more tell me?:D

thnx
MagnusTP

I normally don't go with the pre-packaged drivers off the repository. I install the drivers from AMD manually. I have had nothing but issues with the pre-packaged AMD drivers from Ubuntu.

Your best bet is to download the latest drivers from AMD and use them. They give step by step instructions on how to install the drivers and that. It is really not that hard either. Some people will make a package using the installer as well, but then it will use a driver optimized for a previous kernel when the kernel gets updated. I have never been a fan of that.

I would rather re run the driver install with each new kernel myself.

You can try from "safe mode" which when grub is loading press escape to get to:

aticonfig --initial -f

by adding the -f switch it will write a clean, new xorg.conf.

That might solve your problem, but as I said I have had issues with the precompiled ones.

---

### Post by MagnusTP on 2010-01-28
yea, lst time i did download and install and activate the ati driver the whole thingie got black ore are you talking about som other way?

---

### Post by sports.car.guy on 2010-01-28
> **MagnusTP said:**
> yea, lst time i did download and install and activate the ati driver the whole thingie got black ore are you talking about som other way?


Did you download it from the repositories through a package manager, from the icon in the taskbar saying there was a proprietary driver, or go to AMD/ATI's support sight and download a file with the .run extension on it?

It sounds like you either went through the icon in the taskbar or the package manager where you have said activated more then once and the window the taskbar icon has activate all over it in the explanation on it.

If so I have never had luck with those pre-packaged binaries myself.

---

### Post by MagnusTP on 2010-01-28
well now i did go to the software download and found some packages to download. i did that the try to activate the driver( stupid mistake) and now the skree is all black again, anyway to get it back? witout re instaling again? and i need some one to tell me how to do it, im all new to linux so i dont know annything about it

---

### Post by markbuntu on 2010-01-28
WHat do you mean you activated the card?
How exactly did you do that?

---

### Post by MagnusTP on 2010-01-28
system->administrator->hardwaredrives

---

### Post by sports.car.guy on 2010-01-29
> **MagnusTP said:**
> system->administrator->hardwaredrives

Well that is your problem. I have never had any luck using those drivers that are on the repositories. 

Go to the AMD graphics drivers downloads section and download the latest driver. Read the instructions there on how to install the driver it is pretty straight forward and it will fix your problem.

Just follow the instructions.

---

### Post by Yellow Pasque on 2010-01-29
To get your original ATI driver back (and fix your X): [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20Need%20to%20purge%20-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20Need%20to%20purge%20-fglrx)

EDIT: best guide to install proprietary driver: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) Just be sure to download Catalyst 10.1 and not 9.12 (Catalyst 10.1 was released very recently and the guide has not been updated yet)

---

### Post by markbuntu on 2010-01-29
Packaging scripts are broken in the 10.1 driver for karmic but the installer works If you are going to install the 10.1 driver the buildpkg command will not work. There is some people on the phoronix forums who figured out how to get the packages to build. You can find them in this thread here

[http://www.phoronix.com/forums/showthread.php?t=21739](http://www.phoronix.com/forums/showthread.php?t=21739)

---

### Post by MagnusTP on 2010-01-29
well now i have re installed ubuntu(again) and i cant install the driver, i alredy have downloaded it, i just cant install it, it woud be nice if some one coud walk me trew it, im so noob in ubuntu and linux

---

### Post by sports.car.guy on 2010-01-29
> **MagnusTP said:**
> well now i have re installed ubuntu(again) and i cant install the driver, i alredy have downloaded it, i just cant install it, it woud be nice if some one coud walk me trew it, im so noob in ubuntu and linux


The documentation on ATI / AMD's website explains it step by step.

Basically what you need to do is make the installer executable because it is not set to be. Then you can create a package like mentioned by another here.

Personally I stay away from packages on the note of video cards. The problem is the modules for the kernel are compiled for the kernel you have running at the time of creating the package. When you go to a newer kernel you are applying a module compiled on an older one. That can lead to issues.

I personally with each new kernel rerun the installer and set the driver up for that kernel.

If you look at the doccumentation included with the driver on ATI / AMD's website, or even google installing Catalyst Control Center Linux, you will find step by step instructions on installing the drivers.

I can rehash everything which will take me a bit, or you can take a few minutes and google.

---

### Post by MagnusTP on 2010-01-29
if you want to you coud use the remote dectop and ill just look how you do it? cuz i dont have nayting "personal" on the pc yet cuz i want to get it up runing first? we coud just talk on irc and use the remote desctop, if you have time for it

---

### Post by markbuntu on 2010-01-29
> **MagnusTP said:**
> well now i have re installed ubuntu(again) and i cant install the driver, i alredy have downloaded it, i just cant install it, it woud be nice if some one coud walk me trew it, im so noob in ubuntu and linux

Right click on the file and go to properties/permissions and check the box Execute:

Open a terminal and cd to wherever the file is (cd Desktop or whatever) and do

sudo sh ./ati-driver-installer.....(fill this in with the rest)

Just say Ok to everything.
After the installer is finished, in the terminal

sudo aticonfig --initial -f

Then reboot.

You will find the catalyst control center in your menu. Use that to configure the driver.

---

### Post by MagnusTP on 2010-01-29
sh: Can't open ./ati-driver-installer-10-1-x86.x86_64.run

thats what i get after whriting in the sh ./  thingie

---

### Post by markbuntu on 2010-01-29
You need to put sudo before that and you need to be in the directory where that file is. Did you make it executable?

---

### Post by MagnusTP on 2010-01-29
yea i did, ill just copy the file to my desctop can u show me how to write it? ore is it just

cd desctop/ati-driver-installer....?

---

### Post by sports.car.guy on 2010-01-29
You can only do one or the other

sudo sh ati-........

or

sudo ./ati-.......

That is why you are having the error running it. **sh** is actually depreciated and the preferred is ./ for executing scripts. For some reason ATI/AMD is not with the times on that note in the documentation.

---


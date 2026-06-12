---
title: "ati fan problem"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by atra on 2006-06-27
I have an ATI x850XT ([link]("http://www.newegg.com/Product/Product.asp?Item=N82E16814102505")) and sadly, the fan speed is set at 20-30% all the time and doesn't change unless I use a program like ATI Tool. This wasn't a problem back when I used Windows for obvious reasons, but I've run into a bit of trouble finding any info on programs that control fan speed that work with Linux. Basically I'm just wondering is there any program similar to ATI Tool for Linux or is there a way to get ATI Tool to work using Wine or something? 

While I was writing this I figured I would try to get it to work using Wine. I can get it to run, but I get the following message
> The Kernel Mode Driver does not seem to be running

A device driver is required for communication with your video hardware.

If you just upgraded from an older version it may help to uninstall ATITOOL, reboot, then install the new version.
I have also tried to install drivers through Wine but that also didn't work.

Thanks

---

### Post by Dropknee on 2006-08-30
I have a X800 XT PE and have the same exact problem, the fan increase without any 3d aplication, the fan do this all the time and is a big problem for me because I have a Shuttle XPC (SFF) and this behavior is critical for me, this generate a lot of heat. To give a example in Windows my normal temp is about 42-44C in Ubuntu with the latest driver I got over 50-52C and this in this small box is a very high temp. 

 I anyone know a tool to control this under linux pls post.

thx

---

### Post by fraorlando on 2006-09-26
Same here. Using dthe 6.06 built-in fglrx driver for my x800xt. Fan spins like mad. It cannot have anything to do with the fan itself, because in windows or other linux (knoppix live cd) there is no problem, so my conclusion is that it is a driver problem - it is heating the card too much. Also ati users with an radeon 9xxx card might check their cards temperature per hand, for there is no in built fan control on these cards.
Anyone has experience or can provide a solution?

---

### Post by XaTriX on 2008-04-04
I've this problem too!

How to set the gpu's fan speed :( ?!

XaT

---


---
title: "ATI vs Nvidia"
date: 2010-08-23
forum: Multimedia Software
---

### Post by Xenmaster on 2010-08-23
So, I have tried everything I can think of and have read in the launchpad, and everykind of potential tweek I read about included updating to the newest ATI driver via the ATI website (Which I had to roll back to the ubuntu repository version as I lost some capabilities) I have an ATI 3650HD 512MB PCI Express 2.0 and I have an Nvidia FX5200 128MB AGP 8x (Note, this Nvidia FX5200 is in a much older pc also). I am able to get much better results with my old Nividia card which is several generations older and kinda under junker level by todays terms then I am able to get with my ATI card. With my ATI the screen flickers on boot up and has a good amount of flickering and fps problems in games whereas with my old Nvidia I dont have the flickering and I get a higher fps..this doesnt seem to make any sense. I know the ATI drivers are a little behind..but that is a HUGE difference between the potential of those cards. As of the date of this post Ubuntu 10.04 is completely up to date with all the recommended patches. But I still have issues with this card. I have tried both Kubuntu and Ubuntu and have the same issues. I have windows vista on the pc also and the ATI works great compared to the old Nvidia card by leaps, bounds, and the nvidia card doesnt really even compare to the ATI perfomance in windows...so what am I doing wrong in Linux with the ATI setup? Note ( I have also had the same problem with an ATI 9600 128MB vs Nvida GeForce 4 MX 64MB, Had far far better results in old pc with Nvidia) Thanks for your help in advance
P.S. Other then this graphics problem, I LOVE UBUNTU LINUX!!

---

### Post by ajgreeny on 2010-08-23
I fear this is an ATI/driver problem in Linux generally.  There are a few new cards which apparently work brilliantly, but there are a lot of threads in this forum with ATI problems; many, many more than nvidia problems, I think.

Also, unfortunately for me, many older ATI cards are a real problem with the new xserver packages, and my ATI 9200SE will only give me reasonable performance at 16 bit colour, and with a custom xorg.conf (by default there is no xorg.conf for this card).  Until 9.04 the card was terrific in ubuntu, and ran compiz very well; in 9.10 and 10.04 it has been a real pain in the a---.

---

### Post by AKADAP on 2010-08-24
Pros for NVidea:
Their proprietary drivers actually work in linux

Cons for NVidea:
They keep their hardware interface secret, so there is no chance of open source drivers for NVidea.

Pros for ATI:
They publish the hardware interface and open source drivers for their cards.

Cons for ATI:
They are not competent at software.

The open source ATI drivers are better for 2D graphics and video, and worse for 3D graphics than the proprietary ATI drivers. ATI also tends to ignore their older hardware.

---

### Post by repilce on 2010-09-01
As one who just made the change tonight from a 4870 512mb to a GTS250 512MB (which is abit performance decrease card vs card) i can say, go nvidia even though theoretically the card should perform worse, i am getting fantastic frame rate increases under WoW with the GTS250 and i havent even tweaked yet. Pretty much out of the box , although i did run into some install problems, but they were quickly remedied 1 simple search here.

---

### Post by tommcd on 2010-09-01
I have always used nvidia and I never have problems in linux.
AMD / ATI have been opening up the source code for the ATI drivers. So the open source ATI linux drivers should be improving in future linux kernels. For now, though, nvidia has more reliable linux support, even though their driver is a closed source binary blob.
The nouveau open source reverse engineered nvidia driver has been making progress also; so things are slowly improving for open source drivers for both ATI and nvidia.

---


---
title: "Complete ATI Driver Install fail, please help"
date: 2009-08-18
forum: Multimedia Software
---

### Post by ardinal on 2009-08-18
Hi,

I am quite new to using Linux, installed Ubuntu 9.04 a few months ago, and have managed to fix any problems myself, using the helpful advice from people on the net :), mostly from this forum. 
I decided I wanted to play Morrowind.
I had problems getting it to run (installed fine) and wondered if there was something wrong with the 3d drivers for my ATI - Radeon 9550. Yes its an old card, but as I used to run WOW on it fairly smoothly, so I thought Morrowind was worth a try.
I looked for drivers that may need installing using my synaptic package manager. 
Silly me, I thought the xorg-driver-fglrx package looked pretty nifty.
I install, I restart, my comp runs fine until it reaches my desktop, which comes up in a fragmented, pixelated mess of doom. 
I later read that xorg-driver-fglrx may not have been the best for 9000+ series cards.
I have no idea how to remove the fglrx, so that I can just go back to using the 2d drivers.
From the terminal I'm pretty sure I would be able to use
 sudo apt-get remove --purge xorg-driver-fglrx
 sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
 dpkg-reconfigure xserver-xorg

however, I don't know how to or if I can use a terminal in this situation.
I'm really not sure what to do, and would appreciate some suggestions. :confused:

---

### Post by markbuntu on 2009-08-18
What you need to do is reboot and when the grub menu comes up select the recovery kernel. This will get you to a menu with a fix x option. Select that and then continue when it finishes. This should get you to a usable desktop where you can open a terminal and use the commands.

---

### Post by ardinal on 2009-08-18
I appreciate the advice, but I think I may not be following your instructions properly.

When I reboot, to get to grub menu do I press "Esc"?
Because I tried that, and it lists 3 recovery kernels, 3 just kernels, and something else at the bottom, which doesn't really say anything about a kernel.

I enter the first recovery kernel, and a menu comes up.
It has something called "xfix" which mentions "Try to auto repair graphic problems" which I think is the right option. It runs something but then I'm not sure what option to enter.
I ended up hiting "resume normal boot", and I still get the same problem, which I think makes sense because it may not be applying the xfix changes. 

Sorry for not understanding your instructions. Could you please walk me right through it, step by step so I can give it another go? Have I gone to the correct menu?

---

### Post by alphacrucis2 on 2009-08-18
> **ardinal said:**
> Hi,

I am quite new to using Linux, installed Ubuntu 9.04 a few months ago, and have managed to fix any problems myself, using the helpful advice from people on the net :), mostly from this forum. 
I decided I wanted to play Morrowind.
I had problems getting it to run (installed fine) and wondered if there was something wrong with the 3d drivers for my ATI - Radeon 9550. Yes its an old card, but as I used to run WOW on it fairly smoothly, so I thought Morrowind was worth a try.
I looked for drivers that may need installing using my synaptic package manager. 
Silly me, I thought the xorg-driver-fglrx package looked pretty nifty.
I install, I restart, my comp runs fine until it reaches my desktop, which comes up in a fragmented, pixelated mess of doom. 
I later read that xorg-driver-fglrx may not have been the best for 9000+ series cards.
I have no idea how to remove the fglrx, so that I can just go back to using the 2d drivers.
From the terminal I'm pretty sure I would be able to use
 sudo apt-get remove --purge xorg-driver-fglrx
 sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
 dpkg-reconfigure xserver-xorg

however, I don't know how to or if I can use a terminal in this situation.
I'm really not sure what to do, and would appreciate some suggestions. :confused:

Forget fglrx with that card in Jaunty. The proprietary ATI Catalyst driver versions that work in Jaunty (>= Catalyst 9.4) don't support cards using chipsets r300-r500 or older.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

Yes purge the proprietary driver. Boot in recovery mode with networking enabled. You will need the Open source ATI drivers.

---

### Post by alphacrucis2 on 2009-08-18
> **ardinal said:**
> I appreciate the advice, but I think I may not be following your instructions properly.

When I reboot, to get to grub menu do I press "Esc"?
Because I tried that, and it lists 3 recovery kernels, 3 just kernels, and something else at the bottom, which doesn't really say anything about a kernel.

I enter the first recovery kernel, and a menu comes up.
It has something called "xfix" which mentions "Try to auto repair graphic problems" which I think is the right option. It runs something but then I'm not sure what option to enter.
I ended up hiting "resume normal boot", and I still get the same problem, which I think makes sense because it may not be applying the xfix changes. 

Sorry for not understanding your instructions. Could you please walk me right through it, step by step so I can give it another go? Have I gone to the correct menu?

After you select the first recovery kernel and hit enter, the menu that then displays has lots more options - scroll down to see. Select the one that says something like command prompt with networking. You will boot to cli and then you can type in the apt commands.

---

### Post by ardinal on 2009-08-19
> **alphacrucis2 said:**
> After you select the first recovery kernel and hit enter, the menu that then displays has lots more options - scroll down to see. Select the one that says something like command prompt with networking. You will boot to cli and then you can type in the apt commands.

I gave that a go and yes, I'm happy to say it worked. I hit esc when promted, went to the first recovery kernel, pressed enter and found a menu option that said "root from shell with networking" and then I was able to type the apt commands.

Although, I only typed in the first line of the apt commands

sudo apt-get remove --purge xorg-driver-fglrx

and that worked (well at first it flipped out because it couldn't find any drivers)

then I rebooted a couple of times, and then everything was fixed. o.0 Everything came back.

Now I'm not entirely sure what happened...  I think there is a way for me to check my drivers, to see if they are working properly.

I'm just not sure if I should go to the terminal and continue with

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
 dpkg-reconfigure xserver-xorg

I get that its re-installing some drivers, but if everything is working ok. (except Morrowind... but I'm sure I'll deal :P) should I just leave it alone?

While I was looking up how to fix the problem, I did read something about how some proprietary ATI drivers don't not work in Jaunty.

I'm not sure how to go about getting the Open source drivers for ATI. I have a feeling I should just leave my computer alone... and possibly save up and upgrade my card anyways. I've heard Nvidia cards work ok with Jaunty.

What I have learnt from this excercise:

1. I now know how to boot from cli. And uninstall things.
2. I really should read up on packages before I use them.
3. You guys are awesome. Thank you very much. :D

---


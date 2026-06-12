---
title: "Ubuntu &quot;This system does not support OpenGL&quot; Dell n5110"
date: 2012-01-02
forum: Multimedia Software
---

### Post by raven1234 on 2012-01-02
hi, i have a problem with ubuntu 11.10 64bit on a dell n5110 with nvidia gt525 and i5
i can't run stellarium, and some other random games that require 3D graphics (i tried a few to see if they'll run)
- i get the message "This system does not support OpenGL" and nothing else happens.
This has always been the case, these programs have never worked for me as this is the first time i used linux (dual boot with Win7)
When i first installed i tried to fix this but failed (even had to reinstall). Now however i can't even find the complete phrase in the message with google (very few finds, non helpful, if i add my dell model then there are none at all)
I know this dual video card system is problematic for ubuntu but i had hopped some way of fixing this would be developed by now.
-does anyone out there have this model laptop, with this problem and some way of solving it?
i have, as far as i know, the latest drivers for my card, unity 3d is working (can see at startup), and i have tried advice given other posts.
-also, as a side-note, does anyone know why the laptop gets hot even from just booting with linux and doing nothing else? under windows the temp stays a lot lower

thank you if you read this post-zilla and if u can help with either it would make my life a lot easier :p

---

### Post by raven1234 on 2012-01-05
so... either i can't make myself understood or nobody has had this problem? or been able to fix it...

---

### Post by mediantiba on 2012-01-06
I have exactly the same problem and I have no idea how to fix it.

---

### Post by rambod on 2012-01-06
Hey guyz , problem is N5110 has 2 graphic card , 1 is Nvidia gt525 which is great one  and other is Intel as default to process only windows display . So what the problem? Intel is main graphic card so Nvidia is not default one and Ubuntu can not detect it for u , so problem is Linux doesn't have enough tech atm to support to VGA at same time for optimizing ur graphic . Ubuntu only can detect first one which is intel and its only 64MB so its sucks to run High quality 3D environment . if i find any way to fix this i gone tell u [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by alphacrucis2 on 2012-01-06
> **raven1234 said:**
> hi, i have a problem with ubuntu 11.10 64bit on a dell n5110 with nvidia gt525 and i5
i can't run stellarium, and some other random games that require 3D graphics (i tried a few to see if they'll run)
- i get the message "This system does not support OpenGL" and nothing else happens.
This has always been the case, these programs have never worked for me as this is the first time i used linux (dual boot with Win7)
When i first installed i tried to fix this but failed (even had to reinstall). Now however i can't even find the complete phrase in the message with google (very few finds, non helpful, if i add my dell model then there are none at all)
I know this dual video card system is problematic for ubuntu but i had hopped some way of fixing this would be developed by now.
-does anyone out there have this model laptop, with this problem and some way of solving it?
i have, as far as i know, the latest drivers for my card, unity 3d is working (can see at startup), and i have tried advice given other posts.
-also, as a side-note, does anyone know why the laptop gets hot even from just booting with linux and doing nothing else? under windows the temp stays a lot lower

thank you if you read this post-zilla and if u can help with either it would make my life a lot easier :p


Does the BIOS allow you to disable the hybrid graphics so that only the nvidia gpu is seen by the OS? That might be a solution.

---

### Post by raven1234 on 2012-01-07
> **alphacrucis2 said:**
> Does the BIOS allow you to disable the hybrid graphics so that only the nvidia gpu is seen by the OS? That might be a solution.

wouldn't that disable that graphics card for windows as well?

> Hey guyz , problem is N5110 has 2 graphic card , 1 is Nvidia gt525 which  is great one  and other is Intel as default to process only windows  display . So what the problem? Intel is main graphic card so Nvidia is  not default one and Ubuntu can not detect it for u , so problem is Linux  doesn't have enough tech atm to support to VGA at same time for  optimizing ur graphic . Ubuntu only can detect first one which is intel  and its only 64MB so its sucks to run High quality 3D environment .yes i know that it has two graphics cards, i bought the thing;).
i'm not sure about ubuntu not recognizing the nvidia since it does give some options for updating the drivers. however it seems it doesn't use the driver (updated and all...) since in System, there is no driver displayed in the graphics tab (sais unknown).
i guess ubuntu just isn't made to work with this configuration, or there is no compatible driver made for ubuntu. I'm just hoping someone has an idea to handle the heating, without disabling the nvidia card (windows), else i guess it's hopeless, because  nvidia would have released a driver by now if they had intended to, i suppose.
thanks for the reply:) hope u do find a way,  if i find a solution i'll post it

---


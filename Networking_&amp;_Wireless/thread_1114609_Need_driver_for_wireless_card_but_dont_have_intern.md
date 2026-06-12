---
title: "Need driver for wireless card but dont have internet. is windows better?"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by freddie3782 on 2009-04-02
:guitar:
Have a 4 year old dell desktop. I installed ubuntu a while back when windows stoped working. I just bought a wireless card for the desktop. but I have no internet connection. how can I get the driver from the installation disk with out getting on the internet. I do not have a internet connection but my windows laptop gets wireless from the appartment complex and I bought the card for my desktop to use internet on the ubuntu. so its a circle of problem. cant get internet with my wireless card with out a internet connection. can anyone help?

---

### Post by freonchill on 2009-04-02
windows drivers do not work in linux
just as windows drivers do not work in mac os x.

sometimes you can utilize the files included in the driver with something called ndiswrapper (which "wraps" around the windows driver)

what is the new wireless hardware card that you got. it might or might not be supported by linux / ubuntu?

and to answer your topic - "is windows better?"

no, but if you have learned how to use computers via windows then linux is going to be different and you arent going to understand how to do things without learning how to do it differently, think differently.

---

### Post by freddie3782 on 2009-04-03
the card says M5 wireless pc card.
I'm guessing the brand is M5.

How do I use the diswrapper?
Have had other users say the same.
But do I need a internet connection to use 
the diswrapper or is it part of the ubuntu program?

And as for WINDOWS.....

After a few weeks of using linux and reading about it.
I do think WINDOWS is easier to use, pop in the installation 
disk to anything and you have new driver with out no trouble.
But the concept of LINUX is awesome. You use you learn.

WINDOWS is follow the leader.
LINUX is let your imagination guide you.

---

### Post by superprash2003 on 2009-04-03
post output of **lshw -C network** from the terminal

---

### Post by freddie3782 on 2009-04-03
ok superbrash typed in 'lshw -C network' into terminal
and gave me a list of network :0 and network:1, network:0= Eternet Controller, and network:1 = Eternet interface..
Don't know why I did this but this did not make the wireless card work. What next?

Can anyone help?

OH! 
And I also found this in the Installation Guide.

-Realtek RTL8185 54M Wireless LAN Network Adapter-

Need driver for this 

Any other information you need about the adapter 
let me know. Still very new to Linux, and I don't 
want to give up on it. 

Thanks For The communities help.

:guitar:

---


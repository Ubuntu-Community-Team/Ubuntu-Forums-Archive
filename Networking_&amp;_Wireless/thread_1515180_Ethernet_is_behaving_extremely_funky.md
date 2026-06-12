---
title: "Ethernet is behaving extremely funky"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by insecureboy on 2010-06-22
Hi  i am getting really pissed off with my new core i5 system 

I have a gigabyte p55m-ud2 mobo (  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128405](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128405)  ) which's got a Realtek 8111D lan chipset

it connected to my router after fresh install of ubun10 and then i installed MacOSX 10.6.3 and it worked there too then i came back to ubuntu and it didn't work anymore, after several restarts it was still not working until i took out the power cord and mobo battery, and reinstalled them back later which caused ethernet to work once again. 

but then after a while it started not to work anymore, which usually got fixed with a reboot.

now this time i had ethernet working and i just resumed from screensaver and it stopped agian

 there are no green or orange lights flashing at the back and when i take the cable out and reinsert it nothing comes on but with a shutdown they do come on 

i don't have this problem on the other harddisk which now has win7 and i some times manually change the sata cable to boot into windows and use itunes and some other stuff to load music to my iphone. 

I dont like to have dualboot and i dont like to use win7 either i just have it on the other hard disk just in case 

is the manual switching of hard disk causing this to happen?
why do i get it working with restart/shutdown and when i am using it fine it just decides to stop working after a resume from screensaver or sometimes for other reasons
and why does none of this happen on win7

is there a way to reconfigure the ethernet drivers or other stuff without a reboot

i am thinking it might be a problem with network manager or a bug or something   --- network manager is really crappy and i used to use wicd until that started to do funky things ( like not connecting to hidden networks, launchpad Bug #473817  )

---

### Post by Minisupra on 2011-03-07
I had the same problem with same Ethernet-Card.

Solved it with a Hard/Cold-Boot. 
Step 1: Shut Down your computer. 
Step 2: Turn off the Power Switch and unplug the PowerCable. 
Step 3: Wait 4-5 Minutes. 
Step 4: Now plug in your powercable and turn on the witch, Start computer, boot your OS, and I hope your internet will work again mate!

---

### Post by annoyingrob on 2011-03-08
Do the system logs show anything interesting?

---


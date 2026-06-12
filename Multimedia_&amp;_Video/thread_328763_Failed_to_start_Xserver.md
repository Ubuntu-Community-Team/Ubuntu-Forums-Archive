---
title: "Failed to start Xserver"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by kingleer on 2006-12-31
Hello, 

     I am currently trying to install ubuntu 6.10-64bit on my desktop computer. My system specs are: 

processor  amd 3800+ x2 64 
2 pci express video cards 
    1) ATI Radeon
    2) driver cd says Asus
wireless - dwl-g520 
motherboard - A8N-SLI Premium Asus
ram 1 gig ddr 

I install ubuntu using the 64 bit install dvd. 

I get to the white splash screen (on an unrelated note I do hope they fix that bug) 

and then I get this error:  

------------------------------------------------

Failed to start Xserver (your graphical user interface). 
It is likely that it is not set up correctly. 
Would you like to view the Xserver output to diagnose the problem? 

----------------------------------------------------- Xserver output: 

X window system Verison 7.1.1 
Release Date: 12 May 2006 
X Protocal Version 11, Revision 0, Release 7.1.1 
Build Operating system: Linux 2.6.15.7 x86_64 
Current Operating system: Linux hackintosh 2.6.17-10-generic#2 SMP
Frid Oct 13 15:34:39 UTC 2006 x86_64 
Build Date: 07 July 2006 
          Before reporting problems check [http://wiki.x.org](http://wiki.x.org) 
          To make sure that you have the latest verision 
Module Loader present 
Markers: (- -) probed, (* *) from config file, (= =) default setting, 
                (+ +) from command line, (!!) notice, (II) informational,
                (W,W) warning, (EE) error, (NI) not implemented, (??) unknown
                (==) Log file:"/var/log/Xorg.0.log", Time: Mon Jan 1 00:34:36  2007 
                (==) Using, config file."/etc/x11/xorg.conf" 
                (ww) NV: No matching device section for instance (Bus Id PCI: 2:0:0) found. 
(EE) No device detected. 
     Fatal server error 

no screens found 

The xserver is no disabled. 

Restart GDM when it is configured correctly. 

___________________________________________________

If it helps, I checked the URL: [http://wiki.x.org](http://wiki.x.org)  to try and find some more info

In particular here for the "no screens found error" 

[http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28error%29#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed](http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28error%29#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed)

And here, for the No device detected error 

[http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28error%29#head-93b1e0b56f76546d61364f789045e9c745b6cfd4](http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28error%29#head-93b1e0b56f76546d61364f789045e9c745b6cfd4)

I get the something similair  with the 32 bit verision of ubuntu. 
_____________________________________________________

Please note that the computer in question is not yet connected to the internet physically via ethernet. All of my machines connect to my router in the basement with a wireless connection. I have no extra ethernet cable around that I can connect my computer to. 

My skill level with ubuntu: New to ubuntu. I was able to install the 32 bit verision on my laptop, and use ndiswrapper to get my wireless card working. I can now use ubuntu to do basic things and am using ubuntu as a windows replacement (typing this on my ubuntu wireless laptop). I deleted windows from all my machines - I don't dual boot, don't need it, never want to install it again. 
                          
In other words, I'm a noob.  The another linux distro I tried was suse. Chances are I would still be using it now if I had taken the time to learn it.  I've taken the time to learn more about linux now. I'll try anything that is suggested and am not afraid to keep trying until the problem is fixed.  I have no problem with learning new things either. 


_________________________________________________________________ 

On an unrelated note, I sense a lot of pessimism surrounding 64 bit verision of ubuntu. Before leaving windows forever, my operating system was windows xp x64 bit. I installed it with the assumption it would be more secure than 32 bit verision of windows. I had had enough of the 32 bit verision of windows and moved to the 64 bit. It was nothing special - an improvement, but it was almost impossible to find drivers for a lot of my things. A few of my favourite programs simply didn't work. And I noticed that i was still faced with the same old problems. I lost count of how many times I reinstalled it.  And I knew that even if Vista fixed some of those problems it would just be a whole different set of problems. 

I had always known how stable linux was so I made a switch to what I believed to be the easiest linux desktop distro to use(ubuntu).  If I want to play a game badly enough than I'll make a 10 gig partition for windows, but said game is going to be the only thing on it. 

The only reason the majority of users use windows is because its what comes installed on the system they buy, or they don't want to play around with new software. To them an operating system is just a hammer, but there are better hammers out there. Also, everytime you use a new operating system there is a learning phase, and I think I'm pretty fast with ubuntu. And I've noticed that a whole lot of emphasis is being put on making linux easier to use.  The myth that linux is just for texies needs to be thrown out. Then there are people who want nothing to do with computers but have to use them anyway - but why do they hate computers in the first place? 

Just like fire fox killed internet explorer, linux can kill windows. Anyone take a look at internet explorer 7? They tried to copy firefox. Nothing really original. Remember the giants of the past who never changed? Where are they now? When is the last time microsoft has done something 
original?

Linux behind windows in 64 bit desktop computing? In my opinion, no. In fact I did a little research on what the windows release after vista is going to be like (released sometime around 2010-2012- Vienna). Apparently microsoft wants to start with a clean slate and make an operating system that uses unix and emulates older windows programs (this is what vista was originally envisioned as), and a new super fancy gui (but Aero is nothing special). So windows is light years behind Linux. 

Ends rant. I feel the same way I felt when I ditched internet explorer for firefox. 
___________________________________________

Any help or links that you can give me would be appreciated.

---

### Post by tseliot on 2006-12-31
type:
```
sudo nano -w /etc/X11/xorg.conf
```

and comment out (i.e. put a # before) the busid in the Section device of both your cards.

Press CTRL+X to exit (save)


I need to know the models of your 2 graphic cards


EDIT: I have moved this thread to a more appropriate section.

---

### Post by kingleer on 2007-01-07
Sorry for taking so long to reply.  

Okay, I login and type "sudo nano -w /etc/X11/xorg.conf".

But I'm not exactly sure what I'm looking for.  

>>and comment out (i.e. put a # before) the busid in the Section device of both your cards.

Is this it? 

Section "Device" 
                Identifier   "Nvidia Corporation NV44 [GeForce 6200 TurboCache]" 
                Driver        "nv" 
                BusID         "PCI:1:0:0" 
End Section

---

### Post by tseliot on 2007-01-07
> **kingleer said:**
> Is this it? 

Section "Device" 
                Identifier   "Nvidia Corporation NV44 [GeForce 6200 TurboCache]" 
                Driver        "nv" 
                BusID         "PCI:1:0:0" 
End Section
Yes.

Make it look like this:

```
Section "Device" 
                Identifier   "Nvidia Corporation NV44 [GeForce 6200 TurboCache]" 
                Driver        "vesa" 
                #BusID         "PCI:1:0:0" 
End Section
```

then CTRL+X to exit (save)

and type:
```
startx
```

---

### Post by kingleer on 2007-01-08
Yuppie! Yup. That did it. Thanks.  The gui starts no problem.

---

### Post by kingleer on 2007-01-20
Everything works fine now, but when I try to drag a window across the screen there is a lot of lag. 

Is this just a matter of installing a driver?

---


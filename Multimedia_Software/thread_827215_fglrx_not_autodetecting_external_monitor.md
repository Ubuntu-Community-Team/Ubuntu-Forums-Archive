---
title: "fglrx not autodetecting external monitor"
date: 2008-06-12
forum: Multimedia Software
---

### Post by godsbane on 2008-06-12
allow me to preface this with the fact that I am not at home,  and am using my phone to write this.

I have been trying to set up my old laptop as a media center on my lcd tv. my favourite media center program is xbmc as I have been using it for years on my xbox. the linux port doesn't support the ati driver, but after an easy tweak to the source I was able to make it work with the binary driver.
now, with the binary driver, and no changes to my xorg.conf it works perfectly on the laptop display. if I connect the vga cable and let it autodetect the tv, x crashes. if I modify the xorg.conf to use the fglrx driver explicitly, it doesn't crash, but it doesn't detect the lcd properly either. I can use amdcccle to turn on the lcd and turn off the laptop monitor. problem here is that I can only get 1024x768 resolution. it seems that x is ignoring the modeline I set and overriding it with the incorrect autodetected settings.
any ideas are greatly appreciated.
one more thought - the open source driver sets it up perfectly at 1366*768.and I used that with a tool to get a perfect modeline.

---

### Post by bubutuntu on 2008-06-12
The short answer is that Ubuntu just is such an utter crap, it would take hours to make basic things like display to work. In Gibbon I had mostly working X (except screen savers) but since Heron 

it 

    just 

         does 

              not 

                  work.

---

### Post by godsbane on 2008-06-12
actually it's not the fault of ubuntu. if anything it's most likely ati's fault. in fact I curse ati daily. however the point of this thread was to get help, not to hear your misguided opinion about the state of a free os. kthxbai

---

### Post by markbuntu on 2008-06-13
Configuring your ATI driver

FIrst of all, this is for machines using the ati fglrx restricted drivers 8.47.3 and 8.5

Second, you should make changes using ccc, Catalyst Control Center. You can find it in Applications/Other. It is very helpful for setting up your monitor(s). refresh rate, resolution, Big Desktop mode, clone, etc. It will also tell you what monitors are attached and if you have them enabled.

aticonfig is the command used to directly configure the driver.  If your type aticonfig --help you will get a list (incomplete) of options for configuring the driver. 

The actual configuration file for the ati driver cannot be edited by hand. You must use aticonfig to do this.

You can also make changes in your xorg.conf but this will not change the driver configuration unless you tell the driver to load them. For example if you want to make these changes to the ati driver to speed it up and help with compiz and video play you can edit this section of your xorg.conf 

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
EndSection

and then run

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

in a terminal.

You can then look in your Xorg.0.log after you reboot and you will see that the changes have been made.

ATI has made great strides lately in supporting linux users. New drivers are issued about every 3 months with extensive upgrades and fixes. 

The only thing that is lacking is an easily findable guide to using and configuring it.

All I can say is search search search and rtfm rtfm rtfm.

---

### Post by godsbane on 2008-06-13
Hey there mark, thanks for responding. My problem doesn't lie in configuring the driver to work properly, it has to do with the external monitor causing x to crash totally. I verified that it was only this monitor doing it by connecting a different one, and that one working perfectly. Weird thing is, the first monitor works just great with the open source driver, just wish that xbmc worked with it. I am not sure where to head from here. I have done just about everything i can think of. 

If i boot the computer without the monitor, and then connect it later and open up amdcccle and tell it to detect the monitor it does. If i tell it to enable that monitor, boom x crashes. Once again this works fine with a different monitor. This all leads me to believe the problem lies in fglrx not reading the edid properly. Once again, if anyone has any ideas as to why this is happening, i would greatly appreciate hearing them.

Oh also after x crashes it goes into low graphics mode, but the text is so tiny and distorted i can't do anything with it.

---

### Post by markbuntu on 2008-06-14
What does your Xorg.0.log tell you about this monitor?

This could be a problem with x and that particular monitor.

---

### Post by godsbane on 2008-06-14
That is a good question. I will check when i get home later tonight. I hesitate to think it is X's problem specifically, as the open source driver works perfectly with the monitor.

---

### Post by markbuntu on 2008-06-14
What card are you using?
Support for many older cards has been dropped by ATI and using their driver is not a good idea with these cards. The ATI driver is only for cards that the open source driver does not support.

Just this week the open source driver has been updated with accelerated 2D support and other enhancements for a number of ATI cards, check the list.

Bottom line, if the open source driver works for you, use it.

---

### Post by godsbane on 2008-06-14
Yeah it is a supported card.  9700, iirc they dropped support for 9500 and earlier. the problem is that the software I like doesn't support the open source driver. if using it were an option, it would be my first choice.

---

### Post by nemilar on 2011-05-18
Hi, 

I hate to bump such an old thread, but I am having this issue with the fglrx driver and this is the first hit on google.

When I plug in my monitor on the external VGA port, it does not autodetect it.

I've tried plugging in the monitor, logging out, and logging back in, but it is still not seen by either the Gnome "Monitors" utility, or the ATI Catalyst Control Center.

Since this is such an old issue, I'm figuring that perhaps it has been resolved by now, so hopefully someone has an answer.  



00:01.0 VGA compatible controller: ATI Technologies Inc Device 9803


jdeprizi@stardust:~$ modinfo fglrx
filename:       /lib/modules/2.6.38-8-generic/updates/dkms/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
srcversion:     EEC3D3F06B0B31BC528C8D9


Hardware is specifically a Lenovo Thinkpad X120e, running Ubuntu 11.04.

---

### Post by godsbane on 2011-05-19
Hey there, I never did get this issue solved. I ended up deciding to pretty much never buy anything with an ATI card in it again after that experience.

It does, however sound slightly different than your issue. With mine X actually crashed every time that monitor was attached. Yours seems to be not detecting an external monitor at all?

According to the Arch Wiki, the open source driver works flawlessly with that netbook. Have you tried using that instead of the binary driver?

---

### Post by nemilar on 2011-05-19
Thanks for the reply, Godsbane.

I figured the open source drive would work, but I noticed a pretty nice boost performance-wise when I switched to the closed driver, so I was hoping that there was some known solution. 

If I can't get this working in a few days, though, I just might have to switch to the open source driver...

Thanks again for the reply!

---


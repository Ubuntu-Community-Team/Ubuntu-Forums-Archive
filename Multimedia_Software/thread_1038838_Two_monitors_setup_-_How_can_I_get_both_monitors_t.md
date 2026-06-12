---
title: "Two monitors setup - How can I get both monitors to act as an extended screen?"
date: 2009-01-14
forum: Multimedia Software
---

### Post by xtiano77 on 2009-01-14
I just setup Ubuntu 8.04 and I cannot figure out how to setup so both monitors act as one. It is an ATI B2. It came with a installation CD. I don't know about the driver. How can I get it to work? I ordered an Ubuntu book, but it will not be here until the end of the week. Any help will be appreciated. Thanks in advance.

---

### Post by xtiano77 on 2009-01-14
I just setup Ubuntu 8.04 and I cannot figure out how to setup so both monitors act as one. It is an ATI B2. It came with a installation CD. I don't know about the driver. How can I get it to work? I ordered an Ubuntu book, but it will not be here until the end of the week. Any help will be appreciated. Thanks in advance.

---

### Post by overdrank on 2009-01-14
Hi and please do not make multiple threads on the same issue. Threads merged :)
What is the model of the graphics card?
If it is nvidia graphics then you can use the nvidia settings ```
gksu nvidia-settings 
```
If not you may use the command ```
gksu displayconfig-gtk
``` to see if the second monitor is detected.

---

### Post by xtiano77 on 2009-01-14
Visiontek Radeon HD 3650 Video Card - 512MB GDDR2, PCI Express 2.0, CrossFireX Ready, (Dual Link) Dual DVI, HDTV, HDMI Support.

I tried using the private software suggested by the system and it did not work.  Also, one of the screens was acting as if the monitor was too little for the display, so if the mouse got close to the edge of the screen, it would move as if you had a big photograph and you were scrolling to view the whole thing.  I would really like get this going without having to send the video card back and wait for another to come in the mail.  Thanks in advance for your help.

---

### Post by peakshysteria on 2009-01-14
Which OS are you running? 32 bit or 64 bit? Why are you not running 8.10?

Most people having ATI cards have successful runs with these [howtos]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide").

Please tell us how it goes. Good luck.

---

### Post by xtiano77 on 2009-01-14
I am running 32 bit.  I just setup the system yesterday and I didn't have time and or know how to update the OS, but I will today.  Now, if I understand correctly, if I update to 8.10, that should take care of the problem, or should I still run the commands on the "How to" link you sent me?

---

### Post by xtiano77 on 2009-01-14
I was browsing around and I found that ATI does have linux drivers for their video cards.  Are any of those appropriate for the one I have?

---

### Post by markbuntu on 2009-01-14
The ati proprietary driver will work just fine with that card on 8.04 but you must be careful about how you go about installing it. If you have already treid to use the driver offered by hardware manager, you need to remove it completely with the Synaptic Package Manager which is in your system menu.
Make sure your system is fully updated.

Next, download the latest driver from the ati site to your Desktop

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

When it finishes downloading right click on it and choose Properties/Permissions and check the box next to Execute.
Open a terminal and type 

cd Desktop

Then

sudo ./ati-driver-installer-8-12-x86.x86_64.run
type in your password
when the screen opens agree to the license and then choose automatic.
When the installation finishes close the window and reboot. If you do not reboot the new kernel modules will not be installed and the driver will fail.

I am running 32 bit Hardy 8.04 with that driver on my HD3650 and that is how I installed it. This is also how I installed the driver on 64 bit Hardy and 64 bit Intrepid which I also use. I also run 2 monitors on a big desktop which can be set up with the Catalyst Control Center which comes with the driver and will be in your menus somewhere.

If you have any problems come back here and we will try to help you.

---

### Post by xtiano77 on 2009-01-14
I ran the Synaptics program and looked for the ATI Driver, and although it showed it, the system had a message below saying that it was not installed.  I couldn't figure out how to remove it completely so it wouldn't be listed anymore.  I went ahead and downloaded the ATI HD Radeon 3XXX Series to my desktop and typed the commands you told me to. I re-botted the system.  I can hear the loading and even the drum sound made when the log in screen starts, but I cannot see the screen. The display is black with some awkward looking colors on the top, but I cannot make sense of anything on the desktop.  Can this be fixed?

---

### Post by xtiano77 on 2009-01-14
If the issue with the video card is not fixable, do I have to install Ubuntu again?

---

### Post by peakshysteria on 2009-01-15
> **peakshysteria said:**
> Which OS are you running? 32 bit or 64 bit? Why are you not running 8.10?

Most people having ATI cards have successful runs with these [howtos]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide").

Please tell us how it goes. Good luck.

Follow the howto mentioned above. And especially see Markbuntu's advices (he's the one who taught me how to work my way around installing the driver from the ATI site after a long period of standing still without the proper driver and the proper resolution).

My experience so far is that right after a clean install I go for the wiki [howto]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide"). Seems to work every time.

Reinstalling your OS (8.04 or 8.10) will bring you back to the beginning. It might be easier for you than locating your real problem and solve it before trying to install the driver once again. A clean install typically takes about 30 minutes anyway (if you don't need to back up data).

Both methods will learn you something. I guess it's up to you how much and what :)

Tell us how it goes and which solution you went for.

---

### Post by xtiano77 on 2009-01-15
Guys, I just want to say thanks for the generous and sincere efforts to help me.  I solved the problem by upgrading to 8.10 and going to Display and clicking next to the box displayed. The second display showed up and that was it.  Thanks again.

---


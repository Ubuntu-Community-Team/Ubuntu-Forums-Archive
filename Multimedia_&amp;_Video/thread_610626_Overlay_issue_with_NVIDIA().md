---
title: "Overlay issue with NVIDIA(?)"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by MathSWE on 2007-11-12
Hello!

Just got a NVidia 8800GTS card, but there seems to be some issues with it, is it some sort of overlay or compiz related problem?

When I switch users the screen often go completely white, if I enter the password of the user I'm switching to I get logged in again and the screen goes back to normal.

Then there are some graphical artefacts:

img256.imageshack.us/img256/5510/screensg6.png

and this one, that is a bit more annoying:

img265.imageshack.us/img265/5896/skarmbild7106openofficeya0.png


Are these known errors, can I fix this problem? Doesn't seem to be any post about it, though...

Best regards

Mathias

---

### Post by Unterseeboot_234 on 2007-11-12
I found I MUST use the restricted driver. When I was running Feisty I used the Automatix2 install and got the factory nVidia driver with all the options like core temperature monitor, several resolution capabilities. Since I switched to Gutsy, I still have to use the restricted driver, but provided by Ubuntu. I don't have the nVidia interface and all the options. Most of the aritfacts went away, but there is that overlay issue if a video hangs -- like viewing something on youtube or metacafe and the video does not stop and finalize to "done" -- then I get a white box on the display that won't go away without a system reboot.

---

### Post by smithman89 on 2007-11-12
With the Nvidia restricted drivers, im pretty sure that package includes nvidia-settings.  Just type that into the terminal and it will give you a little GUI interface that you can configure your card's settings.  Though i am not sure if you will still get the temperature readout (ive never had a card that has done that for me while using ubuntu).

---

### Post by MathSWE on 2007-11-12
Hmm... I think Im using the restricted drivers (activated through "Proprietary driver" autmatic install)?

nvidia-glx-new 100.14.19+2.6.22.4-14.10

Or should I download drivers from Nvidias homepage and install? Id rather not, Id like to keep this install as "clean" as possible, not fiddling with drivers if it isnt absolutely necessary!

---

### Post by Unterseeboot_234 on 2007-11-12
The Linux driver download from nVidia factory requires a heavy duty mod with the X-server, so that X configures up upon the System boot ... something I could not pull off. Automatix2 did that painlessly. There was another script for the Feisty crowd -- Envy --that was almost just as good but the author warns you, you MUST uninstall his script before upgrading Ubuntu (and, that's NO joke, that nVidia script gums up everything on an OS upgrade).

No, the very best was Automatix2 installing the factory driver. The nVidia GUI was very pretty and offered 3D acceleration and core temperature. The 3D seems to be built in with the nVidia from Ubuntu/Restricted.

follow this link for the Envy script, the discussion is about dual monitors

**[Envy]("http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/")**

Use Synaptic under System ==> Administration ==> Synaptic Package Manager and search for nVidia to stay *buntu, more-or-less, with the restricted driver. The Envy script link above is discussing use of Envy nVidia with Gutsy. I'm using the Synaptic version and wishing I had the factory GUI (but do I REALLY need the know the temperature of the vid card????). The factory/Envy version puts the GUI menu under Applications. The Ubuntu puts the GUI under System ==> Administration.

---

### Post by zinc10 on 2008-05-08
My whitebox is caused by a pop-up in gnome. 

TO fix without rebooting - go to Appearance->visual effect - choose None. Let it drop compiz - then go back to Custom. This effectively restarts compiz - and it seems to fix the issue.

Probably either a Compiz or nvidia (Nvidia's driver) issue.

---


---
title: "Configuring really *really* old hardware"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by blueturtl on 2006-03-09
Ok.

I have this other computer that's basically out of the dark ages:
Pentium 233 MHz CPU, 128 megs of RAM, several HDs, CD-burner etc etc... The thing is, I know Ubuntu can give me a more decent functionality than Windows 95. t's just that the hardware is so dang old. I tested the Breezy Live! CD and it started right up. There are a few problems though:

* The soundcard is not automatically detected. I know for a fact it's the Yamaha OPL3-SAX, a SoundBlaster PRO compatible card. I know the IRQs and DMAs it uses, I just haven't had to configure a soundcard before (under Linux), how do I go about it?

* The 10 Mbit Ethernet card is not detected (it does claim to detect FireWire, which obviously isn't present!)
The ethernet card is an ISA card as well...

* There is a Voodoo2 3D-graphics accelerator card in the machine. Voodoo2s can only accelerate fullscreen graphics AFAIK, so is it really any use? If there are benefits how do I make sure the card is working? Will I be able to run OpenGL apps with it?

* I want to run a window-manager lighter on the resources than Gnome. What should I try and how do I setup?

p.s. I have tried other distros such as Puppy and Damn Small and only DSL managed to boot the system (it didn't have sound either). Is Ubuntu too much for a system this old? The reason(s) I'd like to use Ubuntu are APT, fantastic out-of-the-box support, reliability and security, and finally having to use a single disc.

---

### Post by az on 2006-03-09
[QUOTE=blueturtl]Ok.

I have this other computer that's basically out of the dark ages:
Pentium 233 MHz CPU, 128 megs of RAM, several HDs, CD-burner etc etc... The thing is, I know Ubuntu can give me a more decent functionality than Windows 95. t's just that the hardware is so dang old. I tested the Breezy Live! CD and it started right up. There are a few problems though:

* The soundcard is not automatically detected. I know for a fact it's the Yamaha OPL3-SAX, a SoundBlaster PRO compatible card. I know the IRQs and DMAs it uses, I just haven't had to configure a soundcard before (under Linux), how do I go about it?

* The 10 Mbit Ethernet card is not detected (it does claim to detect FireWire, which obviously isn't present!)
The ethernet card is an ISA card as well...

* There is a Voodoo2 3D-graphics accelerator card in the machine. Voodoo2s can only accelerate fullscreen graphics AFAIK, so is it really any use? If there are benefits how do I make sure the card is working? Will I be able to run OpenGL apps with it?

* I want to run a window-manager lighter on the resources than Gnome. What should I try and how do I setup?

p.s. I have tried other distros such as Puppy and Damn Small and only DSL managed to boot the system (it didn't have sound either). Is Ubuntu too much for a system this old? The reason(s) I'd like to use Ubuntu are APT, fantastic out-of-the-box support, reliability and security, and finally having to use a single disc.[/QUOTE]


If you have the disk space, install the full ubuntu and add xfce of the icewm desktop (install the menu package, too for icewm)

You can log out of your gnome session and start up an icewm session or scfe to see if you like it.

Thry this for your sound card:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

Also, your ethernet card is not loaded for the same reason.  Try modprobing the 3c509 module, or one like it....

sudo modprobe 3c509

Edit:

I am not sure that the vodoo card supports dri which is what you need for hardware acceleration.  So you would not be able to run openGL aps properly.

---


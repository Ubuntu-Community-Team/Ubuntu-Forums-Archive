---
title: "Should I switch to UbuntuStudio?"
date: 2009-04-24
forum: Multimedia Software
---

### Post by Envergure on 2009-04-24
I am thinking of switching from Ubuntu to Ubuntustudio, but I'd like some input first.

Ubuntustudio, if I understand it, is just Ubuntu with GNOME with a different default package list, so all the standard repos are available?

It also has RT-kernel optimized for low-latency audio.  How well does it work out of the box?  I have a problem with Nvidia kernel module failing to load in normal Ubuntu under the RT kernel.

Can I get Scala (the microtonal program, not the language)?  Does Amsynth work?  (Amsynth has not worked on my system since I got Intrepid.)

In Windows Vista, I was surprised to find I could achieve a latency of around 10-20ms  (Vista has a timer-based audio system like Fedora).  Will I be able to get this in Ubuntustudio?


Thanks
-- Chris

---

### Post by snowpine on 2009-04-24
Chris, you can easily convert your existing Ubuntu install to Studio. Simply open the Synaptic Package Manager and install the following packages: linux-rt (the real time kernel) and any applicable packages starting with ubuntustudio (for example, ubuntustudio-audio and ubuntustudio-audio-plugins if you are a music guy; installing all of the ubuntustudio- packages will give you the full Studio suite).

Reboot and you should see the rt kernel in your grub boot menu. If your hardware is not well supported by the rt kernel, you can boot with the generic kernel instead and still use all of the studio applications (they do not depend on the rt kernel). I know some people on these forums actually have pretty good luck with the generic kernel for music production. 

Sorry I can't answer the rest of your questions. :)

---

### Post by logos34 on 2009-04-24
> **Envergure said:**
> I
Ubuntustudio, if I understand it, is just Ubuntu with GNOME with a different default package list, so all the standard repos are available?

It also has RT-kernel optimized for low-latency audio.  How well does it work out of the box?  I have a problem with Nvidia kernel module failing to load in normal Ubuntu under the RT kernel.

yes.

For the linux-rt kernel you'll have to use 8.04 because it doesn't work in Intrepid (and 9.04 isn't out yet--or [maybe it is]("http://ubuntuforums.org/showthread.php?t=1133829"), but what's the state of the kernel?).

Not sure about the apps you mentioned.

For latency and config info, maybe [this page]("https://help.ubuntu.com/community/UbuntuStudioPreparation") will help

---

### Post by cariboo on 2009-04-24
An even easier way to install Ubuntu studio, is to go to synapitc-->Edit-->Mark Packages by Task, and select the parts of Ubuntu Studio from the menu and click apply.

---

### Post by markbuntu on 2009-04-24
Jaunty ubuntustudio is out. A few people are having problems with the rt kernel booting but many more are using it successfully.

---

### Post by Envergure on 2009-04-24
@snowpine:
Will that install all the configuration files I need for audio stuff?  Will the Nvidia drivers work then or will I still get stuck in "low-graphics mode"?

Updating by DC ends up taking a lot of time.  I think I'll just figure out how to get RT Nvidia drivers to work, then play with limits.conf.

---

### Post by markbuntu on 2009-04-24
There is a Ubuntustudio manager gui where you can set the limits.conf now.

---


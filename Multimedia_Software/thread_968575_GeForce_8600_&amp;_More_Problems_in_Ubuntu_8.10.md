---
title: "GeForce 8600 &amp; More Problems in Ubuntu 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by beanpole136 on 2008-11-02
I am running Ubuntu 8.10 in Virtual PC 2007 SP1. For some reason, Ubuntu didn't get any drivers for anything, be it my GeForce 8600 GT graphics card, the volume card, or my monitor. I have to start Ubuntu in low graphics mode every time I log on, the volume doesn't work, and the screen resolution maxes out at 896x600, while my monitor is capable of 1440x900. I have tried modifying xorg.conf and installing Envy but neither seems to help. I am also unable to activate desktop effects, probably due to Ubuntu being in low graphics mode. Please help if you can!

---

### Post by error420 on 2008-11-02
> **beanpole136 said:**
> I am running Ubuntu 8.10 in Virtual PC 2007 SP1. For some reason, Ubuntu didn't get any drivers for anything, be it my GeForce 8600 GT graphics card, the volume card, or my monitor. I have to start Ubuntu in low graphics mode every time I log on, the volume doesn't work, and the screen resolution maxes out at 896x600, while my monitor is capable of 1440x900. I have tried modifying xorg.conf and installing Envy but neither seems to help. I am also unable to activate desktop effects, probably due to Ubuntu being in low graphics mode. Please help if you can!

Edit.....I'm using 8.04......Have not jumped to 8.10 yet due this the possiblility of issues like this. It's a good idea to always wait a few weeks when new releases come out. You might have to download and install the drivers manually.

Maybe you have a bad install because I use envy for my Nvidia 8600 gt and it works great!!! Make sure you are using synaptic package manager to install envy. It works like magic man. Make sure you do a sudo apt-get update to make sure you have the latest headers and such installed before installing envy.

---

### Post by beanpole136 on 2008-11-02
I have just been trying out Ubuntu in Virtual PC 2007, not upgrading my system.

Anyway, I did a sudo apt-get update and used synaptic to install Envy, but it still doesn't work.

---

### Post by error420 on 2008-11-02
> **beanpole136 said:**
> I have just been trying out Ubuntu in Virtual PC 2007, not upgrading my system.

Anyway, I did a sudo apt-get update and used synaptic to install Envy, but it still doesn't work.

I think Virtual PC is your problem. Envy works by detecting your Hardware video card via speaking to it directly and not through third party emulation software. 

Try booting off the live CD and see if you get desktop effects and such.

This will mean testing while not running in a virtual environment. I'm 100% sure this will work and give you even desktop effects with just built in restricted drivers enabled. Running envy in a virtual environment is kind of like playing a windows game that uses direct-X 9 over a remote desktop session or in a virtual machine. It just won't talk to your accelerator hardware directly. 

Then again..this is just my 2 cents. I could be wrong :( . Good luck man.

---

### Post by Vadi on 2008-11-02
Virtual PC is your problem. Very high chances are that it doesn't support and kind of 3d acceleration.

If you'd like to get the fancy desktop effects and nvidia drivers going, you need to install Ubuntu directly. I'd recommend [Wubi]("http://wubi-installer.org/") as it's quite easy to use.

After installation, you'll either be automatically promted to install the drivers, or go to system - administration - hardware drivers

---


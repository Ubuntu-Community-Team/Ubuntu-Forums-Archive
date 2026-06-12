---
title: "How to install ATI open source drivers"
date: 2011-05-23
forum: Multimedia Software
---

### Post by Fabled One on 2011-05-23
As far as I can tell, I have the proprietary AMD drivers installed.

I want to install the open source drivers instead to see if I can get better performance.

According to this [site]("https://help.ubuntu.com/community/RadeonDriver"), I have to install the PPA to my software sources as instructed [here]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty"). I've done that. But how do I actually install the open source drivers?

---

### Post by Fabled One on 2011-06-09
Someone must have installed the open source drivers...

---

### Post by silex89 on 2011-06-09
The ATI open source drivers are installed by default with Xorg, you don't need to do anything (I have an ATI Mobility Radeon HD 4250 and I had to do nothing)


Regards :)

---

### Post by coffeecat on 2011-06-09
As silex89 points out, the open source ATI driver is the default one.

> **Fabled One said:**
> As far as I can tell, I have the proprietary AMD drivers installed.

As far as you can tell? Did you install the proprietary driver either by enabling it in Jockey (Additional Drivers) or downloading and installing the Catalyst package from ATI/AMD? If you didn't then you don't have the proprietary driver. If you are not sure, post the terminal output of:

```
sudo lshw -C display
```> **Fabled One said:**
>  According to this [site]("https://help.ubuntu.com/community/RadeonDriver"), I have to install the PPA to my software sources as instructed [here]("https://launchpad.net/%7Exorg-edgers/+archive/ppa?field.series_filter=natty"). I've done that. But how do I actually install the open source drivers?

Xorg-edgers may not the best first choice for improving performance until we know exactly what driver you are using at the moment.

If you do have the proprietary driver and you want to revert to the open source one, you need to take a number of steps because bits of the proprietary driver and/or its configuration can get left behind interfering with the open source driver. I can give you more details, but let's see what you are using first.

**EDIT**: might be useful to know. Which version of Ubuntu are you running?

---

### Post by Fabled One on 2011-06-09
> **coffeecat said:**
> As silex89 points out, the open source ATI driver is the default one.



As far as you can tell? Did you install the proprietary driver either by enabling it in Jockey (Additional Drivers) or downloading and installing the Catalyst package from ATI/AMD? If you didn't then you don't have the proprietary driver. If you are not sure, post the terminal output of:

```
sudo lshw -C display
```Xorg-edgers may not the best first choice for improving performance until we know exactly what driver you are using at the moment.

If you do have the proprietary driver and you want to revert to the open source one, you need to take a number of steps because bits of the proprietary driver and/or its configuration can get left behind interfering with the open source driver. I can give you more details, but let's see what you are using first.

**EDIT**: might be useful to know. Which version of Ubuntu are you running?

I'm using Ubuntu 11.04.  I downloaded the version 11.5 of proprietary drivers from AMD.  I installed following this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide").  

```
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Radeon HD 5800 Series (Cypress LE)
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:51 memory:d0000000-dfffffff memory:fdec0000-fdedffff ioport:de00(size=256) memory:fde00000-fde1ffff
```

fglrxinfo results in:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series  
OpenGL version string: 4.1.10750 Compatibility Profile Context
```

The reason I said "as far as I know" is because the performance sucks, so I thought it might be because I installed incorrectly.

And now that you say I shouldn't use Xorg-edgers, I have no idea where else the open source drivers are.  I've researching this stuff for 2 months now.

---

### Post by handy on 2011-06-10
Disable Catalyst, remove it, purge it.

Then reboot.

You will get better performance with the Gallium driver stack that you can access via xorg-edgers.

I'd upgrade the kernel too.

There is a how-to in the Ubuntu-Stuff: section of the post here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

In the last two upgrades that I have done (over the last few days), I have got speed increases in 3D. This is a first for at least a couple of months for my HD2600 pro GPU. 

I'm running Arch, & using the -git packages for the kernel & the rest of the driver stack; have been for over 18 months now; seldom a problem in that time. (& I upgrade my system usually every day.) :)

---

### Post by Yellow Pasque on 2011-06-10
Remove Catalyst according to instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
Then, Follow instructions here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Fabled One on 2011-06-10
Handy and Temujin, this is the part I don't get:

```
Then, Follow instructions here: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa").
```

That site just instructs you on how to add a repository. I'm pretty new to linux, but I thought adding a repository just means you can now install stuff through synaptic or apt-get. Where is the instructions on how to actually install the driver after i added the _xorg edgers ppa?_[]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

---

### Post by Fabled One on 2011-06-10
> **handy said:**
> Disable Catalyst, remove it, purge it.
Then reboot.

You will get better performance with the Gallium driver stack that you can access via xorg-edgers.

I tried that, but not even compiz will run.

> **handy said:**
> 
I'd upgrade the kernel too.


I have 2.6.38-8-generic which seems to be one of the newest. I'm afraid to upgrade it because I am sure I will break my system.

---

### Post by Yellow Pasque on 2011-06-10
After you add the repository:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by handy on 2011-06-10
+1 ^

**@Fabled One:** If you had of looked at the *Ubuntu Stuff:* section in the link that I previously provided, you would have seen what you do & in what order to do it. That how-to has been working correctly for well over a year now. So if you can't get compiz functioning with the open-source drivers then I think you aren't following instructions correctly.

It is hard to tell what state your machine is in, as you don't seem to follow the instructions to their conclusion.

You may have some of the old Catalyst stack left in your system? 

If you haven't correctly followed the instructions (possibly for more than one course of action that you thought may solve the problem) you may have therefore created a state of confusion for your system which doesn't know which driver stack its using as its got bits of more than one & not all of any.

If you have managed to clear your system of the Catalyst stack, & you have added the xorg-edgers ppa repo, then inputting the commands that Temüjin gave you above will give you the AMD/ATi open-source Gallium driver stack that is more recent than that found in the Ubuntu repos.

***[edit:]** As far as the kernel versions are concerned, I'm currently using **2.6.39-rc6-ARCH-*54949-g2a9e586-dirty** & it is faultless.

---

### Post by Fabled One on 2011-06-16
> **handy said:**
> +1 ^

**@Fabled One:** If you had of looked at the *Ubuntu Stuff:* section in the link that I previously provided, you would have seen what you do & in what order to do it.

I did follow those steps, but my previous response was according to this:[INDENT]                     Originally Posted by **handy**                 
                 Disable Catalyst, remove it, purge it.
Then reboot.

You will get better performance with the Gallium driver stack that you can access via xorg-edgers.
[/INDENT]I simply tried removing the drivers. That didn't work.

*Then* I said* "I tried that, but not even compiz will run.*" 

> **handy said:**
> 
That how-to has been working correctly for well over a year now. So if  you can't get compiz functioning with the open-source drivers then I  think you aren't following instructions correctly.


*Then *I followed the Ubuntu Stuff link to the letter. It at least got Compiz working, but I am unable to even start any games. Getting games to run is why I'm looking good for good performance.

> **handy said:**
> 
It is hard to tell what state your machine is in, as you don't seem to follow the instructions to their conclusion.


I happened to be following instructions in the order I received them in this thread. And then, per comment, I followed all instructions in order.

> **handy said:**
> 
You may have some of the old Catalyst stack left in your system? 

No, I removed them according to the instructions in [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver").

> **handy said:**
> 
If you haven't correctly followed the instructions (possibly for more than one course of action that you thought may solve the problem) you may have therefore created a state of confusion for your system which doesn't know which driver stack its using as its got bits of more than one & not all of any.

This could be the case. I'm new to linux which is why I need help in the forums. All I can do is follow what I see online, which is what I've been trying. I don't want to try messing around and breaking my install again.

> **handy said:**
> 
***[edit:]** As far as the kernel versions are concerned, I'm currently using **2.6.39-rc6-ARCH-*****54949-g2a9e586-dirty** & it is faultless.

I installed 2.6.39-020639rc4-generic and it gave me a firmware error:
Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169

I can still boot and log in, but I can't even install the AMD drivers because that also gives me the same error when I try (Yes, I uninstalled the open source drivers according  with:
```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists) sudo apt-get remove --purge fglrx* sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
```(I don't expect help for the kernel in this thread as it is unrelated)

Thanks for the help so far.

---

### Post by Fabled One on 2011-06-16
> **Temüjin said:**
> After you add the repository:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Thanks, I didn't know those commands actually installed programs.

(this part of the tutorial threw me off:
```
Step 3: Now, as a one-off, you should tell your system       to pull down the latest list of software from each archive it knows       about, including the PPA you just added:     
             sudo apt-get update     
             **Now you're ready to start installing software from the PPA!     **

```
It made it sound like more steps were needed.
)

---


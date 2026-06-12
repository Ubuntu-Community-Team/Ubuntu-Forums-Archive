---
title: "Intel i855 graphics help"
date: 2010-11-13
forum: Multimedia Software
---

### Post by markoid63 on 2010-11-13
I am running Ubuntu 10.10 and am trying to enable my Intel i855 graphics chipset without much luck. I have found various articles that have helped but am stuck at one point. It says "To enable the Intel driver you need to create a file called /var/log/xorg.conf" Being a newbie, I am a little confused as to how to go about this. Any help would be greatly appreciated.  :confused:

---

### Post by Anthony25 on 2010-11-28
Hi,
I am running on ubuntu 10.10 on my laptop with the chipset intel 855GM  too. I have found a "solution" (because it doesn't fix all bugs) that is  to install a different kernel that the official'.

Download files on this address : [http://people.canonical.com/~ogasawara/lp614176/i386/]("http://people.canonical.com/%7Eogasawara/lp614176/i386/")
and put them in the same folder (for example in the folder "Linux" in your home).

Then you open the terminal, and you type :

**cd /home/(the_user_name)/Linux       **(You go in the folder where you have put your files, here it's an example that I have took)
[B]sudo dpkg -i *.deb
  
[/B]It's installing the kernel.

Then you have to modify the configuration of Xorg :
In the terminal you type :

[B]sudo gedit /etc/X11/xorg.conf
  
[/B]And you paste this :
[I]

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"[/I] [I]
        Identifier      "Configured Monitor"
EndSection

Section "Screen"[/I] [I]
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection  [/I]


Save and reboot.
In grub boot on the kernel 2.6.35-22.32+lp614176

If you want to delete the official kernel you have to uninstall the package "linux".

**Don't do updates for your kernel, because it will reinstall the official kernel.**


PS : sorry for my bad english, I am french :wink:

---


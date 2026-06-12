---
title: "nVidia driver breaks X in post-8.04"
date: 2009-10-29
forum: Multimedia Software
---

### Post by mysticofjesus on 2009-10-29
Hello all,

I've been having some issues getting the recent versions of Ubuntu (8.10 and 9.04, x86 and x64) working with the nVidia drivers (173, 180, and 185). After I install the drivers or upgrade from 8.04, the X server will not start.

Once or twice I went to low graphics mode, several times I got a command prompt, usually the startup ceased at "checking battery state". A lot of times I saw an error about my bios not commuicating ACPI objects (I think) in a way that Linux understands. I tried a bios update, to no avail.

I'm currently running 8.04, which works pretty much flawlessly. I would like to upgrade to 9.10, but I'm not convinced that it will survive the nVidia drivers. I actually just downloaded 9.10, and will try installing it on a USB drive. I'll let you know if that somehow works.

If it matters, I have an Asrock motherboard with the nVidia 780a chipset, an AMD Athlon x2 7750 BE, and two 8800GTX. I don't need SLI on my Linux partition, as one of those cards is absurd for anything I do on Linux.

Does anyone have any insight into this issue?

---

### Post by SeaDeep on 2009-10-29
I have just today installed Ubuntu 9.10. This is on a system that has been running Hardy Heron for quite some time just fine.

Graphics Card = nVidia GeForce 7900 GS

If I recall correctly, on Hardy Heron I just loaded the accelerated drivers through the hardware acceleration driver tool.

On 9.10, doing the same install path (using the recommend "183" driver set), then rebooting, I get the Ubuntu icon in the middle of the screen, then screen goes black, then prints "trying 1583x768 Failed", then "trying 1024xx768", then it prints out the logon for command prompt with the screen flashing wildly, typing is mostly impossible, and the disk light is flashing. I have to just power cycle.

Next I tried a more manual approach, downloading the appropriate driver from the nVidia website and installing that using same technique I have used for a long time on an old laptop which has always worked.

However, I got exactly the same results... black flashing screen at logon prompt.

From other posts I have read just now, it seems some similar results are rather common.

Ideas?
Thanks.

---

### Post by Turtle.net on 2009-10-30
I didn't solved the actual problem but you can access the graphical interface using the nv driver instead of the nvidia one.
Look [here]("http://ubuntuforums.org/showpost.php?p=8198195&postcount=9")

---

### Post by SeaDeep on 2009-10-31
I have my case working now (mysticofjesus - not sure if this fixes your issue, but if so, please mark this as SOLVED).

I am not sure exactly what step solved my issue, but I assume it was stopping gdm properly. In any case, here is what I did:

1) freshly install KK (9.10)
2) Obtain latest nVidia drivers (for my nVidia GeForce 7900 GS, it was: [NVIDIA-Linux-x86-190.42-pkg1.run]
3) I installed dependencies (not sure if required, but probably so):
  sudo apt-get install build-essential pkg-config xserver-xorg-dev
4) hit [cntrl-alt-F2], and login at text screen
5) stop gdm (this is a new thing I did):
  sudo service gdm stop
6) install the drivers (go to the directory where they are):
  sudo sh NVIDIA-Linux-x86-190.42-pkg1.run
7) Follow prompts to install. Also, at end, say YES to modify xorg.conf
8) Finish up with :   sudo reboot

When it boots up, all is working. You can verify by running glxinfo in a terminal, or run glxgears and note the high frame rates.

---


---
title: "ubuntu 8.04 virtual machine resolution problems"
date: 2008-05-19
forum: Multimedia Software
---

### Post by leemajors on 2008-05-19
hi there,

first time caller, long time listener... :D

on the weekend i installed virtualbox and made a new virtual machine with a fresh install of ubuntu 8.04 on it.

the window's tiny as it only lets me run 800x600 so i've been trying to figure out what to do to allow me to increase my resolution to something sensible (i've got an ati mobility radeon 9600 video driver on a dell inspipron 8600).

i followed some posts in here and somehow i've ended up with something funny... 

when i logged out after changing some xorg settings it won't boot up into the gui, and instead boots to the shell. 

i'm not sure how to fix things, nor am i sure of how to change my settings to increase my resolution without breaking things :(

any help possible? or am i going to have to reinstall?

---

### Post by mrtomservo on 2008-05-19
Not trying to be preachy, but you should always backup configuration files before you edit them.  But if worse comes to worse and you can't get into the GUI, then you can try running as root or sudo:
```
dpkg-reconfigure xserver-xorg
```

That should reset your xorg.conf.

Regarding VirtualBox and the small screen size, there's a extra you can download for VirtualBox to allow larger screen sizes and some other options.  I believe it's called Guest Additions.  Hope that helps.

---

### Post by leemajors on 2008-05-19
> **mrtomservo said:**
> Not trying to be preachy, but you should always backup configuration files before you edit them.

agreed :) i'm really new to all this, and i'm really just trying to sort stuff out at the moment! but i appreciate being told off, it helps me learn :D

```
dpkg-reconfigure xserver-xorg
```

brilliant, that worked really well! just went through the options and finished it, restarted and it booted back up into the gui.

> there's a extra you can download for VirtualBox to allow larger screen sizes

So it's not a display driver issue? i've been trying hard to figure out how to use the right display driver, at the moment it's only giving me an 800x600 or 640x480 option.

but LOL I just did something stupid -- i tried changing the screen option from the screens and graphics menu and now it's increased the size of the window but the display is completely unviewable. i dunno how to fix that either.

sorry for my noobness.

---

### Post by mrtomservo on 2008-05-19
Sorry I wasn't trying to be a pain, but hey if it help you remember. Gosh knows i've been guilty of doing what you've done, i've no room to judge. :)

Anyway, sorry I misunderstood your question about the resolution... I thought the resolution problem was localized to your Virtualbox setup.  Could you post the results of:
```
lspci 
```

Maybe I can help you install the proper drivers for your display adapter.  I've had plenty of trials working with nVidia's for years, and recently ATI.

---

### Post by leemajors on 2008-05-20
> **mrtomservo said:**
>  
Could you post the results of:
```
lspci 
```


Sure thing:

```
 
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller

```

i've been wandering these forums trying to cobble together a way to sort the display  driver thing. i think i may have used the package manager to get a few proprietary ati things as well as try the native 8.04 drivers, but man, coming to terms with all the lingo is pretty tough so i can't really explain what i've done.

---

### Post by mrtomservo on 2008-05-20
Ok, well it looks like you do indeed need the Guest Additions.  Open up VirtualBox, and run your Ubuntu virtual machine.  Click on *Devices* on the VirtualBox window, and then *Install Guest Additions*.  In the Ubuntu desktop, open up a terminal (Accessories-Terminal) and type:
```
sudo sh /media/cdrom0/VBoxLinuxAdditions.run
```

If it runs ok, the restart the virtual machine and let me know what happens.

---

### Post by leemajors on 2008-05-21
woot! sorry it took a while, i had a bunch of problems actually installing the guest additions -- for some reason the version of vbox i have didn't like me using the method you suggested above for mounting the cd.

instead i had to shut down, completely release and remove the iso and add it again -- only then would ubuntu recognise the disc and i could continue.

and once i'd fixed that -- the window is now a decent size! 

thank you so much, it's been a bit of a mission but you've been really helpful. i'm so glad you found this post :)

---

### Post by mrtomservo on 2008-05-21
No problem at all, i'm really glad I was able to help!  I've only been on these forums for about a month, but I really like it here.  Nice folks.

I'm not quite sure how you do it, but if you can figure it out, wanna mark this as solved?

Enjoy your Ubuntu!

---

### Post by leemajors on 2008-06-07
I know I marked this thread as solved but...

Things have been running nicely for a bit. I'm really starting to enjoy using the VM Ubuntu over Windows, and thought I was getting ready to switch even.

Last night, the updater told me there were some critical updates to install. I reviewed them, and they all looked reasonable (there was about 100 mb in total) and so I just clicked install.

It did its thing, and I carried on using the machine that evening, all fine.

I try and boot up this evening and first I got a "can't detect display drivers, reverting to basic etc etc" message and it booted fine but in the mini-window a la Virtualbox without the guest additions installed.

I restart again and this time it won't even boot up the GUI, it boots me straight to the shell.

I have a feeling the installer downloaded new ATI drivers as part of the package and something has happened during the installation of that to make things poop out, but I wouldn't know where to begin with fixing it.

Any ideas?

---


---
title: "Drivers for an NVIDIA GeForce FX 5200"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by rayofash on 2007-03-05
I get slow downs when Ubuntu tries to do anything graphical (resizing windows, screensavers, games, etc...) . I figure updating the graphics drivers will help.

So I followed the guide here: [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

And I got an error about the drivers in the X Server and the NVIDIA drivers being different versions. What do I do? I'm using Dapper Drake.

---

### Post by Dr. Nick on 2007-03-05
can you post the exact steps and the specific spot the message appears?
 
For me 
sudo apt-get install nvidia-glx 
 
then editing xorg.conf to nvidia from nv has always worked easily

---

### Post by techstop on 2007-03-05
[Automatix]("http://www.getautomatix.com") should install the driver for your card very easily.

---

### Post by rayofash on 2007-03-05
> **Dr. Nick said:**
> can you post the exact steps and the specific spot the message appears?
 
For me 
sudo apt-get install nvidia-glx 
 
then editing xorg.conf to nvidia from nv has always worked easily

I did Method 1: [https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-23d008b049974e62464d0a65108816a3d7bcf198-2](https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-23d008b049974e62464d0a65108816a3d7bcf198-2)

It's basically what you just said.

The error happaned after I reset the x-server.

---

### Post by rajeev1204 on 2007-03-05
hi

type this

sudo dpkg-reconfigure xserver-xorg

Just select nvidia when it prompts u to select driver and the for the rest just press ok - that means just select whatever default option is shown

It will ask u things like bus ID etc - just keep pressing ok

xserver will work ok the next time u boot


regards

rajeev

---

### Post by Dr. Nick on 2007-03-05
If it still gives errors just double check to make sure that you have the proper versions to the "." of the restricted modules that match your running kernel.

---

### Post by rayofash on 2007-03-05
> **Dr. Nick said:**
> If it still gives errors just double check to make sure that you have the proper versions to the "." of the restricted modules that match your running kernel.

How do I do that?

---

### Post by Dr. Nick on 2007-03-05
run 
 
uname -r
 
take a look at that number then open synaptic and ckeck the restricted modules installed version and make sure they match up, might remove any that do not.
 
The nvidia drivers have to be set for each kernel, if you are trying to switch kernels at boot it can cause problems. Once done properly though upgrades should be alright

---

### Post by rajeev1204 on 2007-03-05
yes that s right

for dapper , if u have kernel 2.6.15.27 u need restricted modules with same version.


i believe u need the above version for nvidia drivers.

I am running fine with default nvidia 8776 drivers . Upgrades cause problems and i recomend u stick to it unless an upgrade is offered via synaptic.

Downgrage to older driver .

Also the method u have used is not required at all and too complicated. .just type the command in previous post which is for recofiguring the xserver. .Its pretty simple for nvidia .

Let me outline the steps needed for nvidia.

install from synaptic nvidia -glx

sudo nvidia-glx-config enable ( this will enable the drivers)

sudo gedit /etc/X11/xorg.conf will open the file and then change nv to nvidia.

If u screw up ,this is the code- sudo dpkg-reconfigure xserver-xorg



regards

rajeev

---

### Post by rayofash on 2007-03-05
How do I check what drivers i'm using?

---

### Post by Dr. Nick on 2007-03-05
If you search nvidia-glx in synaptic it should say a version number (not in the package name, in the next colum over)

---

### Post by rayofash on 2007-03-05
When I ran uname -r it came up with 2.6.15-27-386 . I have linux-restricted-modules-2.6.15-27-386, linux-restricted-modules-2.6.15-28-386 and linux-restricted-modules-386 installed. Should I remove linux-restricted-modules-2.6.15-28-386? If I do it will want me to remove linux-restricted-modules-386.

Also I have nvidia-glx 8776 installed.

---

### Post by Dr. Nick on 2007-03-05
You could try removing 28, not totally sure it would work though. Just watch what it removes, it should be safe though

---

### Post by rayofash on 2007-03-05
Moment of truth, i'm going to restart.

Edit: I switched 'nv' to 'nvidia' and it works. I removed linux-restricted-modules-2.6.15-28-386 and linux-restricted-modules-386, and nothing seems to be broken.

Now to test it.

Edit: Dagnabit Conky why are you taking up %100 of my system resources?

Edit: Resizing windows (clicking in the corner and dragging them out) is still slow :(.

---

### Post by Dr. Nick on 2007-03-05
Hmm, if its says nvidia then you are using the 3d drivers, not sure about the persistent jerkyness of windows. Their are a few options to add to the xorg that may help. I dont recall them though
 
search the forums for render acceleration of similar and see if you can locate it

---

### Post by rayofash on 2007-03-05
The jerkiness only happens in fluxbox. But the screensavers run even slower now.

Dagnabit. I'll search for that render acceleration stuff.

---

### Post by rayofash on 2007-03-05
After I restarted my kernel version changed to the 28 stuff. Dagnabit. So I had to reconfigure everything. Anyways, that's working now and I have render acceleration enabled. Everything looks a lot better, but the screensavers run even slower. The jerkiness in fluxbox is a bit better I guess. I'll also check a few games to see how well they run.

Edit: Abuse (sdl) runs a lot better. Now I need something 3D to test it on.

---

### Post by rayofash on 2007-03-05
No help for getting render acceleration to work?

---

### Post by Dr. Nick on 2007-03-05
go ahead and post your /etc/X11/xorg.conf up for others to see. I forgot what all I had in mine when I had nvidia, I have a ati card at the moment which is a huge headache and takes different configuration options then the nvidia, but ill try and find a site to post here with help

---

### Post by Dr. Nick on 2007-03-05
Here is a link and a subsequent link to configure your xorg.conf better

[http://ubuntuforums.org/showthread.php?t=49329&highlight=nvidia+tweak](http://ubuntuforums.org/showthread.php?t=49329&highlight=nvidia+tweak)

i imagine most of this will work on your 5200 even though it was written for a 6xxx card. Just disregard or modify some of the other things like video ram size if yours isn't a 128mb card.

I havent used all them options so I am not sure what does what exactly, but alot is explained

Good Luck

---

### Post by rayofash on 2007-03-12
> **Dr. Nick said:**
> Here is a link and a subsequent link to configure your xorg.conf better

[http://ubuntuforums.org/showthread.php?t=49329&highlight=nvidia+tweak](http://ubuntuforums.org/showthread.php?t=49329&highlight=nvidia+tweak)

i imagine most of this will work on your 5200 even though it was written for a 6xxx card. Just disregard or modify some of the other things like video ram size if yours isn't a 128mb card.

I havent used all them options so I am not sure what does what exactly, but alot is explained

Good Luck

Thank you! Everything runs perfect now!

---


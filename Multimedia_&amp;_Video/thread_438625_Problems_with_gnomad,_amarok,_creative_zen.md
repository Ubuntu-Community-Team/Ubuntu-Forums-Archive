---
title: "Problems with gnomad, amarok, creative zen"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by lunarmelody on 2007-05-09
Hello all,
I have a Creative Zen Xtra mp3 player, and am trying to get it to work with Fiesty.
First I tried installing gnomad2.  It will correctly import the tracks, but then hangs when it tries to load datafiles/playlists.  Running from a terminal yields only the following message:
No MTP devices.
This is a PDE device
Anyone either know how to fix this, or how to stop gnomad from trying to load playlists and datafiles?  
Thank you!

I was having problems with amarok, but now they seem to be ok... still curious about the gnomad problem if anyone knows.

---

### Post by godd4242 on 2007-05-16
> **lunarmelody said:**
> Hello all,
I have a Creative Zen Xtra mp3 player, and am trying to get it to work with Fiesty.
First I tried installing gnomad2.  It will correctly import the tracks, but then hangs when it tries to load datafiles/playlists.  Running from a terminal yields only the following message:
No MTP devices.
This is a PDE device
Anyone either know how to fix this, or how to stop gnomad from trying to load playlists and datafiles?  
Thank you!

I was having problems with amarok, but now they seem to be ok... still curious about the gnomad problem if anyone knows.

Just a quick question, seeing as I have a creative zen as well.

How did you get it to work with Feisty?
I have mine sitting here, but I haven't gotten and new music lately, so i haven't really worried about.

I realize that Amarok has a "detect audio / mp3 device" button, but when I do that it asks for port # etc.

I was wondering if you know what to do?

---

### Post by lunarmelody on 2007-05-17
Yes I can help with that!

Go to Settings -> Configure Amarok -> Media Devices, then click on "Add Device".  Under "Select the plugin to use with this device", select "Creative Nomad Jukebox Media Device", then enter a name for the device.  The mount point field should gray itself out.

Then, connect the jukebox to your computer.  On the main gui, click on the devices tab on the left side.  Just under the menu bar, there should be a "Connect" button.  Click on that for it to detect your player.

To put tracks on it, go to the "Collection" tab, right click on a CD or track, and select "Transfer to media device".  This creates a list of things to transfer, but does not actually do the transferring.  To put them on your jukebox, go back to the devices tab and click "Transfer" (also right below the menu bar).  

I hope this helps you!

---

### Post by godd4242 on 2007-05-17
;_;

/org/freedesktop/Hal/devices/usb_device_41e_413c_01052551EB03931C_if0
camera
USB Interface

false



false
camera://Creative Zen MicroPhoto@[usb:005,002]/
media/gphoto2camera

I thought maybe since it was just the same make it wouldn't have any problems using your method, but that's the return I got.

I tried using the all the other settings while putting the usb: 005,002 bit in for the mount, and trying as mount points both media/gphoto2camera as well as the really really long line of numbers, but still no luck.

Just wondering, are you using KDE? 

Amarok tells me to make sure that Hal Daemons are configured for KDE, so that's why I ask.

---

### Post by JawsThemeSwimming428 on 2008-02-20
Did this ever get solved? I am currently having this issue.

---

### Post by godd4242 on 2008-02-20
> **JawsThemeSwimming428 said:**
> Did this ever get solved? I am currently having this issue.

God you come out of nowhere and this is almost from a year ago now.

No, this never got resolved as far as I am aware. I wouldn't mind it being resolved, but I've tried every music interface possible for lUbuntu and ain't nothing changed.

---

### Post by RedRat on 2008-02-20
> **godd4242 said:**
> God you come out of nowhere and this is almost from a year ago now.

No, this never got resolved as far as I am aware. I wouldn't mind it being resolved, but I've tried every music interface possible for lUbuntu and ain't nothing changed.
________________________________
I just got gnomad2 to work with my Creative Zen Xtra, which is a few years old. The thing is that the older Creative Zen, i.e., mine uses a linux file system called njbfs and you need to install the libraries that will read that file system. I too when I installed gnomad, could not get it to see the files on my Creative Zen. I figure that the installation scripts for gnomad2 are for the newer file systm from micrsoft called MTP--all the newer Zens use this protocol for transfering files. I went back to Synaptic and installed neutrino a separate application that was designed for the older Zens. In so doing it download the correct njb libraries and then Gnomad2 worked just fine. I was able to transfer mp3 files over to the Zen. Gnomad3 allows you to do the reverser also. The trick is getting the right libraries installed. 

Hope this helps.

---

### Post by JawsThemeSwimming428 on 2008-02-21
Just wondering, I am having the same issue, If I get it resolved I will let you know.

---


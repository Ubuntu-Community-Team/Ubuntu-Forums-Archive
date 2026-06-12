---
title: "The uptate that was too much (nvidia downgrade)"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by gerard67 on 2006-05-31
Hello,
Yesturday I upgrade my Dapper system without checking first what packages will be updated. Everything went right but after reboot, nvidia Driver can't launch, the version missmatch thing, just like this thread : [http://www.ubuntuforums.org/showthread.php?t=184303&highlight=nvidia+broke](http://www.ubuntuforums.org/showthread.php?t=184303&highlight=nvidia+broke)

Ok .. I switch back to nv driver so I can check for solutions .. I tried the script provided by tseliot ( [http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html) ) to install a proper version of lastest nvida driver but here comes the second problem of mine, I'm stuck with a 2.6.15.20 kernel, newer version are not able to detect root disk at boot, just like this thread : [http://www.ubuntuforums.org/showthread.php?t=164458&highlight=waiting+root+file+system](http://www.ubuntuforums.org/showthread.php?t=164458&highlight=waiting+root+file+system)
So I start the script with kernel 2.6.15.20 and at some point it tries to install packet linux-header-2.6.15-20-386 wich is not in apt tree anymore .. of course without propers headers, I cant buid driver by hand ..

Last try, I did check synaptics to just downgrade nvidia-glx from 8762 to 8756 but of course, package 8756 was not available. I checked /var/cache/apt/archive to find corresponding .deb but no luck, nothing there too...

My question is quite simple, is there any chance to "downgrade" or where can I find version of packages that are not in package tree anymore ..

Sorry for my poor english, I'm trying to improve it ...
Mathieu

---

### Post by gerard67 on 2006-05-31
at least, is there someone here wo can send me a link to 
nvidia-glx_1.0.8756+2.6.15.10-2_i386.deb
or
linux-header-2.6.15-20-386.deb 

Thanks ...
Mathieu

---

### Post by disturbed1 on 2006-05-31
Those are located on the install cd under /pool/restricted/l/linux-restricted-modules-2.6.15

If you don't have your CD anymore, or don't feel like downloading the image again, I can send you just the .deb file.

---

### Post by siorai on 2006-05-31
I had the same breakage with the update. I tried using tseliot's script, but that didn't work either. It seemed like it did, but when I rebooted, the drivers were messed up again. So I ended up goign the manual route and used method two from here: [HowTo: Latest Nvidia Drivers]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") and it went fine after making sure that all the proper restricted modules and whatnot were installed.

It would be really nice to see them actually fix this. For a user that's not that knowledgable in what could possibly go wrong, this has the potential of making them nuke Ubuntu and go back to Windows.

---

### Post by gerard67 on 2006-05-31
Thanks disturbed1, I did find both package in .iso file and install them, now everything is Ok.
I did also lock kernel package and nvidia-glx to avoid futur upgrades...

Mathieu

---

### Post by disturbed1 on 2006-05-31
Good to here you got it fixed :)

---

### Post by NT4usB on 2006-05-31
Pardon my noobicity if this is the wrong forum.
I'm ~ 2 weeks into Linux after a lifetime of 'Dozing so I'm going the *learn by screwing up* route to learn Linux.
I battled the nvidia driver thing for hours and hours until tseliot's fine skript sorted it for me. (didn't learn anything but at least it's working.)
Now I find I still don't have the correct kernel for my hardware so I'm going to slap the 686-smp kernel on it and expect that nvidia will be jacked again.
Enough babbling... once I get it sorted *(again...)*, how do I _lock_ the kernel so my screwings around won't bork it?

ed: speling

---

### Post by hanzomon4 on 2006-06-01
Just make sure you install the linux restricted modules for the 686 kernel that you install

---

### Post by gwilson on 2006-06-01
I'm not a guru, but you guys might want to verify what kernel version is being loaded by GRUB. My system downloaded the newest kernel (2.6.15-23-) but GRUB continued to load the older kernel (2.6.15-21-) due to the way my system was set up. I don't think the 21 kernel supports the newest version of the nvidia driver. You might want to do a "sudo update-grub" in a terminal window. The system will search out all of the available kernels and operating systems and update your /boot/grub/menu.lst file. It will find the 23 kernel and make it available for you to select when the GRUB menu comes up when you boot the computer. Doing this and selecting the newest kernel 23 solved all of the nvidia problems I had following the most recent update of Dapper.

---

### Post by gerard67 on 2006-06-01
[QUOTE=NT4usB]
Enough babbling... once I get it sorted *(again...)*, how do I _lock_ the kernel so my screwings around won't bork it?
ed: speling[/QUOTE]

I use synaptic to to that, You select the packet you want to lock, then "Packet">"Lock version" (I don't know if translation matches, in french it's "Bloquer la version"). Now whenever there is a more recent version of this packet, update won't install it ... Anyway, I don't now how harmfull it is for the system integrity ..

Mathieu

---

### Post by NT4usB on 2006-06-01
Thanks Mathieu.

---


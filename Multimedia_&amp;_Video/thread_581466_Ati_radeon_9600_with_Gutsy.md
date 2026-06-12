---
title: "Ati radeon 9600 with Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by nixie21 on 2007-10-19
Not the XT...

In 7.04 I used the open source drivers, worked fine, in gutsy it is not working right...

Anyone get it right?

If so, how and what entry did you put in the Xorg.conf?

Thanks

---

### Post by msmith677 on 2007-10-19
I had same problem, 7.04 worked fine, 7.10 not so good.

Looking for the answer as well

---

### Post by nixie21 on 2007-10-19
What is the problem you are having?  Mine is with the display, it is very light, and light fonts are not readable on pages.

---

### Post by nzadLithium on 2007-10-19
Maybe turning monitor brightness down would help?

I don't think you can really just install the previous version. It is not available in any of the gutsy repository's. You would have to go to the xorg website and see if you can find a previous deb or tarball or something. This might end up breaking something else in gutsy so i wouldnt do it.

I would try looking for another solution maybe there's an option you can add to xorg or something?

---

### Post by msmith677 on 2007-10-20
mine keeps jacking up the resolution/screen size. 

and it forgets which video card I have after a reboot...

---

### Post by terminator911 on 2007-10-24
Hello friends,

I have a major problem with a Radeon 9600.

When using the restricted drivers on 7.10 Openoffice won't launch; any of the applications. They simply show a splash screen and then nothing happens. 

Evince Document Viewer actually launches but never opens the document, it just sits there and clocks.

Any idea?

When disabling the restricted drivers everything goes back to normal but I can't play Enemy Territory.

If nothing else, I'm going back to 7.04.

Thanks,

Adonis

---

### Post by herteljt on 2007-10-24
You know what they say misery loves company :)  I had nexuiz working great on 7.04, installed 7.10 and poof video card issues.  I have tried both openGL and restricted drivers, neither seems to work.

---

### Post by herteljt on 2007-10-24
Update
I booted to Ubuntu 7.10, kernel 2.6.17-11-386 and things are working well again.

---

### Post by terminator911 on 2007-10-25
herteljt:

Hey brother, what or how did you go back to that kernel number?


Thanks,

terminator

---

### Post by psel00 on 2007-10-25
I had the same problem with the brightness.
There is a bad solution, by now.
Try to connect your monitor with the VGA plug, not the DVI connection.
This has gone good for me.

---

### Post by mesilliac on 2007-10-25
Hi, I just fixed my mum's computer after something broke when she upgraded to 7.10. So I thought I'd say how I fixed it here in case it helps someone else.

I'd set her computer up to use the restricted drivers with XGL, and desktop effects were all working. After the upgrade heaps of stuff was messed up. I'm not sure exactly what fixed it but here's what I did.

a) **DISABLE the restricted ATI driver** using System > Administration > Restricted Drivers Manager

b) **RECONFIGURE xorg (WARNING: this will replace any custom xorg.conf you have created)**: open a Terminal and type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

c) **RECONFIGURE XGL** (dunno if this did anything but I did it anyway)
```
sudo dpkg-reconfigure -phigh xserver-xgl
```

d) **REENABLE the restricted ATI driver** using System > Administration > Restricted Drivers Manager (this should reinstall the driver and set up xorg to use it)

e) restart the computer

Desktop effects are now working better than in 7.04 :). Screen resolution and everything was auto-detected perfectly. Didn't need to edit xorg.conf at all. Hopefully I haven't missed anything important that I did.

---

### Post by herteljt on 2007-10-25
> **terminator911 said:**
> herteljt:

Hey brother, what or how did you go back to that kernel number?


Thanks,

terminator
I did an upgrade from 7.04 so I have a few other kernel that I have not removed (I found out that this is a safe bet when upgrading).  2.6.17-11-386 was still available on my grub boot screen so I just changed the boot settings.  You should be able install other kernel images by going to Synaptic Package Manager and looking under the base system section or search for linux-kernel.  2.6.17-11-386 should be one of the options.

---


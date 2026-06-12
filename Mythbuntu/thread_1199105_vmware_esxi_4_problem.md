---
title: "vmware esxi 4 problem"
date: 2009-06-28
forum: Mythbuntu
---

### Post by jd896 on 2009-06-28
hi im new to myth tv and mythbuntu and was wanting to run the backend on my hp prol ml115 g5 under esxi4 with a HD homerun so not to have pci issues as i havent yet played with the pci passthrough on esxi4 but i have display problems with the gui backend setup as all i get is different shades of pink boxes but the strange thing is that i have ran the vm locally on my vaio under workstation with the same resorces and it dipslays fine i have even converted it with the stand alone client to my server and i then run it to the same display problems does anybody have any ideas or has anybody managed to get this working as a esxi 4 vm

---

### Post by crez79 on 2009-06-28
> **jd896 said:**
> hi im new to myth tv and mythbuntu and was wanting to run the backend on my hp prol ml115 g5 under esxi4 with a HD homerun so not to have pci issues as i havent yet played with the pci passthrough on esxi4 but i have display problems with the gui backend setup as all i get is different shades of pink boxes but the strange thing is that i have ran the vm locally on my vaio under workstation with the same resorces and it dipslays fine i have even converted it with the stand alone client to my server and i then run it to the same display problems does anybody have any ideas or has anybody managed to get this working as a esxi 4 vm

I recommend punctuation and capitalization because I don't know what you are trying to say. I understand not everybody reads and writes English perfectly, but I don't think this is the issue.

---

### Post by jd896 on 2009-06-28
Sorry I do apologize late night last anyway 



Hi, I&#8217;m new to myth tv and mythbuntu. I was wanting to run the myth backend on my hp prol ml115 g5 under esxi4, with a HD homerun tuner, so not to have pci issues as I haven&#8217;t yet played with the pci pass-through on esxi4. But I seem have display problems with the GUI backend setup as all I get is different sized pink boxes and no way to select and navigate. The strange thing is that I have installed virtually under VMware workstation and it displays fine I have even converted the workstation vim with the stand alone converter client to my server, and I run into the same display problem does anybody have any ideas or has anybody managed to get this working as a esxi 4 vim

hope thats better
 
  i do welcome the help I do feel I should mention not many people appreciate arrogance

---

### Post by Bungo71 on 2009-12-21
I have this problem also.  I want to run the ESXi VM as the myth backend without tuners, and slave backends with tuners.  Don't ask, a complicated living arrangement requires some creative and complicated solutions.

Anyway, without VMWare tools and the video driver that comes with that, I get orange myth-setup screens with no text, but I can see the fields, and with the vmware driver installed from vmware tools, it's pretty much pink with little else.

I suspect it's to do with the lack of Direct Rendering (DRM) in the xorg driver, but how do I get mythtv-setup to render properly without the hardware/driver acceleration?

Running mythbuntu 9.04 i386.

cheers

Bungo

---


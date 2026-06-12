---
title: "Video is breaking in VLC and Movie players in Ubuntu 9.10"
date: 2010-04-09
forum: Multimedia Software
---

### Post by Kanna2412 on 2010-04-09
Hi,

I Installed Vlc player through repositories in Ubuntu 9.10. Audio is playing well, but video is breaking. I checked the same with Movie Player, given with ubuntu, also. Again same problem.

Please help me fix this problem.

Indian.

---

### Post by WinterRain on 2010-04-09
It sounds like a video card problem. Are you using a proprietary driver?

---

### Post by Cabs21 on 2010-04-09
What do you mean breaking?  Does the video not show up?  Does the video or sound pause and skip at times?  Does VLC stop the video and tell you files are broken/corrupt/need repair?  Does this happen in full screen or all the time?  Does sound play but not video??  We need more details to help you.  Please be more specific. Thank you.

---

### Post by Alan James on 2010-04-09
I had this problem for some time when running Ubuntu on my laptop and it was caused by a video card driver problem. For some odd reason I never experienced this problem on openSUSE, however openSUSE is no were near as easy to use as Ubuntu, so I eventually moved over to Windows 7 on my laptop.
 

 What video card do you have?

---

### Post by Mary jones on 2010-04-09
[SIZE=4]Actually,I can't understand what do yu mean exactly,:confused:that is,I don't know what we can use it for,:confused:please let me know some details.I am longing for it.[/SIZE]

---

### Post by Kanna2412 on 2010-04-09
Hi guys! I am sorry for the confusion.

I am using Intel DH55TC mother board with i3 processor. Graphic card is built in motherboard. The details of graphic card as below.
  *-display               
       description: VGA compatible controller
       product: Clarkdale Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:fe000000-fe3fffff memory:d0000000-dfffffff(prefetchable) ioport:f160(size=8)

Earlier I had problem with the motherboard when I installed Ubuntu 9.10. Mouse pointer and keyboard were not working. I contacted Intel support and they gave me a link ([http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)) for graphic drivers. I downloaded the drivers. but I don't know the commands to installed them. I changed a setting in boot options and mouse and keyboard are working fine.

Now I have problem with VLC and Media players. When I play a video, it is pausing and skipping all the time. But audio is playing good.

Do I have to install graphic drivers for Ubuntu 9.10? If so, please let me know the commands.

Thanks for your help.

Indian.

---


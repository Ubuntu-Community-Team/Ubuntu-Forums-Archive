---
title: "Using a laptop as media center"
date: 2009-10-24
forum: Multimedia Software
---

### Post by keymoo on 2009-10-24
Hi there,

I have an old laptop lying around that I want to use as a media center. It's a Toshiba Portege R200 running Ubuntu 9.04 and plays videos fine from my Debian Server.

I have an old 32 inch CRT widescreen TV which has a scart socket on it and I want to connect the laptop to the TV.  I bought a VGA-SCART adapter and plugged it in and in System Preferences->Display clicked on Detect displays. It seemed to detect something but did not recognise it. Also, no picture came up on the screen - does anyone know what resolution to use?

Is there anything else I need to do? Has anyone actually done something like this?

Thanks
keymoo

---

### Post by steefjeqv on 2009-10-24
Hi,

I used to watch TV like this.

I made the vga to scart cable myself, using soldering schemes like this :

[http://www.idiots.org.uk/vga_rgb_scart/index.html]("http://www.idiots.org.uk/vga_rgb_scart/index.html")

As you can see, the above link is particular for the ATI Radeon graphics, which are the easiest to use. In fact, not all graphic chips can do this.

You need to be able to set your pixel clock low (12 MHZ) and output an interlaced image. The Radeon can furthermore do "composite RGB" which simplifies the cable layout.

Greetings,
Steven

---

### Post by keymoo on 2009-10-25
Thanks for the reply. So it's not as simple as just buying a cable and plugging it in and configuring ubuntu?

---

### Post by steefjeqv on 2009-10-29
Hi,

Sorry for the late reply.

The simplicity depends on your graphics chipset.

ATI is the easiest, some Intels work great too but Nvidia needs specific soldering (of the cable) because it can't output composite RGB.

By the way, is your cable RGB or S-video ?

Greetings,
Steven

---


---
title: "Change Video modes? No xorg.conf?"
date: 2010-12-30
forum: Mythbuntu
---

### Post by TheLinuxq on 2010-12-30
Hi, 

I just installed Mythbuntu newest release on the following system:

- Asus Pundit-R
- TT DVB-S 2300 (Full featured)
- DVI out to our LED-TV

It works in 1920x1090 pixels, but watching TV it now fluently and shows diagonal "lines" when things move fast on TV.

I tried the other resolutions, but they won`t work out of the box and I will have to change the settings. Where can I do this?

**There is no xorg.conf?** :mad:

Other question: Can I redirect it to the TV-out of my FF DVB-S card?

Thanks for any hint!

LinuxQ

---

### Post by newlinux on 2010-12-30
What video card do you have? Nvidia cards have their own setup and config utility (nvidia-settings). An xorg.conf file is rarely needed these days, but you can still create one.

---

### Post by Grenage on 2010-12-30
> **TheLinuxq said:**
> Hi, 

I just installed Mythbuntu newest release on the following system:

- Asus Pundit-R
- TT DVB-S 2300 (Full featured)
- DVI out to our LED-TV

It works in 1920x1090 pixels, but watching TV it now fluently and shows diagonal "lines" when things move fast on TV.

I tried the other resolutions, but they won`t work out of the box and I will have to change the settings. Where can I do this?

**There is no xorg.conf?** :mad:

Other question: Can I redirect it to the TV-out of my FF DVB-S card?

Thanks for any hint!

LinuxQ

I haven't used Myth, but do such symptoms not indicate a lack of vertical-sync?

---

### Post by newlinux on 2010-12-30
> **Grenage said:**
> I haven't used Myth, but do such symptoms not indicate a lack of vertical-sync?

yes they do, that's usually the case if this is tearing.

---

### Post by TheLinuxq on 2010-12-30
Hi,

the Asus Pundit-R has an ATI IGP 9100 chipset. TV-Out works in lower resolution but with very bad quality. Thus I would love to use DVI.

Thanks

TheLinuxQ

---

### Post by TheLinuxq on 2010-12-30
My Toshiba 40VL743 accepts only 1080p@50Hz on the HDMI port. All other resolutions Mythbuntu supports out of the box lead to a black screen. Also it should accept the following:

[IMG]http://dl.dropbox.com/u/6259226/Bilder/DVI_Toshiba.jpg[/IMG]

---

### Post by newlinux on 2010-12-30
can't help you much with ATI cards. They are often problematic in Linux for video (not to say you can't get it working right, but I avoid ATI GPUs as much as possible in Linux). Which driver are you using (proprietary or open source)? Maybe try switching drivers.

---

### Post by Grenage on 2010-12-30
I (unfortunately) have an ATI card in my XBMC.  I get black screens or a small section blown to the size of the screen, unless I selected basic shaders.  I also had to enforce V-sync, naturally.

---

### Post by TheLinuxq on 2010-12-30
I use the ati_agp  that was automatically chosen by mythbuntu.

>  I also had to enforce V-sync, naturally.
How do I do this?

How can I setup a xorg.conf with the settings used automatically as a beginning?

---

### Post by Grenage on 2010-12-30
> **TheLinuxq said:**
> I use the ati_agp  that was automatically chosen by mythbuntu.


How do I do this?

How can I setup a xorg.conf with the settings used automatically as a beginning?

Hey again.  Remember, I don't use Myth, but reading below:

[http://www.mythtv.org/wiki/ATI_Proprietary_Driver](http://www.mythtv.org/wiki/ATI_Proprietary_Driver)

There appears to be a section (and command) for enabling v-sync.

---

### Post by TheLinuxq on 2011-01-04
Hi,

ok, I tried the proprietary drivers and they won`t work. As I now found out, the ATI IGP 9100 are not anymore supported anymore in the proprietary drivers (fglrx) :( Thus I am stuck with the open source version.

I would like to change the standard resolutuion of mythbuntu. How can this bi done? I guess via xorg.conf!?

---

### Post by newlinux on 2011-01-04
> **TheLinuxq said:**
> Hi,

ok, I tried the proprietary drivers and they won`t work. As I now found out, the ATI IGP 9100 are not anymore supported anymore in the proprietary drivers (fglrx) :( Thus I am stuck with the open source version.

I would like to change the standard resolutuion of mythbuntu. How can this bi done? I guess via xorg.conf!?

I don't use mythbuntu proper (XFCE by default is the desktop environment) but usually there is an app to change the resolution in the menu. In standard gnome ubuntu it's in Preferences->Monitors. That might work for you. Otherwise you can use xorg.conf to do so.

In mythbuntu-control-centre there is all a launch xorg config option that you might want to try to use to create an appropriate xorg.conf.

---


---
title: "Setting VLC as default Media Player"
date: 2009-09-27
forum: Multimedia Software
---

### Post by buster2209 on 2009-09-27
My OS is Hardy 8.0.3

I have set VLC as my default media when selecting a file via the right click > Open With > Open With Other Application method for all the file types I have on my hard drive but when I open media directly from firefox or preview it within deluge, it uses Totem.

There is nowhere in 'Preferrred Applications' to change the default media player and if I uninstall Totem, I can't open media from firefox (without downloading it to my hard drive first) or watch a preview within deluge.

Can the default player be done via 'Configuration Editor' perhaps?

Any ideas would be helpful!

---

### Post by Vaphell on 2009-09-27
firefox has its own settings, Edit->Preferences->Applications
you can change default actions for filetypes there

i agree it's somewhat broken that FF and few other apps override system settings.

---

### Post by khelben1979 on 2009-09-27
remove this.

---

### Post by u-slayer on 2009-10-27
The easy way:

cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'

---

### Post by vinutux on 2009-10-27
> **u-slayer said:**
> the easy way:

Cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'

+1

---

### Post by birddog165 on 2009-11-03
thank you u-slayer. +1 to you buddy

---

### Post by nss0000 on 2009-11-03
Gents:

Running x32_Jaunty and AMD-965 / MSI_790-gd70 / BFG-9800-gtx+ /Liteon_br.dvd

Good call! Only NV_190.xx & VLC worked for me viewing dvd_movies. My original combo MPLAYER & NV_180.xx produced grey_screen dvd output. Funny ... cause WWW images & FLASH(Adobe not GNASH-yer-teeth)  were fine with the original setup.  

On to 8-Gig Crucial & x64_Jaunty ... and I imagine total confusion and failure waiting around till next April for the next x64_LTS.

Many thanks to the UBUNTU/UBUNTU-forum developers & 'experimenters' who clear paths for us casual nix-lusrs. We may scream at you in frustration , but we know who puts chicken into the pot!

---

### Post by Jugantor on 2010-02-12
> **u-slayer said:**
> The easy way:

cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
  Super !! +1

---

### Post by ptrlow on 2010-06-12
> **u-slayer said:**
> The easy way:

cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
This worked! Thanks!

---

### Post by crazzy8 on 2011-08-24
I had to do sudo cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop' but it worked great! 

Thankx

---

### Post by crazzy8 on 2011-08-24
Another question...why does this work?

---

### Post by radek_42 on 2011-11-07
I seem to have the same annoying bug ... There is also "Control Center > System Info > Default Application" but it does not help.

> **u-slayer said:**
> The easy way:

cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'

This is indeed a simple solution. However, it really should ne necessary for something as simple as setting default application for given files.

Cheers, R>

---

### Post by radek_42 on 2011-11-07
> **crazzy8 said:**
> Another question...why does this work?

The quick fix works, because you are fooling ubuntu into thinking it's running totem ... "totem.desktop" is like an application shortcut and you replace it "vlc.desktop" one.

Of course, you might be breaking other stuff; e.g. I don't think you'll be able to run totem (easily) if you choose so (frankly I never knowingly did).

R>

---

### Post by pazuzuthewise on 2011-11-28
In oneiric ocelot:

The mimetype association can be set by right-clicking inside nautilus a file of the respective type and choosing properties, selecting the desired application and then clicking "set default". 

(I haven't thought of this one and I've panicked when I couldn't find the "set default" button in the "open with" sub-menu)

---


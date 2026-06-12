---
title: "generic video for X possible?"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by eternaluxe on 2007-08-29
I've got Ubuntu 7.04 installed to an external USB hd which I want to use to boot multiple different computers.
Is there a generic xorg.conf that has generic video drivers, etc that any one knows about?  Is this even possible?
How does the installer cd figure our video?  Perhaps I could use that process.
Any help would be greatly appreciated.
-Patrick

---

### Post by w4ett on 2007-08-29
Set your video driver to vesa and resolutions to 800x600 @ 60 Hz and that will be well supported across most cards and monitors.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

---

### Post by eternaluxe on 2007-08-29
Still not working.
If I change the ```
DefaultDepth 24
``` to ```
DefaultDepth 16
``` X will start, but only in vga (640x480), even if this is the only Display in Screen:
```
SubSection "Display"
  Depth 24
  Modes "800x600"
EndSubSection

```

I can live with vga, since this setup is only meant to be bootable usbhd frontend for MondoArchive, but I'm still curious as to why it would behave this way.

---

### Post by w4ett on 2007-08-29
Well...what video cards are you trying to use it on?

---

### Post by eternaluxe on 2007-08-29
Could be anything, hence my desire to have a generic xorg.conf
Everything is 4yrs or newer.  All Dell, mostly optilex, some laptops.
When I boot from an install cd or usb key, X is automagically configured.  Is there a way to duplicate that?

---

### Post by w4ett on 2007-08-29
You could do a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after booting in recovery mode then:

```
startx
```

taking you to a GUI Desktop

I suppose you could write a bootup script to automate the process, but it will still require a manual input from you.

---

### Post by eternaluxe on 2007-08-29
Aw, poot.

---


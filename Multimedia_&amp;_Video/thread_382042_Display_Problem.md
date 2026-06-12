---
title: "Display Problem"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by Raein on 2007-03-11
Hi,

I got problem with my display. Before i install the nvidia driver, i can still set the display to 1240 x 1028. Now that i finished with the installation I can't change my display to 1240 x 1028 in system settings (Monitor & Display, Default: 1024 x 768). But i can change my Display settings in Nvidia X server settings.

Everytime i restart it goes back to the default size of 1024 x 768.

I look at my xorg.conf and it doesn't have 1240 x 1028 display mode, i thought of asking first before i mess it up.

raein

---

### Post by steveneddy on 2007-03-11
I believe that you will have to add the screen resolution that you want X to display to the xorg.conf file. Otherwise it won't know what you want to do.

Example:

Here is a portion of my xorg.conf file -

```
SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800"
```

Although this is only two modes, you will need to add the resolution that you want to each line of the "screen" section of the file. If, for instance, I wanted to have a resolution of 1600x1200, I would add that resolution to every "Display" section in the "Screen" section. 

Make sure you back up the file before changing it, just in case you mistype something. 

I have become accustomed to editing the xorg.conf file in the terminal if x doesn't start by typing:

```
sudo gedit /etc/X11/xorg.conf
```

then to start GDM, you can use the line:

```
sudo /etc/init.d/gdm restart
```

Good luck. Let me know how this works for you.

-SE

---

### Post by Raein on 2007-03-11
thanks :popcorn: 

one more thing, i can't change the refresh rate. The standard refresh rate of my monitor is 60hz but my only option in system settings is 50hz. how do i change it? or is it alright to use 50hz?

---

### Post by pettybone on 2007-03-13
> **steveneddy said:**
> I believe that you will have to add the screen resolution that you want X to display to the xorg.conf file. Otherwise it won't know what you want to do.

Example:

Here is a portion of my xorg.conf file -

```
SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800"
```

Although this is only two modes, you will need to add the resolution that you want to each line of the "screen" section of the file. If, for instance, I wanted to have a resolution of 1600x1200, I would add that resolution to every "Display" section in the "Screen" section. 

Make sure you back up the file before changing it, just in case you mistype something. 

I have become accustomed to editing the xorg.conf file in the terminal if x doesn't start by typing:

```
sudo gedit /etc/X11/xorg.conf
```

then to start GDM, you can use the line:

```
sudo /etc/init.d/gdm restart
```

Good luck. Let me know how this works for you.

-SE Do you know where I can find this file and edit it? WHat will I use to edit it, the text editor?

---

### Post by chewearn on 2007-03-13
> **pettybone said:**
> Do you know where I can find this file and edit it? WHat will I use to edit it, the text editor?

Open a terminal, copy and paste this line:
```
sudo gedit /etc/X11/xorg.conf
```

Once you have edit/save and close gedit, you can use the same terminal:
```
sudo /etc/init.d/gdm restart
```

---

### Post by steveneddy on 2007-03-13
Thank you, AstalaVista

---


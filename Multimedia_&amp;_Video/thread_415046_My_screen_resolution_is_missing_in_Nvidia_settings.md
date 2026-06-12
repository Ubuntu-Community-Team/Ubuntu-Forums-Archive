---
title: "My screen resolution is missing in Nvidia settings"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by zweiundzwei on 2007-04-20
I'm trying to change my screen resolution via the nvidia settings interface or whatever it's called. It works really well, apart from the fact that my screen resolution (1200x1024) isn't listed. Any ideas how to get my proper resolution?

Right now I'm using 1024x768, which seems to work better than all the other resolutions I've tinkered with (1200x960 etc) - those made everything on my screen pretty unreadable.


by the way, I hope this is the right forum to post, the new system is still confusing me.

---

### Post by MaLk0 on 2007-04-20
First make a backup of your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now edit the xorg.conf file with the command

```
sudo gedit /etc/X11/xorg.conf
```

Find the screen section and add your desired resolution to the list, so it looks something like this:
```

SubSection "Display"
		Depth	1
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1200x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection

```

Now save the file and press ctrl+alt+backspace to restart the X server. Your resolution should be correct now.

---

### Post by zweiundzwei on 2007-04-20
Oh, I've already done that, I forgot to mention.

I've also tried the auto-detection thing, but that doesn't work either. I've been having problems with my resolution since Edgy, for some reason.

---

### Post by MaLk0 on 2007-04-20
> **zweiundzwei said:**
> Oh, I've already done that, I forgot to mention.

I've also tried the auto-detection thing, but that doesn't work either. I've been having problems with my resolution since Edgy, for some reason.

Ok, sounds strange... I guess you have tried System->Preferences->Screen Resolution aswell then :p

---

### Post by dabl on 2007-04-20
Possibly the Nvidia driver isn't quite recognizing or understanding your screen correctly (I'm assuming you know for a fact that your screen supports the resolution that you want).  Is the model number of your LCD or CRT or whatever shown correctly on that panel of the Nvidia Xserver Configuration app?  Maybe your screen is the "-XX" model or something slightly different that what it shows.  The Nvidia driver is supposed to offer you all the resolutions and refresh rates that your screen/monitor is capable of using, but of course it is probably not perfect ...

---

### Post by diargasm on 2007-04-20
Same exact problem here.  Everything was fine with 6.10, but feisty fawn has been a mess.

---

### Post by comfortablynumb on 2007-04-20
I am also having the same problem, I've tried all the same steps to no avail

Any other ideas?

---

### Post by whitefort on 2007-04-20
Just adding myself to the list of people with this problem.

Installed Feisty, screen resolution was great.  Installed the Nvidia driver using the new tool, and Yeagh...  800 X 600 is the best I can get now.   The only other choice the screen resolution tool offers me is 640 X 480!!  I've been loving Feisty so far, but this is a nightmare. I could probably stand across the street and still read this screen!

Any solutions would be very welcome!

---

### Post by gionas on 2007-04-20
Had the same problem today after upgrading to Feisty. Solution? Go to the NVidia website:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Download the one that fits your card (I used the Latest Version: 1.0-9755 for a 256 MB GeForce Fx on a 3 yr oldToshiba notebook) to a location on your hard drive, switch to text mode (it won't work in X11), and run the installer. 

In my case, the installer probed the system, looked for ready compiled kernel modules on NVidia's ftp servers, and decided to compile a new one. It took about 5 minute to compile, set up the new module, and rewrite the xorg.conf file. Now I have my native monitor resolution back.

Good luck!

---

### Post by Tulx on 2007-04-21
I got my Feisty Nvidia working with first enabling from Restricted Driver manager (my refresh rate was too low) and then running following command in terminal:

nvidia-settings

Im a noob too so this information might be somehow uncorrect. I hope it helps.

---

### Post by comfortablynumb on 2007-04-21
> **Tulx said:**
> I got my Feisty Nvidia working with first enabling from Restricted Driver manager (my refresh rate was too low) and then running following command in terminal:

nvidia-settings

Im a noob too so this information might be somehow uncorrect. I hope it helps.

I tried nvidia-settings, and it said to use apt-get.... I'm using the restricted driver as I have a an old card (Geforce 2 GTS)

I reinstalled Feisty last night and before enabling the restricted driver I was able to select my Resultion to 1440X900.

I enable the restricted driver and the setting dissapears for 1440x900 in my selectable screen resolutions, yet when I check my x11 conf it's in there. :confused: :confused: 

So for now I'm stuck with 1280X960 and have to scroll my desktop, this sucks...

---

### Post by zweiundzwei on 2007-04-23
> **gionas said:**
> Had the same problem today after upgrading to Feisty. Solution? Go to the NVidia website:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Download the one that fits your card (I used the Latest Version: 1.0-9755 for a 256 MB GeForce Fx on a 3 yr oldToshiba notebook) to a location on your hard drive, switch to text mode (it won't work in X11), and run the installer. 

In my case, the installer probed the system, looked for ready compiled kernel modules on NVidia's ftp servers, and decided to compile a new one. It took about 5 minute to compile, set up the new module, and rewrite the xorg.conf file. Now I have my native monitor resolution back.

Good luck!

I'm back and first thanks to all for the tips.
I found this one in particular helpful because it's something I hadn't tried yet, but I screwed up in the middle. 
It took me a while to figure out how to make the installer work, but then it did and finished successfully. When I tried rebooting though, I got an error message telling me something along the lines of that it could not compile properly after all since I used different versions of (what? kernel-something? I wish I had copied that down) and should re-do it. 
Then, X was broken. I edited xorg.conf in text mode and changed the driver to nv because that works at least somewhat (but makes the middle section of my screen unusable, which is highly annoying) and tried to figure out how to revert all that. Obviously, I didn't manage do to that, which is why I'm here again.
I'm looking for a noob-friendly explaination how to get my native screen resolution back while in text mode, as my screen drives me crazy otherwise. I can supply more information on my screen etc if needed, I just don't know what's necessary to know.

---

### Post by Johnny B on 2007-12-12
I've been having the same problem for the past 3 months. I finially fixed it by looking up the refresh rates (horizsync and vertrefresh) for my specific monitor and changed them in my xorg.conf. nvidia-settings immediately behaved and im breaking out the celebratory shots of whiskey because this was the obstacle that was keeping me tethered to windows xp.

---

### Post by tenzen on 2008-03-20
I had a similar issue to everybody, only I managed to solve mine, so here is my post. 

I am running ubuntu 7.10 with a wide-screen 22" LCD.   My default (clear) resolution is 1680x1050.

This resolution was missing from the list.   I tried to load the restricted drivers for my Nvidia 7600, tried the Nvidia Drivers, tried editing the xorg config files -- no avail.

Finally I dug around and found the issue.. <slap on forehead>

System>Administration>Screens and Graphics

Choose the pull-down for screen and it opened another box "Choose Screen"
Choose LCD Panel 1680x1050
Here is the slap part:  Checked Widescreen Monitor
Clicked OK

BINGO
My resolution appeared in the box.
</slap on forehead>

Hope this helps somebody

Lance

---


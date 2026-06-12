---
title: "gnome color manager w/Ubuntu 10.04"
date: 2010-11-23
forum: Multimedia Software
---

### Post by kolibri on 2010-11-23
Anyone know much about gnome color manager?
(running Ubuntu 10.04, Dell studio laptop w/2nd external monitor)

I needed/need to calibrate my monitors.  I got a spyder3express because the argyll page says that the spyder3 is supported, but I can't get gnome color manager to work with it.  It recognizes that the colorimeter is attached- the create profile for device button is activated, and I get the first device calibration screen that asks me what precision I want to use, but after I select High precision, the screen flashes and then nothing else happens.

So I gave up and installed the provided software with the Spyder3 on my Windows partition, ran it on the laptop screen, and got a .icm color profile, which i copied over to my Ubuntu partition, and made a copy with a .icc extension.
Then I restarted windows, ran Sypder3 on the external monitor, renamed the 2nd profile, and copied it over to my Ubuntu partitition, didn't even need to rename it to .icm

Now gnome color manager is applying those profiles independently to my dual monitors, and they MATCH!  Yeah for gnome manager being able to run each monitor independently.   The test will be in printing, but for now the color looks good.

I'd like to be able to get the Spyder3Express working with gnome manager though.

[I][When I ask gnome color manager to browse for the profile using other profile under the Color profile menu- the gnome screen that comes up is blank.  I have my folder menu on the left, but nothing, no files and no folders in the screen on the right , and cannot browse deeper into the file structure than what is showing up on the left tab.

Anyone got any ideas as to what is going on?  I'd love to get the spyder3express working under Ubuntu, but failing that, I'd at least like to be able to use the profile derived under Windows.][/I] [I]

Ubuntu restart fixed this, so it's resolved, but I can't really say what the issue was.[/I]

Oh, and btw, not a fan of Spyder3 and Colorvision- had to register the instrument online before it would let me use it, in addition to having a serial number on the CD case, considering how often I wipe my windows partition and reinstall, this is going to be a pain in the ***.  I didn't see that part in any of the reviews I read, also, on Windows the software won't let me apply two profiles independently, or name them uniquely from the get-go.

TIA!

---

### Post by lance21broke on 2010-11-23
I have been calibrating my monitor to. But I cant find the right color I want for it to.
Can anyone please help us with this?

---

### Post by llarch on 2010-12-03
i found this to be comprehensive. 

[http://live.gnome.org/GnomeColorManager](http://live.gnome.org/GnomeColorManager)

---


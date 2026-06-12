---
title: "Stop Recording on Startup"
date: 2007-11-18
forum: Mythbuntu
---

### Post by pt123 on 2007-11-18
Is there a setting that will prevent the application from recording what I am watching. 
It slows the computer down and I don't have much space.

Also is it possible to record on an NTFS drive. I changed the recordings folder to one of these drives and mythTV fails to start the tv tuner.

---

### Post by ubnewbie2 on 2007-11-18
> **pt123 said:**
> Is there a setting that will prevent the application from recording what I am watching. 
It slows the computer down and I don't have much space.

Also is it possible to record on an NTFS drive. I changed the recordings folder to one of these drives and mythTV fails to start the tv tuner.

It has to record what you watch on live TV, otherwise you won't be able to pause and rewind etc.  All the recordings are marked to be the first to expire when the HD space is required, so just ignore them.

I would not recommend NTFS.  If you have read/write access it might work, but I suspect performance will be bad.  Use something xfs.

---

### Post by pt123 on 2007-11-19
> **ubnewbie2 said:**
> It has to record what you watch on live TV, otherwise you won't be able to pause and rewind etc.  All the recordings are marked to be the first to expire when the HD space is required, so just ignore them.

I don't want need this feature so there is no way to turn it off?
:(

Or even feature to limit how much it wastes on this.
> 
I would not recommend NTFS.  If you have read/write access it might work, but I suspect performance will be bad.  Use something xfs.
what user needs access given to them? myth or main account?

Edit : got this to work by editing fstab by giving ownership to mythtv

---

### Post by ubnewbie2 on 2007-11-19
> **pt123 said:**
> I don't want need this feature so there is no way to turn it off?
:(

Or even feature to limit how much it wastes on this.


I don't believe so.

---

### Post by s_g_robertson on 2007-11-19
> 
Quote:
Originally Posted by ubnewbie2 View Post
It has to record what you watch on live TV, otherwise you won't be able to pause and rewind etc. All the recordings are marked to be the first to expire when the HD space is required, so just ignore them.


I don't want need this feature so there is no way to turn it off?

Or even feature to limit how much it wastes on this.

It won't waste space on these recordings.  They will be automatically deleted if a new recording needs the space.

---

### Post by superm1 on 2007-11-19
> **pt123 said:**
> I don't want need this feature so there is no way to turn it off?
:(

Or even feature to limit how much it wastes on this.


Well it will only be using space when the live tv area is active.  You can change how much space live tv is allowed to occupy.  Note also, any recordings will always take precedence.  So if you drive was filled with live tv, it would go away when a recording needed the space.

---

### Post by macegr on 2007-11-19
Switch to a native MPEG2 card or a better CPU, or play around with settings that will reduce CPU usage. Installing the proper Xorg drivers will help a lot, as will getting the Xvmc overlay output up and running. Also, spend some time working on your "Live TV" record encoder settings, you may need to select a lower resolution or reduce compression. One gotcha, especially if you don't have Xvmc working, is using a high monitor resolution. Without any hardware overlay support, your CPU will have to do all of the scaling in software. Normally you would want your video resolution to be around 800x600, unless you're running a true HDTV setup.

It took me a few hours of constant tweaking to get the CPU usage during Live TV down to acceptable 25%-35% levels with a no-MPEG2 bt8x8 card. Out of the box, so to speak, it was running up to 80% usage on an AMD64 3200+ at 2.0GHz.

---

### Post by pt123 on 2007-11-19
> **superm1 said:**
> Well it will only be using space when the live tv area is active.  You can change how much space live tv is allowed to occupy. 
Where is this setting. 
I am also using this drive with other OSes & programs and they really don't know when mythtv has crapped over the drive. 


> **macegr said:**
> Switch to a native MPEG2 card or a better CPU, or play around with settings that will reduce CPU usage. Installing the proper Xorg drivers will help a lot, 
It's a DVTB card so it doesn't need to do any encoding. 

> 
as will getting the Xvmc overlay output up and running. Also, spend some time working on your "Live TV" record encoder settings, you may need to select a lower resolution or reduce compression. One gotcha, especially if you don't have Xvmc working
How do you know if XVMC is working. I have the nvidia driver for an MX440 card.  

> 
It took me a few hours of constant tweaking to get the CPU usage during Live TV down to acceptable 25%-35% .
Is it possible to get the CPU usage overlayed on the screen because myth TV runs full screen and on top. 

Anyway I feels its really unnecessary load on the CPU esp. during the summer here in Australia, a lot like Vista. 
I guess to watch normal TV I will stick to me-TV
[http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml](http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml)
(you guys should include this). It's a very intuitive piece of software.


Anyway thanks for the help guys.

---

### Post by superm1 on 2007-11-19
> **pt123 said:**
> Where is this setting. 
I am also using this drive with other OSes & programs and they really don't know when mythtv has crapped over the drive. 

There is a setting to tell myth how much of the drive to "not touch"

> 
How do you know if XVMC is working. I have the nvidia driver for an MX440 card.  

Black and White On Screen Display

> 
Is it possible to get the CPU usage overlayed on the screen because myth TV runs full screen and on top. 

Yeah probably with a screenlet and/or Compiz Fusion.

> 
Anyway I feels its really unnecessary load on the CPU esp. during the summer here in Australia, a lot like Vista. 
I guess to watch normal TV I will stick to me-TV
[http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml](http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml)
(you guys should include this). It's a very intuitive piece of software.
Anyway thanks for the help guys.
Look like an interesting piece of software.  We won't be switching any time soon, but its always good to have alternatives to point people at.

---

### Post by pt123 on 2007-11-19
> **superm1 said:**
> There is a setting to tell myth how much of the drive to "not touch"
I found this: 
AutoExpireDiskThreshold 	 1 	 NULL 	At this percentage of disk space usage recorded programs begin to auto expir
[http://www.mythtv.org/wiki/index.php/Settings_table](http://www.mythtv.org/wiki/index.php/Settings_table)
but where is the config file located?

> 
Black and White On Screen Display

Not sure what you mean but the web page above has something about xmvc:
 UseMPEG2Dec 	 1 	 mythtv 	 Which MPEG decoder to use. There are several; Standard (ffmpeg), libmpeg2, and hardware acceleration (XVMC, XVMC-VLD, MacAccel)
UseXVMC 	0 	mythtv 	 
UseXvMcVld 	0 	mythtv 	 

> 
Yeah probably with a screenlet and/or Compiz Fusion.

That is cumbersome, does XFCE have something like a system monitor in Gnome?


> 
Look like an interesting piece of software.  We won't be switching any time soon, but its always good to have alternatives to point people at.
No need to switch but having it in the repositories.

Thanks.

---

### Post by ubnewbie2 on 2007-11-19
No config file, just run the setup program for Myth.


By "Black and White On Screen Display" he means the on-screen display while watching a movie, will be in black and white - not coloured.

---

### Post by superm1 on 2007-11-20
> **pt123 said:**
> I found this: 
AutoExpireDiskThreshold      1      NULL     At this percentage of disk space usage recorded programs begin to auto expir
[http://www.mythtv.org/wiki/index.php/Settings_table](http://www.mythtv.org/wiki/index.php/Settings_table)
but where is the config file located?

There is a setting in the frontend for this.  Don't modify it via the settings table.  This is what the frontend is for.

> 
Not sure what you mean but the web page above has something about xmvc:
 UseMPEG2Dec      1      mythtv      Which MPEG decoder to use. There are several; Standard (ffmpeg), libmpeg2, and hardware acceleration (XVMC, XVMC-VLD, MacAccel)
UseXVMC     0     mythtv      
UseXvMcVld     0     mythtv      

What video card do you have, and does it support Xvmc in the first place?

> 
That is cumbersome, does XFCE have something like a system monitor in Gnome?

Not that I know of offhand.

> 
No need to switch but having it in the repositories.
Thanks.
It's on its way in for hardy.  It's up on revu right now.

---

### Post by pt123 on 2007-11-20
> **superm1 said:**
> There is a setting in the frontend for this.  Don't modify it via the settings table.  This is what the frontend is for.


I looked and I can't find it. 

Setings feature for myth is very confusing. 

> 
What video card do you have, and does it support Xvmc in the first place?
.
Nvidia MX 440

Thanks

---

### Post by superm1 on 2007-11-20
> **pt123 said:**
> I looked and I can't find it. 

Setings feature for myth is very confusing. 

Utilities/Setup->Setup->TV Settings->General->Page 2-> Extra Disk Space (in Gigabytes)

> 
Nvidia MX 440

Thanks
This supports Xvmc.  Set the setting in the Playback option for Preferred MPEG2 Decoder to be Standard XvMC

---

### Post by pt123 on 2007-11-21
> **superm1 said:**
> Utilities/Setup->Setup->TV Settings->General->Page 2-> Extra Disk Space (in Gigabytes)



Thanks but that is nothing like this:
 AutoExpireDiskThreshold 	 1 	 NULL 	At this percentage of disk space usage recorded programs begin to auto expire

One is is percentage while the other is in GB

---


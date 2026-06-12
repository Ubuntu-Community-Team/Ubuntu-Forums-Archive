---
title: "Radeon HD 4350 - Trying to install...no luck"
date: 2009-07-29
forum: Multimedia Software
---

### Post by stealthbt on 2009-07-29
Today I installed Ubuntu for the very first time.  I'm a linux beginner and I'm hoping someone can help me get my video card working.  I have an ATI Radeon HD 4350.  I downloaded the latest driver from ati's site, but it won't run/install when I double click it.  Here are two pictures to show you what I'm dealing with.  I can't see the bottom of any windows because of the resolution which means I can't see what options I'm being offered at the bottom.

the first is the message I get when I click on System ---> Admin ---> Hardware Drivers

the second pic is what comes up when I double click on the ati driver package I downloaded from their website.

I'm trying to set this box up as an HTPC.  Any help in getting this display driver installed would be greatly appreciated!  I can't get anything better than 640 X 480 right now.

Thanks!

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error6.jpg[/IMG]

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error7.jpg[/IMG]

---

### Post by vinutux on 2009-07-30
don't open .run file with gedit install it

1. right click[B] .run file > properties >permission tab > Allow executing
[/B]
2 . open terminal... [B][COLOR="DarkRed"]applications > accessories > terminal
[/COLOR][/B]
3 drag .run file to terminal  and hit **enter**

.:D

---

### Post by stealthbt on 2009-07-30
> **vinutux said:**
> don't open .run file with gedit install it

1. right click[B] .run file > properties >permission tab > Allow executing
[/B]
2 . open terminal... [B][COLOR=DarkRed]applications > accessories > terminal
[/COLOR][/B]
3 drag .run file to terminal  and hit **enter**

.:D

Thanks for the reply!  I was hoping somebody would be able to help the newbie!

Everything looked good to start with but, unfortunately, I did what you said and I received the following error: "You need to run this installer as the super-user."

I tried typing sudo and then dragging in the .run file but that didn't work.  

Hopefully you have some more info for me! :)  Thanks!

---

### Post by stealthbt on 2009-07-30
> **vinutux said:**
> don't open .run file with gedit install it

1. right click[B] .run file > properties >permission tab > Allow executing
[/B]
2 . open terminal... [B][COLOR=DarkRed]applications > accessories > terminal
[/COLOR][/B]
3 drag .run file to terminal  and hit **enter**

.:D

I got impatient so I tried a couple of other things as well.  I was reading some documentation on how to use the root (which I'm assuming is the "super user" that the error message keeps referring to).  Here is a screen shot of the command I ran.  I was able to get a bit further into the process.  Check out the second screen shot to see where I ended up, but ultimately, it failed with an error message that I definitely don't understand.  

Hopefully somebody can help! Thanks!

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error9.jpg[/IMG]

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error10.jpg[/IMG]

---

### Post by vinutux on 2009-07-30
You are try to install .run from ati.com...but install from official repo is recommend...(and more simple too)

first screenshot show that you need to install driver..... install it from repo....**System>Administartion>hardware drivers** and tick and enable **Ati/amd propritery FGLRX **it.....the restart


it take some time...coz downloading drivers from ubuntu repo...try it...it is better than .run from ati

---

### Post by stealthbt on 2009-07-30
> **vinutux said:**
> You are try to install .run from ati.com...but install from official repo is recommend...(and more simple too)

first screenshot show that you need to install driver..... install it from repo....**System>Administartion>hardware drivers** and tick and enable it.....the restart


it take some time...coz downloading drivers from ubuntu repo...try it...it is better than .run from ati
That's the very first thing I tried but unfortunately, because the default resolution without the proper driver is so low, I cannot see the bottom of the window!  Check out the first pictures I posted.  

Do you know a key combo shortcut that will force the window to resize to my actual desktop?

this was a problem during installation as well.  most times i had to just hit 'enter' and take the leap of faith that it was on the correct 'next' or whatever button!

I can't figure out how to get my screen to either scroll down so i can see the bottom of the window, or force the window to resize.  Any suggestions?

---

### Post by stealthbt on 2009-07-30
> **vinutux said:**
> You are try to install .run from ati.com...but install from official repo is recommend...(and more simple too)

first screenshot show that you need to install driver..... install it from repo....**System>Administartion>hardware drivers** and tick and enable **Ati/amd propritery FGLRX **it.....the restart


it take some time...coz downloading drivers from ubuntu repo...try it...it is better than .run from ati

Also, when I try to tick the box as you suggest, nothing happens.  the box doesn't fill in.

---

### Post by vinutux on 2009-07-30
> **stealthbt said:**
> Also, when I try to tick the box as you suggest, nothing happens.  the box doesn't fill in.

thats because of you are unable to see th whole screen...check this system>preferences>display and change resolution....:D

---

### Post by stealthbt on 2009-07-30
> **vinutux said:**
> thats because of you are unable to see th whole screen...check this system>preferences>display and change resolution....:D

I'm an Ubuntu newbie but not a complete idiot!  haha!  

I tried to change the resolution but it won't let me.  Without being able to install the correct display drivers, the only resolution available to me is 640 X 480. It's the only option in the dropdown box in the display setting.

Any other way to change the screen resolution or force the window into the screen?...

---

### Post by vinutux on 2009-07-30
> **stealthbt said:**
> I'm an Ubuntu newbie but not a complete idiot!  haha!  

I tried to change the resolution but it won't let me.  Without being able to install the correct display drivers, the only resolution available to me is 640 X 480. It's the only option in the dropdown box in the display setting.

Any other way to change the screen resolution or force the window into the screen?...

**Chek and tweak xorg.conf ([COLOR="Red"]at your own risk)[/COLOR]**

Alt+F2 and type gksu nautilus....eneter password

go to /etc/X11 in that window (file manager)

[**[COLOR="Red"]back up xorg.conf before edit[/COLOR]**]

open xorg.conf and change your resolution...save....reboot 

.

---

### Post by Sepanderi on 2009-07-30
> **vinutux said:**
> You are try to install .run from ati.com...but install from official repo is recommend...(and more simple too)

I'm interested to hear why the drivers shouldn't be downloaded from ATI and installed with the provided installer. Is the only reason that using the package manager is "easier" or is there something else to it?

---

### Post by vinutux on 2009-07-30
Driver from repo means well tested by ubuntu community and stable too...It autoinstall and remove via syanaptic/add-remove

Driver from ati/amd.com is updated every month....coz...not so stable..(they give support for ubuntu) but updated.......it is need to install manually with.run file....and not uninstallable easily:)

---

### Post by Sepanderi on 2009-07-30
> **vinutux said:**
> Driver from repo means well tested by ubuntu community and stable too...It autoinstall and remove via syanaptic/add-remove

Driver from ati/amd.com is updated every month....coz...not so stable..(they give support for ubuntu) but updated.......it is need to install manually with.run file....and not uninstallable easily:)

Hmm, I wonder if this is why I lost my graphics drivers (which I installed using ATI installer) when I installed kernel updates and what not? [http://ubuntuforums.org/showthread.php?t=1226318](http://ubuntuforums.org/showthread.php?t=1226318)

---

### Post by stealthbt on 2009-07-30
I finally figured it out!  Thanks a ton for your help guys!

P.s.  I forgot I had the big screen tv hooked up via hdmi.  this wasn't allowing me to see the proper resolution on my 19" lcd that I was using for configuration.  I disconnected the big screen, restarted the machine, and I was able to get everything working.

Thanks again for all the help.  I really appreciate it and look forward to learning all about Ubuntu.

---


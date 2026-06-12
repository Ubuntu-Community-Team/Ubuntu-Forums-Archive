---
title: "Can't change system sounds"
date: 2010-12-11
forum: Multimedia Software
---

### Post by billburn2 on 2010-12-11
I'm using Ubuntu 10.10I'm trying to put in my own custom sounds for the Ubuntu system sounds (Like login, logout, message received...)
I have .mp3 files, I converted them to .ogg files. I went into the system sound folder (usr/share/sounds/ubuntu/stereo) and tried pasting in my sounds named as what I want (ex. I named my custom sound "desktop-login.ogg").  When I try pasting mine in, it asks if I want to replace the old one, I say yes, and it says "Error opening file '/usr/share/sounds/ubuntu/stereo/desktop-login.ogg': Permission denied"

I've tried just going into System > Preferences > Sound.  The only sound themes available are "Ubuntu" and "No Sounds" I don't see a way to make a custom theme or anything.

I've tried looking up ways to do this, that's how I got the first idea. :\

---

### Post by Jahid65 on 2010-12-11
By default you can't paste anything under root directory. To copy-paste in / directory you must use nautilus (File manager) as root. 

[B]Caution: While in root mode, Please careful about what are you doing. Because if you do something wrong in root mode, that can be very dangerous.


[/B]Press alt+F2 & type "gksu nautilus"(without the qoutes) in text-field & select run. Then Copy-paste your file in desired location.

But I will suggest to install ubuntustudio-sounds from the synaptic.

---

### Post by billburn2 on 2010-12-11
Nautilus worked just fine. 

I installed ubuntustudio-sounds but it wasn't exactly what I was looking for. Yeah, it's a different theme instead of default, but I want something customizable...

Is this really the easiest way to set up custom sounds in Ubuntu 10.10?

---

### Post by Yellow Pasque on 2010-12-11
> **billburn2 said:**
> Is this really the easiest way to set up custom sounds in Ubuntu 10.10?
There used to be a nice GUI for it (pic: [http://www.zolved.com/UserFiles/Image/28407/sound4.jpg](http://www.zolved.com/UserFiles/Image/28407/sound4.jpg) ), but it got replaced with a much simpler theme selector when ubuntu went to pulseaudio-specific volume GUI. Apparently, the way to do it is to create your own theme, install it, and select it. Overwriting individual files in an installed theme will probably work too, but it's generally not a good idea to replace files belonging to an installed .deb.

Another tip about nautilus: install nautilus-gksu package to get easy root access by right-clicking a folder in nautilus.

---

### Post by billburn2 on 2010-12-12
Yeah, I ended up deciding against editing the system sounds that way, I put all the original files back in their rightful place.

I saw pics of a GUI like that every time I looked up how to customize the themes, but was a little upset when my sound preferences menu is nothing like that.

How do I go about creating my own theme and installing it, then?

---

### Post by pbpersson on 2011-01-17
Here is an [old article]("http://www.rebelzero.com/tweaking/hacking-sound-themes-in-karmic/209") about how to create your own theme.  Hopefully it still applies to modern versions of Ubuntu.

I wish they would add the ability to customize the sound theme and create new themes from the GUI.  This has been missing for several versions - creating a GUI to fill this need would be fairly simple and it is a glaring omission from Gnome, IMO.

---

### Post by pbpersson on 2011-01-17
Oooo....look what I just found!

---

### Post by lupopa on 2011-11-18
Hi,

where u found this?

can i install this in Ubuntu Lucid Lynx 10.04.3 ?

greetings

lupopa

---


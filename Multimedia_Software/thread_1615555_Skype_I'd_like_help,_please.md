---
title: "Skype: I'd like help, please"
date: 2010-11-07
forum: Multimedia Software
---

### Post by throese on 2010-11-07
Downloaded it, works just fine minus the face that my web cam and headset won't work. What do I need, drivers, programs, what? I'd really like to get this set up before Monday. Anything to help.

Really old logitech cam and I've had the headset since 2007 or 2008.

---

### Post by inobe on 2010-11-07
you should just need to configure your devices, start with sound then do video.

for future use it would be helpful if we know the make and models of the devices.

---

### Post by cpmman on 2010-11-07
For your webcam download cheese (repositories) and see if it works from there.

For your sound check Sound Preferences - Hardware & Output to see it is recognised and not muted.

---

### Post by throese on 2010-11-07
How do I configure Cheese so my web cam works? No luck with just plugging the devices in and the program didn't detect the devices on its own either. So, what do I do to get the drivers?

---

### Post by inobe on 2010-11-07
> **throese said:**
> Downloaded it, works just fine minus the face that my web cam and headset won't work. What do I need, drivers, programs, what? I'd really like to get this set up before Monday. Anything to help.

Really old logitech cam and I've had the headset since 2007 or 2008.

noticed your edit, does the device appear in drop down menus ?

---

### Post by cpmman on 2010-11-07
Cheese has the main webcam dependencies with it so if it didn't work for you try System - Administration - Additional Drivers to see if it can find any.

As inobe says - let us know your devices makes and models.

---

### Post by throese on 2010-11-07
cpmman: No, the devices do not appear in the drop down box.

---

### Post by cpmman on 2010-11-07
Did you have them working in Windows and if so what version of Windows?

Sounds a bit like legacy drivers in which case you may need ndiswrapper and I'm afraid I can't help with those.

Hopefully someone who can will see this unsolved thread.

---

### Post by gradinaruvasile on 2010-11-07
Webcam (cheese is just for testing if the webcam works with your system):

Open a terminal and type this - first make sure the libv4l-0 package is installed - it is by default if i remember correctly (or lib32v4l-0 for 64-bit Ubuntu):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Or, if you have a 64-bit Ubuntu installation:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Test if the webcam is working. The idea behind this is that certain webcams wont work with some apps, although they are detected and set up by the kernel - some more here:

[http://developer.skype.com/LinuxSkype](http://developer.skype.com/LinuxSkype)

And how to make it permanent (if it works):

[http://ubuntuforums.org/showthread.php?t=1583886](http://ubuntuforums.org/showthread.php?t=1583886)

Headset: Make sure you have a system wide WORKING mic/speakers. Skype just uses these, IT DOES NOT USE ANYTHING ELSE. It uses the default output device of your system (provided by PuldeAudio).
More specifically you have to set up PulseAudio with the default input/output device of your choice. It is done from the right-click menu from the system trays volume icon (Sound Preferences, it is the only option besides mute).

---

### Post by pauwl on 2010-11-07
If you do get Cheese working, some of the Logitech Cameras still cause skype to crash. Easily reproducabble if you have a working Cheese, go to the video options in Skype and click the TEST button.

It crashes for me with a newer Logitech webcam. Some work, some don't. Unfortunately.

Hope your one does :P

---

### Post by throese on 2010-11-07
Update: Web cam works. Still trying to get the headset to work.

---

### Post by gakon77 on 2010-11-08
Mine crashes. :(

Any help, please?

---

### Post by throese on 2010-11-08
> **gradinaruvasile said:**
> Webcam (cheese is just for testing if the webcam works with your system):

Open a terminal and type this - first make sure the libv4l-0 package is installed - it is by default if i remember correctly (or lib32v4l-0 for 64-bit Ubuntu):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Or, if you have a 64-bit Ubuntu installation:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Test if the webcam is working. The idea behind this is that certain webcams wont work with some apps, although they are detected and set up by the kernel - some more here:

[http://developer.skype.com/LinuxSkype](http://developer.skype.com/LinuxSkype)

And how to make it permanent (if it works):

[http://ubuntuforums.org/showthread.php?t=1583886](http://ubuntuforums.org/showthread.php?t=1583886)

Headset: Make sure you have a system wide WORKING mic/speakers. Skype just uses these, IT DOES NOT USE ANYTHING ELSE. It uses the default output device of your system (provided by PuldeAudio).
More specifically you have to set up PulseAudio with the default input/output device of your choice. It is done from the right-click menu from the system trays volume icon (Sound Preferences, it is the only option besides mute).

gakon77: Read the stuff I quoted, that's how I got my web cam to work, hope it helps you like it helped me.

---

### Post by gakon77 on 2010-11-16
> **throese said:**
> gakon77: Read the stuff I quoted, that's how I got my web cam to work, hope it helps you like it helped me.

I installed the patch to make the changes with libv4l permanent, and actually it make the webcam work in skipe during the test, but once I took it the crunch -video conference- skipe just crashed!:(

Thanks anyway.

---

### Post by throese on 2010-11-16
Ah, you're welcome and it worked just fine for me when I took the crunch. To be honest, only problem I have with Skype is the headset not working

---

### Post by oldsoundguy on 2010-11-16
camera works in Cheese & Skype, audio works.  It won't connect to echo to test (password is valid!)
Lucid .. cable connection.

---


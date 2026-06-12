---
title: "Internal MIC fix for Acer Aspire 6930, 6930G and maybe other Aspire laptops"
date: 2010-10-16
forum: Multimedia Software
---

### Post by mtnova on 2010-10-16
Hi Everybody,

This was posted as a reply to another thread but i tought it might help others who have a problem with the internal mic , so i'm posting it here as a separate thread.

If the moderator finds that it is not needed you are free to delete it.

For a very long time i was trying everything to make internal MIC work on my laptop (Aspire 6930g)

Did all the possible input in /etc/modprobe.d/alsabase.conf and NOTHING worked.

All i can hear from the internal MIC was a static noise (it's a digital stereo microphone in those laptops).

So, here it is the fix for it.

It is guaranteed to work with "Vanilla" Maverick Meerkat and Lucid Lynx and probably with Karmic etc with ALSA 1.0.22 or later.

You DO NOT HAVE to edit anything in /etc/modprobe.d/alsabase.conf BUT if you want you can input options snd-hda-intel model=auto (with me it works better with model=auto or acer-aspire-6530g).

You have to EDIT as root

> gksudo gedit /etc/pulse/daemon.conf  

Find in it:

> ;default-sample-format = s16le
;default-sample-rate = 41600
;default-sample-channels = 2
;default-channel-map = front-left,front-right

and make it like this:

default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
; default-channel-map = front-left,front-right 

IMPORTANT : REMOVE the ; in front of the first 3 lines

SAVE, Reboot and that's it.

It should work now.

It took me 2 months  to realize that this was the problem since pulseaudio is poorly documented (or i could not find any on those settings)

Now with default-sample-rate = 48000 there is only a little static on the internal MIC so maybe someone could suggest better sample-rate??

I am glad if this is going to help anyone. 

With those settings Ubuntu MAverick (thats what i got is 100% compatible with this laptop) 

Just as a small note that DSDT needs to be fixed on it for the battery to be corectly recognized (but that is another story).

So if it helps, post your results for me and others to know.

Take care :popcorn:,

mtnova

---

### Post by lyuba on 2010-10-16
Is it safe to try the same for Lenovo ThinkPad Edge? My internal microphone is not working in new Ubuntu.

---

### Post by mtnova on 2010-10-16
No danger,

Try and let us know

mtnova

---

### Post by lucoli on 2010-11-27
Hello.
I made the changes you suggest in the conf of pulse, even though my laptop is a Lenovo G560.
Unfortunately nothing changed, my internal mic is still not working.
I should say that the mic initially was working on Ubuntu maverick. 
I had to add a line in alsa-base  in order to make the headphones input stop the external volume of the laptop, which didn't occur by default, and then I've lost the mic. Even if i go back to the previous configuration the mic remains mute.
Thanks in advance for any eventual help.
Luc.

---

### Post by Teh H4rRy on 2011-01-23
I was having trouble using Team Speak 3 with my laptop, (I would deafen my friends with static) but this method fixed it perfectly, I still need to play around with the amplification of the microphone input, otherwise perfect solution.

Thank you kindly

---

### Post by hardboy007 on 2012-07-10
hi there im having the same problem trying to fix my mic
but i have no idea how to fix it didnt understand anything u wrote lol
 any chance of any help please??
im runing windows vista
thanks

> **mtnova said:**
> Hi Everybody,

This was posted as a reply to another thread but i tought it might help others who have a problem with the internal mic , so i'm posting it here as a separate thread.

If the moderator finds that it is not needed you are free to delete it.

For a very long time i was trying everything to make internal MIC work on my laptop (Aspire 6930g)

Did all the possible input in /etc/modprobe.d/alsabase.conf and NOTHING worked.

All i can hear from the internal MIC was a static noise (it's a digital stereo microphone in those laptops).

So, here it is the fix for it.

It is guaranteed to work with "Vanilla" Maverick Meerkat and Lucid Lynx and probably with Karmic etc with ALSA 1.0.22 or later.

You DO NOT HAVE to edit anything in /etc/modprobe.d/alsabase.conf BUT if you want you can input options snd-hda-intel model=auto (with me it works better with model=auto or acer-aspire-6530g).

You have to EDIT as root



Find in it:



IMPORTANT : REMOVE the ; in front of the first 3 lines

SAVE, Reboot and that's it.

It should work now.

It took me 2 months  to realize that this was the problem since pulseaudio is poorly documented (or i could not find any on those settings)

Now with default-sample-rate = 48000 there is only a little static on the internal MIC so maybe someone could suggest better sample-rate??

I am glad if this is going to help anyone. 

With those settings Ubuntu MAverick (thats what i got is 100% compatible with this laptop) 

Just as a small note that DSDT needs to be fixed on it for the battery to be corectly recognized (but that is another story).

So if it helps, post your results for me and others to know.

Take care :popcorn:,

mtnova

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---


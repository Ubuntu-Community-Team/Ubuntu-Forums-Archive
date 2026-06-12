---
title: "firefox and lack of sound"
date: 2008-07-25
forum: Multimedia Software
---

### Post by applebypd on 2008-07-25
Hi all,

I have firefox 3 running on xbuntu 8.4. Movie Player, RhythmBox, Alsa etc all work perfectly!  

If I go to youtube and try to view anything the pictures  work perfectly but there is no sound.   I have even tried 'aoss firefox &' in a terminal and then relaunching firefox all to no avail.

/etc/firefox/firefoxrc does not exist on my system so I cannot edit it.
Any thoughts on how to fix this problem will stop me having to reboot into XP to view youtube!!!!!!!:lolflag:

Regards

pete

---

### Post by Orlsend on 2008-07-25
You cant do swf or flv properly if you have any Video Player or Media Player running (The only one I have seen that those not do that is Kaffeine)

If you want to do both get Seamonkey I quess....

---

### Post by Gibunit on 2008-07-25
I'm also banging my head against a wall with this one too.

Not having any problems with audio in media files (music/movies) even works when you hover the cursor over a track, i get audio there.

However browser audio won't work, youtube etc.

I also have no sound in WoW, this is how I initially found the problem and thought it may be a config.wtf problem or a wine config problem and so wasted hours on that trying every little combination that there's how to's on to come up with still no sound. Then went to youtube off handedly and was getting no sound there either.

Any help would be much appreciated.

If it matters at all, I had everything running perfectly, youtube worked, WoW worked, it was all cruisy. Then I restarted the PC.

I have only been using Ubuntu for about 10 days and computer has been on most of that time.

Thanks in advance.

---

### Post by applebypd on 2008-07-25
> **Orlsend said:**
> You cant do swf or flv properly if you have any Video Player or Media Player running (The only one I have seen that those not do that is Kaffeine)

If you want to do both get Seamonkey I quess....

Have tried with nothing but firefox running and Flash 9  or 10 will not give any sound in either ephifiny or firefox !

My conclusion is that it is how flash is installed on Ububtu 8.04 that is the problem but i cannot get to the root of it!

---

### Post by gandaran on 2008-07-25
> **applebypd said:**
> Hi all,

I have firefox 3 running on xbuntu 8.4. Movie Player, RhythmBox, Alsa etc all work perfectly!  

If I go to youtube and try to view anything the pictures  work perfectly but there is no sound.   I have even tried 'aoss firefox &' in a terminal and then relaunching firefox all to no avail.

/etc/firefox/firefoxrc does not exist on my system so I cannot edit it.
Any thoughts on how to fix this problem will stop me having to reboot into XP to view youtube!!!!!!!:lolflag:

Regards

pete

the easiest fix for all that flash sound problems is to use adobe flash 10 beta, remove first flash 9 or any other flash installed from your system,
if you still want to use adobe flash 9, the fix is to install the libflashsupport package, find it in synaptic.

---

### Post by gandaran on 2008-07-25
> **applebypd said:**
> Have tried with nothing but firefox running and Flash 9  or 10 will not give any sound in either ephifiny or firefox !

My conclusion is that it is how flash is installed on Ububtu 8.04 that is the problem but i cannot get to the root of it!
 

flash 10 will give you sound, maybe you still have flash 9, swfdec flash or gnash flash installed.

---

### Post by applebypd on 2008-07-25
> **gandaran said:**
> the easiest fix for all that flash sound problems is to use adobe flash 10 beta, remove first flash 9 or any other flash installed from your system,
if you still want to use adobe flash 9, the fix is to install the libflashsupport package, find it in synaptic.

Unfortunately Flash 10 is only in the 32 bit application - i have a dual core 64 bit processor and the flash10 installer will not run

Pete (with even less hair now):lolflag:

---

### Post by gandaran on 2008-07-25
> **applebypd said:**
> Unfortunately Flash 10 is only in the 32 bit application - i have a dual core 64 bit processor and the flash10 installer will not run

Pete (with even less hair now):lolflag:

I believe there's a fix for you, search the forum's, especially the beginners section, if I'm not wrong the fix is just to leave the flash 9 installed then substitute the libflashplayer.so file in /usr/lib/flashplugin-nonfree for the new flash 10 libflashplayer.so file.

---

### Post by applebypd on 2008-07-25
> **gandaran said:**
> I believe there's a fix for you, search the forum's, especially the beginners section, if I'm not wrong the fix is just to leave the flash 9 installed then substitute the libflashplayer.so file in /usr/lib/flashplugin-nonfree for the new flash 10 libflashplayer.so file.

hi Gandaran,

Many thanks for all your help - it is very much appreciated.

I have done as you said and installed flash 9 and then replaced the libflashplayer.so.  According to synaptic (when searching for flash) I have the following flash bits installed:

flashplugin-nonfree  9.0.124-Oubunto2

and thats all.   It still does not work !!:confused:

Regards
Pete

---

### Post by Yellow Pasque on 2008-07-25
If you're using PulseAudio (if you're using Ubuntu 8.04, you probably are):
```
sudo apt-get install libflashsupport
```

---

### Post by applebypd on 2008-07-25
> **Temüjin said:**
> If you're using PulseAudio (if you're using Ubuntu 8.04, you probably are):
```
sudo apt-get install libflashsupport
```

Sorry tried that and still no sound from firefox on youtube even with a reboot.

pete

---

### Post by Yellow Pasque on 2008-07-25
The next thing I would do is try starting FF from a terminal and seeing what errors it throws when you try to play Flash.

---

### Post by applebypd on 2008-07-25
> **Temüjin said:**
> If you're using PulseAudio (if you're using Ubuntu 8.04, you probably are):
```
sudo apt-get install libflashsupport
```

Still no joy with youtube even after a reboot. I'm running out of ideas :lolflag:

Pete

---

### Post by applebypd on 2008-07-25
> **Temüjin said:**
> If you're using PulseAudio (if you're using Ubuntu 8.04, you probably are):
```
sudo apt-get install libflashsupport
```

Sorry guys but even with libflashsupport  I still get no sound from the web browsers.  I am nearly going bald here trying to get flash working properly on Xbuntu 8.04 (xfce4 with gnome support):(

Pete

---

### Post by gandaran on 2008-07-25
there's only one thing left for you then, get alsa working, change all your sound settings from pulseaudio to alsa.

---

### Post by applebypd on 2008-07-25
> **Temüjin said:**
> The next thing I would do is try starting FF from a terminal and seeing what errors it throws when you try to play Flash.

hi My errorr is:

(npviewer.bin:8510): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

And will try getting rid of Pulse and adding alsa.

---


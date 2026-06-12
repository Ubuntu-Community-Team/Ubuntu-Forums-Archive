---
title: "No sound through usb device"
date: 2008-08-10
forum: Multimedia Software
---

### Post by vnetha on 2008-08-10
Hi,

I'm running Ubuntu 8.04 on an old DELL OptiPlex GX280. I have most of the system setup fine, but I am having trouble with the sound portion. You see... I have the default audio through an intel soundcard installed on the desktop, but I want to mainly use these Logitech notebook usb speakers.

problem is, with video playing on firefox or vlc, i can hear it fine if i use a separate non-usb headset. but the sound refuses to come out of the usb speakers, even though the OS seems to detect the audio device fine.

surprisingly, when i use totem, it manages to use the usb speakers ok. but i don't care for totem and would rather use vlc, and more importantly, firefox.

i have the default audio device selected properly through System-> Preferences->Sound and System->Preferences->Volume Control; to no avail.

any help would be greatly appreciated.


thanks,
Vivek.

---

### Post by vnetha on 2008-08-16
HELP! 

anyone?

---

### Post by Krydahl on 2008-08-16
Go into System -> preferences -> sound while you have the usb speakers plugged in. In the devices tab, in music and movies, you'll probably see it set to autodetect. Look in the drop down list and you find something like "usb audio" - select this and your speakers will now work.

Be nice if autodetect actually worked, true, but I haven't found a fix for that yet. In the meanwhile, this isn't a bad workaround.

---

### Post by eggdeng on 2008-08-16
You could try following post #2 on [http://ubuntuforums.org/showthread.php?t=700477](http://ubuntuforums.org/showthread.php?t=700477). You will probably need to go to Preferences -> Sound first and tell everything to use ALSA. Reboot for changes to take effect.

---


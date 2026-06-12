---
title: "Skype Mike Problem/Question?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by cybrsaylr on 2010-06-03
I put skype on both my desktop and laptop below. Went to Skype website and downloaded/installed the Linux version and Skype runs perfect on my desktop with 64 bit Karmic but a bit buggy on the laptop with 64 bit Lucid. 

Laptop problem is the Mike input level can only be be set at 50%. If it is set higher it does not work, I have to lower mike input setting back to 50 % and then people complain they can't hear me and tell me to get a better phone.

I use the same mike on the desktop and crank the mike input level up to 100% and people tell me sound quality is excellent, so I figure the mike is OK.

I'm guessing the 3.5mm mike input jack on the laptop is the problem. Tried replugging it a few times but the problem remains. Was thinking of getting a usb headset to use Skype. Would a usb headset work better and solve this low mike input sound level?

---

### Post by sanderd17 on 2010-06-03
I have a build in mic and I can't go over 50% volume without loosing the sound. So I think it won't solve your problem if you buy a usb mic. It's a software problem, not a hardware.

---

### Post by cybrsaylr on 2010-06-03
Anyway to correct this?
Was hoping to use the laptop as a cell phone since Skype works so well on the desktop. But on the laptop the mike input volume is too low and people say they can't hear me.

Is there another way to boost the mike input?

---

### Post by cybrsaylr on 2010-06-03
Update:

Since I dual boot thought I'd try out Skype with Vista on the laptop.
Installed Skype on Vista logged in and made a test call and Skype worked very well with Vista!

So right now Skype runs very well on the desktop with Karmic and on the laptop with Vista but Skype runs very poor with Lucid on the same laptop.

Think I saw someone on another thread with this issue. Could Lucid be the culprit? Problem is I can hear who is called very well but they can't hear me.

---

### Post by cybrsaylr on 2010-06-05
Bump.

---

### Post by lidex on 2010-06-05
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Reboot.

---

### Post by cybrsaylr on 2010-06-06
lidex,
Put in those 3 lines as directed then rebooted.

Made a couple test calls and Skype now works a bit better than before on laptop with Lucid. People can hear me better but still say to speak up. On sound preferences I can only go up to ~ 66% on mike input volume. If I set it higher mike cuts out with no sound at all. 

I don't have this problem when using Skype with Vista on this same laptop.

Skype works best on my desktop with Karmic with the mike input volume set all the way up to 100%. People say the sound quality is excellent on desktop.

Those 3 lines of code did improve it some with Lucid.

---

### Post by lidex on 2010-06-06
Also make sure skype option to control sound levels is unchecked.
Try gnome-alsamixer to make sure any mic-boost options are enabled.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

---

### Post by cybrsaylr on 2010-06-06
> **lidex said:**
> Also make sure skype option to control sound levels is unchecked.
Discovered and did this already on both PCs.

> **lidex said:**
> **Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.

I don't understand what you mean here? Can't figure out how to get there to make that setting before installing your final code?

---

### Post by lidex on 2010-06-06
Those are somewhat generic instructions for using gnome-alsamixer and finally, installing it, which you don't need if it's already installed. You can open it via Alt+F2 run dialog, enter 
```
gnome-alsamixer
```
In the 'edit' menu, select "Sound Card Properties' and select/deselect the various options pertaining to microphone.
Can also be accessed through gnome-menu under 'Sound&Video'

---

### Post by cybrsaylr on 2010-06-06
lidex,
Thanks that seemed to do the trick. Figured out your directions in Post #8 and had to install gnome-alsamixer. Then the 'edit-> Sound Card Properties' menu to enable elements, made sense to me.

Made the mic adjusts as needed and was able to boost the mic volume levels to a higher setting needed.

Skype now works much better on the Lucid laptop than before.

Thanks again.

---


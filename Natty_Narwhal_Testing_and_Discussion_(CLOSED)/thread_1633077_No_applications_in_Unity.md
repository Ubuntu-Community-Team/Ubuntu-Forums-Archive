---
title: "No applications in Unity"
date: 2010-11-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-11-28
I have had a rough afternoon. I went on Thanksgiving vacation with my family. When I left, both Maverick and Natty were ok. After being away for several days, naturally there were updates for both when I came back.

First, Maverick got a new kernel. After installing, it told me to reboot to complete the update. When I rebooted, the new kernel didn't show up in the grub2 menu, but it started the old kernel just fine. I decided to go to Natty and run update-grub. It ran successfully, but found nothing on my Maverick partition. I had to fix it by running the Maverick Live DVD and reinstalling grub2. Luckily, that worked.

On to Natty. Hundreds of updates, including a new kernel. "sudo aptitude update" ran ok, but "sudo aptitude safe-upgrade" hung after it said it was unpacking useradd. I went and made a sandwich, ate it, came back, and it was still in the same place. So, I rebooted and ran the safe-upgrade, again. It ran farther, this time, but hung when it was configuring grub2. Waited a long time again, bailed out, and of course, when I tried to reboot, there was no entry for Natty.

So I ran update-grub in Maverick and it found Natty and made it selectable from grub2.

Now, I boot to Natty and it comes up with a new Unity interface. It looks nice, but I cannot find a way to run my apps. The only Unity icons are for Firefox, Empathy, Tomboy, and workspace switcher. None of my apps are in any of the menus. The only panel indicators are for Sound Volume, Email, Calendar, Me, and the Shutdown/Restart/etc...  I can't even open a Terminal window.

[B]How do I get icons or menu entries for my applications?
[/B]
What a day!

Tim

---

### Post by Starks on 2010-11-28
Binary names in the terminal or Alt-F2

---

### Post by bdgdl08 on 2010-11-28
Alt+F1 opens the application menu from the classic desktop which seems to be behind the top bar, but not clickable.

---

### Post by ratcheer on 2010-11-28
> **bdgdl08 said:**
> Alt+F1 opens the application menu from the classic desktop which seems to be behind the top bar, but not clickable.

Thank you. I will try it the next chance I get.

Tim

---

### Post by shafin on 2010-11-29
If you can somehow remove the application-places-system menu from your gnome panel, Alt+f1 will bring the menu at the tip of your mouse pointer. This is faster than the traditional menu

---

### Post by MacUntu on 2010-11-29
Option 1: right-click on the desktop, create a launcher for the gnome-terminal, start the apps from there.

Option 2: use gsettings (from the libglib2.0-bin package) to set the list of launcher icons in the launcher bar: ```
gsettings set com.canonical.Unity.Launcher favorites "['nautilus.desktop','gnome-terminal.desktop','gedit.desktop', ...]"
```See the /usr/share/applications folder for valid names.

Option 3: wait until Unity is mature enough to allow you to open applications and pin them to the launcher bar.

---

### Post by garvinrick4 on 2010-11-29
# Had to go to true terminal graphical terminal was freaking out. and sudo apt-get purge unity and same with ubuntu-desktop and same with ubuntu-netbook why netbook in natty I do not know but when ran then had to run a sudo apt-get autoremove. Then reinstall ubuntu-desktop: seems as though unity offending package for now.(unity working now 11-29-10 installed).
 All seems well now:
#Have 2 installs one a fresh install at 11.04 inception aptitude safe-upgrade was fine.
1 install dist-upgraded since 9.04 was one that had to be fixed a bit. 
Works fine now: 
#Oh yes removed cairo-dock she freaked out a bit. Why I had cairo-dock running on a Alpha is beyond me anyway.
###Stopped reading sticky's in natty this all caught me by surprise over Holidays:

---

### Post by LaneLester on 2010-11-29
I'm going to try to learn to love Unity. After all, Maverick is my work system; Natty is just for fun now.

I just installed Natty, and the above tips make it possible to start applications.

The gsettings command is working for me. I found I needed to open the Properties of each file in /usr/share/applications and use the command name plus ".desktop".

It looks like there's room for about 17 icons on my screen, and I'll be hoping for a way to access more program than that, either with drawers or a menu icon (there may already be something for that which I haven't found yet).

Lane

---

### Post by nperry on 2010-11-29
> **MacUntu said:**
> 
use gsettings (from the libglib2.0-bin package) to set the list of launcher icons in the launcher bar: ```
gsettings set com.canonical.Unity.Launcher favorites "['nautilus.desktop','gnome-terminal.desktop','gedit.desktop', ...]"
```

That command returns: 62-63:invalid character in number

---

### Post by MacUntu on 2010-11-29
> **nperry said:**
> That command returns: 62-63:invalid character in number

You typed the dots, didn't you? :)

It's a list, so it should look like: "['a','b','c']"

---

### Post by nperry on 2010-11-29
> **MacUntu said:**
> You typed the dots, didn't you? :)

It's a list, so it should look like: "['a','b','c']"

*Walks away whistling* #-o* 

Thanks

---

### Post by ratcheer on 2010-11-29
Alt+F1 is working fine, for my purposes. Thanks again, bdgdl08

Tim

---


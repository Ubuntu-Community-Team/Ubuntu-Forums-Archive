---
title: "How to add a custom launcher to unity?"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mexlinux on 2010-09-20
Is there a way to add a custom launcher to unity?
Thanks,

---

### Post by kerry_s on 2010-09-20
use the "main menu" to create your launcher.
when you use it right click the icon-> keep

---

### Post by mexlinux on 2010-10-01
customized launchers, created with alacarte "main-menu" do not appear in the unity "menu interface", so there is no way to do that....

---

### Post by kerry_s on 2010-10-01
> **mexlinux said:**
> customized launchers, created with alacarte "main-menu" do not appear in the unity "menu interface", so there is no way to do that....

yeah, sorry it changed with updates.
i ended up doing it manually after that.

i'm no longer using unity, i'm running the normal desktop setup to look like unity now.

so this is from memory.

you need to create a *.desktop file for your program.

**gksudo gedit /usr/share/applications/name.desktop**

put:
```
[Desktop Entry]
Name=the name you want shown
Comment=
Exec=command to run
Icon=icon name
Terminal=false
Type=Application
StartupNotify=true

```

now in your file manager, in your home folder, press **ctrl+h** to show hidden.

go to-> .gconf-> desktop-> unity-> favourites-> launchers

you'll see a bunch of folders starting with "app-".
you need to create a folder for your program, use the same name.desktop you used in /usr/share/applications, go into 1 of the folders for something that is already on the dock & copy the xml file, paste that into your new folder & open it with the editor, change the name of the *.desktop to your name.desktop.

now open gconf-editor & go to-> desktop-> unity-> favorites, double click the list on the right & add your name.desktop.

log out & back in

if you did it right it should now be on the dock.


i found unity to be much to limiting, but like the over all look & feel. i also wanted a 64 bit install, so i installed the desktop version & used
dockbarx + maximus + xdotool to get what i wanted.

---

### Post by cariboo on 2010-10-01
I just open an app I want in the panel, then right click the icon, select keep in launcher, then left click. That works for the apps I want in the panel.

---

### Post by mexlinux on 2010-10-01
> **kerry_s said:**
> 
i found unity to be much to limiting, but like the over all look & feel. i also wanted a 64 bit install, so i installed the desktop version & used
dockbarx + maximus + xdotool to get what i wanted.

I in fact tried a similar approach, but my top panel overlaps the left one, so I have problems with the menu icon on the very top left..... How did you solved that?

---

### Post by seeker5528 on 2010-10-01
> **mexlinux said:**
> I in fact tried a similar approach, but my top panel overlaps the left one, so I have problems with the menu icon on the very top left..... How did you solved that?

If you top panel is the stock gnome-panel, then the 'application, places, system' menus are provided by a single applet, right click it, if there is a check next to 'lock to panel' click that, if there is no check next to 'Lock To Panel' then you should be able to click on 'Move', then slide the applet over with your mouse, touch pad, etc....

Later, Seeker

---

### Post by kerry_s on 2010-10-01
> **mexlinux said:**
> I in fact tried a similar approach, but my top panel overlaps the left one, so I have problems with the menu icon on the very top left..... How did you solved that?

they were both gnome-panel, gnome-panel don't overlap. i used dockbarx applet for the unity like launcher.

---

### Post by bobmanuk on 2010-10-03
> **cariboo907 said:**
> I just open an app I want in the panel, then right click the icon, select keep in launcher, then left click. That works for the apps I want in the panel.

Ive just installed 10.10 and i have chromium-browser installed via software centre, this method works for things like 
terminal, rhythmbox, firefox, epiphany etc, but not for things like chromium, opera etc...

any thoughts?

---

### Post by cariboo on 2010-10-03
I've been using Unity since it became available in the repositories, except for a week or two, I've always been able to add apps to the panel, it seems to me that you can only add apps after a reboot. I normally use hibernate, so reboots are something that doesn't happen very often normally. I have two installs, one that has been upgraded since alpha 2 and the other was a Lucid to Maverick upgrade for testing purposes.

Once the final is released, I'll do a clean install on both partitions, one for a fallback, and one for testing Natty.

---

### Post by bobmanuk on 2010-10-05
ive been using 10.10 since the alpha's too, all of the alpha installs and the beta install failed in one way or another, both upgrading from 10.04 and fresh installs, or indeed failed to boot from usb (since im using a netbook) i could try wiping and installing again.

I did what kerry suggested (but found out for myself by poking around in terminal) and it works but is a VERY long winded way of solving the problem....

i do hope this issue doesnt pop up when 10.10 is released

---

### Post by cariboo on 2010-10-05
I'm sure there will be more customization when Unity matures a bit more.

---

### Post by bobmanuk on 2010-10-06
well ive just formatted and re-installed (and for my sins have to download and reinstall about 150MB of updates so i can send crash reports) and it seems that unity is behaving ok now. how very odd

EDIT - spoke too soon, just installed chromium and the issue is still there... just a thought, maybe the updates kill unity's ability to add these custom launchers?

---

### Post by cariboo on 2010-10-06
I usually update daily, if not twice a day, so that has nothing to do with it. I updated this morning and added a launcher for gnome-screenshot to the panel.

---

### Post by kerry_s on 2010-10-06
> **bobmanuk said:**
> well ive just formatted and re-installed (and for my sins have to download and reinstall about 150MB of updates so i can send crash reports) and it seems that unity is behaving ok now. how very odd

EDIT - spoke too soon, just installed chromium and the issue is still there... just a thought, maybe the updates kill unity's ability to add these custom launchers?

log out & back in for unity to detect the newly installed program.

---

### Post by bobmanuk on 2010-10-06
well, im no expert so it was a mere guess, but as it turns out after a fresh install and no updates, I installed xchat, and it wont let me attach it to the side bar.

[screenshot](http://img25.imageshack.us/img25/9614/screenshotib.png)

---


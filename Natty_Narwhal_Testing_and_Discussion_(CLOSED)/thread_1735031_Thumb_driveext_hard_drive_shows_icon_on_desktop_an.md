---
title: "Thumb drive/ext hard drive shows icon on desktop and in dash when connected"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by residualbit on 2011-04-20
I'm guessing it works this way for everyone, but when I connect a flash drive or ext hard drive, the icon is displayed on the desktop and at the bottom of the dash.

It would be cool if it *only* showed on the dash. I have a usb HDD that is attached all of the time, so the dual icons are redundant.

I did notice that the right click menu's are different. The dash icon only gives you open and safely remove.

Anyone know of a way, for this scenario, to get rid of the desktop icon, keep the dash icon, and possibly have the dash icon inherit the right click options from the desktop icon?

---

### Post by dwielunski on 2011-04-20
Alt+F2, type 'gconf-editor'.
Under 'Apps-Nautilus-Desktop', uncheck 'Volumes visible' and it will no longer be on the desktop.

What are you wanting to see when you right-click the icon on the launcher?

---

### Post by residualbit on 2011-04-21
> **dwielunski said:**
> 

What are you wanting to see when you right-click the icon on the launcher?


Mostly just the format and properties options.

---

### Post by Daedal on 2011-04-22
i don't think there's a way to add those options on the laucher icons without someone changing the code. the mounted media icons appear to be completely controlled by unity so it isn't nearly as easy as adding static list options into the other buttons.

if you'd rather keep the icons on the desktop instead of the launcher. it's a almost the same process except using dconf-editor instead of gconf-editor.

first install dconf-editor. you can find it in the ubuntu software center. once installed press Alt+F2 and type in dconf-editor

the option is under desktop > unity > devices.  just change the devices-option value from OnlyMounted to Never and you're finished.

---


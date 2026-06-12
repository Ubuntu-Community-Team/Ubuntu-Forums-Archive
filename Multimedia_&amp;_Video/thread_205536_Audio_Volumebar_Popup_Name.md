---
title: "Audio Volumebar Popup Name?"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by Egalus on 2006-06-28
Hi,

as I needed to redefine the multimedia keys on my laptop to change the master volume and the headphone volume at the same time I had to remove the keyboardshortcuts for those keys and now the nice volumebar indicating at which setting the mastervolume is no longer pops up.

As I would love to have it back but have absolutely no idea how this small popupwindow is handled or what it's name might be I hope someone else can tell me how I "manipulate" it with a shellscript.

Thanks for you answers,
Norbert

---

### Post by LordRaiden on 2006-06-28
If you are using Kubuntu, the application is kmix.

---

### Post by Egalus on 2006-06-29
No, I am using Ubuntu not Kbuntu, so it's gnome and not kde.
Also I don't mean the normal mixer program of gnome, but the popup volumebar that appears if you press special multimedia keys.
This popup shows you at which setting the volume is at that moment and this is only visible for a short period of time.

---

### Post by mattweber on 2006-07-01
I am looking for information on that same popup.  I think gnome-settings-daemon is what controls the popup, however I have no idea how to adjust it's settings.

---

### Post by Astro96 on 2006-07-08
I am also looking for information on this.  Anyone know?

---

### Post by Astro96 on 2006-07-11
I am using KeyTouch to control my keyboard so I lost control of the cool audio bar.  KeyTouch allows me to run a program when the volume is changed, hence why I wanted to know the name of the volumebar.  I have found a workaround, however:

1. Download the xautomation package.  That will give you xte which allows you to simulate keystokes.

2. Set the volume up/down/mute shortcut keys in gnome to be obscure shortcuts -- like Control+Alt+Shift+u for volume up.

3. Create a script for up, down and mute.  My script for volume up looks like this:
----start----
#!/bin/bash

xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key u' 'keyup Alt_L' 'keyup Control_L' 'keyup Shift_L'
----end----

4. Make the script executable: chmod +xx <path_to_script>

5. Set the program to be called when the appropriate key is pressed.  For me, using KeyTouch this is really simple -- just click on the right entry and type in the path.

It is working great for me!  Hope it helps you guys.
Andy

---


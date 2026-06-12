---
title: "Chrome as Netflix app in lubuntu"
date: 2016-02-19
forum: Multimedia Software
---

### Post by lhffan on 2016-02-19
Hello

Im on myway setting up a simple tvbox for my personal use. 
Where i will have the following installed:

Firefox: Browsing
Plex: Videos
Spotify: Music
Chrome; Netflix  *(Changed Icon to Netflix Icon)*

Now i launch all those applications through the panel in lubuntu/lxde. I want to have chrome to use the --start-fullscreen switch.
I have searched for any file that i can edit the launch of chrome. But still no luck.

Edit:
**~/.local/share/applications** or **/usr/share/applications**
Exec=xxx --start-fullscreen

Do you Think it will work? Im at work atm and looking for a solution

---

### Post by ajgreeny on 2016-02-19
You simply need the command for chrome (google-chrome)? with the command option you show, ie ```
google-chrome --start-fullscreen
```

It works in chromium, so I assume it will also work in Chrome, but I have no way to test it as I don't use Chrome.

---

### Post by shane_faulkinbury2 on 2016-02-19
I use Google Chrome on Ubuntu 15.10 and on every screen such as in Netflix or Udemy there is a button in the lower right hand corner to make fullscreen!

---

### Post by lhffan on 2016-02-20
I have now managed to create a new shortcut that start the brower in full screenmode (F11).

Feels better this way. :-)

google-chrome --start-fullscreen work wery good.

---

### Post by ajgreeny on 2016-02-21
Great!
Please mark as SOLVED from the Thread Tools menu at the top.
Done on your behalf.

---


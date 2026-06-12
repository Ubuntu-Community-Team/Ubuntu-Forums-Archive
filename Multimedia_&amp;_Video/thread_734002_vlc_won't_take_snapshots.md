---
title: "vlc won't take snapshots"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by the2ndgenesis on 2008-03-24
Hey all, recent convert from XP here. Just had a quick question about taking screenshots with my favorite video player, VLC.

Just last night the screencap function seemed to work like a charm, but this morning it doesn't seem to do anything when I give the command, When I click the menu option, there's no screencap preview, no save location, nothing. Whenever I try to change the screenshot directory nothing happens and it eventually resets to blank after closing the player. The same thing happens when I try to set the image format to .jpg instead of .png.

I'm continuing to have problems even after re-installing VLC and all of its related packages from Synaptic. Is there some setting I've screwed up along the way, and is there a quick fix to this issue? Any help you could offer would be hugely appreciated.

---

### Post by wolfen69 on 2008-03-24
the best way to re-install is to first:
```
sudo apt-get remove --purge vlc
```
then
```
sudo apt-get clean
```
```
sudo apt-get install vlc
```
which will remove unused packages that would otherwise be re-installed, insuring that you download a new package. you may want to also go to home folder and view hidden files (ctrl-h) and delete the .vlc directory. (not mandatory)

for screenshots of active window, do alt-prtsc.

---

### Post by the2ndgenesis on 2008-03-24
> **wolfen69 said:**
> the best way to re-install is to first:
```
sudo apt-get remove --purge vlc
```
then
```
sudo apt-get clean
```
```
sudo apt-get install vlc
```
which will remove unused packages that would otherwise be re-installed, insuring that you download a new package. you may want to also go to home folder and view hidden files (ctrl-h) and delete the .vlc directory. (not mandatory).

I did all that as you suggested, but still, no luck. Thanks anyway, though!
Does anyone else have any suggestions?

---

### Post by mc4man on 2008-03-24
It seems that can be borked  - when I tried the default hotkey (ctrl+alt+s) - nothing. Went into settings and changed to something that didn't conflict with another preset - ctrl+shift+r - saved and then it worked. Went back and changed to ctrl+shift+s _saved_ and still works. As far as changing png>jpg didn't try

Edit: changing to jpg works - pick it from drop down list and _save_

---

### Post by the2ndgenesis on 2008-03-24
> **mc4man said:**
> It seems that can be borked  - when I tried the default hotkey (ctrl+alt+s) - nothing. Went into settings and changed to something that didn't conflict with another preset - ctrl+shift+r - saved and then it worked. Went back and changed to ctrl+shift+s _saved_ and still works. As far as changing png>jpg didn't try

Edit: changing to jpg works - pick it from drop down list and _save_

Thanks for the ideas, mc4man, but that didn't seem to work either.
Oh well. I guess I could just use prnt scrn to screencap whatever it is I'm watching, worse come to worse (I could never do that on Windows for some reason...)

---

### Post by Tylazene on 2008-03-26
Did you try to manually change the .vlc config file? I had problems saving my settings too until I did it manually. Sometimes it's easier that way because everything is all in the same place instead of spread out like in the GUI.

---


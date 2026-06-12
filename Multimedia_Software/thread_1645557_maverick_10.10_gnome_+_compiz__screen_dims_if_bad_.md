---
title: "maverick 10.10 gnome + compiz : screen dims if bad keyboard input (ex: del key)"
date: 2010-12-14
forum: Multimedia Software
---

### Post by hanasaki on 2010-12-14
Running 10.10 with compiz and gnome

The whole screen goes dim for any of the below examples.  running "compiz --replace" fixes it until any of the below happens again.  When the screen is dim, a new window opened (ex: firefox new window or a new gnome terminal) is full brightness while the rest of the screen stays dim.

Following causes the screen to go dim:

[LIST]
[*]in the screen saver - hit the delete key to backspace when the password field is empty.
[*]in firefox - ^f to find on a page - start typing and as soon as the find field has text that does not exist anywhere on the page "Phrase not found" the screen dims.
[*]in gnome terminal - the profile has the terminal bell checkbox ON - hit backspace on a bash input line with no text on it.
[/LIST]

---

### Post by hanasaki on 2010-12-15
Turns out to be the "visual bell" in compiz and "fading" that is set in the compiz manager.
[http://ubuntuforums.org/archive/index.php/t-1521362.html](http://ubuntuforums.org/archive/index.php/t-1521362.html)


[LIST]
[*] CompizConfig Settings Manager
[*]"Fading Windows"-plugin's settings
[*]turn off "Visual  Bell" and "Fullscreen Visual Bell"
[/LIST]

---

### Post by cmcginty on 2011-05-05
I just want to say thanks for posting this solution

---


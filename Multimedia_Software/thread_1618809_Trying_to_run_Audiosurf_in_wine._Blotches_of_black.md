---
title: "Trying to run Audiosurf in wine. Blotches of black? no game loading?"
date: 2010-11-11
forum: Multimedia Software
---

### Post by Ukarion on 2010-11-11
I was wondering why my Audiosurf isnt loading properly in wine? When I try to load the game from the .exe a window full of white pops up and then little black progress bar moves and some strange rectangle is on the left. I hear NO sound nor does anything load after the bar and rectangle.

What am i missing? What do i need to install on wine to make the game run? Thank you :)

And also why isn't my network thing showing next to the time and date? None of my icons seem to be appearing (Skype not showing and when i close out a chat i cannot open skype again because the icon isn't there)

Thank you!!

[IMG]http://i55.tinypic.com/20i6o1u.jpg[/IMG]

Screeen shot :)

I'm running on Ubuntu 10.10 Desktop :)

---

### Post by ExileAmongYou on 2010-11-11
Try opening up /home/(your username)/.wine/drive_c/Program Files/Steam/steamapps/common/audiosurf/config.ini and setting "runfullscreen" to true.

You might also want to try running "Configure Wine" from the menu and unchecking "Allow the window manager to control the windows" and "Allow the window manager to decorate the windows"

Audiosurf works for me at the moment, although in the past there were patches where it didn't, which might have been linked to particular versions of Wine. Great game.

---

### Post by YfoMp5QBh2 on 2010-11-11
I gave up on Wine a while ago. It seems half the games I try and use with it don't run very well, so I use VirtualBox with WinXP installed on it instead.

---


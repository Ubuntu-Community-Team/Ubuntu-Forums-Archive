---
title: "How to set up media keys for Audacious?"
date: 2012-09-13
forum: Multimedia Software
---

### Post by slmpika on 2012-09-13
I am using Ubuntu 12.04. The default media player is Rhythmbox, however, I installed Audacious as well since Rhythmbox was unable to handle large playlists without crashing. The only problem I have now is that the media keys on my keyboard do not work with Audacious. How can I make the keys that I set in Settings->Keyboard->Shortcuts->Sound and Media work with Audacious? Currently, if I press any of the media keys, a stop symbol "( / )" appears.

---

### Post by slmpika on 2012-09-18
I fixed part of my problem so far.

To set the default media player go te Settings->Details->Default Applications.

To remove Rhythmbox from the taskbar, install the package 'dconf' and run 'dconf-editor'. Navigate through com -> canonical -> indicator -> sound. Remove rhythmbox from the interested-media-players and add it to blacklisted-media-players.

However, I still cannot get my Play/Pause, Stop, etc keys to work with Audacity only with Rhythmbox. Does anyone have a fix for this?

EDIT:

I found out how to do this. It appears that Audacious has a hidden menu. To show this menu, you have to right-click on any of the top-right icons (play,stop) and select View -> Show Menu Bar. Now you can enter the preferences menu through File->Preferences. Navigate to Plugins -> General and check both "Global Hotkey" and "Gnome Shortcuts".

---


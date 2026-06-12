---
title: "HOWTO - VLC ISO Audio"
date: 2008-06-08
forum: Multimedia Software
---

### Post by mastermindg on 2008-06-08
VLC No sound ISO

I had an issue earlier today that left me scratching my head. After much tedious work I realized that vlc would play audio from a terminal but not i you opened from nautilus. I searched around and found a posting in launchpad referring to this. 

The fix for this is to change how vlc is opened. Right-click on VLC in the menu, choose Properties, and change to:

**vlc %m **

Alternately you can edit /usr/share/applications/vlc.desktop.
Also you could set only iso images to open in this manner, whatever you choose.

This fixed this issue; however, my primary reason for starting all of this was because I couldn't open my dvd images in Myth. I tried %m in place of the initial %s but nothing. So I remembered the mention of setting up iso to open with a custom command.

The command in MythTV is:

**vlc -f dvd://%s vlc:quit**

The -f and vlc:quit options just make it easier to play within the frontend.

If you have some time to waste lookup some of the advanced options to open up vlc. It's amazing the stuff you can do from command-line, which is why I dropped Vista Premium like a bad egg. :-)

---


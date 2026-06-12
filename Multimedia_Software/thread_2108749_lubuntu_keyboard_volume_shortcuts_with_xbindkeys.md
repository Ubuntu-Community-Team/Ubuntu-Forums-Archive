---
title: "lubuntu keyboard volume shortcuts with xbindkeys"
date: 2013-01-25
forum: Multimedia Software
---

### Post by opiumpoetry on 2013-01-25
1. install xbindkeys in Synaptic or in terminal: sudo apt-get install xbindkeys xbindkeys-config


 2. execute this in terminal: xbindkeys --defaults > ~/.xbindkeysrc


 3. to open xbindkeys GUI, execute this in terminal: xbindkeys-config


 4. press the "New" button on bottom to create a new keybinding


 5. the basics:

    Name: Mute
    Action: amixer sset Master toggle

    Name: Increase volume
    Action: amixer sset Master 1+ unmute

    Name: Decrease volume
    Action: amixer sset Master 1- unmute


 6. after entering each "Name/Action" pair, press the "Get Key" button on right ( you may need to maximize the blank white window that opens),
    press the key or combination of keys you want, and it will capture it for you; then hit the "Apply" button on right


 7. go to "File" tab in upper left corner and hit "Save to default File" in the dropdown menu


 8. Add "xbindkeys &" to your autostart.sh so it runs on startup


Finished.

---

### Post by raen on 2013-05-07
Thanks for this! My main problem is that I can't find my autostart.sh. I've searched the entire directory structure and turned on "show hidden" but I get no results.

---


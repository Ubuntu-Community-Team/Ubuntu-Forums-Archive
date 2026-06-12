---
title: "Resolution"
date: 2013-11-28
forum: Multimedia Software
---

### Post by soulsilver569 on 2013-11-28
sorry, i am new in ubuntu and i need change mi pc resolution to 1024x768 how can i do it

---

### Post by sudodus on 2013-11-28
Welcome to the Ubuntu Forums :-)

Are you familiar with the terminal window? You can start it with the hotkey combination ***ctrl + alt + t***
Run the command ```
xrandr
``` Type it and press the Enter key to start the command.

It will show a list of available resolutions in your system. Choose one of them,

```
xrandr -s <size>/<width>x<height>
```

so if available, run```
 xrandr -s 1024x768
```

---

### Post by Yellow Pasque on 2013-11-29
This is often helpful: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

If you still can't get it, pastebin (or post using code tags) your /var/log/Xorg.0.log

---


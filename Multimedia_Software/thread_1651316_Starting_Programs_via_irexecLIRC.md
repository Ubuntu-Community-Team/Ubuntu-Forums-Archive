---
title: "Starting Programs via irexec/LIRC"
date: 2010-12-22
forum: Multimedia Software
---

### Post by Lone_Joker on 2010-12-22
How do I map commands to my remote?

I have LIRC working with my remote and *irexec* runs on login. The only command I've been able to map has been my power/halt button. I'm trying to map other buttons to start Hulu Desktop and Boxee. I've edited my *.lircrc* to get these working, but something isn't working right. I don't have access to the machine right now but I remember using something similar to this:
```
begin
prog = irexec
button = ${BUTTON}_UP
config = ${COMMAND}  # Hulu Desktop = huludesktop, Boxee = path somewhere in /opt
end
```

For some reason there is a huge lag between the time that the buttons are pressed and when the programs start. This lag does not occur when I use my mouse to click on the programs' icons or when I start the programs from my terminal.

Oh, and how would I get my remote to switch between Boxee and Hulu Desktop? I was thinking about creating a script that would kill one program and start the other and using that as the config in my *.lircrc*. Would this be the way to go, or is there a better way?

---


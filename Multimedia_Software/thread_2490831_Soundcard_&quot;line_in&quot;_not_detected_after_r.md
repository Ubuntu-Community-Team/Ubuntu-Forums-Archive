---
title: "Soundcard &quot;line in&quot; not detected after reboot"
date: 2023-09-17
forum: Multimedia Software
---

### Post by alvere on 2023-09-17
Kubuntu 22.04.3 here
i have a TV next to computer and TV audio exit connected to LineIn input from soundcard. When i turn on or reboot computer the "line in" input doesn't show in pulse audio volume control neither in '[FONT=monospace][COLOR=#000000]pactl list | grep "Line In"' command. If i unplug and plug again the minijack connector to the soundcard plug then the "line in" device appears in both pactl and pavucontrol. 
This is the output for [/COLOR][/FONT][FONT=monospace][COLOR=#000000]pactl list | grep "Line In"[/COLOR]
[/FONT]```
[FONT=monospace][COLOR=#000000]analog-input-linein: [/COLOR][COLOR=#ff5454]**Line In**[/COLOR][COLOR=#000000] (tipo: Línea, prioridad: 8100, disponible) [/COLOR]
analog-input-linein: [COLOR=#ff5454]**Line In**[/COLOR][COLOR=#000000] (tipo: Línea, prioridad: 8100, compensación de latencia: 0 usec, [/COLOR]disponible)[/FONT]
```

[FONT=monospace][COLOR=#000000]Is there any way to fix this and set "line in" as a permanent device?[/COLOR]



[/FONT]

---

### Post by alvere on 2023-11-19
Anybody have a single clue about it? My line-in minijack connector is starting to fail because i have to unplug and plug again everyday.

---


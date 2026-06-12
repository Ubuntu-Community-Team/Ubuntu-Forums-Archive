---
title: "Discord - No Input or Output Devices detected"
date: 2017-05-31
forum: Multimedia Software
---

### Post by therocan64 on 2017-05-31
I'm very new to Linux in general and have only been on for a month. I've been slowly getting used to Ubuntu and love it so far. So, here's the issue:

On Discord (installed through 'Ubuntu Software'), my Input and Output Devices both say 'No [Input/Output] Devices'. It only started to happen after I installed Wine. Steam's sound and voice still works though.

I just recently installed Wine [Stable Branch] using the official [[WineHQ Wiki instructions]]("https://wiki.winehq.org/Ubuntu"). Ever since, 'pulseaudio' fails to load on startup but does open when I open it via the terminal. When I do, however, I get this:

```
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

I just tried the chmod and chow methods most googling lead me to and I almost locked myself out of my own computer. :neutral: Any help to figure this out would be great and thank you for your time.

I'm online most of the time so I should reply quickly to any replies. :smile:

---

### Post by therocan64 on 2017-06-01
Moved due to wrong section.

---

### Post by vasa1 on 2017-06-01
> **therocan64 said:**
> Moved due to wrong section.

Please don't post duplicate threads. If you need a thread or post moved, use the Report button and mention what you need.

---

### Post by therocan64 on 2017-06-01
I resolved it. I uninstalled the Discord I found searching the Ubuntu  Software app and downloaded the .deb from the official website. I still  don't know why pulseaudio won't open on startup but I'm sure I can  figure that out.

---


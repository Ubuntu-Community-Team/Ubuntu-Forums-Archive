---
title: "Problems with sound in Flash player"
date: 2014-08-28
forum: Multimedia Software
---

### Post by JvH1983 on 2014-08-28
Hello,

At the moment I'm facing 2 problems with the Flash player plug-in.

Problem 1:
Ever since PulseAudio was introduced in Ubuntu, I've had the problem that there is a very noticeable sound delay in many applications. Since then, the situation has improved considerably. However, this sound delay remains when playing Flash games. In earlier versions of Ubuntu I was able to fix this by launching Firefox with this script:
```
#!/bin/bash
export PULSE_LATENCY_MSEC=20
exec /usr/bin/firefox "$@"
```
But not anymore... When I use this script in Ubuntu 14.04 (whether it be Unity or Gnome Session Fallback, which I'm using at the moment) this fix doesn't seem to have any effect.
Does anybody know how to solve this?

Problem 2:
When I open the settings menu in the Flash player, it doesn't respond to mouse clicks. Somewhere I read that it has to do with Compiz, but I'm still not sure how to solve this issue. Who can help me with this?

Thanks in advance for your answers.

Kind regards,

JvH

---

### Post by Yellow Pasque on 2014-08-29
Have you tried this tsched hack? [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by JvH1983 on 2014-08-29
Thanks for your reply. I'll give it a try as soon as I get home.

---

### Post by JvH1983 on 2014-08-31
Here's what I have tried:

I added the tsched parameter to default.pa. Then I tried launching Firefox both with and without setting the PULSE_LATENCY_MSEC environment variable.
I used the command [FONT=courier new]env PULSE_LATENCY_MSEC=20 firefox[/FONT] during my test. Unfortunately, it didn't help. Then I also tried the HDA Intel thing described in that article, launching Firefox both with and without the environment variable. That didn't work either...

---

### Post by JvH1983 on 2014-09-19
I found a work-around.
I installed Chromium and pepperflashplugin-nonfree. Both sound and settings menu work properly in Chromium.

---


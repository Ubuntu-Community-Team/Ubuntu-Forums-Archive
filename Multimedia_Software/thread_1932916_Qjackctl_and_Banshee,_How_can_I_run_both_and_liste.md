---
title: "Qjackctl and Banshee, How can I run both and listening to banshee or youtube music?"
date: 2012-02-28
forum: Multimedia Software
---

### Post by Abufalia on 2012-02-28
Hi all, 

as I run qjackctl I can't reproduce any music from banshee or youtube (chromium) videos. 

How can I fix it?

Thank you

Abufalia

---

### Post by undeuxtrois on 2012-03-05
Hello,

On Oneiric (this also applies to previous ubuntus ...),  "/usr/bin/qjackctl" is actually a bash script that disables PulseAudio before running the "real" qjackctl binary at: "/usr/lib/qjackctl/qjackctl.real". This is part of the problem. You should use "qjackctl.real" to prevent disabling other PulseAudio apps.

Also, to be able to run Banshee or youtube videos in your JACK session, you should setup PulseAudio to send it's audio through JACK, while you are using it.

[Here is an older thread]("http://ubuntuforums.org/showthread.php?t=1799304") that can guide you setting it all up.

I hope it helps, 

P.

---

### Post by undeuxtrois on 2012-03-05
I just realized that the Arch wiki doesn't have the "PulseAudio through JACK" section anymore... 

Here's a link to a previous version:

[https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#PulseAudio_through_JACK_the_new_way](https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#PulseAudio_through_JACK_the_new_way)


P.

---


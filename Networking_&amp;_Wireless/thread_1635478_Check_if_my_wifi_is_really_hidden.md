---
title: "Check if my wifi is really hidden"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by lucacerone on 2010-12-01
Dear all,
I just have a wifi network that I want to be hidden.
I configured my router so to hide my SSID and as I had the settings
for my wireless I can connect at it with no problem.
I just would like to know if there is a way to check that my wlan
is really not visible to other users.

If i type > sudo iwlist scan in my terminal
I can still see it.
How can I check if the "hidden" setting is working or not?
Cheers, -Luca

---

### Post by killa.fr0gg on 2010-12-01
Open a Friend object and query, "can you see any wireless networks with your web-enabled device?"

~peace on Earth

---

### Post by lucacerone on 2010-12-02
> **killa.fr0gg said:**
> Open a Friend object and query, "can you see any wireless networks with your web-enabled device?"

Yeah that's one way :) but I'd really like to know if there is a more technical one
Thanks in any case!

---

### Post by mattgyver83 on 2010-12-02
from the iwlist man pages about the 'scan' parameter:
>  With  some card/driver, this enables to see hidden networks

Its safe to say if Ubuntu's Network Manager does not 'see' the network but iwlist scan does, its hidden.  Wireless Network Detection suites such as Aircrack and Kismet as well probably have an option to locate this information.

---

### Post by lucacerone on 2010-12-02
> **mattgyver83 said:**
> 
Its safe to say if Ubuntu's Network Manager does not 'see' the network but iwlist scan does, its hidden.  Wireless Network Detection suites such as Aircrack and Kismet as well probably have an option to locate this information.
Thanks, my problem is that I'm not sure if Network Manager detects it
or simply just notifies that I'm connected to it.
So I removed my network settings, scanned for networks, and
as mine doesn't appear, I reconnected by "Connect to a Hidden network",
so that I know it is working.

I was just wondering if there is any tools that let you check this without
removing the settings of your wifi.

Cheers, -Luca

---


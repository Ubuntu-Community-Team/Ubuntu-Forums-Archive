---
title: "UFW Settings - need help"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by kingzones on 2012-04-05
[LEFT]Hello, This is my first post on Ubuntu forum..

I have installed the ubuntu system, and deny both incoming and outgoing ports loosing internet access.

Now I want access only for my firefox that I have installed separately from the firefox website not the one from the repositories. 

Now using Application Integration of UFW , I created a profile shown below:
[firefox]
title=firefox
description=firefox web browser
ports=80,443/tcp

and added 53 port to allowed list for DNS. and then allowed  firefox app profile outgoing connection. My final settings are shown below:

Status: active
Logging: on (full)
Default: deny (incoming), deny (outgoing)
New profiles: skip

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                                         Action                           From
--                                          ------                                ----
53                                    ALLOW OUT                          Anywhere
80,443/tcp (firefox)              ALLOW OUT                      Anywhere
53                                    ALLOW OUT                   Anywhere (v6)
80,443/tcp (firefox (v6)       )  ALLOW OUT                     Anywhere (v6)

Now, Firefox is able to access the internet, but all other applications are also able to access those open ports.

How to stop other applications from accessing the internet except firefox, installed at opt/firefox11/firefox


[/LEFT]

---


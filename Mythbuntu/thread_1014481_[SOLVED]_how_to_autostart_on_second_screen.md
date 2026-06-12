---
title: "[SOLVED] how to autostart on second screen"
date: 2008-12-17
forum: Mythbuntu
---

### Post by 4dognight on 2008-12-17
I have both my monitor and the TVout configured. When mythtv starts it starts up on my monitor. I want it to start on my TVout. It is configured as, 'to the right of'. What do I need to change in the autostart script?

---

### Post by 4dognight on 2008-12-18
There is an option on mythfrontend
 -display :0.1

This worked when I tried to start it manually, but would not work when I restarted X. I put the option in /etc/mythtv/session-settings, which gets sourced when mythtv starts with the --service option, as it does in the autostart file.

I got it to work by simply setting the DISPLAY variable in the start script for myth, /usr/bin/mythfrontend.

if [ "$1" = "--service" ]; then
    [COLOR="Red"]DISPLAY=:0.1[/COLOR]
    #source frontend session settings
    if [ -f /etc/mythtv/session-settings ]; then
        . /etc/mythtv/session-settings
    fi

I decided to offer $20 paypal for a fix. Oh, I just earned $20! ;-)

---


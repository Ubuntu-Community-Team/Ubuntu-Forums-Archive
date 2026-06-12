---
title: "LIRC with Multiple Applications"
date: 2009-09-12
forum: Multimedia Software
---

### Post by stderr on 2009-09-12
I'm trying to use LIRC for multiple applications simultaneously. E.g., I want to be able to use the STOP button to control Rhythmbox, then somehow switch to controlling Totem and use the same STOP button to control Totem. Has anybody managed something like this?

I tried to create a solution whereby the .lircrc file was modified upon pressing a button (switches between customised Rhythmbox and Totem versions) and then lircd rereads the .lircrc config file. First I tried using **/etc/init.d/lirc restart** to get it to reread .lircrc, which works, but the client apps don't automatically re-connect to lircd, so it's useless. Second, I tried **killall -HUP lircd**, which didn't seem to do a whole lot. 

However, I figure this method is hopeless anyway, since I think the client apps only read .lircrc on startup. 

Can anybody think of a solution other than writing plugins for all the client apps I want (Rhythmbox, Totem, VLC...) which either detect if the app is in the foreground, or rereads .lircrc on receiving a particular button signal? (I'd much rather not have a solution that depends on significant coding for each additional client app I want to control).

---

### Post by Spectre5 on 2009-11-13
> **stderr said:**
> I'm trying to use LIRC for multiple applications simultaneously. E.g., I want to be able to use the STOP button to control Rhythmbox, then somehow switch to controlling Totem and use the same STOP button to control Totem. Has anybody managed something like this?

I tried to create a solution whereby the .lircrc file was modified upon pressing a button (switches between customised Rhythmbox and Totem versions) and then lircd rereads the .lircrc config file. First I tried using **/etc/init.d/lirc restart** to get it to reread .lircrc, which works, but the client apps don't automatically re-connect to lircd, so it's useless. Second, I tried **killall -HUP lircd**, which didn't seem to do a whole lot. 

However, I figure this method is hopeless anyway, since I think the client apps only read .lircrc on startup. 

Can anybody think of a solution other than writing plugins for all the client apps I want (Rhythmbox, Totem, VLC...) which either detect if the app is in the foreground, or rereads .lircrc on receiving a particular button signal? (I'd much rather not have a solution that depends on significant coding for each additional client app I want to control).

Definitely an interesting idea - did you ever make anymore progress with this?

FYI - You can do this very easily using modes.  Read up about them at the lirc site.

---


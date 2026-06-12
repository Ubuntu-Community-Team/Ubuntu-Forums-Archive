---
title: "/dev/lirc0 gone after sleep / resume in jaunty"
date: 2009-08-27
forum: Multimedia Software
---

### Post by odx on 2009-08-27
Hello,
after some tinkering i found my problem with my media center is that the lirc device /dev/lirc0 which is initialized correctly at boot does not show up after sleep (and resume).
After resume i see a short kernel notice on the screen:

[ 91.054000 ] lirc_dev: lirc_register_plugin: minor (0) just registered!
* Stopping remote contron deamon(s): LIRC

I believe this is when my XBMC tries to reconnect to LIRC and lirdc quits when it finds /dev/lirc0 not present.

Now i am not sure when and how the lirc device is beeing initialized and how i can add reinitialization to the acpi scripts.


When i un- and replug the USB reciever i get the /dev/lirc0 back. But thats not the way to go since the USB plug is far insice my media desk.


I apreciate any ideas.

odx

---

### Post by pulpinator on 2009-09-02
My /dev/lirc0 just went away completely. It was working for a year, and then after a reboot it went away.

Any ideas on how to make it come back?

---


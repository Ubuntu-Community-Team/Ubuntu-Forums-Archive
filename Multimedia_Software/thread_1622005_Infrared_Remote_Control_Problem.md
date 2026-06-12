---
title: "Infrared Remote Control Problem"
date: 2010-11-14
forum: Multimedia Software
---

### Post by foxruns on 2010-11-14
i bought a cheap new infrared remote specifically because i read on its reviews that people were using it in linux without a hitch.. i am trying to use it to control banshee and thats it, i just want the pause and play button for when im not near the computer..the only thing working is the volume, ive tried setting up .conf files for it to work with lirc and i cant get it working. after trying a million things over the past 4 hours i managed to mess something up to where i cant get system-preferences-infrared remote to work.
if anyone has any ideas for help it would be very much appreciated im ready to throw my computer out the window

---

### Post by bogoliubov on 2010-11-15
I don't know what gconf has to do with this.

But I tried to get a remote working using the gnome gui to lirc, but it did not work. So I removed it, reinstalled lirc and then it worked!

It seems your remote does work, since at least some buttons behave as expected. You can test the other buttons using the irw command (in the terminal). If necessary, you can also use the irrecord command to see what codes a certain button sends, and then edit the config file for your remote (within lirc settings) to make that button work.

I'm sorry for not being too detailed, but it was a long time ago that I did all this, so I don't remember the details anymore.

Good luck!

---

### Post by foxruns on 2010-11-15
see my problem is that i must have done something more to it because now it wont open even if i uninstall then reinstall it..
and my problem in making a config file in the settings of the gui is that whenever i try, or tried, to do something it would say something like the remote wasnt responding..i cant test that anymore seeing as it wont open.. what i was trying to do was copy the config file i found on lirc's website that was supposed to be for my remote control to a document and save it in etc/lirc/something
i was kind of confused on that seeing as they dont tell you exactly where to save it they just give you a bunch of files
im so beyond lost.

---


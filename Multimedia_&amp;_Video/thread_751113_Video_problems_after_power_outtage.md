---
title: "Video problems after power outtage"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by BuntuFreak on 2008-04-10
Okay so I made a  bad situation impossible. I'll be as clear and brief as possible. 

There was a storm and then a power outage. I had a disk in my drive so computer did not reboot. I took the disk out of the drive and let the computer reboot. When I rebooted my display resolution was set to 17xx X yyyy. Don't remember the xx and yyyy. Thus, I could view all parts of the screen if I moved my mouse to the right and bottom extremities. Of course, this was hardly a good situation. When I tried to set my screen resolution back to 1440 X 900 - which was what I was running with prior to the power outage - the only options presented to me where the existiing resolution and 640x480. And this is when I royally messed things up.

I swiitched from Screen 1 to Screen 2.  There I saw all the resolution options I needed! Including 1440 x 900. So I changed Screen 2 to 1440 x 900. Of course, that did not change my screen resolution. The reason was Screen 2 was disabled. So I did - the now - unthinkable. I checked the radio button for "Default Screen". I was prompted my message saying "All users should log out for changes to take effect". So I logged out, logged back in and now my machine's hosed.

X-Server will not start. The diagnostic trace says the following lines that I hope are interesting. I'm having to manually type everything, so please bear with me.

[B][COLOR="Blue"](==) Log file: "/var/log/Xorg.0.log", Time: [...whatever...]
(==) Using config file: "/etc/X11/xorg.conf"
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(II) Module already built-in
(EE) Screen 0 deleted because of no matching configuration
(EE) Device(s) detected, but none match those in the config file.

Fatal Server error:
no screens found[/COLOR][/B]

I have a dual boot with Windows XP. So I guess I can boot in XP and go change some config files on the Ubuntu partition, if I only knew what to do. I spent so much time configuring AWN, etc. on my machine, it would be so bad to lose all the settings. Needless to say, right now, I just need my Ubuntu back. Simply can't go to XP, I've been spoilt senseless by Ubuntu.

Any help will be deeply appreciated.

Best.

---

### Post by tgalati4 on 2008-04-10
Sounds like the storm may have scrambled your computer's BIOS.  Have you tried removing the video card, cleaning it, and reseating it?  Also leave the computer unplugged for a while.  Take out the motherboard battery.  Let it sit for a few minutes, then put the battery back in and reboot.  You will have to reset the clock and some other BIOS settings--write them down somewhere.

---

### Post by BuntuFreak on 2008-04-10
No man, it's not any hardware problem.

As I said, I have it as a dual boot. I can boot into XP just fine. As I said, whatever settings I selected for Screen2 hosed it up.

Thanks.

---

### Post by BuntuFreak on 2008-04-10
Okay. So I was smart enough to have taken a backup of xorg.conf. I copied the backup onto that file. Presto, I can now boot into Ubuntu.

Now my AWN manager does not show. I see a "white bar" all along the bottom of my screen. I can actually click on this bar and launch applications :-) I just don't know what I'm launching.

Also, my Window title bars are gone. So I cannot move/close windows. I have to use File Exit to close applications.

So then I'm thinking, my AWN and Emerald settings are also in some configuration files. Hopefully if I could go and edit them, it will fix my problem. Anyone have any idea where I should get started?

Thanks in advance.

---


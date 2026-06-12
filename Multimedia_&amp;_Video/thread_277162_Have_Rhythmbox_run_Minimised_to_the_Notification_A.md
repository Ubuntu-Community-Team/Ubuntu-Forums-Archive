---
title: "Have Rhythmbox run Minimised to the Notification Area / System Tray on Startup"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by yishai on 2006-10-14
I run Rhythmbox as my default media/podcast client.

I'm keen to be able to have the program run (automatically) minimised to the notification area / system tray on startup (preferably with no splash screen and with no tab in the window list).

Any ideas?... Has anyone been able to achieve a similar result with another program? And if so, how so?

Thanks in advance.

---

### Post by doclivingston on 2006-10-16
Rhythmbox should remember that it was minimised to the tray if it's like that when you quit/logoff. You can also make it start up when you log in by using System->Preferences->Sessions, going to the Startup Programs tabs and entering "rhythmbox" after pressing add.

Having it start up automatically, and either quitting via the tray icon, or just logging off, might work.

---

### Post by yishai on 2006-10-17
Thanks for your reply doclivingston (thanks too, for your comments within the rhythmbox-devel mailing list re. the thread: 'Feature Requests & Bug Reports').

I had tried running the program through 'Sessions->Preferences->Startup'... just hadn't been able to get it to run minimised to the notification area. I took your advice though, and logged-off with rhythmbox still running minimised to the notification area (coupled with having again added rhythmbox to the startup list). The program ran on startup, however it still ran maximised. I suppose it is somewhat of a mystery that it would work on your system but not mine...

I also tried exiting the program through the menu in the notification area (and with the program minimised), to see if this might have an effect on its startup behaviour. To no avail.

---

### Post by yishai on 2006-10-17
I've just now become aware that I'm not running the latest version of Rhythmbox (0.9.3.1 is the latest version within synaptic, presumably based on the repositories I'm subscribed to / not subscribed to). I'll look into upgrading and perhaps this will have some bearing on things.

---

### Post by doclivingston on 2006-10-17
> **yishai said:**
> I've just now become aware that I'm not running the latest version of Rhythmbox (0.9.3.1 is the latest version within synaptic, presumably based on the repositories I'm subscribed to / not subscribed to). I'll look into upgrading and perhaps this will have some bearing on things.

Ah, I think we might have added support for doing what I suggested in 0.9.4 (or it might have been 0.9.5, I don't recall).

If you wanted to update, there is a 0.9.5 package (made by seb128, who does the official Ubuntu does) at [http://people.ubuntu.com/~seb128/rhythmbox-dapper/](http://people.ubuntu.com/~seb128/rhythmbox-dapper/). You could probably find references to 0.9.6 ones in various fortums threads too.

---

### Post by yishai on 2006-10-17
Thanks mate. I'll have a look at the 0.9.5 package and let you know how I get on.

---

### Post by yishai on 2006-10-19
Installing 0.9.5 seems to have done the trick (namely, if left running minimised to the notification area on shutdown, and having added the program to the startup utility, the program will load on startup minimised to the notification area). -- Thanks for your responses doclivingston.


I might look into installing 0.9.6, too. Off-hand, you wouldn't happen to know if a .deb file of 0.9.6 is being hosted publicly (as well as where I might be able to find a .deb file for 'gstreamer-plugins-good 0.10.4')?

---

### Post by raintheory on 2006-10-19
This is the 0.9.6 deb that I installed with no problems..

[http://mighmos.org/apt-repository/pool/r/rhythmbox_0.9.6-1mighmos1_i386.deb](http://mighmos.org/apt-repository/pool/r/rhythmbox_0.9.6-1mighmos1_i386.deb)

---

### Post by yishai on 2006-10-22
Thanks for that... seems to have installed well for me, too.

---


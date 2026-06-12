---
title: "Flash video stutters in Edgy"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by spaceghoti on 2006-10-26
I can rightly say it did this before, since I installed Dapper and immediately performed a dist-upgrade to Edgy Knot Three.  I then installed Automatix and pulled in all the neat multimedia software I would need.  Video on the hard drive runs normally, but flash video as in Google Video and YouTube stutter as though I'm watching stop-motion photography.  If I download the FLV files and play them under VLC there's no stutter.

I'm operating on an IBM T42 laptop with 2GB RAM and a 5Mb DSL connection.  I don't think it's my hardware, but I don't now where to begin to look.

Thank you in advance.

---

### Post by pressman57 on 2006-10-27
The only way I gat all that crap to disappear was to install Firefox for windows and run it under wine. I think there's a how-to written on it somewhere.

---

### Post by spaceghoti on 2006-10-30
Very odd.  I loaded the xubuntu-desktop package and ran Firefox under the GDM server.  The stutter issue has gone away, suggesting that the problem is inherent somewhere within the KDE desktop.  Now I just need to figure out why I'm getting uncontrolled key commands, like scrolling and tabbing through desktops.

---

### Post by spaceghoti on 2006-11-04
Xubuntu is fun enough, but I find that I still prefer KDE.  Does anyone have any suggestions on how I can fix my flash problems under KDE?

---

### Post by ADT on 2006-11-06
> I can rightly say it did this before, since I installed Dapper and immediately performed a dist-upgrade to Edgy Knot Three. I then installed Automatix and pulled in all the neat multimedia software I would need. Video on the hard drive runs normally, but flash video as in Google Video and YouTube stutter as though I'm watching stop-motion photography. If I download the FLV files and play them under VLC there's no stutter.

I'm operating on an IBM T42 laptop with 2GB RAM and a 5Mb DSL connection. I don't think it's my hardware, but I don't now where to begin to look.

Thank you in advance.
Reply With Quote

I had the exact same problem with flash video. The way I fixed it was to install the Flash Player 9 Beta plug-in.
The steps to do this are here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")
You do not have to delete your previous version of flash-mozilla plug-in.
I haven't had any problems with it so far. Hopefully it will work.

regards

---

### Post by spaceghoti on 2006-11-07
Sweet!  That seems to have done the trick, thank you!

---


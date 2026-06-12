---
title: "Adding new city to the weather module"
date: 2007-12-29
forum: Mythbuntu
---

### Post by drkm_4_frm on 2007-12-29
Hi,

I dont find my city "rockford, IL, US" ( I may be blind but...) in the weather module's cities list. So i'm just wondering how to add my city to the list.

Do i have the option of adding my pincode like what i do in weather.com or can i add my city directly???  

Does any body know how to do that???

Help please!!

---

### Post by drkm_4_frm on 2007-12-29
I'm really sorry! I could actually find my city in the list!

---

### Post by linuxwizard on 2007-12-29
Are you talking about the Weather Report applet for your Gnome panel ? If so Rockford, IL. is listed, I live there also.

---

### Post by Lido on 2008-01-01
I had trouble getting the weather feature working, but it turned out to be a networking issue. I got it working, but I don't know if the fix will remain fixed after reboot.

---

### Post by Nimda1000 on 2008-01-05
So how do you add a city to the weather listing?

I am in Lindsay Ontario Canada and just about every weather listing service/application I have used has Lindsay except for MythTV's weather module.

It would be nice to see my actual city instead of having to choose Peterborough orToronto that are near me.

Nim

---

### Post by Nimda1000 on 2008-01-14
anyone?

---

### Post by clakomy on 2008-06-17
Okay, I figured it out and it is working. The file you need to modify is
/usr/share/libgweather/Locations.xml. Make sure you make a copy of it first just in case.

1 - Do a search on Google: "yourcity yourstate coordinates"
2 - sudo gedit /usr/share/libgweather/Locations.xml
3 - Search for a city in your area or state that is not that common (not Springfield!) so that you can do a find and replace with your city name.
4 - Find and replace to update that city to have your city's name.
5 - Scroll down to the bottom of city section. (sections starts with <location> and end with </location>).
6 - At the bottom of that section you will see the coordinate for the old city. Using the same format, put in the coordinates you found via Google.
7 - Save it and update the applet and then change the location.
8 - If you did it right, your city will show up and the update will work.
9 - If it doesn't work, play with the coordinates.
10 - ** You could copy and paste a new city location rather than replacing an old one. However, after you see the file, you'll know why I went with replace.
11 - ** If you live in the US, you can go to [http://www.htl-weather.com/](http://www.htl-weather.com/) to gather all of the variables you will need for your city (coordinates, code for airport, and zone for regional forecast "I think it is in that order").

Have fun!
clakomy

---


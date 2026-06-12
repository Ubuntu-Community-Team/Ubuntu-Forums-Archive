---
title: "xbox live ics problem"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by christopher.mountford on 2009-11-23
I have tried many different way to connect my Xbox 360 to Xbox live using a shared connection via my ubuntu laptop but I cant seem to get access.
I would be very grateful if anyone could help me with this problem.^^

Details of my setup:
-My laptop has an internal Wi-Fi card which I am using as the internet connection.
-My laptop is running the karmic (9.10) version of ubuntu with both the xfce and gnome interfaces installed.
-My Xbox 360 is running dashboard 2.0.8507.0
-I am connecting both machines together using a crossover cable


If you need anymore information about my setup please ask.

---

### Post by ArrrghJ on 2009-12-26
I literally twenty seconds ago got mine to connect, but only with a Moderate NAT.

1. Right click the internet connection on the panel.
2. Go to edit connections
3. Go under the wired tab and select your ethernet port (Mine is eth0, for example), and click Edit.
4. Check the "connect automatically" box.
5. Under IPv4 Settings, click on the Method drop box and set it to "Shared to other computers" then Apply the settings.
6. Go to your Wireless tab, select the name of the router you connect to, and click "edit."
7. Under IPv4, select "shared to other computers" as the connection method.

That's it.

I've been able to get online, but like I said, it's a moderate NAT.

---

### Post by ArrrghJ on 2009-12-26
Actually, just found this thread.. way easier than what I did.

[http://ubuntuforums.org/showthread.php?t=1183420](http://ubuntuforums.org/showthread.php?t=1183420)

just make sure you click your "auto eth0" on your network icon in the panel

---


---
title: "Network Settings Gone After Upgrade"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by hp-p00nst3r on 2009-06-07
As I was trying to upgrade my installation of 8.04 to 9.04, I was using an internet connection that was connected to my Vista laptop.  On that laptop, I had configured a network bridge.  My laptop would get internet via wifi and share that connection via wired connection to the ubuntu computer.  It worked fine until I upgraded to 8.10.  I noticed that all my network settings are gone and I cannot connect back onto the internet.  I do not know how to put the settings that I had on before.  The network settings window seems to be different, and I dont know what settings to use anymore.  How can I fix this?

before there were two connections already showing in the list.  All I remember doing is going into one of them and changing the setting to Automatic.  In 8.10, I don't know where that menu has gone and I have no idea what settings to use when I click the add wired connection button.

**i dont know if there is other info you need like system specs or anything like that, but i can give it if you need it

---

### Post by Iowan on 2009-06-07
> **hp-p00nst3r said:**
> As I was trying to upgrade my installation of 8.04 to [COLOR="Red"]9.04[/COLOR]...
It worked fine until I upgraded to [COLOR="Red"]8.10[/COLOR]...
In [COLOR="Red"]8.10[/COLOR], I don't know where that menu has gone and I have no idea what settings to use when I click the add wired connection button.Upgrading to Intrepid (8.10) or Jaunty (9.04)?  I skipped Hardy and Intrepid for desktops, but have Jaunty on a laptop. In Jaunty, the information is available either via applet in top right corner, or by System>Preferences>Network Connections.

---

### Post by hp-p00nst3r on 2009-06-07
Yeah, I know where to input the settings, but I don't know what to put in there anymore.

---

### Post by superprash2003 on 2009-06-08
you could try the following settings , these are most common settings
ip address - 192.168.1.10
subnet - 255.255.255.0
gateway - 192.1268.1.1

DNS
1)208.67.222.222
2)208.67.220.220

OR

ip address - 192.168.0.10
subnet - 255.255.255.0
gateway - 192.1268.0.1

DNS
1)208.67.222.222
2)208.67.220.220

---

### Post by hp-p00nst3r on 2009-06-08
heh
gave up on that
jsut went with a reinstall straight to jaunty

---

### Post by Iowan on 2009-06-08
> **hp-p00nst3r said:**
> In 8.10, I don't know where that menu has gone ... Sorry - sounded like you were missing the "where".
Is the Jaunty install working?

---

### Post by hp-p00nst3r on 2009-06-08
After installing Jaunty, it was able to detect my network card and automatically configure the settings.  So in short, it worked right after install!

---


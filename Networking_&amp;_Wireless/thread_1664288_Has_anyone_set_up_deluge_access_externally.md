---
title: "Has anyone set up deluge access externally?"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by peter_parker on 2011-01-10
Hi guys,

I just set up deluge on my of my old boxes running ubuntu server 10.10.

I'm trying to set up access to my deluge site from any where i travel (outside my network)

im not sure if im setting my port forwarding correctly on my router as i can't seem to access from out side my network.

i selected start and end ports to what i gave to deluge...

---

### Post by PatchesTheCaveman on 2011-01-11
Are you sure you set it to the WebUI listening port and not the BitTorrent communication port?  You can check in the ~/.config/deluge/web.conf file or the WebUI section of the Preferences window if you installed the GUI.  The default appears to be 8112.

Did you open the firewall for that port?  Try
```
sudo ufw allow 9092
```

If not, your IP address might be changing on you.  Did you set up Dynamic DNS in your router?  Or do you have a static IP address?

ETA:  you'll need to forward the BitTorrent communication port too for uploading to work

---

### Post by peter_parker on 2011-01-15
Hey,

i have dynamic IP set up.  And obtain DNS from ISP set up.

I ran sudo ufw allow 9092 (rules updated)

Checked  /etc/init.d/deluge-daemon and the line has 9092

DAEMON2_ARGS="-p 9092 -c /var/lib/deluge -l /var/log/deluge-web.log -L warning"

Also made the change in /var/lib/deluge/web.conf to 9092

Although in the web interface.  under Preferences and Interface.  The server port was pointing to 8112.

I had to enter in 9092 manually and applied.

BUT. i am still unable to access outside of my network...

---


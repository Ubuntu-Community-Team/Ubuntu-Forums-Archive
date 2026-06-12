---
title: "Network Connections is Broken"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by popejeremy on 2011-12-05
Hi! I recently tried to hook up to a new WiFi network and wasn't able to. I found the SSID in the dropdown menu and clicked on it, but it never gave me the dialog box to enter the password.

Then I opened up the Network Connections app and found that Edit and Delete is greyed out for every Wifi connection on the list. And when I click Add, all the boxes in those dialog boxes are greyed out too.

Long story short: Network Connections is borked and I don't know how to fix it. Any clues? Thanks!

---

### Post by praseodym on 2011-12-05
Try to start the applet from the terminal:

```
gksu nm-connection-editor
```

---

### Post by popejeremy on 2011-12-05
Starting the applet from the command line works! So now what? I don't want to start it from the command line every time, and it doesn't solve the initial problem of not prompting for a password when a new network is joined.

---

### Post by praseodym on 2011-12-05
Is the applet checkboxed in "autostart"?

---

### Post by popejeremy on 2011-12-05
When I look at Startup Application Preferences, it is not on the list at all. When I try to drag and drop it into the Startup window, it fails.

I just added it manually and rebooted. On startup, I'm prompted for my password for the sudo, the application opens and works. Then when I close that window and try to open it again from Edit Connections, it's the same old story: not working.

---

### Post by popejeremy on 2011-12-05
Also, now for the second time today, Gmail told me to delete all my cookies because there was a cookie mismatch. Something is really wrong somewhere.

---


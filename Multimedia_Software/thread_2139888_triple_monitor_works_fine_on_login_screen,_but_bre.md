---
title: "triple monitor works fine on login screen, but breaks upon login (13.04)"
date: 2013-04-28
forum: Multimedia Software
---

### Post by webgoddess on 2013-04-28
I have three monitors, two DVI and one HDMI.  I have a GeForce GTX 660 with nvidia driver 313.30.

On the login screen the three monitors work fine.  So I don't think anything is wrong with the xorg.conf file:

[http://pastebin.com/QdyBjh1w](http://pastebin.com/QdyBjh1w)

Once I log in, however, the second monitor gets cloned on the third monitor.  The only way to fix it is by launching nvidia-settings and setting up the monitors again.  Works fine after I apply the settings.

in the nvidia settings, the first monitor is labeled DPF-0 (DVI), the second (HDMI) DPF-1, and the third (DVI) DPF-3:

[http://i.imgur.com/amXoXa5.png](http://i.imgur.com/amXoXa5.png)

These settings are correct.

However under settings/Display it is completely wrong:

[http://i.imgur.com/oPDfCNV.png](http://i.imgur.com/oPDfCNV.png)

The first monitor is detected as "digital display", set Left of "ViewSonic Corp"

The second monitor is detected as "ViewSonic Corp" but is actually the "Ancor Communications" monitor, set Right of "Digital Display"

The third monitor is detected as "Ancor Communications" but is actually the "Viewsonic Corp", also set Right of "Digital Display".

Somehow, in the process of logging into the system, whatever controls Settings/Display is reading the wrong information, and overriding the correct nvidia-settings configuration.

The triple monitor used to work just fine, on 12.10, but for unknown reasons it stopped working, probably because of some ubuntu update.  I tried to fix this by updating to the latest nvidia drivers, and i'm now having significant tearing when playing videos on VLC, which is yet another frustrating issue related to video drivers.

Everything still works great on windows 7 (via dual boot), and used to work great on Xubuntu.  I was hoping 13.04 would fix the problem, but it didn't make a difference.

I have no idea how to correct this issue.  Please help.

---

### Post by webgoddess on 2013-04-28
i was able to solve the problem by using [arandr]("http://christian.amsuess.com/tools/arandr/"), adding a sleep to the shell script, and adding it to the startup applications.

---


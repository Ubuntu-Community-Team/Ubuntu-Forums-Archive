---
title: "Fixing HP f1503 monitor refresh rate"
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by eztigma on 2005-12-22
When I tried the 5.06 live cd I found that my f1503 monitor was moving the screen a bit to the right. This happened before on Fedora Core and was fixed simply when changing the refresh rate of the monitor to 70 hz. In Ubuntu this is NOT possible because it only recognizes one refresh rate, that is 60 hz.

I found out a way to fix this and make the screen look OK on 5.10 (but it should work in earlier versions too). Open a new terminal and type the following:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

in the xorg.conf document find: Section "Monitor", find the HorizSync and VertRefresh and change them for 30.0-63.0 and 56.0-76.0, respectively.

It should look a little bit like this:

```

Section "Monitor"
     Identifier "Generic Monitor"
     Option "DPMS"
     HorizSync: 30.0 - 63.0
     VertRefresh: 56.0 - 76.0
EndSection

```

Save the file and restart x by pressing ctrl alt and backspace, if it takes you to a command prompt just log in and type startx, now you should be able to select 70 hz from the screen resolution applet.

I hope this is useful for anyone because I wasn't able to find any of this on the Internet before and I'd appreciate any feedback. :KS

---


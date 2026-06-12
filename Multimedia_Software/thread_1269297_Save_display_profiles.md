---
title: "Save display profiles?"
date: 2009-09-18
forum: Multimedia Software
---

### Post by brad_richards on 2009-09-18
I have a laptop (Ubuntu 9.04) that I use at my desk - attached to a docking station and monitor - and that I also use for presentations. The presentations are in rooms with fixed projectors, and the projectors are different models.

The problem: almost every time I move the laptop, I have to manually adjust the display settings. Sometimes this gets really exciting: Ubuntu insists it has to adjust the virtual display settings and I have to log out and log back in. Usually twice.

Is there some practical way to create a display profile for each situation, and to tell Ubuntu "I am in room X, use these settings"?

---

### Post by brad_richards on 2009-09-19
bump. Does anyone else have such a problem? Any ideas?

---

### Post by brad_richards on 2009-09-22
Here is the best answer I've come up with - perhaps this will be of help to others.

1. Determine the highest resolution of any external monitor or projector that you will ever use. Remember that you can set the resolution in the display properties, so you don't necessarily need to know the native resolution.

2. Decide where to place the monitor/projector relative to your laptop screen (in the display settings). For example, I place the laptop screen on the left and the external display on the right. Always use the same position!

3. Calculate the required virtual resolution. In my case, with the screens side-by-side, this means adding their horizontal resolutions and taking the maximum vertical resolution. Do not make the virtual resolution unnecessarily large (I did, by accident, and both screens remained totally blank).

4. Edit /etc/X11/xorg.conf to use the virtual resolution you calculated. Log out and log back in, so that the new xorg.conf takes effect. Here is the relevant section of the xorg.conf file:

```
Section "Screen"
  Identifier "Default Screen"
  Monitor    "Configured Monitor"
  Device     "Configured Video Device"
  SubSection "Display"
    Virtual 3120 1050
  EndSubSection
EndSection
```Now, every time you are about to make a presentation, or otherwise attach to an external monitor or projector:

1. Boot the system and log in (*before *attaching the external monitor/projector).

2. Plug in the external monitor/projector.

3. Open the display properties, turn the display on and set its resolution. *Be sure to position the display as planned above* (sometimes it jumps to some totally random spot). If you are ever again prompted to let Ubuntu adjust your virtual resolution, click no, and check this.

4. Apply the changes in the display-properties dialog.

This isn't quite as easy as it ought to be, but basically seems to work.

One last tip, for anyone using OpenOffice to make the presentations: OpenOffice appears to store information about the available displays at start-up. Hence, do not start OpenOffice until *after *adjusting the display properties.

---


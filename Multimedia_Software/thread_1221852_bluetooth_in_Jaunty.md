---
title: "bluetooth in Jaunty"
date: 2009-07-24
forum: Multimedia Software
---

### Post by raymondvillain on 2009-07-24
How does one start up bluetooth headphones in Jaunty?  The bluetooth icon is present on my taskbar, but I don't know how to get my headphones to pair.  If I select "setup new device", a wizard launches but their my headphones are not on the list from which to choose a device.  In fact, nothing is.

I need to pair the headphones so I can select the "default sink" in pulseaudio device chooser.

---

### Post by ohzopants on 2009-07-24
Are your headphones already paired to another device?
Is there a "sync" (or something similar) button on them?  You may have to press this button before your computer will find them.

---

### Post by martinbaselier on 2009-07-24
for better bluetooth control, I would advice blueman

you can install it like this in a terminal:
```

echo deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main | sudo tee >> /etc/apt/sources.list
sudo apt-get udpate && sudo apt-get install blueman

```
I do not have a bluetooth headset, but with other bluetoothdevices I have more option than by using the orignal applet. For pairing do you need a certain code?

---

### Post by cgb on 2009-07-24
There probably is a pairing mode setting on your headset in which you need to hold a button down for 30 seconds or something like that for it to be discoverable by your computer.  Until your device is set to discoverable it will not be found.  If you had already set to discover then their is another issue going on.

---


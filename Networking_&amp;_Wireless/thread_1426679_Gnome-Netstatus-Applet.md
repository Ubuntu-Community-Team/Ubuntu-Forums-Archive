---
title: "Gnome-Netstatus-Applet"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-03-10
I can't seem to locate it anywhere. I installed and reinstalled.

---

### Post by leopards on 2010-05-07
> **Silvertones said:**
> I can't seem to locate it anywhere. I installed and reinstalled.

 Re: On line indicator
Audiomick made a good guess.

It is now a package (wasn't in previous releases) called "gnome-netstatus-applet" and you have to install it for it to show up in "Add to Panel". It should be in Synaptic under packages NOT installed (and again it's named "gnome-netstatus-applet")

And there's a nuance to this. Once you install it, it still won't show up until you reboot (or you could do a killall command on gnome-panel, but I'm not sure of the syntax for that command, so I do a reboot).

Once you reboot, it should show up and then you can add it as you wish.

That should do it. I tested the method by removing it from the panel and then uninstalling it. I then reinstalled it, rebooted, and it showed up (I put it back where I had it).

Am curious to know if it is in your Synaptic Package Manager . . . it should be . . . so post back and let us know.

---

### Post by pesarak on 2011-06-10
thank you.
i install gnome-netstatus-applet from synaptic packet manager , after half an hour search in applications menu , i restart and found in "add to panel' as you say.

but still another question i have that if i want to run an applet program like
gnome-netstatus-applet or 'nm-applet'(network manager) is there alternate way ?
if i want to run such a application what command i should run or where it installed?
thank in advance.

---


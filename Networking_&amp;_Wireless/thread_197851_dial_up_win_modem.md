---
title: "dial up win modem"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by abdul wahed on 2006-06-16
i have acer 4003 lab with dial-up modem Intel 82821DB/DBL/DBM
i install package sl-modem-daemon and ubuntu recognize my modem automatically under /dev/modem i configure ppp connection and activate it but my modem still not working and no connection alive
need help

---

### Post by zxee on 2006-06-16
How did you configure dial up and what tool/application are you using to connect with? Try using pppconfig from a shell, and then modem monitor to connect. Hope that helps.

---

### Post by abdul wahed on 2006-06-16
thanks iam using pppconfig then i add modem monitor to the panel but its gives me not connected

---

### Post by mpvano on 2006-06-16
If you really have an Intel modem, here are a few things to try. If you actually have a "winmodem" ignore the rest of this message - it WON'T help you.

The intel motherboard modem in my ibm notebook is the same hardware partnumber as you listed and works great....

Try opening a terminal window and using the "tail /var/log/messages -f" command to watch the connection progress. This may tell you more about what's failing. If you get a "connected" line in the log, then the modem is probably working but your ppp configuration may be wrong.

Sometimes you need to configure the dialer to ignore dialtone (if it has such a setting).

If nothing at all is happening, you should make sure that the modem daemon is actually being loaded. (It's not installed by default - you did install the package named "sl-modem-daemon" from the synaptics program, didn't you?). The daemon program is actually what loads the driver and dials for it when needed.

You should also check the settings in the file /etc/default/slmodem-daemon to make sure you have the daemon enabled.

In most cases you do NOT need to build the modem from source - the driver is already installed in both dapper and breezy (but you DO need to install the daemon as described above). If you did build the driver from source, you may have done it improperly...

Depending on which driver got used, your modem may actually have an alsa mixer setting that needs to be set correctly for dialing to work. Try browsing your gnome volume control. Look in the menu File:change device to see if there's an entry for your modem. Mine lists the intel modem as a device.

The gnome volume control doesn't always disclose all the settings possible. Once you choose the modem, you need to open the preferences (from the Edit:Preferences menu) and check ALL the preference boxes to disclose all the controls. In some cases the off hook switch in the mixer needs to be set for the modem to work - normally this shouldn't be done because if it's not needed, it may take the modem off hook!

hope this helps,

All the above information applies ONLY to intel and lucent hardware. I have no idea what you need to do to get any other kind of software based modem to work. The above works great in my IBM T30 with intel modem hardware and in my old IBM 1400 with lucent modem hardware (but the slow celeron in the antique 1400 makes the connection less reliable when the line gets noisy)....

good luck

Mario

---


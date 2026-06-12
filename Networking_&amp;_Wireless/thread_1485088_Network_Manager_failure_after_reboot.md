---
title: "Network Manager failure after reboot"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by dallingham on 2010-05-16
I have a new system76 pangolin that came with 10.04 installed. NetworkManager has been working fine for several days. After a reboot today, the nm-applet no longer displays, and I can no longer connect to a wireless network. I have been able to restore internet access on the wired connection by editing the /etc/network/interfaces file. 

NetworkManager is running, and doesn't seem to be giving any error messages. Syslog shows:

syslog.1:May 16 10:09:26 gromit NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
syslog.1:May 16 10:09:26 gromit NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
syslog.1:May 16 10:09:26 gromit NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
syslog.1:May 16 10:09:26 gromit NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
syslog.1:May 16 10:09:26 gromit NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0

nm-applet refuses to display, so I cannot connect to any wireless APs.
Killing nm-applet and restarting it displays:
dona@gromit:/var/log$ pkill nm-applet
dona@gromit:/var/log$ nm-applet
** (nm-applet:2965): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2965): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2965): DEBUG: foo_client_state_changed_cb
** (nm-applet:2965): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:2965): DEBUG: going for offline with icon: notification-network-disconnected


But still, nothing displays. The card is alive. iwconfig reports:

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Any help would be greatly appreciated. 
Thanks.

---

### Post by foresthill on 2010-05-16
I know there is a command that will rebuild your panel and applets, but I don't know what it is offhand.

One temporary solution might be to create another account and see if the applet comes up when you log into that.

---

### Post by dallingham on 2010-05-16
Logging as another user works. The other user has the nm-applet in the panel, and I can connect to the access point.

I tried deleting the .gconf and .gconfd directories to try to restore the panel to an initial state. Apparently this wasn't the right thing to do. I  get a clean panel, but nm-applet does not display. Checking ps, nm-applet is running. If I kill it, and start a new copy, it still does not display.

---

### Post by dallingham on 2010-05-16
Deleting the panel and creating a new panel seems to have solved the problem. I did the following:

```

gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by foresthill on 2010-05-16
Let me know if you figure out how to fix this. I had my power icon disappear, so that the only way I could log out was to hit control alt delete and then reboot. So I fixed that problem and now my sound applet is gone and I can't adjust my volume.

The Gnome panel in 10.4 is clearly screwed up, and I hope the devs can fix it soon.

EDIT: Thanks, I'll try this.

---

### Post by foresthill on 2010-05-16
Hey that worked, thanks! :guitar:

I will have to keep those commands handy for the next time this happens.

---

### Post by Beetroot Dog on 2010-05-17
> **dallingham said:**
> Deleting the panel and creating a new panel seems to have solved the problem. I did the following:

```

gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

Thank you :)

---


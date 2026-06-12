---
title: "Tethering on AT&amp;T with v3xx"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by FolsomBlue on 2009-11-08
I have a Motorola v3xx, and I have had good luck tethering via USB on ubuntu versions 9.04 and earlier.  I upgraged to 9.10, and I cannot tether anymore.  I go through all the steps in network manager, but when I try to connect, the connection fails.

Here are some entries in the syslog when I try to connect:

```
Nov  8 12:35:23 laptop modem-manager: (ttyACM0) opening serial device...
Nov  8 12:35:23 laptop modem-manager: Got failure code 100: Unknown error
Nov  8 12:35:23 laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Unknown error
Nov  8 12:35:23 laptop NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 (reason 1)
Nov  8 12:35:23 laptop NetworkManager: <info>  Marking connection 'AT&T MEdia Net' invalid.
Nov  8 12:35:23 laptop NetworkManager: <info>  Activation (ttyACM0) failed.
Nov  8 12:35:23 laptop NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 (reason 0)
Nov  8 12:35:23 laptop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0).
Nov  8 12:35:23 laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Nov  8 12:35:23 laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Nov  8 12:35:23 laptop modem-manager: (ttyACM0) closing serial device...
```Has anyone else seen this?

---

### Post by FolsomBlue on 2009-11-09
I got tethering working with wvdial and GNOME-PPP.  Is there a way I can debug networkmanager so I can see what the error is?  I don't see anything apparent in the log files.

---

### Post by kennethmsmith on 2009-11-10
can you describe how you got this working.  I also had tethering working with V3xx under 9.04, but can't seem to get it working under Ubuntu Netbook Remix 9.10.  Thanks.

---

### Post by FolsomBlue on 2009-11-10
1.  Install gnome-ppp.  I don't remember how I did it, maybe "sudo apt-get install gnome-ppp" in a terminal.

2.  Run gnome-ppp from the pulldown applications-internet-gnome ppp and then fill in the following:

username:  [EMAIL="WAP@CINGULARGPRS.COM"]WAP@CINGULARGPRS.COM[/EMAIL]
password: CINGULAR1
phone number:  *99#

3.  Go into setup and change the following:

device:  /dev/ttyACM0  (if you look at the system logs you can see where the phone is, also type it in if it is not in the pulldown list)
type:  USB modem
speed:  i have it at 460800, I don't think it matters

init strings:  I have init 2 set to AT+CGDCONT=1,"IP","WAP.CINGULAR"
options tab:  I only have the following checked:  Abort connecting if no dialtone, check default route, ignore terminal strings (stupid mode)

---

### Post by kennethmsmith on 2009-11-10
this won't disturb any wired or wireless (wifi) settings or drivers will it?  I don't want to mess up my wifi access in an effort to get my mobile tethered access working.

thanks
Ken

---

### Post by FolsomBlue on 2009-11-10
I don't think gnome-ppp is connected to network manager.  I can still use my wifi and wired ethernet with gnome-ppp installed.

---

### Post by kennethmsmith on 2009-11-10
thanks.. I'll give this a try tonight.  I'll post back here how things turn out for me.

---

### Post by kennethmsmith on 2009-11-10
just a note.... i noticed today that when using network manager using the default settings for att wap.cingular that it puts the password and stuff in.  I know that from before I would have to clear the password and login for the connection to work, but when trying that now in 9.10 it doesn't seem to let the password be taken out.  it just keeps repopulating the password.  That may be why the connection won't work.

---

### Post by kennethmsmith on 2009-11-11
got it working.. but had to change my user - group settings to allow connection throught modem.  otherwise it only wanted to work in root mode.

thanks for your help in getting this working.

---


---
title: "Disabling networking as a normal user?"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-04-12
Is there a way I can forcibly disable networking as a non-root user?  I want to be able to make a script with the capability to turn off all networking on my computer, but I don't want to have to run it as root.

---

### Post by Stonecold1995 on 2013-04-16
bump

---

### Post by SeijiSensei on 2013-04-16
I don't think so, no.  You'd need to take down the interfaces with commands like "ifconfig eth0 down" and those require root privileges.

The reason for this is obvious, once you recall that Linux is multi-user.  Letting an individual user bring down the network would crash any other users' sessions that were using networking.

---

### Post by Cheesemill on 2013-04-16
How about pulling out the ethernet cable and turning off the wireless with its hardware switch :)

---

### Post by SeijiSensei on 2013-04-16
That must be the part in the script that controls the robotic hand!

---

### Post by Stonecold1995 on 2013-04-18
> **SeijiSensei said:**
> I don't think so, no.  You'd need to take down the interfaces with commands like "ifconfig eth0 down" and those require root privileges.

The reason for this is obvious, once you recall that Linux is multi-user.  Letting an individual user bring down the network would crash any other users' sessions that were using networking.
I'm sure there's a way.  I can disable wireless simply by clicking on the red (X) or uncheck the checkboxes [here]("http://www.pictureshack.us/images/66350_screenshot4.png"), and I'm pretty sure that GUI runs as a normal user yet is still able to "ask" the process running as root (NetworkManager) to disable networking.  So why can't my script "ask" NetworkManager to bring down the network just as the GUI does?  Theoretically I could even write a script that would move my mouse to the icon and disable networking as if I were doing it myself, and that wouldn't require root (not that it would be practical to do though).

Maybe using qdbus?

---

### Post by steeldriver on 2013-04-18
Yes you could try qdbus or even dbus-send, I can get wireless to disable/enable that way but the overall networking enable doesn't seem to allow it i.e.

```

$ dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager \
/org/freedesktop/NetworkManager \
org.freedesktop.DBus.Properties.Set string:"org.freedesktop.NetworkManager" **string:"WirelessEnabled" variant:boolean:false**
method return sender=:1.3 -> dest=:1.251 reply_serial=2
```

(and it works) but

```
$ dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager \
/org/freedesktop/NetworkManager \
org.freedesktop.DBus.Properties.Set string:"org.freedesktop.NetworkManager" **string:"NetworkingEnabled" variant:boolean:false**
Error org.freedesktop.DBus.Error.AccessDenied: Property "NetworkingEnabled" of interface "org.freedesktop.NetworkManager" is not settable

```

You *may* need to look at modifying the polkit-1 rules to make it work the way you want

---

### Post by SeijiSensei on 2013-04-18
> **Stonecold1995 said:**
> I'm sure there's a way.  I can disable wireless simply by clicking on the red (X) or uncheck the checkboxes [here]("http://www.pictureshack.us/images/66350_screenshot4.png"), and I'm pretty sure that GUI runs as a normal user yet is still able to "ask" the process running as root (NetworkManager) to disable networking. 

You know, I never really thought about that, though I have certainly turned wifi and wired networking off and on as an ordinary user with NetworkManager.  I think the first or second time I used that ability I wondered about its security implications, but then I soon forgot about it.

---

### Post by Stonecold1995 on 2013-04-18
> **steeldriver said:**
> Yes you could try qdbus or even dbus-send, I can get wireless to disable/enable that way but the overall networking enable doesn't seem to allow it i.e.

```

$ dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager \
/org/freedesktop/NetworkManager \
org.freedesktop.DBus.Properties.Set string:"org.freedesktop.NetworkManager" **string:"WirelessEnabled" variant:boolean:false**
method return sender=:1.3 -> dest=:1.251 reply_serial=2
```

(and it works) but

```
$ dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager \
/org/freedesktop/NetworkManager \
org.freedesktop.DBus.Properties.Set string:"org.freedesktop.NetworkManager" **string:"NetworkingEnabled" variant:boolean:false**
Error org.freedesktop.DBus.Error.AccessDenied: Property "NetworkingEnabled" of interface "org.freedesktop.NetworkManager" is not settable

```

You *may* need to look at modifying the polkit-1 rules to make it work the way you want

I don't really understand all this.  My knowledge of qdbus is limited to setting/reading klipper contents, controling plasma-desktop, and related.

How do I modify polkit-1 rules?

> **SeijiSensei said:**
> You know, I never really thought about that, though I have certainly turned wifi and wired networking off and on as an ordinary user with NetworkManager. I think the first or second time I used that ability I wondered about its security implications, but then I soon forgot about it.
I doubt there are many security implications in relation to networking.  Same goes with the ability to shutdown and reboot (actions which are normally only available to root), etc.  The real issue is the ability to access the keyboard, display, etc without root making keylogging easy.

---

### Post by steeldriver on 2013-04-18
> **Stonecold1995 said:**
> I don't really understand all this

Well I *certainly *don't - I've played with dbus a little (using dbus-send / dbus-monitor and some python) but I'm still waiting for the 'Aha!' moment. Right now it's all looks like the API was dreamed up by the Department of Redundancy Department - to make matters worse most of the documentation that I've found so far appears to be incomplete and/or out of date. 

Did you try just pasting in the 1st dbus-send command to see if it works for you?

> **Stonecold1995 said:**
> How do I modify polkit-1 rules? 

It's all XML iirc - I *almost* played with the network-manager bits at one point (trying to work around the 'non privileged user can't connect to a new network' issue) but decided against messing with it. I *think* the right way to do it is to create a custom rules file in /etc/polkit-1/localauthority/ however I've seen threads where people edit the file(s) in /usr/share/polkit-1 directly. Don't quote me though.



EDIT: ... FINALLY figured out the dbus interface to disable / enable ALL networking not just wireless (equivalent to the nm-applet Enable Networking check item) - it's the org.freedesktop.NetworkManager interface instead of the org.freedesktop.DBus.Properties interface:

```
dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager **org.freedesktop.NetworkManager.Enable** **boolean:false**
```

The *--type=method_call* seems to be optional

---

### Post by Stonecold1995 on 2013-04-19
> **steeldriver said:**
> EDIT: ... FINALLY figured out the dbus interface to disable / enable ALL networking not just wireless (equivalent to the nm-applet Enable Networking check item) - it's the org.freedesktop.NetworkManager interface instead of the org.freedesktop.DBus.Properties interface:

```
dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager **org.freedesktop.NetworkManager.Enable** **boolean:false**
```

The *--type=method_call* seems to be optional
This works, thanks.

How likely is this to fail?  The reason I need this is to bring down my network within 30 seconds of my VPN accidentally disconnecting, and I want the script to have an almost 0% chance of failing to disable networking.  I'm thinking, if this ever fails, to have the script detect that and run something like "kill -9 -1" as a last resort.

---

### Post by Stonecold1995 on 2013-05-02
What dbus command would I run to check if the network is enabled or not?

---

### Post by steeldriver on 2013-05-02
try

```

dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"NetworkingEnabled"

```

or for wireless specifically
```

dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"WirelessEnabled"

```

---

### Post by Stonecold1995 on 2013-05-03
> **steeldriver said:**
> try

```

dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"NetworkingEnabled"

```

or for wireless specifically
```

dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"WirelessEnabled"

```
If I remove the "--print-reply" will it return true if networking is on, false if it's off?

---

### Post by steeldriver on 2013-05-03
I think it just returns nothing if you omit the --print-reply (useful when you're making Set commands - not so much for Gets)

If you want to do more elegant stuff with dbus I suggest you look at the python API

OTOH if you just need a quick connectivity check then the output of nmcli is easier to parse - something like

```
$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         **connected**       enabled         enabled    enabled         enabled   
$
$ dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.**Enable boolean:false**
method return sender=:1.5 -> dest=:1.288 reply_serial=2
$ 
$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         **asleep**          enabled         enabled    enabled         enabled   

```

---

### Post by Stonecold1995 on 2013-05-04
Hm, turns out if I ommit --print-reply it exits 0 every time I run it, whether or not networking is enabled or not.

I'm just doing it this way now:
```
dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"NetworkingEnabled" | grep -q true
```
That way grep will return 0 if the network is up, 1 if it's down.

---


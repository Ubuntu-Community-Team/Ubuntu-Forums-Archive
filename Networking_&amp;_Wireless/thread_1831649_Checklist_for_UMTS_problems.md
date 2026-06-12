---
title: "Checklist for UMTS problems"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by praseodym on 2011-08-23
Some users may have trouble in setting up an UMTS connection. This is a checklist for the most common problems that occur.

**[SIZE="3"]General[/SIZE]**:

From the Ubuntu version 10.10 on the UMTS support is significantly improved.

**SIM card**:

    [LIST]
[*]Disable PIN code request (in the mobile phone / with WIN-software or  umtsmon), this is often helpful

[*]    Stick Sim-/Netlock free (after a change of provider)

[*]    enter PUK (This is the 8-digit code to unlock the SIM card if the PIN is entered incorrectly multiple times)

[*]    SIM card is inserted correctly (or dirty)? (For those who groan at this point. It can easily happen, happens, and no one needs to be embarrassed!)

[*]    sufficient Funds are available (may be consumed quickly by using the wrong APN)
[/LIST]

**Miscellaneous**:

    [LIST]
[*]    Check whether the correct APN is used

[*]    Always enter at number * 99 # and never the mobile phone number ([COLOR="Red"]I dont know if 99 is country specific[/COLOR] :confused:)

[*]    Check:  &#8594; Users and Groups &#8594; Select "Advanced Settings" &#8594; User Rights &#8594; a checkmark in both entries, in which the word "modem" is included, then login once again for the changes to take effect (manual applies to gnome2-desktop apply to other graphical interfaces corresponding to the suppliers).

[*]    disable Parallel WLAN / LAN connection

[*]    Use alternative dialer programs (from version 10.10 not really necessary anymore.) Umtsmon / Vodafone Mobile Connect (BMC as successor) / ixconn / sakis3g / wvdial / Ubuntu Kubuntu-NWM

[*]    If modem is not detected or is in disk mode: install "USB-modeswitch"

[*]    Check whether the package **modemmanager** is installed (e.g. **Lubuntu** lacks this package in its default installation)

[*]    In some models which are set in the disk mode it is automatically switched to modem mode when drive / virtual CD is removed (right click, remove the drive safely).

[*]    All (kernel) updates installed?

[*]    Does Stick / modem work in Windows?

[*]    Browser in offline mode?

[*]    Check whether "Enable Mobile Broadband" is set (click on the icon in the panel)

[*]    Network Manager: Manually set the nameserver settings in the network manager

[*]    In certain cases it may happen that in network (under the APN) or the "Mobile Network Code" must be specified. Overview here: [http://en.wikipedia.org/wiki/Mobile_Network_Code](http://en.wikipedia.org/wiki/Mobile_Network_Code)

[*]    Connections may be required. try different USB ports (if posible: for Notebooks try CardBus USB) to avoid any long USB extensions, possibly using Y-cable. By using Y-cable or CardBus the sticks get a better power supply. Same effect is achieved by connecting to a powered hub (with power adapter).

[*]    In poor connections, it may be useful to chose the transmission rate (3G/2G). In Gnome network manager (Ubuntu until 10.10. Possible) klick "Type" button (default "Any") and choose accordingly. Likewise, in alternative dial-in programs and in the K-Network Manager (Kubuntu)

[*]    Disable firewall if installed
[/LIST]

You can check by

```
lsusb
lsmod
usb-devices
```
if the modem mode is active and if the driver is shown.

This checklist was Google-translated and corrected from the best of my knowledge from [this one]("http://forum.ubuntuusers.de/topic/web-n-walk-stick-iv-bekomme-keine-verbindung/#post-2572257") without warranty ;-)

---

### Post by praseodym on 2012-07-31
Last link updated :!:

[http://wiki.ubuntuusers.de/Mobiler_Datentransfer/UMTS-Checkliste](http://wiki.ubuntuusers.de/Mobiler_Datentransfer/UMTS-Checkliste)

---


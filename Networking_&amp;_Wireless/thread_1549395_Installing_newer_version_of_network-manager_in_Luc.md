---
title: "Installing newer version of network-manager in Lucid, from daily trunk builds ppa."
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by gvoima on 2010-08-09
**FYI** this is only for Lucid and Maverick, as there's no 0.8.1 builds for other releases in this ppa.

Why?
Because today there seems to be a fuss about 3g usb-modems. And as of network-manager version 0.8.1, there is added support for those and some more.

The release features for current version 0.8.1, from gnome.org
# **Bluetooth Dial-Up Networking (DUN) support**
# Enhanced IPv6 support including DHCPv6 capability
# Command-line interface
# **Mobile broadband signal strength, status, and roaming display**
# **Support for restricting mobile broadband roaming behavior**
# Enhanced logging and debugging infrastructure
# **Better handling of suspend/resume** (huawei didn't work well on my comp after suspend, now it does)
# Enhancements to the 'keyfile' system connection format
# Ability to suppress periodic scans by locking connection to a BSSID


Lucid ships with an earlier version and there's a ppa for daily builds (that could break, so use it on need-only-basis).
Visit the link, or google: [_NetworkManager daily trunk builds for ubuntu_]("https://launchpad.net/~network-manager/+archive/trunk")

Follow the steps on the site to add it in the repositories.
After that, it's just a simple ```
sudo apt-get update; sudo apt-get upgrade
```
apt will update the needed files. Then reboot, you're done.

I strongly recommend, that you disable the PIN code query for your SIM card **and** enable 'Connect automatically' from:
System > Preferences > Network Connections > Mobile Broadband > choose your provider from the list and edit.
As this seems to be more reliable than connecting/reconnecting manually from the applet list. After that, it's plug&play.


I use the modem Huawei E1820 (uses option1 driver) and for me, this update...
- gives you the ability to choose the desired network; 3G only, 3G pref., EDGE etc.
- Then it shows the signal strength and the technology used atm.; HSPA, UMTS etc.

And the main reason I installed it, bluetooth DUN support.
So far it has been working great with Lucid on 32bit architecture, and I don't have to disconnect the modem between boots, or after suspend/resume.

---

### Post by alexfish on 2010-08-09
Thanks for the thread

it will save having to downloading all of this
see screenshot

---

### Post by gvoima on 2010-08-09
That's quite a list.
Are you using Ubuntu, not Kubuntu or other OS builds?

[fixed]

---

### Post by alexfish on 2010-08-09
Ubuntu gnome

upgrading the network manager can be a thankless task if you are  using the debian repo's as shown by the downloads , you have to check for dependencies , if you break some of this then one can come unstuck .

so now we know of an easier way to go

thanks 

alexfish

---

### Post by swallisa on 2010-08-09
Thanks gvoima, asked this over at the Fedora forum and still no response that the previous NM update was broken.

---

### Post by Neill_R on 2010-08-10
Thank you I now have NetworkManager Applet 0.8.0.998 running well. 

But has not solved my current problem that unless i keep doing something on the internet my connection drops out yet the NM activity remains constant. Question how often or is it event driven does the activity (which i assume is signal strength at the dongle) and the mode (HSDPA or UMTS) status updated.

---

### Post by gvoima on 2010-08-10
> **Neill_R said:**
> Question how often or is it event driven does the activity (which i assume is signal strength at the dongle) and the mode (HSDPA or UMTS) status updated.

Actually it is, the technology works such a way, that if you idle, it doesn't stay on HSPA or alike, but drops to UMTS.
And when you again do something it tries to connect to the fastest possible available technology, so there's a slight lag which is annoying.

I've solved this by downloading something superfluous with wget, in my case a 1 gigabyte null file from one of the backbone provider's server in my country.

```
wget -c -q --limit-rate=0.5k [insert some file here to download] &
```

The 512 bits is enough to keep it alive and not to clog the connection.

---

### Post by mawhrin on 2010-08-12
> **gvoima said:**
> That's quite a list.
Are you using Gnome and Ubuntu, not Kubuntu or other OS builds?

Because, network-manager is a part of the gnome desktop.

Or then you're just using network-manager in other desktop environments, which is ok. It's quickly becoming a good manager. :)

kubuntu uses NetworkManager too. The KDE control applet (knetworkmanager) lagged behind the Gnome applet (nm-applet) (there were complaints from KDE people about Gnome's documentation IIRC) but is good enough now. It doesn't have an "allow this connection for all users" option, but otherwise seems feature complete, usable and stable. There's a less stable plasma widget too.

NM may be a part of the Gnome project, but it doesn't require any part of the Gnome desktop. It's just a daemon, and is desktop agnostic. In the ubuntu apt repositories network-manager and the Gnome and KDE control applets are separate packages.

---

### Post by gvoima on 2010-08-13
> **mawhrin said:**
> kubuntu uses NetworkManager too

Thanks for clearing that up, I wasn't aware of this.

---

### Post by alexfish on 2010-08-13
Hi all

Just been doing a bit of testing of modem manager 0.8.1

notice that the 3g signal strength has now been implemented

this facility uses an alternate port of the device 

if you use a the text services with the likes of wammu or gammu you may find they can no longer access the device , as modem manager now has control of this port

as a work around you may have to drop the connection with the network manager
if you still can't get the service try stopping the Modem Manager from the System Monitor, then restart Modem Manager when done or end the process altogether

alexfish

---

### Post by raunhar on 2010-10-29
Is there any way that I can just upgrade ModemManager to .4 (being used in Ubuntu10.10). ZTE device are recognised by this version.
The current version is .3 on Ubuntu 10.04

---

### Post by ravindasenarath on 2011-03-28
can some one provide a screenshot that where to set configuration for Mobile broadband signal strength, status, and roaming display please

Thank you

---


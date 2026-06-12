---
title: "Deleted Network-Manager, stuck with no Internet!"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by GiagNova on 2013-08-29
I recently Installed Kubuntu 12.04 and I'm really new to it.
After following some tutorial on setting up LAN (Only could choose wireless), I accidently removed Network-manager.
My network settings first had 4 options, now only 3.
I can't find any way to get internet again, how do I reinstall? I tried installing network-manager.0.9.2.deb (I think it was 0.9.2, 0.8 couldn't be installed) but after it finished, nothing happend.

Anyway to restore this?

---

### Post by _0R10N on 2013-08-29
The network manager for KDE is

```
network-manager-kde
```

So, you should run

```
# apt-get install network-manager-kde
```

---

### Post by ofnuts on 2013-08-29
Maybe your network manager is disabled:

Check /var/lib/NetworkManager/NetworkManager.state:and see if it says: "NetworkingEnabled=false"

In which case, remove it and restart the daemon:

sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager restart

You may have to manually kick networking back on with commands like `sudo ifconfig eth0 up` (where eth0 is your network interface) and `sudo dhclient`.  (these last lines are notes I took with a similar problem on a previous version, I don't know if they still apply).

---

### Post by GiagNova on 2013-08-29
> **ofnuts said:**
> Maybe your network manager is disabled:

Check /var/lib/NetworkManager/NetworkManager.state:and see if it says: "NetworkingEnabled=false"

In which case, remove it and restart the daemon:

sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager restart

You may have to manually kick networking back on with commands like `sudo ifconfig eth0 up` (where eth0 is your network interface) and `sudo dhclient`.  (these last lines are notes I took with a similar problem on a previous version, I don't know if they still apply).
I know for sure it's deleted because I actually used the "remove" command.

---

### Post by GwL3eNC on 2013-08-29
hi,

please post first

sudo dpkg -l | grep network-manager

or if it ist not possibe becasue your missing connection remove all  this packages with

sudo dpkg -P packagename

Possibly you must add a force option (think --force-depends) to remove them. After that
add into your /etc/interfaces these lines

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOURESSID
    wpa-psk YOUSECURITYKEY

then save and try sudo service networking restart. Also make shure wlan0 is your www interface.
If it works, you are connected and you can reinstall network-manager out of the repos.

---

### Post by whatthefunk on 2013-08-29
If you actually deleted it, you cant do a simple "sudo apt-get install network-manager" because youre internet is gone and you cant download the package from anywhere.  However, you can reinstall it from the CD/DVD you used to install the original OS.  

Put the CD in and open Muon Package Manager.  Go to Settings > Configure Software Sources and navigate to the Other Software tab.  Some where in the list of available sources there should be cdrom or something similar.  Make sure that box is ticked.  If its not there, click the Add CD-ROM button.  Once youve done this, close the Software Sources window and go back to the main Muon Package Manager window.  Click Check for Updates and then do a search for network-manager.  Mark it for installation and Apply Changes.  You might have to reboot for it to fully install.  Hopefully that will get you going again.

---

### Post by GiagNova on 2013-09-13
> **whatthefunk said:**
> If you actually deleted it, you cant do a simple "sudo apt-get install network-manager" because youre internet is gone and you cant download the package from anywhere.  However, you can reinstall it from the CD/DVD you used to install the original OS.  

Put the CD in and open Muon Package Manager.  Go to Settings > Configure Software Sources and navigate to the Other Software tab.  Some where in the list of available sources there should be cdrom or something similar.  Make sure that box is ticked.  If its not there, click the Add CD-ROM button.  Once youve done this, close the Software Sources window and go back to the main Muon Package Manager window.  Click Check for Updates and then do a search for network-manager.  Mark it for installation and Apply Changes.  You might have to reboot for it to fully install.  Hopefully that will get you going again.
Ok, so I tried to do this but In the window it says Network-manager and Network-manager-gnome are already installed. My problem is that I only got 3 options in Network manager, I am missing the connection option.

I tried installed the network-manager.deb from a usb, nothing happend. I tried this, nothing happend.
I also got "Waiting for Network Configuration" at startup now.

Anybody?

---

### Post by whatthefunk on 2013-09-13
> **GiagNova said:**
> Ok, so I tried to do this but In the window it says Network-manager and Network-manager-gnome are already installed. My problem is that I only got 3 options in Network manager, I am missing the connection option.

I tried installed the network-manager.deb from a usb, nothing happend. I tried this, nothing happend.
I also got "Waiting for Network Configuration" at startup now.

Anybody?

If you're using Kubuntu, you should probably have Network-manager-kde, not Network-manager-gnome.

What kind of connection do you have?  If its a pppoe connection, you could ditch network manager altogether and use the terminal program pppoeconfig.

---

### Post by nerdtron on 2013-09-13
Try
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Then reboot.

---

### Post by GiagNova on 2013-09-14
> **nerdtron said:**
> Try
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Then reboot.
Tried this, nothing happend.
It boots, says "Waiting for network configuration" then "Waiting up to 60 Seconds for network configuration" and then "Starting system without full network configuration"

---

### Post by steeldriver on 2013-09-14
It might help if you posted a link to the original tutorial that you followed - otherwise we are really just guessing at what you might have done

Or we could go right back to basics starting with the following outputs

```

ifconfig

sudo lshw -C network -sanitize

cat /etc/network/interfaces

```

The output of the nm-tool command would also be useful but you may wish to remove MAC addresses / SSIDs before posting it

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Networking & Wireless**.*

---


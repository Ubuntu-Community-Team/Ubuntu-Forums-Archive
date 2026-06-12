---
title: "Problem with WPA2 (Enterprise) &amp; Interpid"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Cpudan80 on 2009-01-06
Hello all:

I am trying to get WPA2 Enterprise working with 8.10. It worked great under 8.04. Right now my college has a WPA2 encrypted wifi network using PEAP (ver 0) and MSCHAPV2. When I go to connect in 8.10 (using the network manager GUI) the following is logged to /var/log/wpa_supplicant.log:

Trying to associate with --- (SSID='---' freq=2437 MHz)
Associated with ---
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
EAP-MSCHAPV2: Authentication succeeded
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-TLV: Earlier failure - force failed Phase 2
CTRL-EVENT-EAP-FAILURE EAP authentication failed
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

I am trying this using a T42 with an Atheros 5001X+ chipset.

All help is appreciated -- thanks in advance.

Dan

---

### Post by Cpudan80 on 2009-01-08
Here's the solution - as posted to Bug #272185:
====

## WARNING: Following these instructions may break your Intrepid installation. They worked great for me on a variety of laptops, but your mileage may vary. Proceed at your own risk. ###

The problem is with how wpa_supplicant and network manager interact. Updating the relevant packages to their jaunty equivalents fixes the problem. Here's the procedure:

0. Run a standard update to make sure you have all relevant Intrepid updates.

1. Add the jaunty repositories to /etc/apt/sources.list. Using your favorite text editor (ex. gksudo gedit /etc/apt/sources.list), add the following lines (we will remove these when all is said and done.)
# Jaunty Sources
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jaunty main restricted

2. Update your sources list by running the following command: sudo apt-get update

** A zillion new updates will show up. Do not run any automatic updaters! Doing so may break your installation. **

3. Open the synaptic package manager (System --> Administration --> Synaptic Package Manager). Search for and upgrade the packages listed below:
* wpasupplicant
* libnm-glib0
* libnm-util0
* libxcb-render-util0
* network-manager
* network-manager-gnome

After you finish - Ubuntu will tell you to restart. Don't restart yet.

4. Go back and remove the lines from step one (1) from your /etc/apt/sources.list. Once the lines are removed -- save the file. After that, do another sudo apt-get update to remove the jaunty sources. Any automatic updaters should go back to normal and say that no updates are available.

5. Now restart your computer. It should all work after that. You may have to delete your existing (broken) associations in order for it to work right.

Tested to work on several atheros chipsets and several Intel chipsets. Special thanks to the College of William and Mary for providing the test equipment.

I hope it works out for you!

Dan

---


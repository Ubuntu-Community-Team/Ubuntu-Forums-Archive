---
title: "[SOLVED] Can't get bluetooth mouse and keyboard paired"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by newoldguyindenver on 2008-12-12
Have a msft 5000 bluetooth notebook mouse 5000 and a Rocketfish bluetooth keyboard. I am attempting to pair with my ASUS EeePC 1000H. I am getting the message (quote) 'Couldn't display "Obex://[00:18:A3:00:40:D9]/".

Error: Host down
please select another viewer and try again.' (end quote).

I am a newbie and am at a loss as to what to do - I need the bluetooth mouse and keyboard - the ASUS mousepad is too sensitive and I have fat fingers that constantly touch the mousepad and prematurely execute commands with the mousepad.

The workarounds I have found in HOWTO books are incomplete and confusing - some reference files (I don't know if the files are needed or not) that I do not have, or the files reside somewhere else on the computer.

Any help would be greatly appreciated.

Newoldguyindenver

---

### Post by buttertoad on 2008-12-12
I am going to assume you are running Ubuntu 8.10, if not let me know.

Make sure your bluetooth adapter is on and open your bluetooth preferences.
Click: System > Preferences > Bluetooth

Click on the add button and follow the directions. To make your mouse discoverable hold down the tiny button on the bottom until the light on top flashes between green and red. Wait until the mouse is listed in the device box (it could take about 20-30 seconds).

I'm not sure how to make your keyboard discoverable but it should be something similar. Check the manual if you are not sure.

If you pair either device with another OS or different computer you probably need to repeat this process.

I'm using that exact mouse right now so I know it works. :)
Good luck.

Oh I almost forgot. Obex is used for file sharing so that is why you are getting an error because the mouse and keyboard are not capable of that. Make sure that you are only trying to pair a device not set up a network.

---

### Post by newoldguyindenver on 2008-12-12
I am using 8.04.

I have attempted the process you recommended, and I have paired the mouse and keyboard uncer win xp on this same laptop.

If the error message concerning file sharing displays, will this interfere with the pairing process?

---

### Post by buttertoad on 2008-12-12
Well in 8.04 I used Blueman to connect bluetooth devices. This should still work ok you just need to install it first.

These instructions are straight from the Blueman web page:

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

```
wget -q http://download.tuxfamily.org/blueman/blueman.gpg -O- | sudo apt-key add -

```

Next, add the repository to your system's list of APT sources:

```
sudo wget http://download.tuxfamily.org/blueman/hardy.list -O /etc/apt/sources.list.d/blueman.list
```

Then update APT's package information by running ```
sudo apt-get update
```

Now you can install blueman by [[COLOR="Lime"]clicking this link[/COLOR]]("apt://blueman"). Alternatively, you can install by going to System->administration->Synaptic and searching for blueman.


Once it is installed open the program by going to Applications > Accessories > Blueman Bluetooth Manager. Make your device discoverable and then click on the Inquiry button (if your mouse/keyboard doesn't show up click it again).
After your device shows, in the menu click Edit > Services and make sure for Input Status has a green check mark and Autostart has a check mark. Next in the Services window click on the Configure button and select Add New Input Device. For the address click on the drop down menu and your device should be listed, select it and click on add. It will ask you some questions about authorized and trusted, make it both.

And that should do it. Do this for both your keyboard and mouse and if you make the right selections for favorites and trusted it should remember the devices every time you boot your computer.

Let me know if this works for you. A lot of it had to come from memory. :p

---

### Post by kitelau888 on 2009-01-05
> **buttertoad said:**
> 

Click on the add button and follow the directions. To make your mouse discoverable hold down the tiny button on the bottom until the light on top flashes between green and red. Wait until the mouse is listed in the device box (it could take about 20-30 seconds).

I'm using that exact mouse right now so I know it works. :)
Good luck.



Hello, I have problem connecting the exact mouse under 8.10. The mouse was discovered but with exclamation mark icon insead of a key icon on the list of device. Is this normal? What other steps should be take to connect the bluetooth mouse.

command dmesg showed: [ 1910.436041] hci_cmd_task: hci0 command tx timeout

"bluetoothd -nd" showed:
bluetoothd[10319]: Bluetooth daemon
bluetoothd[10319]: Enabling debug information
bluetoothd[10319]: parsing main.conf
bluetoothd[10319]: discovto=0
bluetoothd[10319]: pairto=0
bluetoothd[10319]: pageto=8192
bluetoothd[10319]: name=%h-%d
bluetoothd[10319]: class=0x000100
bluetoothd[10319]: inqmode=0
bluetoothd[10319]: Key file does not have key 'DeviceID'
bluetoothd[10319]: Unable to get on D-Bus

So something is not right. I tried hidd, but hidd --search found the device and could not connect either.

Notes: I have upgraded kernel to version 2.6.28 and bluetooth packages to latest vertion 4.25. Before upgrading, bluetooth mouse and file transfer and browsing with my bt mobile phone did not work; After, bluetooth mouse still does not work, but file transfer and browsing with my bt mobile phone works!

upgraded:
bluetooth_4.25-intrepid-ppa1_all.deb
bluez_4.25-intrepid-ppa1_i386.deb
bluez-compat_4.25-intrepid-ppa1_i386.deb
bluez-cups_4.25-intrepid-ppa1_i386.deb
bluez-gstreamer_4.25-intrepid-ppa1_i386.deb
bluez-pcmcia-support_4.25-intrepid-ppa1_i386.deb
bluez-utils_4.25-intrepid-ppa1_all.deb
libbluetooth3_4.25-intrepid-ppa1_i386.deb
libbluetooth-dev_4.25-intrepid-ppa1_i386.deb

uname -a:
Linux kitelau-laptop 2.6.28-4-generic #6-Ubuntu SMP Thu Jan 1 22:53:42 UTC 2009 i686 GNU/Linux

---


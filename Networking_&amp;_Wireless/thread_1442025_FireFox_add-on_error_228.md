---
title: "FireFox add-on error 228"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by ubunterooster on 2010-03-29
I had firefox having an inability to download addons, so I edited the dhclient.conf file by entering the following into a terminal:

```
sudo gedit /etc/dhcp3/dhclient.conf
```When the document opened, I edited the line that starts prepend domain-name-servers to read:

```
 8.8.8.8,8.8.4.4;
```Saved and closed the file.  I went back to the terminal and opened the nsswitch.conf file by entering:

```
sudo gedit /etc/nsswitch.conf
```When the document opens, I edited the line hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 to read:

```
hosts: files dns
```Saved and exited the document.  To be on the safe side, I restarted my computer after making the edits. [/QUOTE]

This was done following the thread someone wrote on a similar error: [http://ubuntuforums.org/showthread.php?t=1311774](http://ubuntuforums.org/showthread.php?t=1311774)


Still does not allow addons...

---

### Post by ubunterooster on 2010-03-29
If I go in through Epiphany, right click the install here links, and save them to hdd, I can select them to be opened with Firefox and this installs them.

Why is it that Thunderbird extensions are easily installed, yet Firefox's will not install properly? Even with epiphany-browser, Firefox's add-ons take at least five minutes to begin downloading.

---

### Post by ubunterooster on 2010-03-29
Solution:

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). If the settings reset after restart, then delete the file user.js from the profile folder, to reset proxy settings.

Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.

   1. Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart your Mozilla application and try again.

Found on: [http://lovinglinux.megabyet.net/?page_id=220#Connections-settings-are-reset-after-restart-2](http://lovinglinux.megabyet.net/?page_id=220#Connections-settings-are-reset-after-restart-2)

---


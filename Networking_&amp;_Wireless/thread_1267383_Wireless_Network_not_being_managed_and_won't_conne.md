---
title: "Wireless Network not being managed and won't connect"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Hobbsilla on 2009-09-15
I'm using Jaunty and about four or five days ago my wireless which had been working flawlessly at my house (unlike the Wireless on my XP computer) suddenly stopped working. I've reset the router and it did nothing. I get wifi on other networks and on an ethernet cable but I want wifi to work at my house again. Everyone else in my house uses XP or Vista and nothing has changed for them so I'm pretty sure it has something to do with my computer. I attempted to use WICD but it didn't do anything and I reinstalled the default wireless network settings and now my wireless network is not being managed. Pinging does not work either. Can anyone help me? I think it had something to do with an update I recently did, I've been hearing about a recent ndiswrapper update causing problems for some Jaunty users. Attached is a photo of what it shows under the wireless interface.

---

### Post by Iowan on 2009-09-15
I haven't used Wicd, but...
Check contents of /etc/network/interfaces - it should only have two lines: one defining "lo" and one "auto lo". If there are more, comment them out by inserting a # at beginning of line (via **sudo nano /etc/network/interfaces** or **gksudo gedit /etc/network/interfaces**). Restart (or reboot) and see if the "unmanaged" message goes away.

---

### Post by JakP on 2009-09-15
Had this problem, if you have switched back to networkmanager then enter this in terminal:

sudo gedit /etc/NetworkManager/nm-system-settings.conf

in the file it brings up change the line "managed=false" to "managed=true" (no quote's) and this solved problem for me

---

### Post by Hobbsilla on 2009-09-15
To Iowan: thank now I can see my networks again. I unfortunately still have the problem of not being able to have access to the internet despite my interface saying I'm connected to my home's wireless network. I just made the change to my Network Manager settings that JakP recommended and I will reboot my computer to see if that fixed the problem.

---

### Post by Hobbsilla on 2009-09-15
So I made the changes that JakP suggested and I had internet for 10 minutes before it killed on me. Anymore suggestions?

---

### Post by uylug on 2009-09-15
Okay, try this:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "YOUR_AP_NAME"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

...where YOUR_AP_NAME is your Access Point name

---

### Post by gfbv on 2009-09-18
Recently was able to properly configure my wireless interface to connect to my router and connect to the internet.  However, the Network Manager did not reflect that so I was excited to find out that I simply needed to comment out everything in the /etc/network/interfaces file, and then update the /etc/NetworkManager/nm-system-settings.conf from managed=false to managed=true.  Last night I updated both files and then rebooted my system.  After the system booted back up and the login screen came up my system froze - no keyboard input is recognized, the mouse wont move, the cursor in the username text field is frozen, and my keyboard's caps lock and scroll lock keys blink on and off. Also booting into recovery mode works fine.
This behavior is very repeateable - I rebooted several times and got the same exact behavior, though I did notice that I can move the mouse and type a few characters in the username text field before it freezes up.  In other words my keyboard/mouse work fine before the box locks up.  
 
Please note the two files listed are the ONLY changes made to the computer; I literally booted up changed those files and rebooted.
My next step is to go back into the recovery mode and to undo the changes in both those files.
If anyone has any idea of what could be going on with my system I'd love to hear it.  Thank you!

---

### Post by gfbv on 2009-09-18
After looking into the root cause of my Ubuntu box freezing up. I ran into a post [[System freeze Caps lock blinking?]("http://ubuntuforums.org/showthread.php?t=976287&referrerid=914606)")]  that ultimately points to an issue with Network Manager.  I've reverted back to my previous versions of /etc/network/interfaces and /etc/NetworkManager/nm-system-settings.conf so that NM was (again) no longer managing any network interfaces.  When I rebooted my system was back to normal (no longer freezing up).  Then I ultimately uninstalled NM and instead installed WICD and that worked right off the bat.  Problem solved!

---


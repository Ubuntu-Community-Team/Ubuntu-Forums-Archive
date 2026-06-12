---
title: "WICD Tray Icon/Frequent Disconnects in Network Manager"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by batbrownbear on 2013-04-29
I've been using Ubuntu for a little over a year.  After the 12.10 upgrade, I started having frequent wireless disconnects in Network Manager that I wasn't getting before.  Before I maybe would have a lost connection about once or twice a day, about the same as I get if booted into Windows 7 on the same computer.  After the upgrade, I'd get disconnected about once every 10 minutes.  I thought at first that the usb adapter had just gone through too much abuse after several years of use so I purchased a new adapter (same chipset different brand).  I had the same problems with the new adapter and Network Manager, so I switched to WICD.  I get that same infrequent disconnect in WICD, but nothing like I was seeing in Network Manager, I even switched back to the older adapter and it still worked.

Now, with the 13.04 upgrade I can't have a wireless status icon in the tray because WICD lacks an AppIndicator.  Right now I'm still running WICD, but have to launch the settings out of the launcher if I want to change anything.  I'd really like to have a working wifi connection with easy access to connection status and signal strength from the tray.  Anything that could be done to help, either a work around to put WICD in the tray like the old panel whitelist or how to figure out what stopped working with these adapters in Network Manager?  Not sure what all the information you might need if it's down to diagnosing Network Manager settings.  I'd have to reinstall it again, I tried right after the 13.04 upgrade and saw the same disconnects and swapped back to WICD.

The adapters are: G-SKY GS-27USB (older) and Alfa [COLOR=#000000][FONT=verdana]AWUS036H, both [/FONT][/COLOR][COLOR=#000000][FONT=Arial]RTL8187L

Thanks for the help.[/FONT][/COLOR]

---

### Post by tetralectic on 2013-05-31
Have a look at [HOW TO GET THE SYSTRAY WHITELIST BACK IN UBUNTU 13.04]("http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html"). Also have you tried changing the channel that your router is broadcasting on? You may be getting interference from nearby routers broadcasting on the same channel.

---


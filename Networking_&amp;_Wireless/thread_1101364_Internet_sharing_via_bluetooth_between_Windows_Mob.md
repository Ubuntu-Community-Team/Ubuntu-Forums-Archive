---
title: "Internet sharing via bluetooth between Windows Mobile and Linux"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by Lety on 2009-03-20
Hello, I just want to tell how I managed to share gprs internet connection between Windows Mobile 6.1 (HTC P3600 Trinity) and Ubuntu 8.10 64bit (eMachines D620 laptop) via bluetooth.

1. I pluged in my USB-dongle (TrendNET TBW-105UB) , then I installed Blueman 1.02 from .deb , took it here:
[https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa)
The program replaced the standart Bluetooth Manager, so you go to System/Preferences/Bluetooth manager to launch the Blueman.

2. I went Start/Programs/Connectivity/Internet Sharing on my WM6.1 PDA.
Settings are:
PC Connection - Bluetooth PAN
Network Connection - GPRS (internet connection name on the PDA).
Then I pushed connect, my PDA started internet sharing over bluetooth (device must be visible for all).

3. I went to Bluetooth manager applet (my device was already there, because I configured it's connection with the laptop in the standart bluetooth manager before).
Right click on the tray icon of the Bluetooth manager -> Local services
I chose 'Let's Blueman handle the network interfaces' on the Network tab.

4. Now in the main window of the Bluetooth manager I right-clicked on my device and chose Network Access -> Network access point.

That's all, Internet started working on my laptop via GPRS on my WM 6.1 communicator!:)
I was suprised it was so easy.
As I read before I was going to do a lot of stuff: install packages, edit config files, do some commands in the terminal.
But using Blueman I did everything through GUI very fast, and of course I didn't have to install any drivers for the bluetooth dongle :)
Hope this will be helpful.

---

### Post by Nostalos on 2009-03-20
Thanks!   Been looking for a bettwe way to manage this connection than the scripts i been using!

---

### Post by keltose on 2009-03-28
Worked for me on Moto Q with 6.1.

thanks!

---

### Post by manishmahabir on 2009-07-13
how can I access internet in my mobile via bluetooth from my PC?

---

### Post by jonlowe on 2009-08-24
Many, many thanks!!  Works under with Verizon Motorola Q9C with WM6.1.  IntShr.exe is installed by default with WM6.1 (download WM6.1 and install from the Motorola site; backup ALL of your contacts first as they don't tell you it will completely wipe your system), and is in the Windows directory.  Make a shortcut of IntShr.exe and add to the Start menu using File Manager.

Pair your phone with your computer.  Start Intshr on your phone,  Select Bluetooth PAN and Broadband on the main screen.  Hit Connect.  The next screen should bring up your computer name.  DO NOT hit connect there.  Click on the Bluetooth icon in your system tray on your computer.  The Bluetooth app window will appear with your phone shown in the main window.  Click on the menu item Device>Network Access>Network Access Point.  Your devices should connect in a few seconds.  Now surf.

If you hit connect in the second screen on your phone instead of the way I outline above, it WILL FAIL to connect, even though it says connected.  You must do things in the order I describe, or it will fail to connect EVERYTIME!

Now if I could only find a way to make a USB connection between my phone and Ubuntu work.  Works great on XP...

Jon
eeebuntu 3.0 Standard w/.30 kernel
Asus eeePC 900a
2gb ram, 32gb SSD

---


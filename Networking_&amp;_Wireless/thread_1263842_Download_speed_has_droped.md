---
title: "Download speed has droped"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by zeedzler on 2009-09-11
Hi, when i first installed Ubuntu the download speed was very very fast but now after a few weeks the download has become very very slow. Is this because of some error or is it because its normal?

---

### Post by threetwoone on 2009-09-11
Well the first thing you should do is check to see if something has changed in your set up, i.e. did you move the computer further away from your router if you are using wireless or did a cable get damaged, did you install anything that uses you network card, etc. (this seems pretty obvious but if I had a nickel for every time...well I think you get my point;-)).

The next thing to do is read your computers logs if there is an error chances are good that its in there.  Gnome has a very nice log viewer under System > administration > log file viewer.  Its not that hard to learn how to read  them and its a good habit to get into because it aids in maintaining system security, functionality and it can help you to better understand the system. A great place to start is [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles).  Don't hesitate to ask in the appropriate forum about something you see in there if you think it could be a problem.:D.

After that you should check the hardware specific stuff.  In this case the commands should get you started:

[LIST]
[*]ifconfig (for wired and wireless) - shows info about network adapters
[/LIST]

[LIST]
[*]iwconfig (for wireless only) - shows info about wireless network adapters
[/LIST]

[LIST]
[*]lshw - lists hardware (you will have to run this as sudo) but this will output a lot of stuff that isn't important right now so you can add the -c network parameter (this will make it list only devices in the "network" _c_lass) this shows all the goodies about your hardware, things like who made it, what model is it, what the system has named it, what it can do, what driver its using and much more!
[/LIST]
The information from your system logs and these commands should you should have a solid base to try and figure out what's going on.

Also, remember that we need more details in order to help you!!!  Things like: What are you downloading?, is it slow on all computers or just the one you are using?, is it slow on other networks or just yours?, is it slow while transfering files from one computer to another or just when downloading from the Internet?, How is it connected to the internet, etc.

---


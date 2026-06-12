---
title: "Hang on reboot when connected to NFS/ldap server via wireless"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by larseko on 2010-06-18
Hello there. I have a strange problem here. Let me first say that I'm very impressed by Lucid Lynx, which works like a charm and was easy to set up on our Dell Vostro 3300 laptops. There is, however, a small problem with our particular setup.

First, a general description the situation:

School with linux running on students' laptops, connecting via wlan to a Debian NFS and LDAP server. Every student logs on his/her profile residing on the NFS server. The clients are set up with autofs. Earlier, I had set up the wireless network in /etc/network/interfaces, but this time I decided to configure network manager so as to bring up both wireless and wired network before logon. This setup has been working on for the last fire or five years with only minor changes. Also worked with Karmic Koala, but still with the interfaces file instead of networkmanager. The Vostro is also new here, we've previously used mostly Dell Latitude D505s.

So here is what works:
1: Clients can log on to LDAP and NFS servers both wired and wirelessly. Everything is smooth.
2: While on LAN, shutdown and restart works flawlessly (and quick as a breeze, I'm really impressed by startup/restart/shutdown times, under 25 secs!).
3: Shutdown and restart also works wirelessly when doing it either from a local account or from the GDM chooser.

What doesn't work, however, is shutting down or restarting directly from a networked account connected while only being connected over the wireless network.

This is what's being displayed on the terminal after it has tried tho shut down for a while:

```

The system is going down for halt NOW!
acpid: exiting

init: cron main process (1011) killed by TERM signal.
init: tty1 main process (1365) killed by TERM signal.
.... same for all the ttys ...
init: avahi-daemon main process (1047) terminated with status 255

* Stopping the Winbind daemon winbind [OK]

* Stopping puppet configuration management tool [OK]

Checking for running unattended-upgrades: modem-manager: Caught signal 15, shutting down...
init: Disconnected from system bus

(Then a long wait)

[3119.502860] INFO: task gconfd-2:2756 blocked for more than 120 seconds.
[3119.502923] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs"
(Same message repeated for gnome-settings-, polkit-gnome-au, nm-applet, bluetooth-apple, syndaemon, gtk-window-deco, gdu-notificatio, python, update-notifier)

```

If I try ctrl-alt-del at this stage, it says:

"init: rc main process (3030) killed by TERM signal"

"Checking for running unattended-upgrades: "

And then it will hang again, until I hold the powerbutton for some seconds. The unattended-upgrades part is what seems to be the culprit. I suspect it is about the wireless network not being connected any longer or something like that, but I'm not sure about how to go about debugging shutdown scripts here. I'd be grateful for pointers.

I will try and see how it goes with the old interfaces file setup, but I'd rather make nm work.

---

### Post by larseko on 2010-09-23
I'm still having these problems. It seems like the wireless network is brought down before the NFS shares are unmounted. Can anyone confirm this?

---

### Post by msakms on 2010-10-29
[COLOR=Blue][FONT=Comic Sans MS]I also have the exact same issue when shutting down my laptop. How come such a critical bug doesn't get fixed right away? [/FONT][/COLOR]

---

### Post by larseko on 2010-11-19
This bug or whatever makes another bug very annoying:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

Since the PC hangs on shutdown, pupils tend to just close the lid and leave the laptop. This results in the machine going into suspend/hibernation at last, which in its turn results in the network being disable for the next reboots.

---


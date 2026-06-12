---
title: "i appear to have broken my network"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Post Monkeh on 2009-01-25
i installed 8.10 a few weeks ago and bar the odd (well when i say odd it's at least once a day) disconnection requiring a reboot, my wireless has been working ok.

i've been experimenting (read fiddling) the past few days, trying the kubuntu and xubuntu desktops, and i'd also installed ufw & gufw (without actually using the firewall packages to make any changes, i just opened them up to have a look)

earlier today i decided i wanted to stick with the standard ubuntu package for a while, so i removed the kubuntu & xubuntu packages (and kde & xfce packages)  at the same time i also removed ufw/gufw.  during the removal procedure, my laptop froze (i think because although i was in the gnome environment, it was running some aspect of the kde packages)

now everything booted up again ok, however although my newtwork connected immediately, it wouldn't work (couldn't ping my router, couldn't connect to the internet)
when i tried to ping the router ip address, it told me something along the lines of "not allowed" rather than "could not find host" so i had a fair idea that my problem was not with the network as such, but something was blocking my access.

i reinstalled gufw (luckily i didn't remove the installation files) and bingo, my network worked as soon as i enabled the firewall.  if i disable the firewall it still works.  however if i restart the system, i'm back to square one and have to load up the firewall again.

i've also tried installing firestarter and removing ufw, and it is exactly the same, to connect to my network i have to load my firewall, although it continues to work even if i then disable the firewall until my next reboot.

it seems some setting has been modified somewhere that's automatically blocking all access until a firewall is loaded and over rides it.

any ideas?

---

### Post by oscarmeyer51 on 2009-02-02
Having a similar issue here. I had wired/wireless working and after last upgrade (and install of True Crypt), I have the issue with ufw where I have to manually disable it to get out to the internet on every reboot. 

I additionally have had one of my wireless (ath0) interfaces disappear (was working last Thursday, is gone this morning from all iwconfig, ifconfig listings). I am running wicd instead of network manager. Will be happy to post any additional info requested, but as I travel 3 days a week, my responses may depend upon my location and availabilty to reply/post.

Thanks to any/all info to assist.

---

### Post by rogier.de.groot on 2009-02-02
I think ufw is a standard component in an Intrepid install (all my machines run the service, though I never installed it). You didn't remove the ubuntu-desktop packages while uninstalling ufw, did you?
Anyway, please post your ufw configuration file.

---

### Post by oscarmeyer51 on 2009-02-02
FYI -- There is a thread in this forum titled "[SOLVED] Uncomplicated Firewall Configuration" originally posted by urban48.

It that post there is a ufw setting that appears to have solved my connection issue on reboots.

The command is:

sudo ufw allow from any to any

the ufw has to be enabled to run this, but on reboot, I did not have to disable/renable ufw. I am certain this creates a huge gaping security hole, so I am searching for tutorials on ufw.

Here are some I found via Google.

[http://www.tutorialhero.com/click-30857-ufw_%5C%27uncomplicated_firewall%5C%27_for_ubuntu_hardy.php](http://www.tutorialhero.com/click-30857-ufw_%5C%27uncomplicated_firewall%5C%27_for_ubuntu_hardy.php)

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

Also avoid any address from google gruppi or ivihbk0, they only lead to porn and have no informational value for this issue.


There is also some good information on securing/hardening your laptop/desktop/network at
[http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/)

I can wait on my missing ath0 port and work on that later. Hope all of the above is useful for you.

---

### Post by oscarmeyer51 on 2009-02-02
> **oscarmeyer51 said:**
> FYI -- There is a thread in this forum titled "[SOLVED] Uncomplicated Firewall Configuration" originally posted by urban48.

It that post there is a ufw setting that appears to have solved my connection issue on reboots.

The command is:

sudo ufw allow from any to any

the ufw has to be enabled to run this, but on reboot, I did not have to disable/renable ufw. I am certain this creates a huge gaping security hole, so I am searching for tutorials on ufw.

Here are some I found via Google.

[http://www.tutorialhero.com/click-30857-ufw_%5C%27uncomplicated_firewall%5C%27_for_ubuntu_hardy.php](http://www.tutorialhero.com/click-30857-ufw_%5C%27uncomplicated_firewall%5C%27_for_ubuntu_hardy.php)

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

Also avoid any address from google gruppi or ivihbk0, they only lead to porn and have no informational value for this issue.


There is also some good information on securing/hardening your laptop/desktop/network at
[http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/)

I can wait on my missing ath0 port and work on that later. Hope all of the above is useful for you.

Di! Ecce hora! Uxor mea me necabit!
God, look at the time! My wife will kill me!

---


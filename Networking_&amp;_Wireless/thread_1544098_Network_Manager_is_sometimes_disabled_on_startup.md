---
title: "Network Manager is sometimes disabled on startup"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Darwin Award Winner on 2010-08-02
If you sometimes have to manually enable networking after a reboot of your computer, you can follow the steps here to force your computer to re-enable networking at every reboot.

First, you'll need a package called cnetworkmanager. It is a command-line program that fulfills the same function as your network management applet, and we'll be using it to send the "enable" command to Network Manager. Unfortunately, the cnetworkmanager package was added after the latest release of Ubuntu (10.04), so you'll have to download it manually from here: [https://launchpad.net/ubuntu/maverick/+package/cnetworkmanager]("https://launchpad.net/ubuntu/maverick/+package/cnetworkmanager"). 

Now, you'll need to edit the file "/etc/rc.local". You'll need administrator rights to do so. Add the following lines anywhere before the line that says "exit 0":

```
# Enable networking
cnetworkmanager --online=true
cnetworkmanager --wifi=true
```

This file is executed at the end of the boot sequence, and it should guarantee that both networking and wireless networking are enabled.

---

### Post by prshah on 2010-08-02
You can do the same thing without the need to install external, non-repo software, with the command```
service network-manager start
``` (Add "sudo" if executing from the command line, instead of rc.local).

---

### Post by Darwin Award Winner on 2010-08-02
That doesn't solve exactly the same problem. The problem I am talking about is when the option to "Enable Networking" is unchecked in the right-click menu of the network applet in the panel. That is, my problem was that the service was running, but decided to wait for my permission to connect to the network.

---

### Post by theNthDoctor on 2010-08-19
The original poster's solution worked for me using Jolicloud 1.0, an Ubuntu-based distro.  Cheers!

---


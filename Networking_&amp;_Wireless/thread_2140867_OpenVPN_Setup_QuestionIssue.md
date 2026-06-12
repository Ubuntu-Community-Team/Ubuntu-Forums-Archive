---
title: "OpenVPN Setup Question/Issue"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by Precipitous on 2013-04-30
I am running Ubuntu 12.10 and recently started using the [Private Internet Access]("https://www.privateinternetaccess.com") VPN service. They have an install/setup script for OpenVPN that installs OpenVPN and configures all of thier accessable gateways. I ran the script and everything went fine. I was able to right-click the Network Manager icon, go to VPN, see a list of gateways, click on one and connect...  After rebooting the computer when I right-click the Network Manager I no longer have VPN listed on the menu. If I select Edit, then select VPN I see that all of the configured gateways are still there, and still properly configured.

My question is this:  Is what I am describing normal and I am just supposed to be running a script at bootup that sets up OpenVPN and the Network Manager each time, or is what I am describing not normal and indicative of an issue that needs to be addressed? If I need to be running a script at bootup, does anyone have any examples of what it needs to contain?

I am new to OpenVPN, so I don't know if I am just being an idiot, or I am experiencing an actual problem.

Thanks in advance for any assistance anyone can offer!

---

### Post by ahallubuntu on 2013-04-30
~

---

### Post by Precipitous on 2013-05-01
@ahallubuntu:  Thank you for the information. I did not realize the Network Manager was so buggy...

I  got around the issue by doing the following: First I ran the following  command in the Terminal to find out the uuid numbers for all installed  VPN gateways:
```
nmcli con list | grep -i vpn
```
Once I knew the uuid number for the gateway I need to use I ran the following command to connect to it (substituting the real uuid for xxxxxx):
```
nmcli con up uuid
```
Since that worked I created the following script and added a link to it in the Startup Applications so I connect automatically at boot (the sleep command gives the Network Manager time to load before the command is issued to connect to the VPN gateway):
```
#!/bin/bash

sleep 10
nmcli con up uuid
```

---


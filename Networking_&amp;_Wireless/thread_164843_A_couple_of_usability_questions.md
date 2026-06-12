---
title: "A couple of usability questions"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by tiuk on 2006-04-23
First of all, let me note that I'm running Dapper Flight 6. I don't think this will have any bearing on the specific questions I have, but if it does then I apologize for posting in the wrong forum (is there a networking forum for Dapper? Couldn't find one).

My laptop has a Broadcom bcm4318, which after much googling is working through ndiswrapper.

Here are my questions:

-Every time I reboot I have to "sudo modprobe ndiswrapper", then go into Network Settings and activate eth1 (my wireless adapter), then "iwconfig eth1 essid [my essid]". Is there any way to automate this?

-I mainly use my wireless at home and at school. In Windows I can set a list of preferred networks that it will automatically connect to. Can I do this in Ubuntu?

-My school's network is unencrypted, but uses a captive portal for authentication. Sometimes the login page doesn't come up unless (in windows) I release and renew the laptop's IP. I suspect I will also have this problem in Ubuntu. What is the linux equivalent of "ipconfig /release" (releases the current DHCP IP address) and "ipconfig /renew" (gets a new DHCP IP address)?

-"iwlist eth1 scan" only seems to find my AP when I'm at home (haven't been able to try elsewhere yet), but I know there are a few other wireless networks around here that I can connect to. Is there any reason why they wouldn't be showing up?

Thanks, so far I'm very impressed with Ubuntu.

---

### Post by Jason_25 on 2006-04-23
1.  Add ndiswrapper to /etc/modules.  The /etc/network/interfaces file is for network settings.

2.  Network Manager does this.

3.  Not sure. I don't use DHCP.

4.  iwlist shows all it can find.  You may be able to increase the power of the card with iwconfig.

---

### Post by strongbow1800 on 2006-04-25
[QUOTE=tiuk]
-My school's network is unencrypted, but uses a captive portal for authentication. Sometimes the login page doesn't come up unless (in windows) I release and renew the laptop's IP. I suspect I will also have this problem in Ubuntu. What is the linux equivalent of "ipconfig /release" (releases the current DHCP IP address) and "ipconfig /renew" (gets a new DHCP IP address)?
[/QUOTE]

```
sudo dhclient eth0
```

should do it. If it doesn't, try ```
sudo dhclient -r eth0
```
-r specifies to release, which it doesn't do automatically.

FYI, in Windows, you don't have to go to command line to release/renew your DHCP lease. Just open the interface window and click on "repair" on the Support tab.

---

### Post by tiuk on 2006-04-25
[QUOTE=strongbow1800]```
sudo dhclient eth0
```

should do it. If it doesn't, try ```
sudo dhclient -r eth0
```
-r specifies to release, which it doesn't do automatically.

FYI, in Windows, you don't have to go to command line to release/renew your DHCP lease. Just open the interface window and click on "repair" on the Support tab.[/QUOTE]

Thanks, both of you. Everything is working great now.

For the Windows thing, thanks for the tip. I just had a batch file with the necessary commands on the desktop that I could use when needed.

---


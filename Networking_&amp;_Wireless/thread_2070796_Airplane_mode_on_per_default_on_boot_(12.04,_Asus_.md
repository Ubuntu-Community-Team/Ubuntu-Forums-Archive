---
title: "Airplane mode on per default on boot (12.04, Asus Zenbook Prime)"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by PikoMedia on 2012-10-13
Hi,

I have this very annoying anomaly; Ubuntu 12.04 defaults to airplane mode on every boot and on every resume from hibernate. Thus, every  time I log on or resume, I have to go to to the system settings, go to the network section, set airplane mode "off" and then wait for reconnection which is not always done in a snap.

I'm fully fine with working around this problem with a nice .bashrc script but I have not found _anything_ on the web regarding this <ironic>fantastic</ironic> feature of "airplane mode".

Anybody out there who can help? 

Thanks

/Tom
---
Asus Zenbook Prime UX31A R4003X

---

### Post by PikoMedia on 2012-10-21
Quick update on the topic:

I played around with taking the wireless up and down:
[FONT="Courrier New"]sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
[/FONT]
==> does not resolve the issue 
If "Aiplane mode" is _off_, you can bring the wireless up and down as you wish. On the other hand, if "Airplane mode" is _on_, ifconfig wlan0 up/down has no effect.

I attempted to restart the network manager to see what hapened.
[FONT="Courier New"]sudo service network-manager restart[/FONT]
If airplane mode is off, the restart shuts down, and then when the network i brought up again, the Airplane mode is ON again.
If the airplane omde is on, the restart does not have any effect at all.

Seems like at startup, whatever reason for the startup of the wireless, airplane defaults to "on".

Not much of progress so far. I still have not found anything on "Airplane mode" and how to switch it on and off from the cli.

Next I'll go and dig in the logs to see if there is some trace that can give me a clue or two.

---

### Post by PikoMedia on 2012-10-21
Did some further digging and found [this]("http://www.linuxquestions.org/questions/linux-networking-3/cant-get-rid-of-airplane-mode-in-ubuntu-11-10-a-912031/") post where the issue is similar.

If I run 
[FONT="Courier New"]rfkill list[/FONT]
[...]
[FONT="Courier New"]1. asus-wireless LAN
soft blocked yes
hard blocked no
[/FONT][...]

runing 
[FONT="Courier New"]rfkill unblock 1[/FONT]

does not have any effect at all. Note that even if the interface is stated as being soft blocked, it _is_ up and running(!)

Still don't have a clue...

---

### Post by PikoMedia on 2012-10-25
New observation: The system settings > Network dialogue box always defaults to "airplane mode on", no matter what the actual wireless state is. That is to say that if I have wifi up&running, then go to system settings > networks, the airplane mode is "on" even when I'm using the wifi!

There seems to be two problems here:
a) On boot and resume wireless is disabled by default.
b) upon access to "system settings > networks" airplane mode is on no matter what.

---

### Post by PikoMedia on 2012-11-13
Any ideas on what I can investigate or any logs I could pull and post? Anything? Anyone?

---

### Post by HermanH on 2012-12-06
I has this same problem on my new Asus Zenbook Prime under Ubuntu 12.10. Wireless was always off on boot or resume. Airplane mode was always on and I could not turn it off, but I could turn on the wireless despite that. It fixed itself after I hit Fn+F2 (wireless on/off keyboard function) a few times. I could then turn Airplane mode off via System Settings and it stayed off through a reboot (and wireless stayed on).

---

### Post by PikoMedia on 2012-12-06
Thanks HermanH! As simple as that! I pressed alt+F2 and it looks like the problem is solved. 

Caveat: Pressing alt+F2 turns on/off both wifi and BT. I had trouble with serious interference between wifi and BT while running 12.04, so I permanently turned BT off. However, I've upgradet to 12.10 since, and I have not seen the same wifi/BT problem again, so far.

---


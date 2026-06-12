---
title: "WMP300N Wireless Help"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by bvill on 2009-09-07
I am an absolute newbie to Ubuntu but am learning. I am trying to get my 9.04 64 bit system set up but am having trouble with my wireless adapter. I have a dual boot system with Windows XP Pro 32 bit and Jaunty 64 bit. My wireless adapter in Linksys WMP300N and it works fine in XP. I have spent hours trying to configure it by browsing the forums and help sections but am still having trouble. I installed ndiswrapper and used the instructions to install bcmwl5 driver and blacklist bcm43xx. It looks like the device is recognized in lshw but I get no wireless options in Network Manager. I found what I think is an updated bcmwl5.inf driver from Linksys. Could it be that the driver I installed does not have 64 bit support but the new one I found does? If so how do I uninstall the original bcmwl5 driver and install the new one? I am a complet novice at the terminal so I apologize in advance. If anyone could hold my hand and walk me through some suggestions, I would really appreciate it. I am looking forward to migrating away from Windows, but still have a lot to learn. Thank you in advance.

---

### Post by Cuba71 on 2009-09-08
AFAIK the WMP300N comes in two versions: v.1 uses bcm43xx driver and v.2 [168c:0023] uses madwifi driver.

Here's a link for madwifi:  [http://madwifi-project.org/]("http://madwifi-project.org/")

---


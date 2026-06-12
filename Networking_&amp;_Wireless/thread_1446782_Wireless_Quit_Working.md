---
title: "Wireless Quit Working"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by wblogan on 2010-04-04
My son set up a home computer network using a Netgear wireless router connected to a dell desktop, uname -a output:

"Linux dell-desktop 2.6.22-16-generic #1 SMP Mon Jan 26 00:07:52 GMT 2009 i686 GNU/Linux"

The dell-desktop is the computer with the internet connection. We switched from dialup to DSL,	purchased an "Embarq Model: EQ-660HW ADSL Gateway" modem/wireless router, reconfigured the interface and the desk-top connects to the internet properly. 

However, I could not connect to the new router with my laptop as I had been doing. I'm using a Dell XPS 1530, uname -a output:

"Linux dell-laptop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux"

At first the laptop found the router, but I could not get it to connect. I poked around a bit with the Network Connections with no luck. I plugged the ethernet cable into the laptop and can connect to the internet successfully. 

Problem is the wireless is apparently gone. I can do "iwlist scan" and it finds the router, but it no longer appears under Network Connections, and I cannot use my wireless mouse. Furthermore, I am experiencing some strange behavior in my x session; namely when I click on an taskbar icon to open an application it works for a while then quits and never opens the application. Also, the keys on the keyboard cease to function properly. Only thing I can do is power off. If I use ALT-F4 and switch to another session, I can log in, get a prompt, but when I issue a command it does nothing - doesn't execute the command and doesn't return to the prompt. Again, I must hit the kill switch and reboot. After rebooting the system will appear to work properly for a while, I still have no wireless, then I have to kill the power and reboot.

My son is gone and cannot help me. I've search the forums and Google and am lost. Any help will be appreciated. TIA.

---


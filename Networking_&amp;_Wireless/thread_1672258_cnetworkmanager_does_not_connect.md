---
title: "cnetworkmanager does not connect"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by thEClaw_ on 2011-01-20
Short version:
cnetworkmanager shows "Entering mainloop" but does not continue to "Connecting", it just runs without success.
The WLAN-USB-stick seems to be working, "cnetworkmanager -n" (i think that's the switch) shows me all access points surrounding me. I want to connect to a wpa2-network, the syntax i use is triple-checked.
The whole system is a Ubuntu 10.10, freshly installed without any graphical user-interface.

Long version:
Hello there,
after having been able to kind of figure out linux on my own for quite a while i now got problems with my network-connection. Something completely new :P.
I am using a laptop with an attached WLAN-stick, i am running Ubuntu 10.10. Until some days ago i did not encounter any problems (i was using Xubuntu 10.04), a little mistake while booting my second operating system (Windows 98) crashed the whole system and i decided to set it all up again.

So i installed Ubuntu 10.10, using the alternate-cds (x86). I used the option to install a pure commandline-version of the system, hence i am completely limited to the commandline - and lacking any network-connections.
With the help of another pc i got me some packages, especially the cnetworkmanager (0.21.1 i think) and its dependencies - i have to connect to a wpa2-wlan and cnetworkmanager was working fine with my faded Xubuntu.
I do not really remember what i did the last time i set up my laptop but it seems i left something out since running cnetworkmanager does not successfully connect me to a network.

Up to now i reinstalled the system three times, hoping to uncover a mistake somewhere. But after telling cnetworkmanager to connect to a network (syntax ist correct, i even reused an old script) i just get "Entering mainloop", never do i see "Connecting..." or anything further. It seems, something isn't right and i am completely out of ideas about it.

Up to now i just installed some packages (vpnc, emacs, cnetworkmanager and lynx) and i configured grub. Despite that the system should be untouched.
My WLAN-stick seems to work, it is listed under ifconfig and iwconfig and cnetworkmanager is able to give me a list of all available access-points through it. The stick uses some driver included in the kernel (zd1211rw i think), it runs fine with a live-cd and probably with a full installation of Ubuntu - but for performance-reasons i have to use the commandline.

If any printouts of commands are needed, i will supply them. But i am hoping for a simple solution, after all the system has been working until some days ago.

Thanks in advance, hopefully somebody will enlighten me.

---


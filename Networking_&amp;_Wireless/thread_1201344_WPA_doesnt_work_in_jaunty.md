---
title: "WPA doesnt work in jaunty"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by Virtualboxbuntu on 2009-07-01
Hello,

I use Kubuntu Jaunty on my desktop. Or at least, I'd like to. I use WPA security on my wireless router, and Jaunty's network manager won't connect to it. Apparently other people also have this problem. My wireless adapter works quite fine in the KDE 3 network manager and Gnome's network manager.

What should I do to make it work with my WPA security? And if you want me to install some other program, just how do I do that if I have no Internet?

In case you're wondering, my laptop has Internet.

---

### Post by Virtualboxbuntu on 2009-07-03
I solved this by temporarily disabling my WPA security while installing the gnome network manager.

---

### Post by Erbid on 2009-07-03
Update 2009-07-06:  

I reloaded Ubuntu 9.04 and updated everything using a wired connection, and rebooted.
I then downloaded the closed source STA driver (and the NVidia video driver) using the "Drivers" tool.
I then used the "attach to a hidden network" option from the NetworkManager status bar icon.
Result:  WPA PSK connection to a "hidden" network, reliable through reboots and hibernates.


(edited to save someone the hassle of what I did earlier, which follows)

I used apt-get install wicd to clear things up at last.  Yep, apt-get needs internet.

(see also [https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/339313](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/339313) )

What finally worked for me was using wicd.

The first solid connection I got from my wireless was when I broadcast my SSID.  But after I went and disabled broadcasting the SSID again, the wireless connection would not stay connected or re-establish.  

WPA + no broadcast SSID = "use wicd"!

Step by step:

sudo apt-get install wicd
sudo reboot (To get the nice gui tool wicd-client to go.)

Erbid

> **Virtualboxbuntu said:**
> 
What should I do to make it work with my WPA security? And if you want me to install some other program, just how do I do that if I have no Internet?

In case you're wondering, my laptop has Internet.

---

### Post by lucloubier on 2009-07-04
> WPA + no broadcast SSID = "use wicd"!

This is true after the latest ubuntu update was applied last night on my IBM laptop T41, but that still does not work on my eeePC 1000HE though !

---

### Post by Erbid on 2009-07-06
I reinstalled Ubuntu 9.04, and installed all the updates using a wired connection, and rebooted.
I then downloaded the closed source STA driver (and the NVidia video driver) using the "Drivers" tool.
I then used the "attach to a hidden network" option from the NetworkManager status bar icon.
Result:  WPA PSK connection to a "hidden" network, reliable through reboots and hibernates.

No more "problem" for me.  Minor problem resolved by using the STA proprietary Broadcom driver.  Pretty much as expected.

Not using Kubuntu this time, could that have been a factor requiring wicd?

Erbid

---

### Post by dksmiffs on 2009-07-12
> **Virtualboxbuntu said:**
> I use Kubuntu Jaunty on my desktop. Or at least, I'd like to. I use WPA security on my wireless router, and Jaunty's network manager won't connect to it. Apparently other people also have this problem. My wireless adapter works quite fine in the KDE 3 network manager

What should I do to make it work with my WPA security?

           I got my Kubuntu Jaunty, SSID not broadcasted, WPA-PSK setup working. My prior problems were very similar to the portion of @Virtualboxbuntu's post I quoted above. Here's a writeup of my configuration, and the steps I follow to make plasma-widget-network-manager work:

 [http://uncleham.wordpress.com/2009/07/11/kubuntu-904-wpapsk-nobroadcast/](http://uncleham.wordpress.com/2009/07/11/kubuntu-904-wpapsk-nobroadcast/)

---


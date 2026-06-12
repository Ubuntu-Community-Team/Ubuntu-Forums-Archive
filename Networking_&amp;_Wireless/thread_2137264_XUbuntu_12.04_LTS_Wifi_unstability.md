---
title: "XUbuntu 12.04 LTS Wifi unstability"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by arodulfo on 2013-04-20
Dear all,

I have been fiddling with the Intel Cebtrino Wireless-N 2230 wlan adapter of my new laptop.
At first, I made I fresh install, out of the XUbuntu 12.04 LTS 64 bits disk.
I checked the options for downloading updates while installing and for third party sources, so those files were downloaded with tha same settings the Live CD was using.

Once everything was installed and the installer told me to restart the system, the WiFi connection started to give a lot of problems.
I decided to keep going, assuming it would be a temporary problem... which it wasn't.

I have googled for solutions and followed many different hints I found on forums, starting with Ubuntu Forums, but not being limited to. I have also followed hints for Red Hat, Mandriva, Arch Linux, and some other ones...
None of the gave the proper solution to the problem.

I decided to try a different approach. 
Using my brand new system and the installation disk as Live CD, I tried to stress the wifi connection to the max.
No problems at all!

I did a new install, from scratch, unchecking third party software and updates downolads boxes.

When using the Live CD, the WiFi connection information pane shows some 130 to 144 Mb/s and keeps downloading and playing more than twelve YouTube videos at once.
The system I installed XUbuntu on has an Intel Core i7-3632QM PPGA988/2,2GHz/Ivy, with 16 GiB and a GEForce GT635M.
When the first install reached its end, the system was running 12.04.2. After the second one, the system was running 12.04. None of them was capable of properly using WiFi.

Some forums do recommend to disable the 11n option in the adapter. I have been unable to get any useful result of using "iwconfig wlan0 modu 11b 11g" (the system says it is an unknown command).
If I try to do it through modprobe, it says the options are not reconginzed, or something similar. 

"uname -a" says I am effectively installing an x86_64 system, and that the Live CD is an x86_64 system as well.
"lspci" says it finds an Intel Corporation Centrino Wireless-N 2230 (rev c4) adapter (along with a Realtek Semicond. Co., Ltd. Device 5289 rev 01 unassigned [ff00])

What else can be done? May I look anywere else? I have XUbuntu installed in all my family PCs, both desktops (2) and laptops (4, not including the new one)... 
I have also posted a help request to the manufacturer of the machine, a German company called Wortmann, but their answer will take time to arrive.
They are not a Windows shop, but seem to pay more attention to it than to Linux (nothing unusual in this market, anyway)

I hope anbody will come with some help. Thanks in advance...

---

### Post by arodulfo on 2013-04-23
Dear all,

Given that I've been looking for a solution to this matter, I have received help from many sources.
One of those hints seem to have solved the issue. Well... sort of.

First of all, I will summarize here what I have done:
* Fresh install of XUbuntu 12.04 LTS 64b
* Open a terminal
* [FONT=verdana]Enter the orders:

```

[COLOR=#000000]echo "options iwlwifi [/COLOR][COLOR=#417394]11n_disable[/COLOR][COLOR=#000000]=1" | sudo tee /etc/modprobe.d/iwlwifi.conf[/COLOR]
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```

You can read the full thread I did following [this link]("http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable").
This way, you get rid of the WiFi-N capabilities of your Intel Centrino 2230 adapter. I tried the hint and it works.[/FONT]:popcorn:[FONT=verdana] Now I have 54 Mb/s consistent connection to the router and all my wlan activities run quite smooth.[/FONT]:)[FONT=verdana]

After reading several posts, the core problem seems to be related to the way different companies implement the matching standard. Intel seems to have taken the strict approach and, when contronted with a more relaxed implementation on a router, the adapter seems to fall back to silence.

However, even though I have control over my WiFi adapter now, it doesn't mean I have a couple of unsolved questions:
* I have an adapter with added capabilities I won't be able to benefit from
* Using the Live CD option (with the same support I used to install 12.04 LTS on my laptop) I was 100% capable of using all those capabilities, bringing my WiFi connection speed to a whopping 144 Mb/s; even if that speed can't be kept 100% of the time, the miimum speed I saw was around 130 Mb/s.

If the Live CD option can fully use the adapter, why an actual install can't perform as well?
Where's the difference? Am I doing anything wrong? Am I forgetting anything?[/FONT]:confused:[FONT=verdana]

Thank you so much for being there!



[/FONT]

---


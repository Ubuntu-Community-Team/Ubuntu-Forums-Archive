---
title: "Network-Manager meets the indicator applet"
date: 2010-11-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Framli on 2010-11-24
Hi fellow testers,

1) Mathieu Trudel, long time nm contributor has set up a PPA for a patched *network-manager*, that proudly shows up on Unity's panel in his glorious indicator's shape.

2) The UDS plans are to make Network-Manager a back-end for *indicator-network* aka Network Menu (which actually uses ConnMan as a back-end).

3) Network-Manager already has a great config interface we all know and the mock-ups for indicator-network interface are great too, but they are only mock-ups. ( [https://wiki.ubuntu.com/Networking](https://wiki.ubuntu.com/Networking) )

4) Let's hope those talented guys : Kalle Vallo and Mathieu Trudel, meet, have cake and decide to work together.

**PPA for nm-applet indicator**
[https://launchpad.net/~mathieu-tl/+archive/nm-indicator](https://launchpad.net/~mathieu-tl/+archive/nm-indicator)

**PPA for indicator-network**
[https://launchpad.net/~indicator-network-developers/+archive/daily-ppa](https://launchpad.net/~indicator-network-developers/+archive/daily-ppa)

---

### Post by hugmenot on 2010-11-24
Doesn’t really work here. I get a menu in the indicator-application area with the former nm-applet left-click and right-click menu concatenated (ugly, long) but where the wireless networks should be there’s only empty menu entries. 

And the thing flickers every few seconds.

---

### Post by cariboo on 2010-11-24
I created a bug report about the problem earlier this week Bug# [lpbug]680298[/lpbug].

---

### Post by zekopeko on 2010-11-25
> **Framli said:**
> Hi fellow testers,

1) Mathieu Trudel, long time nm contributor has set up a PPA for a patched *network-manager*, that proudly shows up on Unity's panel in his glorious indicator's shape.

2) The UDS plans are to make Network-Manager a back-end for *indicator-network* aka Network Menu (which actually uses ConnMan as a back-end).

3) Network-Manager already has a great config interface we all know and the mock-ups for indicator-network interface are great too, but they are only mock-ups. ( [https://wiki.ubuntu.com/Networking](https://wiki.ubuntu.com/Networking) )

4) Let's hope those talented guys : Kalle Vallo and Mathieu Trudel, meet, have cake and decide to work together.

**PPA for nm-applet indicator**
[https://launchpad.net/~mathieu-tl/+archive/nm-indicator](https://launchpad.net/~mathieu-tl/+archive/nm-indicator)

**PPA for indicator-network**
[https://launchpad.net/~indicator-network-developers/+archive/daily-ppa](https://launchpad.net/~indicator-network-developers/+archive/daily-ppa)

This is great news. The spec looks really good (then again mpt's work is always excellent). I hope this makes it in Natty.

---

### Post by suoko on 2010-11-30
what about bluetooth ?
is anyone still consindering it ?

---

### Post by Framli on 2010-11-30
Network-Manager indicator is now default and will be for Natty.

This is really awesome news as Kalle Vallo is continuing is work on ConnMan. Resulting in stability AND consistency from N-M in Natty, then new shiny network management to come in 11.10...

---

### Post by bash on 2010-11-30
Don't have Natty set up yet, so anyone feel like providing a screenshot or two?

---

### Post by hugmenot on 2010-11-30
Now it’s in the default seed and completely ****ed up. Great.

I can’t connect to my wireless anymore and suddenly it respawns all the time and pegs both cores at 100%.

---

### Post by cariboo on 2010-11-30
Here's a screen shot

---

### Post by Red_Steve on 2010-12-04
Installed on my 10.10 box. works near flawless, the menu only sometimes blinks as if something is reloading. But it's a minor graphical glitch, nothing that impairs it's functionality. Untill connman is able to provide an interface to manage vpn connections this will server me well.

Great find, thanks!

Edit: oh snap. now seeing that it has some sort of memory leak gradually eating up my RAM.

---

### Post by cariboo on 2010-12-04
I just noticed in my screen shot that it doesn't differentiate between secured and unsecured networks. One of the ap's in the screen shot is wide open and the other is secured using wpa.

---

### Post by screaminj3sus on 2010-12-07
> **cariboo907 said:**
> I just noticed in my screen shot that it doesn't differentiate between secured and unsecured networks. One of the ap's in the screen shot is wide open and the other is secured using wpa.

Yeah that's definitely not good, hopefully it gets fixed.

---

### Post by Starks on 2010-12-07
nm-applet is still memory leaking like a sieve

---

### Post by ronacc on 2010-12-07
there may be a new indicator but there is still the memory leak .

---

### Post by Quackers on 2010-12-07
I think it's actually worse. Mine's up to 117.3MB and it's only been on for 4 hours.

---

### Post by Starks on 2010-12-07
Doesn't even take an hour to balloon to over 100MB on my machine.

---

### Post by ronacc on 2010-12-07
I keep checking jimml's bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599)  its confirmed and lots of me too's but still unassigned , they better get off their butts and take this seriously .

---

### Post by castrojo on 2010-12-07
> **ronacc said:**
> its confirmed and lots of me too's but still unassigned , they better get off their butts and take this seriously .

Great attitude!

---

### Post by ronacc on 2010-12-07
I simply mean that a memory leak of this magnitude in a critical app should be high priority . Correct me if I am wrong but nm-applet seems to me to be a very critical app .

---

### Post by ratcheer on 2010-12-08
My nm-applet is currently using only 11.7 meg. I've had Natty up for about an hour.

Tim

---

### Post by afv on 2010-12-10
Heh, nm-applet using 640 MiB after 20 hours of uptime…

---

### Post by efflandt on 2010-12-10
It seems to be fixed now.  I don't know if it is an accepted method to do updates, but I boot to (recovery) and select dpdg to "fix packages", it did a bunch of updates (removed 3).  I shutdown, booted, selected the regular kernel and ... it rebooted.  Oh well, rebooted the (recovery) kernel, did nothing, shutdown and rebooted, and everything worked fine into Unity.

nm-applet is now 3.9 MB and NOT growing at all.  So I don't know if that was risky with the python changes taking place, but what fun would it be without any risk.

PS: Maybe I spoke too soon, in the hour since I posted, nm-applet has grown from 3.9 MB to 4.4 MB, but that is much slower than it was growing before.  Whatever network manager is used in Kubuntu natty stays right at 3.8 MB and I have never seen that change.

---

### Post by cariboo on 2010-12-10
> **efflandt said:**
> It seems to be fixed now.  I don't know if it is an accepted method to do updates, but I boot to (recovery) and select dpdg to "fix packages", it did a bunch of updates (removed 3).  I shutdown, booted, selected the regular kernel and ... it rebooted.  Oh well, rebooted the (recovery) kernel, did nothing, shutdown and rebooted, and everything worked fine into Unity.

nm-applet is now 3.9 MB and NOT growing at all.  So I don't know if that was risky with the python changes taking place, but what fun would it be without any risk.

There's no need to boot in recovery mode to do updates, you can do them from a terminal on the desktop. The power button in the top right corner turns red when a reboot is required to complete the update.

---

### Post by Red_Steve on 2011-01-16
Any news about the status of the memory leak? I would love to get the indicator for my 10.10 but this memory leak makes it useless to test.

---

### Post by efflandt on 2011-01-16
I don't think it has been totally fixed yet.  But it is much slower than it was.  In 8 hours of uptime it only grew from 4.2 GB to 9 GB.  It still throws an error occasionally in .xsession-errors, but not that you would notice.  So that is no reason not to try it if you have some extra drive space and a sense of adventure.

(nm-applet:1499): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nm-applet:1499): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

** (nm-applet:1499): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/4: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

** (nm-applet:1499): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/4: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

---

### Post by shrimpy89 on 2011-01-17
It still leaks here. 200.4 MB after 6 and a half hours of uptime.

---

### Post by nyex on 2011-01-25
Hey all,

I'm on Maverick and since the nm-applet turned into an app indicator, even though I can choose wireless networks, it won't let me edit connections (I click it, nothing happens, so far I didn't NEED it, but I'll need it in the future), and when I click "more networks" (I have it in Portuguese, not sure that's how it says in English) nothing happens either.

(Also can't see signal strength and whether or not the network is protected, which can be annoying when you're searching for the right network at a cafe or something.)

Any chance this is getting fixed soon or maybe a way I can go back to the old network manager?

Thanks :)

~o.

---

### Post by Harry33 on 2011-01-25
> **nyex said:**
> Hey all,

I'm on Maverick ...



This is Natty development discussion forum. ;)

---

### Post by hugmenot on 2011-01-25
> **nyex said:**
> Hey all,

I'm on Maverick and since the nm-applet turned into an app indicator [...]

Any chance this is getting fixed soon or maybe a way I can go back to the old network manager?

Thanks :)

~o.

If you really want the Maverick nm-applet back you can find it here:
[http://packages.ubuntu.com/maverick/network-manager-gnome](http://packages.ubuntu.com/maverick/network-manager-gnome)

But how did you get to install Natty’s nm-applet in the first place?

---

### Post by ComputerJy on 2011-01-28
> **shrimpy89 said:**
> It still leaks here. 200.4 MB after 6 and a half hours of uptime.
Use the following command whenever you feel like it's eating more and more of your memory
"*killall nm-applet && nm-applet --sm-disable &*"

You can set it up to run automatically every 15 minutes or so if you want

---


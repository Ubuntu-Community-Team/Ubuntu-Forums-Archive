---
title: "Wireless connected but no connection (Intel Corporation Centrino Wireless-N 130)"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by Psycho Game on 2012-03-15
Hello everybody,

I have a problem which I can't solve on my own.
I've just bought a new laptop (Samsung NP300E7A-S01NL), which has a Intel Corporation Centrino Wireless-N 130 card.
I have Xubuntu 11.10 installed with the xorg-edgers ppa enabled, because of a graphics bug I had earlier.

Now the problem is that the network is connected.
Sometimes there's no problem, and I am able to get on the internet.
But after some time, or intensive use of the network card, for example downloading updates etc. the connection suddenly stops.
The signal strength logo indicates that it's still connected, but I can't open any internet sites anymore. Also downloading the update files stop, so in my opinion the complete network is unreachable.
Although when looking at the connection information it still shows that it has acquired an ip-adress through DHCP.

What I already tried was to get the newest linux-firmware from the precise repositories, and installed them by hand with dpkg. Unfortunately the problem still persists. I tried to search for this particular problem with google first, but couldn't find any good posts with a solution that seemed to work for me. This was also where I found a solution to install the newest linux-firmware.

It's a very annoying problem, because I constantly have to reconnect to the network whenever this problem occurs. And unfortunately that's not once a day. So hopefully somebody with more knowledge on wireless network cards can help me find a solution for this problem.

The output of the lspci -v command is:
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 130 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at e1500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

When I need to deliver more information, feel free to ask.

Greetings Psycho Game

---

### Post by Psycho Game on 2012-03-16
Already found out the solution to this problem as well.
As I already thought it was the 802.11n support which was giving problems in the driver.
For some reason the implementation of this support is still quite buggy.
The solution was already in the collection of forum posts I found earlier, only I applied them wrong.
The driver my wireless card uses is the iwlwifi.
One of the solutions was to put "options iwlagn 11n_disable=1" (Without the quotes) in a file called iwlagn.conf in /etc/modprobe.d, only this didn't solve the problem for me.
This was because I applied it to the wrong driver, namely the iwlagn driver.
When I made a new file called iwlwifi.conf in /etc/modprobe.d, and added the line "options iwlwifi 11n_disable=1" (Again without the quotes) and restarted the computer the problem seemed to be solved.
Hopefully by reporting this solution back, I'm able to help other people with this problem as well.

Greetings Psycho Game

---

### Post by pfindan on 2012-06-03
Thank you do much! This helped me a lot!

---


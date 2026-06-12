---
title: "An Open Letter to Mark Shuttlesworth and other Linux Developers about WiFi's limits"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Total Noob on 2009-03-14
Dear Mr. Shuttlesworth and other developers:

Many of us have been banging our heads over getting Linux distros to work with wifi, a huge problem since Linux desktops are pretty much useless without a broadband connection.

There is page upon page upon page in forums like this one containing gripes about connecting, and I suspect that most people -- the hobbyists on these pages -- just assume the OS or poor drivers are the culprits.

That is only partly true; the software works and can work well. I just found out what the problem really is, and I'm telling you fixing this has to be a first priority.

It turns out that Linux wifi is way, way too sensitive to signal strength. The software works just fine -- provided you are not more than 8 or so meters away from the transmitter. Which seriously defeats the purpose of having wifi.

I'm using a Compaq Pentium 3 with a USB wifi dongle, all of which works just fine when the computer is booted with Windows 98SE. The computer is across the house from my router, about 8 or 9 meters or so, and the register reports a good signal in the 60% range with either Windows or Ubuntu.

But running on Ubuntu 8.10, the 60% is not good enough. I may get the name of my website on the tab, but that is it. Occasional spikes of 70% draw a little more, then it stops.

I put the dongle on a USB extension cable that is 4 feet long, and there was no improvement with Ubuntu.

So I added a 6 foot second extension cable, stretched it in the direction of the transmitter -- of course I can't keep it there because it blocks the entranceway -- so that the dongle is now only about 16 feet away from the transmitter, and voila, it works perfectly. I regularly hit 90% signal, and have no problem whatever. Excpet if I try to move the dongle at all. No matter how carefully I try, the connection drops plus the network manager crashes for good and I have to reboot, so that is just bad software.

The lessons: First, I think this phenomenon has escaped notice because I don't think anyone who has been struggling with this has ever realized that a one or two meter location change with respect to the transmitter is the difference between total failure and total success. I think nobody previously understood how much the signal strength dropoff impacts performance with Linux. That is contrary to the Windows experience, where a weak signal is fine, moving around a little does not cause a crash, and the distance required to be really out of range is much further.

Second, wifi should work at a distance of more than 6 meters within a house for certain, and I shouldn't have to stretch wires all over my house to have wireless service, it is asinine. My XP laptop works at 30 or 40 meters. I don't know why the signal strength drops off so radically over the distance between 6 and 8 meters out, but a computer should be able to use 60% and still work well, as does my laptop.

Third, the issue of making a fix a priority. If you developers are targeting casual computer users in addition to the hard core hobbyists, you also have to realize they want wifi. And they want to run it on old junk and leftovers as backup computers, like my P3, and they are putting them in basements, spare rooms and so forth.

No wifi means no casual Linux user dabblers/supporters, and ultimately no Linux.

---

### Post by mobilediesel on 2009-03-14
I'm pretty sure the wifi adapter manufacturers are mostly at fault. Just like all hardware: If the manufacturer doesn't support the OS, drivers are going to suck. Users are going to have to reverse engineer the signals going to and from the hardware in order to make a driver that works.

Linux users should stop buying new wifi adapters altogether. Only buy used adapters until the hardware makers support your OS.

---


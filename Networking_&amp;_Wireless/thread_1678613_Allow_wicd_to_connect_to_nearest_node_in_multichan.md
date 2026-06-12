---
title: "Allow wicd to connect to nearest node in multichannel wifi network?"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Afisamuleal on 2011-01-30
At college, many wireless network signal extenders are installed: when viewed through wicd, there are at any given place 20 networks of the same name, each of varying signal strengths. When using NetworkManager, I see one network with the same name, and network manager automatically connects to the channel with the strongest signal strength.

Is there a way to enable this functionality in wicd? I like the power of being able to select among access points, and in general the functionality of wicd better, however it is extremely inconvenient in this setting.


An aside: yesterday I successfully used the [bug]("https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/555403") which allows wicd and network manager to be installed at the same time by means of some very elementary commands to stop/start either of the conflicting daemons, allowinging me to switch back and forth between wicd and network manager with relative ease. Unfortunately, my terminal doesn't seem to have recorded *those* specific commands, and I can't find a service named NetworkManager anymore. network-manager exists, but I specifically remember disabling NetworkManager. Protip?

---


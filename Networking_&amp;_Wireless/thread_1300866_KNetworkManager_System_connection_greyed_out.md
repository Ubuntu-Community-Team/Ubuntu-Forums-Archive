---
title: "KNetworkManager: System connection greyed out"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by dentharg on 2009-10-25
Hi!

I've configured my wireless connection with KNetworkManager and it works perfectly. However it works only when I log in.

I am unable to select it as a system connection (directory /etc/NetworkManager/system-connections exists). See screenshot:

[http://imagebin.ca/view/iK3xfyj.html](http://imagebin.ca/view/iK3xfyj.html)

Please advise. I would like to have it connected even without logging in.
I've tried copying NM settings from my .kde to the /etc/.. directory but without success.

---

### Post by alpeterson on 2009-11-01
This is happening to me too.   I'd like it to be available to everyone on the system, without being able to see the password.

in 9.04 it was worse,  it would disconnect when logging back in after the screen went off...   So if I was downloading something, I would have to not touch the computer if the screen saver went on.. but then guess how long it would take... because going back would have disconnected the network!

Now it's just back to the basic problem where I want to be able to log into it etc via wireless ssh... and keep all users from seeing my wep key, but still have access.

---

### Post by Dimath on 2009-12-24
Bump.

---

### Post by janvkn on 2010-01-03
Apparently this functionality simply hasn't been implemented yet in the KDE network manager.

See: [https://bugs.kde.org/show_bug.cgi?id=204340](https://bugs.kde.org/show_bug.cgi?id=204340)

I did manage to get wireless-on-boot working by following these steps:

1. Install the gnome network manager:
```
sudo apt-get install network-manager-gnome
```

2. Kill the knetworkmanager process in your KDE session:
```
killall knetworkmanager
```

3. Start the gnome network manager applet:
```
nm-applet
```

4. Now you can configure the wireless connection with the gnome applet and check the "available to all users" check box. You will be asked for your sudo password. If all is well, it should have created a file for your connection in /etc/NetworkManager/system-connections/ which is readable by root only.

5. Reboot your system. After the reboot, your wireless connection will come up before you login.

---

### Post by Justin Trouble on 2010-01-12
> **janvkn said:**
> Apparently this functionality simply hasn't been implemented yet in the KDE network manager.

See: [https://bugs.kde.org/show_bug.cgi?id=204340](https://bugs.kde.org/show_bug.cgi?id=204340)

Thanks for that!
I've been searching off and on for months heh :P

---

### Post by FryinRyan on 2010-07-25
> **janvkn said:**
> Apparently this functionality simply hasn't been implemented yet in the KDE network manager.

See: [https://bugs.kde.org/show_bug.cgi?id=204340](https://bugs.kde.org/show_bug.cgi?id=204340)

I did manage to get wireless-on-boot working by following these steps:

1. Install the gnome network manager:
```
sudo apt-get install network-manager-gnome
```

2. Kill the knetworkmanager process in your KDE session:
```
killall knetworkmanager
```

3. Start the gnome network manager applet:
```
nm-applet
```

4. Now you can configure the wireless connection with the gnome applet and check the "available to all users" check box. You will be asked for your sudo password. If all is well, it should have created a file for your connection in /etc/NetworkManager/system-connections/ which is readable by root only.

5. Reboot your system. After the reboot, your wireless connection will come up before you login.

Thank you sir, this helped me get rid of this most ridiculous problem! I cannot believe they even have such a stupid bug. Knetworkmanager really needs some work.

---

### Post by Number 2 on 2010-10-18
My problem was that I wanted it to login to the network at login, automatically. And this option being greyed out seemed to be the reason why it wasn't happening.

After looking all over the place, in forums and in the system, I have found in "information sources" (this may be wrong as I have it in spanish and don't know (yet)how to turn it back into english) that there was network manager daemon called Wicd, I set this one as priority, I installed it and turned off the NetworkManager. Restarted the computer and, "voi la", it works. Automatic connection to the wireless network, as I wanted.

---


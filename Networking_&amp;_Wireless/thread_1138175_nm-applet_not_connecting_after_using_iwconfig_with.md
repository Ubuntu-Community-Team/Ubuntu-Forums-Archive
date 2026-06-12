---
title: "nm-applet not connecting after using iwconfig with ath5k"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Shootfast on 2009-04-26
Hi all,

I've installed a stripped down copy of ubuntu via debootstrap onto my eeepc. I upgraded it to jaunty and everything was fine.

Today I set about creating a script to set my wireless card into ad-hoc mode and create a connection to my iphone. My wireless card is an Atheros AR5BXB63 and I've been using the ath5k module perfectly for weeks.

I use JWM as the window manager, but run a few gnome applications to manage things like power and network.

I usually connect to my wireless network through nm-applet but after running my script, I can no longer connect to any network, even after a reboot!

Here is the contents of my script:

```

if [ "$(whoami)" != 'root; ]; then
    echo "NOT ROOT"
    exit 1;
fi
killall nm-applet
ifconfig wlan0 down
echo "wlan0 down"
echo

iwconfig wlan0 mode ad-hoc
echo "wlan0 mode ad-hoc"
echo

iwconfig wlan0 channel 6
echo "wlan0 channel 6"
echo

iwconfig wlan0 essid "linkup"
echo "essid linkup"
echo

iwconfig wlan0 key 1234567890 restricted
echo "wlan0 key set"
echo

ifconfig wlan0 up
echo "wlan0 up"
echo

```

Just some basic commands and a check for root. This script is run manually when I want to create the ad-hoc connection, and I can't see how any of these changes could break my networking enough that a reboot couldn't fix it. But alas.

Any ideas?

Thanks

---

### Post by Shootfast on 2009-04-26
Gah, Turns out my router was playing up. After a reboot and a hard reset everything seems back to normal.

Just as well! I'd tried everything I could think of on the laptop side!!

---


---
title: "Ad-hoc network Connection Problems? (beyond ping)"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2011-06-25
Been trying out ad-hoc networking for a small project I have on the go at work, am currently in the testing phase with a netbook and a laptop. Both machines are running a custom Xubuntu based distro with WICD for networking, although all commands were done on the CLI. No wireless security at this stage due to testing.

These two machines are standalone and are not connected to any other network or the internet, they will just be connected to each other wirelessly for admin and file transfer

Following the wiki [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)    &   [http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html) have set up the ad-hoc network on subnet 192.254.34.x, with netbook on 192.254.34.1 and laptop on 192.254.34.2, using these commands:

```

sudo service wicd stop
sudo ip link set wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 4
sudo iwconfig wlan0 essid "STANDALONE"
sudo ip link set wlan0 up
sudo ip addr add 192.254.34.x/16 dev wlan0
```

I see the same cell on each PC

I can ping each PC from the other (although the netbook keeps dropping its IP address so I have to tell it what it is again, then ping).

When I try to ssh (both PCs have ssh client and server installed) I get a **connection closed** or **no route to host** response, even though I can successfully ping before and after. 

The wiki only takes you as far as ping, so have I missed something? And how do I stop the netbook from dropping its IP address?

Thanks

---


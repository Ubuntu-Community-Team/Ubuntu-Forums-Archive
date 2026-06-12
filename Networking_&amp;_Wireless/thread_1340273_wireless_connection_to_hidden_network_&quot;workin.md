---
title: "wireless connection to hidden network &quot;working&quot; ... I hope this helps others"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by the_lynx on 2009-11-28
Hello,

    If you are trying to get Kubuntu 9.10 to connect to a wireless network with a hidden ESSID and WEP encryption, this note _may_ help you.  Hopefully if it does not solve your problem it will at least provide a starting point.  If not, please feel free to post whatever solution you do find.

    Please note that my "solution" still needs some work (help from the developers would be greatly appreciated), but after ripping my hair out for the last two hours I thought I would share my experience.

     I upgraded to Kubuntu 9.10 from 9.04.  Wireless was terminally broken ... I would ask the plasma-widget-network-whatever to connect to an existing wireless connection, and it would silently fail.  Sad.  Wired connections "worked", but the icon on the network manager in the tray was a disconnect cable.

    After searching for and following a dozen posts telling me how files were "supposed" to look, and getting so frustrated that I started to ignore those posts, I finally modified my /etc/network/interfaces file as follows:

```

auto lo
iface lo inet loopback

```

    Do note that this is a direct contradiction of the first half dozen fixes that I found (as it contained no references to eth0 (wired) or eth1 (wireless)).  This one change caused the network manager to display a green "connected" icon for the wired network connection.

    I then re-created the wireless connection (I don't know if it is necessary, but I deleted all previous wireless connection info), and ... was unable to connect to the wireless network.  I pulled out a trick (see below) from 9.04, however, and everything was back to working.

    Wireless also started out broken in 9.04, then magically started working correctly after a patch or ten.  For the 9.04 setup "broken" means that I initially needed to create a new wireless entry every time I wanted to connect to the wireless network.  Automatic connections (obviously) failed in such a setup.  After scanning the intertubes a bit, I found a suggestion that the following command line might help (sorry, I don't have a reference to the original post):

```

sudo iwlist eth1 scan essid ESSID

```

    Once I had logged in to a session, issuing this command (from a terminal) would cause the network manager to prompt me for my password (via the wallet), and then would connect to a wireless network that was marked "automatically connect" in the network manager connection list.  It was almost as if the network manager had to be "primed" to connect to a hidden network.

    So, KDE network manager devs ... can you re-apply the patch from 9.04x that caused automatic network connections to function for hidden networks ?

---


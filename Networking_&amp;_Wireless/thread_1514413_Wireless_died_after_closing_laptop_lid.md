---
title: "Wireless died after closing laptop lid"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by Eviltechie on 2010-06-21
I was connected to wifi, and I closed my laptop's lid. Now, I can't connect to any wireless networks, nor do any show up as available to be connected to. I've tried rebooting several times now, but my wireless connection still isn't working. The wired connection works fine.

It's a 2wire router, broadcasting ssid, no encryption, mac address filtering. There is another wireless device on the network that seems to be working fine, and I don't think that it is the router, because the neighbors encrypted connection was showing up, and isn't any longer.

---

### Post by llanitedave on 2010-06-21
I'm having the same problem, on a Dell Vostro 1720.  I'm also using Wicd Network Manager.  When I reopened my laptop lid, it shows my network, but fails to connect with a "bad password" error.  

I'm dual-booting with Windows 7, and the Windows side still connects just fine, which is just rubbing salt on the wound.

I've tried rebooting multiple times, and switched between Gnome and KDE, and the problem remains.

My System Log shows wlan0 authenticated, then a couple of messages later it reports "AP denied association (code=12)".
Then it reports "deauthenticating from nn:nn:nn:nn:nn:nn by local choice (reason=3)".

That's not too informative for me, but if there's a corrupted configuration file somewhere it would be nice to find it.

I hope the same fix works for both Eviltechie and me.

---

### Post by llanitedave on 2010-06-21
Well, I got my problem fixed, and I don't think it's the same one as Eviltechie had.

Apparently when I installed Wicd, network-manager didn't uninstall properly.  The last time I cycled the lid is the time it chose to create a conflict with Wicd.

I browsed these forums until I found the following solution, which worked for me:
```
sudo apt-get remove network-manager
```

Once all the messages finished scrolling and I got back to the prompt, I entered
```
sudo /etc/init.d/wicd restart

```

For Eviltechie, I might recommend that if nothing else seems to work, that you can get good results by installing Wicd.  My network manager cratered a couple of months ago, and nothing I could do would get it working again.  I installed Wicd and it's run without a hitch until tonight.  And that seems to have been caused by a zombie network-manager anyway.

---


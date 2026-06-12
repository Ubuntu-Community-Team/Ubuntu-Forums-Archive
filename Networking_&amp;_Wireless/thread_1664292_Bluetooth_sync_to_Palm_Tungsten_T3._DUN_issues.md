---
title: "Bluetooth sync to Palm Tungsten T3. DUN issues"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by ScarletPea on 2011-01-10
I have just aquired a Palm Tungsten T3 and am trying to get sync/network via bluetooth working in Natty.

 Sending files via bluetooth works fine.

I have tired:
 [http://howto.pilot-link.org/bluesync/ga.html](http://howto.pilot-link.org/bluesync/ga.html)
 [http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html)
 [http://lindajane.wordpress.com/2008/11/02/palm-centro-hotsync-via-bluetooth-on-ubuntu-810-intrepid-ibex/](http://lindajane.wordpress.com/2008/11/02/palm-centro-hotsync-via-bluetooth-on-ubuntu-810-intrepid-ibex/)

 Basically they follow the same idea, setup a ppp connection by invoking 
```
dund --listen --persist --msdun call dun
```

When I attempt to connect from the palm I see no output in the terminal, and the following error on the palm:
```
Error:Serial:
timeout. Could be bad cable or faulty Modem. (0x0305)
```
This error persists whether dund is running or not.
 
Sometimes in rare circumstances I get a ppp timeout instead.

 I am wondering if there is a 'correct' way to do this as the bluetooth architecture has changed drastically since these howtos were written.

Connecting with rfcomm works fine, for whatever good that is 8)

Cheers.

---

### Post by ScarletPea on 2011-01-14
The kind people at #bluez-user helped me through this.
It turns out that a plugin for maeomo is getting in the way.
 Dos disable it add
pnat
to the list of DisabledPlugins in /etc/bluetooth/main.conf

There was a weirdness where the connection wouldnt work unless hcidump was running, but this is intermittant.

then its all go!

---

### Post by ScarletPea on 2011-01-14
The kind people at #bluez-user helped me through this.
It turns out that a plugin for maeomo is getting in the way.
 Dos disable it add
pnat
to the list of DisabledPlugins in /etc/bluetooth/main.conf

There was a weirdness where the connection wouldnt work unless hcidump was running, but this is intermittant.

then its all go!

---

### Post by bdoe on 2011-05-23
I'm afraid this didn't help me at all. I still have exactly the same problem as described in the OP: Nothing happens when I run the dund command and attempt to connect with my Palm Tungsten E2. I added pnat to the list of DisabledPlugins and then restarted the bluetooth service, but this didn't help. I even removed the other entries under DisabledPlugins so that pnat was the only one listed, but no joy there either.

Ultimately, I am having absolutely no luck syncing my Palm under Mint 11 (which is effectively Ubuntu Natty without Unity), even though both my laptop and my Palm are properly paired. I even see the "connect" icon appear next to my Palm's entry in Bluetooth prefs when I attempt to sync, but Gnome-Pilot is completely unaware of the connection. I did not have this problem with Maverick.

---


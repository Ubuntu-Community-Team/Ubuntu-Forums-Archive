---
title: "Cannot connect to hidden wireless since upgrade"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by Saintj on 2009-11-16
Since the moment i upgraded to karmic koala i coulden't connect to my wireless network anymore.

Im using an E-tech usb wlan card wich seems to be recognized better then on 9.04 (the green light flashes wich it didn't on 9.04 but it DID connect on there)

My router is a linksys WRT54GL, flashed with the stable DD-WRT, SSID is not sending (hence the hidden network lol) protection is WPA2 Personal Mixed.

It just doesen't connect i tried a miljion times and you can't just click connect anymore either you need to constantly make a new hidden network account because if i go to connect to hidden network the connect is greyed out.

Someone please help, im really clueless what to do since it worked perfectly before i upgraded.

---

### Post by t0mppa on 2009-11-16
The whole greyed out thing sounds like a Network Manager eccentricity, some people can't even edit their connections, since the edit or apply buttons are always greyed out. To date, I have yet to see any solutions that would fix this issue. Should test with another GUI software like WICD or WifiRadar.

A secondary issue is why are you even disabling your SSID broadcast in the first place? It is one of the things that people falsely think adds security, but in practice it only makes things more difficult for the user. Even if the broadcast itself is hidden, there's still 4 other types (probe requests, probe responses, association requests, and re-association requests) of non-encrypted packages that display the SSID information that can easily be picked up by anyone who knows what they're doing. Plus, since your neighbour doesn't see your network on his casual scans, he could set his AP on the same channel as yours and thus unknowingly create a lot of interference for both of you.

---

### Post by Saintj on 2009-11-16
I think you could be correct about the channels mixing, there are atleast 20 signals i pick up here the only reason i dont send out SSID is because of lots of people here trying to burst into the wireless connections (its a thing here i guess)) but i figured if its hidden it gives them more work so why bother with me if they can easially get another visible badly protected router.

And the other thing is i been having it up and running for years like this and no problems at all, i install koala and *poof* problem appears.

---

### Post by Saintj on 2009-11-16
Anyone any idea how to fix this? (btw it doesen't change if i put SSID on broadcast still doesen't connect neither does switching signal channels etc.)

---

### Post by t0mppa on 2009-11-16
> It just doesen't connect i tried a miljion times and you can't just click connect anymore either you need to constantly make a new hidden network account because if i go to connect to hidden network the connect is greyed out.

> btw it doesen't change if i put SSID on broadcast still doesen't connect neither does switching signal channels etc.

Does that mean you can connect by making a new hidden network? Or are the connection choices in Network Manager always greyed out? You can still see networks present (the non-hidden ones) though?

Open up a terminal, run **lshw -c network**, check which driver you're using (there's a *driver=xxx* part on the configuration line) and then run **dmesg | grep <driver_name>** to see if it's outputting any hints to the kernel ring buffer (just post output here, if you can't figure it out yourself). Can also do a Google search for the driver name and Karmic to see if there are any known issues.

If the driver appears to be working properly, then try [connecting manually from the command line]("http://ubuntuforums.org/showthread.php?t=571188"). If that works, then the problem is merely with Network Manager and you should be able to solve it by switching to another program for handling your connections.

About the security, like I said it's a secondary issue. Things should work even when the router isn't broadcasting its SSID, so that's not the origin of your problem. However for troubleshooting purposes, it's often best to first run as simple a configuration (open network, no security measures) as possible to pinpoint the problem. And after it's fixed get the security measures back up.

I just wanted to point out that simply running WPA2 will take care of your security. If your password is weak someone might be able to brute force - i.e., by trying different commonly used or dictionary based passwords - their way in, but the algorithm itself has been unbreakable so far. Anything on top of that will only cause extra effort for you and will only delay a possible cracker by a minute or two.

---

### Post by Saintj on 2009-11-17
Well i'll give this a shot later (im not at my ubuntu comp right now) but as WPA2 security goes i'm using a 12 characters string consisting of four numbers and a double word wich is not in the dictionary :P atleast not in our language lol so that should be fine, but the weird thing is that it worked perfectly on jaunty but the second i updated to koala it disconnected and went *poof* that's the weird thing (and i tried while broadcasting SSID so that ones in the clear) but i'll try running the command line and doing the trouble shooting and i'll give you an update on if i got it to work or not :)

---


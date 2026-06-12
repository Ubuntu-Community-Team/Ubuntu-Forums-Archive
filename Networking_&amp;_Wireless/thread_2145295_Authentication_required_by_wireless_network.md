---
title: "Authentication required by wireless network"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by Krellan on 2013-05-15
Hi there.

Anybody else tired of seeing this message?

I'm looking for any help I can get, because it keeps knocking my box offline, and I would love to be able to access it remotely.

I have a laptop running Ubuntu, and there's no wired Ethernet available nearby so I have it wireless.  It's running the GNOME desktop.  I can't physically move the laptop because it's recording audio.

I know the password for my wireless network is correct.  However, NetworkManager keeps asking for it every time, and it won't attempt a reconnect automatically in the background.  So, it works for a few hours, then whenever the signal gets weak for a moment (somebody uses the microwave or whatever), it goes offline.  Other devices automatically reconnect, but Ubuntu keeps assuming my password is wrong!

Every time I come back to visit the laptop, I'm greeted by that dialog box.  A single click to "OK" gets me back online, but I really wish I didn't have to make that click.  It's impossible to do remotely.  I really wish there was a way to make that dialog box go away forever, and simply have Ubuntu try again, using my existing password.  I can confirm that it correctly memorizes my password (no problem with keyring or anything like that), because in the dialog box, the password is prefilled into the window, and it is correct.

Does anybody have a workaround for this critical usability problem?  I see I'm not the first to complain... according to the bug reports, this is a commonly filed bug.

Thanks!
Josh

---

### Post by Hadaka on 2013-05-15
Hi, this might be a pointless question...but
is the "Connect Automatically" box checked
when you edit or look at the settings with
network mgr.?

---

### Post by Krellan on 2013-05-15
Yes, it is.  In the "Edit Connections" box, under "Wireless", I have 2 wireless networks configured (both fairly weak, unfortunately), and both of them have the "Connect automatically" box checked.

---

### Post by Hadaka on 2013-05-15
ok, you might try setting the Ipv6 to Ignore,
make sure you have a unique ssid name since
the signal is weak,maybe others in the area with
the same name,perhaps change the channel, scrounge
up another wireless router and put it into the repeater
mode and place it closer to your buntu machine.Lastly
I had a like problem,and not sure if this had any effect or not
but...i edited the connection, then went through each setting..
wireless,ipv4,ipv6 and security, unchecked and then re checked
the connect automatically box and clicked save on each setting.
i no longer have the problem...thats pretty much all the suggestions
i have to offer..
good luck.

---

### Post by Krellan on 2013-05-15
I actually need IPv6 because I use that.  Among other things, my laptop has a public IPv6 address so I can reach it from anywhere (it doesn't have a public IPv4 address).

SSID name and channel number are unique on both networks.  There's other noise nearby, but that's true of almost any populated area these days, there's always somebody else's wireless network nearby.

Perhaps a repeater is necessary, but those can cause their own problems.  I've had more trouble from the repeater losing the link, than I have from losing the original signal.  I'll try to find another repeater, though.

It's unfortunate that only NetworkManager does this.  Other devices just know to reconnect automatically in the background, so I hardly know they've lost the connection.  Ubuntu puts it right up front in your face, though, and keeps you offline until you hit "OK", unfortunately.

---


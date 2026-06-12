---
title: "ad hoc wireless ubuntu - vista"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by mireson on 2009-01-15
Hi,

I'm trying to set up an ad hoc (comp to comp) wireless link between two laptops.

One runs Intrepid exclusively (mine)
One runs Vista Home Premium exclusively (my wife's)

Both connect without a problem to the wlans we have at work.

When I try to set up an ad hoc network between them though, they just won't connect.

Do I need to have any specific packages install to enable a cross-platform connection? Or is there an existing how-to I can follow?

I'd consider myself an intermediate user. I've been using Ubuntu for about 2 years, so I'm cool with the cli, but I'd rather not mess around with iptables. I can leearn if i have to.

Thanks in anticipation.

---

### Post by Teegoat on 2009-01-15
I there,
I'm trying to do a similar thing but using xp sp3.
Managed to set-up adhoc on xp but ubuntu stays blind to it...

---

### Post by HavocXphere on 2009-01-15
Good luck with that. Vista and ad hoc is a disaster.

Managed ad hoc on Vista once. Connecting took 2 hours, then I had a connection with a range of 5m that was soooo damn flakey that I couldn't transfer anything.

---

### Post by superprash2003 on 2009-01-15
hope this helps for the linux part [http://www.prash-babu.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://www.prash-babu.com/2008/08/how-to-createjoin-adhoc-network-in.html) and this for the vista part [http://windowshelp.microsoft.com/Windows/en-us/help/293c504f-b944-4d5d-835c-f080129bd5dc1033.mspx](http://windowshelp.microsoft.com/Windows/en-us/help/293c504f-b944-4d5d-835c-f080129bd5dc1033.mspx)

---

### Post by mireson on 2009-01-16
Thanks superprash2003, i'll check out those links and post my results back here. 
Sounds like if I can get this to work, others may find it helpful.

---

### Post by mireson on 2009-01-19
well, i had a bit of a poke around both vista and ubuntu. I checked out the above links, but they weren't so helpful. Some of the commands in the linux one didn't seem to work for me. And the Vista one is what i was trying to do anyway. thanks though.

The closest I got to getting it working was with the following (all GUI i'm afraid):

**Set up an ad hoc connection in Vista**
- Set it up using WPA2 personal encryption (i did this because I've had trouble with Ubuntu connecting to unsecured wlan previously)
- used a simple SSID, like 'network' or something

**Connect using Ubuntu**
Ubuntu didn't automatically see the network unfortunately, so I had to right-click on the network manager icon in the systray, and select "Edit Connections"
- Go to "wireless" tab
- Hit the "add" button on right, dialogue comes up
- on the wireless tab, typed SSID name and changed mode to ad-hoc
- on security tab, entered the WPA2 passphrase

After that the network was visible when i left-clicked the network manager icon in systray.

**Still have a problem:** I try to connect to the network from Ubuntu and it tries for about two minutes (the animated "connecting..." icon in systray) before bringing up a passphrase request dialogue. One odd thing is that the passphrase is converted to a very long string, rather than a short passphrase. I tried adjusting both the passphrases again, but with no luck.

I wonder if there is something in the way Vista and Ubuntu establish connections?

Also, I'm not sure what i need to do about IP addresses, whether i use ipv4 or ipv6, and DNS? I've kind of avoided the issue, but perhaps that's what is stopping the connection being established. I really don't know. Has wnyone s

---

### Post by mireson on 2009-01-21
In an effort to correctly diagnose this problem (watching too much House lately)...

Is there something in the protocols that Ubuntu and Vista use connect to wireless networks that mean it is impossible for them to connect with each other (in an ad hoc network)?

---

### Post by mireson on 2009-01-21
always pays to check community docs, I'm running myself through this one at the moment, will let you know how it goes...

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by mireson on 2009-02-02
> **mireson said:**
> always pays to check community docs, I'm running myself through this one at the moment, will let you know how it goes...

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

No luck.

I thought it was a hardware issue for a moment, but I also tried with a supported usb wireless dongle - still didn't work.

I'm still stuck... Has anyone managed to get this working at all? How?

(seriously considering purchasing a simple router...)

---

### Post by waynema on 2009-09-13
I have ad hoc network set up, but there is no security!

One windows xp, another Ubuntu Jaunty 64bit. Using the same method as you, instead of choosing WPA2, I chose NONE. Then both computer can connect to the ad hoc network.

However, whenever I tried to set a securiy (WEP/WPA) for the ad hoc, the ubuntu network manager would always asked me for passphrase, just like mireson mentioned.
 
So, in my experience, the ad hoc [COLOR="Red"]cannot[/COLOR] be setup [COLOR="Red"]with security[/COLOR]. 

Don't know if this is a bug or some mis-configuration..

---

### Post by _6i on 2009-12-11
hi, in my case: Ubuntu vs. WinXP SP2 (+ windows WPA2 encription update "WindowsXP-KB893357-v2-x86-ENU.exe" - i didn't have WPA or WPA2 among the choices before)
with jaunty, it worked only with no protection (as for the others above)
with karmic however i could use WEP

my setup:
i set my wireless connection as "Home networking connection" in ICS (Internet Connection Sharing) settings (internet connection properties, advanced page) - because my goal was obviously to share my internet over an ad-hoc network

```

Windows Xp (Wireless Network Connection Properties -> "Wireless Networks" page
-> "Preferred networks" section -> "MyAdHocNetwork" -> Properties):
  "MyAdHocNetwork" properties:
    "Association" page:
      Network Authentication: Shared
      Data encryption: WEP
      Network key: AnyThingULike
    "Connection" page:
      [&#8730;] Connect when this network is in range

```
```

Ubuntu Karmic 9.10 (Network Connections -> "Wireless" page -> Auto MyAdHocNetwork -> Edit):
  Editing Auto MyAdHocNetwork:
    [&#8730;] Connect automatically
    "Wireless" tab:
      SSID: MyAdHocNetwork
      Mode: Ad-hoc
      MTU: automatic
    "Wireless Security" page:
      Security: WEP 40/128-bit Key
      Key: AnyThingULike
    "IPv4 Settings" page:
      Method: Automatic (DHCP)
    "IPv6 Settings" page:
      Method: Ignore

```

when i started connecting from ubuntu, despite the fact that the key was already set, i had to set the passkey again in a dialog, then the connection was established

i know that WEP is also unsecure, but it's a little bit better than having no encryption at all

something similar could work in Vista, too

NOTE: when i attempted to connect to WPA2-AES secured WinXP ad-hoc network, the dialog popped up similarly, but after setting the key, it was trying to connect for a while, then the passkey-dialog popped up again, and it kept doing this until i gave up

anyone? any progress with WPA2-AES?

---


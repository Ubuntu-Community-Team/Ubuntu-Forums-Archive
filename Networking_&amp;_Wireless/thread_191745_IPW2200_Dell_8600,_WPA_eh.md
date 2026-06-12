---
title: "IPW2200 Dell 8600, WPA eh?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by scottylans on 2006-06-07
Hi guys,

I was under the impression that WPA would be supported better under Dapper?

I've installed it and it appears to have detected my card.
However under the system / administration / network menu, there's still only a section to enter WEP keys, not WPA?

Wasn't there meant to be a newer better networking tool included which let's you use WPA convieniently? like a complete replacement of the current tool?

Since it doesn't work off the bat, I'm now back to reading luca_linux's 64 page tutorial on how to figure it all out.

---

### Post by polo_step on 2006-06-08
[QUOTE=scottylans]
I was under the impression that WPA would be supported better under Dapper?
[/QUOTE]
[FONT="Courier New"]So was I, but apparently not only did it not happen, but WPA is actually **less** supported in 6.06 than in 5.10 according to the posts I've read here.](*,)

I have no idea what's up with that. [/FONT]

---

### Post by zdavidlnx on 2006-06-08
HI, I have the same problem. Making work ipw2200 with WPA, it was working in 5.10. And now i was hoping that 6.06 will support it from the network manager. No way i only can choose WEP. My network is protected with WPA, and i Won't change that.

---

### Post by scottylans on 2006-06-08
Ok well surely someone with some knowledge can weigh in here?

What's the deal - are we doing something wrong?

I definately can't see anything within the network manager for WPA :( nor can I find a WPA management tool within the menus.

NOTE: My install was a totally fresh install from CD.

---

### Post by scottylans on 2006-06-12
Bump - hello guys? What's going on with the ipw2200 support? - I thought WPA was meant to be dead easy on 2200's under Dapper, is there a readme we haven't read? - Another package in the menu's we haven't found or is our network manager  tool "broken" ?

I simply can't find  WPA support without dropping to a console and fiddling with wpa supplicant, which I don't fully understand.

---

### Post by ronzo on 2006-06-12
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=194607](http://ubuntuforums.org/showthread.php?t=194607)

---

### Post by scottylans on 2006-06-12
[QUOTE=ronzo]Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=194607](http://ubuntuforums.org/showthread.php?t=194607)[/QUOTE]


Ronzo, I'll follow that tonight.
Still very disapointing, I was under the impression we were up for out of the box easy support this round - I've been using it since 5.04 then 5.10 now 6.06 and still it's not simple out of the box wireless support.

Also according to that, I need an older firmware and older driver? - pretty bad! :(

---

### Post by Jeff250 on 2006-06-13
No no no.  It does (or should) work with an ipw2200.  You just need to install the network-manager and network-manager-gnome packages.  This, and its dependences, will install a gnome applet that will allow you to connect to WPA networks.

---

### Post by scottylans on 2006-06-13
Just those 2 apps?
As simple as finding them in synapting, selecting, installing and I guess re-booting?

If so that's great, but why not installed as default - replacing the current WEP only network tool?

---

### Post by Jeff250 on 2006-06-13
Actually, you really just need to install network-manager-gnome, since it depends on the package named network-manager. :p  And to avoid rebooting, I think you can just run the nm-applet command from the console after it's installed.  (If not, just reboot.)

Why is it not installed by default?  That's a good question. :eek: No, I think I can answer it.  The applet still has some limitations.  For one thing, it hasn't yet incorporated static IP's.  A while ago, it was rumored that these will be included in NetworkManager 0.7x.  I don't know if that's still the case.  Also, since NetworkManager is controlled through an applet, it means that you don't get connected to your network until AFTER you've logged on through a display manager and the applet is loaded.  This also doesn't effect most users.  But these issues are significant enough for many users to keep NetworkManager from being the default network tool.  Whether or not NetworkManager ever will be the default, I cannot speculate either.

---

### Post by Jeroen Vernooij on 2006-06-14
Indeed, I'm using a IPW3945 (update of the 2200) with WPA, working flawlessly with network-manager-gnome. I haven't even edited a single text-file to make it work, just GUI's.
Make sure you got linux-restricted-modules installed, along with network-manager-gnome.

---


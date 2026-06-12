---
title: "New nm-applet indicator"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-01-05
There will be a new nm-applet indicator coming as soon as the icons are finished, for a preview have a look [here]("http://twitpic.com/3n0a95").

---

### Post by Mr. Picklesworth on 2011-01-06
For context: [http://blog.cyphermox.net/2011/01/natty-nm-applet-improvements.html](http://blog.cyphermox.net/2011/01/natty-nm-applet-improvements.html)

This is all a stop-gap before the new indicator-network lands.

---

### Post by wojox on 2011-01-06
I was wondering when those pad locks were coming back.

---

### Post by MacUntu on 2011-01-06
Bah, can't we get consistent item icon/text alignment with indicator menus? ](*,)

  [[img]http://img.xrmb2.net/476185.jpg[/img]](http://img.xrmb2.net/images/476185.jpeg)

Sound and messages indicator look right, the new nm and the session indicator look weird, and other indicators/menus look weird if a certain gconf-key is set. So much for consistency, yay!

---

### Post by Framli on 2011-01-06
IMHO it is fairly consistent: 
[LIST]
[*]An icon on the second colum is only relevant to a particular menu entry, which will then be expressed when the menu is closed.
[*]An icon on the first column is relevant to every entries related to a particular application (applications being separated by -hum- separators). 
[*]An arrow indicates the status of an application. 
[*]A tick indicates the status of an option.
[/LIST]
Maybe I'm getting to used to these to notice weirdness, but it also explains why this gconf-key is not set by default.
(In fact, it doesn't really explain it, because the key has been unset by default before app-indicators appear IIRC... But now it makes sense! :P)

---

### Post by hugmenot on 2011-01-06
> **MacUntu said:**
> Bah, can't we get consistent item icon/text alignment with indicator menus? ](*,)

  [[img]http://img.xrmb2.net/476185.jpg[/img]](http://img.xrmb2.net/images/476185.jpeg)

Sound and messages indicator look right, the new nm and the session indicator look weird, and other indicators/menus look weird if a certain gconf-key is set. So much for consistency, yay!
[Here&#8217;s a bug about that]("https://bugs.launchpad.net/bugs/608584"). Chime in or something

---

### Post by MacUntu on 2011-01-06
> **hugmenot said:**
> [Here’s a bug about that]("https://bugs.launchpad.net/bugs/608584"). Chime in or something

Subscribed since 2010-09-13. :P

---

### Post by Mr. Picklesworth on 2011-01-06
> **MacUntu said:**
> Bah, can't we get consistent item icon/text alignment with indicator menus? ](*,)

  [[img]http://img.xrmb2.net/476185.jpg[/img]](http://img.xrmb2.net/images/476185.jpeg)

Sound and messages indicator look right, the new nm and the session indicator look weird, and other indicators/menus look weird if a certain gconf-key is set. So much for consistency, yay!

One explanation is icons are being used to mimic hanging indents for titles. With the music players in the Sound menu, each player's name appears to hang over its respective playback controls, so you can tell these things are related. Having icons in-line with text for related elements (that aren't titles) continues from that kind of naturally.

And it *has* to be done for the Me menu since we need both icons and an indication of which item is selected. That is actually impossible with icons on the left column. (For what it's worth, that's why MacOS *also* does icons in line with text).

Indeed, it's a weird, kind of unspecified way to do things. I brought this up at UDS and the folks who do it seem *interested* in getting a proper Title menu entry but that isn't really on the roadmap because what we have is working okay at the moment. It should really change in GTK+, first, which means a major change to the philosophy and the API for menus.

Of course, I think the same can be done with vertical whitespace (instead of useless menu separators), but that's another debate.
[ATTACH]180309[/ATTACH]

As for the problem you highlight on the bottom left of the picture: one of the advantages of having icons in-line with text is to highlight those inconsistencies. With that, we can see why menus_have_icons was disabled by default: it makes no sense. Find has an icon, for example, but Find Next doesn't. The real problem is not with the indicators, and it isn't really a problem with the app: it was a problem with trying (with about 40% failure rate) to throw an icon beside every line of text in Gnome, and it has since been solved.

---

### Post by MacUntu on 2011-01-06
So basically I just didn't know that I have a problem. Now THAT sounds like Apple. ;):P

---

### Post by Starks on 2011-01-06
Connman can't get here soon enough...

---

### Post by zekopeko on 2011-01-07
I'm still confused what the plan is. Are we getting conman plus the indicator or network-manager with an indicator? If we are getting conman then I think it's a bad call. Network-manager is far more mature and has less issues. Adding indicator support to it should be easier then vetting the entire conman infrastructure.

---

### Post by MacUntu on 2011-01-07
> **zekopeko said:**
> I'm still confused what the plan is.

[http://askubuntu.com/questions/10272/will-connman-replace-networkmanager-on-the-desktop-for-11-04](http://askubuntu.com/questions/10272/will-connman-replace-networkmanager-on-the-desktop-for-11-04)

[http://askubuntu.com/questions/15123/why-are-two-indicator-network-versions-being-worked-on](http://askubuntu.com/questions/15123/why-are-two-indicator-network-versions-being-worked-on)

---

### Post by ratcheer on 2011-01-07
Here's some more info: [http://blog.cyphermox.net/2011/01/natty-nm-applet-improvements.html](http://blog.cyphermox.net/2011/01/natty-nm-applet-improvements.html)

Tim

---

### Post by zekopeko on 2011-01-07
> **MacUntu said:**
> [http://askubuntu.com/questions/10272/will-connman-replace-networkmanager-on-the-desktop-for-11-04](http://askubuntu.com/questions/10272/will-connman-replace-networkmanager-on-the-desktop-for-11-04)

[http://askubuntu.com/questions/15123/why-are-two-indicator-network-versions-being-worked-on](http://askubuntu.com/questions/15123/why-are-two-indicator-network-versions-being-worked-on)

Oh, god. It's one of those decision that make you facepalm.

---

### Post by andrek on 2011-01-08
Looks like it's in Natty already and it looks pretty neat!

---

### Post by hugmenot on 2011-01-10
> **Starks said:**
> Connman can't get here soon enough...

Why are you cheering for Connman? I see no advantage in switching. It seems much less sophisticated than NetworkManager. Where’s the advantage?

---

### Post by MacUntu on 2011-01-10
Like with every change: awesome, active upstream. ;)

---

### Post by hugmenot on 2011-01-10
NetworkManager upstream seems [very much active]("http://mail.gnome.org/archives/networkmanager-list/2011-January/thread.html"). And they have achieved much more of the features already that Connman just lacks:


**Supported features:**
[LIST]
[*]Ethernet
[*]Wi-Fi Open, WEP, WPA and WPA2
[*]3G on GSM networks
[*]BT PAN
[*]IPv6 (static)
[/LIST]
**Notable missing features:**
[LIST]
[*]any sort of VPN
[*]Wi-Fi Ad-Hoc, WPA Enterprise
[*]CDMA/EVDO modem support
[*]BT DUN
[*]PPPoE
[/LIST]

---

### Post by MacUntu on 2011-01-10
Ah, I was just kidding, cause that often comes up as _the_ reason for switches/rewrites. :P

---

### Post by hugmenot on 2011-01-10
Oh, I see now. Missed that smiley.

Anyhow, I find this thread very telling:
[http://thread.gmane.org/gmane.comp.handhelds.moblin.connman/1456](http://thread.gmane.org/gmane.comp.handhelds.moblin.connman/1456)

Connman and Desktop don&#8217;t mix. Networking life is too complicated to idealize use cases and then strip it down like that.

Dude says people don&#8217;t need to create ad-hoc. Well, they do.

Dude says people don&#8217;t need pppoe. Well, very novice users I met who didn&#8217;t have a router and just a DSL modem did. And with NM they figured it out by themselves. I myself needed pppoe when my wifi router went down and I needed to look something up on the net.

So whyTF are they considering this switch? Anyone?

---

### Post by Mr. Picklesworth on 2011-01-10
I was actually under the impression that the new network indicator would support multiple backends (Conman and Network Manager). Is there something that says otherwise?

---

### Post by hugmenot on 2011-01-10
I got that impression from the existence of the two separate applets and the statements made by sabdfl on Ask Ubuntu and Ayatana mailing lists.

Anyhow, consider these examples:

```
<me> hi, i&#8217;m referring to this email by marcel holtmann
http://article.gmane.org/gmane.comp.handhelds.moblin.connman/1457

 why is he saying that people don&#8217;t need pppoe?

 there are so many non-contrived situations where pppoe is essential.

<wagi> me: depends on the environment you want to use connman, e.g. connman is not indetet
to be used in data centers

 me: simply speaking it's not the solution for all problems

<me> wagi, ubuntu is planning to switch to it for desktops.

 wagi, and even for netbooks, allow me to give a hypothetical scenario:

 you are moving to a new flat, you arrive there ahead of time and need to access the net
 urgently. but there&#8217;s only the dsl modem that they left you. you connect your netbook to
 the modem and there&#8217;s no way to access the net.

 so you&#8217;re supposed to write to pppoeconf?

<holtmann> Bring you 50 USD access point with you and be done with it. And then use WiFi.

<me> holtmann, you traveled from abroad and now you found a room for subletting. there&#8217;s
only a modem and ethernet. what do you do?

<holtmann> I always have my WiFi AP with me. These are tiny.

<me> you always pack your wifi router, or what is the idea? buy one on the streets?

<holtmann> Both would work ;)

<me> sorry, that is backwards. networking realities are not clean cut like your use cases.
sometimes you have to fall back to old style methods.

 recently i brocked my openwrt router and needed to look something up on the net. i just
 needed to use pppoe then. would you had me purchase a new router just for that?

<me> third example, i met a very non-technical girl who kinda wanted me to dump ubuntu on
her laptop for some reason. i was not really convinced that was a good idea. but she went
home with it and popped up with an IM message saying that he likes it. i was dumbfounded
asking "how on earth did you get on the internet?". says she "why, i just entered my
password?".

 note that that was using nm-applet DSL tab, which she just found. and yes, her provider
 alice just gave a locked down dsl modem.

 same thing with ad-hoc, btw.

 holtmann, so if connman is used i would have to tell people they have to either boot
 windows of buy a new device they didn&#8217;t need before?

 s/of/or/

<sameo> me: pppoe patches are welcome. I have no interest or need for it, but I'll be
happy to review patches.

<holtmann> sameo: From a technical point of view, I don't wanna deal with pppd. That one
is just a beast.

<kvalo> me: pppoe is definitely needed. I'm hoping to work on that at some point, but
definitely not within the next few months

<me> in that case i don&#8217;t see how ubuntu would be served better with connman on the
desktop, or even on the netbook.

 those are really big feature regressions from NM.

<kvalo> me: fully agree
```

---

### Post by zombiepig on 2011-01-10
> **hugmenot said:**
> 
**Notable missing features:**
[LIST]
[*]any sort of VPN
[*]Wi-Fi Ad-Hoc, WPA Enterprise
[*]CDMA/EVDO modem support
[*]BT DUN
[*]PPPoE
[/LIST]

I'd add internet connection sharing to that list too. Network manager makes it so easy to share a wired/3g connection over wifi!

---


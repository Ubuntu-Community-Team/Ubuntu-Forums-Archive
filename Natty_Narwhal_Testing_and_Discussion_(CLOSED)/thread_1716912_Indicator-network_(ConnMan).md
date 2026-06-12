---
title: "Indicator-network (ConnMan)"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-03-29
Is indicator-network going to be default or it will be only available in repositories for manual install?

What are the missing features and is it considered enough stable?

I personally find stable for wired connection in virtualbox, I wonder about wifi and hdspa..

[IMG]http://i.imgur.com/CJL4C.jpg[/IMG]
[http://www.omgubuntu.co.uk/2011/03/indicator-network-is-looking-good-in-natty/](http://www.omgubuntu.co.uk/2011/03/indicator-network-is-looking-good-in-natty/)

---

### Post by Harry33 on 2011-03-29
> **lucazade said:**
> Is indicator-network going to be default or it will be only available in repositories for manual install?

What are the missing features and is it considered enough stable?

I personally find stable for wired connection in virtualbox, I wonder about wifi and hdspa..
...


For Natty Connman is an option and will not be default for desktop installation.
What happens in future is not clear.
Anyway, I use Connman everyday in desktop setup.
Works quite well and is indeed lighter software than Nm is.
In a laptop setup I found that it does not detect hidden networks.

It seems the notification area may be removed later (used by network-manager-applet).
Connman does use the recent indicator-applet scheme.

---

### Post by lucazade on 2011-03-29
> **Harry33 said:**
> For Natty Connman is an option and will not be default for desktop installation.
What happens in future is not clear.
Anyway, I use Connman everyday in desktop setup.
Works quite well and is indeed lighter software than Nm is.
In a laptop setup I found that it does not detect hidden networks.

It seems the notification area may be removed later (used by network-manager-applet).
Connman does use the recent indicator-applet scheme.

Ok.. interesting.
Thanks Harry33 :)

---

### Post by hugmenot on 2011-03-29
> **Harry33 said:**
> For Natty Connman is an option and will not be default for desktop installation.
What happens in future is not clear.
Anyway, I use Connman everyday in desktop setup.
Works quite well and is indeed lighter software than Nm is.
In a laptop setup I found that it does not detect hidden networks.

It seems the notification area may be removed later (used by network-manager-applet).
Connman does use the recent indicator-applet scheme.

That’s untrue. The nm-applet is an indicator just as well nowadays.

Connman doesn’t do Ad-Hoc and PPPoE, among other things. ConnMan just isn’t deigned to handle normal networking scenarios on a desktop.

And the developer told me to carry around a separate router if I expect to need to access modems on the road.

---

### Post by Harry33 on 2011-03-29
> **hugmenot said:**
> That&#8217;s untrue. The nm-applet is an indicator just as well nowadays.

Connman doesn&#8217;t do Ad-Hoc and PPPoE, among other things. ConnMan just isn&#8217;t deigned to handle normal networking scenarios on a desktop.

And the developer told me to carry around a separate router if I expect to need to access modems on the road.

It is not untrue.
Not in Ubuntu Classic session.
Nm-applet is and stays in the notification area only
If I remove the notification area I do not have Nm-applet at all.

See this bug report for your self:
[https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385)

---

### Post by hugmenot on 2011-03-30
> **Harry33 said:**
> It is not untrue.
Not in Ubuntu Classic session.
Nm-applet is and stays in the notification area only
If I remove the notification area I do not have Nm-applet at all.

See this bug report for your self:
[https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385)

Poppycock man, check »aptitude changelog network-manager-gnome«.

---

### Post by Harry33 on 2011-03-31
> **hugmenot said:**
> Poppycock man, check »aptitude changelog network-manager-gnome«.

So, do you have two Nm-icons and bluez-icons on your panel (when running Ubuntu Classic) - one in notification area and one in indicator-applet?
I only see those in notification area.
If I remove sound, weather and datetime icons from indicator-applet,
I see text "no indicators" there.

I know the bug #741387 is about ubuntu-mono package (issue being cache generation fails to validate).
Did you look at this?

---

### Post by VinDSL on 2011-03-31
> **hugmenot said:**
> Connman doesn’t do Ad-Hoc and PPPoE, among other things. ConnMan just isn’t deigned to handle normal networking scenarios on a desktop.[...]Thank you!

I don't mean to pick sides!

Truthfully, I like Harry33, and I've never heard of you, but...

Personalities aside, I totally agree with you, hugmenot!

In a moment of weakness, minutes before going to bed, I installed Connman (about a month ago).

Sorry for being blunt, but Connman was a total POS FAIL, in my book!

That %@$%# thing uninstalled my network manager, and after I realized what a mistake I'd made, e.g no direct DSL PPPoE support... it took me another hour to delete Connman and restore the normal network manager.  By the time I went to bed, I was spitting nails!

OMG!  Connman was the first "virus" I'd run across in Linux, and I'm still licking my wounds.  LoL!

Anybody reading this post, read and heed!  :D

---

### Post by lucazade on 2011-03-31
> **VinDSL said:**
> Thank you!

I don't mean to pick sides!

Truthfully, I like Harry33, and I've never heard of you, but...

Personalities aside, I totally agree with you, hugmenot!

In a moment of weakness, minutes before going to bed, I installed Connman (about a month ago).

Sorry for being blunt, but Connman was a total POS FAIL, in my book!

That %@$%# thing uninstalled my network manager, and after I realized what a mistake I'd made, e.g no direct DSL PPPoE support... it took me another hour to delete Connman and restore the normal network manager.  By the time I went to bed, I was spitting nails!

OMG!  Connman was the first "virus" I'd run across in Linux, and I'm still licking my wounds.  LoL!

Anybody reading this post, read and heed!  :D

Fortunately my isp provider doesn't use PPPOE or PPPoA, it provides a hag/router and a simple 10/100 ethernet connection... it's a giant MAN all behind NAT.

What I'd like to try with connman are Wifi, 3G dongle support and PPTP VPN.
I'll probably do a respin of natty with connman to do some tests.

---

### Post by VinDSL on 2011-03-31
Good luck to you, lucazade!  ;)

---

### Post by hugmenot on 2011-03-31
> **Harry33 said:**
> So, do you have two Nm-icons and bluez-icons on your panel (when running Ubuntu Classic)

Nope. I run the gnome-classic session. And nm-applet /is/ an indicator (you better check with apt-cache policy network-manager-gnome).

Here’s picture:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187648&stc=1&d=1301575359[/IMG]


> **Harry33 said:**
> I know the bug #741387 is about ubuntu-mono package (issue being cache generation fails to validate).
Did you look at this?

That bug is about icon images, not applets. You seem fairly confused.

---

### Post by Harry33 on 2011-03-31
> **hugmenot said:**
> Nope. I run the gnome-classic session. And nm-applet /is/ an indicator (you better check with apt-cache policy network-manager-gnome).
That bug is about icon images, not applets. You seem fairly confused.

Do not mix things up yourself.
In my Natty setups, just like in Maverick, the Bluetooth and Network-manager applet icons are in the notification area.
If I remove the notification area there is no bluetooth nor network-manager applet icons anywhere.
But I can still see for example sound icon in the indicator area.

With connman and indicator-network the network icon is in the indicator area.

About the bug #741387
This bug is about broken notification area (cache is not built successfully upon install of ubuntu-mono and the Ubuntu Monochrome icons are not restored). Icons are not broken.

---

### Post by hugmenot on 2011-03-31
Ok. Show »apt-cache policy network-manager-gnome«

---

### Post by Harry33 on 2011-03-31
> **hugmenot said:**
> Ok. Show »apt-cache policy network-manager-gnome«

My main Desktop (NVidia) does not have network-manager any longer, but Connman instead.
However, I have Nm in my ATI GPU Desktop and Intel GPU Laptop setups.
Here is the request from ATI GPU setup:

```

network-manager-gnome:
Installed: 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1
Candidate: 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1
Version table:
*** 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1 0
       500 http://archive.ubuntu.com/ubuntu/ natty/main amd64 Packages
       100 /var/lib/dpkg/status

```

For Dell laptop (Intel GPU) the message is the same.

---


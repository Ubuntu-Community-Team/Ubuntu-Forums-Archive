---
title: "Appalling - Prism2 PCI and mini PCI borked in Dapper"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by dickmorrell on 2006-07-01
Posted this morning about problems that in previous versions of Ubuntu mini PCI prism2 and PCI prism2 orinocco cards just worked wonderfully. Install Dapper = no more wireless. 

Ok so with the Orinocco cards being popular as hell and ndiswrapper not really being required since eons ago under Linux why haven't the Ubuntu dev team worked out that maybe all the postings online have a point, tallied up all the combined complaints about this and looked at a kernel update or some fix ?

There are numerous postings (which I've sat and trawled for the last four hours to no avail) but no-one seems to have an answer as to why so much Wireless stuff is now screwed in Dapper.

Anyone got an opinion as I am about to ditch Dapper on 140 machines for SuSE.

Prism2/Orinocco cards are hardly unpopular

Dick

---

### Post by mpvano on 2006-07-01
Perhaps because there is no problem. All my orinoco and prism 2 cards work perfectly here "out of the box" with dapper!

I'm typing this on an IBM T30 with an orinoco_pci minipci card that came up and ran immediately (scanning even now works under dapper - it didn't work under breezy with the standard orinoco driver).

I have two other notebooks using prism2 cards. One uses an original orinoco gold pcmcia card - it came up and ran immediately. The other one is using an actiontec card that belongs in my spare router. It's a prism 2 card as well, and it also works perfectly in a vanilla dapper clean install on a third notebook here.

In general, every card I have (including some usb2 adapters and adapters that used to be a pain under breezy) are now working perfectly with no special tricks on several unencrypted and 128 bit WEP networks here.  (although two of my cards - the linksys WPC11v4 and my trendnet usb adapter both need to work with ndiswrapper. It, however worked perfectly the first time!) using the basic networking configuration tools in Dapper.

I find the basic tools limiting for roaming, however and I agree that there is not currently a working alternative that's suitable for more complicated uses. I use a homemade scripting solution to switch configurations, but it's ugly and requires manual configuration.

Anyway, I have nothing but praise for the improved drivers in Dapper. They're definitely much better than the ones in breezy. The GUI tools could be improved a bit, but at least they work! I could never get the gnome network adminstration tool working reliably on any of my machines under breezy!

Many people have trouble configuring wirelss networks on ALL platforms. The situation has become MUCH more complicated now that overlapping networks (often misconfigured) are the rule rather than an exception.

this problem is not just confined to Linux - I spend a lot of time visiting my friends in response to problems they have getting wireless working under XP! In fact the last XP update broke my own XP drivers for orinoco_pci - it took me hours of reconfiguring everything on this IBM T30 that had anything to do with wireless to get it working again!.

Perhaps a more specific problem description might help? Threats don't work well in the open source community.

Note also that this is not the paid support forum - everyone here is just trying to be helpful. I believe that Canonical provides support for industrial users with as many machines as you claim to control for a fee. For more information check out the ubuntu top page.

good luck with SUSE - I understand they just fired their CEO and are about to change direction completely....

Mario

---

### Post by awaldram on 2006-07-02
No actualy wireless is borked in dapper

it was broken around 2.6.15-19 when all the back ports from 2.6.17 went in 2 weeks prior to release

prism2 cards will work for wep and open in the native network tools and for wpa if you blacklist all the orinoco drivers and use hostap, wpa_supplicant and gnome netork manager . 

but then you can't connect to open or wep networks, most of the cards which will cause you issue are easy to spot do a google for your card see what the normal intreface name is i.e prism2 'wlan0' then check what is is in dapper 'eth1' you just know you'll have issues as the user land programs don't seem to have caught up.

If you need to access both open/wep and wpa site then investigate wifi radar as it uses native connection routines for open/wep and only wpa_supplicant fro wpa so works in dapper screwed up wireless world quite well.

I'm sorry mpvano putting your head in the sand 'it works for me' does not mean there is not and issue, though I agree why should I care if he ditches dapper on 140 machines ;-) 

At present 70% of dapper users are finding wireless more problematical than Breezy that's a large percentage when the dapper team advertised 'improved wirless support'.

For your reference the 2 most screwed up cards are the prism2 and prism54 chipset cards.

the prism54 is so badly borked that you need to use the ndiswrapper for v1 cards because 

islsm (dapper default) bearly beta grade driver (from prism54 developers) does not support wpa yet.

prism54 native linux driver for v1 cards has been working great since 2.6.10 when it was integrated in the kernel borxed in dapper kernel (upgrade to 2.6.16 will fix this -- downgrade to pre 2.6.15-19 will also resolve).

---

### Post by timefortea on 2006-07-02
I have been unable to get my Netgear MA401 working in 6.06 (Xubuntu). I piggy-backed someone else's topic here with the details of the issue [http://www.ubuntuforums.org/showthread.php?t=206912](http://www.ubuntuforums.org/showthread.php?t=206912) but haven't got any further info. This is a Prism chipset too. Last night I installed SUSE 10.1 and I got the card working, but I prefer Xubuntu and will be reinstalling it.

Disturbingly, I read somewhere last night that the Netgear WG511 worked best under Linux, so I ordered one of those to try. Now I read that its chipset, the Prism54, is faulty under 6.06 too :cry: 

Can anyone can shed any light on what could be wrong with the MA401? If its not worth trying to fix it, what PCMCIA Wireless card should I get which will work well with 6.06?

---

### Post by dickmorrell on 2006-07-04
mpvano,

I have been around open source probably 10 years longer than you have... and a pretty accomplished developer / project manager / project founder. I am stating on the record there are issues with Dapper and Prism2/Prism54. If I thought this was an easy fix I wouldn't have posted would I ?

Engage brain before posting.

---

### Post by cyboreal on 2006-07-11
It seems that the problem can be solved (at least for my mini-PCI Prism 2.5 card) by editing /etc/iftab and changing the entry for eth1 to wlan0 and rebooting.  I'm not sure what is going on under the hood but it seems the kernel is fine using eth1 but the userland tools are choking when looking for wlan0.  By renaming the interface to wlan0 (using the same MAC address) all the tools - kernel and userland - are working as expected... at least KNetworkManager now connects to my WPA router at home and the WEP router at work.  I also changed /etc/network/interfaces so it looks like this:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---


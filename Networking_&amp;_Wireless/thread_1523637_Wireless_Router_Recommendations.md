---
title: "Wireless Router Recommendations?"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by PanP5 on 2010-07-03
Can anyone recommend a good wireless router?

I just bought Cisco Linksys E2000 Router and was really frustrated with it. In addition to your normal wireless network, it also sets up a guest network, by default. It's a cool idea, in that computers on the guest network don't have access to any resources you have on your main network. 

However, the ONLY way to edit its settings (change its password, turn it off, etc) is to install software on to your computer. The standard router interface that you'd access via 192.168.1.1 doesn't have any control over it. As you'd guess, the software can only be installed on a PC or a Mac. If you only use some version of Linux as your OS, you have no control over the guest network.

Even if have the software installed, if you change the router password via the standard interface rather than with the software, YOU LOSE ACCESS TO THE SOFTWARE! (and, consequently, the guest network). In that case, the only thing you can do to get access again is to restart your router. 

Sooo, I returned it. Can anyone recommend a router?

---

### Post by VeeDubb on 2010-07-04
Depends what you want your router to be capable of.

I just upgraded to the Netgear WNR3500L about 6 weeks ago.

There is never a need to use the software disc that came with it.  Absolutely everything is configurable through the web interface, which defaults to 192.168.1.1

It supports B G and N networks, although it's not an active dual-band, so if anything on your network is at 2.8ghz, everything drops to 2.8ghz.  Really not a big deal unless you have multiple devices connecting at 5ghz, and you really need 5ghz.  Also, contrary to the idiots at BestBuy, dropping to 2.8ghz, does NOT mean that you're dropping to G speeds.  You still get N speeds. You're just stuck opperating on the same frequency as bluetooth, cell phones, cordless home phones and a million other things, so you lose some range and some resistance to interferance.

It also has open source firmware.  Yup, the firmware is open source.  You can get modified firmware rolled by the community, or even roll your own if you're capable.

As an added bonus if you have network file shares, it has gigabit ethernet.  Probably a non-issue for most people, but if you're like me, and you have hundreds of ripped movies stored on an NAS, gigabit is a lifesaver.

---

### Post by PanP5 on 2010-07-04
> **VeeDubb said:**
> Depends what you want your router to be capable of.

I just upgraded to the Netgear WNR3500L about 6 weeks ago.

There is never a need to use the software disc that came with it.  Absolutely everything is configurable through the web interface, which defaults to 192.168.1.1

It supports B G and N networks, although it's not an active dual-band, so if anything on your network is at 2.8ghz, everything drops to 2.8ghz.  Really not a big deal unless you have multiple devices connecting at 5ghz, and you really need 5ghz.  Also, contrary to the idiots at BestBuy, dropping to 2.8ghz, does NOT mean that you're dropping to G speeds.  You still get N speeds. You're just stuck opperating on the same frequency as bluetooth, cell phones, cordless home phones and a million other things, so you lose some range and some resistance to interferance.

It also has open source firmware.  Yup, the firmware is open source.  You can get modified firmware rolled by the community, or even roll your own if you're capable.

As an added bonus if you have network file shares, it has gigabit ethernet.  Probably a non-issue for most people, but if you're like me, and you have hundreds of ripped movies stored on an NAS, gigabit is a lifesaver.

Thanks! I don't require much at. All I really need is wireless router fast enough to let me stream media online and that provides reasonable download speeds. I'm also starting to explore my Ubuntu install, so I need something that's compatible with that environment as well. Sounds like a fit :)

---

### Post by VeeDubb on 2010-07-04
> **PanP5 said:**
> All I really need is wireless router fast enough to let me stream media online and that provides reasonable download speeds.


That actually doesn't require much at all.

Despite the commonly held opinion that you need N wireless for that, you really don't need anything more than G, and even B will get the job done if you're in a situation where signal strength isn't a problem.

If you have a 5Mb internet connection, which is plenty for high def, you don't need a 300Mb home network.  At 54Mb (G speeds), it's already almost 11 times as fast as your internet connection.

The only reasons to go with N are:

a. You need the extra signal strength.  
b. You plan to be transferring large volumes of data over the home network, like moving huge files from one computer to another, or using the wireless to back files up to a home server.
c. You have to compete with a lot of other RF interferance in the same range as G, and you're able to get around it by sticking with a purely 5ghz N draft network.

---

### Post by Darkness Des on 2010-07-04
The D-Link DIR-615 is what I use, it supports Wireless B, G, and N. I personally like the Linksys WRT54G, but it only supports B and G.

---


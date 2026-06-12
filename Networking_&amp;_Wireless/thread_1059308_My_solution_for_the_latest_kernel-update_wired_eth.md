---
title: "My solution for the latest kernel-update wired ethernet breakage"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by Dynaflow on 2009-02-03
After spending a couple hours changing random things here and there, I finally seem to have triumphed over the bug that came with kernel 2.6.27-11, which has been responsible for a lot of people losing their ability to use wired ethernet.  Now, this isn't very scientific, I'll warn you; this was more the product of a couple hours of desperate, semi-random tinkering.  If anyone sees some sort of method to my madness, I'd be curious to know what it is.

So, first off, we should look in /etc/network/interfaces.  Does the file look anything like this?:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```
Does that look right to you?  I have no idea what it should look like, because I am an ignoramus and a philistine.  However, I did notice that the last line was commented out.  I uncommented it, tried to make things work, made things worse, and re-commented it.

By the time I hit this point, I had been reading forum posts and mucking around with complicated things about which I know almost nothing for at least an hour, and so I indulged in threatening my laptop with a large knife and some rather coarse language.  I feel this was an important step, and marked a turning point in this battle.  

After I had finished re-establishing alpha dominance over my hapless laptop, I right-clicked the Network Manager applet, went for Edit Connections, found myself at the Network Connections window, and proceeded to strip out all memory of Auto eth0.  Then I restarted.  When I logged back in, Auto eth0 was back, and so I deleted it again and replaced it with a new, minimalist Auto eth0 (just the name, really).  Then I restarted again.  

When I logged back in *this* time, I saw the applet seeking and then give up, looking as if there was no network to be had whatsoever.  However, I noticed that my Netspeed applet elsewhere on my panels was getting some traffic, so I opened Firefox.  Lo and behold, ... Internet.

I hopped onto Synaptic to see what kind of snake oil I could find to make the miracle stick, and found nictools-nopci and nictools-pci, the blurbs for which state that "these tools can help you to diagnose problems with your ethernet cards or - in some cases - give those cards the final hint, to work in your network."  It sounded like a good pitch, and what harm could they do?  

After installing those two packages (and Aircrack, which I had forgotten all about :p ), I decided I'd also mark network-manager and network-manager-gnome for reinstallation, just for the hell of it.  I was asked to restart, so I did.  After logging back in once again, I found Network Manager was working as it should, finding a newly-created, real Auto eth0, and generally allowing me to connect to the network at the speeds I would expect.

For technical details, I'm using a Compaq Presario C706NR that sports a Realtek RTL-8139/8139C/8139C+ (rev 10) NIC.  My initial symptoms were momentary (though real and external) connections that quickly fell to ludicrously-slow speeds before being dropped altogether.  Xorg would also really be racing as the connections failed.  This all started immediately after the last kernel update to 2.6.27-11.

Hope this helps somebody.

---

### Post by ajgreeny on 2009-02-03
This may be of no consequence at all, but my /etc/network/interfaces is similar to yours, but has shorter contents with the *auto eth0* line missing completely.  I have only a wired connection, no wireless, which could perhaps explain this difference, but I thought this might just allow someone with a lot of networking skill to pinpoint the reason for the your problem, or even its solution.

Here's mine, just two lines!

auto lo
iface lo inet loopback

---

### Post by Iowan on 2009-02-03
Rumor has it (OK, I read it somewhere here on the forums) NM ignores what is in /etc/network/interfaces, so to have NM manage eth0, remove it from /etc/network/interfaces. Dunno if it actually works that way...

---


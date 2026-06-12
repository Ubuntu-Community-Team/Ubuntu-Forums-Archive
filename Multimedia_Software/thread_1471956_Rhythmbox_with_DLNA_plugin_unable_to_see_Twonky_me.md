---
title: "Rhythmbox with DLNA plugin unable to see Twonky media server"
date: 2010-05-03
forum: Multimedia Software
---

### Post by a_deano on 2010-05-03
Hi,
I have been trying to get this setup working for a day now, and starting to get frustrated. Hopefully someone out there can help me out.
I have;
QNAP NAS box running Twonky 5.1.3
I can browse to it and use the web browser to see all of the media I have uploaded to it.
I have a ubuntu lucid clean insalled system with rhythbox and the coherence DLNA plugin. I cannot get the rhythmbox to see the media on the server. Very briefly at one point I saw the server name appear as RB started, but it disappeared immediately. I have something like 5K songs up mostly in MP3 format.

Any help debugging this or info from someone who has a similar setup working would be greatly appreciated.

---

### Post by a_deano on 2010-05-04
I have some further info, interestingly the server appeared in Rhythmbox last night and I listened to a whole album. Ahhh Quadraphonia, masterpiece.

This morning though no server in Rhythbox again, I would really like some help to debug this. Even just a pointer to where things might log?

I have downloaded and used the UPnP Inspector app from [http://coherence-project.org/wiki/UPnP-Inspector](http://coherence-project.org/wiki/UPnP-Inspector) and it sees the server. I have attached the device description XML that this app output if that helps anyone.

Hope someone can help me out here.

I should also mention that I have tried Totem with the coherence plugin with the same results, it can't see the server. Although it does see the Rythmbox when it is running.

---

### Post by drknot on 2010-05-27
I have had some issues with my Twonky being visible at all (Twonky 4.4.2 running on a FSG3 NAS, firmware 4.4.5)

[http://coherence.beebits.net/wiki/RhythmBox](http://coherence.beebits.net/wiki/RhythmBox) suggests adding necessary route.

My experience is 

sudo route add -net 239.0.0.0 netmask 255.0.0.0 gw {IP of Twonky} {wlan0/eth0 as appropriate}

I have Twonky on a static IP
If you enable SSDP in the troubleshooting and check the logs on the Twonky, it will show the HOST ip (239.xx.xx.xx) so you could route the specific IP

This reliably makes my Twonky visible to Rhythmbox and VLC :)

Sorry above line is not cut & pastable.

Someone with better knowledge of defining routing tables may be along shortly.

If this works for you is then [solved]?

---

### Post by drknot on 2010-05-27
*if* this works for you, to make it permanent
 
edit /etc/network/interfaces (as administrator)
add to the bottom

up /sbin/route add -net 239.0.0.0 netmask 255.0.0.0 gw {whatever} 

edit : corrected syntax.
reference : [http://ubuntuforums.org/archive/index.php/t-234207.html](http://ubuntuforums.org/archive/index.php/t-234207.html)
interface does not need to be specified  - I assume leaving it blank means if eth0 comes up, the route will appear for that as  well

---

### Post by wkulecz on 2010-05-27
Could someone please explain the rationale  of this DLNA thing?  I mean if you want file sharing, why not just share files. Doh!

Easy to use and compatibility doesn't seem close to being there.  I screwed around with it a bit using Tversity and the "server" built into my Linksys Wireless-N router when we had Direct TV and it was way more trouble than it was worth -- the DirectTV part of it was particularly lame.

Samba is "free" and since Windows dominates the market why re-invent the wheel?

Setting up Samba server shares or connecting to Windows shares couldn't be easier in 10.04, although it'd help if the Places->"Connect to Server" defaulted to Samba instead of FTP.

---

### Post by drknot on 2010-05-28
Ok, a bit more fiddling - the interfaces addition didn't work

following the referenced link, I now have a script file (static routes) in /etc/network/if-up.d
This works.

---

### Post by gillani on 2010-08-31
I have a Western Digital World Edition II with Twonky media server.  My PS3 can see the media server so I know it works.  I can not see the media server using the Rythmbox dnla plug in nor the upnp inspector. I tried adding the route but that didn't help.

Any Suggestions please?

---

### Post by Kubular on 2012-04-05
Realising that this thread is quite old now but it's relevant to me so posting a reply.

First, someone asked why you would want to use twonky.

I use twonky to serve media (mainly music) from a Netgear ReadyNAS Duo that host my music library. The NAS is running 24/7 and is accessable from more or less any device on my network, with the single exception of Rhythmbox..

My music library is quite extensive and the ability to access the library held by twonky is extremely useful (I do not enjoy waiting for my computer based client to rebuild a library every time I want to listen to something).

I primarily play my music via my hifi, which is solely a renderer and does not have it's own control interface, for that I have my phone and laptop (if need be). This is far more elegant than any other setup I've ever used.

The only place I have problems is trying to find good PC software that will make use of the server.

If anyone has any ideas how to get this working with Rhythmbox (or an alternative player) under 12.04 they'd be much appreciated. Struggling to find a good plugin.

---


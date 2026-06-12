---
title: "Wireless network disconnects every couple of minutes, tried everything."
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by alinutza20 on 2011-02-07
Hello everyone! I know this problem has been raised millions of times before, but none of the solutions that seem to have worked for others have done anything for my problem. I've recently installed Ubuntu 10.10 and everything works great except the internet. My wireless connects just fine, but in a few minutes it stops working and I have to disconnect and reconnect for it to work again. I'm dual booting with Win 7, and my internet works great there. :confused:

I've tried the backports solution, the ndiswrapper solution (which resulted in the dissapearance of all my wireless connections, despite the driver being recognized), NOTHING is working. I feel like I'm going crazy, because as much as I love this OS, I NEED internet! ](*,)](*,)](*,)

Anyways, if someone can guide me in any way possible, I'd immensely appreciate it.

I'm running Ubuntu 10.10 and my wireless card is Atheros AR9285.

Thanks a lot! :-)

---

### Post by james_xxx on 2011-02-07
alinutza20,

The PC I am using right is running Maverick, and using an Atheros AR9285 (rev 01) wireless adapter. I have experienced no problems at all.

Is yours also a 'rev 01', or does it have a different revision number?

---

### Post by alinutza20 on 2011-02-08
Hello James! As far as I can tell, mine doesn't mention any rev. It's true, it seems that some people don't have any problems, but I just can't figure out what's going on. The router is fine, Windows and Android work great with it, but in Ubuntu the internet refuses to work right. Aside from the solutions I already mentioned, I've also tried a fresh install, but the problem stays the same. Even when accessing the internet from the LiveCD I get the same problem. I really don't know what to try next... :confused:

---

### Post by alinutza20 on 2011-02-10
Ok guys, for anyone else who is sharing my problem, I managed to (somehow) fix it. Uninstalling networkmanager and installing wicd instead seems to keep the wireless connection stable. It's a temporary solution, but it's definitely better than nothing. \\:D/

---

### Post by dalekirkwood on 2011-02-20
All of a sudden im having huge problems with my Wi-Fi.

You could try this

[http://ubuntuforums.org/showthread.php?t=1341618](http://ubuntuforums.org/showthread.php?t=1341618)

It has sort of fixed my problem. 

P.S. How have you managed to get WICD to run without network manager?

---

### Post by alinutza20 on 2011-02-21
Hey, dalekirkwood! I'm sorry you're having trouble with your WiFi, it's frustrating as hell. Well, since I posted about the Wicd "solution", I realized that it doesn't work as well as I thought so I gave up on it. I wouldn't advise you to try it, the issue seems to come from elsewhere. I went back to networkmanager and now the connection seems to be steady (it doesn't interrupt anymore), but my internet is often very slow, so I still haven't really fixed it. I'll try the post you recommended and I'll get back to you.

Good luck and thanks! :)

---

### Post by dalekirkwood on 2011-02-21
Thanks for your reply. Just to let you know this has driven me mad. I almost looked out my Windows 7 disc but I decided to reinstall Ubuntu 10.10 and I am now sending this message over a steady wireless (fingers crossed). My Nautilis had also messed up. I think the updates for Ubuntu are a bit risky so I don't plan on doing any updates to this install. I would recommend the same. Bit of a pain but this is what we bestow upon ourselves as Linux users :-).

---

### Post by Keiran230 on 2011-02-21
> **dalekirkwood said:**
> I think the updates for Ubuntu are a bit risky so I don't plan on doing any updates to this install.

By chance are you using a WUBI install? I've noticed myself that whenever I update an Ubuntu system that was installed using WUBI, it crashes almost every time. Since I made a full, normal install, updates have only ever broken one thing, which I was able to repair with some tinkering.

@alinutza20: I noticed you're using an Atheros chip. Perhaps you're having a similar bug to [**this one**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/610440"). If your disconnects are also accompanied with high CPU usage, this is probably the bug. Check the system logs to be sure, if you think it is.

---

### Post by dalekirkwood on 2011-02-21
> **Keiran230 said:**
> By chance are you using a WUBI install? I've noticed myself that whenever I update an Ubuntu system that was installed using WUBI, it crashes almost every time. Since I made a full, normal install, updates have only ever broken one thing, which I was able to repair with some tinkering.

@alinutza20: I noticed you're using an Atheros chip. Perhaps you're having a similar bug to [**this one**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/610440"). If your disconnects are also accompanied with high CPU usage, this is probably the bug. Check the system logs to be sure, if you think it is.

Thanks for your reply. Firstly no bot a WUBI install. This is a full blown proper install (might be worth mentioning this is a 64bit system).

I looked at the site and I'm not sure its the same problem. I don't seem to have speed issues or trouble running on battery. I looked at the logs but I'm not really sure what to look for but there is plenty about the WLAN in there.
 
Like I say I have completely re-installed the system and have disabled all updates but even though it's better it has started cutting off the net, then asking for WEP key (the key is there but I have to click connect) doing that about 4-5 times before eventually reconnecting again. Also it seems to be very jumpy on signal, going from 22% up to 57%. The strangest part is that I have had Ubuntu 10.10 for about 4 months now and this problem has only just started. Bit Weird. 

Also the connection is going on and off while I type this. Stupid thing.

---

### Post by myosotis on 2011-02-23
I have the same problem with the same version of Ubuntu and the same Atheros card. Or should I say had. I tried the thing someone suggested with installing wicd instead and uninstalling network manager. Which did not work. And now after reinstalling network manager it doesn't work at all. So I'd be happy for any suggestions too.

---

### Post by gordintoronto on 2011-02-23
If you click the network manager icon, do other strong networks appear? If so, try changing to different channels.

By the way, WEP has been cracked, so you should use WPA if your router supports it.

Did you find "Atheros AR9285" by running lspci? If there's a rev, it should appear there.

---

### Post by dalekirkwood on 2011-02-23
> **myosotis said:**
> I have the same problem with the same version of Ubuntu and the same Atheros card. Or should I say had. I tried the thing someone suggested with installing wicd instead and uninstalling network manager. Which did not work. And now after reinstalling network manager it doesn't work at all. So I'd be happy for any suggestions too.
I have half found a solution. Are you running 64 bit or 32 bit?

---

### Post by myosotis on 2011-02-24
I'm running 64-bit. And now my ethernet connection seems not to work either, and wireless is still spotty.

---

### Post by myosotis on 2011-02-24
> **gordintoronto said:**
> If you click the network manager icon, do other strong networks appear? If so, try changing to different channels.

By the way, WEP has been cracked, so you should use WPA if your router supports it.

Did you find "Atheros AR9285" by running lspci? If there's a rev, it should appear there.

I'm not sure if this was a question for me or for the original poster, but here are my replies:

Yes, I find other networks (my neighbours') but all of them are protected.

I use WPA

I found it running lspci. It's rev 1.

---

### Post by dalekirkwood on 2011-02-24
> **myosotis said:**
> I'm running 64-bit. And now my ethernet connection seems not to work either, and wireless is still spotty.
Try running off a 32 bit install (Just try live cd to test) works fine for me but Ubuntu has some issues running a 64bit on a 32bit install with libraries. Very annoying problem. I love Ubuntu but I don't like these little problems :-(;

---

### Post by myosotis on 2011-02-24
> **dalekirkwood said:**
> Try running off a 32 bit install (Just try live cd to test) works fine for me but Ubuntu has some issues running a 64bit on a 32bit install with libraries. Very annoying problem. I love Ubuntu but I don't like these little problems :-(;

I'll try that this weekend. Busy week *and* internet problems. Ans I agree about Ubuntu. Love it, but hate when this happens.

---

### Post by frostpearl on 2011-02-24
I'll jump into this conversation as another victim.

I'm running 32bit Ubuntu 10.10, Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01) and as the security method I'm using WPA & WPA2 Personal authentication. 

The wireless transmitter is five meters away, and there is one wall between. We have four computers in our network in total and this is the only computer with a Linux installed. The other three computers run either Windows Vista or Windows 7. All the other computers have a normal, seamless connectivity to the wireless Internet.

The connection on this Ubuntu machine drops every few minutes for a duration ranging from a few seconds to a few minutes at most. I would say the blackouts last 20-30 seconds on average. Most of the time it's not enough to seriously disconnect me from the network or instant messaging software, but it causes a major lag spike during which nothing goes or comes through the Internet. Thankfully many flash video providers such as YouTube buffer the entire video while there is connectivity, but what the heck?

I've set-up Ubuntu on several computers during the past few years and I've randomly run into this problem before. Sometimes the problem has just vanished over time, but I've never found a way to fix it. I would also like to add to this that I took my laptop to work last week. I work at a public school with roughly 120 computers connected to it on a wired connection and another 150 laptops or other devices on a wireless connection. The connection on those devices works fine, but unfortunately the same problem persists on my Ubuntu laptop - the connection drops every few minutes.

---

### Post by baceman007 on 2011-04-22
Although I'm not 100% sure that this will apply to all of you with all of the software and hardware involved in the chain here I had the same problem where my wireless connection would work fine unless I played a video from you tube, or a flash source in general, through Firefox 3.6 or Chromium 10.0.648.205 (81283). My wireless connection would disconnect. I tried WiCD instead of Network Manager, went back and forth between the two, different flash plugins, etc. but in the end what fixed my problem was to go to Security>Firewall>Filter Multicast and check it to enable it on my router. (The router is a Linksys E3000). After I did that my problems disappeared. I am using 32-Bit 10.04 LTS on a Toshiba A-100 series laptop. I guess what I'm saying is that you might want to look at your router's settings over too if the other methods listed here don't seem to be solving your problems. :p

---


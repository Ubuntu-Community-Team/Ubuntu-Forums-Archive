---
title: "Internet Connection Sharing"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by Gonz_91 on 2010-02-25
Hello everyone!

I'm trying to set up a wireless or wired network (wireless would be better...) to share my connection with my housemate, as well as with some devices.
The only guide I found regarding this (I must admit, I didn't have much time to put into research), was dating back to 2005, and although doable, seemed somewhat confusing.
Getting to the point: is there a way (maybe a standalone program, or some kind of plugin) to share a connection?

Thanks a lot! ;)
Gonz

---

### Post by mosquetero on 2010-02-25
I am not sure if I know what you want. You will have a direct internet connection and your partner wants your computer to provide him internet, is it?

Internet ----- You ------- your partner

---

### Post by Gonz_91 on 2010-02-25
> **mosquetero said:**
> 
Internet ----- You ------- your partner


Exactly :D

---

### Post by mosquetero on 2010-02-25
Use a proxy called squid.

[http://ubuntuforums.org/showthread.php?t=1262827](http://ubuntuforums.org/showthread.php?t=1262827)

Search on the internet for tutorials, it is not too hard to configure

---

### Post by dmizer on 2010-02-25
First try sharing the connection via wired. You may have to use a [crossover cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") instead of a standard network cable.

Then, right click on NM-applet in your system tray (looks like two plugs connected to eachother), and select "edit connections". There should be two adapters listed here, one that you use to connect to the internet, and the other that your housemate's computer connects to (one may be listed under wireless, and the other under wired).

Click on the adapter your housemate will connect to, and select "edit". Click on the "IPv4 Settings" tab, and change "Method" to "Shared to other computers"

That's it.

---

### Post by Gonz_91 on 2010-02-25
Thank you both for your replies!
I'm not at home right now, nor do I currently have both the computers around, but I'll try it at home, then report.



Once again, thanks a lot

---

### Post by Gonz_91 on 2010-03-04
So, reporting back.

Well, I can connect to the internet when my colleague shares it through a wired connection, using a normal network cable, but I can't establish the connection when I (using Firestarter) want to share.

Why would I need a crossover cable when a normal cable works from windows to linux?

Thanks a lot

---

### Post by Iowan on 2010-03-04
> **Gonz_91 said:**
> Why would I need a crossover cable when a normal cable works from windows to linux? Some gigabit cards can auto-configure, but the kind I generally use need a crossover cable to go from computer-to-computer. Straight cables work if there's a hub/switch/router.

---

### Post by Objekt on 2010-03-04
In my testing, I've found that crossover cables are *usually* not necessary.  Anything new enough to have a gigabit NIC can probably use a standard cable for sharing, but exceptions are possible.

Beyond that..I'm confused.  Did you mean that you got Internet connection sharing working as long as all the connections were wired, but it wouldn't work when one of the connections was wireless?  Or something else?

Also, please tell us more about your gear.  Are you using two laptops with built-in wireless as well as wired NICs, or is one of them a desktop with a wireless card, or what?

---

### Post by Gonz_91 on 2010-03-06
> **Objekt said:**
> In my testing, I've found that crossover cables are *usually* not necessary.  Anything new enough to have a gigabit NIC can probably use a standard cable for sharing, but exceptions are possible.

Beyond that..I'm confused.  Did you mean that you got Internet connection sharing working as long as all the connections were wired, but it wouldn't work when one of the connections was wireless?  Or something else?

Also, please tell us more about your gear.  Are you using two laptops with built-in wireless as well as wired NICs, or is one of them a desktop with a wireless card, or what?

Well, I've shared connections, using this laptop, with a standard cable before, under Windows...

Anyway, here's the complete set-up:
A mobile broadband dongle (which works just fine under Ubuntu, which makes me a happy user :)) connected to my friend's Toshiba Laptop (A500, like 6 months old) who is sharing the connection via wired to my Toshiba L300 (2 y/o). This setup works, and I get a connection.
Then, if he switches the sharing to a WEP ad-hoc connection we had set-up before I switched back to ubuntu, I can't access it, get an eternal loop of "Please insert the password" dialogs.
Additionally, if I plug the dongle into my laptop, I can't share the connection using neither wired nor wireless: wired won't connect (eternal "identifying" on the Windows side, and a timeout on Ubuntu); and regarding wireless, I just can't find enough information in order to be able to successfully configure an ad-hoc host on Ubuntu...

Thank you all for your replies ;)

---

### Post by Gonz_91 on 2010-03-15
Bumpity-bump.


(Sorry, sorry, but since the last posting was a week old, I resorted to bumping. I won't be bumping anymore, don't worry.)

---

### Post by Objekt on 2010-03-15
Not a problem.  Sometimes a bump is what it takes to get an answer.

Many weeks ago, I began having a very similar problem to yours.  I still don't have it fixed, which is why I don't say "had" such a problem.  It is still there.  Since I have more gear, including a router, I've been able to work around the problem, but it still annoys me that something so (supposedly!) simple does not work.  I don't like having that loose end hanging about.  Figuring out a fix might mean I could help people like you.

Here are the essentials:

I have a desktop machine running Ubuntu 9.10, which has two wired network devices, named eth0 and eth1.  One (eth0) is plugged into a router, which connects through my cable modem to the Internet.  I wanted to use the extra network device (eth1) to share my Internet connection with a netbook running Windows XP.  

In principle, this is what you are trying to do.  The important difference is, you want to share a wireless connection, instead of a wired connection (which you already got to work, apparently).

Well, you're ahead of me.  To date, I can't share my second wired connection.  So there I am.

Here's what's crazy: the sharing DOES work, with the same hardware described above...IF and ONLY IF the desktop machine is running a Live CD session of Ubuntu 9.10.  It doesn't matter whether the client is running Windows XP or Ubuntu Netbook Remix or Windows 7; ICS "just works" as advertised.  All I have to do is set eth1 to "shared" status in NetworkManager, as described in most of the tutorials you will find on the Web.

At one point I could not think of anything else to do, so I simply copied exactly the configuration files for NetworkManager when it was running in the Live CD session.  I then applied them to my Ubuntu 9.10 installation.

Next I looked at what IPtables was doing (or wasn't doing, as case may be).  This could be the key.  I've found that I have different rules in IPtables when running the Live CD session vs. running installed Ubuntu 9.10, although I haven't figured out how to fix it yet.

Please try setting up the sharing via wireless again, and tell us what you get when you run this command:
```
sudo iptables -L
```
on the host you are trying to share from.

---

### Post by Gonz_91 on 2010-03-15
Hello there!

Well, I don't have wired sharing working, I can't share via wired. I can have it shared by the Windows box, though.

Also, I don't seem to know how to set up an ad-hoc network to which other devices can connect (this isn't actually an issue related with Ubuntu, it is indeed related to my own lack of knowledge. Help would be greatly appreciated!)

Additionally, when my friend comes home, I'll try setting up ICS via wired (using my Ubuntu box as server) and report back with the output of iptables -L.

---

### Post by Objekt on 2010-03-15
> **Gonz_91 said:**
> Additionally, when my friend comes home, I'll try setting up ICS via wired (using my Ubuntu box as server) and report back with the output of iptables -L.

I thought that was what you were trying to do in the first place, EXCEPT you want to make the link between your Ubuntu server and his Windows (?) client wireless.  Did I get that right?

---

### Post by Gonz_91 on 2010-03-15
> **Objekt said:**
> I thought that was what you were trying to do in the first place, EXCEPT you want to make the link between your Ubuntu server and his Windows (?) client wireless.  Did I get that right?

Indeed, that is my primary goal, but the ability to do that wirelessly would be marvelous!

---


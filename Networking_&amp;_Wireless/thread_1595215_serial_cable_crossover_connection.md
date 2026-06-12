---
title: "serial cable crossover connection"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by ofb on 2010-10-13
I've been reading too much and understanding too little.

What I have: Lucid laptop & desktop. Both have ethernet > hub > internet.

What I want: connect them directly by the serial ports so the laptop can access the desktop's drives, and the desktop can be retired from the internet.

I've got an old DB-25 null-modem, last used for multiplayer Doom. The laptop's dock has DB-9, so the connections is desktop > null-modem > Belkin DB-25 - DB-9 cable > laptop.

I had hoped this post would get me somewhere:
[http://www.ge.ubuntuforums.org/showpost.php?p=7909020&postcount=9](http://www.ge.ubuntuforums.org/showpost.php?p=7909020&postcount=9)

No such luck. When I ping 'grin.local', the connection is through the internet. If I disconnect the hub, i cannot ping.

Dunno if there's something more I should do to enable serial connection in Lucid, or if my null-modem is no longer good.

I'm also rather curious how "grin.local" manages a connection through my ISP's system. These are DHCP. Shouldn't that have required the full numerical IP? 

(It's nothing to do with the hub. Checked that by connecting a third box to the hub. My ISP only hands out two IP. I couldn't ping the third box.)

---

### Post by ofb on 2010-10-13
Meanwhile, statserial for the laptop returns "TIOCMGET failed: Input/output error". BIOS shows it's Enabled and set to COM1. statserial on the desktop side has a proper output.

NEW OPTION: Found a D-Link PCMCIA card. Completely forgot I owned one. So have that, an ethernet null-modem cable, and a second card in the desktop as well. However I'm still getting nowhere with Lucid.

I thought Avahi was supposed to take care of this sort of thing. Is it busted in Lucid? 

Farthest I've gotten is by creating new 'Wired Connection 1' on each, set to link-local. That gives each secondary ethernet card a 169.* IP. Both cards light up when I connect the cable, but I cannot ping.

---

### Post by ofb on 2010-10-14
Looks like Lucid/Avahi doesn't care for multiple ethernet cards. If I remove the laptop's internet connection, then create a new 'Wired Connection 1' on each set to link-local, then I can ping through the null-modem.

[Curiosity: I can achieve this by unplugging the internet from the laptop's built-in ethernet & using the PCMCIA DLink on null-modem. Or I can use the built-in ethernet on null-modem, but only if I completely remove the DLink. Just unplugging its cable isn't enough. If I the DLink is installed, I can't use the built-in ethernet with null-modem. And yes, I did try this with fresh boots each time. Very odd.]

However the DLink has very poor connection quality -- half the speed, and drops about a third of the packets. This was a reason I'd forgotten about that card in the first place. So, back to serial connection.

In the laptop's BIOS I changed the port from COM1 to COM2, and now I get a proper response from statserial.

But that's as far as I get. Lucid's 'Network Connections' panel seems to only handle ethernet and wifi. Serial doesn't seem to exist there.

1) How do I ping to test the serial null-modem?

2) How do I use this connection to access files?

---

### Post by Iowan on 2010-10-14
I'll try to find some of my *old* notes.  I had a machine set up as a (FREESCO) router that used a serial connection (as TTY). It worked as a remote console, but I'm sure it would have painfully slow to transfer files...

---

### Post by ofb on 2010-10-15
Thanks.

Is it like this? 
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

I don't understand how to get from that to establishing a TCP/IP connection. 

I'm guessing that's what I want, anyway. TCP/IP and SSH so I can just select Places > Connect To Server to access files via Nautilus. Or NFS or Samba I suppose, since it's a local connection.

BTW, why would it be slow? Wouldn't it have at least the speed of the modems we used to run? I'm meaning to use this connection to access files in place for things like images and music and movies. Is that overoptimistic?

---

### Post by ofb on 2010-10-24
--Summary for people who search the forums--

It sounds like serial is indeed too slow.
[http://tldp.org/HOWTO/Serial-HOWTO-5.html#ss5.2](http://tldp.org/HOWTO/Serial-HOWTO-5.html#ss5.2)

> 
5.2 RS-232 Cable Is Low Speed & Short Distance 

The conventional RS-232 serial port is inherently low speed and is severely limited in distance. Ads used to read "high speed" but it can only work at "high speed" over very short distances such as to a modem located right next to the computer. Compared to other connections to a PC such as as a USB bus, network card ethernet, or IEEE 1394 (firewire), this claimed "high speed" for a serial port is actually low speed. All of the RS-232 serial cable wires use a common ground return wire so that twisted-pair technology (needed for high speeds) can't be used without additional hardware. More modern interfaces for serial ports exist but they are not standard on PC's like the RS-232 is. See Successors to RS-232. Some multiport serial cards support them.

It is somewhat tragic that the RS-232 standard from 1969 did not use twisted pair technology which could operate about a hundred times faster. Twisted pairs have been used in telephone cables since the late 1800's. In 1888 (over 120 years ago) the "Cable Conference" reported its support of twisted-pair (for telephone systems) and pointed out its advantages. But over 80 years after this approval by the "Cable Conference", RS-232 failed to utilize it. Since RS-232 was originally designed for connecting a terminal to a low speed modem located nearby, the need for high speed and longer distance transmission was apparently not recognized. The result was that since the serial port couldn't handle high speeds, new types of serial interfaces were devised that could: Ethernet, USB, IEEE 1394, etc. All of these use high speed twisted-pair cabling as recommended by the "Cable Conference" of 1888



Meanwhile I've got the PCMCIA card working well enough for Samba. (I use an ethernet crossover cable. Most new computers have ethernet ports that can use a standard cable.) 

Samba setup has its own issues in Lucid. Search the forums for help. Below are the key notes I jotted down for myself.

Don't ask me what the Personal File Sharing panel is for. The relevant section is blanked out with the note "This feature cannot be enabled because the required packages are not installed on your system." But nothing there, or under Help, tells you what packages you need.

Even better, after I got Samba set up, that PFS panel continues to make the same claim.

> 
--------
[http://ubuntuforums.org/showthread.php?t=1201809&page=2](http://ubuntuforums.org/showthread.php?t=1201809&page=2)


Download Samba from Applications -> Add/Remove..

Once installed, run Samba from System -> Administration

Open Preferences from the menubar -> Samba Users

Add a new user. Don't worry about the Unix username. Just fill out everything else with respect to the client PC that will access the files. 

Next, Add Share (from the main Samba GUI).

Find your directory of interest and add it. Then click the Access tab and enable access for your newly created user. 

Close Samba. Now try accessing the share. Hopefully it should work.
--------

--------
[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)


Samba version 3.4.7 is distributed with Lucid through the repositories. To make it work, you need to install a number packages and their dependencies, one being a GUI interface (which has at least one issue that I’ll cover later). From the terminal, that would look like:

sudo aptitude install samba samba-common-bin system-config-samba smbfs smbclient

You can also choose these in Synaptic. The packages will install supporting packages like samba-common. Do you need ALL these packages? I’m not sure to be honest. I ended up installing them all in the process of getting the network sharing to work, and I’m not about to go uninstalling any at this point.
--------


Minor issues - 

Some long filenames are truncated to code. Since I'm using ext3 and ext4, I suspect this is a Samba limitation.

Probably what's really wanted here is NFS, but with Lucid the good GUI for NFS has been removed, so I'm still looking into that.

I've already noticed lots of posts about Lucid NFS being broken by the upgrade to Meerkat, so things aren't encouraging.

Meanwhile if you've got long filenames, you may be better off with sneakernet.

---


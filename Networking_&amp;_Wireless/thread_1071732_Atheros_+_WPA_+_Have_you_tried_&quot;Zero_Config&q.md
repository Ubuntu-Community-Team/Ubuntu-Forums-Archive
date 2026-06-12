---
title: "Atheros + WPA + Have you tried &quot;Zero Config&quot; Yet? - Intrepid 8.10"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by doogleplex on 2009-02-16
Hi there.

I have Atheros chipsets (several pc's) and I was having difficulty connecting to access points, using WPA encryption, and I had the "unsupported driver 'madwifi'" issue (using WPA_supplicant at the command line, after i went to 8.10 Intrepid. In previous versions of Ubuntu, madwifi had worked fine). It is a bit unclear for me, at the moment, what is going on behind the scenes, specifically as it affects wpa_supplicant execution, but i have been told that the "wext" driver may work when madwifi will not. That's not why i am here today though.

It's funny, because for years i was hoping for a 
GUI-based "zero-config"-style wireless network control with Linux (that actually worked out-of-the-box). Apparently, it's a reality now. Pardon my personal excitement, because I'm sure many of you know this, but it is new behavior in the OS (8.10) from my perspective :)
I guess I was so used to wireless connections always being such a manual process, that i never thought to simply click on the network icon, and try to connect to an available wireless network that way...

To make a long story short, through all my upgrades, etc., I hadn't tried to simply click on the network icon on the panel, and connect to an available wireless network using the graphic interface. duh. hehe, it works great. 

So if you are 1. having wireless connection issues, after you upgrade to, or freshly install Ubuntu Intrepid 8.10 (i have done it with i386, amd64, and ubuntu studio amd64 versions), and 2. you have an Atheros Chipset-Based network adapter, and you just want to connect to your network (not wanting to tackle the wpa_supplicant/madwifi/etc. issues right away), AND 3. your Atheros chipset isn't working with the generic drivers that Ubuntu loads when it sees your Atheros based chipset, you might try this:

1. Install the **linux-backports-modules-intrepid-generic** package from Synaptics Package manager (or use apt-get)
2. Restart the computer
3. Activate the newly added "Support for 5xxx Series of Atheros 802.11 wireless LAN cards" in Hardware Drivers (located in System-Administration-Hardware Drivers)
4. Deactivate the generic "Support for Atheros 802.11 wireless LAN cards", also in Hardware Drivers (Probably right underneath the 5xxx entry)
4. Restart your computer
5. See if the regular network manager now shows you a list of available wireless networks. (click on network icon on the panel, often in the upper right part of the screen, by the system clock).
6. Choose your network, and click on it to connect.

I know this is the simplified GUI way, but hey, if it can get you connected right away, then you can work on the other issues at your leisure. I didn't even have to configure an /etc/network/interfaces file or any sort of conf file, etc.

p.s. when i connect, it prompts for the network key, and fully supports WPA encryption, etc. It saves your wireless networks for automatically connecting to the network for subsequent sessions, and they are editable, and the key ring works great too for saving the encryption keys / passwords :) Another reason not to use Windows!!!!

Well I know I'm not the most savvy of posters here, but hopefully everything here is clear enough to follow.

thanks for everyone who has posted about the various atheros issues
also, thanks for the "zero config" after all these years :)

---

### Post by Ryuhayabusa on 2009-05-10
hey man, 

do you have wpa enterprise connection working as well? or wpa personal at home?

peap?


thanks for the help.

---


---
title: "NetworkManager Applet 0.7.0 is a mess!!"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by futz on 2009-04-15
The NetworkManager that came with Hardy Heron (0.6.6?) worked quite well. What happened to the Intrepid Ibex NM 0.7.0? What a bug-filled mess! The quote at the end of this post is what I posted a few days ago. Since then I've had it decide to stop automatically using my wired connection and start insisting on connecting to wireless on every bootup (I have to give it a password and then manually switch to the wired connection), and even just switching to wireless in mid-session, for no apparent reason.

What version of NM will ship with Jaunty? I'm pretty sick of 0.7.0 and hoping they'll ship a properly debugged version.

[quote=futz]My new mainboard (Gigabyte GA-EP45-UD3P) has two onboard ethernet connections. I have both cable and DSL internet, one plugged into each connection. I want to be able to select the one I want to be connected to in NetworkManager at any given time, like I do when I want to switch to one of my three wireless access points.

But it has both marked as active and no matter which of the two I select, it connects to the DSL one. The only way I can switch to cable is to unplug one ethernet cable. That's really annoying!

I have run the Network Connections thing and named them so I could tell which was which, and unchecked "Connect Automatically" on both. There was no change in behaviour after doing this.

Anyone know how to fix this? It shouldn't be too hard, you'd think...[/quote]

---

### Post by Black_Wolf_92 on 2009-04-16
try Wicd out, far more stable to me. Completely uninstalled NM from intrepid, replaced it with Wicd, and nothing wierd has happened yet.

---

### Post by Redhishan on 2009-04-16
Plaese visit [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and download wicd, it should do the work...

---

### Post by KayGenz on 2009-04-16
> **Black_Wolf_92 said:**
> try Wicd out, far more stable to me. Completely uninstalled NM from intrepid, replaced it with Wicd, and nothing wierd has happened yet.


hi black wolf, could you explain me howto uninstall NM and install WICD?? and im sory what us Wicd it was?? i got weird configration with NM and now, i cant click it at all :(

---

### Post by futz on 2009-04-16
Thanks guys. I'll give Wicd a tryout, possibly this afternoon.

---

### Post by futz on 2009-04-16
Though Wicd looks promising, it unfortunately will not properly handle multiple wired networks. They say they're planning to do that in future. I tinkered with it for an hour or so, read their forums for a while and went back to NetworkManager.

So I'm still forced to unplug the DSL ethernet cable to switch to the other wired network (my network printer is on the other network, but I prefer to use DSL for most things on this box).

---

### Post by Black_Wolf_92 on 2009-04-17
ah sorry for the inconvenience, usually Wicd is at least at the same level or ahead of Network Manager.

As for the person wishing to install it:

> Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 

Taken straight out of the installation instructions at the Wicd site. If you do it through the synaptic, using the Wicd Repos, it'll uninstall NM for you without any fuss.

Don't worry if you don't like it though, coz if you DON"T, simply UNINSTALL wicd with synaptic, whack in your LiveCd (make sure you enable it in repositries in synaptic) and find the network-manager-gnome in there, and you can re-install it from the LiveCD without an active internet connection

---

### Post by Iowan on 2009-04-17
Another option is to un-install NM, and re-install the older version.  I'll try to find **dmizer**'s post explaining how.

Found it: [http://ubuntuforums.org/showpost.php?p=6623406&postcount=10]("http://ubuntuforums.org/showpost.php?p=6623406&postcount=10")
There's also [this]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager") help page for disabling NM without uninstalling it.

---

### Post by futz on 2009-04-17
> **Black_Wolf_92 said:**
> Don't worry if you don't like it though, coz if you DON"T, simply UNINSTALL wicd with synaptic, whack in your LiveCd (make sure you enable it in repositries in synaptic) and find the network-manager-gnome in there, and you can re-install it from the LiveCD without an active internet connection
You don't have to uninstall it first as a separate step. When you go to reinstall NetworkManager, Synaptic automatically uninstalls Wicd for you (same as it automatically uninstalls NetworkManager for you when you when you install Wicd). There can be only one! :D

---

### Post by Black_Wolf_92 on 2009-04-17
ah ok, i wasn't aware of that, I remember someone telling me that it was safer to uninstall Wicd first, as the Network Manager script won't remove Wicd (coz its not the default application) but there must be some step to check if you HAVE a network manager full stop and removes that to avoid confliction. Lol gotta love ubuntu developers

---

### Post by futz on 2009-04-20
Was tinkering with it last night and now I think I may have been too hard on NetworkManager. I may have misunderstood how it works.

NetworkManager shows as being connected to both of my two wired connections and one of the three wireless connections simultaneously. I never believed that was possible before, but it really is connected to all of them. I tried pinging each of them - that works! I connected to each of the three routers in the browser - that works too! I tried the printer and it works (didn't before, but does now)! So maybe I was just trying to make it do something it doesn't do. It appears that it really IS connected to all three ports simultaneously and they all work.

I'm still not sure whether selecting different interfaces manually works or not, but I can now use my printer on the "cable" network while doing internet on the "DSL" network, so I don't think I care. Why it didn't work when I tried it earlier I do not know, but all seems good now. :D

It seems NetworkManager is smarter than I gave it credit for.

---

### Post by Iowan on 2009-04-20
Awhile back I was shown [this]("http://www.arachnoid.com/linux/NetworkManager/index.html") article on NM.

---


---
title: "How to access my Samba workgroup?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2011-01-05
Ok, I'm going more than a little nuts here...

Here's what's happening. I have one PC (morpheus) on which I've chosen to share a couple of folders in the home directory. The folders show the "Shared" icon in them and are chmod 777'd. I can access them by going to Dolphin -> Network -> Samba Shares -> Workgroup -> Morpheus -> Foldername ... but *only* on that same computer (Morheus). All my computers are running Kubuntu with KDE 4.5 and attached by ethernet.

If I try and go to Dolphin -> Network -> Samba Shares on *any* other computer, Dolphin just reports "Unable to find any workgroups in your local network. This might be cause by an enabled firewall." I've never set up a firewall on any of these computers. Do I need to open ports on my router just for this? Morpheus is set to DMZ mode on the router so it should accept *any* port request not assigned to another computer already.

I have a feeling that there's just something obvious I don't know, because in all my years of trying to get this to work on and off, I've never managed to find a decent *simple* CLI or GUI based tutorial or figure it out myself. The web just seems full of long threads of people having very specific problems unique to their situation trying to sort them out. I just want to share folders over a lan via KDE. I'm kind of stunned that there's nothing on Userbase to show how it's done. 


Any ideas anyone?

---

### Post by PatchesTheCaveman on 2011-01-06
If you want to completely disable any firewall you might have running to eliminate that as a possibility, go to KMenu/Kicker > Accessories > Konsole/Terminal and type the following in the black box that appears and press Enter:
```
sudo ufw disable
```

Then give it another try.  If that fixes it, we can try and help you open up your firewall just for SMB.  But I'm not sure what the GUI firewall editor for Kubuntu is these days.

---


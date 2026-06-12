---
title: "KNetworkManager/KWallet - Always Asks For PW..."
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-04
Every time I fire up Kubuntu, it asks for my password so my wireless can connect. This isn't the PW to the network, it's my user password.

How can I set it so it just - blam - connects each time without asking me?

---

### Post by MiniMe on 2009-12-07
I'm trying to figure out the same thing. I just installed Kubuntu 9.10 on my laptop to give KDE a try. I was running Ubuntu 9.04 before and got automatic wireless connection on startup working. I can't seem to find any guides on how to do it in KDE. Any help would be appreciated.

---

### Post by MiniMe on 2009-12-07
Just figured it out. Simply change your kwallet password to a blank one and you won't have to enter it.

---

### Post by Roasted on 2009-12-07
Where do I change the PW? :(

---

### Post by MiniMe on 2009-12-18
From what I recall you have to right click the wallet manager icon on the taskbar and select "change password". If you don't see the wallet icon on the taskbar then you have to go to system settings -> advanced -> KDE wallet and click "show in system tray" or something similar. I think I had to reboot to get it to show in the tray.

Hope it works for you, sorry if the instructions aren't exact. I can't remember all the details exactly and I'm not on my Kubuntu laptop at the moment to verify.

---

### Post by garryknight on 2009-12-18
There's a big drawback with this method. If someone gets physical access to your machine, they can run KWallet without a password and read all of the other passwords it has stored.

---

### Post by Roasted on 2009-12-19
> **garryknight said:**
> There's a big drawback with this method. If someone gets physical access to your machine, they can run KWallet without a password and read all of the other passwords it has stored.

Good tip, but since that's the only PW I have saved, we should be in good shape. Plus I'm religious about locking my system anytime I leave if - which I never leave a laptop sitting around at work to begin with for obvious reasons. :lolflag:

I think this will work for me, but I'll be aware of this counter reason behind it. Thanks for making me aware!

---

### Post by svetiev on 2009-12-19
I'm facing a similar problem my self.

I've successfully configured a Huawei k-3565 to work with Edubuntu 9.10, however the network settings manager keeps forgetting the password for my mobile broadband provider.

I also use a Wi-fi network at home and the keyring wallet has a passwd saved for it. But it has no password stored for the mobile broadband network so every time I wan't to connect to the mobile broadband I have to open network settings and reenter the passoword :((((

There is a catch: if i connect to the Wi-fi network first (thus asking me for my keyring passwd) than it has no problem rembering the passwd for the mobile boradband as well. But what's the point in that since I need to use the mobile broadband when my home Wi-fi is not available. In that case it doesn't ask for the keyring passwd and so the mobile broadband cannot load the passwd it has stored and it cannot connect. 

I hope I made my self clear :S so any ideas on how to fix this?

Edit: Disabeling the password in Seashore solved my problem too.

---

### Post by svetiev on 2009-12-22
> **svetiev said:**
> 
Edit: Disabeling the password in Seashore solved my problem too.

Actually it only worked for a short time and now it still doesn't work.

Does anybody know a good mobile broadband manager for Ubuntu?

---

### Post by garryknight on 2009-12-22
I use Vodafone Mobile Connect. It works with my Huawei E220 and your K3565 according to their webpage: [http://www.betavine.net/bvportal/resources/datacards/devices](http://www.betavine.net/bvportal/resources/datacards/devices)

It gives you a GUI dialog from which you can not only connect and disconnect but also send SMS texts.

---

### Post by chip616 on 2010-02-10
MiniMe:

> From what I recall you have to right click the wallet manager icon on the taskbar and select "change password"

Close....

LEFT click the KWallet icon in the system tray (Kicker).  This will open the KWallet window on the desktop.  THEN you right click the KWallet icon, and select 'change password'.  Clear the password box, and the confirmation box, and save it.  KDE will complain about a weak password, but ignore it.  In Kubuntu 8.04, the next time I booted, I was told that Knetworkmanager wanted to open KWallet, and it gave me 4 options.  I chose "allow always" (or similar), and I've had no problems with it since.

My thanks to you for leading me in the right direction.  I only use Kwallet for the Networkmanager, and it is a royal pain to constantly have to open it with a password every time I turn the machine on.  This eliminates that.

Much thanks.

Frank.

---

### Post by Ko$ on 2010-05-17
Maybe it`s already too late for topic starter, but you actually can just turn off the store of password by network manager only. In network manager just go to configurations and set store password NOT in wallet.. And you can use the wallet password further. You don`t need to blank it.

p.s. from google came here for this answer..

---


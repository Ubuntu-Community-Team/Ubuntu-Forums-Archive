---
title: "Help me with the &quot;Belkin Wireless G Desktop PCI Card&quot;"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by ko16736 on 2006-03-13
I bought this card before I got Ubuntu from a friend. I was running Windows 98 and he told me that Ubuntu would be much better and more up to date. So he gave me an install CD and I installed it on my computer. Everything was perfectly smooth until I noticed I hadn't installed the wireless card yet. So I go looking on the internet on another computer and find ndiswrapper. It tells me how to do a lot but I really need some help. Like step by step because this is driving me crazy.

Ok, The roblem was I didn't activate the wireless card. I actually did not even have to install the drivers or anything for it. It was beyond easy and a pitiful mistake on my part. Sorry for the waste of space. Hope no one is looking for help with this.

---

### Post by roachk71 on 2006-03-13
[LEFT]Hi ko,

It would be helpful if you were to tell us what version of the card you have installed; If it has an Atheros chipset you should be able to configure device ath0 in the System -> Administration -> Networking configuration panel.

If not, it probably has a Broadcom chipset, for which you will need at least the ndiswrapper-utils package, which is on the CDROM.

In the latter case, open the Synaptic Package Manager from the same menu and install that package. And once you've done that, look for the driver folder on the CD, and find BCM*.inf .

Remember where you found it for the next step. Open a terminal window, and type:

```

sudo ndiswrapper -i (path to the inf file)/BCM*.inf
{you'll be asked for your password}

sudo ndiswrapper -m (this sets up a link to start the driver at boot time, but that doesn't always work.)

modprobe ndiswrapper
(this will set up the driver right away, so you can set up the connection in the Network Manager.)

``` 
If the "sudo ndiswrapper -m" command doesn't work, you can manually add a startup reference in your /etc/modules file. Re-open your terminal and type:

```

sudo vi /etc/modules

``` 
Here's a sample of this file for comparison:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
ndiswrapper
piix
ide-core
ide-cd
ide-disk
ide-generic

``` 
It's important to add ndiswrapper early, so that the clock sync works correctly, otherwise it'll wait until you press Ctrl-C to stop it.

Now reboot once again.

If this doesn't help (and you have a direct LAN connection,) follow the two links at the top of my signature. Be sure to compile the kernel first, since you'll need the modules that provides.

The kernel will take between 45 minutes and three hours to build, but the effort and wait are worth it.

Oh! I nearly forgot: you'll have to press the Insert key once to get the VI editor to insert your text, and type Escape-:w to save the file. After this, use :q to exit.
[/LEFT]

---

### Post by ko16736 on 2006-03-13
"""It would be helpful if you were to tell us what version of the card you have installed; If it has an Atheros chipset you should be able to configure device ath0 in the System -> Administration -> Networking configuration panel.""



This is what I did and it started working immediatley. I am so sorry you took all that time typing all of that and your effort is amazing. The Ubuntu community is one of the greatest in the world and I shall now delete that nasty Windows partition.

Thansk again. And sorry again.

---

### Post by roachk71 on 2006-03-13
[LEFT]Ha, Ha!!!!

Just noticed your edit. Whoops! :mrgreen:

And BTW, I have a PC Card with the same type of chipset.

And no need to be sorry; Help is what many of us come here to do... 
[/LEFT]

---

### Post by co1dfus1on on 2008-01-13
Sorry, what do you mean when you say that you "activated the card" and got it working? I have the same card but some internet sites say it uses atheros and some say it uses broadcom. Iit's not working with ndiswrapper, and I have no idea how to configure madwifi.

---


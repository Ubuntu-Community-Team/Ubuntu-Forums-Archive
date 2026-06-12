---
title: "Acer aspire one wireless issue"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by halocog on 2009-06-19
My acer aspire one 8.9inch's wireless just refuses to work all of a sudden, and i have tried nidswrapper? and still just connects at random times for just a few minutes and quits, saying device not ready .

can anyone please help me?

---

### Post by Aearenda on 2009-06-19
The ath5k driver isn't as stable with heavy traffic as it could be yet, even on Jaunty with backports. I've seen it crash my router, and cause a kernel crash on my AA1. I use the current madwifi-hal driver (ath_pci) instead.

The [instructions in the wiki]("https://help.ubuntu.com/community/AspireOne") for setting up madwifi on Intrepid still work for Jaunty.

---

### Post by halocog on 2009-06-19
thanks, i will try it and post what happens asap

---

### Post by halocog on 2009-06-19
i need some help making the script to restart the interface thats shown in the wiki page, i have no idea how to do that

---

### Post by Aearenda on 2009-06-19
Sure, here's how to do it:

1. Press ALT and F2 and paste this command into the box that comes up, finishing with <ENTER>:```
gksudo gedit /etc/pm/sleep.d/00wireless
```
Enter your password when requested.

2. Copy the entire contents from the wiki repeated below, and paste it in to Gedit:
```
#
# Restart WiFi interface after suspension
#

case "$1" in
        resume|thaw)
                /sbin/ifconfig wifi0 down
                /sbin/ifconfig wifi0 up
        ;;
        *)
        ;;
esac

exit $?
```

3. Hit 'Save' in Gedit, and then close Gedit.

4. Start a terminal from Applications->Accessories->Terminal, and paste this command in, followed by <ENTER>
```
sudo chmod u+x /etc/pm/sleep.d/00wireless
```
Then close the terminal (<CTRL> and D, or use the mouse).

The rest of the instructions starting 'It may be necessary to remove the ath_pci module when suspending' are not needed on Jaunty.

Good luck!

---

### Post by Aearenda on 2009-06-19
By the way, the wireless LED will not work using ath_pci until you do this (also from the wiki):

1. Press ALT and F2, and paste in the following command:```
gksudo gedit /etc/sysctl.conf
```

2. Carefully move to the very end of the file, and then add these two lines:
```
dev.wifi0.ledpin=3
dev.wifi0.softled=1

```

3. Save the file and close Gedit.

4. Reboot, or start a terminal as before and do ```
sudo sysctl -p
```This will take effect immediately.

---

### Post by halocog on 2009-06-19
thank you so much, you have been a huge help to me, if you need anything feel free to pm me

---

### Post by neu2buntu on 2009-06-19
what version of ubuntu are you running? i have had full wifi success on 8.10 and 9.04 on my aa1!

---

### Post by halocog on 2009-06-19
> **neu2buntu said:**
> what version of ubuntu are you running? i have had full wifi success on 8.10 and 9.04 on my aa1!

jaunty/netbook remix

---

### Post by Aearenda on 2009-06-20
I think there is a combination of ath5k and particular routers and protocols that fails under load. Some of us hit it, some don't.

---

### Post by carcar1 on 2009-06-20
For some reason Fedora 11 released some new driver for this and some one who's good with code might want to check it out and copy it.  Is that stealing?  Oh well, the atheros ar5007eg in my laptop is so slowwwwww with ubuntu.  fedora 11 made it sooooo stable.  I am not promoting fedora, thats like the only good thing about fedora.

---

### Post by Peacepunk on 2009-06-20
> **Aearenda said:**
> The ath5k driver isn't as stable with heavy traffic as it could be yet, even on Jaunty with backports. **I've seen it crash my router**, and cause a kernel crash on my AA1. I use the current madwifi-hal driver (ath_pci) instead.

The [instructions in the wiki]("https://help.ubuntu.com/community/AspireOne") for setting up madwifi on Intrepid still work for Jaunty.

As a very dumb piece of non-advice: I threw my BEFW11 router through the window, and bought a WRT54G2 instead. 'Must say my wireless life is without router crashes since then... Even MacBooks used to crash it :D

A "serious" piece is to build yourself a fixed IP connection, it does stabilise things slightly, and it's quicker to reconnect.

[Doesn't mean I have no issues, but the Aspire One at least can keep a connection while updating itself overnight. 904UNR, "standard" ath5k driver; issues weren't as accurate with Linpus & Fedora10 on the old router]

Cheers

---

### Post by Aearenda on 2009-06-20
> **carcar1 said:**
> For some reason Fedora 11 released some new driver for this and some one who's good with code might want to check it out and copy it.  Is that stealing?

All the distros like Fedora and Ubuntu get their drivers from the same source, it's just the version that is used in a particular release that varies. Ubuntu has a newer version of ath5k in linux-backports-modules-jaunty, and this was updated recently as well, but it still didn't fix my ath5k/heavy-load/router problem.

> **Peacepunk said:**
> I threw my BEFW11 router through the window, and bought a WRT54G2 instead.

Amusingly, I swapped the wireless router for a while so that I could use ath5k and stop having to recompile madwifi on every new kernel version, but a regular visitor with a Windows Vista laptop that has an Intel 3945 wireless interface had trouble with the new one - Vista obstinately refused to recognise the network! So I put the old router back. Luckily I hadn't 'thrown it through the window' :-)

---

### Post by carcar1 on 2009-06-21
How could ubuntu's driver be newer?  Fedora up untill 11 didnt support this card at all.  Now they support it in 11 and it works much better then ubuntu.  And fedora just came out so they are newer.

---

### Post by kevdog on 2009-06-21
Did you guys try compiling the latest ath5k driver from source?  Also there are interactions between the specific driver version and the specific kernel version at play here.  Some combinations work better than others.  Newer is not always better.

---

### Post by Aearenda on 2009-06-21
> **carcar1 said:**
> How could ubuntu's driver be newer?Poor language on my part. I meant that the backports driver is 'newer that the original Jaunty driver', not 'newer than the Fedora'.

kevdog, I haven't tried compiling the ath5k from source, as I haven't come across instructions for that, and until last week I was working on a major essay so I had no time to work it out. The madwifi setup is well known so I could do that quickly. 

I'd be happy to try compiling and testing ath5k now, but I suspect the simplest thing to do is a test installation of karmic to see if it is already fixed in there.

---


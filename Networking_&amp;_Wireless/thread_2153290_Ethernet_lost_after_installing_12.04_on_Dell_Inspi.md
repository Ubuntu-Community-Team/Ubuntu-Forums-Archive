---
title: "Ethernet lost after installing 12.04 on Dell Inspiron 6400"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by DavidBrown2012 on 2013-06-10
I have an oldish Dell Inspiron 6400 laptop. I decided to re-install Ubuntu 12.04 (the previous install was broken - I think I accidentally pressed the MediaDirect button, which tends to wipe things out). I used a Ubuntu 12.04 live CD, with an ethernet connection for downloading during the install. All appeared to go OK, and the ethernet connection was working until I restarted the system, after which - no ethernet.

I've tried various things, after a lot of googling, including for example:

$ lspci | grep Broadcom
03:00.0 Ethernet Controller Broadcom Corporation BCM4401-B0 100Base-Tx (rev 02)
0b:00.0 Network Controller Broadcom Corporation BCM4311 802.11b/g (rev 01)

$ sudo lshw -C network
...
  * - network UNCLAIMED
           description: Ethernet controller
           product: BCM4401-B0 100Base-Tx
           vendor: Broadcom Corporation
...

ifconfig -a gives info about loopback (lo) but that's all - nothing about eth0 or eth1. I can't run hwinfo because it's not installed by default and I can't install it without a connection.

$ more /etc/network/interfaces
auto lo
iface lo inet loopback

(i.e. nothing about ethX)

(I don't think this last one is relevant - except that it confirms the ifconfig result - as I get the same output on the machine I'm entering this on, which is using ethernet on the same network. I only included it because it was suggested as a diagnostic on one of the many google sites I've looked at.)

The really strange thing is that the ethernet connection worked absolutely OK (and showed up in the network manager GUI) during the install, but seems to have disappeared almost without trace after rebooting. One suggestion (based on the 'network UNCLAIMED' response to lshw) was a missing driver, but this seems unlikely as the installation went without a hitch. It seems more likely that a setting is lost on reboot, but my knowledge of Linux/Ubuntu internals is limited and I've no idea what to check!

Can anyone help?

---

### Post by Hadaka on 2013-06-10
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then with your now working wired connection do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
report back any error
thanks.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by DavidBrown2012 on 2013-06-10
It worked - very many thanks!

I was a bit concerned by the fact that initramfs never returned. There was virtually no CPU activity so in the end although I couldn't break out of it and the system complained that there was still a running process I closed the terminal anyway. There were some strange messages during reboot, but after the firmware install, the modprobe (which I understand adds the driver to the kernel) and a further reboot to check, everything seems to be fine.

If you have the time and inclination to explain why this was necessary  it would be good, but I'm grateful for your help anyway so don't bother if you're too busy!

Thanks also to ahallubuntu - that info will probably be useful some time!

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by Hadaka on 2013-06-10
Hi, despite some issues,mostly realating to loading the incorrect driver
there is nothing wrong with Broadcom drivers, as is evident by the fact
there are millions of them out there doing exactly what they were designed
to do. Your problem was caused by loading the Broadcom-kernel-source
driver. That dirver blacklists, the ssb module and the b43 module.
your wireless card requires the the ssb and b43 and your wired connection
B44 also uses the ssb module. so loading the incorrect driver killed both wireless
and wired. Once the broadcom-kernel-source diver was removed the wired worked
then loading the linux-firmware-nonfree driver..for your 4311 wireless loaded the 
b43 and ssb module, there by making it function correcty.
glad its working !!

---

### Post by varunendra on 2013-06-10
> **ahallubuntu said:**
> and it's quite common to need to tweak them after an installation..

With due respect to your knowledge, I must completely disagree with the above statement.

Apart from loading a correct driver, broadcom drivers have never required any tweaking in my personal experience. When it works (which is almost always leave a few exceptional cases), it just works. Yes it does not always work out of box due to the proprietary firmware issue, but that has never been a big deal. It is as easy as downloading a package and double-click > install. I suspect even windows needs more work than that.

And the reason why even that much is (sometimes) needed is very well explained here (in reasonably short text :)) : [https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

The only time when they need some extra work is when the device in question is very new and proper support for it could not have been included yet. And broadcom, just like intel, has been quite active in providing support to its linux drivers for its cards.

The intel cards, on the other hand, do need some tweaking often to provide their optimal performance. And that requirement exists for both its new and old drivers/cards. Some of its older cards were even totally ignored by intel itself so their drivers/firmwares never really got fixed (iwl4964, iwl3945 come to mind), and whoever have them have to either switch to another card or compromise with buggy performance.

I can't say whether the overall performance has been better in broadcom or intel cards, but with the personal experience and the lot of searches I have done so far, I can confidently say that dealing with broadcom drivers has been relatively easier.

---

### Post by DavidBrown2012 on 2013-06-10
At least my problem has given rise to some interesting debate! There are some interesting comments and links in there, and when I get time I'll follow them up. Thanks again for the explanations.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by varunendra on 2013-06-10
> **ahallubuntu said:**
> That was my POINT: why should you even need to load a driver?  This confuses many new users who expect their laptops to work automatically after installing Ubuntu.
Working out-of-box is not necessarily the best thing about a driver if it can't work nicely afterwards.
And requiring a driver for a non-generic device like wireless in not a new concept. In fact, before Windows 7, even generic ethernet adapters needed external drivers on windows (where most of the 'innocent' users are) and still do if the product is released 'After' the release of a particular OS version. So they are used to that concept, just not used to the different terminology that non-ms OSes use.

It never surprised me (or anybody I personally know). On the contrary, what surprises most new users is the fact that Linux doesn't need external drivers for most of their hardware (provided the machine is not ultra-modern). If someone new to Linux expects all their hardware to work out-of-box with Linux, they are just being over-optimistic, or someone has given them the false impression that Linux is the name of Harry-Potter's magic wand. :)

So.. I believe those who are new to Linux would be used to the concept of installing of driver, just need a little search on how to do it for their card on Linux.

Those who are not new to Linux - know how to get it right.

And for both the new users, and the relatively experienced ones - searching a solution for broadcom chip, if and when required, is one of the quickest searches with least confusing results (most often the threads end within first page, with a uniform, almost fixed set of steps involved).

Whereas searching for a solution for optimizing performance on other cards more than often yields results that confuse even troubleshooters like myself (okay, this one didn't work, that one failed too, what to try now...??). Different people, different fixes.

The fact that there are more broadcom threads on the forums doesn't mean it is more problematic. It is because most of these threads are started by users who are absolutely new to Linux, and don't even know how to search a solution for their card. Fixing is almost always a two step thing - either get a wired connection and install the suggested driver, or remove that one and install (actually just copy) the firmware. Reboot and celebrate.

Once it is working (which almost always requires just one of the same two fixes above), we never see another problem thread about it. That's what I call really problem-free.

While with many other cards (including many intel ones) that work out-of-box, we fix one issue somehow in 3-4 pages, then after an update suddenly the same problem or a different one re-occurs. I don't see that working-out-of box much useful.

As for intel cards being problem-free, just take a look at these threads I recently dealt with (and gave up in the last) : 
[http://ubuntuforums.org/showthread.php?t=2143995](http://ubuntuforums.org/showthread.php?t=2143995)
[http://ubuntuforums.org/showthread.php?t=2150398](http://ubuntuforums.org/showthread.php?t=2150398)

I don't mean that "because I gave up, it was a huge problem". But yes, finding a solution was hard for me at least, and I did a lot of search - only to find there were many like me who failed to find a solution. The threads are for the older intel cards, but also note the OPs comment in post #18 in the second thread, where he stated that he also had bugs with the newer 5100, and 6200 cards.

Does it prove that those cards are crap? I don't think so. It only proves that different users may have different experience with the same hardware, especially when it is something like a wireless card that depends upon too many factors.

The fact that one piece of hardware is working better for you doesn't necessarily make all others useless. And as for broadcom chips, I have seen least no. of issues once they are working (which again, is most often a piece of cake with a little search on the net or the forums).

That's my personal experience. And that does not make me believe or tell others that broadcom is the best or a particular other one is the worst.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by varunendra on 2013-06-10
> **ahallubuntu said:**
> Many solutions involve typing terminal commands; one of the criticisms of Linux on the Desktop still is that you have to be an expert with the terminal just to use the operating system.  We should strive to get away from that impression.
Must agree with that.

However, I don't see it as a downside. We do need to 'Create' a new impression, but that does not need to take away the CLI ways. While being able to provide GUI ways to do things is great and desirable (and you must agree too that a lot of progress has been made in this area), the terminal is the real power of all Unix-based OSes.

Personally I prefer the terminal commands (while most often there are GUI alternatives) simply because it is short, quick and almost always uniform across various distros. While the GUI ways keep changing dramatically across different DEs and it is difficult (if not impossible) to keep up with all of them.

And as for broadcoms, we can always tell users to open synaptic/USC > search for broadcom > click install (or mark > apply in synaptic). Or, if it is the 'other' variant, download "linux-firmware-nonfree" (a single package with no dependencies) > double-click to install (or do that from USC/synaptic as well).

So both the fixes never really need CLI. It's just the way we prefer just to save a few extra lines and to avoid confusion of different GUIs.

It is good if we get the 'choice' of GUI for everything, but if in the process of trying to become the deceptive and delusional term "User-Friendly", Linux lost its true power, I'd find myself looking for yet another alternative. (I know this was slightly off-track, well..)

> I still contend that Broadcom wireless issues on the forums are far more prominent and frustrating for users here than for any other brand of wireless cards.    (One of the three "Sticky" threads in this forum is a long thread with various solutions for Broadcom wireless cards.)
..And I wouldn't even try to change your or anyone else's opinion about that. Like I said, different people, different experience.

But maybe the reason why there are no other stickies is only because the developers, us, the mods/admins know 'exactly' what problems are going to arise, and 'exactly' what their solutions will be. Meaning everything is predictable and easy enough to write once and trust that it'll work for everyone.

The lack of stickies about others may instead be an evidence or something 'otherwise' ;)

The length of the stickies is a misleading thing. Most of their parts are just about teaching people the basic terminology, basic sanity check and how to identify their card, rather that actual fix. The actual fix is just as simple as I stated above. There are only three cases -

[LIST=1]
[*]The card will work out-of box (brcmsmac driver will deal with it, no intervention needed)
[*]It will need the firmware file (for b43 driver, download > double-click > done)
[*]It will need the proprietary wl driver (click "Use this driver" in Additional Driver dialogue > done).
[/LIST]

I don't see these fixes needing more than two-three very short posts, IF we strip down the "how to find your way around in Linux" part of the stickies. If we go into complexities, that's where a "General Guide" or manual fails miserably in achieving its goal. So if that makes it confusing and/or frustrating, it is the failure of the guide, not the device or driver itself.

But yes, if a device does not work out-of-box (which is not always as stated above), it IS a problem. You see it as a big one while I don't. I see it as a problem too, but not so big. For me, if I am capable enough to download an ISO and install it on my system, then digging up a fix as easy as this one shouldn't be a thing of least concern if it proves rock-solid afterwards. (oh, maybe I spoke too much about its reliability, I take the term "rock-solid" back, just to be safe.. :P)

In the last, we'd still be getting issue threads regarding both chips (and others), suggesting more or less the same fixes over and over again, and pulling out our hair in the process until we get completely bald. :-\"

I'll shut up now.
Cheers !!

---


---
title: "Wireless dropping connection"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by seattle vic on 2009-12-03
I've been running 9.10 since it came out and am up to date on all upgrades.  I'm using net-manger and the wireless as been running file up until a couple days ago, but now loses connection after a couple hours and I can't reconnect without restarting the laptop.  I even try to restart it using init.d, but no luck.

I'm using a (fairly) new Asus laptop with intel hardware.  I have a dual boot situation, and by going over to win 7 it has no problems.

Has anybody seen this recently?

---

### Post by slumbergod on 2009-12-03
This is quite common with Karmic it seems.

I found when I get booted off my wireless network I had to reboot too. Then someone suggested reloading the wireless kernel modules then reconnecting. Now it works everytime.

I don't know what Intel hardware you have but mine is 3945 and I find issuing these commands sorts it out for me:
# modprobe iwl3945
# modprobe iwlcore
# modprobe mac80211
then again in the reverse order to reload them.

You can also try wicd instead of network-manager. I switched to it a few releases back and prefer it. Some others have had better luck with it too.

---

### Post by coffeecat on 2009-12-03
> **seattle vic said:**
> I'm using a (fairly) new Asus laptop with intel hardware.

Intel hardware does not necessarily mean an Intel wireless chipset - although it might. Without knowing your chipset, any advice would be speculative. Open a terminal and post the output of:

```
sudo lshw -C network
```

---

### Post by coffeecat on 2009-12-03
> **slumbergod said:**
> This is quite common with Karmic it seems.

Not with Karmic in this household and **four** different wireless chipsets. All quite strong and steady. Let's determine the OP's wireless chipset before making generalisations.

---

### Post by slumbergod on 2009-12-03
Well, judging by the fact that almost everyday someone is posting in these forums with wireless issues, i would beg to differ. You might have good luck because you bought hardware you knew would work. or perhaps you are just very lucky. Some of us have found Karmic to be a dog. So I say it is common.

---

### Post by seattle vic on 2009-12-04
lshw shows intel 5100.

---

### Post by seattle vic on 2009-12-06
Well, it is still giving me problems.  9.04 seemed to be more stable, in fact as good as a windows OS, but this one stll disconnects after serveral hours.  This morning, I had to reset net-manager; yesterday I had to restart the machine.

Anyway, running lshw shows the wireless is Inel 5100, which I take to be a very common hardware chipset anymore.

Anybody else having similar problems with this chipset?

---

### Post by AngelKnight on 2009-12-12
I also am having problems with an Asus laptop (about a year old). My specs are as follow:
* Asus M70V
* 4GB RAM
* Intel Core 2 Duo
* AR928X Wireless Network Adapter
* Dual boot: Windows Vista & Ubuntu 9.10

I have Vista on this machine, and the wireless works fine with that, but under 9.10 the connection periodically drops. I can re-connect with it using the network manager, but this is becoming annoying, especially as I stream videos from my main file server (also running Ubuntu 9.10 on a hard wire, which works fine).

I will look into the wicd solution to see if that helps at all.

Any other ideas?

Thanks in advance.

P.S.: Don't know if it helps in this discussion at all, but I attempted to install Ubuntu Lucid Alpha on this machine, but it wouldn't get any further than scanning the hard drive for partitions, at which point it started flashing the screen and locked up tighter than a drum. I'm sure it's not related to the wireless, but extra information can't hurt, right? :)

Edit: Just installed wicd, and things seem a little healthier. Will have to run it this way for a while to make sure all is OK, though, in the long run. Will update later.

Edit 2: Well, went out to dinner, and just got back. Network went out again, although according to wicd, all was well, but I couldn't get anywhere on either my local network nor on the Internet. Double checked a couple logs, and then all of a sudden, it all came back. No indication as to WHY it went out, but it did. So, wicd is behaving better, but still having troubles. Hmm.... here's a thought: I wonder if there's a power setting where it turns off the wireless adapter when not in use and it isn't coming back on when I become active again.... Didn't see a setting for that in the power settings console, but will have another look.

Edit 3: Further information again.... It is still dying, even while I'm actively using the connection. Disconnecting and re-connecting only sometimes fixes it. :( Nothing on the power settings allows me to change that, but now that I'm seeing it die without going idle, I am doubting that is the issue.

---

### Post by usererror on 2009-12-16
There is definitely a bug.  Check out this bug report.  Does it sound like your issue?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432)

---

### Post by spanky1023 on 2009-12-25
> **usererror said:**
> There is definitely a bug.  Check out this bug report.  Does it sound like your issue?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432)

im having pretty much the same issue, and that bug report sounds like my problem.

just switched to 9.10 from 9.04 and now my wireless connection keeps dropping.  i just switched to Wicd, and though it is better, it still drops the signal, only not as often. 

i never had a problem with 9.04 and nor do i have a problem with the connection with Win 7. 

whats the scoop?

---

### Post by spanky1023 on 2010-01-01
bump ?

---

### Post by arrancaru on 2010-01-04
Same problem here, using a ralink chip and rt73usb module. Connection drops every 2~5 seconds, using wicd and setting automatic reconnect is possible to surf the net, but any direct download doesn't complete. Happens too in jaunty.

---

### Post by spanky1023 on 2010-01-04
quick update but no solution.

i switched to Wicd about 2 weeks ago, and it is better, but still having issues.  it will work fine until my laptop goes to sleep, or is suspended.  once its put into suspend or put to sleep, i must restart the laptop in order to connect Wicd again.  

Haha, so as long as im actually using the laptop, its working great!  
bummer though once i loose internet connection, i restart again and use windows 7 since i dont seem to have a problem with that. 

hopefully there will be a fix for this bug soon!

---

### Post by spearfish on 2010-01-05
> **slumbergod said:**
> Well, judging by the fact that almost everyday someone is posting in these forums with wireless issues, i would beg to differ. You might have good luck because you bought hardware you knew would work. or perhaps you are just very lucky. Some of us have found Karmic to be a dog. So I say it is common.

No kidding.  It really is a dog.  I've just installed 9.10 Notebook on my brand new Acer Aspire One and I have been fighting with it ever since.  Also, the *regular* version of 9.10 just locked up when I tried to install it.  The notebook version was the only thing that would install, and the network card has been super buggy.  Don't these things get tested before release? :confused:

---

### Post by Ibidem on 2010-01-06
Haven't tried 9.10 on my Aspire One--everything I read implied that it was asking for trouble.  I'm currently running Kuki Linux (a Jaunty remix for the AA1) & XP as main OS's.
Kuki Linux works fine.
Also, I'm running Lucid (ALPHA) in VirtualBox for a test run...That's where I'm posting from.  Works, except 
1) GRUB 2 screws up every boot
2) I ran startx as root...
3) There's a memory leak--no, that's a broken main-- in there; a base install should not be using 250+ MB after no significant commands!
So, try Jaunty instead of Karmic.

---

### Post by arrancaru on 2010-01-06
I give up, wpa with rt73usb just don't work well. Maybe the good part of all this suffering is discovering how windows 7 actually is good. I feel so good in using a system that JUST WORKS!!

---

### Post by zaphod777 on 2010-01-07
Are you downloading torrents when the connection drops? Please comment on this bug we have filed so we can get more attention.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/374650](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/374650)

---

### Post by Ibidem on 2010-01-08
Try ndiswrapper, then.

---

### Post by bill_p on 2010-01-11
I guess this is a "me too", sort of. Using Karmic, I have a RealTek 8192E, using ndiswrapper, tried both network manager and wicd, both were not reliable making a WPA connection, config'ed wpa supplicant and network/interfaces manually and connects 100% of time on boot.

But...resuming from suspend wireless doesn't reconnect without init.d restart of network. That works, sometimes immediately, sometimes after up to 5 minutes. Would be nice to have it automatically connection on resume.

Also, transferring some amount of data (over say 5 mb) *to* an SMB share causes the connection to drop and I cannot get it back without a reboot. From an SMB share I can transfer gb without a problem.   

Any thoughts?

---


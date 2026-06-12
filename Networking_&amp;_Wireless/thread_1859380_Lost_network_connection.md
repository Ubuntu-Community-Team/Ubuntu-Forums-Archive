---
title: "Lost network connection"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by sideburns on 2011-10-13
My sister uses Ubuntu, and suddenly she can't reach anything outside the LAN.  I know she's not completely off-line because she can reach the modem by IP.  Checking the Network icon on her top panel, her connection's idle, and clicking on Configure shows no connections listed.  I know we're on-line, because I'm posting this from another computer on the LAN.  How do I get her re-configured, preferably without rebooting as we both keep our boxes running 24/7 as much as possible.  (I have the appropriate DNS numbers to put in, so that's not an issue.)

---

### Post by sideburns on 2011-10-14
More information.  We finally broke down and did a complete shutdown/restart, with no effect.  After a little playing around with Network Control, I tried adding a new wired connection.  I configured it manually, because it needs a static IP on the LAN to allow port forwarding, so I set it up with IP, Netmask, Gateway and DNS.  After several tries, it allowed me to click Apply, but it didn't take.  On the next try, it finally asked for a password, but the connection didn't show up and it still can't resolve DNS.  What do I need to do to rebuild her connection without reinstalling everything?

I'm a computer geek, with ample Linux experience, but I run Fedora, with XFCE, and I'm not familiar enough with the Ubuntu configuration programs to work this out on my own.  I don't need baby steps, but I do need, badly, a pointer in the Right Direction.

---

### Post by Nutria on 2011-10-14
Wired or wireless?

Can she ping and log into the router?

---

### Post by sideburns on 2011-10-14
The router's password protected, and I've not bothered to set her up on it.  As I wrote in the first post, she can reach the modem by IP, because its main page isn't protected.  As the modem is on the other side of the router, trying to reach the router seems a tad redundant.

The router is wired only and her desktop doesn't have WiFi capability.  Good question, though.

She not only doesn't have an DNS numbers, her system currently won't let me add them so she can't possibly reach anything except by IP address and that's what I need to correct.  (See my second post for details.)

I spent almost eight years doing ISP tech support and was considered a specialist in LAN set up and troubleshooting.  I know how find out what needs to be done, but in this case I'm not familiar enough with the software to beat it into submission.

---

### Post by Nutria on 2011-10-14
Another question: can she ping any external IP addresses?

---

### Post by Nutria on 2011-10-14
> **sideburns said:**
> She not only doesn't have an DNS numbers, her system currently won't let me add them so she can't possibly reach anything except by IP address and that's what I need to correct.  (See my second post for details.)

Before it failed, did she use dhcp?

> I spent almost eight years doing ISP tech support and was considered a specialist in LAN set up and troubleshooting.  I know how find out what needs to be done, but in this case I'm not familiar enough with the software to beat it into submission.

Network Mangler is a Red Hat abomination, and XFCE uses it (on Ubuntu, I think).

Anything in the log files?

---

### Post by sideburns on 2011-10-14
Good questions.  Yes, she can ping the outside world by IP.  No, she didn't use DHCP.  I had her set up with a static IP and manual DNS so that I can forward a port to her box for ssh.  I agree with you about Netwok Mangler[1], but it's not relevant here because she's not using Xubuntu.  (I only use it on my laptop, because network doesn't seem to handle WiFi correctly, but again, that's not part of the issue here.)

[1]Or should I be referring to Notwork Mangler?

---

### Post by gnush on 2011-10-14
Is she using a wireless or wired network? I'm going to assume she's using a wirelss network.

```
iwconfig wlan0
```What does iwconfig say about the network interface?

```
# wpa_passphrase essid "passphrase"
# wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf &
# dhcpcd wlan0
```If you use a static IP, just skip the dhcpcd command and enter the relevant information.
I'm not sure if Ubuntu comes with wpa_supplicant by default, but does that work? You might have to use ip link to put up the wireless interface. If you use WEP or non-encryption just use iwconfig.


If she can ping external servers it seems that ICMP packets are functional, does she have a misconfigured firewall running?

---

### Post by Nutria on 2011-10-14
> **sideburns said:**
> Good questions.  Yes, she can ping the outside world by IP.  No, she didn't use DHCP.  I had her set up with a static IP and manual DNS so that I can forward a port to her box for ssh.  I agree with you about Netwok Mangler[1], but it's not relevant here because she's not using Xubuntu.  (I only use it on my laptop, because network doesn't seem to handle WiFi correctly, but again, that's not part of the issue here.)

Ubuntu uses NM even for static addresses.

I found nmcli while researching your question.  This is what it shows for my box using static addressing sitting behind a router:

```
$ nmcli dev list
GENERAL.DEVICE:                 eth0
GENERAL.TYPE:                   802-3-ethernet
GENERAL.DRIVER:                 r8169
GENERAL.HWADDR:                 00:24:1D:27:C0:FF
GENERAL.STATE:                  connected
CAPABILITIES.CARRIER-DETECT:    yes
CAPABILITIES.SPEED:             100 Mb/s
WIRED-PROPERTIES.CARRIER:       on
IP4-SETTINGS.ADDRESS:           192.168.1.10
IP4-SETTINGS.PREFIX:            24 (255.255.255.0)
IP4-SETTINGS.GATEWAY:           192.168.1.251
IP4-DNS1.DNS:                   xx.yy.zz.aa
IP4-DNS2.DNS:                   bb.cc.dd.ee
IP4-DNS3.DNS:                   ff.gg.hh.ii
```

---

### Post by sideburns on 2011-10-14
Your question was already asked and answered, gnush, in my second post, and your assumption is dead wrong.  Thank you, however, for playing.

I tried nmcli and got this in response:

bash: nmcli command not found.

If you can point me to a source for it, I can download it on this box and transfer it by sneakernet.

---

### Post by gnush on 2011-10-14
> **sideburns said:**
> Your question was already asked and answered, gnush, in my second post, and your assumption is dead wrong.  Thank you, however, for playing.


Sorry, I should've payed more attention to the rest of the thread. Do you know if she has a misconfigured firewall running, then? Since she seems to be able to send ICMP packets to external servers.

---

### Post by Nutria on 2011-10-14
> **sideburns said:**
> I tried nmcli and got this in response:

bash: nmcli command not found.

In Ubuntu, it's in package network-manager which should already be installed.

---

### Post by sideburns on 2011-10-14
No, gnush, she doesn't have a misconfigured firewall, and if she did, it wouldn't matter.  The state of her firewall isn't relevant because her network connection won't accept DNS entries so she can't resolve machine names to IP addresses to connect to them.

While waiting for responses, I tried configuring her connection (eth1) again.  I was able to give it a static IP, netmask, gateway and a pair of DNS addresses and it even allowed me to click Apply.  Wireless connection 1 showed up in the list, but nothing changed.  I went back in, clicked on the checkbox to make it available to all users (which had been grayed out before) and clicked Apply.  It asked for her password and I gave it.  The connection vanished.

---

### Post by Nutria on 2011-10-14
> **sideburns said:**
> The connection vanished.

Anything in any log files?

---

### Post by sideburns on 2011-10-14
I went to /var/log and tried this:

sudo 'cat messages | grep eth1'

but was told that it couldn't find grep.  I had to copy it to a new file, chmod it (with sudo) to make it world-readable and try again as a regular user.

This showed me that some time yesterday, eth0 was renamed to eth1 and that the link was up.  It also showed the same thing happening again when we rebooted.  Nothing else in that file.  What other logs do you suggest?

---

### Post by Nutria on 2011-10-14
> **sideburns said:**
> I went to /var/log and tried this:

sudo 'cat messages | grep eth1'

but was told that it couldn't find grep.  I had to copy it to a new file, chmod it (with sudo) to make it world-readable and try again as a regular user.

I thought you were a power user...

```
$ sudo cat /var/log/messages | grep eth1
```


> This showed me that some time yesterday, eth0 was renamed to eth1 and that the link was up.  It also showed the same thing happening again when we rebooted.  Nothing else in that file.  What other logs do you suggest?

The "suddenly she can't reach anything" mentioned in your OP... is that the yesterday when eth0 was renamed to eth1.

And, now that you're on her machine, you can run nmcli.

---

### Post by sideburns on 2011-10-14
I am a power user.  I'm also lazy enough to put myself in the right directory so that I don't have to keep typing the complete path over and over again.

And, as far as running nmcli, no I can't because it's not installed on her machine.  I can walk across our condo from my machine to hers as needed, because we share living quarters, but if I could be responding to you from her box, I wouldn't need to.

I'm not sure just when her box dropped off the net, but it was mid-afternoon.  Checking, the message about renaming the interface has a time stamp of 23:22, seven or eight hours later.

---

### Post by Nutria on 2011-10-14
> I can't because it's not installed on her machine

NM is *always* installed in Ubuntu.  Plz ssh into her machine and type in:
```
$ apt-cache policy network-manager
network-manager:
  Installed: 0.8.1+git.20100810t184654.ab580f4-0ubuntu2
  Candidate: 0.8.1+git.20100810t184654.ab580f4-0ubuntu2
  Version table:
 *** 0.8.1+git.20100810t184654.ab580f4-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages
        100 /var/lib/dpkg/status
```

The only possible reasons that it wouldn't be there is that you manually deinstalled it or she's running an Ubuntu prior to 10.10 (maybe earlier).

```
$ dpkg -L network-manager | grep nmcli
/usr/share/man/man1/nmcli.1.gz
/usr/bin/nmcli
```

---

### Post by sideburns on 2011-10-15
Sigh!  I should have thought of ssh sooner.  Thanx.

Your first command returns this:

network-manager:
  Installed: 0.8-0ubuntu3.2
  Candidate: : 0.8-0ubuntu3.2

I'm not going to try to copy out all of the version table, because PuTTY doesn't let me copy from it and paste into another window, but there are references to lucid-updates and lucid-security if that helps.  Your second command returns nothing.  And, as far as being an old version of Ubuntu, it's upgraded every time a new version of Ubuntu is released.

I remember, once, having a similar trouble on this computer, where something was apparently over-writing my DNS at boot.  Eventually it was tracked down to a config file that needed hand editing to put the proper numbers in so that they'd be present when networking came up.  I'll be looking at my own box to find where that was and see what's on her box.  Maybe that's where the trouble's hidden.

---

### Post by sideburns on 2011-10-15
More info: /etc/resolv.conf has the correct DNS numbers in it.  /etc/network/interfaces has this in it:

auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1

All of the numbers are correct.

---

### Post by Nutria on 2011-10-15
> **sideburns said:**
> Sigh!  I should have thought of ssh sooner.  Thanx.

Your first command returns this:

network-manager:
  Installed: 0.8-0ubuntu3.2
  Candidate: : 0.8-0ubuntu3.2

Maverick 10.10 has n-m 0.8.1

> I'm not going to try to copy out all of the version table, because PuTTY doesn't let me copy from it and paste into another window, but there are references to lucid-updates and lucid-security if that helps.  Your second command returns nothing.  And, as far as being an old version of Ubuntu, it's upgraded every time a new version of Ubuntu is released.

Lucid is 10.04LTS which is 18 months old.  That's OK, since LTS means "Long Term Support".  It just means that you're sister is *not* upgrading to every release.  (Neither do I, since 11.04 compiz breaks with the nvidia binary driver and it wasn't fixed even after 6 months.)

> I remember, once, having a similar trouble on this computer, where something was apparently over-writing my DNS at boot.  Eventually it was tracked down to a config file that needed hand editing to put the proper numbers in so that they'd be present when networking came up.  I'll be looking at my own box to find where that was and see what's on her box.  Maybe that's where the trouble's hidden.

NM is fundamentally different from networking driven by /etc/network/interfaces.

---

### Post by sideburns on 2011-10-15
All I know about that is that every time she gets prompted for a distro upgrade she does it.  And, now that we know that, what do you suggest we do to get her back on line properly?

---

### Post by Nutria on 2011-10-15
> **sideburns said:**
> All I know about that is that every time she gets prompted for a distro upgrade she does it.

If she's on Lucid Lynx (which I think she is, because of the NM version she's running) then there's some factual disconnect.

System->"About Ubuntu" should tell you exactly what version she's running.

> And, now that we know that, what do you suggest we do to get her back on line properly?

To recap: it's DNS that's not working, right?

What if you disable networking (via right-clicking on the NM icon), make the changes and then reenable networking?

---

### Post by sideburns on 2011-10-15
Yes, she's still on Lucid because she decided to wait a bit after the upgrade to let things settle down, then forgot.

The icon on her panel is Network Monitor 2.28.0 and right-clicking on it doesn't give an option to shut down networking.  What program were you thinking of?  If she doesn't have what you're looking for, I can always download it here and move it across to her box.

---

### Post by Nutria on 2011-10-15
> **sideburns said:**
> Yes, she's still on Lucid because she decided to wait a bit after the upgrade to let things settle down, then forgot.

:)

> The icon on her panel is Network Monitor 2.28.0 and right-clicking on it doesn't give an option to shut down networking.  What program were you thinking of?  If she doesn't have what you're looking for, I can always download it here and move it across to her box.

Hmmm.  This is why I hate gooey configuration.

Anyway, here are two partial screen shots.  (I'm on Maverick 10.10, but NM is v0.8.4 because I upgraded using the ppa:network-manager/ppa.)

---

### Post by sideburns on 2011-10-15
OK, where do I get it?

---

### Post by Nutria on 2011-10-15
> **sideburns said:**
> OK, where do I get it?

Try:

```
$ apt-cache show network-manager-gnome
```

10.10 might be sufficiently different from 10.04 that I'll never be able to help you.... :(

(I just upgraded my wife/kids' PC from 10.04 to 10.10.  With PPAs, it's got current versions of all apps we care about.  You *might* want to admit defeat and have her try out Live DVD versions of Maverick 10.10 and Oneric 11.10 and see which one she likes better.)

---

### Post by sideburns on 2011-10-15
That got me a pointer to [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/) and I've downloaded NetworkManager 0.90 and the applet version 0.8.4 to my box.  I'll transfer them to hers, install them and see what happens.  Will report back when I'm done.

---

### Post by sideburns on 2011-10-16
I tried to install just the applet, but ./configure failed because NetworkManager wasn't installed.  I tried installing it, but it failed because, apparently, ./configure looked for a release version for every possible Linux distro except Ubuntu.  Can you give me a pointer to where I can get them in .deb form?  Either that or a cli way to shut down and restart networking that might actually be on her computer.

---

### Post by Nutria on 2011-10-16
> **sideburns said:**
> I tried to install just the applet, but ./configure failed because NetworkManager wasn't installed.  I tried installing it, but it failed because, apparently, ./configure looked for a release version for every possible Linux distro except Ubuntu.

I didn't think it would work...

> Can you give me a pointer to where I can get them in .deb form?  Either that or a cli way to shut down and restart networking that might actually be on her computer.

The network-manager PPA has what you need.

```
sudo add-apt-repository ppa:network-manager/ppa
```

But that won't work unless what I'm about to explain works.

IIRC, you said that you could ping dotted quad addresses, so it's all a DNS issue.  So, I'd try this:
```
$ sudo bash
# echo "74.125.73.106 www.google.com" >> /etc/hosts
# exit
$ ping www.google.com
```

If that works, then add the IP addresses of  every URL in /etc/apt/sources.list plus that of ppa.launchpad.net into /etc/hosts.

**Then** you can add the PPA, update and install the new NM.

Simple, huh... :)

---

### Post by sideburns on 2011-10-16
That is an incredibly bad idea.  I have no desire to poison her hosts file that way unless there's absolutely no choice, and there's always a better way than that, as long as I can reach the outside world through this box.  Checking, I was able to get to [http://ppa.launchpad.net/network-manager/](http://ppa.launchpad.net/network-manager/) in another browser tab, but not find what I need.  Is there some reason you can't give me a pointer to the file itself so that I can pick it up from here?  If nothing else, download it yourself and I'll give you my email address in a private message so you can send it to me.

---

### Post by Nutria on 2011-10-16
> **sideburns said:**
> That is an incredibly bad idea.  I have no desire to poison her hosts file

Poison?  You think this is some permanent alteration that can't be subsequently deleted?

The whole **purpose** of the hosts file is to hard code your own name resolutions ](*,)

> Checking, I was able to get to [http://ppa.launchpad.net/network-manager/](http://ppa.launchpad.net/network-manager/) in another browser tab, but not find what I need.  Is there some reason you can't give me a pointer to the file itself so that I can pick it up from here?

Amazingly, I was able to find it with a bit of diligence:
[http://ppa.launchpad.net/network-manager/ppa/ubuntu/pool/main/n/](http://ppa.launchpad.net/network-manager/ppa/ubuntu/pool/main/n/)

> If nothing else, download it yourself and I'll give you my email address in a private message so you can send it to me.

What's incredibly bad is you and your sister not using the same distro.

---

### Post by sideburns on 2011-10-16
Thank you for finally agreeing to give me the link I've been asking for.  Of course, as an Ubuntu user you knew what to look for and I don't.

As far as poisoning /etc/hosts, it's the principle of the thing: don't do twit things like that unless there's no choice, and there's almost always a better, safer and easier way to do it.  In this case, sneakernet's the sensible way to do it.

If my sister and I used the same distro, I'd not be here, because she'd be using Fedora.  However, I'm a computer geek, she's an Aunt Minnie and I don't want to subject her to something like Fedora because it takes more skill than she wants to have.  She's just a Windows refugee, so Ubuntu is Just Right for her.

---

### Post by Nutria on 2011-10-16
> **sideburns said:**
> Thank you for finally agreeing to give me the link I've been asking for.  Of course, as an Ubuntu user you knew what to look for and I don't.

I have no Magical Ubuntu Knowledge, and have never had to manually install packages from repositories.

Simply, from the URL which you said you couldn't find anything, I started poking around and actually found what you were looking for.

> As far as poisoning /etc/hosts, it's the principle of the thing: don't do twit things like that unless there's no choice, and there's almost always a better, safer and easier way to do it.

If I'm such a twit who recommends doing such poisonous things, why are you relying on me?

> If my sister and I used the same distro, I'd not be here, because she'd be using Fedora.  However, I'm a computer geek, she's an Aunt Minnie and I don't want to subject her to something like Fedora because it takes more skill than she wants to have.  She's just a Windows refugee, so Ubuntu is Just Right for her.

You can't configure and manage it remotely for her?  Even Ubuntu can for the most part be managed remotely.

---

### Post by uRock on 2011-10-16
> **Nutria said:**
> I have no Magical Ubuntu Knowledge, and have never had to manually install packages from repositories.

Simply, from the URL which you said you couldn't find anything, I started poking around and actually found what you were looking for.



If I'm such a twit who recommends doing such poisonous things, why are you relying on me?



You can't configure and manage it remotely for her?  Even Ubuntu can for the most part be managed remotely.

If you are not willing to help the user, then why are you posting? You are criticizing the user for not being able to spot a file that he/she kindly asked you to to point them to.

---

### Post by sideburns on 2011-10-16
I'm relying on you for the simple reason that I have no choice: you're the only person on this forum willing to respond.  And, 99.44% of the time, her box runs with no need for my help.  This is a very unusual circumstance because although I know why she's off-line, I don't know enough of the Ubuntu-specific configuration programs to resolve it myself.

I also know that when I gave telephone tech support for an ISP, I was expected to treat the callers with respect and courtesy, regardless of what I thought of them.

---

### Post by Nutria on 2011-10-16
> **uRock said:**
> If you are not willing to help the user, then why are you posting? You are criticizing the user for not being able to spot a file that he/she kindly asked you to to point them to.

Read the whole thread.

---

### Post by uRock on 2011-10-16
> **Nutria said:**
> Read the whole thread.

I have. The user has kindly asked you where in the link you see the file he/she needs. Could you point him/her to it?

---

### Post by Nutria on 2011-10-16
> **sideburns said:**
> I'm relying on you for the simple reason that I have no choice: you're the only person on this forum willing to respond.

You had to **privately** email me in order to get my help.  (I never read the Networking forum **because I don't know anything about it!!**)

> And, 99.44% of the time, her box runs with no need for my help.  This is a very unusual circumstance because although I know why she's off-line, I don't know enough of the Ubuntu-specific configuration programs to resolve it myself.

Neither do I.

> I also know that when I gave telephone tech support for an ISP, I was expected to treat the callers with respect and courtesy, regardless of what I thought of them.

You're getting exactly what you paid for from someone you consistently gave erroneous answers to and **who's advice you don't take**.  :x  :x

---

### Post by CharlesA on 2011-10-16
> **Nutria said:**
> 
You're getting exactly what you paid for from someone you consistently gave erroneous answers to and **who's advice you don't take**.  :x  :x

I would suggest losing the attitude. No need to be disrespectful. If you don't want to keep helping sideburns, then don't and leave it at that.

---

### Post by Nutria on 2011-10-16
> **CharlesA said:**
> I would suggest losing the attitude. No need to be disrespectful.

Is it disrespectful for him to consistently give me inaccurate information and call me a poisonous twit?

> If you don't want to keep helping sideburns, then don't and leave it at that.

Is there any way for me to disable people from directly emailing me even though I don't make my address public?

---

### Post by sideburns on 2011-10-16
> **Nutria said:**
> You had to **privately** email me in order to get my help.  (I never read the Networking forum **because I don't know anything about it!!**)

I have no idea what you're talking about.  I couldn't possibly have emailed you because I haven't the slightest idea who you are.  You just showed up here, out of the blue, asking quite reasonable questions and making good suggestions about trouble shooting it.  Then, when it got down to actually helping me find the files I need, you suddenly got coy and ignored my requests.  As far as reading the entire thread, I suggest that you go back and read the first three or four posts.

---

### Post by CharlesA on 2011-10-16
> **Nutria said:**
> Is it disrespectful for him to consistently give me inaccurate information and call me a poisonous twit?

I don't see anywhere in the thread where sideburns called you a "poisonous twit."

> Is there any way for me to disable people from directly emailing me even though I don't make my address public?

Their is no way for one member to email another, unless you are refering to the [Private Message]("http://ubuntuforums.org/private.php") feature.

---

### Post by sideburns on 2011-10-16
People, this argument is fun to read, but it's not getting anybody anywhere.  Please, if you must continue, do it in private.  (I love getting to tell the administrators that!)

A friend has told me, in private email, that there must be something badly wrong with Ubuntu if NetworkManager isn't installed.  I'm going to move the .deb files I downloaded over to her box, install them, reboot and see what happens.  If that fails, I'm going to back up her complete /home, get the newest version of Ubuntu via this computer and do what has to be done.

I have two questions about that: first, is it possible to tell the LiveCD to keep /home as it is if it's not on its own partition and second, is there a way to use the LiveCD to update or repair the current installation?

---

### Post by Nutria on 2011-10-16
> **sideburns said:**
> I have no idea what you're talking about.  I couldn't possibly have emailed you because I haven't the slightest idea who you are. 

**Someone** who calls himself Joe Zeff emailed me, saying that he use Fedora and his sister uses Ubuntu and that she lost all DNS functionality.

---

### Post by sideburns on 2011-10-16
I sit corrected, then.  Not only didn't I realize that was you, I'd completely forgotten about it.

---

### Post by CharlesA on 2011-10-16
> **Nutria said:**
> **Someone** who calls himself Joe Zeff emailed me, saying that he use Fedora and his sister uses Ubuntu and that she lost all DNS functionality.
Interesting. I have no idea how they would have gotten your email address, but I'm 99% sure that it wasn't from these forums.

---

### Post by Nutria on 2011-10-16
> **CharlesA said:**
> I don't see anywhere in the thread where sideburns called you a "poisonous twit."

OK, you're right.  He says that I suggest that he do poisonous, twit things.

[http://ubuntuforums.org/showpost.php?p=11351028&postcount=31](http://ubuntuforums.org/showpost.php?p=11351028&postcount=31)
[http://ubuntuforums.org/showpost.php?p=11353181&postcount=33](http://ubuntuforums.org/showpost.php?p=11353181&postcount=33)

IMO, only a poisonous twit would suggest that someone else do poisonous, twit things.

> Their is no way for one member to email another, unless you are refering to the [Private Message]("http://ubuntuforums.org/private.php") feature.

Yes, how to I stop that?  None of this wouldn't have happened if "Joe Zeff" didn't PM me.  See [http://ubuntuforums.org/showpost.php?p=11353649&postcount=45](http://ubuntuforums.org/showpost.php?p=11353649&postcount=45)

---

### Post by CharlesA on 2011-10-16
> **Nutria said:**
> 
Yes, how to I stop that?  None of this wouldn't have happened if "Joe Zeff" didn't PM me.  See [http://ubuntuforums.org/showpost.php?p=11353649&postcount=45](http://ubuntuforums.org/showpost.php?p=11353649&postcount=45)

That doesn't look like a normal PM notification. Those look like this:

```
DO NOT REPLY TO THIS EMAIL!
***************************

Dear CharlesA,

You have received a new private message at Ubuntu Forums from CharlesA, entitled "Test PM".

To read the original version, respond to, or delete this message, you must log in here:
http://ubuntuforums.org/private.php

This is the message that was sent:
***************
This is just a test.
***************

Again, please do not reply to this email. You must go to the following page to reply to this private message:
http://ubuntuforums.org/private.php

All the best,
Ubuntu Forums

```

And are sent from [email]site@ubuntuforums.org[/email].

---

### Post by Nutria on 2011-10-16
> **CharlesA said:**
> That doesn't look like a normal PM notification. Those look like this:

<snip>

And are sent from [email]site@ubuntuforums.org[/email].

Thanks for that info.

---

### Post by CharlesA on 2011-10-16
> **Nutria said:**
> Thanks for that info.
No problem.

I'm going to go ahead and close this thread.

sideburns: I would suggest creating a new thread in general help or in this forum with a more descriptive title and go from there.

---


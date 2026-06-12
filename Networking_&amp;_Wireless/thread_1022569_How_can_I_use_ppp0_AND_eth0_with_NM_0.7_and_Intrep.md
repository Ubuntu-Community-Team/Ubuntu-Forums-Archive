---
title: "How can I use ppp0 AND eth0 with NM 0.7 and Intrepid ?"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-26
As per the title of this thread, how can I use ppp0 _AND_ eth0 with NM 0.7 and Intrepid ?

I 'lost' ppp0 whilst trying to get a USB wireless dongle going (E169), and the only way to get ppp0 'back' was to remove eth0

I need the ppp0 of course for the USB wireless dongle, it is attached _direct_ to the computer, not a router.

I need eth0 to be able to share the wireless connection to another computer, and to be able to share files between 2 computers.

At present, no eth0 at all, it's disabled in the BIOS.

I don't dare enable it again, unless someone can convince that NM 0.7 with 8.10 can use ppp0 **and** eth0 (_without_ bugs/faults and other problems).

Oygle

---

### Post by oygle on 2008-12-27
Have seen a few posts about NM, where people recognise that NM can only enable one interface at a time. Some suggestions were to manually edit the file /etc/network/interfaces . Here are the contents at present:

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 



iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0
$ 

The 'gateway line was there previously, as the computer used to use a shared connection, but now that this computer is THE connection, I guess I could remove the whole gateway line.

But the major problem is not the gateway, it is not being able to use ppp0 and eth0.

There is a 'Wired' tab in NM. I assume that is eth0 ?

Also, I noticed in a thread in this forum ..

> Network Manager will not manage anything that is in /etc/network/interfaces

Is that correct ?

Oygle

---

### Post by oygle on 2008-12-27
In Hardy, there used to be, as part of network 'management', a function to alter the settings of eth0 and ppp0.  I assume all that did was modify /etc/network/interfaces file. What should be in that file for Intrepid, if I want to use ppp0 and eth0 ?

What impact has /etc/network/infaces (in Intrepid ) have on the whole control side of networking ??

Oygle

---

### Post by oygle on 2008-12-29
Is there any more information I can supply, to help solve this problem ??

Oygle

---

### Post by oygle on 2008-12-29
I assume no one knows how to do this ?

Should I remove all references to eth0 in the file /etc/network/interfaces ?

Hello, ....... anyone there.  ):P

---

### Post by oygle on 2008-12-30
Found a bug that seems to be the exact problem - [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290639](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290639) , and also at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262) , a number of people removed all the lines in /etc/network/interfaces for the ethernet side of things, and just left this ..

> auto eth0

which seems to agree with what other people have stated about Network manager 0.7 with Intrepid, that it won't mange anything that is in that file, hence the 'auto eth0' _only_.

HTH

Oygle

---

### Post by oygle on 2009-01-06
This bug report - [http://bugzilla.gnome.org/show_bug.cgi?id=559474](http://bugzilla.gnome.org/show_bug.cgi?id=559474) , states "resolved".

When will it 'appear' in Intrepid ?

Oygle

---

### Post by ciaranodonnell on 2009-01-06
I was having similar issue. I installed wicd instead and set up wireless through that program.  Seems much easier to use and less problems.  google wicd and it's the first hit.

---

### Post by oygle on 2009-01-06
Thanks, I will try out wicd. I assume it can use ppp0 and eth0 at the same time. There is a poll/thread [here]("http://ubuntuforums.org/showthread.php?t=587010") about NM and wicd, very interesting.

Oygle

---

### Post by Cinch64 on 2009-01-10
oygle,

I am having the same problem with my ppp0 internet AND getting my eth0 lan connection to work. Have you found a solution?
I tried to us wicd but ran into some compatability issues with Intrepid. Had to reinstall Intrepid and start again.
I have searched and searched for a fix for this Bug but to no avail.

---

### Post by oygle on 2009-01-11
@Cinch64 - I have been preparing to try a few things. Because i may not have internet when I do try these things, I need to (a) do a full backup prior to doing it, and (b) Have another computer with internet connection, so that I can get help if the Intrepid and NM doesn't with with the new setup.

Just about there, to do some changes, keep on eye on this thread and [http://ubuntuforums.org/showthread.php?t=1034850](http://ubuntuforums.org/showthread.php?t=1034850)

Oygle

---

### Post by oygle on 2009-01-17
Have had 'some' measure of success with doing this ..

1. Have made **NO** changes to the network manager connections. I think this is important, becasue it seems you need to leave NM to handle the ppp0 connection (internet), and then use CLI to get the eth0 up and going.

# cat /etc/network/interfaces

> 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0



iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0


all that has been done there, was to remove the 'gateway' line, as it caused some minor error. My understanding is that NM doesn't actually use this file anyway ???  (See Alexander Sack comment on this at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262/comments/55](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262/comments/55) )

2. Enabled the lan card

This might sound strange, but initially, I could only get NM to use the ppp0 by disabling the lan card in bios.

3. AFTER the ppp0 is up and running, bring up eth0 manually

```
sudo ifconfig eth0 up
```

4.  Assign the IP address of the 'host' computer (could not ping to it, prior to this, even though it was in /etc/hosts )

```
ifconfig eth0 192.168.1.100 netmask 255.255.255.0
```

At this stage, I had the 3 interfaces - lo, ppp0 and eth0

On rebooting, for several days now, it has worked flwlessly, in fact there has been no need to do the CLI commands, I get the ppp0 connect to the internet, and eth0 is up and working (can ping to it, from that computer).

So, all looked good, until [this little minor hiccup]("http://ubuntuforums.org/showthread.php?t=1042755") today.

Only have ppp0 and lo going now. No eth0, but hopefully some workaround for that. The lan card is disabled in the bios, but somehow ACPI, or for some reason, ACPI, is still loading the driver.

HTH

Oygle

---

### Post by oygle on 2009-01-18
Despite the minor hiccup yesterday (the update), it booted up today and I got internet okay. Still no eth0 going though.

Sure wish I knew where to get some help on this, there doesn't seem to be a NM trouble shooting guide or such, to be viewing what is happening in syslog, and to know what those messages mean.

Can NM be run in debug mode, I don't know :confused:

---

### Post by oygle on 2009-01-18
In a number of posts here , and also some responses to NM bug reports, I have seen advice/tips that Network Manager ignores any interfaces that have entries in /etc/network/interfaces.

Assuming this to be true, then the lines referencing eth0 can be removed, right ??  I will have to try it, and do a reboot.

Now, assuming that NM cannot manage 2 connections, and this is backed up by ....

> **dmizer said:**
> Ubuntu is perfectly capable of managing more than one connection. As of this writing, NetworkManager is not capable of managing more than one connection.

... I will have to use CLI to bring the eth0 up, assign it an IP, etc, etc

Back to some notes, or more the case, back to where I was several days ago.


Oygle

---

### Post by Macchi on 2009-01-21
Hi Oygle,

I believe that there are many limitations of the network manager, preventing it from handling several interfaces in the way you wish.

On problem for me right now is that Internet connection sharing does not seem to be working (as advertised for NM 0.7 ?). I could not get it to work with different  mobile broadband modems, besides testing with the latest Ubuntu, Suse and Fedora. Unfortunately no success. 

Another limitation is that the priority order seems to be fixed: Cable > Wifi > 3G. Thus if you have a different use case that what it was designed then it will not work.


Anyway, I would like to thank all the people that contribute for the network manager since it is a very important piece of software. But I hope that the NM will be improved soon because the number of mobile devices is growing, so as the complexity of the ways it is used.

---

### Post by oygle on 2009-01-21
Hi Macchi,

Wow, you have even tried different distros, you sure have been working hard at trying to get this going.

Are you sharing your ICS over ethernet, or over the mobile broadband (ppp0) connection ? I ask this because assuming NM cannot manage 2 connections concurrently, then using other tools (CLI ?? ) to share the internet connection may be the way to go ?

My 'approach' to trying to get this going, is to leave the NM setings as is, and then get eth0 up and going, and then try ICS from another computer. Although NM is 'tied into' the whole/complete networking, so it may 'complain' about ethernet, even though that is not managed by NM.

Yes, seems 3G is at the lower priority order. I even installed 'usb_modeswitch' , as some people had trouble with their USB sticks/modems, and that package sorted out any USB problems.

I also agree with you, that network manager since is an important piece of software. I did see some posts on different bug reports, where people could simply not test a mobile broadband connection, simply because they did not have the modem. As you say, complexity in the different network setups.

But, the bug reporting (launcpad) is not the 'place' for discussion, only for reporting, so solutions will not be found there, and the NM developers do not provide solutions on the Ubuntu forums, so it is up to Ubuntu users to find their way in the dark, so to speak.  ;)

Oygle

---

### Post by Loosewheel on 2009-01-21
Hi oygle,

I don't think you can run two connections at the same time from within NetworkManager. It seems NM looks for a wired connection first, and if it has one, sets it up. Then wireless, but doesn't set it up until after login and only if it has been used before.
Here's a link from the folks that brought you NetworkManager:
[http://www.redhat.com/magazine/003jan05/features/networkmanager/](http://www.redhat.com/magazine/003jan05/features/networkmanager/)

And a quote:
"Debian and Ubuntu modified NetworkManager so that it would not manage any devices listed in /etc/network/interfaces. If you open this file and comment out the lines for the interfaces you want to manage and reboot NetworkManager will see them. **Do not comment out l0**" 
From here:
[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-ded68c9a636fda990082a195d75c9d9129d1ba0a](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-ded68c9a636fda990082a195d75c9d9129d1ba0a)
(Look under 'Harware')

 A user guide:
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

And two others that are real handy:
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

You know, I think we are having problems going from ifupdown/network-admin, which uses /etc/network/interfaces, (Ubuntu-8.04/NM-.0.6.6), and NM-.0.7. It's an entirely different deal, using 'hal' via 'dbus'. I mean, after reading the man page for 'interfaces' I thought you were supposed to have the entries in the interfaces file. Not if ya want that physical IF to come up with NM. 

Anyhow, hope this helps.

---

### Post by oygle on 2009-01-21
> **Loosewheel said:**
> 
I don't think you can run two connections at the same time from within NetworkManager.

Agreed. It absolutely cannot be done with NM, not concurrently. Has been confirmed by many, and is on the NM bug list.

> **Loosewheel said:**
> 
It seems NM looks for a wired connection first, and if it has one, sets it up. Then wireless, but doesn't set it up until after login and only if it has been used before.
Here's a link from the folks that brought you NetworkManager:
[http://www.redhat.com/magazine/003jan05/features/networkmanager/](http://www.redhat.com/magazine/003jan05/features/networkmanager/)

Okay, the doc is 4 years old now, but still obviously very relevant, in that the mechanics of NM now, with hal, dbus, etc.

> **Loosewheel said:**
> 
And a quote:
"Debian and Ubuntu modified NetworkManager so that it would not manage any devices listed in /etc/network/interfaces. If you open this file and comment out the lines for the interfaces you want to manage and reboot NetworkManager will see them. **Do not comment out l0**" 
From here:
[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-ded68c9a636fda990082a195d75c9d9129d1ba0a](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-ded68c9a636fda990082a195d75c9d9129d1ba0a)
(Look under 'Hardware')


Yep, a number of the NM bug reports suggest this also. People have been able to get an interface 'going' by commenting it out in the interaces file. For me, ppp0 is critical, as it is the internet (mobile broadband), and so I intend to let NM connect as now, and then find out how to 'manually' manage eth0, that is, _not_ let NM try and manage it, but bring it up via CLI (and when that's working, some script file I guess).

Thanks for the links to those docs.

> **Loosewheel said:**
> 
You know, I think we are having problems going from ifupdown/network-admin, which uses /etc/network/interfaces, (Ubuntu-8.04/NM-.0.6.6), and NM-.0.7. It's an entirely different deal, using 'hal' via 'dbus'. I mean, after reading the man page for 'interfaces' I thought you were supposed to have the entries in the interfaces file. Not if ya want that physical IF to come up with NM. 


Yep, apparently NM doesn't look at that file at all.

I would like to know where the NM settings and config files are stored.

If I do this

```
# ls -alR /etc/NetworkManager/
```

apart from 'nm-system-settings.conf' , there is only a script, which uses scripts and files from /var/run/network and /etc/network. I'd like to know where NM stores the connection information. The small 'conf' file only has

> [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Thanks,

Oygle

---

### Post by oygle on 2009-01-22
Enabled the network card in BIOS, booted into Ubuntu and connected to the mobile broadband okay (ppp0).

I then started up the other Ubuntu computer (Hardy), it is connected to the hub/switch on the lan. Did this on the Intrepid computer, to make sure that ethernet was down first

```

# sudo ifconfig eth0 down

```

and then

```

# sudo ifconfig eth0 up
# sudo /etc/init.d/networking restart

```

It took a bit of checking the syslogs to see what each computer  was requesting, and then adjust firestarter appropriately. There were many of these messages appearing

> Jan 22 20:53:18 kernel: [ 2787.496084] Unknown OutputIN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.101 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=38718 SEQ=2 

and found a post in the Ubuntu archives, stating that it is Firestarter doing that. Checked the preferences in Firestarter, and it had

Internet connected device --  ppp0
Local connected device --   ppp0

although the local device was a select list and it did have eth0 there. As soon as i set the local one to eth0 though, all those extra messages stopped appearing in syslog.

I think that was a big issue in this not working before, getting Firestarter to have ppp0 as internet and eth0 as local. There is ICS enabled on Firestarter, so that is very handy.

I did have dnsmasq and ipmasq installed on the Intrepid computer, but have not for several days. I see no reason for it ??

Eventually was able to ping to each computer, and the Hardy one was actually able to get out to the internet, so ICS was up and going, and for some strange reason, I'm able to use both ppp0 and eth0 on Intrepid. NM is only 'managing' ppp0 though.

Have taken backups on both computers, and the hardy one has been rebooted and is still able to use the internet via ICS.

Will reboot this one soon, and hopefully, it will all come up okay.

Oygle

---

### Post by oygle on 2009-01-22
Booted up okay, connected okay, and can use the eth0 as well as ppp0.  :popcorn:

Also, the Hardy computer is still able to use ICS, so everything looks as though it is working okay.

No doubt a power down on both computers and a boot up will really show if it now works, but as NM is not managing the eth0, it should be okay.

Oygle

---

### Post by oygle on 2009-01-24
Well, I think I'll mark this as solved. Have booted up now for a few days, and all 3 interfaces are going (lo, ppp0 and eth0).

Network manager still says 'unmanaged' for eth0, but that's not a problem, because eth0 is actually up and working okay, and I don't have to touch anything at all.

The only CLI commands i did were outlined in [post #12]("http://ubuntuforums.org/showpost.php?p=6569126&postcount=12")

To answer the thread title, "How can I use ppp0 AND eth0 with NM 0.7 and Intrepid ?" , ....

It can be done, just make sure that you only use NM for _one interface_, and usually that will obviously be your internet connection (ppp0 for me).

Oygle

PS I would mark this as **SOLVED**, but the feature is disabled for now, see [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---


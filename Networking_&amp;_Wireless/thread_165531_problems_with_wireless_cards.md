---
title: "problems with wireless cards"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by thecrazymonk86 on 2006-04-24
I have a linksys WMP54G v.2(broadcom chip), i downloaded the the wireless network config tool from automatix  and got my drivers to install (bcmwl5.inf and so on..) it says that it has an ip address, has a link, but when i got to firefox ans try to open a page, or ping something, it says that the site couldnt be found.  I'd also like to note that when i see what the percentage of the link is, it says 100% but theres no way it has a 100% link.  Any ideas?  thanks!

---

### Post by khightower on 2006-04-24
Run the command ifconfig (from the terminal). Copy the results so we can have more info to help.

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]Run the command ifconfig (from the terminal). Copy the results so we can have more info to help.[/QUOTE]



eth0      Link encap:Ethernet  HWaddr 00:01:29:82:03:A4
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fe82:3a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2780673 (2.6 MiB)  TX bytes:494031 (482.4 KiB)
          Interrupt:22 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:724057 (707.0 KiB)  TX bytes:724057 (707.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:65:A9:20
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe65:a920/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16253 (15.8 KiB)  TX bytes:4108 (4.0 KiB)
          Memory:ec004000-ec005fff

---

### Post by khightower on 2006-04-24
what is the IP of your router?

---

### Post by thecrazymonk86 on 2006-04-24
192.168.1.1 or do you mean the outside?

---

### Post by khightower on 2006-04-24
When you open firefox can you get to the routers homepage with you type in that address?

---

### Post by thecrazymonk86 on 2006-04-24
no i cant

---

### Post by khightower on 2006-04-24
It's seems you may be connected to another wireless network. Did you configure you wireless card with a static IP or DHCP?

---

### Post by thecrazymonk86 on 2006-04-24
DHCP and the essid is mine, its the only one in range

---

### Post by khightower on 2006-04-24
Run sudo dhclient, you will need to enter your password.

See if you can revieve a new IP address, and even if it is the same you should see that the IP came from 192.168.1.1

---

### Post by khightower on 2006-04-24
Worst case you should be able to hit your router.

---

### Post by thecrazymonk86 on 2006-04-24
i got the same ip address and it came from 192.168.1.1, still cant get on

---

### Post by khightower on 2006-04-24
Still can't hit the 192.168.1.1 from firefox?

---

### Post by khightower on 2006-04-24
What version of ubuntu are you running?

---

### Post by thecrazymonk86 on 2006-04-24
breezy

---

### Post by thecrazymonk86 on 2006-04-24
you think it might have something do with my router?(WRT54g linksys)

---

### Post by khightower on 2006-04-24
Under System>Administration>Networking if you see your Wireless card there you can Deactivate it and Activate it. I had to this on my Wireless card. 

Also If you have not done it yet, you might want to re-boot the system.

---

### Post by khightower on 2006-04-24
Can you contect through a ethernet port on that same router?

---

### Post by thecrazymonk86 on 2006-04-24
i have done that a few times, but to no avail, also when i reboot my comp, the drivers exist, but the card is no longer in System>Administration>Networking, i have to uninstall then reinstall the drivers.

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]Can you contect through a ethernet port on that same router?[/QUOTE]


yes i can

---

### Post by khightower on 2006-04-24
I am using the Dapper version of Ubuntu, very stable. My network card worked right out of the box. I am using a SMC wireless card.

I think others have had many problems with previous version of Ubuntu and wireless networking. If you can you should try Dapper.

---

### Post by khightower on 2006-04-24
If you can connect through the ethernet port, your router seems fine. One last thing do you have WEP enabled?

You don't need it to connect, just want make sure we are not trying to connect to a secure wireless network without a key.

Seems like your problem has more to do with that version of ubuntu.

---

### Post by khightower on 2006-04-24
what kernel version are you running?

from the command line run  uname -r

---

### Post by thecrazymonk86 on 2006-04-24
ok a few things, i did another reboot for the hell of it, and my wireless stayed and i can log on to my router for some reason, but no internet yet, my kernal is...2.6.12-10-386

---

### Post by khightower on 2006-04-24
Good. progress

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]ok a few things, i did another reboot for the hell of it, and my wireless stayed and i can log on to my router for some reason, but no internet yet, my kernal is...2.6.12-10-386[/QUOTE]


Cable or DSL

---

### Post by thecrazymonk86 on 2006-04-24
its on a college connection so t3+

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]its on a college connection so t3+[/QUOTE]

You must have the cable form the wall in a regular port on the rounter and not the wan port

---

### Post by thecrazymonk86 on 2006-04-24
well yea, its an ethernet cable to the wall

---

### Post by thecrazymonk86 on 2006-04-24
umm, i tried to get to the router again, but it wouldnt go

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]well yea, its an ethernet cable to the wall[/QUOTE]

Sorry, what port do you have the cable in on the router. The WAN port or just any of the other ports. I think the WAN port should be off on its own

---

### Post by khightower on 2006-04-24
I say this because you will be able to get internet through the ethernet if you have the jack from the wall plugged into any port (sometimes). 

To easiest way to make sure the wireless part works you want to make sure the cable from the wall goes to the WAN port on your router.

---

### Post by thecrazymonk86 on 2006-04-24
i have the cable in the input, the only ports on the back are 1-4 and internet, the ethernet cable fromt the wall is plugged into the the internet cable, the computers internet is in on port 1.  I know internet is working because i'm on a laptop using wireless for that exact router.

---

### Post by thecrazymonk86 on 2006-04-24
did you get what i said on the previous page about not being able to connect to the router anymore?

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]i have the cable in the input, the only ports on the back are 1-4 and internet, the ethernet cable fromt the wall is plugged into the the internet cable, the computers internet is in on port 1.  I know internet is working because i'm on a laptop using wireless for that exact router.[/QUOTE]

OK

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]did you get what i said on the previous page about not being able to connect to the router anymore?[/QUOTE]

No, I thought you where able to connect to the router. DId you try and renew the IP address again

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]ok a few things, i did another reboot for the hell of it, and my wireless stayed and i can log on to my router for some reason, but no internet yet, my kernal is...2.6.12-10-386[/QUOTE]

I guess you meant **can't**

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]No, I thought you where able to connect to the router. DId you try and renew the IP address again[/QUOTE]


no i didnt, i realized that eth0 was still enabled and i guess it connected to the router, but the wireless tried to use the net?

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]umm, i tried to get to the router again, but it wouldnt go[/QUOTE]

The pages threw me off

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]The pages threw me off[/QUOTE]


yea i know what you mean

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]no i didnt, i realized that eth0 was still enabled and i guess it connected to the router, but the wireless tried to use the net?[/QUOTE]

The machine we are working on, is only trying to access the router via wireless, and now the ethernet cable is removed, right.

---

### Post by thecrazymonk86 on 2006-04-24
yes it is, sorry that took a while, the pages got me again

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]yes it is, sorry that took a while, the pages got me again[/QUOTE]

I am running a newer kernel version 2.6.15-21 and dapper 6.06

This is the last thing I would recommend, but I know newer kernel provide better driver support.

It seems like you have the router setup right if you are using it from another machine.

---

### Post by thecrazymonk86 on 2006-04-24
so can i update my kernal(i dunno how to do that), i tried dapper but i'm not good with developmental releases, do you know when dapper stable is being released? june 1st maybe?

---

### Post by thecrazymonk86 on 2006-04-24
i also read how broadcom isnt too great with linux either, and my chip on the wmp54g is a broadcom chip

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]so can i update my kernal(i dunno how to do that), i tried dapper but i'm not good with developmental releases, do you know when dapper stable is being released? june 1st maybe?[/QUOTE]

Dapper seems like it should not be a devel release. It has been working fine for me. 

When was the last time you ran a system update System>Administration>Update Manager

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]i also read how broadcom isnt too great with linux either, and my chip on the wmp54g is a broadcom chip[/QUOTE]

Thats why I got a SMC card. Cheap and works nice with Linux

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]Dapper seems like it should not be a devel release. It has been working fine for me. 

When was the last time you ran a system update System>Administration>Update Manager[/QUOTE]

today

---

### Post by thecrazymonk86 on 2006-04-24
is there a way to update the kernal from the terminal or something like that, i dont know that much about linux

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]is there a way to update the kernal from the terminal or something like that, i dont know that much about linux[/QUOTE]

I am about to write it out for you, one sec

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]is there a way to update the kernal from the terminal or something like that, i dont know that much about linux[/QUOTE]

Lets try it through Synaptic

---

### Post by khightower on 2006-04-24
System>Administration>Synaptic Package Manger

Enter your password.

Top right search for kernel

---

### Post by thecrazymonk86 on 2006-04-24
ok i did that but got this error, never seen it before when i opened syanptic:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

---

### Post by thecrazymonk86 on 2006-04-24
nevermind, i got rid of it

---

### Post by thecrazymonk86 on 2006-04-24
but searching kernal in synaptic didnt give me anything

---

### Post by khightower on 2006-04-24
I get that it means that the repositorys are not there or out of date.

You should still be able to use Synaptic.

---

### Post by thecrazymonk86 on 2006-04-24
but i'm stupid and spelt kernel wrong, i got a bunch of stuff, what should i click on?

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]but searching kernal in synaptic didnt give me anything[/QUOTE]

Conntect that machine to the net via ethernet

---

### Post by thecrazymonk86 on 2006-04-24
its connected

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]its connected[/QUOTE]

Try the Synaptic process again

---

### Post by thecrazymonk86 on 2006-04-24
alright i bunch of results, what should i choose

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]alright i bunch of results, what should i choose[/QUOTE]

You should see linux-386.

Check the version #

---

### Post by thecrazymonk86 on 2006-04-24
it says linux-386 2.6.12.16.1

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]it says linux-386 2.6.12.16.1[/QUOTE]

Top left, click the reload button

---

### Post by thecrazymonk86 on 2006-04-24
i did that but the version didnt change...

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]i did that but the version didnt change...[/QUOTE]

from the command line the only way I know will update your enitre distro. I don't want to do you like that. I am looking for a solution

---

### Post by khightower on 2006-04-24
I would try out dapper. I have been running it for 3 weeks and no problems

---

### Post by khightower on 2006-04-24
Let me know How it works out

---

### Post by thecrazymonk86 on 2006-04-24
alright thanks, would i just update the distro throught the command line?( how do i do that?

---

### Post by khightower on 2006-04-24
[QUOTE=thecrazymonk86]alright thanks, would i just update the distro throught the command line?( how do i do that?[/QUOTE]

Hold On

---

### Post by khightower on 2006-04-24
apt-get dist-upgrade

---

### Post by thecrazymonk86 on 2006-04-24
[QUOTE=khightower]apt-get dist-upgrade[/QUOTE]



thanks

---


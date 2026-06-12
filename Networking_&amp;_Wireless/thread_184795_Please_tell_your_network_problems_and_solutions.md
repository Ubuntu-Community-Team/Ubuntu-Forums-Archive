---
title: "Please tell: your network problems and solutions"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by christian.convey on 2006-05-30
I've seen a lot of chatter about network problems in Dapper. I suspect my problem was ethernet-chipset-related, so other people may have it as well. We should probably figure out what the common elements are of the problems we're collectively experiencing.

For those with problems, how about we use this thread to report:

- what chipset / adapter you're using
- what symptoms you experienced
- any workarounds you've tried and whether or not they worked?
- is this a regression for something that worked in previous versions of Ubuntu?
- are you using DHCP?

I'll go first...

_Hardware_
- Both computers had this adapter: Ethernet controller: **Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)**
 - One computer also had the **build-in adapter** in its **nForce4** motherboard.

_How I installed Dapper_
On two computers I upgraded from Breezy to Dapper RC using update-manager.  The updates went without a problem.

_Symptoms_
After installing, upon reboot my attempts to open web-pages failed.  Doing some tinkering with ifup/ifdown I concludded:[LIST]
[*]Sometimes DHCP lease acquisition would timeout.
[*]Other times it seemed to complete but I couldn't find a route to other computers.[/LIST]_Workarounds_
- On one computer, I did a clean Breezy install and right-away upgraded to Dapper. This was in case some extra junk I had installed on Breezy was causing the problem. This work-around *was not effective*.
- On the other computer, it turns out my **nForce4**-based ethernet controller is finally supported. (It wasn't in earlier versions of Ubuntu.) I started using that interface instead. This work-around *was effective*.

_Regression?_
Yes.  On both computers I had previously run Breezy, and the adapters worked with no problem.

_Bug tracking?_
I filed this bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46822]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46822")

---

### Post by playa_wun on 2006-05-30
> For those with problems, how about we use this thread to report:

- what chipset / adapter you're using

1. Cisco Aironet 350 
2. Sony PCWA 300 (Atheros)
3. Buffalo Airstation WLI-CB-G54A (Broadcom)
4. 3Com 3CRWE254G72 (USB)

> - what symptoms you experienced

1. Won't connect via DHCP after some update (perhaps install of network manager or kismet) - gave up.
2. Works fine out of the box, but kills jogdial on Vaios for some reason
3. Looked into ndiswrapper and lost the will to live
4. Quite like the USB option as this laptop only has one cardbus slot where a 5GB vfat disk lives

> - any workarounds you've tried and whether or not they worked?

1. Reflashed several times, no joy.  Backed out network manager and set back to normal and now fails on DCHPDISCOVER. 
2. Need jogdial so quite disappointed - works, but no jogdial.
3. Gave up pretty much straight away
4. Discovered driverloader and on 30 day trial - works *really* well, this device was flaky under windows but is reliable under driverloader...

> - is this a regression for something that worked in previous versions of Ubuntu?

Nope - booted floppy install for Breezy then updated to Dapper straight away.

> - are you using DHCP?


Yes - and OpenWrt on the router that rocks with everything else - how ironic!
Oh, and only using WEP.

Have ordered two cheapie USB wifi dongles as I'm of the school of thought that thinks paid for Linux software for personal use is a no-no.
 
One's a Zydas and the other is some other chipset that will need ndiswrapper or driverloader..  Will report back if I get anywhere with these.

Must say I've done so many restarts to attempt to fix the above that I've seen the fsck progress bar twice.  After trying every wireless device in the house I am *this* close to reinstalling 'doze, which is a shame as the rest of Dapper is so polished. :(

Not doing any bug reports until I've managed to do a clean install of Dapper, but can't due to lack of floppy install images (see my other thread floating round this forum)

---

### Post by apejcic on 2006-05-30
Hardware
- **SMC 2802W v2**

How I installed Dapper
Fresh install

Symptoms
Loaded prism54 module, that doesnt work with my v2 card

Workarounds
- Installed ndiswrapper, and blacklisted prism54 (/etc/modprobe.d/blacklist)
- Islsm (softmac) should support it now, but it didnt work for me

Also networkmanager (latest 6.2) doesnt work for me.

---

### Post by bmasephol on 2006-05-30
Hardware
------------------------
ActionTec 802CAT1 (Atmel based) using the kernel drivers (just works)
info here --> [http://thekelleys.org.uk/actiontec.html]("http://thekelleys.org.uk/actiontec.html")

Install
------------------------
Fresh install, been trying releases since Xubuntu - Flight 6 or 7

Symptoms
------------------------
when connecting to any AP with WEP (device only supports WEP) everything works fine.

when connecting to any AP without WEP (open) I get no signal but do get the MAC of the AP and also DHCP fails to get a ip.  Also from what I can tell trying to setup static ip fails as well.  I've tried with 3 different open AP's including 2 that were located 10 feet from the laptop.

Other Notes
------------------------
Have dual boot with windows 2000 and when in windows can connect to everything just fine.

---

### Post by awaldram on 2006-05-30
Intersil Corporation Prism 2.5 Wavelan chipset
RC1
symptoms
won't connect using network manager wep/wpa
solution
gave up on wep forced wpa_supplicant to connect using hostap afterwards works with network manger (go figure)


3com prism54
RC1
islsm driver doesn't support WPA couln't get to work with WEP 
solution....
blacklisted islsm to use prism54 .. didn't work

compiled 2.6.16 works fine with prism54 as per prior kernels before devs latest 'feature freeze' kernel updates (no I'm not bitter mutter mutter mutter).


I should point out both funtioned fine in Breezy and earlier Dapper releases.

---

### Post by detour on 2006-05-30
Hardware: Netgear WG311v2 (ACX111 chipset -aka- Texas Instruments)

Install: Fresh from CD

Symptoms: Claims to work using ACX111 drivers. Lies.

Workaround: Use ndiswrapper. Wrote a script to fix - remove acx module, add ndiswrapper module, reload networking. Needs to be run every time I reboot. Ideas on automating would be helpful.

---

### Post by ggw10 on 2006-05-30
i) setup: Thinkpad T42 running Ubuntu Dapper, 
with an ipw2200 wireless chipset. Netgear DG834G 
router.access point 
at home, wireless network with various access points. 
WAP authentication on my network at home, no authentication
on my network at work. 
ii) symptoms: NetworkManager does not work on
the home network (just will not associate).. However, NetworkManager does work, quite
unproblematically, on the work network. 

It might seem that the problem lies with wpasupplicant (because
wpasupplicant handles authentication for NetworkManager), but
wpasupplicant works fine on my home network when
driven from the command line with suitable arguments. 

iii) workaround: I use ifup/ifdown, after editing /etc/network/interfaces
by hand after each transition from home to work and back. This
works fine. 

I have tried, in a similar way, using the Properties tab in System/Administration/Networking, but (apart from the fact that
it's slower to do than editing /etc/network/interfaces by hand) 
it seems to have no effect: it claims that interfaces are active
when they are not actually configured. 

iv) regression: NetworkManager used to work fine in Breezy,
before it used wpasupplicant for authentication. 


Final remark (1): I'm quite a good systems programmer, but it
seems to me that this whole network system is made of so many
interlocking and barely compatible parts that it's extraordinarily
difficult to find out what component is responsible when
something goes wrong. 

Final remark (2): Problems like this, which are due to the
interaction between different packages, do no do very well
in the current debugging system, which has to assign
responsibility for failure to a single package. I have 
no idea whether this problem is due to NetworkManager, or
to wpasupplicant, or to something strange and arcane about 
their interaction.

---

### Post by ssam on 2006-05-30
Ralink RT2500

doesn't work with wpasuplicant and therefore does not work with networkmanager > 0.6
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37120](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37120)

solution

use network manager 0.5 (i can live without WPA)

get the network-manager package
[https://launchpad.net/distros/ubuntu/dapper/powerpc/network-manager/0.5.1-0ubuntu19](https://launchpad.net/distros/ubuntu/dapper/powerpc/network-manager/0.5.1-0ubuntu19)
[https://launchpad.net/distros/ubuntu/dapper/i386/network-manager/0.5.1-0ubuntu19](https://launchpad.net/distros/ubuntu/dapper/i386/network-manager/0.5.1-0ubuntu19)
and nm-applet
[https://launchpad.net/distros/ubuntu/dapper/powerpc/nm-applet/0.5.1-0ubuntu19](https://launchpad.net/distros/ubuntu/dapper/powerpc/nm-applet/0.5.1-0ubuntu19)
[https://launchpad.net/distros/ubuntu/dapper/i386/nm-applet/0.5.1-0ubuntu19](https://launchpad.net/distros/ubuntu/dapper/i386/nm-applet/0.5.1-0ubuntu19)

if you get a message about "The NetworkManager applet could not find some required resources. It cannot continue." then run
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```
(see Bug #37128 )

(if those links go down i have the packages, so email me and i'll put them online)

---

### Post by joepotter on 2006-05-30
Ralink RT2500:
I have control of 25 desktop boxes of various types that use this chipset in the wireless card. The cards will connect to a 3Com router with WEP but can not be made to connect to the router with WPA. Further the cards can not connect to WEP or WPA if the wireless router is in mixed mode that allows for clients of either type.

Broadcom:
I also have control of some laptops with built in Broadcom cards and the latest kernel upgrade killed wireless connection using ndiswrapper. We can still boot with wireless on older kernels that are still on the boxes.

---

### Post by playa_wun on 2006-05-30
*Totally* agree - there should be some sort of automagic way to say versions x y and z of packages a b and c work the best together - having all these disperate versions of vital components is nothing but a headache to diagnose a problem with.

---

### Post by secretlondon on 2006-05-31
[QUOTE=playa_wun]

Have ordered two cheapie USB wifi dongles as I'm of the school of thought that thinks paid for Linux software for personal use is a no-no.
 
One's a Zydas and the other is some other chipset that will need ndiswrapper or driverloader..  Will report back if I get anywhere with these.
[/QUOTE]

Hardware: Cheap USB wireless dongle with zydas chipset. Built in Nforce 2 wired ethernet.

Install: OEM install of RC.

Symptoms: DHCP timed out on wireless connection. No throughput using static IP.

Workarounds: Boot machine without dongle attached. Insert dongle after boot and it Just Works. Wired card works out of the box - no problems.

Regression: Not tried Breezy, didn't work in Warty.

---

### Post by TimJ on 2006-05-31
Hardware:
Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31) (if I check device manager under XP it says CnetPro200WL Fast Ethernet Adaptor)

Install: Update from Breezy and, after problem emerged, clean install from cd.

Symptoms: Usually, I can open Firefox with connectivity or use the update manager and download files for 5-10 seconds within booting up, then it goes dead. Symptoms sound very similar to post 1 in this thread.

Workaround: XP on other hard drive. Contemplating reinstalling Breezy but feeling annoyed at the idea of going back to Breezy instead of being able to use Drake.

Regression: Yes worked fine under Breezy (ironically I started using Ubuntu because Breezy life disk was the only live disk distro I tried that found my network card and had net access up and running).

Anyone got any solutions? Or even avenues to try?

[Edited to fit into format of Hardware: Install: etc.]

---

### Post by tonyr on 2006-05-31
_Hardware_
Dell Inspiron 2650 laptop,  Zonet ZEW1501 PCMCIA (RaLink RT2500 chipset)

_How I installed Dapper_
Started with Flight-4, both Ubuntu and Kubuntu as #3 and #4 OS
multi-boot with XP and Mandriva 2006.

_Symptoms_
ra0 was recognized and the driver installed at OS installation, but was not
configured.  I worked exclusively with Kubuntu.  Neither **Connections** nor
**Network Settings**  in the **System Settings** UI would affect
configuration or activation (both would throw exceptions).  I edited
**/etc/network/interfaces** to add the **iface**, **wireless-essid**,
and **auto** entries for ra0.  I checked the behavior during upgrades
and the next couple of flights, but didn't see any improvement, so I'm
sticking with the  manual method for now.  Otherwise, the card works OOTB.

_Regression?_
N/A

_Bug tracking?_
N/A

---

### Post by playa_wun on 2006-05-31
> Have ordered two cheapie USB wifi dongles as I'm of the school of thought that thinks paid for Linux software for personal use is a no-no.
 
One's a Zydas and the other is some other chipset that will need ndiswrapper or driverloader..  Will report back if I get anywhere with these.

Success!  Followed instructions from zydas howto in the breezy forums and adjusted for dapper/revision b of hardware.   Modprobe'd first time and mouse buttons died.

Swore, crossed fingers and bounced machine and all came up with no problem.  Chuffed to bits and quite pleased as this was the cheapest dongle I could find.

First time I've compiled from source too...

---

### Post by gozzerd on 2006-06-01
Ok I'm also using a Davicom listed as 21x4x DEC-Tulip compatible 10/100 and the driver is tulip. I've got no connection to anything. dmesg | tail gives me this repeated message

[  421.286694] 0000:00:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc740000 CSR6 0x2042002)
[  423.686736] 0000:00:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc740000 CSR6 0x2042002)
[  426.086765] 0000:00:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc740000 CSR6 0x2042002)
[  428.486816] 0000:00:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc740000 CSR6 0x2042002)

and so on. 

the network app shows all send and receive errors.

lsmod shows tulip is loaded

I haven't got a clue what to do. I would think maybe it's the wrong driver, but i have been running tulip for this card for years.

Currently works in XP, puppy linux and I'm sure anything else I run. worked great in Breezy. 

I could sure use some help.

Geoff

---

### Post by charles woodward on 2006-06-01
Network manager works fine when connecting to an unencrypted wireless network, but cannot log into an encrypted network.

Looking at the /var/log/messages I noticed that when trying to contact an encrypted network I get something like this :
 localhost dhcdb : message_handler : message handler not found under /com/redhat/dhcp/eth0 for sub path ....

I do not have a directory for `/com/redhat` - does anyone now how I can change this - I have re-installed all wireless, network manager and dependenceis and still get this message.  

Is this a bug - or have I got the wrong version of something?  Anyhelp would be appreciated.  I think this is either the cause of the problem, or a strong hint as to the exact problem.

(I've searched the forums and noticed that several other people have had the same error message - but it hasn't been picked up by others and I can't tell if their problems were resolved)

---

### Post by charles woodward on 2006-06-01
Having problem with network manager - does not connect to encrypted networks, but works ok with non-encrypted ones.   Have tried every suggestion put on the forums (I first encountered this problem almost two months ago).

However I've noticed on the /var/log/messages that whenever I try to connect to an encrypted network I get the following message:
** localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name**

Now I don't have a directory called /coms/redhat, and a find doesn;t show up any software called mess_handler

Does anyone know how I can correct this - I've re-installed every part of the wireless and network manager stuff (including all dependencies) but still get the error.

(sorry If I've already posted this - I lost connection and have been trying for two hours to get back on)](*,) ](*,)

---

### Post by kbunsie on 2006-06-01
**Hardware**:
Linux - Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
Windows - CnetPro200WL Fast Ethernet Adapter

**Install**:
Update (Breezy), Live Install, Clean Install

**Symptoms**:
Not able to establish a connection to D-Link router. After boot, DHCP gets IP and DNS fine but is unable to communicate with router. Pinging router fails 100%. Worked in Breezy and on all Live CDs. Breezy Identified the NIC the same as dapper.

**Workaround**:
If ethernet cable is disconnected and reconnected, Dapper can communicate with the router and connection lasts for only a couple of minutes.

---

### Post by mriya3 on 2006-06-01
Hardware:
  Siemens PC-Card 11 (PCMCIA), wireless card
  dmesg returns:  eth1: Atmel at76c50x. Version 0.98. MAC ...

**Worked on Breezy (kernel 2.6.12)**

On a clean Dapper install I cannot get DHCP to work (wireless access points are listed, but dhcp requests times out)

I think it's a kernel regression with the atmel driver, as I tried also with Suse 10.1 and I got the same problem.

---

### Post by bmasephol on 2006-06-01
[QUOTE=mriya3]Hardware:
  Siemens PC-Card 11 (PCMCIA), wireless card
  dmesg returns:  eth1: Atmel at76c50x. Version 0.98. MAC ...

**Worked on Breezy (kernel 2.6.12)**

On a clean Dapper install I cannot get DHCP to work (wireless access points are listed, but dhcp requests times out)

I think it's a kernel regression with the atmel driver, as I tried also with Suse 10.1 and I got the same problem.[/QUOTE]

I've got the same problem with my Atmel (actiontec 802CAT1) - can you elaborate on what you mean by kernel regression and if anybody knows what might help fixing... upgrading the kernel?  Thanks

---

### Post by dfme on 2006-06-01
[QUOTE=TimJ]Hardware:
Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31) (if I check device manager under XP it says CnetPro200WL Fast Ethernet Adaptor)

Install: Update from Breezy and, after problem emerged, clean install from cd.

Symptoms: Usually, I can open Firefox with connectivity or use the update manager and download files for 5-10 seconds within booting up, then it goes dead. Symptoms sound very similar to post 1 in this thread.

Workaround: XP on other hard drive. Contemplating reinstalling Breezy but feeling annoyed at the idea of going back to Breezy instead of being able to use Drake.

Regression: Yes worked fine under Breezy (ironically I started using Ubuntu because Breezy life disk was the only live disk distro I tried that found my network card and had net access up and running).

Anyone got any solutions? Or even avenues to try?

[Edited to fit into format of Hardware: Install: etc.][/QUOTE]

I have the same problem.
i upgraded my distribution from breezy to dapper...
since the upgrade my box gets an ip at startup but shortly after the connection is lost again. and when doing ifdown - ifup the dhclient responds with an error (no dhcpoffers received). and yes before (with breezy) dhcp worked without any problems...
i´ve tried to apply a static ip to the box with the corresponding gateway but the same thing happens: at start up i have a connection for 30secs and then the connection is lost again....](*,)

---

### Post by meat on 2006-06-01
Install: Clean install of Dapper on my Thinkpad T21 laptop.

Network Card: Lucent Ornico Gold PCMCIA wireless network card.

Driver: Dapper sees the card out of the box and I activate the connection.

I can see the wireless signal bar graph, but wireless does not work.

Unable to get a DHCP address using dhclient.

Static IP, no encrytion does not work either.

Solution: Install Windows XP on laptop and play with Dapper on a desktop machine.

---

### Post by TimJ on 2006-06-02
For those with the Davicom Card this thread might have the answer, so far it's working for me.
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by dfme on 2006-06-02
[QUOTE=TimJ]For those with the Davicom Card this thread might have the answer, so far it's working for me.
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)[/QUOTE]
this worked for me! :D (even though i´m not using a davicom card...)
thanks for the link!

---

### Post by entangled on 2006-06-02
System: Intel Mac Mini with Atheros AR5006EXS wireless card (AR5424 chipset).

Latest Situation: After booting CD of desktop 6.06 RC (the 'live' CD) the card was detected but not associated to AP (running on channel 1). Issued 'sudo iwconfig ath0 channel 1' and was connected to my Netgear DG834G Open AP, with DHCP address. Now working well.

Previously: Have been running Dapper from hard disk and upgrading regularly. Had to deinstall linux-restricted-modules to remove madwifi modules and compile up the madwifi-ng modules instead. The card worked but DHCP used to fail.

Now, with the new 6.06 RC CD, it works better because I can use DHCP and I don't have to reinstall the madwifi modules.

PS. To get connected during boot I put the iwconfig line at the end of /etc/init.d/bootmisc.sh.

---

### Post by rustinh on 2006-06-02
This is the same problem I am having with my CnetPro200WL card.  I'm connected for 10 seconds then nothing responds.


[QUOTE=TimJ]Hardware:
Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31) (if I check device manager under XP it says CnetPro200WL Fast Ethernet Adaptor)

Install: Update from Breezy and, after problem emerged, clean install from cd.

Symptoms: Usually, I can open Firefox with connectivity or use the update manager and download files for 5-10 seconds within booting up, then it goes dead. Symptoms sound very similar to post 1 in this thread.

Workaround: XP on other hard drive. Contemplating reinstalling Breezy but feeling annoyed at the idea of going back to Breezy instead of being able to use Drake.

Regression: Yes worked fine under Breezy (ironically I started using Ubuntu because Breezy life disk was the only live disk distro I tried that found my network card and had net access up and running).

Anyone got any solutions? Or even avenues to try?

[Edited to fit into format of Hardware: Install: etc.][/QUOTE]

---

### Post by TimJ on 2006-06-02
Rustinh see my post 23 above, it has a link that fixed my problem. If you've the exact same as me give it a tryl.

---

### Post by polo_step on 2006-06-04
[QUOTE=joepotter]Ralink RT2500:
I have control of 25 desktop boxes of various types that use this chipset in the wireless card. The cards will connect to a 3Com router with WEP but can not be made to connect to the router with WPA. [/QUOTE]
[FONT="Courier New"]I have no idea if this would be of the least use, but here's [a thread]("http://www.ubuntuforums.org/showthread.php?t=78250&highlight=rt2500") about getting WPA working with the RT2500 in 5.10 and it looks like some of the same principles would still apply.

I have this card in my notebook.  Despite all the claims for improved wireless support in 6.06, it looks from these threads as though nothing has changed much at all. :( [/FONT]

---

### Post by joepotter on 2006-06-04
[QUOTE=polo_step][FONT="Courier New"]I have no idea if this would be of the least use, but here's [a thread]("http://www.ubuntuforums.org/showthread.php?t=78250&highlight=rt2500") about getting WPA working with the RT2500 in 5.10 and it looks like some of the same principles would still apply.

I have this card in my notebook.  Despite all the claims for improved wireless support in 6.06, it looks from these threads as though nothing has changed much at all. :( [/FONT][/QUOTE]

Thanks for your attempt to help. The way things worked in Breezy is different to the way things work in Dapper. This will be a good thing, perhaps, in the long run.

As it stands, Dapper was released without any official way to get WPA done. The official wiki links you to a Debian resource.

So, I figured to heck with Ubuntu, I'll go to the people that do this:
[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)

From that and other pages around I was led to try the below in my /etc/network/interfaces file:


auto ra0
iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "bucky"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set Channel=5
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="show7me7the7net"
        pre-up ifconfig ra0 up

Not to worry, I have changed my pass-phrase already. I think the rt2500 driver is a tad flaky so the up-down-up-down jazz helps with the hand-shake part.

I went though all the pre-up commands from the command line first, ie.

...
$ sudo ifconfig ra0 down
$ sudo iwconfig ra0 essid "bucky"
$ sudo iwconfig ra0 mode Managed
$ sudo iwpriv ra0 set Channel=5
$ sudo iwpriv ra0 set AuthMode=WPAPSK
...
and so on untill I made sure each line worked with my card. These commands work with a rt2500 chip and the driver in Dapper.

My wife has used this set-up from the other end of the house for days, and I and using it now. We both use desktop boxes and have pci cards. 

This could make a difference as the 2500pci driver seems to be working. 

Note: My laptop is still dead (not an rt2500 however)

---

### Post by JeremyBoden on 2006-06-04
I've got *exactly* the same configuration etc (Tulip, Davicom etc).
Since I've got a static address, I changed it for that - doesn't make any difference!!!

BTW if I reset my ADSL router (the gateway address), then I get internet access - but only for about 30 seconds.

Jeremy

---

### Post by ousooner919 on 2006-06-04
Hardware: Dell Latitude D610, Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express, Intel Corporation PRO/Wireless 2200BG

Everything worked wonderfully in Breezy, even with a bit of manual config to get wpasupplicant going. Now, everyone says "use Knetworkmanager", so I do. First got it going last night, and everything was fine...surfed fine, everything reachable.

Then I made my mistake...I shut my laptop down.

This morning, I wake up, fire up the laptop, look at knetworkmanager and see the following:

"No network device found."

Now, everything is EXACTLY the same as how I left it last night...no mucking with configs for networking or anything. It just doesn't work at all now, and worse, knetworkmanager doesn't even see my WIRED let alone my wireless. Only reason I'm on right now is because I went back to the wired and configured everything by hand through ifconfig!!!!

I'm going to try uninstalling and reinstalling knetworkmanager for now to see if I can get the dadgum thing running again but that will quickly become quite tiresome if it works and that's my current "workaround". Frankly, I'd rather do it the old-fashioned way, using the manual wpasupplicant...at least THAT worked consistently.

---

### Post by ousooner919 on 2006-06-04
More on my issues...nothing unusual in dmesg, nothing unusual in /var/log/messages. I know the system sees the card and the wireless is working, because I use wlassistant and it sees my neighbor's SSIDs with no trouble and sees my own AP (though it's hidden). But wlassistant doesn't do anything for WPA.

---

### Post by aresgunther on 2006-06-04
Hello.  I just installed Ubuntu over Windows XP.  I use a wireless connection with a linksys 802.11g wireless notebook adapter.  After installing v6.06, it reconized my card and I put in the router address (linksys).  I enabled it, and got nothing.  The signal shows zero, even when I put my computer very close to the router.  With previous installations of Ubuntu I never had this problem.  The wireless card is not at fault, because I have tried others.  Also, I have tried the hardware detector, and it always freezes up when it gets to networking.

Any suggestions?


Ares

---

### Post by gizzmoe on 2006-06-04
_Hardware:_
- Gigafast WF747-UI (USB Wireless Adapter)

_Problem_
- You will notice that Dapper will tell you it knows about your device (it shows up in the network settings area of the control center), yet you can't get it to come up.

_Solution_
- The culprits here are some Prism drivers that Dapper thinks need to be associated with your device. To fix this issue, you will need to add these lines to /etc/modprobe.d/blacklist:

blacklist islusb
blacklist islsm
blacklist islsm_usb

Reboot.

Now, in addition to blacklisting those, you will need to install ndiswrapper from the repository (located on the install cd), and load the driver from the CD that comes with the adapter (AWLGTNIC.inf). After ndiswrapper is all configured, you should notice that the adapter will show up again in the network settings (most likely it will have a new name tho...mine went from eth1 to wlan0). Re-configure it in the network settings and enable it and voila!

That's how i got this adapter to work and now it comes up every time when i restart :)

---

### Post by polo_step on 2006-06-05
[QUOTE=joepotter]Dapper was released without any official way to get WPA done. [/QUOTE]
[FONT="Courier New"]If true, that's absolutely astonishing.

I mean, why did they even *bother* with wireless?[/FONT]:rolleyes:

---

### Post by microsome on 2006-06-05
Hi,

have similar problems. Everytime I start my laptop (Dell 600M, ipw2200) the network manager either does not connect or doesn't see a network at all or, surprise,  just connects. It's totally unpredictable. Probably 'cause it is still a beta version. Luckely I have a dual boot with XP.

---

### Post by darckhart on 2006-06-05
hi all. i had originally posted my problem here, but maybe you guys can shed some light on the issue:
[http://www.ubuntuforums.org/showthread.php?t=187811](http://www.ubuntuforums.org/showthread.php?t=187811)

i am using a manually configured for static ip WIRED lan connection (ie. ifconfig, resolv.conf).

eth0: 192.168.1.149
gateway: 192.168.1.1
nameservers: 208.13.28.12, 208.13.31.12, 63.203.35.55

hardware:
nic: D-Link RTL8139 (rev10)
router: Linksys WRT54g v1.0 w/HyperWRT Thibor firmware
modem: SBC Efficient Networks Speedstream 5100

symptoms:
no name resolution. pinging router gateway works. pinging wan ip works. pinging the named url does NOT work. HAVE tried the various suggestions from posts in these forums, but none have worked as of yet.

---

### Post by tropho on 2006-06-05
*To those weary from battling Linux wifi I offer this story:*

**NOTE: All of the following takes place AFTER the epic journey to find NDIS drivers that ndiswrapper would actually accept***

I fought and fought with both Breezy and Dapper regarding support for my SiS 163U chipset-based USB 802.11g adapter.  After several nights I finally figured out what the problem was via a French (!) wireless Linux forum:

My wireless USB adapter defaults to 802.11FH rather than 802.11g!

Correct me if I am wrong (or don't bother) but apparantly the FH specification is for some sort of long distance or coporate-type wireless setup vs. the home-oriented 54g specification.

At any rate typing:

* "sudo iwpriv wlan0 network_type g"*

configured the adapter for 802.11g operation and I could then use:

[I] "sudo iwconfig wlan0 essid xxx",
 "sudo iwconfig wlan0 key open s: yyy",
 "sudo iwconfig wlan 0 commit",[/I]
 then finally *"sudo dhclient wlan0"*

to get DHCP to assign an IP address to the adapter (replace *xxx *with your ESSID and *yyy *with your WEP key)

I still had to do this every time I rebooted or unplugged, then plugged in the adapter, so I put all of the above in my */etc/init.d/bootmisc.sh* file and it *Just Works* every time!

Good luck to all and I hope this helps at least the 3 other people in the world trying to make a SiS 163U chipset-based wifi USB dongle work in Linux, or at least Ubuntu.

---

### Post by Snowmansam on 2006-06-15
[QUOTE=gizzmoe]_Hardware:_
- Gigafast WF747-UI (USB Wireless Adapter)

_Problem_
- You will notice that Dapper will tell you it knows about your device (it shows up in the network settings area of the control center), yet you can't get it to come up.

_Solution_
- The culprits here are some Prism drivers that Dapper thinks need to be associated with your device. To fix this issue, you will need to add these lines to /etc/modprobe.d/blacklist:

blacklist islusb
blacklist islsm
blacklist islsm_usb

Reboot.

Now, in addition to blacklisting those, you will need to install ndiswrapper from the repository (located on the install cd), and load the driver from the CD that comes with the adapter (AWLGTNIC.inf). After ndiswrapper is all configured, you should notice that the adapter will show up again in the network settings (most likely it will have a new name tho...mine went from eth1 to wlan0). Re-configure it in the network settings and enable it and voila!

That's how i got this adapter to work and now it comes up every time when i restart :)[/QUOTE]

Thanks man...worked great for me using an older D-Link AirPlus XtremeG DWL-G120 USB nic. 

Breazy was no problem setting up ndiswrapper but with Dapper the "improved wireless support" got in the way of a perfectly good solution. Dapper was saying my card was a B type card instead of the G type that it is.

also fyi: before applying solution i could only see my ap after i set nic mode to managed manually. guess auto...really isn't auto. although i could see my ap, dhclient couldn't get a connection.

thanks again gizzmoe

---

### Post by Anophele on 2006-06-15
My problem... and my solution

[http://ubuntuforums.org/showthread.php?t=193575](http://ubuntuforums.org/showthread.php?t=193575)

HTH

---

### Post by paradoxium on 2006-06-15
_Hardware_
Rhine II ethernet adapther
Broadcom 43xx, works fine with ndiswrapper in Breezy, using the bcmwl5 driver.


_How I installed Dapper_
Downloaded DVD ISO.   I tried installing fresh twice.  I also tried the "update." 


_Symptoms_
I can get both to "look" like they work, everything seems to look like it did from Breezy, but if I try to use ethernet...nothing happens.  wireless doesn't scan or anything...

_Regression?_
Yes.  On both computers I had previously run Breezy, and the adapters worked with no problem.  I reinstalled Breezy.

---

### Post by dan4444 on 2006-06-15
see my post at [http://www.ubuntuforums.org/showthread.php?p=1142288#post1142288](http://www.ubuntuforums.org/showthread.php?p=1142288#post1142288)

---

### Post by Noobie_Unbuntu on 2006-06-15
I am new to Unbuntu 6.06 I am having major problems with my inter net addapters! [COLOR="red"][COLOR="Navy"]**_Please Please help me_**[/COLOR][/COLOR]! I am at my wits end!!

I have tried two different working adapters that I had lying around:

1.  [COLOR="navy"][COLOR="Navy"] Intel Pro /100 ISA (TP) 651538 with i82556 chipset[/COLOR][/COLOR]

2.  [COLOR="red"][COLOR="Red"]SMC ultra 8416 ISA card[/COLOR][/COLOR]

Apprently there isn`t any drivers avalible to run The Intel Pro with Linux?????

The SMC card shows up under system devices as PNP1 , but is not visible under networking, the only device showed under networking is a fax modem PPP0???? which I removed from the PCI slot inside the case!

I have treid a "hot unplug replug" with the SMC ISA card, and tried using the dos program that came with the SMC driver to configure it, etc.. 

What I don`t understand is that the [COLOR="Red"]SMC card seems to register as PNP1, shouldn`t it be eth0, or eth1[/COLOR], being a Ethernet card for a cable interent connection?

---

### Post by Noobie_Unbuntu on 2006-06-16
[QUOTE=Noobie_Unbuntu]I am new to Unbuntu 6.06 I am having major problems with my inter net addapters! [COLOR="red"][COLOR="Navy"]**_Please Please help me_**[/COLOR][/COLOR]! I am at my wits end!!

I have tried two different working adapters that I had lying around:

1.  [COLOR="navy"][COLOR="Navy"] Intel Pro /100 ISA (TP) 651538 with i82556 chipset[/COLOR][/COLOR]

2.  [COLOR="red"][COLOR="Red"]SMC ultra 8416 ISA card[/COLOR][/COLOR]

Apprently there isn`t any drivers avalible to run The Intel Pro with Linux?????

The SMC card shows up under system devices as PNP1 , but is not visible under networking, the only device showed under networking is a fax modem PPP0???? which I removed from the PCI slot inside the case!

I have treid a "hot unplug replug" with the SMC ISA card, and tried using the dos program that came with the SMC driver to configure it, etc.. 

What I don`t understand is that the [COLOR="Red"]SMC card seems to register as PNP1, shouldn`t it be eth0, or eth1[/COLOR], being a Ethernet card for a cable interent connection?[/QUOTE]

[COLOR="DarkRed"]I found my own fix, so if anyone else needs it hear you go:

Open a terminal, and Type:

Sudo gedit /etc/modules[/COLOR]
[COLOR="darkred"][COLOR="darkred"]type "smc-ultra" without the qutes and save [/COLOR][/COLOR]

[COLOR="darkred"][COLOR="darkred"][COLOR="DarkRed"]Go back to the terminal, and type: 

Sudo gedit/etc/modprobe.d/blacklist
add "blacklist tulip" without the qutes and save, then restart the system[/COLOR][/COLOR][/COLOR]!


*note: I believe this will work with any ethernet card just insert your cards driver were I inserted "smc-ultra" 

 I hope it works for you as easy as it did for me!!

---

### Post by Sparkalo on 2006-06-16
_Hardware_:
DrayTek Vigor520 (yeah, I hadn't heard of it either, but it uses the ACX100 chipset)

_How I installed Dapper_:
Installed Dapper fresh back in Flight 2, have been staying up to date since.

_Symptoms_:
Network manager 0.6.2...er...doesn't work.  I don't know why, I was too lazy to really dig into the problem.  It sees the card just fine, it sees networks just fine, but just doesn't ever connect.  It hangs on the weird little connecting icon for a minute or two and gives up.  If anyone knows how to do a thorough analysis of what's going wrong, let me know.

_Solution_:
It's not really a solution, but I just downgraded to the most recent release of 0.5.1.  Everything works just fine...except for the VPN plugin which is apparently incompatible with my version.  If anybody has a compatible version of the network-manager-vpnc plugin, please give it to me ^__^.

_Regression?_:
Yeah, breezy worked just fine (including VPN).  Heck, everything before the first release of 0.6 worked great!  Unfortunately, 0.6 doesn't work for some reason 0_o

I haven't filed a bug-report, but if anybody has the same problem with the ACX100 chipset, let me know and I'll file one, or if there's another one out there, let me know and I'll confirm it!

P.S.  I'm desperate for a solution for VPN that's compatible with network-manager, if you have any suggestions, please let me know : P.

---


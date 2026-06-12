---
title: "Easy MS VPN support"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by salsafyren on 2006-01-03
Hi,

[http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support/](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support/)

describes how to add easy setup of MS VPN.

It could  be cool to see  this natively in Ubuntu.

How do I make a  request for this to be included  in universe?

I have tried to compile the source but it failed with:

 testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build NetworkManager-pptp.  Download the appropriate package for
  from your distribution or get the source tarball at
    [ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz](ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz)

Can anybody make it work?

/Chris

---

### Post by lithorus on 2006-01-03
Pptp is already in Ubuntu and even the mppe patch is in the standard Ubuntu kernel. All I do to connect to my VPN is write "pon VPN" and it sets up everything.
Read more about it here : [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

---

### Post by can3p on 2006-01-14
No, It's just said about gui support for VPN(pptp). If it will be in next Ubuntu, it will be great, because no distro supports it well now

---

### Post by palco on 2006-04-05
I've been using the pptp-config GUI. It is good. It does the job properly. But that's just abother piece of software which needs to be installed, ran with root privilages, as another application, with lots of options, staying in the taskbar all the time/not hiding in the tray on connection, not supporting GTK or whatever and thus standing out of the hole desktop picture. :-k That's just not what you're looking for when you think of VPN connection! ](*,) 
NetworkManager seems to be just opposit. Just it! It stays in tray. It has wizards to setup connections. It has a single button for a connection once set up. Just perfect. 

But! :-| 
It suports Cisco and Opne VPN only I believe. I use VPN to connect to internet through my ISP server. There are over 400 PCs on our network. Mainly Windows PCs mainly for this very reason. It's getting just tooooo complicated when simply connecting to Internet! :( 

Come on, guys! There is a solution for pptp support in nm at [http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support) 
But I'm not a Ubuntu developer (yet :D ), I cannot compile the package. 

PLEASE! :( Someone make a package for Ubuntu. So we could simply install it and enjoy this super Lunix distro.

---

### Post by palco on 2006-04-05
[QUOTE=salsafyren]Hi,
[http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support/](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2005/11/21/networkmanager-pptp-vpn-support/)
... ... ...

I have tried to compile the source but it failed with:
... ... ...
Can any
body make it work?
[/QUOTE]

](*,) That's the point! :cry: We need a compiled .deb file! 
Is there anyone we can conact with this request?! :| I am sure the PPTP plugin developer would help if any problems accour, and I would do it myself, but it I never done it be4 and have absolutly no clue how to. F1/HELP!

---

### Post by lithorus on 2006-04-24
I got it compiled, but am having problems connecting to any vpn connection created. The item is simply just grayed out.

---

### Post by onlymee on 2006-04-25
palco, 

Hi, I'm a.j.mee, the PPTP plugin author, salsafyren got on to me by email
and I've joined your lovely forum.  For those that are possibly about to
bombard me, please bear with me as I'm a Gentoo user and my Ubuntu knowledge is limited -- mostly just installation as I always recommend Ubuntu to others and have occasionally assisted them in setting it up.

I am, as you all happy to assist you all if I can.
installer -- for all the people that want me to help then get Linux)

---

### Post by palco on 2006-04-25
[QUOTE=lithorus]I got it compiled, but am having problems connecting to any vpn connection created. The item is simply just grayed out.[/QUOTE]
WOW! :o \\:D/ Halleluya! =D> Thank you so much! I copied this post for Antony J Mee the author of the plugin. He may be aware of the reason, or just require more info. But it started! We've got something to go with, to work on! :o Thank you.

Ops! Here he is Himlef. Welcome here!

---

### Post by onlymee on 2006-04-25
So lithorus,

Which version of Network Manager are you using? And are you using PPTP from the tarball on my blog, or the CVS version?

I was using the tarball version as a stop gap fix (or the commandline pon method mentioned before)

------------------
Background (and the CVS version):
  The tarball version uses all that static config stuff and was tested with NM 0.5.x (around the time of the blog entry).  The NM gang understandably didn't like all the goofing around that had to be done to get the dhcp config info back into NetworkManager and so I came up with a new version that actually has a PPPD plugin to capture the information and send DNS etc. info to NM directly via DBUS.  It was also to be capable of providing the authentication credentials directly from NetworkManager.

Current state in the CVS version is that it had some occasional seg. fault issue on disconnect that could tear down the NM daemon too (perhaps DBUS related... pppd plugin + DBUS seems to be a strange mix!)

Also: the hooks for the authentication info are written into the pppd plugin, but the DBUS messages to request that information from the NM applet have not been written so the auth information is hard coded in the source!

Development stopped while I try to get my thesis finished and also because I have been without a laptop (busted) to test with/develop on.  My new one may arrive 14:00 today (gambled on Acer 8204 TravelMate eek!)

---

### Post by lithium on 2006-04-25
[QUOTE=onlymee]I am, as you all happy to assist you all if I can.[/QUOTE]

Hi! because my university uses pptp for their VPN, I wanted to use the NM plugin, too. There was even an effort to build a .deb package, but the result was a non-working version because noone got the plugin working. If you could assist me in building/installing/configuring the plugin, i'm sure we could finish the .deb package for anyone to use. Can I contact you in private?

---

### Post by onlymee on 2006-04-25
By all means contact me :-)  

I have a little very little experience building .debs (and only for Debian) but if you can do that bit we could have it up and running quite quickly.

---

### Post by lxndr on 2006-04-25
[quote=lithium]Hi! because my university uses pptp for their VPN, [/quote]
 
So does mine, they've given me some options to use while connecting, but results are mixed. Could you specify what kind of connection parameters you have to use? Mine (Tilburg University, NL) are:
 
[SIZE=2]Interface name UvT-VPN
IKE DH Group dh2
Perfect Forward Secretcy nopfs
IPSec gateway [[COLOR=#0000ff]137.56.127.10[/COLOR]]("http://137.56.127.10/")
IPSec ID ******
IPSec secret *********[/SIZE]
 

[SIZE=2]Funny thing is that when i check the Universitys manual for setting up cisco connection under WinXP (same as what vpnc should be doing) they give login info completely different from above, but thats a whole other story...[/SIZE]

[SIZE=2]So my financial support and everlasting friendship to whoever fixes this stupid Linux shortcoming...!:mrgreen: [/SIZE]

---

### Post by onlymee on 2006-04-25
Are they using Cisco (vpnc) or PPTP (this thread aka M$ VPN)?

My Uni uses PPTP VPN too!  That's how I got on to this in the first place :-)

I hated having moving from wired to wireless at uni / wireless at home... NetworkManager rocks :-)

---

### Post by lithorus on 2006-04-25
[QUOTE=onlymee]So lithorus,

Which version of Network Manager are you using? And are you using PPTP from the tarball on my blog, or the CVS version?

I was using the tarball version as a stop gap fix (or the commandline pon method mentioned before)[/QUOTE]
I used the currently packaged NM 0.6.1. The only thing I had to change was adding :
```
#include <NetworkManagerVPN.h>
```(or something like that, you get the idea :))
My first problem was that NM for the VPN framework to work, you had to have the LAN connection setup through NM and I use a static ip for my laptop. Something that NM doesn't support in Ubuntu (but does reportedly in FC).

I did some nasty work-around and I could use the VPN links. But they would not connect (something about the MPPE stuff). I'm going to take a closer look at it, but there seems to be some problems with the configuration dialogs. When you try to eg. disable MPPE it will not be changed in gconf.

I will be more than happy to help. I just packaged it with checkinstall.

---

### Post by lithorus on 2006-04-27
I finally got it to connect, but there are still some problems with communicating with dbus to get the ip configuration so it just diconnects again.

---

### Post by Pygi on 2006-04-28
Hi,

seems like n-m caused much of effort around it :)
Anyway, if I can be of any help around n-m,
debian packaging or anything else, please
don't hesitate to contact me, and
I'll be more then glad to help.

Also, I hope you understand this isn't going to come into
Dapper.

Kind regards,
Mario

---

### Post by palco on 2006-04-28
[QUOTE=Pygi]Hi,

seems like n-m caused much of effort around it :)
Anyway, if I can be of any help around n-m,
debian packaging or anything else, please
don't hesitate to contact me, and
I'll be more then glad to help.

Also, I hope you understand this isn't going to come into
Dapper.

Kind regards,
Mario[/QUOTE]

Hi, Pygi. I stired this up a little, but I am not any kind of developer or packager. I am generally very new to Ubuntu and linux, just that I am trying to promote Ubuntu here in my neighborhood and since all ISPs use PPTP for authentication, it gets almost impossible to get people to switch to Ubuntu (specially in the country where Microsoft is getting new customers by simply allowing to use illegal copies of Windows still untill now. i come from Ukraine) as long as they have to type pon/poff in terminal. :( But It's such a shame to waste the chance of using such a great and mature distro as Dapper. Well, you know it is great timing now to promote Linux that as Vista coming, but not yet, good level of development of linux dectop wice ..... So I kept asking in forums and @ launchpad to package a.j.mee's nm pptp support plugin. I couldn't do it myself as I never done, I don't have dapper yet. 

So what I actually was going to say, was : WELCOME! Thank you very much for answering to the request. And at least wham what I know though the name of the thread does not obviosly show it, but it is most current mn pptp support plugin dev/package/discuss place on the net at the moment. I would greatly appreceate your support to a.j.mee and lithorus, just like thouthands of others I am sure. 

P.S.: Oh, you have no idea how this every post like "I got it compiled, but am having problems connecting to any vpn connection created", or "I finally got it to connect..." (well, but...) makes my blood preasure go up! Just the way it did when I finally found info about nm pptp support existing at all! :p I know it may be still a long way till it's finished, but, guys, thank you so much for all your great work generosness to help so many! =D>

---

### Post by Pygi on 2006-04-28
Hello people,

we've packaged 0.6.2, and got it into Main ages ago :)
So let's start with the questions :)

Anyone tried running it with 0.6.2?

Kind regards,
Mario

---

### Post by lithorus on 2006-04-29
[QUOTE=Pygi]Hello people,

we've packaged 0.6.2, and got it into Main ages ago :)
So let's start with the questions :)

Anyone tried running it with 0.6.2?

Kind regards,
Mario[/QUOTE]
I've only used it with 0.6.2.

---

### Post by palco on 2006-05-07
[QUOTE=lithorus]I finally got it to connect, but there are still some problems with communicating with dbus to get the ip configuration so it just diconnects again.[/QUOTE]
Is it the authentication information which is being comuincated? (In case it is possible to putt it in the NM pptp dialog) If so, would placing manually this info in *secrets file help? 
I mean, can it be used any yet?

---

### Post by lithorus on 2006-05-07
[QUOTE=palco]Is it the authentication information which is being comuincated? (In case it is possible to putt it in the NM pptp dialog) If so, would placing manually this info in *secrets file help? 
I mean, can it be used any yet?[/QUOTE]
No, it's when the connection is made and it have to give the network information back through dbus to NM, which in turn will acknowledge the connection as being established. I think it's due to some API changes between, 0.5.x (which the module was first intended for) and the new 0.6.2.

---

### Post by crb on 2006-05-11
Pardon my confusion, but is there a .deb of the plugin for PPTP actually available yet? Some of the posts above talk like there is.

---

### Post by lithorus on 2006-05-12
[QUOTE=crb]Pardon my confusion, but is there a .deb of the plugin for PPTP actually available yet? Some of the posts above talk like there is.[/QUOTE]
Not really there was one which was built for NM around version 0.5.2. It needs some fixings to work with the newer 0.6.2.

---

### Post by onlymee on 2006-05-12
[QUOTE=lithium]Hi! because my university uses pptp for their VPN, I wanted to use the NM plugin, too. There was even an effort to build a .deb package, but the result was a non-working version because noone got the plugin working. If you could assist me in building/installing/configuring the plugin, i'm sure we could finish the .deb package for anyone to use. Can I contact you in private?[/QUOTE]

Now I have my new laptop (my Uni also used PPTP for wireless auth.) I tried the otherday with the newer CVS version the one with the PPPD plugin that aims to get the info straight from NM rather that needing all the config info stuff.  It seemed to work for me straight away (though I admit it requires one's password in the source code at present as the DBUS requests are not yet complete)  I would be more interested in getting that version working as the NM crew are then willing to package it with NM itself.  Would you be interested in giving it a quick try?  It used to have various seg fault issues but they seem to have disappeared and I could perhaps now implement the DBUS stuff for the user credentials.

---

### Post by lithorus on 2006-05-15
Just found something interesting...
While I was fixing a problem with samba and adding a third party repository, it also had the network-manager-pptp package version 0.6.2 aswell. Haven't tried it yet, but will when I get home.

Here's the repo :
> deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) dapper main

---

### Post by palco on 2006-05-15
[QUOTE=lithorus]Just found something interesting...
While I was fixing a problem with samba and adding a third party repository, it also had the network-manager-pptp package version 0.6.2 aswell. Haven't tried it yet, but will when I get home.

Here's the repo :[/QUOTE]
I am not quite getting it. Looks like it is Antony's plugin .... 
So I would love to know if this package already works..

---

### Post by can3p on 2006-05-15
I've installed the package and now nm-vpn-properies allows to add a tunnel. But how can I launch it? Can I do it, if I have no wi-fi? nm-applet doesn't show any vpn tunnels, it says: "No network devices have been found", but "sudo pon" works great

---

### Post by lithorus on 2006-05-15
[QUOTE=palco]I am not quite getting it. Looks like it is Antony's plugin .... 
So I would love to know if this package already works..[/QUOTE]
It doesn't seem to work quite well yet. You can configure the VPN connections, but they don't show up at all in the list of availible connections.

Edit:
Anyway it seems to be part of the cvs tree, so it'll probably work someday :)

---

### Post by lithorus on 2006-05-15
[QUOTE=can3p]I've installed the package and now nm-vpn-properies allows to add a tunnel. But how can I launch it? Can I do it, if I have no wi-fi? nm-applet doesn't show any vpn tunnels, it says: "No network devices have been found", but "sudo pon" works great[/QUOTE]
NM VPN depends on another network connection setup by NM. So if you have configured your LAN in /etc/network/interfaces (or by the Ubuntu GUI System -> Administration -> Networking) it won't let you connect to them. You have to comment all the eth* devices in your /etc/network/interfaces to let NM take over the configuration. If you need a statically configured LAN, it's a no-go (atleast for now in Ubuntu).

Edit:
comment, not uncomment :)

---

### Post by can3p on 2006-05-16
[QUOTE=lithorus]NM VPN depends on another network connection setup by NM. So if you have configured your LAN in /etc/network/interfaces (or by the Ubuntu GUI System -> Administration -> Networking) it won't let you connect to them. You have to uncomment all the eth* devices in your /etc/network/interfaces to let NM take over the configuration. If you need a statically configured LAN, it's a no-go (atleast for now in Ubuntu).[/QUOTE]


My English is rather bad, and I didn't understand all your answer.
You say, that I can't use nm, when LAN interface is configured in /etc/network/interfaces, and you say that I need to uncomment all eth* settings to let nm work, but all the intefaces there are uncommented. 

So I can't use nm vpn support without wifi? If it is so, it's bad, very bad.

---

### Post by lithorus on 2006-05-16
[QUOTE=can3p]My English is rather bad, and I didn't understand all your answer.
You say, that I can't use nm, when LAN interface is configured in /etc/network/interfaces, and you say that I need to uncomment all eth* settings to let nm work, but all the intefaces there are uncommented. 

So I can't use nm vpn support without wifi? If it is so, it's bad, very bad.[/QUOTE]
No, I meant that you have to have all the eth* settings commented, not uncommented. The things is that NM can only have 1 connection up at any time. Which means that if you are connected through your wifi connection, it'll disable the LAN connection.

Either way it'll need one of them up to let you connect to a VPN connection.

---

### Post by Behel on 2006-05-17
Hi,

Im not an expert of wireless networking and Im trying to use ubuntu to connect to the wireless network of my uni.
I've managed to setup my wireless card (Netgear WG511 v2 made in China) and Im using Wifi Radar to setup my connection. So far I am connected to the wireless network but can't really use it since every time I open my web browser, I have the same page saying:
1. You are connected to the Wireless LAN service
2. However you are not yet connected to the VPN service so you are seeing this message.
3. There are 2 methods: VPN client or 802.1x/WPA

So my questions are: how to set up easily a VPN connection (I couldn't decide whether or not this thread has solved the problem of VPN connection) or a WPA connection?
In wifi radar app, I can choose to use WPA but then it ask for a driver. Which one is it?

help

---

### Post by onlymee on 2006-05-17
[QUOTE=Behel]
1. You are connected to the Wireless LAN service
2. However you are not yet connected to the VPN service so you are seeing this message.
3. There are 2 methods: VPN client or 802.1x/WPA

So my questions are: how to set up easily a VPN connection (I couldn't decide whether or not this thread has solved the problem of VPN connection) or a WPA connection?
[/QUOTE]

HI Behel, this is a bit off topic for this thread but I'll try to assist.

First, IF you were to choose the VPN method, you would need to know what kind of VPN it is eg. Cisco IPSEC, PPTP ('Windows VPN'), ... The latter PPTP is what this thread is about.  Often the only way to tell that it is PPTP is that the provided instructions for connecting just use the standard Windows 'connect to a VPN' tools.  So, if you HAVE TO use PPTP as many of us do,
then this thread is the right place to be.

BUT... If you can use WPA instead, I'd suggest you use that! I must admit tat what you say seems a little strange as I do not know a way to have open wireless+VPN and WPA via the same routers... I'll just have to accept it's possible.   Why should you choose WPA? Well, the VPN thing was really just a  quick hack that various sites used because WPA wasn't quite ready yet!  WPA is supported out of the box by NetworkManager (so long as your card and driver support it).  It will also manage the connection automatically without the need to start a second 'VPN' connection once the wireless has started.  Finally WPA should be a tiny bit faster since it is mostly done in dedicated hardware and has one less level of protocol jiggery pokery.

[QUOTE=Behel]
In wifi radar app, I can choose to use WPA but then it ask for a driver. Which one is it?[/QUOTE]

wifi radar app?  I'm only really familiar with NetworkManager (this thread).
As for a driver, do you mean:
       WPA 1  vs. WPA Personal  vs. WPA Enterprise?
Which one is a question for your wireless provider.  If it's one of the first 2 you'll need to know some kind of secret key.  If it's the latter, then you'll need a certificate or some kind of login credentials.

PS. I use WPA Personal at home, and the GF's laptop with a NetGear WG511 v1 works fine (in Windows though) haven't tried her adapter in Linux.

---

### Post by Behel on 2006-05-17
Thank you very much Onlymee,
[QUOTE=onlymee] PPTP ('Windows VPN'), ... The latter PPTP is what this thread is about.  [/QUOTE]

Yes after investigation, the vpn connection is PPTP...

[QUOTE=onlymee] I must admit tat what you say seems a little strange as I do not know a way to have open wireless+VPN and WPA via the same routers... I'll just have to accept it's possible.[/QUOTE]

Don't worry and keep your beliefs! There are indeed two concurrent wireless networks, one using VPN and the other WPA. I first tried to setup a WPA connection but I couldn't manage how to make it works although I found the necessary certificate... I don't know where to specify it.
I then tried to set up a VPN connection. I installed the pptpclient and pptpconfig from [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) and configured it. Well I tried again cos it didn't work in the end... So I will sadly not take a linux laptop when I travel and when I need connection everywhere I want. Hopefully in few years.

I'll try again when I'll have some time.

---

### Post by onlymee on 2006-05-17
[QUOTE=Behel]Well I tried again cos it didn't work in the end... So I will sadly not take a linux laptop when I travel and when I need connection everywhere I want. Hopefully in few years.

I'll try again when I'll have some time.[/QUOTE]

PPTP is a little interesting in Linux, mostly because it involved patented Microsoft protocols.  The WPA stuff should be pretty straight forward though.
Have you tried NetworkManager or are you using something else?

I too travel all over the world and have been very pleased with NM, it seems to handle most things.  

ALternatively, if you want to use some wpa_supplicant based tool that requires manual configuration, then there is some info where to put the certificates and how to configure wpa_supplicant under "configuration files" here: 
   [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)
there's and example config using MSCHAPv2 with a certificate:
  [http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/ieee8021x.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/ieee8021x.conf?rev=HEAD&content-type=text/plain)
And one using a completely certificate based method:
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/wpa2-eap-ccmp.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/wpa2-eap-ccmp.conf?rev=HEAD&content-type=text/plain)

---

### Post by onlymee on 2006-05-30
You may all be interested to know I have update the PPTP plugin in CVS.

The reason I've been a bit stagnent on this was that I couldn't get PPTP to connect and sent data (even using it directly!)  It turns out that on my Gentoo box the mppe-mppc use flag which applies the mppe-mppc patch to pppd IS NOT compatible with the ppp_mppe support in kernels >= 2.6.15. Infact the necessary ppp_mppe support is in plain old unpatched pppd >= 2.4.3.  I was trying to use a patched pppd with at regular 2.6.16 kernel.  The result is some thing which connects but then won't send any information over the link!

Two issues have been fixed in the code.
    1) The segfault when a connection has been established
    2) Uses the "require-mppe" option rather than the "mppe required" option
        associated with the mppe-mppc patched pppd!

Please let me know if any of you have more luck with it.

---

### Post by lithorus on 2006-05-31
[QUOTE=onlymee]You may all be interested to know I have update the PPTP plugin in CVS.

The reason I've been a bit stagnent on this was that I couldn't get PPTP to connect and sent data (even using it directly!)  It turns out that on my Gentoo box the mppe-mppc use flag which applies the mppe-mppc patch to pppd IS NOT compatible with the ppp_mppe support in kernels >= 2.6.15. Infact the necessary ppp_mppe support is in plain old unpatched pppd >= 2.4.3.  I was trying to use a patched pppd with at regular 2.6.16 kernel.  The result is some thing which connects but then won't send any information over the link!

Two issues have been fixed in the code.
    1) The segfault when a connection has been established
    2) Uses the "require-mppe" option rather than the "mppe required" option
        associated with the mppe-mppc patched pppd!

Please let me know if any of you have more luck with it.[/QUOTE]
This was excactly the issue I had. Alot of the options seemed to have been hardcoded. Checking/unchecking the mppe option didn't really do anything from what I could see.

Also which version of dbus do you use? There seems to be some issues with how it communicates back and forth with dbus, but that could just aswell be contributed to the different versions of pppd.

---

### Post by lithorus on 2006-06-01
I tried checking out the latest CVS but didn't see many changes to the pptp plugin. It still uses the "mppe required" option and it's still including files from pppd 2.4.3 which is inside the NM-pptp source.

---

### Post by evaso on 2006-06-01
as you can see from [cia network-manager log]("http://cia.navi.cx/stats/project/gnome/NetworkManager") this issue seems solved actually:

    * fixed segfault on acquiring IP4Config info
    * use "require-mppe" option instead of "mppe required" which was associated with the mppe-mppc patch rather than the mppe included in pppd >= 2.4.3 and kernel >= 2.6.15

---

### Post by elamericano on 2006-06-02
I tried to get this working with:
network-manager_0.6.2-0ubuntu7linux2go2
network-manager-pptp_0.6.2-0ubuntu0linux2go1
pptp-linux_1.7.0-1ubuntu1

It does well at home with WPA2-PSK, but has problems getting my desired AP in the scan list at work (>25 APs), so I haven't tested WPA2-TLS. I can connect with wpa_supplicant.

Anyway, I configured a vpn connection and put the password in /etc/ppp/chap-secrets (*   64.233.187.99   "reddog"), but it prompts me for a password anyway. I enter the right password and it immediately returns a login failure. Ethereal shows that no packets went out.

Is there a version that doesn't prompt. Maybe I'm caught between a version that used to work and a new feature. Anyone have this working?

---

### Post by elamericano on 2006-06-04
I set up my own /etc/ppp/peers/company file and connected with "pon company" Is there a particular remotename that I need to use in /etc/ppp/chap-secrets - or some other secret setting not in the instructions -  for this to work with network-manager-pptp?

---

### Post by lithorus on 2006-06-04
[QUOTE=elamericano]I set up my own /etc/ppp/peers/company file and connected with "pon company" Is there a particular remotename that I need to use in /etc/ppp/chap-secrets - or some other secret setting not in the instructions -  for this to work with network-manager-pptp?[/QUOTE]
The above method does not work with network-manager-pptp. It uses gconfd to store it's configuration.

---

### Post by lithorus on 2006-06-04
[QUOTE=onlymee]You may all be interested to know I have update the PPTP plugin in CVS.

The reason I've been a bit stagnent on this was that I couldn't get PPTP to connect and sent data (even using it directly!)  It turns out that on my Gentoo box the mppe-mppc use flag which applies the mppe-mppc patch to pppd IS NOT compatible with the ppp_mppe support in kernels >= 2.6.15. Infact the necessary ppp_mppe support is in plain old unpatched pppd >= 2.4.3.  I was trying to use a patched pppd with at regular 2.6.16 kernel.  The result is some thing which connects but then won't send any information over the link!

Two issues have been fixed in the code.
    1) The segfault when a connection has been established
    2) Uses the "require-mppe" option rather than the "mppe required" option
        associated with the mppe-mppc patched pppd!

Please let me know if any of you have more luck with it.[/QUOTE]
Btw. it seems that the plugin doesn't compile anymore, missing a file called "static_credentials.h" and it's not in the cvs tree.

---

### Post by elamericano on 2006-06-04
[QUOTE=lithorus]The above method does not work with network-manager-pptp. It uses gconfd to store it's configuration.[/QUOTE]
Thanks, I was trying to show that I otherwise have all the right versions and configurations to connect to an MS PPTP server.

I suppose I should restate my original question: Does the network-manager-pptp plug-in available in the linux2go repository (network-manager-pptp_0.6.2-0ubuntu0linux2go1) work? Or am I wasting my time?

---

### Post by lithorus on 2006-06-04
[QUOTE=elamericano]Thanks, I was trying to show that I otherwise have all the right versions and configurations to connect to an MS PPTP server.

I suppose I should restate my original question: Does the network-manager-pptp plug-in available in the linux2go repository (network-manager-pptp_0.6.2-0ubuntu0linux2go1) work? Or am I wasting my time?[/QUOTE]
No, it doesn't seem to work. Atleast not when using pppd 2.4.4. The new changes done in CVS are versioned NM 0.6.3.

---

### Post by can3p on 2006-06-22
I found network-manager useless at this time, because it doesn't support static ip addresses at this time, and I can't get write network settings through it. If nm will support it, it wil be fully usable.

---

### Post by elamericano on 2006-07-24
Does this plugin work for anybody?

I've tried HEAD from CVS, but invoking the VPN profile and entering username/password does not do anything.

---

### Post by crb on 2006-08-19
Download a [new NetworkManager PPTP plugin package for Dapper]("http://craig.dubculture.co.nz/blog/2006/08/19/networkmanager-pptp-plugin-one-ubuntu-package-hold-the-pepper/"), built against some nice shiny new CVS code that onlymee has worked on for me!

Comments welcome on my blog please - I'm trying to get this through REVU for possibly inclusion in Edgy.

---

### Post by pangloss on 2006-08-22
That's great news. What's at issue for getting this into Edgy?

---

### Post by Wilb on 2006-09-11
> **crb said:**
> Download a [new NetworkManager PPTP plugin package for Dapper]("http://craig.dubculture.co.nz/blog/2006/08/19/networkmanager-pptp-plugin-one-ubuntu-package-hold-the-pepper/"), built against some nice shiny new CVS code that onlymee has worked on for me!

Comments welcome on my blog please - I'm trying to get this through REVU for possibly inclusion in Edgy.

Works perfectly, absolultely legendary - thanks loads! :biggrin:

---


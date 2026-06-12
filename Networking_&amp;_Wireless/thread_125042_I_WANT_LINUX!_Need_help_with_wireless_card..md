---
title: "I WANT LINUX! Need help with wireless card."
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by solidus on 2006-02-02
I've gone through a few docs and such to find out a way to get my ZyXEL Zyair G-302 wireless PCI card to work. However, due to my lack of understanding linux, I've been left in the dust.

So here is what I got:

ZyXEL Zyair G-302
Ti ACX-111 54Mbps Wireless
ubuntu (gnome)
(I can get a connection through eth0-so I can get all the updates, etc.-, but I want to have my computer hooked up through wireless)

Could someone please guide me through the steps to get this to work? Start off from just after ubuntu finishes installing as I type my username/pass for the first time... if that helps at all...

I really want to use linux, the only thing preventing me is the lack of internet.

---

### Post by towsonu2003 on 2006-02-02
First, check to see whether you got it recognized out of the box: 
System > Administration > Networking . If it is there, you can configure it from there. 

If it is not, check out this: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper) You'll need some time, patience, reading, and windows drivers (you'll see how to find drivers in the link as well). 

Ndiswrapper is a tool that uses windows drivers to make wireless work in linux... hopefully, it will work for you.

Oh, also, you might want to search for your card "Ti ACX-111" in the forums in the meantime (while reading the wiki).

---

### Post by az on 2006-02-03
[QUOTE=solidus]I've gone through a few docs and such to find out a way to get my ZyXEL Zyair G-302 wireless PCI card to work. However, due to my lack of understanding linux, I've been left in the dust.

So here is what I got:

ZyXEL Zyair G-302
Ti ACX-111 54Mbps Wireless
ubuntu (gnome)
(I can get a connection through eth0-so I can get all the updates, etc.-, but I want to have my computer hooked up through wireless)

Could someone please guide me through the steps to get this to work? Start off from just after ubuntu finishes installing as I type my username/pass for the first time... if that helps at all...

I really want to use linux, the only thing preventing me is the lack of internet.[/QUOTE]
I just bought a similar device.  Are you sure it is the acx111 chipset?  Is that from the device manager?

---

### Post by solidus on 2006-02-05
azz: I did lspci and it says:

0000:01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Inter face

Maybe they changed the chipset?

Alright, towsonu2003, I'll give it a try! (fingers crossed)

---

### Post by solidus on 2006-02-05
Okay, so here is how the first attempt went. I installed ndiswrapper-utils and ndisgtk, according to the directions on the wiki page. Then I went to System>Administration>Windows Wireless Drivers. Using the drivers from my windows installation (couldn't find them on the provided cd) I put them into the home directory, directed Windows Wireless Drivers to the .inf file. In the little window it says,

tnet1130
Hardware present: Yes

Then I go, System>Adminstration>Networking and hit the properties for wlan0. After hitting 'enable this device' and plugging in the info and clicking ok, it proceeds to show a loading bar thing. Then I clicked ActivateThen for the wlan0 it says

Wireless connection
The interface wlan0 is active.

However, when I go into Network settings the wlan0 doesn't appear to be working. The configure button is unclickable too... does this mean the windows driver won't work? Is there another driver I might try? I looked at the ndiswrapper wifi driver, [here.](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#Z) list and (of course) mine isn't listed. But I looked at the Zyxel G-162 802.11g Wireless CardBus Card that also has the Ti ACX-111 chipset, found the matching pciid and it doesn't provide any link, just to use the provided windows driver.

SOMEBODY HELP!!!!

---

### Post by solidus on 2006-02-05
Also, I found on another thread here to do

* sudo ifdown wlan0
returned:
"ifdown: interface wlan0 not configured"

and..
* sudo ifup wlan0
returned:
"Ignoring unkown interface wlan0=wlan0."

I'm not sure what this means.

---

### Post by solidus on 2006-02-05
As you will probably be able to tell, I am new to linux.

I found out that I need to edit the interfaces thing in etc/network/ ; however, when I open it up it says read-only and when I right-click>Properties it says, "You are not the owner, so you can't change these permissions." and "File Owner: root" and "File group: root". I am logged in as the account you create when you install it, which from what I gather isn't root. So how do I edit this file?

Thanks!

---

### Post by bscbrit on 2006-02-05
You have to have root permissions - which in Ubuntu means you prefix commands with 'sudo'  e.g.

sudo gedit /etc/network/interfaces

See this link for more: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bscbrit on 2006-02-05
This is my interfaces file, which sets up my wifi card and uses WEP 104( 128 ) bit.

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo wlan0
allow-hotplug wlan0
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid bscbritnet
wireless-nick spare
wireless-channel 6
wireless-mode managed
wireless-ap 00:13:46:9E:FF:FF
wireless-key1 aa11bb22cc33dd44ee55ff6600
wireless-defaultkey 1
wireless-keymode open


---

### Post by batty505 on 2006-02-05
Hey Folks
similar deal here. trying desperately to rid myself of M$ products. 
I have a linksys 54G card and cant get ubuntu to see it.

Ive downloaded and installed ngtk and ndiswrapper. I get the window wireless drivers but when I put try to open the inf file with ndiswrapper nothing happens?

should I have the card in when I do this? Ive tried it both ways, with and without the wifi card in.

ive googled it with ndiswrapper, ngtk, even wine to try to open the exe, nothing. 

I really like this distro, and hope the dev team can find an easier way for noobs to install drivers..

Please advise.

mike

---

### Post by batty505 on 2006-02-05
Oh 
sorry, I forgot to mention that when I do try to open the inf file, 
i also get a msg sometimes saying I need to be in root or sudo? mode.

Please advise
Mike

---

### Post by bscbrit on 2006-02-05
See my #8 in this thread, please.

---

### Post by bscbrit on 2006-02-05
batty505

Please use this WIFI troubleshooting guide to identify where the problem is:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

and this to help you with ndiswrapper:

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

---

### Post by solidus on 2006-02-05
So I edited the interfaces file like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo wlan0
allow-hotplug wlan0
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

iface wlan0 inet dhcp
wireless-keymode open
wireless-mode managed
wireless-nick linux_ubuntu
wireless-essid ACTIONTEC
wireless-channel 9
wireless-key1 1a2b357fc9

```

Still doesn't work. I went to Network Tools and it says:
(I can now click the configure button... I hope that is a good sign.)

Interface Information
Hardware address: not avaliable
Multicast: ''
MTU: ''
Link Speed:
State: ''

But it is recognizing the device in System>Administration>Networking

Any ideas?

Thanks

---

### Post by psk on 2006-02-05
I had a similar problem, found the following somewhere (can't remember where). Apparantly acx drivers may already be installed (some very old ones). Check by executing the following in a terminal (you may have to "sudo")

find /lib/modules/`uname -r` -name "*acx*"

if any are found then move them out

find /lib/modules/`uname -r` -name "*acx*" -exec mv {} /root \;

Also, you may want to try 

iwconfig

this should list details of your wireless setup

iwlist wlan0 scan

should show details of supported functionality

---

### Post by bscbrit on 2006-02-05
Solidus
If you look back in this thread to post #9 you can see how I set up my working interfaces file.  You haven't selected a default key, nor have you given your card any gateway or DNS servers, as far as I can tell.
Secondly, I do not think that the Network Configuration GUI works with wireless cards.  I know that it looks like it should, but I have not had any success with it. Do it from the command line and you will soon have a connection!

---

### Post by solidus on 2006-02-05
bscbrit: sorry, forgot to add the default key to the post. Also, I didn't add the gateway or DNS because I'm using DHCP... do you need those for DHCP? Alright, I'll give it a try from the command line.

psk: I'll try that too!

Thanks for the advice!

---

### Post by bscbrit on 2006-02-05
Well, I can't think how the computer would know what IP to use as the gateway if you don't tell it.  But, as I have never used DHCP, there could be some finer point that is passing me by - perhaps there is a default address that is used? - but I suspect not.

If you are going to post the contents of a file, it is _always_ best to cut and paste.  Otherwise, you might inadvertently correct the error while typing it out in your post, and no amount of people looking at it will spot what is really wrong in your file.  ;)

---

### Post by bscbrit on 2006-02-05
I also suspect that you are using your wireless AP to provide DHCP? In which case, that would be the IP to use for your gateway.  And without DNS you cannot hope to connect to anything. DNS converts your typed address (e.g. [www.ubuntuforums.org](www.ubuntuforums.org)) into the numerical values that the computer needs to establish the link.

---

### Post by solidus on 2006-02-05
Well, after removing the "old driver" and getting the interfaces file right....











I HAVE INTERNET!! WOOO! Thanks for the help! FEEL THE POWER OF LINUX!!! OHHH YEAH!

---


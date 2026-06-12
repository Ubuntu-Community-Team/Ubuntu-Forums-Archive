---
title: "Slow internet - Some page not loading at all"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by volpone on 2011-03-21
Problem with Jaunty (yes I know its old) on line. The thing is some web pages are fine and some just never seem to open up with Firefox. 

I dont seem to have any problems when I attempt to ping for instance google.

ping -c 1 google.com

PING google.com (209.85.149.103) 56(84) bytes of data.
64 bytes from ber01s02-in-f103.1e100.net (209.85.149.103): icmp_seq=1 ttl=59 time=19.4 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 19.425/19.425/19.425/0.000 ms

I also can open up for example, The Guardian (newspaper) home page, but when I try to open any page within the site it will try loading to no avail.

In general it seems to be almost 50% open and 50% will never open.

Network Connection type DSL
MAC address is blank
MTU  automatic
IPv4 automatic (PPPoE)

Luckily google and ubuntuforms both seem to load no problems.
Ive googled and searched within these pages but have not found a solution.

I really hope we can resolve this, please help

Thanks 
V

---

### Post by volpone on 2011-03-21
Ive been advised that the MAC address should not be blank,
That if I run ** ifconfig **Ill find my MAC address in the line.

[B]wlan0     Link encap:Ethernet  HWaddr 00:10:13:50:a3:43 
[/B]
00:10:13:50:a3:43 being the MAC address, I edited it into the network connection DSL wired section, unfortunately nothing seems to have improved.

But now **sysctrl.conf** opens up in a blank page. Even after I return MAC address to blank
 
One step forward two steps back  aarrrrggghhh.

---

### Post by dineshs on 2011-03-22
You may 
1)[Disable ipv6 in firefox]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can") OR
2)Set a different MTU 
a)Rightclick network manager icon-edit connections-DSL tab-select connection-edit-under wired set MTU to say 1492 or 1482 
b)Run```
sudo service network-manager restart
```
c)Connect DSL and see if there is any difference
Note:To findout an optimum MTU value see [this]("http://ubuntuforums.org/showthread.php?t=872346"))

---

### Post by volpone on 2011-03-22
Thank You dineshs

I tried your suggestions, first Firefox.
set to:** No Proxy** 
disabled **IPv6**
disable **DNS Prefetching**
Now the **MTU,** changed the values to the ones you suggested, then ran,

sudo service network-manager restart
returns
$network-manager: unrecognized service

OK First problem so far.

Then I try to optimise the **MTU**, using the information from the link:
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
Starting with **1464** I ping no problems so I increase the packet I can get to 
ping -s **65507** -c1 google.com
PING google.com (209.85.149.99) 65507(65535) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

Then I ping
ping -s 65508 -c1 google.com
Error: packet size 65508 is too large. Maximum is 65507
Okay 6557 + 28= 65535 so thats my **MTU**
This is 45 times bigger than 1464 can this be right
When I try to enter this number into Network connections it automaticly gets resized to 9990

When I run **gksudo gedit /etc/network/interfaces**
The page has only
[B]auto lo
iface lo inet loopback[/B]

But the scarest thing for me is now when I try and open **/etc/sysctl.conf**
I get **bash: /etc/sysctl.conf: Permission denied**
This was happening before your information, but a few days ago before I tried to resolve this problem sysctl with or without the (r)  was full of data.

Needless to say the internet is acting just as bad as before.

HELP

---

### Post by dineshs on 2011-03-22
Did you try a different DNS ? Can you ping the sites which are not loading? If no try this
Right-click on the NM icon- click on Edit Connections.
Select the tab,DSL-select the connection and click edit-select ipv4
method-Automatic(pppoe)addresses only
DNS [COLOR="Red"]4.2.2.1[/COLOR] click apply
(let MTU automatic)
Restart machine and see if pages are loading when MTU is automatic (default is 1500) and DNS is 4.2.2.1

> I get bash: /etc/sysctl.conf: Permission denied
Did you try ```
sudo gedit /etc/sysctl.conf 
``` Can you post the result?

> When I run gksudo gedit /etc/network/interfaces
The page has only
auto lo
iface lo inet loopback This is normal because the devices are managed by Network manager and not /etc/network/interfaces

---

### Post by volpone on 2011-03-23
Thanks again for your reply

OK I pinged yahoo.com and the answer was:

64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=1 ttl=54 time=167 ms

This kept on scrolling going up one icmp_seq=1, icmp_seq=2,.icmp_seq=3....so on.

64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=274 ttl=54 time=167 ms

I had to kill terminal as it looked like it was going indefinitely.
Then I tried to ping  nytimes.com

PING nytimes.com (199.239.136.200) 56(84) bytes of data

then hangs with out returning to my command line just a flashing prompt on a empty line again I cant type exit must kill terminal.

sudo gedit /etc/sysctl.conf Worked thank you. Heres the results

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1

I changed 
Automatic(pppoe)addresses only
DNS [COLOR=Red]4.2.2.1[/COLOR] click apply
restarted the machine, but unfortunatly no improvement.

I also noticed that when my connection breaks (which it does every 30mins or so) for that split second just before I go off line all the web pages that were hanging seem to appear.
Now can I ask a stupid question?

Whats the difference between wired and DSL

I thank you again for your patients.

---

### Post by dineshs on 2011-03-23
> I had to kill terminal as it looked like it was going indefinitely.You may add -c3 to limit the count to three ie```
ping -c3 google.com
```
> Whats the difference between wired and DSL

[http://www.superpages.com/supertips/what-is-dsl.html](http://www.superpages.com/supertips/what-is-dsl.html)
Wired connection usually refers to a local area connection (ethernet).You can use ethernet port to setup a LAN or DSL connection.A DSL connection normally requires a username and password to be sent from customer end to to the ISP end for getting authentication.Most of the operating systems are capable of doing this using PPPoE .Ubuntu users can either run *pppoeconf* command to setup the connection or use DSL tab in network manager.Also There are DSL modems capable of doing this.If you have such a modem configure it in PPPoE mode with username and password given by ISP save and reboot(modem).If you do so the connection will be always ON and you need not use DSL tab/pppoeconf command(whichever be the operating system).ie just connect ethernet cable to the modem open browser and proceed.(If the modem is in bridge mode you need DSL tab/pppoeconf)
Are you using wired or wireless? Do you have a DSL modem?Pl post the result of ```
sudo lshw -C network
```

---

### Post by volpone on 2011-03-23
Heres the results of
sudo lshw -C network


*-network:0             
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:10:13:50:a3:43
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+sr9usb driverversion=1.53+ARCHEON Semiconductor, Inc. link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:b1:34:bb:e3:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

The modem I think is DSL it has WLAN but I gave up on that along time before, Im using a LAN cable and have gave myself a DSL connection in Ubuntu.
The name of the modem is Alice WLAN 1121 made by Siemens, it seems to be only available in Germany bundled with the DSL provider Alice, I cant speak German so the only forums that comment on this modem/router are in German.
The thing is Ive had the modem running with Ubuntu for over a year and when I connect a friends laptop (Xubuntu) via the LAN cable it works fine.

Ive recently changed my computer over to Windows (shame on me I know but it was firewire issues) and have dedicated that machine for music, it will never go on line windows and internet is just not a good mix, so I know have a second PC 1GHz 500mb RAM, small hence why Im back to running Jaunty, which Im using (hopefully) for Internet and watching videos etc. I thought it would be really easy as I had everything running nice, in the last computer it was set up as DSL connection but perhaps I should have it Wired.

I hope the information makes it a little clearly.

Thank you again.

---

### Post by BruisedQuasar07 on 2011-03-29
You can connect with your router and you connect with Internet. That is good. Most people do not get that far with wifi. I suggest you get back to the beginning with your problem. Right now people have you scattered all over the place. Focus.

Most likely your problem is not an Ubuntu distro or a Linux O\S problem at all. It is a common basic wireless network problem. You connect and you have connected all along, so you do not have a problem related to MAC Address. The MAC Address, from the user point of view, only enters into the picture when you address security issues.

What you have is a network signal problem of some sort (assuming your wireless router is not defective). All wireless routers consist of at least two different components, a wired router and a wireless radio. Connect by Ethernet cable (through the wireless router) and see if you get proper speed. Then address the wireless issue. 

The most common cause of slow wireless Internet speed is insufficient signal strength reaching the computer wireless card (radio). To address that install Wicd Network Manager. Find it in your Ubuntu Software Center, under Applications". Once installed, it will appear under "Applications" > "Internet". Activate it by clicking it. An icon will appear to the left of your wireless icon. You may have to reboot for the icon to appear. Click on the icon to get a box that lists all the Networks within the range of your wifi card (radio) at the top of each listing find signal strength reaching your card, security method and channel. Look over the channels listed for networks using the same channel as you. Note your channel.

All routers come with a default channel. Routers have 11 channels, 1 through 11. Its is common for other networks channels to interfere with a particular home connection, especially when its in an apartment. If you find other networks using the same channel as yours, change your channel, in setup, to one that isn't being used by the other networks. If you have a cordless phone that operates on the 2.4GHz frequency, so do routers. Try powering off a 2.4 cordless and see if your speed increases.

Other electronics in your dwelling may interfere with wireless operation.Rather than try to idenify each one, try other, simpler measures such as trying other channels in router setup. While you're tweaking for speed, position your router in a central location and as high as posible & make sure the antenna is straight up and down. Make sure the router isn't close to metal objects such as a filing cabinet or right next to a window (A lot of the broadcast will go out the window and into the neighborhood and into the wall, instead throughout the dwelling.

The easiest and quickest thing to do is try different channels and check the results of each one. 

SECURITY problem. whether or not you or your router was connected to Internet, so long as the router was on and broadcasting the default name, punk crackers could have been working on cracking your network so they can piggyback from your Internet service. I had this problem. I would get fast speed early in the morning, when they were sleeping and slow to no speed evenings. I added two layers of security until I had full speed all the time.

The cracker leeches can drain the life from YOUR wireless connection. They can also invade & take over your computer through your wireless router. Chances are very high that if you have a piggybacking problem, its being done by low grade punks using free wifi Network cracking software and just a few basic security measures will rid you of them.

Here are a few quick and easy steps to take now. You connect so reset the name of your network and turn off broadcasting. Punks will figure the network is gone. Never leave a router on the default name. This advertises for the router maker but it also tells punks what router you use. Crackers actually collect and post local lists of network names and basic data about each one on Internet.

Each router has a default name and password that lets owners into setup. change them. Don't let anyone convince you that you need an expensive wireless router. I've set up a lot of people with $15 to $18 TP-Link WR340G routers that work just fine for them. You do not want a hotshot router for home use. Anyone who knows anything about radio knows that radio electronics is the minor aspect of reception and broadcasting. Basic antenna science is everything. I'm a life long Short Wave and Amateur radio hobbiest who specializes in using inexpensive, small radios to pick up broadcasts globally. A powerful $17 Alpha high range USB adaptor can more than make up for a weak signal router and a weak signal router prevents piggybacking and intrusions. 

Don't fall for BS cable company and wifi hardware maker hype that sharing an Internet connection does not noticeably affect Internet speeds. With two PCs connected by wifi, set one to downloading a linux distro torrent or streaming a movie to HDMI posted HD TV and see if Internet speed is negatively affected with the other PC.

---

### Post by isa.dsouza on 2012-10-28
I suggest, try using the terminal to open the web page directly.

sudo firefox [http://www.xxxxxxx.com](http://www.xxxxxxx.com)

I have this problem with my ISP login page only. Once logged in though everything is fine. I have complained to my ISP about the page cannot be displayed issue with their website, still awaiting a response.

---


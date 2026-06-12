---
title: "Belkin wireless g Web encryption problems"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by mannu on 2006-01-27
Hi,

I installed the belkine wirelss g PCI card. The router is a netgear Rangemax. When not encrypted, everything is rosy, get my picng and I'm online. all great. When I tehn encrypt I just cannot getting working. I've tried to edit the /etc/network/interface by adding the following but to no avail...

auto wlan0

iface ra0 inet dhcp
wireless- essid <inserted network SSID>
wireless-key  <inserted hexidecimal here>
wireless-channel  6
wireless-mode managed

No joy, can anyone help once this is running its goodbye windows

Paul Mannu

---

### Post by bscbrit on 2006-01-28
I am trying to debug precisely the same problem with my Belkin.  Insecure is OK, but any attempt to encrypt causes the link to fail.  It works under Windows XP, so I can discount a hardware problem.  This appears to be a linux/Belkin problem.  I have got the afternoon and evening to try to get this sorted so I will come back here if I find a solution.

---

### Post by mannu on 2006-01-28
Thanks,

I have been trying with several on line sugegstions. I'm focusing most of my attentions on the way the encryption is conveyed in etc/networks/interface. I'm not sure what I'm dong but things like...

hex instead of ascII
putting a hash after every fourth number eg for 64 it would be xxxx-xxxx-xx
putting an s: before an ascii text

I'm also toying with the inclusion of wireless-restricted key xxxx-xxxx-xx in the command line

All to know avail, the bummer is it works when you take it off encryption and it works under windows with encryption so the hardware is deifnitely compatible.

Hope you get better luck and plese others join if they know more,

Paul Mannu

---

### Post by Lambert on 2006-01-28
Try this.

Look for a file called RT2500STA.dat

```
sudo slocate -u
``` builds a search index for the slocate command

```
slocate RT2500STA.dat
``` 
copy this file to /etc/wireless/RT2500STA directory

the contents look like this

```
[FONT=monospace]
[[/FONT]Default]
CountryRegion=0
WirelessMode=0
TXBurst=0
TurboRate=0
BGProtection=0
ShortSlot=0
TxRate=0
PSMode=CAM

SSID=YourSSID
NetworkType=Infra
Channel=1
AuthMode=SHARED
EncrypType=WEP
#DefaultKeyID=1
Key1Type=0
Key1Str=YourKeyGoesHere
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
#RTSThreshold=2312
#FragThreshold=2312
PSMode=CAM

``` 
Add the information for you network then restart networking

```
sudo invoke-rc.d networking restart
``` 
Now try to connect.

pullef from [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500)

---

### Post by mannu on 2006-01-29
Would like to say I worked this out but a friend took it from his directory

i edited etc/network/interface file so it looks like this

This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto eth0
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0


auto ra0

iface ra0 inet dhcp
wireless-essid <your ssid>
wireless-mode managed
wireless-key1 <your key don;t space them>
wireless-defaultkey1
wireless-keymode restricted
wireless-enc on
wireless-channel <your channel>
[COLOR="Red"]post-up iwconfig ra0 enc on[/COLOR]

auto ra0

the bit in red seems to be quite important but more importantly i had not appreciated that you need to tell it where you have p[laced the key i.e. key1 in my case,

Hope this helps,

Paul Mannu

---

### Post by bscbrit on 2006-01-29
Paul.  Many thanks - I have just spent the entire weekend trying all the combinations that you tried and with the same degree of failure. I was just reading through the man iwconfig page yet again to see if there was some clue.

I will have to wait until tomorrow to try out what you have said.  Its late and I don't think that I have time to do it tonight.

Thanks again

bscbrit

---

### Post by bscbrit on 2006-01-30
I have tried using your script but, for some reason, it didn't work for me.  However, I have managed by trial and error to discover a script that works reliably for me:
> 
sudo iwconfig wlan0 essid "mynet"
sudo iwconfig wlan0 nick "mylan"
sudo iwconfig wlan0 channel 6
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 ap 00:13:21:9E:98:9F
sudo iwconfig wlan0 key [1] aa11bb22cc33dd44ee55ff6677
sudo iwconfig wlan0 key [1]
sudo iwconfig wlan0 commit
sudo iwconfig wlan0 key open


\\:D/ 

Try as I might, I cannot get the equivalent combination to work in /etc/network/interfaces - it simply does not set the same settings when I ifup.  I'll keep working on this although simply running the script late in the boot sequence does the job for the time being.


EDIT:  Of course, I can remove each of the 'sudo' simply by running the script as root, or using sudo, but this is my development script and I want to play safe :D

---

### Post by bscbrit on 2006-01-30
The final solution was obvious (eventually!).  After setting up the IP address in /etc/network/interfaces for the wlan interface, I simply called the script using the following line

post-up /usr/sbin/wlansetup

It seems to work but I will give it a few hours of serious testing before I shout too loudly about it.

---

### Post by bscbrit on 2006-01-31
Another bug seems to be caused by having dhcp-client installed.  I use static IP addresses but when I installed wifi-radar it installed dhcp-client as a dependancy.  Looking through the logs showed that I was getting dhcp errors immediately after installing ndiswrapper which was affecting the 'key' settings somehow. In fact, the key was not being correctly set when dhcp-client was installed but I don't pretend to understand the mechanism that caused this problem.  When I removed dhcp-client the fault disappeared.

I will do some more investigation and see if I can work out what is happening.  So far, I have found problems when using ndiswrapper if:

I try to use the GUI to configure the wireless network key settings.

OR

dhcp-client is installed.

OR

I try to configure the wlan card using commands in /etc/network/interfaces.  The commands have to be in a separate file which can be called by /etc/network/interfaces but the commands cannot be run directly inside the interfaces file.

---

### Post by bscbrit on 2006-01-31
I am not really talking to myself in this thread - I am trying to ensure that what I do can be found by someone searching for keywords indicating the same problem that  am experiencing.  :-D

---

### Post by bscbrit on 2006-02-03
OK all my problems solved.

I found that NetworkManager was installed - don't remember doing that and, if I did, it was a big mistake.  Get rid of it, at least until the installation is complete.  It doesn't let you have a cable and wireless NIC at the same time.  Why not?  Well somebody thought it a good idea not to but that wasn't obvious.  And it also takes over DHCP to do its own thing.  So that also prevented several connections.  I don't use DHCP and prefer all static IP allocations.  However, NetworkManager decides that this isn't what you should be doing and therefore ignores what you ask for but gives you what it wants.  This sounds very "Microsoft'ish".  I'll decide what my computer does, thank you.  I know what NetworkManager is trying to achieve but to my mind it isn't yet ready for prime-time.  I'm sure that there are some out there that disagree but, hey, live with it :-D 

Next, I cannot find a good list that contains all the 'wireless-xxx' possibilities.  I was using iwconfig wlan0 commit, which my card happily accepts, but there is no wireless-commit equivalent, or none that I could find.  However, I've now managed to avoid using it so that problem has been overcome.  But while setting up my network it was throwing an error leaving my network incomplete.  When I ran iwconfig in my script it was quite happy but it doesn't like wireless-commit.

So I am now happily using my wireless network.\\:D/

EDIT:  Oh, the network configuration GUI doesn't set up WEP keys properly.  Don't know why, but I now avoid it.

---


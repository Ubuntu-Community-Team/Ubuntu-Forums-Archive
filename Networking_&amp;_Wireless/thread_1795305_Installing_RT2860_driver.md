---
title: "Installing RT2860 driver?"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by thunderloki on 2011-07-02
Hey guys,

I've been snooping around on the forums for a couple of hours now looking for a straightforward guide to installing custom wireless drivers.  I have a new Airlink101 AWLH6075 wireless card (and no ethernet connectivity.)  The Linux drivers are the RT2860 Ralink drivers in a .tar, which I have on a different computer.

So -- I'm on Server (command-line only), 64-bit, no working internet.  Btw, the wifi card works fine on my alternate boot of Windows.  wlan0 (wlan1?) is not detected during installation.

So, I know I need to:
 1. mount the usb drive I'm storing the file(s) on
 2. put those files in my local Linux directory
 3. somehow install them
 4. (disable my old ethernet connection?)
 5. enable my new wlan0 and set up dhcp and the WEP login.
 6. make it my primary connection?

I'm just guessing here.  iwconfig results in 

wlan1: IEEE802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off

and some other apparently irrelevant stuff ("lo  -- no wireless extensions" etc).

I would greatly appreciate any help I can get with any of these things.  I don't even know how to mount a USB stick in command-line...  but obviously the internet connectivity (and thus driver installation) is the major issue here and I can find out most of the other stuff on my own.  Thanks in advance,

Bodie

---

### Post by MooPi on 2011-07-02
Can you give us the results from these commands individually
```
lsmod
lspci
sudo lshw -C network
```
Also have you attempted to install the Ralink drivers yet ?

---

### Post by chili555 on 2011-07-02
I'd like to skip #1, 2 and 3. I'm lazy. In most distributions, rt2860sta is already present. The evidence is that a wireless interface has been created.> wlan1: IEEE802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:offThere is often a driver conflict with rt2800pci. Run this command:```
lsusb | grep rt2
```If you find that rt2800pci *AND* rt2860sta are loaded, blacklist rt2800pci:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800pci
rmmod -f rt2x00pci
```Rerun lsmod and be sure only rt2860sta is loaded. wlan1 should be a lot more comfortable.

Now, let's amend /etc/network/interfaces to enable connection for wlan1 and disable ethernet, eth0:```
vim /etc/network/interfaces
```Here is a rough guide:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan1
iface wlan1 inet static
address 192.168.1.118
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid <your router>
wireless-key <your WEP key>
```Now we need to provide DNS nameservers:```
vim /etc/resolv.conf
```Add one line:```
nameserver 192.168.1.1
```You did want a static IP for the server, correct? Of course, substitute your details above.

Usually, the router suffices for the DNS nameserver. Now do:```
 ifdown wlan1 && ifup wlan1
```If everything has gone well, you can ping the router and Google:```
ping -c3 192.168.1.1
ping -c3 www.google.com
exit
```If everything has not gone well, post back; the doctor is in.

---

### Post by thunderloki on 2011-07-02
Hello MooPi,

I'm writing this from a separate laptop so copying the text is kind of difficult.  Are you looking for a particular module?  (If I didn't include something, let me know what else I can add or look for!)

I didn't try to install the RT2860 driver because I have no idea how to install drivers or any of that.  That's kind of what I was looking for originally, but the output you requested seems to show that I already have the driver installed.

===== lsmod
a LOT of stuff that I'm not going to have time to copy out in detail, but the relevant ones seem to be:

rt2860sta (size) 543010 (used by) 0 
as well as
rt2800pci (size) 18535  (used by) 0
rt2800lib (size) 45181  (used by) rt2800pci
crc_ccitt 12667 2 rt2860sta,rt2800lib
rt2x00pci 14322 1 rt2800pci
rt2x00lib 49235 3 rt2800pci,rt2800lib,rt2x00pci
mac80211 290274 3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211 178528 2 rt2x00lib,mac80211
eeprom_93cx6 12725 1 rt2800pci
.
.
.
.
.

===== lspci

lspci gives me a whole list of my PCI slots.  The one in question is:
09:01.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus

There is also
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
and
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

==========  sudo lshw -C network

lshw -C network results in 3 networks, all of which are DISABLED:

Ethernet interface ....blahblah... pci@0000:07:00.0 ... eth0
Ethernet interface ....blahblah... pci@0000:04:00.0 ... eth1
Wireless interface ....blah blah
product: RT2760 Wireless 802.11n 1T/2R Cardbus
vendor: Ralink corp.
physical id: 1
bus info: pci@0000:09:01.0
logical name: wlan1
version: 00
serial: (MAC addr excluded)
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-server firmware=N/A latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:fbef0000-fbefffff

---

### Post by chili555 on 2011-07-02
> rt2860sta (size) 543010 (used by) 0
as well as
rt2800pci (size) 18535 (used by) 0
rt2800lib (size) 45181 (used by) rt2800pci
crc_ccitt 12667 2 rt2860sta,rt2800lib
rt2x00pci 14322 1 rt2800pci
rt2x00lib 49235 3 rt2800pci,rt2800lib,rt2x00pci
mac80211 290274 3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211 178528 2 rt2x00lib,mac80211
eeprom_93cx6 12725 1 rt2800pci
.Man! That's the classic conflict. Blacklist and you should be set.

---

### Post by thunderloki on 2011-07-02
Okay, sweet.  Thanks for the quick reply.  Problem is, I have no idea what you just said... lol

And once I've blacklisted, then what...?

---

### Post by thunderloki on 2011-07-02
@chili555, 

My bad, didn't see your earlier reply.  Loving the detailed response!  Much appreciated,

Bodie

PS -- How do I write ifconfig type changes permanently to disk?

---

### Post by thunderloki on 2011-07-02
Oh yeah, and I was following some directions from another thread I had followed -- apparently "service network-manager" is unrecognized.  Is that normal / problematic / how do I fix this / do I even need to?

---

### Post by thunderloki on 2011-07-02
Followed your instructions precisely.  lsusb | grep rt2 had no output; "sudo ifdown wlan1 && ifup wlan1" resulted in the error message: "ifdown: interface wlan1 not configured." and "ifup: failed to open statefile /var/run/network/ifstate".

Going to restart and see what happens.

---

### Post by chili555 on 2011-07-02
> Oh yeah, and I was following some directions from another thread I had followed -- apparently "service network-manager" is unrecognized. Is that normal / problematic / how do I fix this / do I even need to?Network Manager is a graphical front-end to ifconfig, etc. Servers have no "graphical" so no Network Manager and all its files.> lsusb | grep rt2 had no outputOops! It seems we have lost rt2860sta itself! Please do:```
sudo modprobe rt2860sta
sudo ifdown wlan1 && sudo ifup wlan1
iwconfig
```Does it show you are connected?```
wlan1     IEEE 802.11abg  ESSID:"[COLOR="Red"]your_router[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 22:24:56:22:D7:22   
          Bit Rate=[COLOR="Red"]54 Mb/s[/COLOR]   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=70/70[/COLOR]  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0
```

---

### Post by thunderloki on 2011-07-02
No it doesn't, and lsusb still greps nothing -- perhaps this is because I have the PCI version?  lspci | grep rt2 is blank but lspci | grep RT2 results in the line containing the rt2760 controller.  Sorry for the confusion!

I have changed the network/interfaces setting to
auto wlan0
iface wlan0 inet dhcp
#address 192.168.1.200
#netmask 255.255.255.0
#gateway 192.168.1.1
wireless-essid [top secret]
wireless-key [eyes only!]

I'm still having some issues though.  The ESSID is not showing my network in iwconfig -- I'll try rebooting again.  sudo ifdown wlan0 works fine, but sudo ifup wlan0 just hangs.  when I ctrl-C, ifconfig shows it back up, but I'm not sure if there's something weird happening there.

After reboot, iwconfig still shows no ESSID, no Access Point, and a Bit Rate of 1 Mb/s and a link quality of 10/100 ....  =[

---

### Post by chili555 on 2011-07-02
> auto wlan0
iface wlan0 inet dhcp
#address 192.168.1.200
#netmask 255.255.255.0
#gateway 192.168.1.1
wireless-essid [top secret]
wireless-key [eyes only!]I thought your interface was wlan1.> lsusb still greps nothing -- perhaps this is because I have the PCI version?I asked you to check in ls**mod**, not lsusb.> Rerun lsmod and be sure only rt2860sta is loadedIf your interface is wlan1, please correct your interfaces file.```
iwconfig
```

---

### Post by thunderloki on 2011-07-02
Sorry, I totally thought I had posted the reply where I explained the confusion with wlan0 / wlan1 -- I think by changing the driver it somehow changed the interface.  I did check lsmod and it is only using rt2860sta.  

sudo lshw -C network still shows the same pci port for the RT2760, it just has a different "logical name" now.

Anyway -- not too sure how to proceed here...  ifdown gives "interface wlan0 not configured" and ifup just hangs.  My /etc/network/interfaces file is updated to use wlan0 with DHCP.....  update: ifup finally finished, and ssh said "stop/waiting (newline) start/running, process xxxx"....  Not sure if that has anything to do with anything, though

---

### Post by thunderloki on 2011-07-02
I'm on the verge of reinstalling and trying this from scratch -- this is a very fresh installation.  So the steps you're suggesting are just:
1. blacklist rt2800pci via
```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800pci
rmmod -f rt2x00pci

```
2. edit /etc/network/interfaces to include wlan0
3. edit /etc/resolv.conf
4. ifdown wlan0, ifup wlan0

Correct?  And if that doesn't work....?

---

### Post by chili555 on 2011-07-02
Please run:```
iwconfig
sudo lshw -C network
```Is your interface wlan0 or wlan1? You interfaces file must match. Why are you running a DHCP address on a server? Just so you can see if it connects?> product: RT2760 Wireless 802.11n 1T/2R Cardbus
vendor: Ralink corp.
physical id: 1
bus info: pci@0000:09:01.0
logical name: [COLOR="Red"]wlan1[/COLOR]
version: 00
serial: (MAC addr excluded)
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-server firmware=N/A latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:fbef0000-fbefffff

---

### Post by chili555 on 2011-07-02
Do not reinstall. If lshw shows wlan1 then change your interfaces file to match and then:```
sudo ifdown wlan1 && sudo ifup wlan1
```That's all there is to it!!!

---

### Post by thunderloki on 2011-07-02
What I'm trying to say is, after blacklisting the rt2800 etc, the logical name of the interface changed to wlan0, so I changed my /etc/network/interfaces file to wlan0.  The reason I'm running DHCP on the server is because it's behind a wireless router -- I'm trying to have the router forward ports to it based on hostname, since the rest of the network is DHCP.  I don't suppose there's a way to do DHCP with a manual address?

iwconfig isn't showing that wlan0 is associating with the network correctly.  The SSID is given as "", the speed is 1 Mb/s and the link quality is 10/100 ... 

I posted my .../interfaces file above -- it seems like it should be set up correctly for dhcp.  Maybe I'll try with a static address...

---

### Post by thunderloki on 2011-07-02
Oh, and just now when I did a sudo ifdown wlan0, it replied with "SIOCDELRT: No such process".  What the hell ever that means.  LMAO!

---

### Post by thunderloki on 2011-07-02
Okay, trying now with static.  The SIOCDELRT error was due to a typo in interfaces.  ifup wlan0 doesn't hang any more, but it also doesn't seem to be associating with the network.  my file is as follows:

# other stuff
auto wlan0
iface wlan0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid blah
wireless-key blah

after ifdown and ifup, iwconfig is still not showing wlan0 associated with a network.  funny thing is, I'm almost positive it was associated immediately after I followed your first instructions.  maybe it had something to do with the modprobe command?

---

### Post by chili555 on 2011-07-02
> The reason I'm running DHCP on the server is because it's behind a wireless router -- I'm trying to have the router forward ports to it based on hostname, since the rest of the network is DHCP.Isn't the hostname the same either DHCP or static? The fact that all other, some or no other computers are DHCP makes not a whit of difference, just select an address that's outside the range of addresses assigned by the DHCP server in the router. If the router uses ten addresses from 192.168.1.100 to 192.168.1.109, then you can safely use 192.168.1.115 for the server.

If the IP address for the server wanders all over the place every time it boots, it's hard (not impossible) to ssh and ftp into it. Without samba, netbios, and all that MS junk, you can simply do:```
ssh -l loki 192.168.1.200
```

---

### Post by chili555 on 2011-07-02
> after ifdown and ifup, iwconfig is still not showing wlan0 associated with a network.Check syslog:```
sudo cat /var/log/syslog | grep -e wlan -e rt2
```How many characters are in your key? Ten, 53 or 6 or what?

---

### Post by thunderloki on 2011-07-02
Okay.  Weeeeellll...   it doesn't look like a static config is working either.  I'm on the verge of giving up for today.  Not sure why it wouldn't associate, since it works great on the windows partition.

nslookup times out, and ping results in destination host unreachable -- however, that's a slight improvement from "network unreachable."

---

### Post by thunderloki on 2011-07-02
I think the problem has something to do with addressing...ifdown and ifup are the only ways to refresh the connection?

---

### Post by chili555 on 2011-07-02
> ifdown and ifup are the only ways to refresh the connection?Yes, or reboot.

What did syslog say?> ping results in destination host unreachableThe router, Google or both? Did you edit /etc/resolv.conf?> I'm on the verge of giving up for today.The night is young. Take a break and let's try again later. In any case, the doctor is in.

---

### Post by thunderloki on 2011-07-02
Oops, didn't see your reply before I posted.  I'll look into it.  But for now I gotta run.  I'll check back in soon.

---

### Post by thunderloki on 2011-07-11
I have returned.

So, I did go through with reinstalling, and of course -- same problem.  The steps I followed were:

1. sudo su, blacklist rt2800, etc etc.
2. vi /etc/resolv.conf, add nameserver of gateway.
3. vi /etc/network/interfaces, add

```

iface wlan0 inet dhcp
wireless-essid blahblah
wireless-key etc

```

4. ifdown wlan0 && ifup wlan0
5. reboot
6. sudo ifup wlan0

iwconfig results in: lo, eth0, eth1, blah blah
wlan0:
Ralink STA ESSID:"" Nickname:"RT2860STA"
Mode:Auto Frequency:2.412GHz Access Point: Not-Associated
Bit Rate: 1 Mb/s
RTS thr:off Fragment thr:off
Link Quality:10/100 Signal level:0 dBm Noise level:-97 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

This wireless card does work perfectly under LiveCD and Windows 7, so... I have no idea why it's not getting the SSID from my network interfaces file....   any help would be appreciated!

[EDIT]
sudo iwlist scanning DOES list the correct network that I'm trying to log in to.  I also added "auto wlan0" to the top of my wlan0 section of /etc/network/interfaces which apparently does nothing for me.  Also, not sure if it's any help, but sudo ifup wlan0 hangs for a while before giving me
```

ssh stop/waiting
ssh start/running, process xxxx

```
ifconfig returns
```

wlan0
Link encap:Ethernet [snip]
UP BROADCAST RUNNING MULTICAST [snip]
RX packets:921[snippidy snip]
RX bytes:86626 TX bytes 0

```

and any attempted pings besides "localhost" give "Network unreachable."

---

### Post by chili555 on 2011-07-11
> iface wlan0 inet dhcp
wireless-essid blahblah
wireless-key etcI think this needs to include auto eth0:```
auto etho
iface wlan0 inet dhcp
wireless-essid blahblah
wireless-key etc
```Yours is a WEP network? How many characters in the key?

Does syslog have any clues?```
sudo cat /var/log/syslog | grep -e rt2 -e wlan
```Please refresh my memory, is Network Manager expunged?

vi, eh? Not many of us still use vi. I'm a vim man, myself. I always wanted to learn emacs but it's still on my list along with python.

---

### Post by thunderloki on 2011-07-11
Hehe, I'm not very good at it, but it is supposedly very powerful.  I uncommented my auto eth0 line, and it also includes iface eth0 inet dhcp after it, but the cable is unplugged of course.  It is a WEP network with 10 characters in the key.

Maybe auto wlan0 is a bad idea?

I don't think Network Manager comes with Server, and it is as clean an install as possible this time.  Wanted to make sure I hadn't added any ip route info.

syslog has lots of DCHPDISCOVER on wlan0 to 255.255.255.255 port 67 of various intervals from dhclient.
kernel says rt2860 is from the staging directory...
rt28xx_init, status=0....
can't create /var/lib/dhcp3/dhclient.wlan0.leases: no such file or directory...
wlan0: no IPv6 routers present...
and then basically the same messages repeated.  except the one about RT2860sta being unknown quality.

---

### Post by thunderloki on 2011-07-11
Could it be a problem where, for example, Apache2 is spamming my ports with requests and overriding the network requests?  This problem seems really weird to me.  It works perfectly in all other OSes including live Knoppix. >_<

It's just not getting that ESSID value in iwconfig...

---

### Post by chili555 on 2011-07-11
> It's just not getting that ESSID value in iwconfig...It won't until it connects.> I don't think Network Manager comes with Server, and it is as clean an install as possible this time. Wanted to make sure I hadn't added any ip route info.Correct. Once you get it set up, start it and forget it...hopefully.> Could it be a problem where, for example, Apache2 is spamming my ports with requests and overriding the network requests?I don't know much about Apache. (Insert Navajo and Ute joke here.) I guess it's possible. 

Are we sure no competing modules are loaded?```
lsmod | grep rt2
```> RT2860sta being unknown quality. Trivial, it shouldn't interfere with connection in any way. 

Are the entries in /etc/network/interfaces separated in nice neat stanzas?```
auto lo
iface lo inet loopback

auto **wlan0**
iface wlan0 inet dhcp
wireless-essid blahblah
wireless-key etc
```I see I made a mistake above with etho. It is late here and I usually like to stop at least for food and sleep! Sorry about that.

If there are letters in your WEP key, have you tried both upper and lower case? 096c7f or 096C7Fetc.

---

### Post by thunderloki on 2011-07-11
Food and sleep!?  Preposterous.  I feed upon the tears of trolls.

My interfaces file is as follows:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid MG606
wireless-key #A##AAAAA#
```

sudo lsmod | grep -i rt2 results in
```
rt2860sta #### #####
crc_ccitt #### #### rt2860sta
```

It seems counter-intuitive that a server application would interfere with IP resolution.  One problem I did notice in syslog was along the lines of: ```
Aug 16 11:37:27 lifemote ntpdate[707]: name server cannot be used, reason: Temporary failure in name resolution
``` except replace Aug 16, etc, with my own relevant data.  lifemote being my hostname.

---

### Post by thunderloki on 2011-07-11
(perhaps this is because, during install, I chose not to automatically set the system time via internet, since my internet does not work.)

---

### Post by thunderloki on 2011-07-11
One thing I am wondering is if perhaps domain name could be a problem?  I did not include a domain name but I am wondering if it is required somehow.  I'm pretty flummoxed here.  Been Googling for hours.

---

### Post by thunderloki on 2011-07-11
I am thinking that perhaps I would be better off with a static IP.  Let's see how that goes for me.

---

### Post by thunderloki on 2011-07-11
In fact... perhaps installing the typical Ubuntu GUI and all that crap will solve my problems.  Maybe that way I can use Network Manager to set everything up for me and then forget about the GUI.  Any guidance on that route would be appreciated.

:???:

---

### Post by chili555 on 2011-07-12
> ntpdate[707]: name server cannot be used, reason: Temporary failure in name resolutionThat simply means that ntpdate couldn't resolve the name in the .conf file, someting like time.clemson.edu into a IP address. Of course it couldn't resolve it; we don't yet have a connection. > I am thinking that perhaps I would be better off with a static IP. Let's see how that goes for me.So how did it go?> In fact... perhaps installing the typical Ubuntu GUI and all that crap will solve my problems.I doubt it. I suggest we look at:```
dmesg | grep -i rt2
```See if there any complaints or warnings. If you can tranfer the entire thing to a USB key, I'd like to see it, after a reboot.```
dmesg > thunder.txt
zip thunder.zip thunder.txt
```Thanks.

---

### Post by thunderloki on 2011-07-13
The static IP didn't work out for me either.  I'm about to install Desktop, but ... pardon the noob questions, but how do you transfer something to external media?  I never really understood the mount/unmount process.

---

### Post by thunderloki on 2011-07-13
(surprise) Ubuntu Desktop installer found and connected to my wireless.  Let's hope I can figure out how to install Desktop without wiping out Server XD

---

### Post by chili555 on 2011-07-13
> pardon the noob questions, but how do you transfer something to external media? I never really understood the mount/unmount process.In a server, without a GUI, I can only surmise that when you insert a USB key, it doesn't automount and pop up an icon on your desktop. I think I'd insert the drive and then run:```
dmesg
```Towards the end, you'll see that the drive was recognized as /dev/sdb or similar; if the drive has partitions, dmesg will refer to /dev/sdb1. 

In case it did automount, I'd check the place these usually automount:```
ls /media
```If it it not listed, mount it by creating a mount point:```
sudo mkdir /media/usbdrive
```Now mount the device:```
sudo mount -t [COLOR="Red"]???[/COLOR] /dev/sdb1 /media/usbdrive
```The command mount needs the file type, ext3, vfat, whatever. You can find out with:```
sudo fdisk /dev/sdb
```Here is an example:>    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1015      255752    b  [COLOR="Red"]W95 FAT32[/COLOR]Now we come to one of those Linux things you either stumble over until you find it or many years of hard experience has taught you. W95 FAT32 means, to the mount command, msdos.

So, if we wanted to mount this drive, we'd do:```
sudo mount -t msdos /dev/sdb1 /media/usbdrive
```Now we can copy our log file:```
sudo cp log.txt /media/usbdrive
```These drives are usually not terribly fast, so wait a few moments. Now we unmount the drive before we remove it:```
sudo umount /dev/sdb1
```Yes, it's umount and not unmount. If it's still busy copying, it will tell you.

---

### Post by thunderloki on 2011-07-15
Yknow, what's weird is, when I do an ```
iwconfig wlan0 ap blah blah blah MAC address of my router
iwconfig wlan0 key ########## 10-digit WEP key
iwconfig wlan0 channel 6
iwconfig
```

it shows the correct SSID, but it says ```
Encryption key:off
```.  It even has the correct signal strength and everything.  Maybe this has something to do with the problem?

---

### Post by dog-soldier on 2011-07-16
just a thought but have you tried to reboot your router and modem? 
i had to reboot mine when i first installed 11.04 on my laptop.
also when you installed did you hard wire the machine to your router?

---

### Post by thunderloki on 2011-07-17
Discussion continued at [http://ubuntuforums.org/showthread.php?t=1803635&highlight=thunderloki&page=2](http://ubuntuforums.org/showthread.php?t=1803635&highlight=thunderloki&page=2) for anyone interested.  [/thread]

---


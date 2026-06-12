---
title: "bcm4318 wireless AP using network bridge"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2011-09-26
Alright,
Here's my setup:

Dell PowerEdge 1800 running as my local router/server.  All of the wired (eth0-eth3) interfaces share internet via eth4.  I'm trying to get my wireless card to share internet as well.  It is setup as wlan0, and I am trying to bridge it to eth3 (unused, otherwise).

How do I go about allowing wlan0 to go into "master mode" and share to the rest of my house?  My /etc/network/interfaces is attached.

---

### Post by svtguy88 on 2011-10-06
No responses?  

It's got to be possible.  I amended my interfaces file, following [this thread]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")  The new one is attached.

I didn't do the "GUI method," as I've got Network Manager disabled - I'm using Webmin/the config files.  For those that don't want to read that post, it sets up wlan0 as another interface (where I will listen for DHCP clients), rather than bridging it to one of the ethernet interfaces.

When I restart the networking service, all of the interfaces come up (no errors), but I can't see the wireless network from any clients, nor can I connect to it by doing "connect to hidden network."

---

### Post by jwcalla on 2011-10-06
Based on my experience it seems that you need a software AP to put your wireless interface into master mode.  For modern linux the package that does this is hostapd.  I haven't been able to find any other way to do this.

---

### Post by svtguy88 on 2011-10-07
Thanks for the reply.  I've got hostapd installed, and, I think, configured.  The config file is as follows:  

```

interface=wlan0
driver=nl80211
ssid=test
hw_mode=g
channel=11

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=YourPassPhrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

I got this from [here.]("http://linuxwireless.org/en/users/Documentation/hostapd#Getting_hostapd")  It should allow for WPA2 authentication...

Now, after I run hostapd, iwconfig reports the following about wlan0:

```
wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

Note that it is in master mode, but not associated with any SSID.  

I can't see/connect to the network at all wirelessly.  Also, I tried running hostapd with a more simple config (no WPA,etc.), and it still isn't visible.

---

### Post by jwcalla on 2011-10-07
Try running it with the -d or -dd options to check out any possible errors or warnings.

E.g.,

hostapd -dd /my/config/file

---

### Post by jwcalla on 2011-10-07
Actually I think I needed to bring wlan0 up before I could run hostapd to get a broadcast.

For turds and giggles try as root:

```
ifconfig wlan0 inet 192.168.90.1 netmask 255.255.255.0
```

Then try to bring hostapd up and see if your clients can find your network.

---

### Post by svtguy88 on 2011-10-07
I brought wlan0 down, and then back up (inet 192.168.90.1 netmask 255.255.255.0), rand hostapd with the -dd flag, and I got basically the same result.

The terminal output of hostapd -dd is attached.

---

### Post by jwcalla on 2011-10-07
Does ifconfig show an IP address associated with wlan0?

Is your client able to see other wireless networks?

---

### Post by svtguy88 on 2011-10-09
Alright.  I dug around, and looked at my setup a bit more.  I took all of the security out of the hostapd.conf file (open authentication).  I can now see the network, but I don't get an IP from it.

Below is the output of hostapd -dd when trying to connect from my laptop:

```
STA 00:13:e8:74:92:5b sent probe request for broadcast SSID
STA 00:13:e8:74:92:5b sent probe request for our SSID
mgmt::proberesp cb
mgmt::proberesp cb
mgmt::auth
authentication: STA=00:13:e8:74:92:5b auth_alg=0 auth_transaction=1 status_code=0 wep=0
wlan0: STA 00:13:e8:74:92:5b IEEE 802.11: authentication OK (open system)
wlan0: STA 00:13:e8:74:92:5b MLME: MLME-AUTHENTICATE.indication(00:13:e8:74:92:5b, OPEN_SYSTEM)
wlan0: STA 00:13:e8:74:92:5b MLME: MLME-DELETEKEYS.request(00:13:e8:74:92:5b)
authentication reply: STA=00:13:e8:74:92:5b auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
mgmt::auth cb
wlan0: STA 00:13:e8:74:92:5b IEEE 802.11: authenticated

```

As you can see, my machine connects, but I don't get an IP.  This authentication output repeats every five seconds or so..maybe my machine isn't waiting long enough for an IP?

I think I have dhcp configured correctly...I mean, it deals out IPs to the rest of the network perfectly...

---

### Post by jwcalla on 2011-10-09
This is where our strategies diverge a bit.  I wasn't sophisticated enough to use an interfaces file and get a bridge interface working.  I kinda hacked at it all and ended up using dhcp3-server.

If you want to see how I went about it, you can check out this thread:

[http://ubuntuforums.org/showthread.php?p=11319157&postcount=2](http://ubuntuforums.org/showthread.php?p=11319157&postcount=2)

It might not be the best method... but maybe there's something there that you can pick out that'll help.

---

### Post by svtguy88 on 2011-10-10
I'll upload my most recent files after I'm done with class today.  

I am using dhcp3-server, and I *think* I have it set up right, as all of my other subnets get IP addresses perfectly.  

Thanks for all the help though, at least now I can associate with the AP.

---

### Post by svtguy88 on 2011-10-26
Okay.  It's been a while, but I took another stab at this today.  I can associate with my access point, and authenticate using WPA2, but I can't, for the life of me, get an IP address.

Originally I had the system set up to use hostapd to put my wireless card into master mode, and then just tried setting the DHCP server to listen on wlan0.  Today I tried setting up a bridge, and the brctl shows that my br0 bridges wlan0 with eth0 (a local network interface that receives IP addresses via DHCP), thinking that I could get the server to deal out IP's that way.  This method got me to the same spot I was before.

Regardless of what I do, I can't seem to get an IP address to my wireless clients.  I do have Shorewall insatlled and configured as my firewall, but I don't think that would be causing any issues (at least not yet - I'm thinking that I should get an IP address before my firewall even starts to come into play).

Anyway, /etc/network/interfaces and /etc/dhcp/dhcpd.conf are attached....

This is starting to get aggravating.

---

### Post by svtguy88 on 2011-10-27
New day, new plan of attack.

I put in a different wireless card, and I'm getting more headaches.  This card (a Realtek 8185) is, apparently, also incompatible with master mode.  I now have it set up to run in ad-hoc mode, which is giving me varying degrees of success.

I had everything up and running (I had to fool around a bit to get it working at all though - bring wlan1 down, edit wlan1 using iwconfig, and then bring it back up and restart my dhcp server).  This seemed to work.  I was able to connect, browse the internet, and access my file shares, at least for a while.  All of a sudden, all of the clients disconnected, and now I can't see the network anymore.

I tried to restart networking, and then tried bringing it all back up how I described above, but I can't get it to work now.

Also, shouldn't the changes I make to /etc/network/interfaces (such as the SSID of my ad-hoc network) automatically take effect after I run /etc/init.d/networking restart?  The reason I ask is, if I change the SSID in my interfaces file, and the restart networking, iwconfig reports that wlan1 is up with the SSID from before (no the new SSID I entered in /etc/network/interfaces).

Ughhhh......I'm about ready to start banging my head against the wall.  Why is it that this stuff can't ever just work?

---

### Post by jwcalla on 2011-10-27
I can tell you where I'm at with this.  I've given up on my USB dongle AP and will be borrowing an older wifi router from a friend until I get around to buying the router of my dreams (Cisco E4200).

I gave up because, while I was able to connect to the network from my Android, it would frequently just drop the connection, and I'd have to reconnect on Android (wifi off / on) before I could use the network again.  That wasn't too bothersome, but when I brought my HP TouchPad onto the network, all hell broke loose.  The TP would work for maybe five minutes, then bam, like clockwork, both of my mobile devices would drop from the network... and I couldn't get them back online unless I brought down and restarted hostapd.

I struggled with configurations and driver updates and everything trying to get it to work.  Eventually I gave up, plugged my dongle into Win7, installed the manufacturer's SoftAP software for creating an AP, and proceeded to watch the whole thing crash and burn worse than on linux.  I couldn't get the TP to even *connect* to the wifi AP.

So that told me everything I need to know about trying to fit a square peg into a round hole.  Sometimes it's easier to just use the right tool for the job.

Is there a way to add a wifi router to your setup?

---

### Post by svtguy88 on 2011-10-27
Hmmm.....I still just don't get it.  I mean, I know this is Linux and with it comes...well, issues, but OS X puts up a ad-hoc network and shares internet beautifully, at least with the Broadcom card.  I find it funny that your Windows access point failed too...I'd expect that to be working by now (I know it was hit and miss the last time I tried to throw up a temporary network, but that was back when Vista first came out).

I mean, the entire rest of my network runs solid.  The ad-hoc set up I had going, ran for a few hours, with no problems at all (I had two clients connected - Android and Ubuntu).  Now I can't seem to get it back up no matter what I try.  I'll mess with it more later.  Maybe I'll throw the other (bcm4318) card back in and try ad-hoc on that.

By the way, with my current setup, I'm not using hostapd at all.  The card goes into ad-hoc mode just fine using 'iwconfig wlan1 mode ad-hoc'

I also still don't understand why /etc/network/interfaces does not seem to be applied to the wireless settings (i.e. changing the SSID in the file does not actually change the SSID that iwconfig displays after restarting the interface).



Maybe I'll try posting on the linux forums or debian forums.

---

### Post by svtguy88 on 2011-10-27
Ok.  I think I figured out how to bring my wireless ad-hoc network back when it crashes.  I thought about why iwconfig wasn't getting updated by the info in /etc/network/interfaces, and figured it must be something related to the driver/module for the card.  I unloaded the rtl8185 module, reloaded it, brought wlan1 back up, and restarted DHCP, and now I can connect again.

Still confused as to why it quit on me earlier.  I wonder how long it will stay up before dropping out again....


**edit**

Just doing some thinking.  When wireless went down on me earlier, I think I disconnected both of my clients from the network at some point.  I wonder if it goes down when there are no more active clients...?

---


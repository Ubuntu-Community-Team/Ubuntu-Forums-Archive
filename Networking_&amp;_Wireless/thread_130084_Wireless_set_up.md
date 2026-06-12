---
title: "Wireless set up"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by uncleant on 2006-02-15
First off I want to say I am a total n00b, just so you know.  I'm in the process of making the switch from windows like most people here.  My problem is with the wireless set up.  I have a dlink di-624 router and a dwl 520 wireless card.  I installed breezy without any problems.  Once that was finished I went into the network set up to see if my card was recognized.  There were 2 wireless connections listed one was wlan0 and the other was wifi0.  From what I have read here I don't think I've seen anyone with this situation.

iwconfig looked something like this
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     IEEE 802.11-ds ESSID:test
           Mode:master 


wlan0    IEEE 802.11-ds ESSID:test
          Mode:master  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

At this point I'm not sure what to do next.  Any suggestions would be appreciated.

---

### Post by Lambert on 2006-02-15
Go to the WifiDocs link in my signature, look for WirelessTroubleshootingGuide or any other help you see on that page. 

Walk through the WTG and post back if you get stuck or can't figure it out.

The one thing that will need to be known is driver being used and the chipset which the lshw/lspci commands explained on that page which tell us.

---

### Post by uncleant on 2006-02-16
I did as you said and went through the troubleshooting guide.  My card is the dwl 520 rev e1.  On the Ifconfig or Iwconfig screen I saw a message about needing driver 18 and 17 was installed but some functions may not work.  Sorry for not having the exact wording.  Could this be the answer to my problem?  If so how do I get the correct driver?

---

### Post by Lambert on 2006-02-16
The exact wording is needed and does sound like it could be where your problem is. If you can get it post here along with output of command

lspci -v | grep -A 4 Eth

I would also suggest doing a google search using all or parts of the actual error, maybe looking on the driver project page for support about specific errors. Go to udsfWireless link in my sig as there are links there to driver sites.

---

### Post by uncleant on 2006-02-17
Okay, I ditched the dlink card and got a used zyxel zyair g302.  Now the ifconfig and iwconfig screens look like the examples, except no ip addr.  Some other info I found was product: acx 111, vendor Texas Inst and driver acx_pci.  I have my router set up as open and configured for dhcp.  The problem is I cant ping the router and iwlist comes up empty.

---

### Post by Lambert on 2006-02-17
Go to this page under the breezy section. You need firmware for the chipset.

[http://doc.gwos.org/index.php/ACXDriver](http://doc.gwos.org/index.php/ACXDriver)

If that isn't the solution there is a link for the houseofcraig site. Ignore the part on compiling as the module is part of breezy. You just need firmware and to configure.

---

### Post by w8iss on 2006-03-02
Here's the comment that uncleant was refering to:

 iwlist wlan0 scan
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     No scan results


I have had this card working before under 5.04 and am tempted to go back as a lot
of things I had working before aren't working now...:(

Maybe this'll help out some.

James W8ISS

---


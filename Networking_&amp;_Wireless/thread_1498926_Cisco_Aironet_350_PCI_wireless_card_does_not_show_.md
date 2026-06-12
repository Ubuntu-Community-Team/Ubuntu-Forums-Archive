---
title: "Cisco Aironet 350 PCI wireless card does not show up in nm-applet or iwlist"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by telewatho on 2010-06-01
I have a Cisco Aironet 350 PCI wireless networking card. ( It's using the airo module, which loads itself automatically on startup)

When I drop-down my network manager applet, it says "disconnected" for wired and wireless, and doesnt give me a list of wireless networks to connect to.  This is very annoying as there isnt a place in the house with both an internet connection and a power socket :-( :-(.
I haven't tried plugging the computer into a wired network yet for this reason, so i dont know whether network manager works at all!

I'm having very similar issues to [this thread]("http://art.ubuntuforums.org/showthread.php?t=1414052&page=2"), and my dmesg output is the same.

iwconfig shows *both* eth1 and wifi0 interfaces..

And yet "sudo iwlist eth1 scan" and "sudo iwlist wifi0 scan" BOTH say no  scan results.
This happens regardless of whether nm-applet is running or not  (nm-applet shows "disconnected" for both wired and wireless).

My /etc/network/interfaces file contains only the loopback interface.

/etc/NetworkManager/nm-system-settings.conf shows "managed=false" for  ifupdown (is this correct?)

The CISCO AIRONET PCI card has two lights on the back of it, green and  amber.  The green is off, and the amber has a pattern:  2-flash...pause....1-flash...pause....
From the CISCO website,
[http://www.cisco.com/en/US/docs/wire...html#wp1020111]("http://www.cisco.com/en/US/docs/wireless/wlan_adapter/350_cb20a/user/windows/1.0/configuration/guide/win5_c10.html#wp1020111")
I have interpretted this as meaning:
"A configuration error has occurred (for example,  static WEP is enabled  in ACU, but the client adapter has not been  programmed with a valid  WEP key). Recheck your client adapter's  configuration settings"

I do not think my card has WEP

Many thanks in advance for your help getting mine and hopefully other people's cards to work 8-[

(2.6.31-21-generic. Ubuntu Karmic)

---

### Post by tenwiseman on 2010-06-26
> 
/etc/NetworkManager/nm-system-settings.conf shows "managed=false" for ifupdown


You need to have "managed=true" for NetworkManager to bring the interfaces up.


Your card and the stock ubuntu airo driver supports WEP. 

If you flash update the card with Cisco's last firmware (best done in Windows) then you can have WPA support using the driver here.

[http://gna.org/projects/airo-wpa/](http://gna.org/projects/airo-wpa/)

Details on how I did this over here :)

[http://ubuntuforums.org/showthread.php?t=1514304](http://ubuntuforums.org/showthread.php?t=1514304)

---

### Post by telewatho on 2010-07-09
Ah brill, Tenwisemen :D

I haven't tried it out yet. Sorry it's been so long. My power supply kind of stopped working.  Got a new one now.  Yeah, I'm gonna wipe my harddisc and upgrade to Lucid in a bit, so I'll try it out then.  Good to know WEP works.  I thought it wouldn't originally because of CISCO's way of naming the cards. Cheers a lot! Tele

---


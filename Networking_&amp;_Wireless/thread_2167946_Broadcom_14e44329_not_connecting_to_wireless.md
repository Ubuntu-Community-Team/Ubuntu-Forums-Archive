---
title: "Broadcom 14e4:4329 not connecting to wireless"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by tim6 on 2013-08-15
Hello all,

I followed the steps in this thread: [http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey](http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey)

and my wireless card is still not connecting. I have chipset: BCM4321.

When I click on 'Activate' in 'Additional Drivers' for 'Broadcom STA Wireless Driver' it tells me to look at: /var/log/jockey.log. Let me know what I should look for in the log and I will paste what's relevant.

Thanks for the help.

---

### Post by chili555 on 2013-08-15
> **tim6 said:**
> Hello all,

I followed the steps in this thread: [http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey](http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey)

and my wireless card is still not connecting. I have chipset: BCM4321.

When I click on 'Activate' in 'Additional Drivers' for 'Broadcom STA Wireless Driver' it tells me to look at: /var/log/jockey.log. Let me know what I should look for in the log and I will paste what's relevant.

Thanks for the help.We don't know what's relevant until we see it. Why not paste it *all* here and give us the link in your reply.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by tim6 on 2013-08-15
ok! here's the log: [http://paste.ubuntu.com/5990968/](http://paste.ubuntu.com/5990968/)

But I think I have a new problem, I restarted my computer and my wireless connected, but then less then a minute later it disconnected >.> Now when I manually click connect it works but like I said, less then a minute later I get disconnected. Ever heard of this happening before??

---

### Post by chili555 on 2013-08-15
>  less then a minute later I get disconnected. Ever heard of this happening before?? A few times. Let's troubleshoot why.

First, I don't see much wrong in jockey.log as relates to wireless. I assume you are using the correct driver wl; check:```
lsmod | grep -e wl -e b43 -e brcmsmac
```wl and a few dependencies should appear and none of the others. Next, let's have a look at:```
nm-tool
dmesg | grep -e wl -e eth1 -e 80211
```

---

### Post by tim6 on 2013-08-15
**UPDATED since I got the proprietary driver installed**

lsmod | grep -e wl -e b43 -e brcmsmac returns:
```
wl 3074942 0 
cfg80211 208382 1 wl
lib80211 14382 2 lib80211_crypt_tkip, wl
```

nm-tool returns:
```
NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:04:4B:16:F2:F2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.252.0.12


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:04:4B:16:F2:F3

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1E:E5:F9:AE:02

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

and finally dmesg | grep -e wl -e eth1 -e 80211 returns:

[http://paste.ubuntu.com/5991502/](http://paste.ubuntu.com/5991502/)

---

### Post by FenrirXIII on 2013-08-15
in case you need to here's the driver for linux [click here]("http://www.broadcom.com/support/802.11/linux_sta.php")... maybe you just need to reinstall it... tell me how it goes

---

### Post by tim6 on 2013-08-16
**I updated my above post**

Ok I successfully have the proprietary Broadcom STA Wireless Driver installed! Still not 100% percent working though.

I am getting the random disconnect problem again. I will connect and then 30 seconds or so later I will get disconnected. I have the checkbox "available to all users" checked. Not sure what to do now though. Edit* sometimes my wireless network doesn't even show up now.

From my above post the error I'm getting is: 
```
[ 1309.047158] ERROR @wl_notify_scan_status : eth2 Scan_results error (-22)
```

**One more edit**

I just restarted and now no wireless networks are showing up at all.

---

### Post by FenrirXIII on 2013-08-16
things you might consider to work with:

Terminal Commands: Note sudo commands requires super user password

[I]sudo rfkill unblock list all

[/I]This command should LIST the Radio Frequency Kill(Switch)

if any of the soft block or hard block says says, this means the blocking of the kill switch is on. to do that you have to:

*sudo rfkill unblock wifi*

This will unblock the the switch and turn the soft and hard block off

youll probably notice your wifi turning on.

hope that helps.

Which version of ubuntu are you using?

alternatively, try and see if any of the wireless switch (actual switch) on the laptop(im assuming) is switch off. Or if you dont have any physical switch, maybe the Fn key and F2 (or whatever your laptop Function key for toggling wireless on and off. if not, ill try my best as i can to assist... im also in a wireless situation myself, though its hard to pin point my dilemma

---

### Post by chili555 on 2013-08-16
> **tim6 said:**
> **I updated my above post**

Ok I successfully have the proprietary Broadcom STA Wireless Driver installed! Still not 100% percent working though.


```
[ 1309.047158] ERROR @wl_notify_scan_status : eth2 Scan_results error (-22)
```

I just restarted and now no wireless networks are showing up at all.Hmmm. You had wireless and no errors before you reinstalled the driver. I hope FenrirXIII has your answer.

---


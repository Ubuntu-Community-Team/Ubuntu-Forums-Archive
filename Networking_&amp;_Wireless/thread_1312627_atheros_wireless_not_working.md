---
title: "atheros wireless not working"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by arjuntank on 2009-11-03
installed 9.10 on my dad's laptop(dell vostro).
on the live cd version, wireless was working fine, but when i installed it was not working. 
```

description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan1
                version: 01
                serial: 00:17:c4:96:37:92
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f6cf0000-f6cffff

```
and
```

$sudo ifconfig wlan1 up
SIOCSIFFLAGS: Unknown error 132

```

and there is no wireless switch that i can turn on or off.
also tried installing the linux-backports-karmic. Nothing shows up on the hardware drivers window(prop. drivers).
and yeah, i am done with the default network manager.I am sorry to say but it sucks. I am using wicd for now.

Help! Otherwise i will need to install windows again for my dad. (had a hard time convincing him)
Thanks!

---

### Post by chili555 on 2009-11-03
My understanding is that error 132 is a wireless switch issue. Isn't there a switch on the left side?

---

### Post by albienoche on 2009-11-03
I did an upgrade from 9.04 to 9.10 and my Atheros Wifi(AR5001X+) wasn't working either; I received the same error as you did when I clicked on the Network Manager applet.

I followed various procedures in other threads that actually got me closer to working again.

(1) One of the procedure was to comment out the line:

blacklist ath5k

*in the file /etc/modprobe.d/blacklist-ath_pci.conf*

**#blacklist ath5k**


(2) I did a reboot, still no luck. But then I noticed that same line is also listed in the madwifi.conf file. So I comment out that line as well:

blacklist ath5k

*in the file /etc/modprobe.d/madwifi.conf*

[B]#blacklist ath5k
[/B]

(3) I then did a reboot and a **'sudo ifup wlan0'** command.  


My Atheros Wifi was up and running again. Even better than before since I didn't get disconnections under heavy streaming content as I did in 9.04.  I am not a linux kernel export nor a Atheros expert, so correct me if I'm wrong.  But by un-blacklisting the above lines the linux kernel is in fact using the ath5k driver for my Atheros card. Can someone give me some insight as to what I did and why the ath5k was blacklisted in the first place.  What is madwifi and what is ath5k?

Check out what this guy did. 

[http://ubuntuforums.org/showthread.php?t=1139059&mode=linear](http://ubuntuforums.org/showthread.php?t=1139059&mode=linear)

---

### Post by albienoche on 2009-11-03
I apologize. After careful examination I DID NOT get the same error as you did.

My error message was:


Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device





Different error, once again my apologies.

---

### Post by arjuntank on 2009-11-03
> **albienoche said:**
> I did an upgrade from 9.04 to 9.10 and my Atheros Wifi(AR5001X+) wasn't working either; I received the same error as you did when I clicked on the Network Manager applet.

I followed various procedures in other threads that actually got me closer to working again.

(1) One of the procedure was to comment out the line:

blacklist ath5k

*in the file /etc/modprobe.d/blacklist-ath_pci.conf*

**#blacklist ath5k**


(2) I did a reboot, still no luck. But then I noticed that same line is also listed in the madwifi.conf file. So I comment out that line as well:

blacklist ath5k

*in the file /etc/modprobe.d/madwifi.conf*

[B]#blacklist ath5k
[/B]

(3) I then did a reboot and a **'sudo ifup wlan0'** command.  


My Atheros Wifi was up and running again. Even better than before since I didn't get disconnections under heavy streaming content as I did in 9.04.  I am not a linux kernel export nor a Atheros expert, so correct me if I'm wrong.  But by un-blacklisting the above lines the linux kernel is in fact using the ath5k driver for my Atheros card. Can someone give me some insight as to what I did and why the ath5k was blacklisted in the first place.  What is madwifi and what is ath5k?

Check out what this guy did. 

[http://ubuntuforums.org/showthread.php?t=1139059&mode=linear](http://ubuntuforums.org/showthread.php?t=1139059&mode=linear)

I already had done that before. I had blacklisted the ath5k from the .conf file. Nothing happened after the reboot. Then I installed the latest backports-modules-karmic and still nothing happened. So, I decided to comment ath5k again so that it goes to default as it came from the installation, that is i did: "#blacklist ath5k" in the .conf file. This is because i thought the live cd version of 9.10, wireless was working perfect,then why not after installation? 
So, magically, its now working as i installed the latest karmic backports.
I hope this is helpful. Thanks for the help guys!

arjun

---

### Post by arjuntank on 2009-11-03
> **chili555 said:**
> My understanding is that error 132 is a wireless switch issue. Isn't there a switch on the left side?

No, there is no such switch. the wireless led on the laptop won't lit up anytime when using the wireless device. the fn+f10 or f11, (i dont remember)used for activating wireless device,works only on the default vista installation that dell gave, plus, no bios settings as such.
Thanks for the help!

arjun

---

### Post by Iowan on 2009-11-03
[This]("http://ubuntuforums.org/showthread.php?t=1312160") one claims a fix...

---

### Post by chili555 on 2009-11-03
> No, there is no such switch.Which model Vostro is it?

---

### Post by arjuntank on 2009-11-04
> **chili555 said:**
> Which model Vostro is it?

it's a860. don't you think there should be a shortcut so that you can turn off wireless devices in the absence of hardware switch? i wonder if i can make a script.

---

### Post by DarkKitsune on 2009-11-07
Thank you SO much! Commenting out the blacklist fixed my same problem with this same problem.

---

### Post by AvgUser on 2009-11-09
Thinkpad R40 here, Atheros chipset.  Been working fine till alledged upgrade to 9.10. Commenting out the ath5k works fine here, had no madwifi.conf...

"in the file /etc/modprobe.d/blacklist-ath_pci.conf

#blacklist ath5k"

---

### Post by stu_edgar on 2009-11-30
#5 worked for me - thanks very much for the help!

---

### Post by kilroy123 on 2009-12-05
When I updated to 9.10 my wireless went out as well. No matter what kernal I tried to bootup in I couldn't get my wireless working. 

Commenting out #blacklist ath5k in /etc/modprobe.d/blacklist-ath_pci.conf.
Then rebooting worked perfectly on my Lenovo R61i. :p


Thank you very much!

---

### Post by zolin on 2010-01-10
I booted up with an usb ubuntu netbook remix and found that the wifi was working fine. I could connect to this forum and read your message, then I opened the */etc/modprobe.d/blacklist-ath_pci.conf *file on the live running instance and noticed that it did't have any reference to ath5k, instead it had the ath_pci module.

I mounted my / partition and comment out ath5k and added ath_pci, rebooted the pc and now it is up and running.

I mas using the madwifi-hal-0.10.5.6-r3879-20081204 driver since 8.10 and I think that when compiling and building that driver, the blacklist file got modified.

Thanks!
Cheers.

---


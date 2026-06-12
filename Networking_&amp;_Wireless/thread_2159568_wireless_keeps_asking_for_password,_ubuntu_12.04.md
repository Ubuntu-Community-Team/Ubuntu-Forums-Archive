---
title: "wireless keeps asking for password, ubuntu 12.04"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2013-07-03
This is on Ubuntu 12.04.

After a reboot and coming back from 'suspend' my wireless connection tries to reconnect but keeps asking for the password.  Its already filled in for me in the little window so I have to hit the 'connect' button.

How do I correct this and connect automatically?

---

### Post by varunendra on 2013-07-03
Please follow the "Wireless Script" link in my signature, download the script as per Method #2 there and keep the script ready. Run the script when it fails to connect after resuming from suspend, and post back the report it generates.

And what do you mean by "after reboot"? Does it work well in any case at all? Is it the same rt3290sta driver that we compiled a few hours ago in a different thread?

---

### Post by varunendra on 2013-07-04
Just got a message from my respectable friend Hadaka, and re-read your post -
> **pretty_whistle said:**
> Its already filled in for me in the little window **so I have to hit the 'connect' button**.

**How do I correct this and connect automatically**?

I think I totally misunderstood your post earlier (if not this time). Do you mean you are able to connect just fine only need to "click" the button manually? If so, there is no need to go through the script or any other hassles. Just edit your connection to make it connect automatically -

Open Network Manager > Edit Connection > Wireless tab > double-click your connection to edit it > make sure "**Connect Automatically**" box has a Tick-mark in it > Save and close > Done !

Thanks again to Hadaka for waking me up :P

---

### Post by pretty_whistle on 2013-07-04
> **varunendra said:**
> Just got a message from my respectable friend Hadaka, and re-read your post -


I think I totally misunderstood your post earlier (if not this time). Do you mean you are able to connect just fine only need to "click" the button manually? If so, there is no need to go through the script or any other hassles. Just edit your connection to make it connect automatically -

Open Network Manager > Edit Connection > Wireless tab > double-click your connection to edit it > make sure "**Connect Automatically**" box has a Tick-mark in it > Save and close > Done !

Thanks again to Hadaka for waking me up :P

That's correct.  I just need to click the button manually.

And the 'connect automatically' box has a tick-mark in it but it's acting like it doesn't.

---

### Post by varunendra on 2013-07-04
> **pretty_whistle said:**
> That's correct.  I just need to click the button manually.

And the 'connect automatically' box has a tick-mark in it but it's acting like it doesn't.

Hmm.. maybe then it is an issue of driver not getting ready in time. But just as a sanity check, have you saved the correct password and security type in Network Manager itself ?

If yes, please post the output of -
```
sudo cat /etc/NetworkManager/system-connections/<your connection name>
```
[COLOR="#FF0000"]**CAUTION !!** The above output will also contain your saved password. Remove or obscure it before posting the output here ![/COLOR]

---

### Post by pretty_whistle on 2013-07-04
> **varunendra said:**
> Hmm.. maybe then it is an issue of driver not getting ready in time. But just as a sanity check, have you saved the correct password and security type in Network Manager itself ?

If yes, please post the output of -
```
sudo cat /etc/NetworkManager/system-connections/<your connection name>
```
[COLOR=#FF0000]**CAUTION !!** The above output will also contain your saved password. Remove or obscure it before posting the output here ![/COLOR]
I saved the right info alright, I even re-entered it to be sure.

Here's the output:

```
[connection]id=H5c8a4fWr
uuid=ea16b0ca-9464-410b-abc5-d5c79fabd74e
type=802-11-wireless
timestamp=1372955628


[802-11-wireless]
ssid=*********
mode=infrastructure
security=802-11-wireless-security


[802-11-wireless-security]
key-mgmt=wpa-psk
psk=**********


[ipv4]
method=auto


[ipv6]
method=auto



```

---

### Post by varunendra on 2013-07-04
Everything seems as it should be in the settings. Maybe we just need to delay the initiation of connection somehow. Unfortunately I don't yet know how to do it. I'll need to do some searching-reading on it. I suggest you do the same (how to delay wireless connection after resuming/rebooting).

Please remind me if I forget about this and no one else comes up with a suggestion either.
(I pick up threads by noticing new posts)

---

### Post by pretty_whistle on 2013-07-04
> **varunendra said:**
> Everything seems as it should be in the settings. Maybe we just need to delay the initiation of connection somehow. Unfortunately I don't yet know how to do it. I'll need to do some searching-reading on it. I suggest you do the same (how to delay wireless connection after resuming/rebooting).

Please remind me if I forget about this and no one else comes up with a suggestion either.
(I pick up threads by noticing new posts)
:)  Thanks for trying.

---

### Post by Hadaka on 2013-07-04
Hi, give this a try..
click your launcher...System Settings..Network..Wireless..(highlight YOUR ssid) then click..Forget Network
boot
when the system comes back up and says.."Network Connections Are Available" then click YOUR ssid
Enter your "password-key" connect.
then..click the wireless icon...next to the envelope..Edit Connections..Wireless..Your ssid..Edit
Click Connect Automatically.then configure exactly like the attached screen shots..
[ATTACH=CONFIG]244411[/ATTACH][ATTACH=CONFIG]244410[/ATTACH][ATTACH=CONFIG]244412[/ATTACH][ATTACH=CONFIG]244413[/ATTACH]
configure your security per your settings..
save settings...boot

---

### Post by pretty_whistle on 2013-07-04
It's still doing it :(

---

### Post by wildmanne39 on 2013-07-04
Hi, please show the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by pretty_whistle on 2013-07-04
> **Wild Man said:**
> Hi, please show the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)	Subsystem: Hewlett-Packard Company Device [103c:1858]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
	Subsystem: Hewlett-Packard Company Device [103c:18ec]
	Kernel driver in use: rt2860



```

---

### Post by wildmanne39 on 2013-07-04
It says that rt2860 is the driver being used but it does not look right to me, if that is the driver like it says you should be able to do this:
```
gksudo gedit /etc/pm/config.d/unload_modules
```
then add this line:
```
SUSPEND_MODULES="$SUSPEND_MODULES rt2860
```
save then close gedit and reboot.
Thanks

---

### Post by pretty_whistle on 2013-07-04
> **Wild Man said:**
> It says that rt2860 is the driver being used but it does not look right to me, if that is the driver like it says you should be able to do this:
```
gksudo gedit /etc/pm/config.d/unload_modules
```
then add this line:
```
SUSPEND_MODULES="$SUSPEND_MODULES rt2860
```
save then close gedit and reboot.
Thanks
I'm trying it now.

---

### Post by pretty_whistle on 2013-07-04
It didnt fix it.  :(

---

### Post by steeldriver on 2013-07-04
Do you have autologin enabled? is the 'Available to all users' box checked as well as the 'Connect automatically' one?

---

### Post by pretty_whistle on 2013-07-04
> **steeldriver said:**
> Do you have autologin enabled? is the 'Available to all users' box checked as well as the 'Connect automatically' one?
No, yes, and yes.

Edit:  Now it has auto login.

---

### Post by steeldriver on 2013-07-04
OK... there goes that theory  :( (I was thinking it might be keyring related rather than wifi related per se)

---

### Post by varunendra on 2013-07-04
> **Wild Man said:**
> It says that rt2860 is the driver being used but it does not look right to me....

Wild Man, it is rt3290sta we compiled here : [http://ubuntuforums.org/showthread.php?t=2159334&p=12716581#post12716581](http://ubuntuforums.org/showthread.php?t=2159334&p=12716581#post12716581)
Weird ways of Ralink.. :P

@ pretty_whistle,
Accordingly, try "rt3290sta" instead of rt2860 in Wild Man's solution. It is supposed to unload the module when going to sleep, then load it again when resuming. Not the same thing that I was thinking (delaying the connection), but often helps.

You also said "reboot". Does it do this after a reboot as well? Or just after a sleep --> resume cycle?
And.. do you need to click on the password box only once? Like everything is working absolutely perfect, just can't do it automatically?

Answer to these two question can significantly change our approach, if the above suggestion fails to do the trick.

---

### Post by pretty_whistle on 2013-07-05
> **varunendra said:**
> Wild Man, it is rt3290sta we compiled here : [http://ubuntuforums.org/showthread.php?t=2159334&p=12716581#post12716581](http://ubuntuforums.org/showthread.php?t=2159334&p=12716581#post12716581)
Weird ways of Ralink.. :P

@ pretty_whistle,
Accordingly, try "rt3290sta" instead of rt2860 in Wild Man's solution. It is supposed to unload the module when going to sleep, then load it again when resuming. Not the same thing that I was thinking (delaying the connection), but often helps.

You also said "reboot". Does it do this after a reboot as well? Or just after a sleep --> resume cycle?
And.. do you need to click on the password box only once? Like everything is working absolutely perfect, just can't do it automatically?

Answer to these two question can significantly change our approach, if the above suggestion fails to do the trick.
I tried Wild Man's solution with rt3290sta but it didnt resolve it.  However I did get an error window (see below) and I couldnt suspend anymore so I had to undo it.
[IMG]http://i43.tinypic.com/jpc0i0.png[/IMG]

As to your question, yes it does it after a reboot too.  And do I need to click on it just once?  Yes.  It just doesn't do it automatically which is what I want it to do.

---

### Post by varunendra on 2013-07-05
Hmm.. at least you got a response :D

I just noticed that the command in Wild Man's post doesn't contain a closing double quote. Did you try it exactly the same way? If so, it should actually be -
```
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta**[COLOR="#FF0000"]"[/COLOR]**
```(notice the last closing double-quote)
Just copy-paste it to avoid mistakes, and see if it succeeds.

If you already corrected that while trying, let me know and we can use a full-fledged script instead.

---

### Post by pretty_whistle on 2013-07-05
> **varunendra said:**
> Hmm.. at least you got a response :D

I just noticed that the command in Wild Man's post doesn't contain a closing double quote. Did you try it exactly the same way? If so, it should actually be -
```
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta**[COLOR=#FF0000]"[/COLOR]**
```(notice the last closing double-quote)
Just copy-paste it to avoid mistakes, and see if it succeeds.

If you already corrected that while trying, let me know and we can use a full-fledged script instead.

I'm confused a bit.  My email notification about this post shows this:

SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta*"*

...but your actual post doesnt contain the *"* at the end of it.

So....which one do I use?

---

### Post by wildmanne39 on 2013-07-05
Hi, it should have been:
```
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta"
```
I do have my doubts that it will fix your issue but in many cases it does.
I am sorry I missed the last set of quotes.
Thanks

---

### Post by pretty_whistle on 2013-07-05
> **Wild Man said:**
> Hi, it should have been:
```
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta"
```
I do have my doubts that it will fix your issue but in many cases it does.
I am sorry I missed the last set of quotes.
Thanks
Ok.  I'll try it.

---

### Post by pretty_whistle on 2013-07-05
It didnt solve the problem.  :(

One thing I didnt mention was it asking to hit the button in the password window doesnt happen right away.  The window always appears after a minute while the icon shows a circular thing going round and round.  When I put my cursor over it it says its configuring the network.

Sorry but I forgot to mention it initially. :(

Dont know if this makes any difference though.

---

### Post by varunendra on 2013-07-05
Yes it does make some difference, although Wild Man'd solution already tries to deal with it.

That behaviour may be an indication that at least the first authentication attempt, although initiated automatically as we expect, is failed for some reason. Reason most probably being the driver not getting ready in time, which is also what we suspected.

Before we try our next approach, please try the following manually (our next attempt will be to do the same thing automatically) -
Before going to sleep, unload the module -
```
sudo modprobe -rfv rt3290sta
```
(let us know if it returns any errors)

After resuming, load it again -
```
sudo modprobe -v rt3290sta
```

and see if it connects automatically (if it doesn't start the connection immediately, do it manually after above command). What I expect to see is that the first attempt doesn't fail in the same manner as you described above. If it works, our script to do the same thing automatically should also work.

If it fails (the first attempt, needing you to click the button again), then please post back the result of -
```
dmesg | egrep 'rt3|rt2'
```

---

### Post by pretty_whistle on 2013-07-05
> **varunendra said:**
> Yes it does make some difference, although Wild Man'd solution already tries to deal with it.

That behaviour may be an indication that at least the first authentication attempt, although initiated automatically as we expect, is failed for some reason. Reason most probably being the driver not getting ready in time, which is also what we suspected.

Before we try our next approach, please try the following manually (our next attempt will be to do the same thing automatically) -
Before going to sleep, unload the module -
```
sudo modprobe -rfv rt3290sta
```
(let us know if it returns any errors)

After resuming, load it again -
```
sudo modprobe -v rt3290sta
```

and see if it connects automatically (if it doesn't start the connection immediately, do it manually after above command). What I expect to see is that the first attempt doesn't fail in the same manner as you described above. If it works, our script to do the same thing automatically should also work.

If it fails (the first attempt, needing you to click the button again), then please post back the result of -
```
dmesg | egrep 'rt3|rt2'
```

I just tried sudo modprobe -rfv rt3290sta and got this error:

> FATAL: Module rt3290sta is in use.

---

### Post by varunendra on 2013-07-06
> **pretty_whistle said:**
> I just tried sudo modprobe -rfv rt3290sta and got this error:

Hmm.. probably that's why the suspend trick didn't work and probably Wild Man knew it, hence "his doubts"... let's see -
```
lsmod | grep rt3
```

---

### Post by pretty_whistle on 2013-07-06
> **varunendra said:**
> Hmm.. probably that's why the suspend trick didn't work and probably Wild Man knew it, hence "his doubts"... let's see -
```
lsmod | grep rt3
```
Here it is:

rt3290sta              1125124  1

---

### Post by varunendra on 2013-07-06
> **pretty_whistle said:**
> Here it is:

rt3290sta              1125124  1

Hmm.. interesting, no dependencies still the error ! Please try -
```
sudo ifconfig **ra0** down
sudo modprobe -rfv rt3290sta
```
(check "ifconfig" or "iwconfig" beforehand to see if the interface is referred to as something else than "ra0", use that one if it is).

---

### Post by pretty_whistle on 2013-07-06
> **varunendra said:**
> Hmm.. interesting, no dependencies still the error ! Please try -
```
sudo ifconfig **ra0** down
sudo modprobe -rfv rt3290sta
```
(check "ifconfig" or "iwconfig" beforehand to see if the interface is referred to as something else than "ra0", use that one if it is).
I checked using ifconfig but I have a question.  Should I use ra0 because it's listing eth1 as well:

```

eth1      Link encap:Ethernet  HWaddr 88:51:fb:c6:60:b2            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:686159 (686.1 KB)  TX bytes:686159 (686.1 KB)


ra0       Link encap:Ethernet  HWaddr a4:17:31:af:77:31  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:feaf:7731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:949747 errors:2 dropped:0 overruns:0 frame:0
          TX packets:119932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161770155 (161.7 MB)  TX bytes:25301509 (25.3 MB)
          Interrupt:18 



```
??

---

### Post by varunendra on 2013-07-06
> **pretty_whistle said:**
> I checked using ifconfig but I have a question.  Should I use ra0 because it's listing eth1 as well:


That is your ethernet interface (cable network). The wireless one is "ra0" and only that one we need to bring down (hoping that the driver will be freed by doing so). It is usually named as wlan<some number>, like wlan0. But some drivers tend to rename it.

So try the exact commands as in my previous post.

---

### Post by pretty_whistle on 2013-07-06
> **varunendra said:**
> That is your ethernet interface (cable network). The wireless one is "ra0" and only that one we need to bring down (hoping that the driver will be freed by doing so). It is usually named as wlan<some number>, like wlan0. But some drivers tend to rename it.

So try the exact commands as in my previous post.

Done.

Do I reboot after that or what?

---

### Post by varunendra on 2013-07-06
> **pretty_whistle said:**
> Done.

Do I reboot after that or what?

So.. it didn't give you the "Fatal..." error this time while doing "modprobe -rfv rt3290sta" ??

If so, that's good. Try next (without rebooting) -
```
sudo modprobe -v rt3290sta
```
and see if the connection gets picked up automatically. Regardless of whether or not it connects automatically, if it got unloaded this time without error, we're gonna place a script in /etc/pm/sleep.d directory to make it unload at sleep, then load again at resume. And see if it works.

---

### Post by pretty_whistle on 2013-07-06
> **varunendra said:**
> So.. it didn't give you the "Fatal..." error this time while doing "modprobe -rfv rt3290sta" ??

If so, that's good. Try next (without rebooting) -
```
sudo modprobe -v rt3290sta
```
and see if the connection gets picked up automatically. Regardless of whether or not it connects automatically, if it got unloaded this time without error, we're gonna place a script in /etc/pm/sleep.d directory to make it unload at sleep, then load again at resume. And see if it works.
Same problem still exists but good news is no error came up.

Would the script affect it not connecting automatically after a reboot?

---

### Post by varunendra on 2013-07-06
> **pretty_whistle said:**
> Same problem still exists but good news is no error came up.

Would the script affect it not connecting automatically after a reboot?

Had it connected automagically after reloading the driver I would have been sure, but not now. Let's just try it. Create a new file in the sleep.d directory -
```
gksu gedit /etc/pm/sleep.d/20_ralink
```

It will open up a blank file. Copy paste the following in it -
```
case "${1}" in
    hibernate|suspend)
        # Unload the rt3290sta driver
        ifconfig ra0 down
        modprobe -rf rt3290sta
        ;;
    resume|thaw)
        # Reload the driver
        sleep 10
        modprobe rt3290sta
        ifconfig ra0 up
        ;;
esac
```
Proofread, save and close the file. Then make it executable -
```
sudo chmod +x /etc/pm/sleep.d/20_ralink
```

Then reboot, do a sleep-resume cycle and see if some miracle happens. If not, it's time to check external factors too, which means follow the "Wireless Script" link in my signature, and post back the report as suggested in the linked post.

One more thing that my friend Hadaka pointed out but I forgot to ask - when you originally compiled the driver, did you make sure to change the line 31 in config.mk file to "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y**"? (by default its value is "n", you had to change it to "y")

I'm not sure how much it is related, but it is an important change.

---

### Post by pretty_whistle on 2013-07-06
> **varunendra said:**
> Had it connected automagically after reloading the driver I would have been sure, but not now. Let's just try it. Create a new file in the sleep.d directory -
```
gksu gedit /etc/pm/sleep.d/20_ralink
```

It will open up a blank file. Copy paste the following in it -
```
case "${1}" in
    hibernate|suspend)
        # Unload the rt3290sta driver
        ifconfig ra0 down
        modprobe -rf rt3290sta
        ;;
    resume|thaw)
        # Reload the driver
        sleep 10
        modprobe rt3290sta
        ifconfig ra0 up
        ;;
esac
```
Proofread, save and close the file. Then make it executable -
```
sudo chmod +x /etc/pm/sleep.d/20_ralink
```

Then reboot, do a sleep-resume cycle and see if some miracle happens. If not, it's time to check external factors too, which means follow the "Wireless Script" link in my signature, and post back the report as suggested in the linked post.

One more thing that my friend Hadaka pointed out but I forgot to ask - when you originally compiled the driver, did you make sure to change the line 31 in config.mk file to "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y**"? (by default its value is "n", you had to change it to "y")

I'm not sure how much it is related, but it is an important change.
Same problem still exists.

I did change it to a Y in line 31.

---

### Post by pretty_whistle on 2013-07-06
Here's what you told me to get:

```
 


*************** info trace ***************


***** uname -a *****


Linux nutin 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:45:16 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise


***** lspci *****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:1858]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
	Subsystem: Hewlett-Packard Company Device [103c:18ec]
	Kernel driver in use: rt2860


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 


***** iwconfig *****


ra0       Ralink STA  ESSID:"H5c8a4fWr"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-39 dBm  Noise level:-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****


0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rt3290sta            1125124  1 


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: ra0  [H5c8a4fWr] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    HOME-5952:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 2 Mb/s, Strength 47 WPA WPA2
    myqwest9999:     Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WEP
    *H5c8a4fWr:      Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1
    DNS:             205.171.3.25




- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


***** NetworkManager.conf *****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,88:51:FB:C6:60:B2,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=100/100  Signal level=-35 dBm  Noise level=-92 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"HOME-5952"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/100  Signal level=-70 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD6A85950103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"H5c8a4fWr"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=100/100  Signal level=-35 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/100  Signal level=-62 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




***** resolv.conf *****


nameserver 127.0.0.1
search domain.actdsltmp


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** dmesg *****


[   22.833170] rt3290sta: module license 'unspecified' taints kernel.
[   22.844295] rt2860 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.844329] rt2860 0000:02:00.0: setting latency timer to 64
[   23.893962] r8169 0000:01:00.0: eth1: link down
[   23.894139] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.894617] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.977098] <==== rt28xx_init, Status=0
[   24.082309] <==== rt28xx_init, Status=0
[  114.826796] <==== rt28xx_init, Status=0
[  131.205397] rt2860 0000:02:00.0: setting latency timer to 64
[  131.274715] <==== rt28xx_init, Status=0
[  131.923269] r8169 0000:01:00.0: eth1: link down
[  131.923636] ADDRCONF(NETDEV_UP): eth1: link is not ready


****************** done ******************



```

---

### Post by varunendra on 2013-07-06
If this is your access point as indicated -> **pretty_whistle said:**
> 
```
***** iwlist *****

          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"**H5c8a4fWr**"
                    Mode:Managed
                    Frequency:2.447 GHz (**Channel 8**)
                    Quality=100/100  Signal level=-35 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: **WPA Version 1**
                        Group Cipher : **TKIP**
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```
Then there are a couple of suggestions to possibly improve the connectivity -

[INDENT]1) Change the encryption type from TKIP to AES, much better - **WPA2**-PSK (AES)
2) Although there doesn't seem the need for, but you may also try changing the channel to 1 or 11 instead of 8[/INDENT]

Everything else looks good to me.

---

### Post by pretty_whistle on 2013-07-06
The problem my wireless is having is that its not recognizing that "connect automatically" is checked off.

Something is getting in the way, but what?  

I once read something like this (see link below) about the default keyring getting in the way.  Could this be it or something like it?

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by Hadaka on 2013-07-06
Hi, thought id'e join in on the fun !
please post the output of..
```
grep "a4:17:31:af:77:31" /etc/udev/rules.d/70-persistent-net.rules
```
*might want to copy and paste that command.
thanks.

---

### Post by pretty_whistle on 2013-07-06
> **Hadaka said:**
> Hi, thought id'e join in on the fun !
please post the output of..
```
grep "a4:17:31:af:77:31" /etc/udev/rules.d/70-persistent-net.rules
```
*might want to copy and paste that command.
thanks.
There was no output.

---

### Post by Hadaka on 2013-07-06
ok, this "might: be an 'AH HA! ' moment..we shall see..
please attempt that command again,by copy and paste...
then do..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
post the output...
thanks.

---

### Post by pretty_whistle on 2013-07-06
> **Hadaka said:**
> ok, this "might: be an 'AH HA! ' moment..we shall see..
please attempt that command again,by copy and paste...
then do..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
post the output...
thanks.

Here it is..........

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:6b:86:0d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:51:fb:c6:60:b2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"



```

---

### Post by Hadaka on 2013-07-06
ok, have you at some time recently
used a different wifi card?...or USB wifi stick??
as in this guy..

PCI device 0x168c:0x001c (ath5k)

---

### Post by pretty_whistle on 2013-07-06
> **Hadaka said:**
> ok, have you at some time recently
used a different wifi card?...or USB wifi stick??
as in this guy..

PCI device 0x168c:0x001c (ath5k)
Well my ubuntu was installed from a disk image which had another wifi card because it was on an older computer.  Then I restored the saved disk image onto this computer which had M$ in it.

---

### Post by Hadaka on 2013-07-06
ok, you'll notice there is no ra0 entry,,,
this .. is from your other machine...

# PCI device 0x168c:0x001c (ath5k) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0" 
we can add it in here...but i need to get some info first..

I also am convinced this is what is causing the problem.
I need to do some research on this and i will be back..
hang in there..i "think" we are close.

---

### Post by pretty_whistle on 2013-07-06
> **Hadaka said:**
> ok, you'll notice there is no ra0 entry,,,
this .. is from your other machine...

# PCI device 0x168c:0x001c (ath5k) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0" 
we can add it in here...but i need to get some info first..

I also am convinced this is what is causing the problem.
I need to do some research on this and i will be back..
hang in there..i "think" we are close.

Ok, Thanx ahead for all your help.  :)

---

### Post by Hadaka on 2013-07-06
ok ..please COPY AND PASTE ALL COMMANDS.
first lets make a copy of your file.. please do..
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old

```
then we will edit the dev rules file..
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```
once in the editor..."#" comment out the wlan0 line..
so it looks like this..
```
# PCI device 0x168c:0x001c (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```
then..ADD the info for your ra0
```
# PCI device 0x103c:0x18ecc (rt2860)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a4:17:31:af:77:31", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"
```
Save and close gedit...
BOOT
report back happy news

---

### Post by pretty_whistle on 2013-07-06
> **Hadaka said:**
> ok ..please COPY AND PASTE ALL COMMANDS.
first lets make a copy of your file.. please do..
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old

```
then we will edit the dev rules file..
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```
once in the editor..."#" comment out the wlan0 line..
so it looks like this..
```
# PCI device 0x168c:0x001c (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```
then..ADD the info for your ra0
```
# PCI device 0x103c:0x18ecc (rt2860)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a4:17:31:af:77:31", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"
```
Save and close gedit...
BOOT
report back happy news

Question about this first:

When you said :
```

then..ADD the info for your ra0

```
ADD the info?  Where do I add it, I dont get it....  :(
Clarify please.

---

### Post by Hadaka on 2013-07-06
no problem, add it to the bottom of the file..
the one you are editing..
as in the gedit window..still confused?

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> no problem, add it to the bottom of the file..
the one you are editing..
as in the gedit window..still confused?
Ok.  But I added it under the wlan entry.  Does that make any difference?

---

### Post by Hadaka on 2013-07-07
thats fine..save and close gedit..boot and give us a report.
thanks.,

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> thats fine..save and close gedit..boot and give us a report.
thanks.,

One more question:

All I was supposed to do was add a # to the beginning of the wlan line, right?

---

### Post by Hadaka on 2013-07-07
YES,,,that is correct....you could actually backspace out
the entire wlan0 entry...but a "#" is fine for now.

---

### Post by varunendra on 2013-07-07
Hey! Nice discovery there Hadaka, I didn't even think about udev rules. I'll sit back and watch for now, but think we could completely do away with those obsolete entries, just to avoid confusion. But yeah, commenting out is same if done correctly. :)

---

### Post by pretty_whistle on 2013-07-07
The problem is still there  :(

---

### Post by Hadaka on 2013-07-07
I think we are on the right track, lets verify there were
no typos and the entries are correct.
please post the output of..
```

cat /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> I think we are on the right track, lets verify there were
no typos and the entries are correct.
please post the output of..
```

cat /etc/udev/rules.d/70-persistent-net.rules
```
thanks.
Here it is:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:6b:86:0d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x103c:0x18ecc (rt2860)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a4:17:31:af:77:31", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:51:fb:c6:60:b2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"




```

---

### Post by pretty_whistle on 2013-07-07
The driver is rt3290sta, not 2860.

:)

---

### Post by varunendra on 2013-07-07
> **pretty_whistle said:**
> The driver is rt3290sta, not 2860.

:)

Actually, these ralink drivers do have this weird way of having multiple aliases, and rt2860 is what most part of the OS recognizes this driver with (just take a look at "lspci -nnk | grep -iA2 net", or "nm-tool" to see what driver they show to be in use ;)). If I remember correctly, the "rt2860" is the correct name that this particular file refers this driver with.

Did you try the changes I suggested in post #39 ? Taking a look at the link you gave in post 40 now.. although I thought *steeldriver* ruled that out in post #18.


**PS:**
And yes, since this is an image of another installation, IF you have changed the password after restoring the image, then the "keyring password" can be an issue.

---

### Post by Hadaka on 2013-07-07
thats correct, you'll notice that line has a "#"
so its just a comment. "Human readable line"
the entry for the ra0 should have been added to /udev/rules
by the system when it was added...It is showing as ra0 with the correct mac
address in the ifconfig printout. but never got written to udev rules. why, I
have no idea.You only have to do one click on the connect button to get it going,
but you shouldnt have to do that.You'll notice for the Eth1 entry in the udev rules,
even though its a "#"comment line...it shows more info on the card with data from
/sys/devices. and the non exsistant  cards from the old machine + the ra0 entry do not
have additional information.How and exactly where all this magic happens and which files
are involved is unknown to me at this point.
One question i do have ..or rather a couple...is
1. Is this a dual boot machine...Ubuntu/windows ?
2. When you created the disk image from the old machine..was it the same brand...dell,hp,,whatever?

---

### Post by pretty_whistle on 2013-07-07
> **varunendra said:**
> Actually, these ralink drivers do have this weird way of having multiple aliases, and rt2860 is what most part of the OS recognizes this driver with (just take a look at "lspci -nnk | grep -iA2 net", or "nm-tool" to see what driver they show to be in use ;)). If I remember correctly, the "rt2860" is the correct name that this particular file refers this driver with.

Did you try the changes I suggested in post #39 ? Taking a look at the link you gave in post 40 now.. although I thought *steeldriver* ruled that out in post #18.


**PS:**
And yes, since this is an image of another installation, IF you have changed the password after restoring the image, then the "keyring password" can be an issue.

Did I try the change?  Nope, too chicken to mess with it.

I never changed the password so the keyring thing shouldnt be an issue. :)

> **Hadaka said:**
> thats correct, you'll notice that line has a "#"
so its just a comment. "Human readable line"
the entry for the ra0 should have been added to /udev/rules
by the system when it was added...It is showing as ra0 with the correct mac
address in the ifconfig printout. but never got written to udev rules. why, I
have no idea.You only have to do one click on the connect button to get it going,
but you shouldnt have to do that.You'll notice for the Eth1 entry in the udev rules,
even though its a "#"comment line...it shows more info on the card with data from
/sys/devices. and the non exsistant  cards from the old machine + the ra0 entry do not
have additional information.How and exactly where all this magic happens and which files
are involved is unknown to me at this point.
One question i do have ..or rather a couple...is
1. Is this a dual boot machine...Ubuntu/windows ?
2. When you created the disk image from the old machine..was it the same brand...dell,hp,,whatever?

Its not a dual boot.

Same brand?  Yes it is, an HP.

---

### Post by varunendra on 2013-07-07
> **pretty_whistle said:**
> Did I try the change?  Nope, too chicken to mess with it.

There was a time when I used to be too chicken to suggest them :P
But you should really try them. The AES vs TKIP thing is always recommended for any OS, any setup; and the channel thing you can always revert if doesn't help.

---

### Post by Hadaka on 2013-07-07
Hi, I am still digging around trying to get an understanding
how data is written to udev/rules. Meantime, and this may be
a waste of time. With all the editing and driver massage,and connection
attempts,it's possible there is some "confusion" between the router and
the machine. Please try this..
Power down the computer
Power down the router
wait 1...2 minutes
Power on the router...let it sync up...couple minutes
Power on the computer..
then with the ethernet cable UNPLUGGED
connect to the wireless connection...
any difference?

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> Hi, I am still digging around trying to get an understanding
how data is written to udev/rules. Meantime, and this may be
a waste of time. With all the editing and driver massage,and connection
attempts,it's possible there is some "confusion" between the router and
the machine. Please try this..
Power down the computer
Power down the router
wait 1...2 minutes
Power on the router...let it sync up...couple minutes
Power on the computer..
then with the ethernet cable UNPLUGGED
connect to the wireless connection...
any difference?
I dont have a router but I did it with the modem.  

No difference.

---

### Post by Hadaka on 2013-07-07
OK,please post the output of..
```
modinfo rt3290sta
modinfo rt2860
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> OK,please post the output of..
```
modinfo rt3290sta
modinfo rt2860
```
thanks.

Here's modinfo rt3290sta
```

filename:       /lib/modules/3.2.0-48-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     13F483178C6DF2E02D874C3
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-48-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)



```

Here's modinfo rt2860
```

ERROR: modinfo: could not find module rt2860



```

---

### Post by Hadaka on 2013-07-07
thanks. I'de like to try something but i need some info first.
1. Do you currently have an ethernet connection...hardwired?
2.post the output of..
```
cat /etc/udev/rules.d/70-persistent-net.rules.old
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> thanks. I'de like to try something but i need some info first.
1. Do you currently have an ethernet connection...hardwired?
2.post the output of..
```
cat /etc/udev/rules.d/70-persistent-net.rules.old
```
thanks.
Hardwired?  No, and I deleted it from network connections.

Here's the output:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:6b:86:0d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:51:fb:c6:60:b2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"



```

---

### Post by Hadaka on 2013-07-07
ok,interesting..
please write this command down on paper..
yup-pencil/pen-paper..
```
mv /etc/udev/rules.d/70-persistent-net.rules.old /etc/udev/rules.d/70-persistent-net.rules
```
*Note there is a space between old and /
In the event you need to recover the rules file...simply boot...bring up a terminal...and enter the above command.
USE ONLY if after the following prevents you from connecting.
------------------------------------------------------------------------
ok...this will clean up your udev/rules and get rid of things from the other machine..
please do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
then do and post the output of..
```
cat /etc/udev/rules.d/70-persistent-net.rules 
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok,interesting..
please write this command down on paper..
yup-pencil/pen-paper..
```
mv /etc/udev/rules.d/70-persistent-net.rules.old /etc/udev/rules.d/70-persistent-net.rules
```
*Note there is a space between old and /
In the event you need to recover the rules file...simply boot...bring up a terminal...and enter the above command.
USE ONLY if after the following prevents you from connecting.
------------------------------------------------------------------------
ok...this will clean up your udev/rules and get rid of things from the other machine..
please do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
then do and post the output of..
```
cat /etc/udev/rules.d/70-persistent-net.rules 
```
thanks.

Here's the output for cat /etc/udev/rules.d/70-persistent-net.rules
```

cat: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory

```

---

### Post by Hadaka on 2013-07-07
ok,pretty much what i expected, with the exception i would think
something should have been written for the "eth" ethernet connection.
are you currently using the wireless..connection to send this info here?
and is there a reason you deleted the wired connection? and lastly..
did you boot?

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok,pretty much what i expected, with the exception i would think
something should have been written for the "eth" ethernet connection.
are you currently using the wireless..connection to send this info here?
and is there a reason you deleted the wired connection? and lastly..
did you boot?
Yes, I'm using the wireless in question.

The reason I deleted the wired connection was because I thought maybe it could try to connect to that instead of the wireless and doing so could delay the wireless from starting.

And yes, I booted.

---

### Post by Hadaka on 2013-07-07
ok,understandable, the wired doesnt seem to be
having any conflict with the wireless..probably best
to add it back in,especially in the event messing with
all these files kills the wireless..at least you will have a way
so send and get data..Lets do 2 things in one action...
please add back in your wired connection.
then boot. and post the output of.
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
with the wired reconnected,it should create a new /etc/udev file...
please post the output..
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok,understandable, the wired doesnt seem to be
having any conflict with the wireless..probably best
to add it back in,especially in the event messing with
all these files kills the wireless..at least you will have a way
so send and get data..Lets do 2 things in one action...
please add back in your wired connection.
then boot. and post the output of.
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
with the wired reconnected,it should create a new /etc/udev file...
please post the output..
thanks.
Here:

```

cat: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory

```

---

### Post by Hadaka on 2013-07-07
ok,please post the output of.
```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules.old
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok,please post the output of.
```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules.old
```
thanks.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 88:51:fb:c6:60:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:736937 (736.9 KB)  TX bytes:160496 (160.4 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:323498 (323.4 KB)  TX bytes:323498 (323.4 KB)


ra0       Link encap:Ethernet  HWaddr a4:17:31:af:77:31  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:feaf:7731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240055 errors:4 dropped:0 overruns:0 frame:0
          TX packets:50368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84227500 (84.2 MB)  TX bytes:9210819 (9.2 MB)
          Interrupt:18 

```

cat /etc/udev/rules.d/70-persistent-net.rules.old
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:6b:86:0d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:67:55:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:51:fb:c6:60:b2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"



```

---

### Post by Hadaka on 2013-07-07
ok, doesnt ok like this is going to be an "ah ha" moment afterall ;)
When you booted...it should have re-witten the /ect/udev file..
so ..one more time....with the ethernet cable plugged in..please 
BOOT 
then do..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules 
```
**IF it comes back,,no directory found...then COPY and paste
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules.old /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok, doesnt ok like this is going to be an "ah ha" moment afterall ;)
When you booted...it should have re-witten the /ect/udev file..
so ..one more time....with the ethernet cable plugged in..please 
BOOT 
then do..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules 
```
**IF it comes back,,no directory found...then COPY and paste
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules.old /etc/udev/rules.d/70-persistent-net.rules
```
thanks.
The 1st one failed because it said no such file.  The last one didnt produce anything.

---

### Post by Hadaka on 2013-07-07
ok,the saying nothing...means...it did it..
which is better than being constantly asked...are you sure?:)

reading the last few posts...im curious...on post #75 i asked you to BOOT
then enter a command..
then in post #77 more commands..this time..ifconfig
then...post 79...i think...is the ifconfig output...the BIG question is...
did you do the boot in post 75 and did you at anytime after that boot
manually start the wireless?? I know...we have done alot...but do you
remember??

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok,the saying nothing...means...it did it..
which is better than being constantly asked...are you sure?:)

reading the last few posts...im curious...on post #75 i asked you to BOOT
then enter a command..
then in post #77 more commands..this time..ifconfig
then...post 79...i think...is the ifconfig output...the BIG question is...
did you do the boot in post 75 and did you at anytime after that boot
manually start the wireless?? I know...we have done alot...but do you
remember??

I recall.  Yes, I booted in post 75.  Did I at anytime after that boot manually start the wireless?  Yes, nearly every time but not when you said to connect hardwire and do a command and boot.

---

### Post by Hadaka on 2013-07-07
ok, you'll notice in post 78 the wired and wireless are both
up and running, and the wired is named eth0, where as before
it was named eth1. so i am wondering if i missed that while focusing
on the fact that  /etc/udev/rules.d/70-persistent-net.rules did not get
rebuilt. Which didnt really seem to matter. If you are up to it, i would
like to redo a few commands and test...we may have fixed it and missed it.
please first post..
```
ifconfig
```
and let me know if you are up to another hour or so of this
thanks.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok, you'll notice in post 78 the wired and wireless are both
up and running, and the wired is named eth0, where as before
it was named eth1. so i am wondering if i missed that while focusing
on the fact that  /etc/udev/rules.d/70-persistent-net.rules did not get
rebuilt. Which didnt really seem to matter. If you are up to it, i would
like to redo a few commands and test...we may have fixed it and missed it.
please first post..
```
ifconfig
```
and let me know if you are up to another hour or so of this
thanks.
May have fixed but missed it?  Last time I tried it the wireless is still doing the same thing so I dont get it.

---

### Post by pretty_whistle on 2013-07-07
Wait a minute.... thinking back at one point I took the wired out and the wireless just connected by itself! Ah!

Ok, lets keep going.  We appeared to have missed it.

---

### Post by Hadaka on 2013-07-07
ok, I think issues have been created by pretty much cloneing
the other older HP drive and importing all its configurations
on the machine..anyway..
lets give it ago...keep the wired connection attached for now..
then please do..
```
sudo cpy /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
sudo rm /etc/udev/rules.d/70-persistent-net.rules 
```
BOOT
the boot should reset wired and wireless..the following commands should be done from the wired connection
please do not try to start the wireless.
then post
```
ifconfig
```
**IF and ONLY if ifconfig shows eth0 and both wired and wireless running
disconnect the wired and see if the wirless is still running...then boot
again and see if the wireless starts on its own.....is this all clear to you??

---

### Post by pretty_whistle on 2013-07-07
Here......

```

eth0      Link encap:Ethernet  HWaddr 88:51:fb:c6:60:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:782708 (782.7 KB)  TX bytes:163487 (163.4 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97325 (97.3 KB)  TX bytes:97325 (97.3 KB)


ra0       Link encap:Ethernet  HWaddr a4:17:31:af:77:31  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:feaf:7731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19667282 (19.6 MB)  TX bytes:826688 (826.6 KB)
          Interrupt:18 



```

As an fyi, I am using my wireless to post this but the wired info is still in the network connections thing.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok, I think issues have been created by pretty much cloneing
the other older HP drive and importing all its configurations
on the machine..anyway..
lets give it ago...keep the wired connection attached for now..
then please do..
```
sudo cpy /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
sudo rm /etc/udev/rules.d/70-persistent-net.rules 
```
BOOT
the boot should reset wired and wireless..the following commands should be done from the wired connection
please do not try to start the wireless.
then post
```
ifconfig
```
**IF and ONLY if ifconfig shows eth0 and both wired and wireless running
disconnect the wired and see if the wirless is still running...then boot
again and see if the wireless starts on its own.....is this all clear to you??
Oh... Just saw this post.  I'll do it now........

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok, I think issues have been created by pretty much cloneing
the other older HP drive and importing all its configurations
on the machine..anyway..
lets give it ago...keep the wired connection attached for now..
then please do..
```
sudo cpy /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
sudo rm /etc/udev/rules.d/70-persistent-net.rules 
```
BOOT
the boot should reset wired and wireless..the following commands should be done from the wired connection
please do not try to start the wireless.
then post
```
ifconfig
```
**IF and ONLY if ifconfig shows eth0 and both wired and wireless running
disconnect the wired and see if the wirless is still running...then boot
again and see if the wireless starts on its own.....is this all clear to you??

I tried [COLOR=#000000][FONT=Ubuntu Mono]sudo cpy /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
[/FONT][/COLOR]It says cpy command not found.  ?

---

### Post by Hadaka on 2013-07-07
oops..sorry..my error
sudo cp

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> ok, I think issues have been created by pretty much cloneing
the other older HP drive and importing all its configurations
on the machine..anyway..
lets give it ago...keep the wired connection attached for now..
then please do..
```
sudo cpy /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
sudo rm /etc/udev/rules.d/70-persistent-net.rules 
```
BOOT
the boot should reset wired and wireless..the following commands should be done from the wired connection
please do not try to start the wireless.
then post
```
ifconfig
```
**IF and ONLY if ifconfig shows eth0 and both wired and wireless running
disconnect the wired and see if the wirless is still running...then boot
again and see if the wireless starts on its own.....is this all clear to you??

Here is ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 88:51:fb:c6:60:b2  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8a51:fbff:fec6:60b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510288 (510.2 KB)  TX bytes:93776 (93.7 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11902 (11.9 KB)  TX bytes:11902 (11.9 KB)

```

Its not listing wireless, is it?  Is it because I shut off the wireless button before I booted?  Did that mess it up?

---

### Post by Hadaka on 2013-07-07
lol...yes you did, so turn the button back on.

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> lol...yes you did, so turn the button back on.
:D  That's what I thought.
What now?  Should I do the commands over again and this time leave the button on?

---

### Post by Hadaka on 2013-07-07
HI, just make sure the "button" is on...
then boot...see what happens...

should put you in the corner with a windows
machine for that one...:lolflag:

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> HI, just make sure the "button" is on...
then boot...see what happens...

should put you in the corner with a windows
machine for that one...:lolflag:

Lol.  I'll probably have nightmares tonight about windows, haha.

Ok.  I'll go do that now..........

---

### Post by pretty_whistle on 2013-07-07
Hmmm.... Now I paste in the 1st line and I get no such file message.  The 1st line being:
```

sudo cp [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old[/FONT][/COLOR]

```

---

### Post by Hadaka on 2013-07-07
You dont need to run those lines again.
What those commands do is...
copy the udev file to a file of the same name with ...dot old on the end.
we simply backed up the original file and called it filename.old
then deleted the original file..
so all that is done..no need to do again...
turn the button ON
and boot...thats all you need to do...

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> You dont need to run those lines again.
What those commands do is...
copy the udev file to a file of the same name with ...dot old on the end.
we simply backed up the original file and called it filename.old
then deleted the original file..
so all that is done..no need to do again...
turn the button ON
and boot...thats all you need to do...
Oh, ok.  :)

---

### Post by pretty_whistle on 2013-07-07
Done booting.
It's still doing it.........

---

### Post by Hadaka on 2013-07-07
If nothing else,its been interesting. I think between
the cloned image and the cobbeled together wireless driver
you may have to put up with clicking the connect button.If you
had a driver that didnt require special treatment, I would suggest
burning a clean 12.04 from a mirror site so you wouldnt have who
knows what from an older system. I am not sure if you will have to reload
files on the next kernel update with your current driver or not, I'll mention it
to Varun and find out.I'm pretty much out of ideas,perhaps varun or someone
else has input. Sorry after all the fun, that it isnt up to speed. Thought for a bit
we were close...thanks for the fun !!

---

### Post by pretty_whistle on 2013-07-07
> **Hadaka said:**
> If nothing else,its been interesting. I think between
the cloned image and the cobbeled together wireless driver
you may have to put up with clicking the connect button.If you
had a driver that didnt require special treatment, I would suggest
burning a clean 12.04 from a mirror site so you wouldnt have who
knows what from an older system. I am not sure if you will have to reload
files on the next kernel update with your current driver or not, I'll mention it
to Varun and find out.I'm pretty much out of ideas,perhaps varun or someone
else has input. Sorry after all the fun, that it isnt up to speed. Thought for a bit
we were close...thanks for the fun !!

Yeah I'll put up with it.  It doesnt really hurt anything.

Thanks for the help!  :D

---

### Post by pretty_whistle on 2013-07-08
I have a question if it's not too late to ask.  Would it solve the wireless issue if I upgraded ubuntu to the latest, 13.04?  Maybe it has support for the wireless driver in it?

---

### Post by varunendra on 2013-07-08
> **pretty_whistle said:**
> I have a question if it's not too late to ask.  Would it solve the wireless issue if I upgraded ubuntu to the latest, 13.04?  Maybe it has support for the wireless driver in it?

As far as support is concerned, yes, it has built-in support for your card. But whether it would perform nicely or not is questionable based on some user experience shared on the forums. But then again, only those come here who have problems, who knows if there are hundreds who didn't have any. :)

So I'd suggest to try a live CD first, if it works nicely (rt2800pci driver will be in use), then go ahead. Else, if we needed to compile the same driver there, then it is better to do a fresh install of 12.04 instead, since more than often I've seen freezing issues with 13.04 when using the compiled proprietary driver.

I'd suggest a fresh installation (not image restoration) of 12.04 also in case if the native rt2800pci driver doesn't work well on 13.04. Who knows if it is just some remnants of the previous machine settings that are causing this problem (small, but a problem nonetheless).

Last, just so you know, you can always install the drivers backported from 13.04, thus getting benefit of the newer driver without installing the newer release of the distro.

---

### Post by pretty_whistle on 2013-07-08
> **varunendra said:**
> As far as support is concerned, yes, it has built-in support for your card. But whether it would perform nicely or not is questionable based on some user experience shared on the forums. But then again, only those come here who have problems, who knows if there are hundreds who didn't have any. :)

So I'd suggest to try a live CD first, if it works nicely (rt2800pci driver will be in use), then go ahead. Else, if we needed to compile the same driver there, then it is better to do a fresh install of 12.04 instead, since more than often I've seen freezing issues with 13.04 when using the compiled proprietary driver.

I'd suggest a fresh installation (not image restoration) of 12.04 also in case if the native rt2800pci driver doesn't work well on 13.04. Who knows if it is just some remnants of the previous machine settings that are causing this problem (small, but a problem nonetheless).

Last, just so you know, you can always install the drivers backported from 13.04, thus getting benefit of the newer driver without installing the newer release of the distro.
Thanx for the reply. :)
That gives me some things to think about.

---

### Post by varunendra on 2013-07-08
Before trying any of them, you may give **wicd** a shot. Although I can't think of a reason why it may work when nm can't, but I'm just learning and don't know everything : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by pretty_whistle on 2013-07-09
> **varunendra said:**
> Before trying any of them, you may give **wicd** a shot. Although I can't think of a reason why it may work when nm can't, but I'm just learning and don't know everything : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

I already tried that and it didnt make any difference.

---

### Post by Hadaka on 2013-07-09
Hi, just to satisfy my curiosity, please post the output of..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig
```
Im cruious if this file was ever recreated as it should be..
thanks.

---

### Post by pretty_whistle on 2013-07-09
> **Hadaka said:**
> Hi, just to satisfy my curiosity, please post the output of..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig
```
Im cruious if this file was ever recreated as it should be..
thanks.

Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo cat /etc/udev/rules.d/70-persistent-net.rules
[/FONT][/COLOR]```
cat: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

Output of [/FONT][/COLOR]ifconfig
```

eth0      Link encap:Ethernet  HWaddr 88:51:fb:c6:60:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1230010 (1.2 MB)  TX bytes:1230010 (1.2 MB)


ra0       Link encap:Ethernet  HWaddr a4:17:31:af:77:31  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:feaf:7731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3594241 errors:10 dropped:0 overruns:0 frame:0
          TX packets:502792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1314371439 (1.3 GB)  TX bytes:61725636 (61.7 MB)
          Interrupt:18 

```

---

### Post by Hadaka on 2013-07-09
ok, thanks, that file gets created when com devices are detected,
as in wired and wireless cards.You currently write eth0 and ra0
in your ifconfig file,but the /etc/udev file never gets written. I suspect
this is being caused by the data you imported from the older HP image.
You might want to consider varun's suggestion and download a fresh
12.04 or 13.04 If you decide to do so,be sure to use the wired connection
when you request the load. And of course when it asks if you want to overwrite
current os, say yes. More than likely the wireless will not work at first and will
require a little massage.
Let us know what you decide.
thanks.

---

### Post by pretty_whistle on 2013-07-09
> **Hadaka said:**
> ok, thanks, that file gets created when com devices are detected,
as in wired and wireless cards.You currently write eth0 and ra0
in your ifconfig file,but the /etc/udev file never gets written. I suspect
this is being caused by the data you imported from the older HP image.
You might want to consider varun's suggestion and download a fresh
12.04 or 13.04 If you decide to do so,be sure to use the wired connection
when you request the load. And of course when it asks if you want to overwrite
current os, say yes. More than likely the wireless will not work at first and will
require a little massage.
Let us know what you decide.
thanks.
A fresh install seems like too much trouble to me, for right now at least, because all my stuff will get removed.

---

### Post by Hadaka on 2013-07-10
Hi, I have been digging around and found a command
that "may" help with re-creating your /etc/udev file..
please do..
```
udevadm trigger --action=add
```
BOOT
then do..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules
```
post the results.
thanks.

---

### Post by pretty_whistle on 2013-07-10
> **Hadaka said:**
> Hi, I have been digging around and found a command
that "may" help with re-creating your /etc/udev file..
please do..
```
udevadm trigger --action=add
```
BOOT
then do..
```
sudo cat /etc/udev/rules.d/70-persistent-net.rules
```
post the results.
thanks.

Oops.  I shouldve said something yesterday but I decided to try upgrading the OS.
Sorry about that.

---

### Post by pretty_whistle on 2013-07-10
I'm having bad luck.  I upgraded to 12.10 but it doesnt have the wireless driver, 13.04 has one but it wont let me upgrade to it. I cant get it through update manager either.

---

### Post by Hadaka on 2013-07-10
hi, try this
```
sudo modprobe rt2800 pci
```
wireless working?

---

### Post by pretty_whistle on 2013-07-10
> **Hadaka said:**
> hi, try this
```
sudo modprobe rt2800 pci
```
wireless working?
I got this when I tried it:

```

FATAL: Module rt2800 not found.

```

---

### Post by Hadaka on 2013-07-10
the joys of 12.10, now that you have 12.10 loaded
you "should" be able to upgrade to 13.04
12.10 doesnt seem to like the rt3290sta driver either.

---

### Post by pretty_whistle on 2013-07-10
Hmmm... The updater is offering me Xubuntu 13.04 as an upgrade.  Very funny.

---

### Post by pretty_whistle on 2013-07-10
I want Ubuntu 13.04 not Xubuntu.

---

### Post by Hadaka on 2013-07-10
no problem, please post the output of..
```
arch
```
thanks.

---

### Post by pretty_whistle on 2013-07-10
> **Hadaka said:**
> no problem, please post the output of..
```
arch
```
thanks.
Here it is:

```

i686

```

---

### Post by Hadaka on 2013-07-10
ok, you are 32bit..
go here..[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
choose 32bit 13.04...you can also choose to donate
or not to donate.

---

### Post by pretty_whistle on 2013-07-10
> **Hadaka said:**
> ok, you are 32bit..
go here..[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
choose 32bit 13.04...you can also choose to donate
or not to donate.
I got that.  It's not allowing an upgrade.  It only wants to do a fresh install. :(

---

### Post by pretty_whistle on 2013-07-10
I'm hoping this will solve it:
```

sudo do-release-upgrade

```
Here it goes.........

---

### Post by pretty_whistle on 2013-07-10
Well it worked.  :)

However a couple other problems have appeared as a result:

1. suspend doesnt work.
2. weird error appears after powering up.

That's for another thread......

---


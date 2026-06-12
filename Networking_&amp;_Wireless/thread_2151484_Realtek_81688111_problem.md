---
title: "Realtek 8168/8111 problem"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by vadimkolchev on 2013-06-04
Hi all. Got a connection problem. Have Realtek 8168/8111 NIC on my Asus mobo. Right after boot it doesn't give any signs of life - even led is not blinking. The only thing for me is after boot into OS to turn autonegotiation off or to set speed 10 duplex half settings on it. Then it begins to work.

What I tried:
1) change bios settings
2) compile driver from official website

Nothing helps.

---

### Post by varunendra on 2013-06-04
Welcome to the forums vadimkolchev!

> **vadimkolchev said:**
> What I tried:
1) change bios settings
2) compile driver from official website

Nothing helps.

Did you try resetting the BIOS? Worked for someone here (although the problem wasn't exactly the same) : [http://ubuntuforums.org/showthread.php?t=2149142&p=12669115#post12669115](http://ubuntuforums.org/showthread.php?t=2149142&p=12669115#post12669115)

If that doesn't help, please post outputs of :
```
sudo lshw -C network
lsmod
nm-tool
sudo mii-tool
```

---

### Post by Bucky Ball on 2013-06-04
*Thread moved to **Networking & Wireless**.*

Welcome. ;)

---

### Post by vadimkolchev on 2013-06-05
Thanks guys for a warm welcome.

First of all I'd like to indicate that I have ASUS mobo and it is different from a GIGABYTE one and it differs in BIOS as well. In GIGABYTE mobos BIOS has some settings that are not present in ASUS ones. I tried all the options and none of them solved my issue. That's why I'm providing the outputs as you requested. I have the same module used as in the specified link you gave me. However, my mobo is brand new and I never had windows installed.

[http://pastebin.com/4AadPYUj](http://pastebin.com/4AadPYUj)
[http://pastebin.com/xWLg7QZZ](http://pastebin.com/xWLg7QZZ)
[http://pastebin.com/TYpbmxxX](http://pastebin.com/TYpbmxxX)
[http://pastebin.com/7KnxKiNc](http://pastebin.com/7KnxKiNc)

Thanks for trying to help! And sorry for the first paste - have Russian language.

---

### Post by benzarti on 2013-06-05
also try with :
ethtool eth0

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> First of all I'd like to indicate that I have ASUS mobo and it is different from a GIGABYTE one and it differs in BIOS as well.
I'd still recommend to do a BIOS reset. I have extensively used both Asus and Gigabyte Motherboards and am aware of the BIOS differences (American Megatrends vs Award). The fact is, none of the BIOS programs I know of is supposed to change its NIC settings by itself. But somehow it is happening with this particular chip (and perhaps some others).

As far as I know, "link=no" in lshw output can only mean that either there is no physical connectivity (bad cable, bad port, bad connector), or there is a problem at physical layer protocols. In the former case, changing cable/ports should fix the issues (yes, even if a lower speed works, it can still mean a bad contact). But if that does not fix issues, then a 'stuck' firmware, or misconfigured port/IRQ are the only reasons I can think of that can cause communication problem at physical layer. And resetting BIOS is the best way to fix it (sometimes perhaps the only way to fix an 'onboard' port).

Oh, and I didn't see any traces of the proprietary driver (r8168). Did you remove it when it didn't work?

---

### Post by vadimkolchev on 2013-06-05
1. BIOS reset done with pulling out battery and waiting for 4-5 minutes before putting it back - no luck.
2. The cable is ok, that's for sure, as well as connectivity.
3. Yes, I did remove the driver after it didn't change anything to positive
4. Actually I can make it work, but it works at half of its speed. What I can do is turn autonegotiation off and it magically becomes alive and gets the link instantly. Also I can pass to NIC such options as speed 10 duplex half - it is the only mode it works in linux, but I have to do it every time after boot and in terms of performance it is not what I need because it reduces speed significantly.

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> 4. Actually I can make it work, but it works at half of its speed. What I can do is turn autonegotiation off and it magically becomes alive and gets the link instantly. Also I can pass to NIC such options as speed 10 duplex half - it is the only mode it works in linux, but I have to do it every time after boot and in terms of performance it is not what I need because it reduces speed significantly.

How do you do that? Using ethtool ?
As mentioned in the manpage of ethtool, some devices can have issues with autonegotiation. So which device are you connecting to? Brand/Model, capabilities etc.

And does turning off autonegotiation alone enables the link?

By the way, 10Mb/s half duplex is not 'half' of its performance, it is 1/200th of the performance your adapter can deliver :( (1000Mb/s full duplex). But usually 100Mb/s full duplex is what it works at.

Try a full power cycle at the router/switch/modem it is connecting to (power-off > wait for about 4 min > power on again). Then force 100Mb/s full-duplex -
```
sudo mii-tool -F 100baseTx-FD
```
I'm not sure about the sequence of power cycle, so try it once more after forcing above speed if the link doesn't turn on.

To me, it almost certainly seems to be a problem between the firmwares of the NIC and the device it is connecting to, but I'm not too experienced with these and I may be wrong.

If it doesn't help, please post -
```
sudo ethtool eth0
dmesg | grep -iE 'eth|r81|firm|network'
cat /var/log/syslog | grep -iE 'eth|r81|firm|network'
```

---

### Post by vadimkolchev on 2013-06-05
Yes, I'm doing this using ethtool. My device is Realtek 8168/8111f. Setting 10mb/s and duplex half has the same effect as turning autoneg off - both variants work. Also tried to poweroff and poweron and tried all the modes - only that one works and if I switch autoneg off, actually it goes to the same mode I mentioned. It is not even blinking, as if there is no cable plugged in, but after turning autoneg off it begins to work. Everybody says r8169 driver is the one that surely must work with this nic.
Here are the pastes you asked for - [http://pastebin.com/FYZ8kxjD](http://pastebin.com/FYZ8kxjD)
[http://pastebin.com/Xi7NVHN5](http://pastebin.com/Xi7NVHN5)

The third one is too long, because I have wlan0 iface working now. Do you need it? How can I narrow the search?

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> The third one is too long, because I have wlan0 iface working now. Do you need it? How can I narrow the search?

Cut it down to, say, last 40-50 lines -
```
cat /var/log/syslog | grep -iE 'eth|r81|firm|network' | tail -50
```
But you should make sure suspicious messages, if any, are not left out. If there are, include them manually.

---

### Post by vadimkolchev on 2013-06-05
Here you are. But I think it is not what you need [http://pastebin.com/QeJcGrgh](http://pastebin.com/QeJcGrgh) There is a lot of info on wlan0 and couple of errors, however.

---

### Post by vadimkolchev on 2013-06-05
[http://pastebin.com/QeJcGrgh](http://pastebin.com/QeJcGrgh)  Here it is, though I'm not sure it can help, as there are a lot of lines on wlan0

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> Here you are. But I think it is not what you need [http://pastebin.com/QeJcGrgh](http://pastebin.com/QeJcGrgh) There is a lot of info on wlan0 and couple of errors, however.
Yeah, indeed it has nothing interesting. It is when the ethernet has been dealt with. I'm afraid you'll have to analyse the syslog manually, then post back if anything looks suspicious. Or just post the full syslog if pastebin allows.

Also, when I asked "which device you are connecting to", I meant the router/switch/modem, not the NIC. I may look up the model to see if there are any known problems with it. As far as the NIC/driver is concerned, it seems there is a sudden rise in complaints recently. But the only one I dealt with was fixed by BIOS resetting (the one I linked to). Other than that, I couldn't find yet any substantial hints about what is causing these problems.

Since you have already tried the proprietary driver, I'm afraid I may not be able to help if we couldn't find any hints about the problem.

If no one else jumps in with any more suggestions, then as a last resort, you may wish to find a PCI card that works with Ubuntu.

---

### Post by vadimkolchev on 2013-06-05
[http://pastebin.com/4f228RbY](http://pastebin.com/4f228RbY) - here is a better one

Actualy I have a router, and a wi-fi hotspot. In my case nic is physically connected with a hotspot.

Oops, I seem to have found where the problem is, but I don't know how to deal with it. I tried to connect my nic not to hotspot, but to router - and it woke up.

---

### Post by albandy on 2013-06-05
> **vadimkolchev said:**
> [http://pastebin.com/4f228RbY](http://pastebin.com/4f228RbY) - here is a better one

Actualy I have a router, and a wi-fi hotspot. In my case nic is physically connected with a hotspot.

Oops, I seem to have found where the problem is, but I don't know how to deal with it. I tried to connect my nic not to hotspot, but to router - and it woke up.

Try with a crossover cable.

---

### Post by varunendra on 2013-06-05
Hmm.. was about to post regarding this -> **vadimkolchev said:**
> [http://pastebin.com/4f228RbY](http://pastebin.com/4f228RbY) - here is a better one you left out 'network' from grep,... smart ;)

However, saw this edit -
> Oops, I seem to have found where the problem is, but I don't know how to deal with it. I tried to connect my nic not to hotspot, but to router - and it woke up.
-reaffirms my doubt on the firmware on the 'other side' of the cable. So, what exact model is this hotspot? Looks like it does not like your NIC (or linux kernel handling it), but does like the router. :)

---

### Post by vadimkolchev on 2013-06-05
it is TP-LINK WR340G 4.0

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> it is TP-LINK WR340G 4.0

Check your firmware version and see if the one they are providing is an upgraded one : [http://www.tp-link.com/en/support/download/?model=TL-WR340G&version=V4#tbl_j](http://www.tp-link.com/en/support/download/?model=TL-WR340G&version=V4#tbl_j)
If it is, try an upgrade (backup the settings first as it will be overwritten). There are a couple of improvements in the newer one, as mentioned on the download page. *([COLOR="#FF0000"]Edit :[/COLOR] Or maybe not, if yours is not version WR340G(D)_v4)*

By the way, what is the problem in connecting to the router if you have one and is working better?

---

### Post by vadimkolchev on 2013-06-05
Just upgraded, the same problem persists. I can't connect straight to the router because it has only 1 port, while TP-LINK has 4. And I have 2 PCs. So now I do have 2 pcs connected to TP-LINK. I noticed that if I change ports, everything starts to work and my NIC is awake until I shut down PC.

---

### Post by varunendra on 2013-06-05
> **vadimkolchev said:**
> I noticed that if I change ports, everything starts to work and my NIC is awake until I **shut down PC**.
Does that mean it is something that can be considered a fix/workaround? What do you mean by "until shutdown"? Does the problem return after a reboot, requiring you to change ports again?

I can't really think of anything else other than believing it is a firmware bug (in either the hotspot or the NIC, which seems rather new) since we are getting no hints in either dmesg or syslog suggesting otherwise. Maybe you can take a close look at complete syslog *(in a fresh reboot, to get much fewer lines to be analysed in syslog ;))* once more and see if there are any clues being left out due to the filters in our grep command.

---

### Post by vadimkolchev on 2013-06-06
> Does that mean it is something that can be considered a fix/workaround?  What do you mean by "until shutdown"? Does the problem return after a  reboot, requiring you to change ports again?
Yes, exactly

Also I cannot see anything of real help in syslog and in dmesg - everything is the same there.

---


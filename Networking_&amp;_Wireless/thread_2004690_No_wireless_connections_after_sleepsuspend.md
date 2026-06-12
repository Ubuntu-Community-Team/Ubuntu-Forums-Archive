---
title: "No wireless connections after sleep/suspend"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by SkyJP on 2012-06-16
Recently, I've setup a dual boot with Ubuntu 12.04 and everything seems to be going fine. 

The networking works perfectly, until I access sleep mode/suspend. After that, when I logon, the wireless connection is lost. I attempted to connect via 'connecting to a hidden wireless network' and entered the password, but it takes a long time to connect and eventually prompts me for the password again without acquiring connection.

After I reboot, however, WiFi works again.

 Network controller: Intel Corporation Centrino Wireless-N 130

If you tell me how to fix it with commands, if you don't mind, please tell me what the commands do as I'm new to Ubuntu =\

---

### Post by chili555 on 2012-06-16
This technique sometimes, but not always works. We are going to add a file that tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume. The driver we'll unload and reload is your wireless driver *iwlwifi*. Let's use the text editor gedit to write a file. Since it's a location owned by root, we'll need to temporarily gain administrative privileges with sudo:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlwifi"
```Proofread carefully, save and close gedit. Reboot.

How does it work now?

---

### Post by SkyJP on 2012-06-16
Thank you, so far it has worked perfectly ;)

---

### Post by chili555 on 2012-06-16
Please use thread tools at the top to mark Solved so the searchers can find it.

**Note to searchers**: your wireless driver may not be iwlwifi. Please check and ask if in doubt.

---

### Post by ping-wu on 2012-06-20
> **chili555 said:**
> This technique sometimes, but not always works. We are going to add a file that tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume. The driver we'll unload and reload is your wireless driver *iwlwifi*. Let's use the text editor gedit to write a file. Since it's a location owned by root, we'll need to temporarily gain administrative privileges with sudo:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlwifi"
```Proofread carefully, save and close gedit. Reboot.

How does it work now?

Followed your procedure.  Now my 12.04 won't suspend?

---

### Post by chili555 on 2012-06-20
> **ping-wu said:**
> Followed your procedure.  Now my 12.04 won't suspend?I've never heard that complaint before. Please check that your driver is actually correct if not *iwlwifi* and also that no typing errors were made.

---

### Post by watgrad on 2012-06-21
Thanks for this - I was having the same problem on my macbookpro8,1
This solved it.
My driver was "b43" for any other mac users looking for a solution to the suspend problem.
(Linux mint 13 - ubuntu 12.04 derivative)

---

### Post by chrismatinez81 on 2012-06-23
i have BCM4312 802.11b/g LP-PHY installed as my driver what do i put SUSPEND_MODULES="" "" i tried SUSPEND_MODULES=BCM4312 and BCM4312 802.11b/g LP-PHY but they both dont work can you help me please

---

### Post by chili555 on 2012-06-23
> **chrismatinez81 said:**
> i have BCM4312 802.11b/g LP-PHY installed as my driver what do i put SUSPEND_MODULES="" "" i tried SUSPEND_MODULES=BCM4312 and BCM4312 802.11b/g LP-PHY but they both dont work can you help me pleaseI am sure that those are not the name of your driver. Please run:```
sudo lshw -C network
```This will take a few moments; please be patient. Look for your wireless device and see what is says at *driver=*. Then amend the file to include the exact name of the driver in quotes. It might be this, but _check_ and _confirm_:```
SUSPEND_MODULES="b43"
```

As a very famous man once said, "Trust but verify."

---

### Post by chrismatinez81 on 2012-06-25
> **chili555 said:**
> I am sure that those are not the name of your driver. Please run:```
sudo lshw -C network
```This will take a few moments; please be patient. Look for your wireless device and see what is says at *driver=*. Then amend the file to include the exact name of the driver in quotes. It might be this, but _check_ and _confirm_:```
SUSPEND_MODULES="b43"
```

As a very famous man once said, "Trust but verify."

thats my driver but its still not working.  i have another question im on mint 13 cinnamon when i change my power setting for my screen i set it to never turn off but it still does. i have looked online but cant find anything please let me know if you know how to fix this problem
thanks

---

### Post by chili555 on 2012-06-25
I'm sorry, I know of no other techniques. As I said above, the one I do know sometimes but not always works.

You might post in General Help and reference suspend in the thread title. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by fgmart on 2012-09-23
This solution totally worked for me -- Ubuntu 12.04 on a Lenovo ideapad u460.  Super!  Thanks!

 -- adding SUSPEND_MODULES="iwlwifi" to /etc/pm/config.d/config

Fred

---

### Post by MikeFlint on 2012-11-21
I'd just like to add a "me too" on the "it works!" front.

On 12.04 - suspend working with WiFi fine until kernel upgrade to Kernel Linux 3.2.0-33-generic-pae, then only coming back to life if I reset the router or re-booted.

Adding the kill/restart code for iwlwifi and so far, all good.

Possibly kernel ... at same time I upgraded to Cinnamon 1.6.7 but don't think that can be relevant. Using WICD, not NM.

****EDIT****
Have removed this patch in 14.04 (remember to remove all your patches between upgrades or you might break fixes that have been made!)

Suspend issues with WiFi no longer occur.

---

### Post by forums4me on 2012-12-11
This is still sot working as far as I am concerned.

Configuration:

Ubuntu 12.04.1 LTS x64
Samsung 700Z3C

[This]("http://www.techytalk.info/ubuntu-fix-network-stopped-working-after-resume-from-sleep/") -- which seems to be the same -- seem to have temporarily worked but that's it.
[]("http://www.techytalk.info/ubuntu-fix-network-stopped-working-after-resume-from-sleep/")

---

### Post by alanchevelleboy on 2013-08-27
> **chili555 said:**
> This technique sometimes, but not always works. We are going to add a file that tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume. The driver we'll unload and reload is your wireless driver *iwlwifi*. Let's use the text editor gedit to write a file. Since it's a location owned by root, we'll need to temporarily gain administrative privileges with sudo:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlwifi"
```Proofread carefully, save and close gedit. Reboot.

How does it work now?

Thanks I had this same problem with my custom built PC. now I need to find one for lubuntu 12.04 live cd then I can use the laptop without restarting after a suspend

---

### Post by Sarab_Jeet_Singh on 2013-10-23
Hi. My symptoms are similar. When I go into sleep or suspend mode (OR restart), I always have to delete the most recent network connection and re-add it in the manage connections window. The problem is not life or death by any means, I can still carry on with my web activities, just a hassle. Additionally, I really like the suspend/sleep/hibernate feature and use it often, so it is unusually troublesome.

When I followed the procedure in this thread I wasn't sure if I did the gedit part correctly. What threw me off, was that there were no contents to the file that opens. So that the one line we are supposed to enter:

SUSPEND_MODULES="wl0"
 
is all that shows up in the editor.

Anyway, I tried the procedure and it didn't work. In fact I am about to try it again and I'll report back. (UPDATE: no change)

Any help would be nice.

Thanks and god bless you

---

### Post by chili555 on 2013-10-24
> SUSPEND_MODULES="wl0"I think it should be, instead:```
SUSPEND_MODULES="wl"
```Please change it and let us have your report.

---

### Post by minos.masterchief on 2013-11-20
> **chili555 said:**
> I am sure that those are not the name of your driver. Please run:```
sudo lshw -C network
```This will take a few moments; please be patient. Look for your wireless device and see what is says at *driver=*. Then amend the file to include the exact name of the driver in quotes. It might be this, but _check_ and _confirm_:```
SUSPEND_MODULES="b43"
```

As a very famous man once said, "Trust but verify."

Thanks, this worked perfectly for me.

---

### Post by bpevrancken on 2014-05-10
The above solutions did not help me (ubuntu 14.04). However, when I unmarked IPV6 settings (from automatic to ignore) I immediately got wireless connection after resuming from sleep mode.

---

### Post by HDTimeshifter on 2014-05-11
My wired connection is disabled after resuming from sleep in Ubuntu 14.04 LTS and trying to select Enable Networking from the pulldown menu at the upper right doesn't enable it - I have to reboot. I tried changing IPV6 from automatic to ignore as bpevrancken did above and that didn't work. Is there a wired driver I can specify to unload and reload in my config file?

---

### Post by chili555 on 2014-05-12
> **HDTimeshifter said:**
> My wired connection is disabled after resuming from sleep in Ubuntu 14.04 LTS and trying to select Enable Networking from the pulldown menu at the upper right doesn't enable it - I have to reboot. I tried changing IPV6 from automatic to ignore as bpevrancken did above and that didn't work. Is there a wired driver I can specify to unload and reload in my config file?We can certainly try. Please run:```
sudo lshw -C network
```What does it say for your ethernet device under 'driver='? Just use the same technique as above.

If in doubt, post the result here and we'll be happy to help.

Here is a sample from my machine:```
*-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: xx:de:f1:3e:b2:xx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=[COLOR="#FF0000"]e1000e[/COLOR] driverversion=2.3.2-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
```So my file would read:```
SUSPEND_MODULES="e1000e"
```We will be very interested in your result.

---

### Post by HDTimeshifter on 2014-05-12
>   *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:00:bf:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:fe9c0000-fe9fffff ioport:dc00(size=128)


The below didn't work:
> SUSPEND_MODULES="ATL1E"

---

### Post by chili555 on 2014-05-12
> The below didn't work:
SUSPEND_MODULES="ATL1E"Once in a while and I have no idea why, the name of the driver listed is not the name of the driver!! Please try:```
SUSPEND_MODULES="atl1e"
```And, yes, case, caps, etc. are crucial in Linux.

Of course, then we have the issue that the technique may not work at all in this case and that, further, the issue is somewhere other than the driver dropping on suspend.

---

### Post by HDTimeshifter on 2014-05-13
Lower case didn't work either. Actually I tried manually suspending, then waking it up almost immediately afterward and the LAN wasn't dropped. But then I suspended it and came back a few hours later and the networking is disabled again.

On another note, is your PC fanless? I was thinking of replacing my 2 HDDs (dual boot Ubuntu & Windows 7) with two 240 GB SSDs if I could turn off all or all but one 12 cm fan, but people tell me SSDs still generate almost as much heat. My CPU is a quad-core Q6600, which isn't the most heat efficient either.

---

### Post by chili555 on 2014-05-13
> Actually I tried manually suspending, then waking it up almost immediately afterward and the LAN wasn't dropped. But then I suspended it and came back a few hours later and the networking is disabled again.It probably isn't an issue of the driver dropping then. Check after it doesn't come back up:```
lsmod | grep atl
```If *atl1e* is listed, then the issue isn't the driver. Since yours is an ethernet issue and not wireless, the subject of this thread, I suggest you start a new thread and PM me the link.

As for my NUC, it does have a very quiet fan. To my old ears, it is silent. To my sound level meter, which, I admit, only registers down to 50 dB, it is silent. When I walk across the carpeted floor holding the meter, my footsteps register higher than 50 dB!

NUCs are often used as HTPCs where the sound level is critical.

---

### Post by ubuntone2 on 2014-06-18
Thanks Chilli,

```

SUSPEND_MODULES="iwlwifi"

```

Solved my issue with wifi not reconnecting after resuming from suspend in lubuntu 14.04 with an Intel 3945abg chipset.

Cheers,

Tony

---

### Post by chili555 on 2014-06-18
> **ubuntone2 said:**
> Thanks Chilli,

```

SUSPEND_MODULES="iwlwifi"

```

Solved my issue with wifi not reconnecting after resuming from suspend in lubuntu 14.04 with an Intel 3945abg chipset.

Cheers,

TonyI believe for the 3945, it ought to be:```
SUSPEND_MODULES="iwl3945"
```

---

### Post by None_OYerbiz on 2014-08-01
Just another thank you, Chili555 - your solution seems to have fixed my problem as well (tested twice just now and worked immediately both times).  I found and tried several variations on a theme (putting a script with various commands in /etc/pm/sleep.d/ to execute upon wake - look [here]("http://askubuntu.com/questions/452826/wireless-networking-not-working-after-resume-in-ubuntu-14-04") for an example), but none of them worked.

Adding my relevant details for others who may be searching to find:
Using a Rosewill RNX-N180UBE USB WiFi adapter, it identifies itself as a Realtek RTL8191SU, but XUbuntu is using the r8712u driver (have to see if there's a proper driver for this out there somewhere because my connection dies occasionally), thus the proper line for this device would be:
```
SUSPEND_MODULES="r8712u"
```

---

### Post by HDTimeshifter on 2014-08-01
> **chili555 said:**
> It probably isn't an issue of the driver dropping then. Check after it doesn't come back up:```
lsmod | grep atl
```If *atl1e* is listed, then the issue isn't the driver. Since yours is an ethernet issue and not wireless, the subject of this thread, I suggest you start a new thread and PM me the link.

My problem solved and also works for wireless router that I replaced my wired router with:  [http://ubuntuforums.org/showthread.php?t=2223566]("http://ubuntuforums.org/showthread.php?t=2223566")

---

### Post by shammydog on 2014-08-28
SUSPEND_MODULES="iwlwifi" fix did not work for me.  shrodi's #8 post [here]("http://ubuntuforums.org/showthread.php?t=2218043&p=13110510#post13110510") did!

---

### Post by bikergeek2 on 2015-05-15
Sorry to bump an elderly thread but this problem reared its head after upgrading my Toshiba Satellite C655 laptop to Xubuntu Vivid.

SUSPEND_MODULES="rtl8192ce" didn't work for me, am still trying to find a solution.  Disabling and re-enabling networking works, so perhaps this is not a wireless driver problem but a problem with DHCP.

**ETA:**  looks like I'm experiencing this bug:  [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771)

---

### Post by chili555 on 2015-05-15
Does it help to do:```
sudo service network-manager restart
```Did you register with Launchpad and add your comments to the bug?

---

### Post by gilles-falquet-z on 2015-05-15
Works well for me too (Ubuntu 10.04 on an old iMac 7,1). Thanks

---

### Post by spotfist on 2015-06-04
Hey sorry for the bump but not sure if i need to start a new thread for this, i am having very similar issues as reported by the OP but none of the solutions work including the other solutions i tried from other sites.


I am running on a lenovo thinkpad with drivers "iwl3945" so have added this to the config file 
```
SUSPEND_MODULES="iwl3945" 
```
to /etc/pm/config.d/config  but this doesn't fix the issue.


```
**lsmod grep iwl**
``` 
shows 


iwl3945   63619  0
iwlegaccy 88016  1


so i assume that its not a driver issue


running 
```
**nmcli nm**
``` 
shows that the STATE is disconnected


i have the nm-applet running so i can try and reconnect using that which changes the STATE to connecting but it will only connect randomly. sometimes after a reboot but not every-time. Once connected it is fine until i suspend the laptop again, then back to square one.


any ideas or outputs anyone needs to see just let me know, cheers

---

### Post by spotfist on 2015-06-06
For anyone with similar wireless problems who are unable to resolve or run out of things to try like I did. I decided to re-install Lubuntu.

From a fresh install I updated straight away before installing my apps, I think this is potentially what caused the problems. I now have the laptop to hibernate instead of sleep, works much better now!

---

### Post by jeanj on 2015-07-20
I found that `sudo killall wpa_supplicant` helps, as reported in this thread:
[http://ubuntuforums.org/showthread.php?t=2230072](http://ubuntuforums.org/showthread.php?t=2230072) (edit: this didn't help on a subsequent occasion).

This was not an issue for me in 12.04 ... sad to encounter it in 15.04 ...

---

### Post by kyrachris on 2015-11-01
BTW, this solution works after upgrading to 15.10, but you need to mark the file as executable:

```
sudo chmod +x /etc/pm/config.d/config
```

Update: It works, but it appears to fail on occasion. Still need to chmod it.

---

### Post by reduxpl on 2016-08-01
> **chili555 said:**
> ```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlwifi"
```Proofread carefully, save and close gedit. Reboot.

How does it work now?
This exact solution worked for my Dell Latitude E5410. Thank you!

---

### Post by celyse on 2017-05-21
> **chili555 said:**
> Does it help to do:```
sudo service network-manager restart
```Did you register with Launchpad and add your comments to the bug?

Really sorry to be bumping such an old thread, but I'm having this issue as well. I'm running Lubuntu 17.04 on an old Toshiba Satellite (and I'm very new to it!). The code I'm quoting works, but I'd like a more permanent solution so I don't have to type this every time I open my laptop back up. The first solution posted didn't work for me as it looks like /etc/pm/config.d/config doesn't exist on my computer. Has there been a change in the latest version where I might be able to try that solution with a different file?

---

### Post by jeremy31 on 2017-05-21
See if disabling wifi power management helps
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

---

### Post by celyse on 2017-05-21
> **jeremy31 said:**
> See if disabling wifi power management helps
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Looks like that worked, thank you!

---


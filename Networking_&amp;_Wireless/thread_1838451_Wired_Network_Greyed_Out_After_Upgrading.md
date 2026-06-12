---
title: "Wired Network Greyed Out After Upgrading?"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by Skasucks93 on 2011-09-03
EDIT: STILL NEED HELP FIXING WIRED CONNECTION, PROBLEM NOT SOLVED. 

I went from 10.04 to 10.10, and my wired network stopped working. So I used wireless, and then upgraded to 11.04 and now BOTH aren't working and not detected. There's no lights coming from the back of the computer where the ethernet cable is plugged in either. So I formatted, popped in the disc to install ubuntu 10.04 again, and the problem still persists... Note that everything was working great the first time I installed ubuntu 10.04 from my disc. 

How do I fix this? It's like it doesn't detect my drivers. I'm posting from my moms laptop right now...

I will gladly give any information you need, but I'm a total noob to linux and have no clue how to give you that information, so I need to be guided very thoroughly please.

---

### Post by praseodym on 2011-09-03
Hi

please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```
Can you get wired if you remove your profile and reboot?

---

### Post by Skasucks93 on 2011-09-03
How do I remove my profile? It says I can't remove it while in use, and there's no way to delete it while logged out. And hold on with the terminal info, working on it, I have to manually type everything up on here.

---

### Post by praseodym on 2011-09-03
copy/paste the outputs into a .txt file and upload it ;-)

---

### Post by Skasucks93 on 2011-09-03
I attached it

Thank you so much for the help!

rfkill list did nothing by the way.

I decided to try formatting my disk and reinstalling ubuntu, I'll upload a new terminal when it's done.

---

### Post by praseodym on 2011-09-03
I cannot see a wireless device...Can you show

lspci -nnk

completely? You may check your BIOS-settings, if wireless is "off" there.

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> I cannot see a wireless device...Can you show

lspci -nnk

completely? You may check your BIOS-settings, if wireless is "off" there.

Sorry I had it unplugged, please check this thread in 10-15 minutes! I'll have the fresh install information up. It's an asus usb wireless stick.

I'm actually more worried about the wired connection - I need that more so than wireless.

---

### Post by Skasucks93 on 2011-09-03
Ok - should I run commands as an administrator using sudo?

---

### Post by Skasucks93 on 2011-09-03
Ok sorry for the wait, just did a fresh install of 10.04 and formatted. Still the same problem. Here are the terminals you asked for with my ethernet and wireless plugged in. I saw a lot of people had this problem with internet breaking after updating ubuntu, and the only solution I came across was to use a static IP but I cannot do that with my router.

I'm looking at my routers page and it doesn't even detect my ubuntu computer even though it's directly hooked up via ethernet cable.

---

### Post by praseodym on 2011-09-03
Ok, try to add the device IDs to the driver rt2870sta:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
and reload the driver:

```
sudo modprobe -rf rt2870sta
sudo modprobe -v rt2870sta
```
Then re-plugin your stick and check:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by Skasucks93 on 2011-09-03
Did everything you said step by step. Here's the terminal code... still not working btw, same problem (don't know if that was supposed to fix it or not).

Edit: Nevermind! Fixed the wireless, I thought you meant replug my wire.

Edit2: Let me give you the new terminal info with the wireless connected. Hold on.

---

### Post by Skasucks93 on 2011-09-03
Ok now 1 down 1 to go! :) 

Here's the terminal with the wireless connected. Thank you so much for your help, I am so relieved now. Would it be possible for you to guide me through fixing my wired connection now?

---

### Post by praseodym on 2011-09-03
Looks good. Additionally you can setup an udev-rule:

```
gksudo gedit /etc/udev/rules.d/10-wusb100.rules
```
Add:

```
# UDEV-Rule for ID 0b05 1784
SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe rt2870sta"
```
save, close and reload udev:

```
sudo service udev reload
```
and replug your stick.

Now you can install the new/better working wired driver for your device via wireless (copy/paste):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2
tar xvf r8168-8.024.00.tar.bz2
cd r8168-8.024.00
sudo ./autorun.sh
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

Then you should update your system via wired, because kernel 2.6.32-33 is the newest and install the following:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic linux-backports-modules-wireless-$(uname -r) linux-backports-modules-wireless-lucid-generic
```
and reboot.

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> Looks good. Additionally you can setup an udev-rule:

```
gksudo gedit /etc/udev/rules.d/10-wusb100.rules
```Add:

```
# UDEV-Rule for ID 0b05 1784
SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe rt2870sta"
```save, close and reload udev:

```
sudo service udev reload
```and replug your stick.

Now you can install the new/better working wired driver for your device via wireless (copy/paste):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2
tar xvf r8168-8.024.00.tar.bz2
cd r8168-8.024.00
sudo ./autorun.sh
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```Then you should update your system via wired, because kernel 2.6.32-33 is the newest and install the following:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic linux-backports-modules-wireless-$(uname -r) linux-backports-modules-wireless-lucid-generic
```and reboot.

Going to try this now, will update when finished. Could you explain what a udev-rule is?

Edit: I'm mostly through your steps, after replugging my stick i installed the wired driver via copypasta, but don't know what you mean by update my system. Update to 10.10? How do I update to kernal 2.6.32-33 and what is that - for my network drivers or ubuntu? My wired isn't working still, so I can't update via wired yet.

---

### Post by praseodym on 2011-09-03
Try the following: Delete your wired profile in the network-manager applet and reboot. Check if wired works.

No, you are not up[COLOR="Red"]grad[/COLOR]ing the system to 10.10 you are up[COLOR="Red"]dat[/COLOR]ing your system to the up-to-date-status.

---

### Post by praseodym on 2011-09-03
The udev-rule automatically loads the driver if the device is present.

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> Try the following: Delete your wired profile in the network-manager applet and reboot. Check if wired works.

No, you are not up[COLOR=Red]grad[/COLOR]ing the system to 10.10 you are up[COLOR=Red]dat[/COLOR]ing your system to the up-to-date-status.

Wired is still greyed out, I deleted eth0, and rebooted. There are no wired profiles currently listed now. Should I proceed to update my system via wireless? 

And I'm not messing with upgrading today, but just for future reference will these steps that fixed my wireless work if I update to 10.10 and then to 11.04 or would I need to make a whole 'nother thread?

---

### Post by praseodym on 2011-09-03
In "Users&Groups" checkbox all user rights and login again. Then check box "allowed to all users" and "connect automatically", delete the profile again, and reboot.

Is there a MAC-adress-filter turned "on" in your router? Maybe this holds your wired connection back ("new clients allowed" or sth.)? Router settings are DHCP (automatic)?

Check afterwards:

```
ifconfig -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> In "Users&Groups" checkbox all user rights and login again. Then check box "allowed to all users" and "connect automatically", delete the profile again, and reboot.

Is there a MAC-adress-filter turned "on" in your router? Maybe this holds your wired connection back ("new clients allowed" or sth.)? Router settings are DHCP (automatic)?

Check afterwards:

```
ifconfig -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

I actually already checked all user rights because I saw you post that in response to a similar problem :P

There is no network profile showing up for wired, so I don't see a box to check for "allowed to all users" and "connect automatically".

There is no MAC address filter that I'm aware of, I've never turned one on and any computer can just plug in and connect without any problems so I'm assuming there isn't one. 

Edit: Just checked, no filter on my router, it allows all connections. Router settings are DHCP. What's weird is under hardware drivers, RealTek RTL-8168 Gigabit Ethernet driver says this driver is activated but not currently in use, which it didn't say before.

Edit2: Made a new connection for wired and checked allowed to all users and connect automatically. Will upload terminal info in 1 sec.

---

### Post by praseodym on 2011-09-03
Can you load the driver by hand:

```
sudo modprobe -v r8168
sudo service network-manager restart
```

---

### Post by Skasucks93 on 2011-09-03
I'll try that now, here's the term info in case you missed it.

Edit: Tried loading by hand, it did nothing. Still greyed out and it says that the connection was used 'never' in the profile. Tried rebooting too, still not working :\.

Edit2: Under Hardware Drivers, it now says that it's activated and currently in use but it doesn't look like it. Making progress at least.

---

### Post by praseodym on 2011-09-03
The wrong module is still loaded:

```
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
```
Check:

```
ifconfig -a
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep r8
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> The wrong module is still loaded:

```
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
```Check:

```
ifconfig -a
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep r8
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```

When I do sudo modprobe -rf r8169 it says FATAL not found...

---

### Post by praseodym on 2011-09-03
Does:

```
sudo ifup eth0
sudo dhclient eth0
sudo service network-manager restart
```
work? Did you check the cable ("eth0: link is down")?

---

### Post by Skasucks93 on 2011-09-03
Cables fine, was working earlier today, and I just went downstairs to router and checked the back of my comp, it's firmly in place. The wire isn't bunk either. This is such a pain in the ***... 

Still greyed out and not working, tried what you said.

---

### Post by praseodym on 2011-09-03
Reinstalling the network-manager?

```
sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by Skasucks93 on 2011-09-03
> **praseodym said:**
> Reinstalling the network-manager?

```
sudo apt-get install --reinstall network-manager network-manager-gnome
```

I don't think it did anything. Thanks for all your help, I can see you pretty much ran out of solutions. I'll just have to wait, or upgrade to 11.04 and try this all again.

If you could answer one question for me though, would all the steps that you've provided with the wireless help me if I were to update to 11.04? Because if I update, I know the network devices are gonna be messed up again.

---

### Post by praseodym on 2011-09-04
You can try this:

Take all components for 10 minutes _completely_ from the current and rebuild you setup. Maybe some old firmware is stuck somewhere.

As far from my experience this workaround works in Natty.

---


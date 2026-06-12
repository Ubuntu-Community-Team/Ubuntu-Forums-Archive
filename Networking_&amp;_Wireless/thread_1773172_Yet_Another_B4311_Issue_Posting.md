---
title: "Yet Another B4311 Issue Posting"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by faraz.yashar on 2011-06-01
I've (like many others) had a ton of problems getting the card to work with 11.04 on a Dell Inspiron 6400.  I have a working ethernet connection, so anything needing the net shouldn't be a problem.
After the computer started up after the Ubu install, the Broadcom STA wireless driver was installed as recommended through the Additional Drivers dialogue.

Here are the results from running commands to identify the device and loaded modules:
```

$ lspci | grep WLAN
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
$ lspci -nn | grep -i 14e4 (More general results)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
$ modinfo ssb | grep 4311
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*

```> This package contains Broadcom 802.11 Linux STA wireless driverfor [sic] use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.No wireless device was recognized by ifconfig or iwconfig. after a restart.

Using the toggle key combination (Fn+F2) switches blocking from no to yes:
/```

$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no/yes
    Hard blocked: no/yes

```bcmwl-kernel-source has been reinstalled as well.

After installing b43-fwcutter and firmware-b43-installer, and removing the STA driver the solution isn't entirely resolved either although it looks like more progress has been made.

iwconfig now has a wlan0:
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```The network button on the top menu bar now shows a section entitled  "Wireless Networks" with a notice below that states "wireless is  disabled by hardware switch."

The next logical move would be to check rfkill while toggling with Fn+F2:
```

$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no/yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Note that soft blocked is now fixed at yes for dell-wifi , and a new phy0 has appeared.  The notice about "wireless is disabled by hardware switch" remains fixed despite the keyboard toggle.

The hardware switch notification changes to "wireless is disabled" after running [FONT=Book Antiqua]sudo modprobe b43[/FONT].  However, when toggling with the key combination or checking "Enable wireless" in the networking menu item, the "wireless is disabled" notification still remains.

Note that Fn+[Key]  works for other keys (e.g. brightness, battery life, volume.) rfkill seems responsive to the wifi toggle as well.

Cheers and thanks!

---

### Post by chili555 on 2011-06-01
Hello, sir! Glad to see you are here. I love a difficult problem. First, I think the module dell-laptop doesn't correctly recognize your key presses and translate them to information the kernel can use. Please do:```
sudo rmmod -f dell-laptop
```Now does the wireless work? If so, we'll need to amend one file to make it permanent. If not, we'll look into other options.

---

### Post by garvinrick4 on 2011-06-01
Maybe will get your SSID in use below:

sudo ifconfig wlan0 up  (will start radio signal
iwlist wlan0 scan (see if SSID is there)
nm-tool (same more or less a bit better )

These 3 will stop and restart your network manager:
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

If cannot get wifi enabled now would just uninstall all in bcm in Synaptics and reinstall:
Do a 
```
sudo apt-get clean
```wiil then install new packages from repositorys instead of what is in your cache:
###EDIT: Chili555 is very good with Network cards and their drivers:####

---

### Post by faraz.yashar on 2011-06-01
Bingo. ;D

Chili555, I'd say its an understatement to say you are "very good" with network cards.

For permanency I've added the command to [FONT=Fixedsys]/etc/rc.local[/FONT] above [FONT=Fixedsys]exit 0[/FONT]

```
rmmod -f dell-laptop
```

Would [FONT=Fixedsys]/etc/modprobe.d/blacklist[/FONT] be better for any particular reason?

And I've added [FONT=Fixedsys]b43[/FONT] to [FONT=Fixedsys]/etc/modules[/FONT]

Feel free to let me know if I've screwed anything up. (Things seem to be working after a restart.)

Out of curiosity, why did the removal of the dell-laptop module suffice to make [FONT=Fixedsys]phys0[/FONT] the recipient of the toggling? Also, from where did that module initially arrive? The STA driver? The Ubuntu installation?

Thanks much again!

---

### Post by chili555 on 2011-06-01
It sounds like you have done everything right. I think either rc.local or blacklist.conf is fine.

dell-laptop is a module that is supposed to convert key presses on Dells to information the kernel can use. However, as you can see, pressing the Fn+F2 keys does *not* enable the wireless once there is wireless to enable; that is, the driver and firmware is installed. As a matter of fact, the wireless is enabled when we *remove* the module dell-laptop! Crazy, isn't it?> The notice about "wireless is disabled by hardware switch" remains fixed despite the keyboard toggle.
Whenever a poster complains that no matter what the key presses, he can't enable wireless on his Dell, that's usually the first thing I try. It almost always works. 

There must be a bug tracker somewhere about this; maybe we can add your experience to the list.

I'm glad your wireless is working. Have fun.

---


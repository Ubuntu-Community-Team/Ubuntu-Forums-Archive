---
title: "Problem with wireless/wired connections."
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by salih1 on 2013-06-06
Hi friends,I just installed ubuntu 12.04 LTS 64 on my asus laptop and i m facing some problems with it. I cant get connected to a wired LAN or wirless network which is active and ok with my desktop. But i can access internet through a wireless usb modem . When i checked with this code-  "rfkill list all" following o/p showed up:
```
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

I tried a lot to unblock it, but failed...:(
What i m missing here??
Plzz help me with this....thnx

---

### Post by varunendra on 2013-06-06
> **salih1 said:**
> I tried a lot to unblock it
How? Usually -
```
sudo rfkill unblock all
```
Should work.


Oh, and Welcome to the forums ! :)

---

### Post by salih1 on 2013-06-06
Thnx for ur replay :).
I could never connect to internet from the beginning.
I tried the code u given, but nothing happend.Restarted system without the usb modem, still no change, not detecting any of the networks...
Is there any problem with the driver?? i dont know it installed by default or not.
thnx..

---

### Post by varunendra on 2013-06-06
> **salih1 said:**
> Thnx for ur replay :).
I could never connect to internet from the beginning.
I tried the code u given, but nothing happend.Restarted system without the usb modem, still no change, not detecting any of the networks...
Is there any problem with the driver?? i dont know it installed by default or not.
thnx..

Let us do some diagnostics then. Please follow the "Wireless Script" link in my signature, do what is suggested in the linked post and post back the diagnostics report as mentioned there.

---

### Post by salih1 on 2013-06-06
Here is the link of diagnostic report(wireless-info.text):
[http://pastebin.ubuntu.com/5738374/](http://pastebin.ubuntu.com/5738374/)

---

### Post by varunendra on 2013-06-06
The driver for your internal card is obviously not installed by default and you must have downloaded and compiled it manually. So, where did you download it from and how exactly did you compile it? Can you give us all the steps you followed to compile it? Or maybe the link to any guide that you followed.

Also, why have you blacklisted asus_wmi module? Was it causing any problems?

I suggest you disconnect (pull out) the usb adapter, reboot the laptop (leave the usb adapter unplugged) and run the wireless_script again. Then post back the new results along with answers to the above questions, plus the full output of -
```
lsmod
```

The driver appears to be correct for the card, I suspect the method used to compile it.

---

### Post by salih1 on 2013-06-06
Hi there, i did try different kind of coding which i found from askubuntu website. I m not expert in ubuntu, so i dont remember what exactly i did.:confused: One link which i used is [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working) and did exactly what it says.
On searching i did found about compat-wireless drivers, i also installed one of them which suites my kernal. Unfortunatly i got wifi connection without that usb modem. But my system started to pause unexpectadly on some occassions, so i reinstalled ubuntu 12.04 again. Now my system is clean and i m giving the details below which you asked:
output of "lsmod" is --> [http://paste.ubuntu.com/5738890/](http://paste.ubuntu.com/5738890/) 
and wireless-info.text without usb modem is --> [http://paste.ubuntu.com/5738897/](http://paste.ubuntu.com/5738897/)

hope this wil clarify everything..

thnk u..

---

### Post by varunendra on 2013-06-06
Good to have a fresh start. The askubuntu link you gave has a good set of instructions.
> **salih1 said:**
> One link which i used is [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working) and did exactly what it says.

Do it again. Follow the OFFICIAL SITE GUIDE and EXTRA GUIDE parts and skip the DROPBOX GUIDE part. To install linux-headers and build-essential (in the very first steps 1 and 2), use your USB modem connection.

Keep an eye on the compiling process, ignore warnings but post back if there are any errors. The 'make' command will return exactly 1 Error in the last regarding 'tftpboot', which can be safely ignored. Post back the error message(s) if there are more.

Finally, if everything goes fine, you should have a working wireless. Let us know how its performance is.

---

### Post by salih1 on 2013-06-07
Screwd up again...:confused:
I did all of the steps one by one correctly, finally i got wireless without usb modem. But a PROBLEM still exists there. When i used to connect internet through system wireless device, system goes hang unexpectadly. And a dos window appeares there with full of codes..dont know what they are. Then i restarted and connected to net through usb modem, system runs perfectly with no errors.
Why is that happening??
Is that driver not comaptible with chipset??

Some of the last line which showed up on the sreen were like this---

```
[157.183349] kernal panic-not syncing:Fatal exception in interrupt
           [157.957142] panic occured, switching back to text console..
```
I had waited long time but nothing happend..only to do is to press long the power button..:frown:

---

### Post by varunendra on 2013-06-07
> **salih1 said:**
> Screwd up again...:confused:

That driver has reportedly been problematic for many users. Unfortunately, so are others. So basically this has been a try and hope thing with the variations of different workarounds available.

Based on the comments on the bug report page ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)), especially comments #8 and #35, #46 and #61, the two following suggestions seem most promising -

[INDENT]**1)** Manually install kernel 3.8 (download from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")) and updated firmware (as suggested at the bottom of this post). This is rather risky and directly jumping to a much higer kernel version than currently in use may break the OS.

**2)** Do an update, then install "linux-generic-lts-raring" package. It will install the latest supported kernel (currently 3.8.0-24) and updated firmware, and will natively support your card. The performance however, is still not verified by many users (at least not on the bug report page).[/INDENT]

Since installing through repositories is a safer path, I'd recommend to go with option 2 first and let us know if it works. To try that, you'll have to do the following -

1. Uninstall the current driver. From within the directory where you did 'make' and 'sudo make install', do-
```
sudo make uninstall
```

2. Do an update -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

3. Install the backported raring kernel and firmware -
```
sudo apt-get install linux-generic-lts-raring
```
Reboot after finishing and see if the wireless comes to life. Moreover, if it is stable and satisfactory.

If it does not work as expected, you may try manually installing the updated firmware (although I believe it is the same that would be installed in above steps, but not sure, so..) -
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
sudo cp linux-firmware/rt3290.bin /lib/firmware
```
reboot and hope for the best !

---

### Post by salih1 on 2013-06-08
Well, i got a working wired connection and it works perfectly.:)Thank u for helping out. But wireless still not working..It is soft blocked.
I used the 2nd option and installed backported raring kernel and firmware. What to do next??
Thank u.

---

### Post by praseodym on 2013-06-08
Try
[B]
sudo rfkill unblock all[/B]

---

### Post by varunendra on 2013-06-08
Well, show us the wireless-info report again. :)

**EDIT:**
Didn't see praseodym's post while making mine, so.. in addition to what he suggested :)

---

### Post by salih1 on 2013-06-08
Hi, i tried it, and now it shows unblocked. But i cant see an option to enable wireless network.
thank u

---

### Post by salih1 on 2013-06-08
:)Here is the link for wireless-info--> [http://paste.ubuntu.com/5744522/](http://paste.ubuntu.com/5744522/)

---

### Post by praseodym on 2013-06-08
Install the appropriate driver according to this:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

### Post by varunendra on 2013-06-08
> **salih1 said:**
> :)Here is the link for wireless-info--> [http://paste.ubuntu.com/5744522/](http://paste.ubuntu.com/5744522/)

In your previous attempts to install the compiled driver, you blacklisted the rt2800pci and rt2x00pci drivers, which, according to the comment on the bug report page I linked to, should be now able to handle your card.

Accordingly, before you try anything else, I'd suggest you 'Un-Blacklist' those drivers and retry. Open the blacklist file with root access -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then delete the last two lines that say "blacklist rt2800pci" and "blacklist rt2x00pci". Proofread, save and close the file. Then do-
```
sudo modprobe -v rt2800pci
```
..and see if the wireless becomes active.

If not, please post outputs of :
```
modinfo rt2800pci
locate rt3290.bin
dmesg | grep -iE 'firm|rt2'
lsmod
```

---

### Post by salih1 on 2013-06-09
Bingo.. i got an option for enable wireless and connected it ONCE--Black listed those items. 
But it not getting connected AUTOMATICALLY when i restarted. I tried manually by selecting...,restarted system and modem, but still not..All available connections are dispalyed there..
Any idea..????????????
thank u varun and praseodym..:)

---

### Post by varunendra on 2013-06-09
Sounds crazy to myself but,.... uh.... the current wireless-info again please ! :P

---

### Post by salih1 on 2013-06-09
:D here it is.. [http://paste.ubuntu.com/5747563/](http://paste.ubuntu.com/5747563/)

---

### Post by varunendra on 2013-06-09
> **salih1 said:**
> :D here it is.. [http://paste.ubuntu.com/5747563/](http://paste.ubuntu.com/5747563/)
Hmm.. looks much better now. But I couldn't decipher the encryption type from the outputs. So just make sure that the encryption type in the router/access-point is set to pure WPA2-PSK (AES) type, and especially NOT WPA/WPA2 mixed mode.

Then, do the following -
```
sudo iwconfig wlan0 power off
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
Then try to connect and see if you can.

Sometimes it also helps if you 'Save' the correct security type and security-key in the Network Manager itself (under "Wireless Security" tab in your wireless connection settings box in Network Manager).

---

### Post by salih1 on 2013-06-09
There were no security enabled for this network...It is open. I dont know why the output shows like that. I eneterd that code and it tried to reconnect but failed. Everything is fine with usb modem. What to do????
I also tried with security enabled and assignd a paswd(not in mixd mode) but still no change..

---

### Post by varunendra on 2013-06-09
> **salih1 said:**
> There were no security enabled for this network...It is open. I dont know why the output shows like that. I eneterd that code and it tried to reconnect but failed. Everything is fine with usb modem. What to do????
I also tried with security enabled and assignd a paswd(not in mixd mode) but still no change..

A couple of suggestions, 1st one first, both together if required -

[INDENT]**1)** Try changing the channel to 1, 6 or 11 - the one that is least used in your neighborhood (currently you are using channel 4). Channel 6 is something I personally *believe* should be good based on some theoretical knowledge, but have absolutely no practical experience or evidence.

Those who have both a good level of theoretical knowledge as well as practical experience recommend channels 1 and 11 the most. So try them first.

**2)** Try Wicd and remove Network Manager altogether exactly as per steps given here : [https://help.ubuntu.com/community/WICD#For_Gnome_.2BAC8_Unity](https://help.ubuntu.com/community/WICD#For_Gnome_.2BAC8_Unity)

Please note that you won't get the tray icon on the top right corner like network manager. Wicd does not have that. It needs to be opened from Applications menu like other normal applications.[/INDENT]

Use the commands in my previous post with wicd as well if required.

Everything else looks good.

---

### Post by salih1 on 2013-06-10
Changed channels several times..nothing happened.
Installed Wicd, did some changes in settings...still nothing.
It shows a problem in obtaining IP address.( connection is open)
wired is okey..

Checked wicd with usb modem..seems fine.
What is happening with ma lap:confused::confused:

---

### Post by varunendra on 2013-06-11
> **salih1 said:**
> It shows a problem in obtaining IP address.( connection is open)
wired is okey..
Hmm.. okay, please do -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee -a /etc/modprobe.d/rt2800pci.conf
```
.. do a reboot after this, try to connect, let it fail, then post back the outputs of -

```
lsmod
iwconfig
ifconfig
cat /etc/resolv.conf
sudo iwlist wlan0 scan
dmesg | grep -iE 'rt2|wlan'
cat /var/log/syslog | grep -iE 'rt2|wlan|dhcp|dhclient|network'
modinfo rt2800pci
```

And keep the security to either pure WPA2-PSK (AES) or disabled in the router.

**[COLOR="#FF0000"]EDIT:[/COLOR]**
Edited the dmesg command and added cat /etc/resolv.conf
Please post as per updated commands.

---

### Post by salih1 on 2013-06-11
Router security is in disabled mode.
Outputs are:
lsmode--->[http://paste.ubuntu.com/5755640/](http://paste.ubuntu.com/5755640/)

iwconfig-->[http://paste.ubuntu.com/5755657/](http://paste.ubuntu.com/5755657/)

cat /etc/resolv.conf-->[http://paste.ubuntu.com/5755663/](http://paste.ubuntu.com/5755663/)

sudo iwlist wlan0 scan-->[http://paste.ubuntu.com/5755670/](http://paste.ubuntu.com/5755670/)

dmesg | grep -iE 'rt2|wlan'-->[http://paste.ubuntu.com/5755679/](http://paste.ubuntu.com/5755679/)

cat /var/log/syslog | grep -iE 'rt2|wlan|dhcp|dhclient|network'-->[http://paste.ubuntu.com/5755697/](http://paste.ubuntu.com/5755697/)

modinfo rt2800pci-->[http://paste.ubuntu.com/5755703/](http://paste.ubuntu.com/5755703/)
------
Thank u...:)

---

### Post by praseodym on 2013-06-11
"(reason 3)" in the dmesg-output comes from the network-manager. Remove your current wireless profile and create a new one.

---


---
title: "HOW TO - Linksys WMP54GS working with WPA2 AES Ubuntu 9.04 Jaunty without ndiswrapper"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by alleycatuk on 2009-08-06
I installed Ubuntu 12 days ago to create a LAMP test machine. The software was in place and working within a few hours - I then spent 12 days pulling my hair out trying to get my wireless network card working. Then someone on another forum pointed me in the right direction so I'm sharing the info in the hope it will save someone else the frustration I've had! I'll try do it from a newbie's point of view seeing as that's how I started - I now feel I know much more but I probably don't!

My spec is as follows:
Windows XP machine set up to dual boot Ubuntu on a separate HD
No wired card
Wireless card - Linksys WMP54GS working perfectly under Windows
Security - WPA2 AES on router with MAC Filtering enabled (also working under XP)

Some of the forums suggest using ndiswrapper which I did get to work but not reliably - if my method fails, try WIEMAN01's HOW TO thread on setting up ndiswrapper - it's brilliant but just didn't work for me. I'd advise you to read all steps before going for it, so you know what to expect. When I first installed Ubuntu, it tried to use b43-pci-bridge driver. Following some forums, I blacklisted this and tried ndiswrapper. Guess what!? I'm posting this using b43... you just need the following to get it to work with WPA2.

1. First of all, open a terminal window (Applications -> Accessories -> Terminal) and type
```
lshw -C network
```You should see a list of wired and wireless devices. Have a look at your wireless one, particularly the Product - it may not say Linksys but don't worry - it's reading the chip that's on the Linksys card. Mine says [COLOR=Blue]BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/COLOR]

2. Now check this page [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to see if your device (the BCMxxxx bit) is listed. If it's not, you don't need to carry on as this probably won't work for you. If it is listed... read on!

3. You're best using an internet connection for this - if you have a working wired one, go to step 4. If not, you need to install from the Ubuntu cd so go to System -> Administration -> Synaptic Package Manager and under Settings -> Repositories, untick any options that link to the internet and make sure that "installable from CD-ROM/DVD" is ticked. Accept all the screens until you're back in the package manager.

4. In System -> Administration -> Synaptic Package Manager, in quick search, type b43-fwcutter. You should see just one package. Right-click on it and select Mark for Installation. On the main screen, Apply should now be lit up - click on it and it should install.

5. At the end of the B43 fwcutter installation, it will ask if you want to "Fetch and install firmware?". Choose Yes. This fetches the firmware from your wireless card into a place where the Linux b43 driver can use it. Don't worry if you're dual-booting with XP as it won't affect the firmware used by XP for your Linksys.

6. Repeat step 4 but using wpa_supplicant instead of b43-fwcutter so that you install wpa_supplicant.

7. To use WPA2, you need to know your pre-shared key/passphrase from your router. Find it/look it up. In a terminal window (Applications -> Accessories -> Terminal) type 
```
wpa_passphrase <network ssid> <passphrase>
 e.g. wpa_passphrase mywirelesslan averylongpassphrase
```This will give you a long hexadecimal number. Keep it handy in the window as you'll need to copy it in a moment.

8.In a terminal window (Applications -> Accessories -> Terminal) type 
```
sudo gedit /etc/network/interfaces
``` and type your password if it asks.
Alter the file to look something like this:
## ---------------------------------------------------------
[COLOR=Blue]auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf
wpa-ap-scan 1
wpa-driver wext
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <paste the hex number from wpa_passphrase from step 7 without quotes around it>[/COLOR]
## ----------------------------------------------------------
where wlan0 is your wireless interface. RSN and CCMP mean to use AES. If you use TKIP, put TKIP instead of CCMP. 

9. In a terminal window (Applications -> Accessories -> Terminal) type 
```
sudo gedit /etc/wpa_supplicant.conf
```alter the file to look like this:
[COLOR=Blue]ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
ssid=<your wireless SSID per the router>
scan_ssid=1
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=[/COLOR][COLOR=Blue]<paste the hex number from wpa_passphrase from step 7 without quotes around it>
}[/COLOR]

10. If it isn't already, enable SSID broadcast on your router. If you have MAC Filtering on your router and you know it's set up correctly, (mine worked under XP so I knew it was OK), then there's no need to turn it off. If you're not sure, turn it off until you get connected.

11. All being well, that should be it!! Reboot the PC (take Ubuntu disc out of cd rom if it's in!) and your wireless should be working ok. If not, I installed wpa_gui in the same way as step 4 (I'm not sure if this is on the Ubuntu cd - if not, you'll have to copy it from a PC with a connection - get the package onto a cd and then do...
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install wpa_gui

```).
WPA_GUI lets you see what the network is trying to do and you can even amend various bits such as your passphrase (the string one, not the hexadecimal).

12. Good luck! I hope this is helpful to someone. Now I'm off to use my network and really get into Ubuntu!

---

### Post by yellowlabrat on 2009-08-16
First off, let me thank you for doing such a great post that truly helps a complete newbie to Ubuntu and Linux in general.
Thank you for that!

I also have Ubuntu 9.04 and a Linksys Wireless-G network card, model #WMP54GS.
I tried following all of the steps you gave, and got all the way to the reboot in Step #11.

It didn't see my wireless card, so I got wpa_gui, and have that installed as well.
When I load wpa_gui, it has most everything greyed out and unavailable. The biggest problem appears to be that the Adapter field is blank and the drop down won't work. So, this make me believe that it does not see an adapter at all.

Any ideas on what to check or where to go from here?
Is there some info I need to spit out that would make it a more helpful assessment?

---

### Post by Xanxer82 on 2010-10-17
I got all the way to the end and rebooted. Got a measge that new drivers are available for my hardware. Clicked Activate for Broadcom B43 wireless driver. Then it saysSystemError: installArchives() failed.

What's going on?

---


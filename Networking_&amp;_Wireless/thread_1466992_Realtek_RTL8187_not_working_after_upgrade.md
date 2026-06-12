---
title: "Realtek RTL8187 not working after upgrade"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Dearhell on 2010-04-30
So after upgrade from 9.10 to 10.04 the wireless network stopped working.

When I click right on the network manager, the "activate wifi network" option it's grey and unselected and cannot be activated.

Though the device seems properly recognized, appears the right name and model when I left click on the network manager. 

Also lsusb shows the right information. 

If I type: iwconfig, the radio appears off. 

I tried ifconfig eth1 up command without success. 

I also tried this: 

> gksudo gedit /etc/NetworkManager/nm-system-settings.conf

In order to set "managed" to true. 

Before the upgrade to 10.04 this device worked like a charm.

---

### Post by Dearhell on 2010-05-01
Still not solution found.

---

### Post by Dearhell on 2010-05-01
Culprit's portrait:

[IMG]http://www.appinformatica.com/imf/redes-inalambrica-connection-usb-wireless-54-con-antena-desmontable.jpg[/IMG]

---

### Post by bngguy on 2010-05-01
I had a similar problem, here's how i fixed it:

I'm assuming you still have the 2.6.31-21-generic kernel on your system, if you have it reboot the system and select it on the grub menu.You should have wireless access now.


1)Select System-->Administration-->Synaptic Package Manager
2)Search for linux-image-2.6.32-21-generic
3)right click on it and select "Mark for Complete Removal"
4)reboot system 
5)Repeat steps 1 thru 3
6)This time select "Mark for Installation"

Reboot your system again, this time select 2.6.32-21-generic kernel on the grub menu.

Let me know if this worked for you.

---

### Post by Dearhell on 2010-05-02
> **bngguy said:**
> I had a similar problem, here's how i fixed it:

I'm assuming you still have the 2.6.31-21-generic kernel on your system, if you have it reboot the system and select it on the grub menu.You should have wireless access now.


1)Select System-->Administration-->Synaptic Package Manager
2)Search for linux-image-2.6.32-21-generic
3)right click on it and select "Mark for Complete Removal"
4)reboot system 
5)Repeat steps 1 thru 3
6)This time select "Mark for Installation"

Reboot your system again, this time select 2.6.32-21-generic kernel on the grub menu.

Let me know if this worked for you.

Starting with 2.6.31-21-generic kernel still not wireless access.

nm-tool output:

> - Device: wlan6 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:05:42:90

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


iwconfig output:

> wlan6     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by Crio on 2010-05-10
Does your dongle have any switches? 
I have rtl8187b card inside my notebook and after the upgrade  switching wifi on/off by keyboard Fn-key began to work. It was quite a surprise, especially since it started in the "off" mode with exactly the same symptoms in NetworkManager as you describe.
Search for "killswitch" in your /var/log/syslog for any (not so :)) helpfull messages.

---

### Post by chili555 on 2010-05-10
> wlan6 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
[COLOR="Red"]Tx-Power=0 dBm[/COLOR]
Retry long limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 I was messing with an RTL8187 just last night! I won a bet from a Microsoft fanboi that I could connect his wireless card on my machine in two minutes or less without his useless driver disk. I noticed the txpower at zero and did:> sudo iwconfig wlan6 txpower 20I had to play around a bit to find the highest number that it would accept before erroring out. Once that was done, I tried:```
sudo ifconfig wlan6 up
sudo iwlist wlan6 scan
```It returned scan results and connected.

---

### Post by Dearhell on 2010-05-10
> **chili555 said:**
> I was messing with an RTL8187 just last night! I won a bet from a Microsoft fanboi that I could connect his wireless card on my machine in two minutes or less without his useless driver disk. I noticed the txpower at zero and did:I had to play around a bit to find the highest number that it would accept before erroring out. Once that was done, I tried:```
sudo ifconfig wlan6 up
sudo iwlist wlan6 scan
```It returned scan results and connected.

So after I executed this: 

> sudo iwconfig wlan6 txpower 20

It returned scan results but the network manager on the top right of screen has the "activate wifi networks" still grey ( therefore it cannot be selected ), although the device seem properly recognized.

---

### Post by Crio on 2010-05-10
May be you are affected by [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143)  or something similar?

---

### Post by Dearhell on 2010-05-10
> **Crio said:**
> May be you are affected by [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143)  or something similar?

rfkill -list output:
> 2: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

I've tried rmmod dell_laptop but rfkill -list is the same: 

> 1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

How do I unblock this?

I've also tried rfkill unblock 1 without success.

My laptop doesn't have a physical switch to control the wireless device.

---

### Post by Crio on 2010-05-11
Sorry, I don't have any idea. May be "rfkill unblock phy1" ?
By the way, in my case rfkill does not work at all - rfkill list produce no output whatsoever.

---

### Post by CoolDreamZ on 2010-05-20
Try Fn+F2 also see [here]("http://ubuntuforums.org/showthread.php?t=1480381")

---

### Post by Tempster on 2010-05-31
all of these threads about the Trendnet tew-424ub (realtek chipset) and ndiswrapper are very confusing.

I booted up a Compaq Presario 2140 laptop off of a USB Drive with the latest versions of Ubuntu and Kubuntu Netbook installs and the trendnet usb wireless adapter shows up and works for both Ubuntu Netbook (from usb drive) and Kubuntu Netbook (from USB Drive) without having to add any drivers or to do anything with ndiswrapper.

However, I have a complete Ubuntu Studio install on a hard drive on a toshiba Satellite laptop and the Trendnet Wireless Adapter does not light up and Ubuntu does not list the adapter when I type lsusb in terminal.

I uninstalled ndisgtk and ndiswrapper that I initially installed on the toshiba to try to get the adapter to work (because these weren't necessary for the Presario laptop and Ubuntu Netbook from usb drive).  I could be wrong but, I think that at one point the Trendnet TEW-424UB Adapter did light up on the Toshiba laptop (and it showed up when I typed lsusb) although it did not display any wireless networks and did not connect to any wireless networks.

I guess my initial question is "Why is the Tew-424UB Adapater not lighting up and not showing up when I type lsusb?".

---

### Post by Tempster on 2010-06-01
Any chance of getting some help with this Toshiba problem?

Is there something special about Toshiba Satellites that the trendnet TEW-424UB will not work under Ubuntu on the Toshiba without ndiswrapper?  As said, I didn't have to do anything special to get the TEW-424UB to work under latest Ubuntu on a Compaq Presario 2140US laptop.

---

### Post by Crio on 2010-06-02
Certainly, your adapter is not working because it is not registered with USB (does not show in usb list). Why is that is another question.
I suggest to try to plug in some other USB device - thumbdrive or something. 
If it works, I'd assume that there is problem with contact in the USB port (may be either plug or socket is damaged).
If it does not, then probably something wrong with usb support on your Toshiba. Hotplug is switched off, or broken, or may be USB support is turned off in BIOS.

---

### Post by Tempster on 2010-06-03
Thanks, I will check the bios of the Toshiba.  AS I said, I thought the Wireless Adapater was lighting up at one time and I have definitely used a usb keyboard and mouse with the machine. 

Maybe someone should alert people that ndiswrapper and installing Windows drivers is not necessary with the latest Ubuntu - at least not with the Trendnet TEW-424UB 3.XR wireless adapter.

---

### Post by Tempster on 2010-06-05
the usb drive works with other devices but still not with the Trendnet USB Wireless adapter.  I will try to update the bios on the laptop and see if that helps

---


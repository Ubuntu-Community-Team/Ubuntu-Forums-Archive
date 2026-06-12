---
title: "Linksys WUSB54G install"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by e-lizza on 2006-06-04
Hi everyone,

I have installed Ubuntu 606 release (new clean install) and I have connected my Linksys WUSB54G.
Now, I want to connect to the router with WPA/TKIP+AES enabled.

I have read a lot of pages, tried to install ndiswrapper, rt2x00, dapper's tools, etc., but I am still in the same place. Some posts describe various approach how to install drivers, front-ends, etc. How-to on ubuntu for wusb54g on DD is still blank.

I will gratefully appreciate your help if you can explain (let me know where to read) how to make it working. I need 1 working procedure. Please, don't explain opportunities and various methods on this subject.

If it will work and it is not published, I promise to write it down and publish for others who have the same problem.

Thank you very much in advance,
   Liz.

---

### Post by lynxus on 2006-06-04
Hi Liz,

The following page may help you, It helped me with my linksys pcmcia card, so it may work with your usb stick as the princble is roughtly the same.
However it wont work if ubuntu doesnt reconise its exsistance at all.
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Type in a terminal : sudo lshw
as see if the devics is listed..

Sorry if this doesnt help though :(

---

### Post by e-lizza on 2006-06-04
Hi, lynxus,
Thank you very much for responding.

[QUOTE=lynxus]Hi Liz,
The following page may help you, It helped me with my linksys pcmcia card, so it may work with your usb stick as the princble is roughtly the same.
However it wont work if ubuntu doesnt reconise its exsistance at all.
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)[/QUOTE]

Did you really install bcm43xx-fwcutter for WUSB54G V4?

---

### Post by e-lizza on 2006-06-04
Well. I've done absolutely clean installation of ubuntu 606DD release.
I loaded it and logged in.

My eth0 is disconnected from LAN; no any connection neither to lan nor wan nor any others. I did not install or update any sw.

I pluged-in my WUSB54G in usb slot. Below is an output of a few commands.

**u@c:~$ lshw**
  ...
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN
  ...

**u@c:~$ iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.
rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr[:]off   Fragment thr[:]off:
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**u@c:~$ ifconfig** // shows only eth0 and lo
eth0      Link encap:Ethernet  HWaddr 00:01:02:03:04:05
...
lo        Link encap:Local Loopback
...


[COLOR="Navy"]Any ideas what to do next?[/COLOR]

---

### Post by e-lizza on 2006-06-04
One more output:

**u@c:~$ sudo lsusb**
Bus 001 Device 002: ID 13b1:000d Linksys
Bus 001 Device 001: ID 0000:0000

It seems that ubuntu could recognize wusb54gv4 and card itself works ok.

[COLOR="Navy"]Should I install any other drivers, e.g. "ndiswrapper"?[/COLOR]

---

### Post by e-lizza on 2006-06-05
After some time I've finally (hopefully) managed my wusb54gv4 card. I followed instructions [here]("http://www.ubuntuforums.org/showthread.php?t=125150"). I skipped all optional steps for driver installation, because it seems card is working properly. I just installed libnl, wpasupplicant, networkmanager.

Now I can see 5-7 networks around me with different security modes in nm-applet. So, my w-card can detect all of them.

1) in network property (i.e. connect to other networks) I can still see WEP; no WPA, no WPA2. How?

2) I tried to connect to the router with wep and wpa (by editing/playing with /etc/wpa_supplicant.conf), but still I can't.
THIS IS THE MAIN QUESTION! HOW TO CONNECT?

3) every time at the beginning nm connects to eth0. How to tell it "not to connect to eth0"?

I am editing this post in oder to inform that after 4-5 hours card is still working and I found that it could detect other networks.

**I would appreciate your ideas in solving of these problems.**

Liz.

---

### Post by wieman01 on 2006-06-24
Liz, 

I will explain to you first what my setup & requirements are and then embark on the approach I have chosen as a security nerd. It appears that very few people take wireless security seriously.

**_Setup:_**
1. WUSB54G V4 wireless adapter
2. WRT54G V22 router (latest firmware)
3. P4 Desktop

**_Requirements:_**
1. WPA2 / RSN
2. AES / CCMP
3. Hidden ESSID (no broadcasting)
4. Static IP (because I use port forwarding & firewall, etc.)
5. Pre-shared key (I refrained from using EAP)
6. NDiswrapper (do yourself a favor & don't use rt2x00)

**_Prerequisites:_**
1. NDiswrapper installed and wireless adapted enabled
2. WPA-Supplicant (0.4.8 or later) installed
3. No NetworkManager installed (!)

So I assume that your network adapter is up & running and configured using "ndiswrapper". Personally I am much in favor of "ndiswrapper" because that's the easiest way to go. Others may prefer "rt2x00" but I could not get it to work (I tried though). Note that WPA-Supplicant v0.4.8 is slightly different from previous version so don't get hung up on my approach.

If you want to know more about WPA / RSN & 802.11i security specification, I recomment this page: [http://en.wikipedia.org/wiki/IEEE_802.11i]("http://en.wikipedia.org/wiki/IEEE_802.11i")

**_Now let's get started:_**

1. Verify that your network device ("wlan0"?) is working:
> ifconfig
Your network device should appear here.

2. Open "/etc/network/interfaces":
> sudo gedit /etc/network/interfaces
The content should look similar to this:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

3. Now replace the last 2 line with the following using your own network settings (the sequence in which the lines appear is absolutely crucial):

> 
auto wlan0
iface wlan0 inet static
[INDENT]wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2	
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>
address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230	
dns-nameservers 192.168.168.230[/INDENT]

I will explain very carefully - one by one - what you see here and how you need to adjust the lines according your setup.

1. auto wlan0 & iface wlan0 inet static:
>> Self-explanatory... I am using static IPs rather than DHCP.

2. wpa-driver wext:
>> That your ndiswrapper driver (wext is a generic driver that is also applicable when using ndisrwrapper). Leave it as it is.

3. wpa-conf managed:
>> Leave it as it is.

4. wpa-ssid:
>> Your network's ESSID (no quotes "" please).

5. wpa-ap-scan 2:
>> Scanning logic of your wireless adapter. Setting "2" enables your PC to associate with hidden networks (no broadcasting of ESSID).

6. wpa-proto RSN:
>> Component of WPA2 (see link above!)... authentication & encryption. You could also specify "WPA2" here which is a recognized alias.

7. wpa-pairwise CCMP & wpa-group CCMP"
>> Component of WPA2 (see link above!)... your actual AES encryption.

8. wpa-key-mgmt WPA-PSK:
>> Your pre-shared key as set up in the router... in contrast to EAP (Extensible Authentication Protocol) which is an overkill for a small home network. See further below for key generation. No quotes "" please.

9. address, netmask, network, broadcast, gateway, dns-nameservers:
>> Also self-explanatory... be aware that "broadcast" needs to end with ".255" for negotiation with the router. These lines need to be according to your own network settings.

As for WPA-PSK key generation, type the following command in a terminal:

> wpa_passphrase <your_essid> <your_ascii_key>

Resulting in an output like...

> network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab15bbc6c52e7522f709a
}

Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. Then save the file and restart your network:

> sudo /etc/init.d/networking restart

You should be connecting to your router now... however, I figured that a restart is sometimes necessary so that's what I usually do (I know this sounds a bit clumsy). 

I should add a few words on how to debug your network settings and how to make use of "verbose" and "log-files" but it is getting late here. Hope this helps anyway. Let me know if you have more questions. I have been through a lot of pain in the last couple of weeks, so I know how frustrating this must have been for to you.

---


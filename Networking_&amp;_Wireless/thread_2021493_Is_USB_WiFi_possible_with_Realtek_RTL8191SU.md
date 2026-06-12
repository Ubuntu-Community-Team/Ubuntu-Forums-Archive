---
title: "Is USB WiFi possible with Realtek RTL8191SU ??"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by yorkwils on 2012-07-09
So near but I simply don't have any knowledge to help me.

Acer Aspire laptop with built-in WiFi that I can't turn off in the BIOS. I need to use Realtek USB WiFi RLT8191SU to increase signal strength. Everything is fine and my router and other services are detected by both the internal WiFi and the USB. I just can't connect to anything with the USB except very occasionally (1 time in 200)! 

Here is NM-tool when NM says USB is connected. It reports that it is connected but then disconnects about 20 seconds afterwards and then tries again, reports it is connected, reports it is disconnected and so on... At no time is any service useable:

inux@inux-Aspire-5630:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Belkin_G_Plus_MIMO_ED217C 1] ---------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        00:0D:81:A0:81:0A

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Belkin_G_Plus_MIMO_ED217C: Infra, 00:17:3F:ED:21:7C, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:16:D4:5F:0D:81

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:18:DE:24:C4:4D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Belkin_G_Plus_MIMO_ED217C: Infra, 00:17:3F:ED:21:7C, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA



and here is lsusb:


inux@inux-Aspire-5630:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
inux@inux-Aspire-5630:~$ 



Perhaps it is something really simple but I will go round in circles for ever!!

---

### Post by chili555 on 2012-07-09
You might have better luck if you blacklist the driver for the internal device. If you wish to do so:```
sudo su
echo "blacklist iwl3945 >> /etc/modprobe.d/blacklist.conf
ifconfig wlan0 down
modprobe -r iwl3945
exit
```Any improvement? It may take a reboot.

---

### Post by yorkwils on 2012-07-10
I did my best to run the script but it well outside my comfort zone!

I copied it into Nano, named the file "black" and saved it in the Home folder.

Then I ran it :   sudo bash black

The cursor changed from:  inux@inux-Aspire-5630:~$   into   root@inux-Aspire-5630:/home/inux#

When  I went to shut down Terminal I was told that a script was still running  and it would be stopped. There was no change when I rebooted and the  built-in WiFi was still available so it doesn't appear to have turned it  off?

Should there be a second quote-mark in the echo line?

---

### Post by yorkwils on 2012-07-10
I put in the second quote-mark in the   echo "blacklist...."  line and it seemed to turn off the built-in WiFi when I then typed   exit   and pressed enter. The cursor didn't change and it still told me the program was running when I closed terminal down.

When I re-started, the built-in WiFi is no longer available so it seems to have worked. However, there is no change with the Realtek RTL8191SU and it connects and disconnects exactly as before :(

---

### Post by chili555 on 2012-07-10
> When I went to shut down Terminal I was told that a script was still running and it would be stopped. What was running is the switch from ordinary user to root.> The cursor changed from: [COLOR="Red"]inux[/COLOR]@inux-Aspire-5630:~[COLOR="Red"]$[/COLOR] into [COLOR="Red"]root[/COLOR]@inux-Aspire-5630:/home/inux[COLOR="Red"]#[/COLOR]It's safe to close the terminal.> Should there be a second quote-mark in the echo line? Yes, indeed and I'm sorry for my mis-step. Glad you caught and corrected it.

Your bash script 'black' is certainly effective, as you've seen, but is the long way around the steps. All you had to do is copy and paste each command one at a time and press Enter after each. The final command, *exit*, switches out of root back to ordinary user.

Now that the internal is out of the mix, let's troubleshoot the USB. Please run and post:```
dmesg | grep -i rtl
iwconfig
```Thanks.

---

### Post by yorkwils on 2012-07-10
Thank you for your patience with me, I just wish I had a little more  knowledge to make things easier! I didn't even realise the lines could  be typed like that. I was just lucky to guess about the second quote. As  it turned out, I ran the script twice and added two lines to  blacklist.conf  I realise that probably didn't matter but I did a sudo  gedit to remove the second occurrence.

Anyway, re-started without internal WiFi and here is the result of your last two lines:

inux@inux-Aspire-5630:~$ dmesg | grep -i rtl
[   15.773626] r8712u: register rtl8712_netdev_ops to netdev_ops
[   16.362319] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
inux@inux-Aspire-5630:~$ iwconfig
lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

inux@inux-Aspire-5630:~$ 

I don't like the sound of signal level:0 !!! I'm 1m away from router.

---

### Post by chili555 on 2012-07-10
> I just wish I had a little more knowledge to make things easier! I didn't even realise the lines could be typed like that.No worries at all. All of us, even old Dr. Chili and even Linus Torvalds didn't know much about Linux once upon a time. 

This looks solid:> inux@inux-Aspire-5630:~$ dmesg | grep -i rtl
[ 15.773626] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 16.362319] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
inux@inux-Aspire-5630:~$ iwconfig
lo no wireless extensions.

wlan1 unassociated Nickname:"rtl_wifi"
Mode:Managed Access Point: [COLOR="Red"]Not-Associated Sensitivity:0/0[/COLOR]
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0You see signal strength 0 because you are not connected. No problem so far.

Please detach the ethernet cable and let's see what Network Mangler is doing as you try to connect with wireless. After you try to connect, please run and post:```
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```That's all one long command; press Enter and twenty hopefully informative lines of text will spew forth. Thanks.

---

### Post by yorkwils on 2012-07-10
Would you believe it, it connected ok that time and this reply is using the Realtek USB!

Occasionally it has connected before but I can't spot any rule. I print the output with the Realtek connected and then I'll disconnect it print the output for when it has problems (assuming that happens of course!)

inux@inux-Aspire-5630:~$ sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
[sudo] password for inux: 
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info>   address 192.168.0.6
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info>   prefix 24 (255.255.255.0)
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info>   gateway 192.168.0.1
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info>   nameserver '192.168.0.1'
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 10 17:14:33 inux-Aspire-5630 NetworkManager[777]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
Jul 10 17:14:33 inux-Aspire-5630 avahi-daemon[782]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.6.
Jul 10 17:14:33 inux-Aspire-5630 avahi-daemon[782]: New relevant interface wlan1.IPv4 for mDNS.
Jul 10 17:14:33 inux-Aspire-5630 avahi-daemon[782]: Registering new address record for 192.168.0.6 on wlan1.IPv4.
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> DNS: starting dnsmasq...
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> Policy set 'Belkin_G_Plus_MIMO_ED217C 1' (wlan1) as default for IPv4 routing and DNS.
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> Activation (wlan1) successful, device activated.
Jul 10 17:14:34 inux-Aspire-5630 NetworkManager[777]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Jul 10 17:14:34 inux-Aspire-5630 avahi-daemon[782]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::20d:81ff:fea0:810a.
Jul 10 17:14:34 inux-Aspire-5630 avahi-daemon[782]: New relevant interface wlan1.IPv6 for mDNS.
Jul 10 17:14:34 inux-Aspire-5630 avahi-daemon[782]: Registering new address record for fe80::20d:81ff:fea0:810a on wlan1.*.
Jul 10 17:14:43 inux-Aspire-5630 kernel: [ 3879.008054] wlan1: no IPv6 routers present
inux@inux-Aspire-5630:~$

---

### Post by yorkwils on 2012-07-10
Guess what? I can't make it go wrong now!! I'll be away from the computer for a while so I'll try again after turning off and see what happens then. It was still misbehaving after removing the internal driver so there appears to be no direct reason for it to suddenly work now. I have connected four times in a row and it has never done that before. More later but many thanks for now...

---

### Post by chili555 on 2012-07-10
> New relevant interface [COLOR="Red"]wlan1.IPv6[/COLOR] for mDNS.
Jul 10 17:14:34 inux-Aspire-5630 avahi-daemon[782]: Registering new address record for [COLOR="Red"]fe80::20d:81ff:fea0:810a[/COLOR] on wlan1.*.
Jul 10 17:14:43 inux-Aspire-5630 kernel: [ 3879.008054] wlan1: [COLOR="Red"]**no IPv6 routers present**[/COLOR]Huh?? I wonder if its problem is struggling with IPv6. Is yours an IPv6 capable router? If it's an ordinary consumer grade router, then probably not.

Is there any change if you Edit Connections in Network Manager and set IPv6 to Ignore? Please see attached.

---

### Post by yorkwils on 2012-07-10
I'm at a different location now with a much weaker WiFi signal on a different router and still the Realtek has connected fine. Is it possible that it took a couple of re-starts after blacklisting the internal WiFi for the Realtek to establish itself?

Whatever caused it to start working properly in the end it was your guidance in turning off the internal WiFi that made it all possible and I am much in your debt. Thank you very much indeed.

I realise there is a chance it may misbehave again but for now the problem is solved. If I have further problems I'll post the printout of the last two lines of code you sent again but, for now, all looks good. IP6 is set to 'automatic' at the moment, I'll change it to ignore t the first sign of trouble.

Once again, many thanks...

---

### Post by chili555 on 2012-07-10
Happy to help. Post back if you need us. Have fun!

---


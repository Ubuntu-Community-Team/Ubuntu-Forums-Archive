---
title: "some troubles with a intel pro wireless 2200 BG"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by stardust.one on 2006-01-03
Hi every body

After installing a driver for my wireless card, the connexion to internet was good
he's a scan 

hyperion@ubuntu:~$ iwlist eth1 scan
eth1      Scan completed :
          
          Cell 02 - Address: 00:13:46:3E:50:90
                    ESSID:"hyperion"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=61/100  Signal level=-64 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2
                    Extra: Last beacon: 317ms ago

hyperion@ubuntu:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"hyperion"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:3E:50:90
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-27 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



- /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
    script grep
    map eth0

# The primary network interface
# The Wifi network interface

iface eth1 inet static
pre-up /etc/init.d/wpasupplicant start
wireless-mode Managed
wireless-essid hyperion
wireless-key mykey 
pre-down /etc/init.d/wpa supplicant stop
address 192.168.0.102
netmask 255.255.255.0
gateway 192.168.0.1



auto eth1


# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.


ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1

network={
      ssid="hyperion"
       scan_ssid=1
      proto=WPA
      key_mgmt=WPA-PSK
      psk="mykey"

}

But after rebooting a computer, my card doesn't cath a signal ,she's on standby. 


i have this message: 

-No space for Tx
- Failed to send ESSID command


hyperion@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"hyperion"
          Mode:Managed  Channel=0  Access Point: 00:13:46:3E:50:90
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Can you help me please?

Thank's

p.S: sorry for my english

---

### Post by kingsidy on 2006-01-03
make sure that in system > netwoking, you check the enable this connection. In the same window fill in the essid and passwork if necessary, leave the dhcp alone click on ok and see if it connects. there are also other tools like gtkwifi which manage wireless connections. I have an intel pro 2200b/g as well and i never had a problem connecting to networks at all. the card is supported by default by ubuntu. there are also other programs like wifi radar.

---

### Post by stardust.one on 2006-01-07
Hi

I have found a solution, the acpi cause some troubles

in menu.list in grub

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda6 ro [COLOR="Red"]acpi=off irqpoll [/COLOR]quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


thank's

---


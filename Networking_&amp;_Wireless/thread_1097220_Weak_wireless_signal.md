---
title: "Weak wireless signal"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Ryvius on 2009-03-15
I just installed Ubuntu 8.10 a few hours ago and I have a signal strength of about 12-13%. On Windows XP this was much higher, so I'm assuming this is a driver issue in Ubuntu. Things to note are: no flashing light on my USB dongle and no driver was needed for installation, which I find very strange.

As I say, I only just installed Ubuntu; and have never used Linux before, so my knowledge is slim to none.

Any suggestions?

Edit: Over the past 24 hours I've learnt a little in regards to basic linux usage. I realise now how little information I previously provided.

Taken from lsusb:
```
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
```

Taken from iwconfig:
```
wlan0     IEEE 802.11bg  ESSID:"BTHomeHub2-5CMG"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:24:2B:35:CB:A2   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=13/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Taken from ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:18:e7:07:8a:e0  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe07:8ae0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3743452 (3.7 MB)  TX bytes:689810 (689.8 KB)
```

Taken from lsmod | grep 8187:
```
rtl8187                53248  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbcore               149360  7 rtl8187,ndiswrapper,usb_storage,libusual,uhci_hcd,ehci_hcd
```

Taken from lshw -C network:
```
 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:db:c6:b5:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:e7:07:8a:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:83:5c:41:19:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

These are just things I've picked up from looking through tutorials and other peoples issues. But with my limited knowledge, I can't seem to get my head around the issue. Maybe someone will spot something in here, that I haven't.

Oh, and if you want me to echo any other commands, just let me know.

---

### Post by Ryvius on 2009-03-17
Bumped due to edit.

---

### Post by Crafty Kisses on 2009-03-17
Hey there Ryvius! I don't think you mentioned if it's actually effecting your Internet performance. Is the connection slow? Here's what I'm going to do, I'm going to ask you to download [this]("http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-jadams-2-1-2008.tar.gz") driver. Once you have downloaded that driver for your card, run these commands:
```
tar xvzf rtl8187b-modified-jadams-2-1-2008.tar.gz
cd rtl8187b-modified*
chmod 777 *
sudo chmod +x makedrv
sudo ./wlan0up
```
Once you have done that, your wireless card should be working, or at least working better.

---

### Post by Ryvius on 2009-03-17
Yeah, my internet connection speed is hugely reduced, sorry.

I'm getting this with the last command:
```
ryvius@ryvius:~/Desktop/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211-rtl.ko': -1 Invalid module format
insmod: error inserting 'r8187.ko': -1 Invalid module format
```

---

### Post by Crafty Kisses on 2009-03-17
Do you have the following package installed?
```
sudo apt-get install build-essential
```

---

### Post by Ryvius on 2009-03-17
I have now. Haha.

I also restarted and tried again.

```
ryvius@ryvius:~/Desktop$ sudo tar xvzf rtl8187b-modified-jadams-2-1-2008.tar.gz
rtl8187b-modified/
rtl8187b-modified/wlan0rmv
rtl8187b-modified/ReadMe.txt
rtl8187b-modified/wlan0dhcp
rtl8187b-modified/release_note
rtl8187b-modified/README.FIRST
rtl8187b-modified/wlan0up
rtl8187b-modified/wpa_supplicant-0.5.3/
rtl8187b-modified/wpa_supplicant-0.5.3/eloop_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_testing.txt
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_ssid.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.conf
rtl8187b-modified/wpa_supplicant-0.5.3/aes_wrap.c
rtl8187b-modified/wpa_supplicant-0.5.3/main.c
rtl8187b-modified/wpa_supplicant-0.5.3/Makefile
rtl8187b-modified/wpa_supplicant-0.5.3/nmake.mak
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_leap.c
rtl8187b-modified/wpa_supplicant-0.5.3/.config
rtl8187b-modified/wpa_supplicant-0.5.3/os_unix.c
rtl8187b-modified/wpa_supplicant-0.5.3/wireless_copy.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_ctrl.h
rtl8187b-modified/wpa_supplicant-0.5.3/pcsc_funcs.h
rtl8187b-modified/wpa_supplicant-0.5.3/sha1.c
rtl8187b-modified/wpa_supplicant-0.5.3/ndis_events.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tlv.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_file.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_atmel.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_ctrl.c
rtl8187b-modified/wpa_supplicant-0.5.3/ms_funcs.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wired.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk.c
rtl8187b-modified/wpa_supplicant-0.5.3/build_config.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_types.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eloop.h
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_unix.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_methods.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_aka.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_gnutls.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wext.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_defs.h
rtl8187b-modified/wpa_supplicant-0.5.3/eloop.c
rtl8187b-modified/wpa_supplicant-0.5.3/ndis_events.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/main_winmain.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_peap.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/main.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/setup-mingw-cross-compiling
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpamsg.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpagui.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/userdatarequest.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpagui.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/eventhistory.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/userdatarequest.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/eventhistory.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/networkconfig.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpa_gui.pro
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/networkconfig.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/scanresults.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/scanresults.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/examples/
rtl8187b-modified/wpa_supplicant-0.5.3/examples/plaintext.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wpa-psk-tkip.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wep.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wpa2-eap-ccmp.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/ieee8021x.conf
rtl8187b-modified/wpa_supplicant-0.5.3/ms_funcs.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_hostap.c
rtl8187b-modified/wpa_supplicant-0.5.3/crypto.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_vendor_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_dbus.c
rtl8187b-modified/wpa_supplicant-0.5.3/eloop_win.c
rtl8187b-modified/wpa_supplicant-0.5.3/preauth_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/pcsc_funcs.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_pcap.c
rtl8187b-modified/wpa_supplicant-0.5.3/hostapd.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_hostap.h
rtl8187b-modified/wpa_supplicant-0.5.3/tls_schannel.c
rtl8187b-modified/wpa_supplicant-0.5.3/common.h
rtl8187b-modified/wpa_supplicant-0.5.3/radius.c
rtl8187b-modified/wpa_supplicant-0.5.3/aes_wrap.h
rtl8187b-modified/wpa_supplicant-0.5.3/os_win32.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver.h
rtl8187b-modified/wpa_supplicant-0.5.3/radius_client.h
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_sm.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_dbus.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_ttls.h
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/copying
rtl8187b-modified/wpa_supplicant-0.5.3/os.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls.c
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_sm.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis_.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_bsd.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_md5.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/events.c
rtl8187b-modified/wpa_supplicant-0.5.3/pmksa_cache.c
rtl8187b-modified/wpa_supplicant-0.5.3/main_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/drivers.c
rtl8187b-modified/wpa_supplicant-0.5.3/crypto_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_freebsd.c
rtl8187b-modified/wpa_supplicant-0.5.3/readme
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_ttls.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/rc4.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_passphrase.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_cli.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/config.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_fast.c
rtl8187b-modified/wpa_supplicant-0.5.3/defconfig
rtl8187b-modified/wpa_supplicant-0.5.3/md5.h
rtl8187b-modified/wpa_supplicant-0.5.3/config.h
rtl8187b-modified/wpa_supplicant-0.5.3/defs.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_otp.c
rtl8187b-modified/wpa_supplicant-0.5.3/ChangeLog
rtl8187b-modified/wpa_supplicant-0.5.3/main_winsvc.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/preauth.h
rtl8187b-modified/wpa_supplicant-0.5.3/README-Windows.txt
rtl8187b-modified/wpa_supplicant-0.5.3/rc4.h
rtl8187b-modified/wpa_supplicant-0.5.3/win_example.reg
rtl8187b-modified/wpa_supplicant-0.5.3/os_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/config_winreg.c
rtl8187b-modified/wpa_supplicant-0.5.3/priv_netlink.h
rtl8187b-modified/wpa_supplicant-0.5.3/todo.txt
rtl8187b-modified/wpa_supplicant-0.5.3/doc/
rtl8187b-modified/wpa_supplicant-0.5.3/doc/kerneldoc2doxygen.pl
rtl8187b-modified/wpa_supplicant-0.5.3/doc/code_structure.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/porting.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/wpa_supplicant.fig
rtl8187b-modified/wpa_supplicant-0.5.3/doc/driver_wrapper.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/eap.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/ctrl_iface.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/mainpage.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/testing_tools.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/doxygen.fast
rtl8187b-modified/wpa_supplicant-0.5.3/doc/doxygen.full
rtl8187b-modified/wpa_supplicant-0.5.3/doc/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/Makefile
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_cli.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_passphrase.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_cli.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.conf.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_passphrase.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_background.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_background.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.conf.5
rtl8187b-modified/wpa_supplicant-0.5.3/sha1.h
rtl8187b-modified/wpa_supplicant-0.5.3/version.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_methods.c
rtl8187b-modified/wpa_supplicant-0.5.3/base64.h
rtl8187b-modified/wpa_supplicant-0.5.3/win_if_list.c
rtl8187b-modified/wpa_supplicant-0.5.3/radius_client.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls.h
rtl8187b-modified/wpa_supplicant-0.5.3/crypto_gnutls.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_gtc.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_mschapv2.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/common.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndiswrapper.c
rtl8187b-modified/wpa_supplicant-0.5.3/preauth.c
rtl8187b-modified/wpa_supplicant-0.5.3/base64.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_openssl.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_udp.c
rtl8187b-modified/wpa_supplicant-0.5.3/config_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/md5.c
rtl8187b-modified/wpa_supplicant-0.5.3/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/openssl-tls-extensions.patch
rtl8187b-modified/wpa_supplicant-0.5.3/pmksa_cache.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/tags
rtl8187b-modified/wpa_supplicant-0.5.3/driver_madwifi.c
rtl8187b-modified/wpa_supplicant-0.5.3/includes.h
rtl8187b-modified/wpa_supplicant-0.5.3/state_machine.h
rtl8187b-modified/wpa_supplicant-0.5.3/radius.h
rtl8187b-modified/wpa_supplicant-0.5.3/aes.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wext.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/main.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpamsg.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpagui.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/userdatarequest.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpagui.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/eventhistory.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/userdatarequest.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/eventhistory.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/networkconfig.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpa_gui.pro
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/networkconfig.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/scanresults.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/scanresults.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tlv.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_prism54.c
rtl8187b-modified/wpa_supplicant-0.5.3/crypto.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_winpcap.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ipw.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_linux.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_broadcom.c
rtl8187b-modified/makedrv
rtl8187b-modified/install
rtl8187b-modified/ifcfg-wlan0
rtl8187b-modified/ieee80211/
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.c
rtl8187b-modified/ieee80211/ieee80211_crypt.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
rtl8187b-modified/ieee80211/kmap_types.h
rtl8187b-modified/ieee80211/proc.c
rtl8187b-modified/ieee80211/Makefile
rtl8187b-modified/ieee80211/license
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
rtl8187b-modified/ieee80211/ieee80211_rx.o
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
rtl8187b-modified/ieee80211/.ieee80211-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_softmac.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
rtl8187b-modified/ieee80211/Modules.symvers
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
rtl8187b-modified/ieee80211/ieee80211_wx.c
rtl8187b-modified/ieee80211/.tmp_versions/
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
rtl8187b-modified/ieee80211/scatterwalk.c
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c
rtl8187b-modified/ieee80211/ieee80211_module.c
rtl8187b-modified/ieee80211/.ieee80211_rx.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_tx.o.cmd
rtl8187b-modified/ieee80211/.ieee80211-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
rtl8187b-modified/ieee80211/api.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_wx.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
rtl8187b-modified/ieee80211/ieee80211_softmac_wx.c
rtl8187b-modified/ieee80211/ieee80211_crypt.h
rtl8187b-modified/ieee80211/ieee80211.h
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_wx.o
rtl8187b-modified/ieee80211/rtl_crypto.h
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.c
rtl8187b-modified/ieee80211/ieee80211-rtl.o
rtl8187b-modified/ieee80211/compress.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
rtl8187b-modified/ieee80211/.ieee80211-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
rtl8187b-modified/ieee80211/.ieee80211_module.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211_tx.o
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.o.cmd
rtl8187b-modified/ieee80211/cipher.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
rtl8187b-modified/ieee80211/ieee80211-rtl.mod.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
rtl8187b-modified/ieee80211/autoload.c
rtl8187b-modified/ieee80211/readme
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
rtl8187b-modified/ieee80211/Module.symvers
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep.c
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
rtl8187b-modified/ieee80211/digest.c
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211_softmac.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.c
rtl8187b-modified/ieee80211/arc4.c
rtl8187b-modified/ieee80211/ieee80211_rx.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.ko.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
rtl8187b-modified/ieee80211/ieee80211-rtl.ko
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
rtl8187b-modified/ieee80211/tags
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt.o
rtl8187b-modified/ieee80211/scatterwalk.h
rtl8187b-modified/ieee80211/.ieee80211_softmac_wx.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/aes.c
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.c
rtl8187b-modified/ieee80211/michael_mic.c
rtl8187b-modified/ieee80211/ieee80211_tx.c
rtl8187b-modified/ieee80211/ieee80211_module.o
rtl8187b-modified/ieee80211/ieee80211_softmac.o
rtl8187b-modified/ieee80211/internal.h
rtl8187b-modified/wlan0down
rtl8187b-modified/rtl8187/
rtl8187b-modified/rtl8187/r8180_wx.c
rtl8187b-modified/rtl8187/Makefile
rtl8187b-modified/rtl8187/license
rtl8187b-modified/rtl8187/r8180_93cx6.h
rtl8187b-modified/rtl8187/r8180_rtl8225.h
rtl8187b-modified/rtl8187/r8180_rtl8225.o
rtl8187b-modified/rtl8187/r8187.ko
rtl8187b-modified/rtl8187/Modules.symvers
rtl8187b-modified/rtl8187/.r8187.o.cmd
rtl8187b-modified/rtl8187/.tmp_versions/
rtl8187b-modified/rtl8187/.tmp_versions/r8187.mod
rtl8187b-modified/rtl8187/r8187.mod.o
rtl8187b-modified/rtl8187/r8180_wx.o
rtl8187b-modified/rtl8187/r8180_93cx6.o
rtl8187b-modified/rtl8187/ieee80211_crypt.h
rtl8187b-modified/rtl8187/ieee80211.h
rtl8187b-modified/rtl8187/r8187.h
rtl8187b-modified/rtl8187/r8180_rtl8225.c
rtl8187b-modified/rtl8187/.r8187.ko.cmd
rtl8187b-modified/rtl8187/copying
rtl8187b-modified/rtl8187/install
rtl8187b-modified/rtl8187/.r8180_wx.o.cmd
rtl8187b-modified/rtl8187/.r8180_rtl8225z2.o.cmd
rtl8187b-modified/rtl8187/readme
rtl8187b-modified/rtl8187/changes
rtl8187b-modified/rtl8187/r8180_pm.h
rtl8187b-modified/rtl8187/authors
rtl8187b-modified/rtl8187/r8180_pm.c
rtl8187b-modified/rtl8187/Module.symvers
rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
rtl8187b-modified/rtl8187/r8187_core.c
rtl8187b-modified/rtl8187/r8187.o
rtl8187b-modified/rtl8187/.r8187.mod.o.cmd
rtl8187b-modified/rtl8187/r8180_hw.h
rtl8187b-modified/rtl8187/r8180_93cx6.c
rtl8187b-modified/rtl8187/.r8187_core.o.cmd
rtl8187b-modified/rtl8187/r8187_core.o
rtl8187b-modified/rtl8187/tags
rtl8187b-modified/rtl8187/r8187.mod.c
rtl8187b-modified/rtl8187/.r8180_93cx6.o.cmd
rtl8187b-modified/rtl8187/r8180_rtl8225z2.c
rtl8187b-modified/rtl8187/r8180_wx.h
rtl8187b-modified/rtl8187/.r8180_rtl8225.o.cmd
ryvius@ryvius:~/Desktop$ cd rtl8187b-modified*
ryvius@ryvius:~/Desktop/rtl8187b-modified$ sudo chmod 777 *
ryvius@ryvius:~/Desktop/rtl8187b-modified$ sudo chmod +x makedrv
ryvius@ryvius:~/Desktop/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211-rtl.ko': -1 Invalid module format
insmod: error inserting 'r8187.ko': -1 Invalid module format
```

Still got the same error.

---

### Post by Crafty Kisses on 2009-03-17
You may want to read [this]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b").

---

### Post by Ryvius on 2009-03-17
```
WPA/WPA2 are not supported. only non-encrypted and WEP encrypted networks function.
```

I can't use that guide, as I'm WPA/WPA2 and on Ubuntu 8.10.

At the bottom it tells me what I already know:
```
[..]the presence of such warnings, the fact that its in unstable release, and that I find wireless speed is greatly reduced, my guess is somewhere between 30%-50% loss in speed which is quite significant. Range is also reduced approx 50-60%.[..]
```

---

### Post by Ryvius on 2009-03-17
Heres a screenshot, just to show you how low it is:
[IMG]http://i216.photobucket.com/albums/cc299/infiniteryvius/signal.gif[/IMG]

---

### Post by brummie on 2009-03-17
I have the same problem

Ubuntu 8.04 functions perfect in both 64/32 bit versions
Ubuntu 8.10 has the problem in both 64/32 bit version.

Even Fedora 10 which i've just tried (to see if it was just ubuntu) has this problem.

Its bloody annoying as i can put on 8.04 and its fine :(

---

### Post by Ryvius on 2009-03-17
Ah, damn. I don't want to have to install Unbuntu 8.04, as I've already had to install Ubuntu 8.10 numerous time due to other problems I've had.

Someone help us out!

---

### Post by sargeant dread on 2009-03-17
My internet doesn't work well enough to update or surf the net using firefox unless it has a very strong signal strength (normally 80% or better). With windows i can surf at much lower strengths

---

### Post by qduaty on 2009-04-25
They reduced transmit power in drivers in order to make them working with so-called "regulatory domains", which are not yet implemented (lol). Drivers read txpower data from the hardware and report them as a maximum, to the system. In my case (rt61 card) these hardcoded values are of 10-14 dBm. However, it can be fixed in the driver source and so I did several months ago. With their 10 dBm of txpower, my downstream rate rarely exceeded 50 Kb/s.

---


---
title: "Trying to understand relationship between wifi components"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by stardotstar on 2006-01-26
OK, if anyone can clarify the way these components interrelate I would be most grateful.

I have been doing heaps of reading and research on wifi since i have been plagued with dropouts and wired behaviour that I can't directly attribute to either of my wireless routers (though my NetGear WGR614 is suspect:rolleyes: ) 

In order to determine that i have the best configuration for my ThinkPad R51 with the Intel Wireless Pro 2200BG I have been looking at the ndiswrapper wiki and other threads as well as using Network Manager and nm-applet without configuring anything in the Gnome Network Configurator.  Therefore until now my /etc/network/interfaces was empty.

Network Manager was finding the networks OK but having lots of trouble with WEP so turning that off improved things but still I would get wierd results like assigned APIPA IPs and continual failure to connect.  (I have some logs of that if anyone thinks it would be informative.)

Now I have decided to go through the ndiswrapper process and after a lot of trouble found the two called for files for the ipw2200.

I have linked to them here for those who may find this a useful place for them - most of the links I googled were dead:

[w22n51.INF]("http://www.sourcepoint.com.au/tempupload/w22n51.INF")
[w22n51.sys]("http://www.sourcepoint.com.au/tempupload/w22n51.sys")

I then loaded the drivers thus:

```

root@geko:/home/wparker/downloads/drivers/wireless# ls
ipw2200-1.0.0.tgz  w22n51.INF  w22n51.sys  w29n51.sys
root@geko:/home/wparker/downloads/drivers/wireless# ndiswrapper -i w22n51.INF
Installing w22n51

root@geko:/home/wparker/downloads/drivers/wireless# modprobe ndiswrapper
root@geko:/home/wparker/downloads/drivers/wireless# ndiswrapper -l
Installed ndis drivers:
w22n51  driver present, hardware present

eth1      IEEE 802.11g  ESSID:"Casper"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:4C:43:0C
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=99/100  Signal level=-22 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

root@geko:/home/wparker/downloads/drivers/wireless# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

``` 

So my Network Manager connection is still good and held up through the process.  Which leads me to wonder...

When and where will the ndiswrapper driver apply to my use of the device?  Will Network Manager be using the older or newer drivers (does this even come into it??)  Do I need to disable Network Manager and use the Gnome Configurator?

If I load wifi radar will it interfere yet further with the process?

Do I need to start using wlan0 as the interface or will the eth1 interface make use of the new driver?  Am I getting this all wrong??

What I guess I am trying to understand is what advantage will I get from using the ndiswrapper as I have applied above?

I know this is a subject with a dozen questions a day but I am hoping I am beginning to grok it...

TIA Will

---

### Post by mpvano on 2006-01-27
ndiswrapper is just an adapter that allows you to use a WINDOWS operating system driver for your card instead of a LINUX operating system driver.

It's useful in cases where the Linux driver doesn't exist or has less features than the windows driver or has bugs that make it unusable.

You don't ADD the ndiswrapper driver. If you use ndiswrapper, you are using a completely different driver program (the one you configured ndiswrapper to use by telling it where to find a windows driver .inf file).

In many cases, drivers specify the name they wish to use at the time they are loaded. Most ndiswrapper drivers default to using drivers named "wlanxx" where xx is the next free driver number not yet used. Many linux drivers for wireless cards (even the same card) default to naming themselves "ethxx" when they load.

One hidden problem that many users experience is that a lot of newer drivers (no matter if they are linux or windows drivers used with ndiswrapper) do not any longer have the ability to scan for wireless networks properly. This is true for some cards EVEN IF THIS USED TO WORK IN THE PAST.

Scanning problems make it very hard to tell what's going on if you have more than one wireless network in range. ESPECIALLY if more than one are on the same channel (a very common situation - surprisingly both networks can work this way without either realizing it's happening - there is some loss of performance, however).

If you are receiving more than one wireless network and your card's RADIO is configured to be able to talk to more than one of them, your card may connect to the wrong one. Once it does this, the authorization method or other configuration options may deny it the ability to gain an IP address using DHCP.

The only cure for this may be for your card to be told to connect to a specific ESSID on a specific channel before it attempts to ask for an IP address.

At the moment confusion over and problems with scanning (the ability of a wireless card/driver combination to identify the ESSID, channel and authorization mode of all the base stations within range and make a list of them) creates some situations that don't seem to be logical.

If you have access to more than one driver that seems to work, try the following tests - the information you gather may clarify the situation:

For each driver, try the command "sudo eth0 iwlist scan"  (substitue the name of the card for eth0 if different with your driver). If this command reports that your card doesn't support scanning with ANY of your drivers, it's very hard to make most network managers work properly.

The list of access points and their detailed descriptions provided by this command (if it works on even one of your srivers) can make the situation much clearer. If you can't get this command to work with any of your drivers you may still be able to at least get the information about the correct access point and one or more of the ones causing a problem in the following manner:

If you can get a connection SOMETIMES, try the following:

sudo iwconfig

This should report a lot of information about the current connection, including the ESSID and channel number. Using this command when your connection is NOT working can also be useful because it may tell you that your radio is connected to a DIFFERENT ESSID than you expect.

Once you know the ESSID and channel number of the base station you are trying to connect to, you can configure your wireless tools to specify the essid and channel of what you wish to connect to. That way, other base stations will be ignored.

Unfortunately, if you can't scan, you can't evaluate the situation easily, so it's hard to tell what you're up against. Most people don't know how to set up their wireless routers properly to avoid interference if there's another nearby base station. Furthermore, base stations that don't require any authorization to connect to have a nasty habit of "capturing" your wireless connection if you just set your drivers to connect without specifying essid, channel and security by means of WEP or something similar.

This function of making sure you connect to the CORRECT network is one of the most important reasons why all networks (even open ones) need to have WEP or other authentication methods enabled. If you wan't to run an open network, tell people the ESSID and WEP key.

I have found over that past year that nearly every open wireless network I use in a public place has overlapping coverage from one or more unprotected networks in the same building. This has caused me strange problems using the desired networks, especially when more than one network is on the same channel.

A little informal survey has shown me that as often as not, people are connecting to the WRONG NETWORK in these places. In some cases, the owners of the "ghost" networks have become very upset when they discovered this "unauthorized use" despite the fact that it's clearly their own fault. If you're using an open network (as you say you are), I suggest that you'd be better off using WEP40 and giving it an obvious password like 123456 (I think that's the right number of digits) or something JUST to make sure you're actually connecting to the expected network.

hope this provides a little more info about what may be going on with your networks....

Mario

---

### Post by stardotstar on 2006-01-27
Thanks Mario, that is a great explanation and makes a new kind of sense to me.  I am finally  coming to grips with this.

It seems that I have the most success connecting to WEP protected networks if they are OPEN, as opposed to shared key or WPA and I sometimes have to fool around with the 64bit(40 bit) or 128Bit ASCII or HEX combinations since it seems that passkeys and hex/ascii strings are not the same thing in all managers.

I have just this evening ditched my Netgear WGR614 in favour of a new D-Link DI624 and have had no trouble since initially hacking out the connection.

It seems that Ubuntu needed rebooting before it would Network Manager would properly handshake with the new router - it could see the original SSID (default) and had no trouble connecting via the wired dhcp connection.  But it would fail getting an IP with the wireless despite having an allowed MAC entry in the router and there being no WEP to begin with.

What you say about WEP is fascinating because there is an unencrypted network around here that I cannot attatch to but often shows up with a strong signal so now that WEP is working I may have a more reliable connection - especially since I am now using the ndiswrapper W22n51.ini and .sys  drivers.  By all accounts there is some confusion about how useful the ndiswrapper is for this interface.  So I chose not to build the ipw2200 project on sf from scratch this time.

The firmware looks current and the loading of the ndiswrapper worked well so I am assuming that my kernel is using the definitive driver - and this may have contributed to a more consistent connection experience this evening and today already (regardless of a new router on deck!)

Here are the tests you suggested and I cannot fault the setup - it is clearly able to scan and happy to make a connection:

```

wparker@geko:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:13:46:BD:49:16
                    ESSID:"skink"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=95/100  Signal level=-31 dBm
                    Extra: Last beacon: 4759ms ago

wparker@geko:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"skink"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:BD:49:16
          Bit Rate=36 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-65 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:4

sit0      no wireless extensions.

``` 
Thanks for your insight and the time taken to answer my many questions :KS

Maybe I was up against a combination of a dodgy router at home, out dated ipw2200 drivers in Linux - but I am still having firmware issues (see code later in post).

Here is some of the syslog messages I was getting when things were falling apart last night (pre ndiswrapper and on the Netgear WGR614 (which has a bad rep if you google it :rolleyes:))

```

wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:20:34 localhost NetworkManager: <information>^IActivation (eth1/wireless): using essid 'sourcepoint', with no authentication.
Jan 26 17:20:43 localhost kernel: [4373778.527000] eth1: no IPv6 routers present
Jan 26 17:20:51 localhost NetworkManager: <debug info>^I[1138260051.284556]  (): Activation (eth1/wireless): no hardware link to 'sourcepoint' in non-encrypted mode.
Jan 26 17:20:51 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 17:20:51 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 17:20:51 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 (Device Configure) complete.
Jan 26 17:20:51 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (sourcepoint)
Jan 26 17:20:51 localhost NetworkManager: <information>^IDeactivating device eth1.
Jan 26 17:20:53 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (sourcepoint)
Jan 26 17:20:53 localhost NetworkManager: <information>^IDeactivating device eth1.
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Jan 26 17:23:01 localhost dhclient:
Jan 26 17:23:01 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 17:23:01 localhost NetworkManager: <information>^IDHCP daemon state now 12 for interface eth1
Jan 26 17:23:01 localhost NetworkManager: <information>^IActivation (eth1) Stage 3 (IP Configure Start) complete.
Jan 26 17:23:01 localhost NetworkManager: <information>^IDHCP daemon state now 1 for interface eth1
Jan 26 17:23:01 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost NetworkManager: <information>^IDHCP daemon state now 1 for interface eth1
Jan 26 17:23:01 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 26 17:23:04 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 26 17:23:04 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:07 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:08 localhost kernel: [4373923.997000] eth1: no IPv6 routers present
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost NetworkManager: <information>^IDHCP daemon state now 1 for interface eth1
Jan 26 17:23:01 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 26 17:23:04 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 26 17:23:04 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:07 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:08 localhost kernel: [4373923.997000] eth1: no IPv6 routers present
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost dhclient: sit0: unknown hardware address type 776
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 26 17:23:04 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 26 17:23:04 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:07 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:08 localhost kernel: [4373923.997000] eth1: no IPv6 routers present
Jan 26 17:23:15 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 26 17:23:04 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 26 17:23:04 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:07 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:08 localhost kernel: [4373923.997000] eth1: no IPv6 routers present
Jan 26 17:23:15 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jan 26 17:23:18 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:01 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:01 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 26 17:23:04 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 26 17:23:04 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:07 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 26 17:23:08 localhost kernel: [4373923.997000] eth1: no IPv6 routers present
Jan 26 17:23:15 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jan 26 17:23:18 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:26 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 26 17:23:26 localhost dhclient: Sending on   Socket/fallback
Jan 26 17:23:26 localhost NetworkManager: <information>^Iautoip: Sending probe #0 for IP address 169.254.131.165.
Jan 26 17:23:26 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 14 for interface eth1
Jan 26 17:23:26 localhost dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Jan 26 17:23:26 localhost dhclient: send_packet: Network is unreachable
Jan 26 17:23:26 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 11 for interface eth1
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 14 for interface eth1
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 14 for interface eth1
Jan 26 17:23:26 localhost dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Jan 26 17:23:26 localhost dhclient: send_packet: Network is unreachable
Jan 26 17:23:26 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 11 for interface eth1
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 14 for interface eth1
Jan 26 17:23:28 localhost NetworkManager: <information>^Iautoip: Sending probe #1 for IP address 169.254.131.165.
Jan 26 17:23:28 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:30 localhost NetworkManager: <information>^Iautoip: Sending probe #2 for IP address 169.254.131.165.
Jan 26 17:23:30 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:26 localhost dhclient: send_packet: Network is unreachable
Jan 26 17:23:26 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 11 for interface eth1
Jan 26 17:23:26 localhost NetworkManager: <information>^IDHCP daemon state now 14 for interface eth1
Jan 26 17:23:28 localhost NetworkManager: <information>^Iautoip: Sending probe #1 for IP address 169.254.131.165.
Jan 26 17:23:28 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:30 localhost NetworkManager: <information>^Iautoip: Sending probe #2 for IP address 169.254.131.165.
Jan 26 17:23:30 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:33 localhost NetworkManager: <information>^Iautoip: Sending announce #0 for IP address 169.254.131.165.
Jan 26 17:23:33 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
wparker@geko:/media/fat/Ubuntu$ tail /var/log/syslog
Jan 26 17:23:33 localhost NetworkManager: <information>^Iautoip: Sending announce #0 for IP address 169.254.131.165.
Jan 26 17:23:33 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:36 localhost NetworkManager: <information>^Iautoip: Sending announce #1 for IP address 169.254.131.165.
Jan 26 17:23:36 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:39 localhost NetworkManager: <information>^Iautoip: Sending announce #2 for IP address 169.254.131.165.
Jan 26 17:23:39 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jan 26 17:23:42 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 (IP Configure Commit) scheduled...
Jan 26 17:23:42 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 (IP Configure Timeout) complete.
Jan 26 17:23:42 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 (IP Configure Commit) started...
Jan 26 17:23:42 localhost NetworkManager: <information>^IYour IP address = 169.254.131.165

Jan 26 20:47:07 localhost NetworkManager: <information>^IFORCE: device '/org/freedesktop/NetworkManager/Devices/eth1', network 'sourcepoint'
Jan 26 20:47:07 localhost NetworkManager: <information>^IDeactivating device eth1.
Jan 26 20:47:09 localhost NetworkManager: <debug info>^I[1138272429.757634]  (): Forcing AP 'sourcepoint'
Jan 26 20:47:09 localhost NetworkManager: <information>^IActivated the DHCP daemon /sbin/dhcdbd with PID 8307.
Jan 26 20:47:09 localhost dhcdbd: Started up.
wparker@geko:~$ tail /var/log/syslog
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) started...
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 (Device Prepare) scheduled...
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 (Device Prepare) started...
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 (Device Configure) scheduled...
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 (Device Prepare) complete.
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 (Device Configure) starting...
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1/wireless) Stage 1 (Device Configure) will connect to access point 'sourcepoint'.
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1/wireless): access point 'sourcepoint' is unencrypted, no key needed.
Jan 26 20:47:10 localhost kernel: [4294808.171000] ipw2200: Firmware error detected.  Restarting.
Jan 26 20:47:12 localhost NetworkManager: <information>^IActivation (eth1/wireless): using essid 'sourcepoint', with no authentication.
wparker@geko:~$ tail /var/log/syslog
Jan 26 20:47:10 localhost NetworkManager: <information>^IActivation (eth1/wireless): access point 'sourcepoint' is unencrypted, no key needed.
Jan 26 20:47:10 localhost kernel: [4294808.171000] ipw2200: Firmware error detected.  Restarting.
Jan 26 20:47:12 localhost NetworkManager: <information>^IActivation (eth1/wireless): using essid 'sourcepoint', with no authentication.
Jan 26 20:47:21 localhost kernel: [4294818.906000] eth1: no IPv6 routers present
Jan 26 20:47:29 localhost NetworkManager: <debug info>^I[1138272449.402623]  (): Activation (eth1/wireless): no hardware link to 'sourcepoint' in non-encrypted mode.
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 (Device Configure) complete.
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (sourcepoint)
Jan 26 20:47:29 localhost NetworkManager: <information>^IDeactivating device eth1.
wparker@geko:~$ tail /var/log/syslog
Jan 26 20:47:12 localhost NetworkManager: <information>^IActivation (eth1/wireless): using essid 'sourcepoint', with no authentication.
Jan 26 20:47:21 localhost kernel: [4294818.906000] eth1: no IPv6 routers present
Jan 26 20:47:29 localhost NetworkManager: <debug info>^I[1138272449.402623]  (): Activation (eth1/wireless): no hardware link to 'sourcepoint' in non-encrypted mode.
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 (Device Configure) complete.
Jan 26 20:47:29 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (sourcepoint)
Jan 26 20:47:29 localhost NetworkManager: <information>^IDeactivating device eth1.
Jan 26 20:47:31 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (sourcepoint)
Jan 26 20:47:31 localhost NetworkManager: <information>^IDeactivating device eth1.

```

compared to my experience just now:

```

Jan 27 18:14:51 localhost dhclient:
Jan 27 18:14:51 localhost dhclient: sit0: unknown hardware address type 776
Jan 27 18:14:51 localhost NetworkManager: <information>^IActivation (eth1) Stage 3 (IP Configure Start) complete.
Jan 27 18:14:51 localhost NetworkManager: <information>^IDHCP daemon state now 12 for interface eth1
Jan 27 18:14:51 localhost NetworkManager: <information>^IDHCP daemon state now 1 for interface eth1
Jan 27 18:14:51 localhost dhclient: sit0: unknown hardware address type 776
Jan 27 18:14:51 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Jan 27 18:14:51 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Jan 27 18:14:51 localhost dhclient: Sending on   Socket/fallback
Jan 27 18:14:52 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jan 27 18:14:52 localhost dhclient: DHCPOFFER from 192.168.0.1
Jan 27 18:14:52 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 27 18:14:52 localhost dhclient: DHCPACK from 192.168.0.1
Jan 27 18:14:52 localhost NetworkManager: <information>^IDHCP daemon state now 2 for interface eth1
Jan 27 18:14:52 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 (IP Configure Get) scheduled...
Jan 27 18:14:52 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 (IP Configure Get) started...
Jan 27 18:14:52 localhost NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon:
Jan 27 18:14:52 localhost NetworkManager: <information>^I  address 192.168.0.103
Jan 27 18:14:52 localhost NetworkManager: <information>^I  netmask 255.255.255.0
Jan 27 18:14:52 localhost NetworkManager: <information>^I  broadcast 192.168.0.255
Jan 27 18:14:52 localhost NetworkManager: <information>^I  gateway 192.168.0.1
Jan 27 18:14:52 localhost NetworkManager: <information>^I  nameserver 192.168.0.1
Jan 27 18:14:52 localhost NetworkManager: <information>^I  domain name 'sourcepoint.com.au'
Jan 27 18:14:52 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 (IP Configure Commit) scheduled...
Jan 27 18:14:52 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 (IP Configure Get) complete.
Jan 27 18:14:52 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 (IP Configure Commit) started...
Jan 27 18:14:52 localhost NetworkManager: <information>^IYour IP address = 192.168.0.103
Jan 27 18:14:52 localhost dhclient: bound to 192.168.0.103 -- renewal in 258361 seconds.
Jan 27 18:14:53 localhost NetworkManager: <information>^IAdding nameserver: 192.168.0.1
Jan 27 18:14:53 localhost NetworkManager: <information>^IAdding domain search: sourcepoint.com.au
Jan 27 18:14:53 localhost named[7325]: loading configuration from '/var/lib/NetworkManager/NetworkManager-named.conf'
Jan 27 18:14:53 localhost NetworkManager: <information>^IActivation (eth1) Finish handler scheduled.
Jan 27 18:14:53 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 (IP Configure Commit) complete.
Jan 27 18:14:53 localhost NetworkManager: <information>^IActivation (eth1) successful, device activated.
Jan 27 18:14:53 localhost NetworkManager: <debug info>^I[1138349693.147343]  (): NetworkManagerInfo triggered update of wireless network 'skink'

```

[B]And then, dramatically this:
[/B]
```

Jan 27 18:31:46 localhost -- MARK --
Jan 27 18:44:21 localhost kernel: [4296686.046000] ipw2200: Firmware error detected.  Restarting.
Jan 27 19:11:46 localhost -- MARK --

```

But the connection is working so I am not sure where to go with this.

Perhaps I need to replace:

```

wparker@geko:~$ ls -l /lib/hotplug/firmware/ipw-*
-rw-r--r--  1 root root   6472 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-boot.fw-2.6.12-10-386
-rw-r--r--  1 root root   6472 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-boot.fw-2.6.12-9-386
-rw-r--r--  1 root root 166960 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-bss.fw-2.6.12-10-386
-rw-r--r--  1 root root 166960 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-bss.fw-2.6.12-9-386
-rw-r--r--  1 root root  16334 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-bss_ucode.fw-2.6.12-10-386
-rw-r--r--  1 root root  16334 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-bss_ucode.fw-2.6.12-9-386
-rw-r--r--  1 root root 161568 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-ibss.fw-2.6.12-10-386
-rw-r--r--  1 root root 161568 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-ibss.fw-2.6.12-9-386
-rw-r--r--  1 root root  16312 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-ibss_ucode.fw-2.6.12-10-386
-rw-r--r--  1 root root  16312 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-ibss_ucode.fw-2.6.12-9-386
-rw-r--r--  1 root root 165028 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-sniffer.fw-2.6.12-10-386
-rw-r--r--  1 root root 165028 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-sniffer.fw-2.6.12-9-386
-rw-r--r--  1 root root  16344 2006-01-17 06:48 /lib/hotplug/firmware/ipw-2.3-sniffer_ucode.fw-2.6.12-10-386
-rw-r--r--  1 root root  16344 2005-10-10 23:16 /lib/hotplug/firmware/ipw-2.3-sniffer_ucode.fw-2.6.12-9-386

```

with these firmwares from the sourceforge site and associated there with the driver version I identified here:

```

0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:02.0 0280: 8086:4220 (rev 05)

Jan 27 18:11:47 localhost kernel: [4294710.518000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
Jan 27 18:11:47 localhost kernel: [4294710.518000] ipw2200: Copyright(c) 2003-2004 Intel Corporation

```

The firmware I downloaded:

```

wparker@geko:~/downloads/drivers/wireless$ ls -l ipw-*
-rw-r--r--  1 wparker wparker   6472 2005-05-18 05:17 ipw-2.3-boot.fw
-rw-r--r--  1 wparker wparker 166960 2005-05-18 05:17 ipw-2.3-bss.fw
-rw-r--r--  1 wparker wparker  16334 2005-05-18 05:17 ipw-2.3-bss_ucode.fw
-rw-r--r--  1 wparker wparker 161568 2005-05-18 05:17 ipw-2.3-ibss.fw
-rw-r--r--  1 wparker wparker  16312 2005-05-18 05:17 ipw-2.3-ibss_ucode.fw
-rw-r--r--  1 wparker wparker 165028 2005-05-18 05:17 ipw-2.3-sniffer.fw
-rw-r--r--  1 wparker wparker  16344 2005-05-18 05:17 ipw-2.3-sniffer_ucode.fw

```

Do I need to just load these firmwares into hotplug and reboot to have them loaded by hotplugger or do I need to build a new driver and module with a custom kernel to take advantage of new/more suitable firmware?

Will

---


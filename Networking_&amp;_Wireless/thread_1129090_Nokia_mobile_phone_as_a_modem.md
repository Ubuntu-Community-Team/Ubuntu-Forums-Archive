---
title: "Nokia mobile phone as a modem"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2009-04-18
Hi all, hope you're well

I'm runing Jaunty Beta (KUBUNTU) and love it! All works well apart from the title in the subject.

Now, in the past I've conquered this issue using wvdial and editing the file as below:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

To get onto the web it's simply a matter of oening a terminal and typing:

> sudo wvdial (followed by the password)

Now in Jaunty wvdial is not installed by default so I've downloaded and installed it and made the modifications above. It seems to work and there's an IP address assigned to the connection. However the Nokia 6300 is NOT 3G and I'm not in a 3G area here at home and performance is like sludge!

What I'm trying to do is get Network Manager to work.

I plug the phone in by USB, select Nokia Mode as usual and a notification pops up advising Network Interface ttyACM0 has been detected. I then go into configure connections and make a new connection. The number I dial is *99# and according to Vodafone in the UK the username and password should be web and web.

If I then try to connect I just get an error, "Connection Empty"

Any thoughts?

---

### Post by AlanR8 on 2009-04-19
24 hour bumpity bump!!!

---

### Post by puppywhacker on 2009-04-19
*99# connects to your default internet profile as configure in your phone. I mean the Vodafone GPRS profile should be configured correctly in your phone and set as default.

could you post the output from wvdial and the last 50 messages?
tail -50 /var/log/messages

---

### Post by AlanR8 on 2009-04-19
Output is:

> alan@SONY:~$ tail -50 /var/log/messages
Apr 19 14:04:40 SONY kernel: [   16.213002] type=1505 audit(1240146278.825:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2260   
Apr 19 14:04:40 SONY kernel: [   16.213085] type=1505 audit(1240146278.829:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2260         
Apr 19 14:04:40 SONY kernel: [   16.213116] type=1505 audit(1240146278.829:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2260                                                           
Apr 19 14:04:40 SONY kernel: [   16.213149] type=1505 audit(1240146278.829:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2260                                                                
Apr 19 14:04:40 SONY kernel: [   16.315027] type=1505 audit(1240146278.929:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2265                                                                          
Apr 19 14:04:40 SONY kernel: [   16.315146] type=1505 audit(1240146278.929:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2265         
Apr 19 14:04:40 SONY kernel: [   16.334655] type=1505 audit(1240146278.948:8): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2269
Apr 19 14:04:40 SONY kernel: [   16.377625] type=1505 audit(1240146278.992:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2273       
Apr 19 14:04:43 SONY kernel: [   21.162036] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                                        
Apr 19 14:04:43 SONY kernel: [   21.162038] Bluetooth: BNEP filters: protocol multicast                                                                         
Apr 19 14:04:43 SONY kernel: [   21.175988] Bridge firewalling registered       
Apr 19 14:04:45 SONY kernel: [   22.390566] ppdev: user-space parallel port driver                                                                              
Apr 19 14:04:49 SONY kernel: [   26.388090] sky2 eth0: enabling interface       
Apr 19 14:04:49 SONY kernel: [   26.388270] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                        
Apr 19 14:04:49 SONY kernel: [   26.388853] iwlagn 0000:06:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode                                                  
Apr 19 14:04:49 SONY kernel: [   26.491446] iwlagn 0000:06:00.0: loaded firmware version 228.57.2.23                                                            
Apr 19 14:04:49 SONY kernel: [   26.701221] Registered led device: iwl-phy0::radio                                                                              
Apr 19 14:04:49 SONY kernel: [   26.701406] Registered led device: iwl-phy0::assoc                                                                              
Apr 19 14:04:49 SONY kernel: [   26.703271] Registered led device: iwl-phy0::RX 
Apr 19 14:04:49 SONY kernel: [   26.703291] Registered led device: iwl-phy0::TX 
Apr 19 14:04:49 SONY kernel: [   26.990507] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                       
Apr 19 14:04:52 SONY kernel: [   29.496880] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                  
Apr 19 14:22:47 SONY syslogd 1.5.0#5ubuntu3: restart.                           
Apr 19 14:44:39 SONY -- MARK --                                                 
Apr 19 15:04:39 SONY -- MARK --                                                 
Apr 19 15:06:36 SONY pulseaudio[4712]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:                                                    
Apr 19 15:06:36 SONY pulseaudio[4712]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.                                         
Apr 19 15:06:36 SONY pulseaudio[4712]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Apr 19 15:06:37 SONY pulseaudio[4725]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Apr 19 15:06:37 SONY pulseaudio[4725]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Apr 19 15:06:37 SONY pulseaudio[4725]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become amember of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limitsfor this user.
Apr 19 15:24:38 SONY -- MARK --
Apr 19 15:42:46 SONY kernel: [ 5904.977058] CE: hpet increasing min_delta_ns to15000 nsec
Apr 19 16:04:38 SONY -- MARK --
Apr 19 16:24:38 SONY -- MARK --
Apr 19 16:44:38 SONY -- MARK --
Apr 19 17:04:38 SONY -- MARK --
Apr 19 17:24:38 SONY -- MARK --
Apr 19 17:28:44 SONY kernel: [12262.848052] CE: hpet increasing min_delta_ns to22500 nsec
Apr 19 17:44:38 SONY -- MARK --
Apr 19 18:02:29 SONY kernel: [14288.192198] usb 6-1: USB disconnect, address 2
Apr 19 18:16:43 SONY kernel: [15142.109099] usb 6-1: new low speed USB device using uhci_hcd and address 3
Apr 19 18:16:43 SONY kernel: [15142.340816] usb 6-1: configuration #1 chosen from 1 choice
Apr 19 18:16:43 SONY kernel: [15142.362746] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input12
Apr 19 18:16:43 SONY kernel: [15142.396366] generic-usb 0003:045E:0084.0004: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Apr 19 18:44:38 SONY -- MARK --
Apr 19 19:04:38 SONY -- MARK --
Apr 19 19:24:38 SONY -- MARK --
Apr 19 19:44:38 SONY -- MARK --
Apr 19 20:04:38 SONY -- MARK --
alan@SONY:~$


wvdial is:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

---

### Post by puppywhacker on 2009-04-19
:( not very much ppp / wvdial action in your messages fail, so it stays it's still guesswork: I think you need to look at the GPRS profile in your phone. You need to set the default (do Nokia's have those?) to the GPRS settings from Vodafone.

---

### Post by AlanR8 on 2009-04-30
puppywacker

Here is some more output for you to look at. I'd appreciate your efforts:

> alan@SONY:~$ tail -50 /var/log/messages
Apr 30 13:25:20 SONY pppd[3816]: PAP authentication succeeded
Apr 30 13:25:20 SONY kernel: [  447.121918] PPP BSD Compression module registered
Apr 30 13:25:20 SONY kernel: [  447.160153] PPP Deflate Compression module registered
Apr 30 13:25:21 SONY pppd[3816]: local  IP address 10.57.30.13                       
Apr 30 13:25:21 SONY pppd[3816]: remote IP address 10.6.6.6                          
Apr 30 13:25:21 SONY pppd[3816]: primary   DNS address 10.205.65.68                  
Apr 30 13:25:21 SONY pppd[3816]: secondary DNS address 10.205.65.68                  
Apr 30 13:37:43 SONY pppd[3816]: Terminating on signal 15                            
Apr 30 13:37:43 SONY pppd[3816]: Connect time 12.4 minutes.                          
Apr 30 13:37:43 SONY pppd[3816]: Sent 308424 bytes, received 1564786 bytes.          
Apr 30 13:37:43 SONY pppd[3816]: Connection terminated.                              
Apr 30 13:37:43 SONY pppd[3816]: Exit.                                               
Apr 30 13:37:57 SONY kernel: [ 1203.712234] usb 6-1: USB disconnect, address 2       
Apr 30 13:50:30 SONY syslogd 1.5.0#5ubuntu3: restart.                                
Apr 30 14:18:07 SONY -- MARK --                                                      
Apr 30 14:38:07 SONY -- MARK --
Apr 30 14:58:07 SONY -- MARK --
Apr 30 15:14:04 SONY kernel: [ 6971.412107] usb 6-1: new full speed USB device using uhci_hcd and address 3
Apr 30 15:14:04 SONY kernel: [ 6971.582788] usb 6-1: configuration #1 chosen from 1 choice
Apr 30 15:14:04 SONY kernel: [ 6971.637440] cdc_acm 6-1:1.1: ttyACM0: USB ACM device
Apr 30 15:14:04 SONY kernel: [ 6971.652448] usb 6-1: bad CDC descriptors
Apr 30 15:14:04 SONY kernel: [ 6971.652469] usb 6-1: bad CDC descriptors
Apr 30 15:14:16 SONY pppd[6675]: pppd 2.4.5 started by root, uid 0
Apr 30 15:14:16 SONY pppd[6675]: Using interface ppp0
Apr 30 15:14:16 SONY pppd[6675]: Connect: ppp0 <--> /dev/ttyACM0
Apr 30 15:14:19 SONY pppd[6675]: PAP authentication succeeded
Apr 30 15:14:20 SONY pppd[6675]: local  IP address 10.49.101.182
Apr 30 15:14:20 SONY pppd[6675]: remote IP address 10.6.6.6
Apr 30 15:14:20 SONY pppd[6675]: primary   DNS address 10.203.65.68
Apr 30 15:14:20 SONY pppd[6675]: secondary DNS address 10.203.65.68
Apr 30 15:21:35 SONY pppd[6675]: Terminating on signal 15
Apr 30 15:21:35 SONY pppd[6675]: Connect time 7.3 minutes.
Apr 30 15:21:35 SONY pppd[6675]: Sent 253125 bytes, received 748108 bytes.
Apr 30 15:21:35 SONY pppd[6675]: Connection terminated.
Apr 30 15:21:36 SONY pppd[6675]: Exit.
Apr 30 15:21:39 SONY kernel: [ 7426.033113] usb 6-1: USB disconnect, address 3
Apr 30 15:38:07 SONY -- MARK --
Apr 30 15:39:35 SONY kernel: [ 8502.444073] usb 6-1: new full speed USB device using uhci_hcd and address 4
Apr 30 15:39:35 SONY kernel: [ 8502.666366] usb 6-1: configuration #1 chosen from 1 choice
Apr 30 15:39:36 SONY kernel: [ 8502.734642] cdc_acm 6-1:1.1: ttyACM0: USB ACM device
Apr 30 15:39:36 SONY kernel: [ 8502.738432] usb 6-1: bad CDC descriptors
Apr 30 15:39:36 SONY kernel: [ 8502.738454] usb 6-1: bad CDC descriptors
Apr 30 15:39:54 SONY pppd[7452]: pppd 2.4.5 started by root, uid 0
Apr 30 15:39:54 SONY pppd[7452]: Using interface ppp0
Apr 30 15:39:54 SONY pppd[7452]: Connect: ppp0 <--> /dev/ttyACM0
Apr 30 15:39:57 SONY pppd[7452]: PAP authentication succeeded
Apr 30 15:39:58 SONY pppd[7452]: local  IP address 10.46.74.150
Apr 30 15:39:58 SONY pppd[7452]: remote IP address 10.6.6.6
Apr 30 15:39:58 SONY pppd[7452]: primary   DNS address 10.206.65.68
Apr 30 15:39:58 SONY pppd[7452]: secondary DNS address 10.206.65.68
alan@SONY:~$


Jaunty is now the release version and wvdial continues to work. The network manager still recognises the phone as in the first post. I tried a mate's 02 USB mobile broadband dongle the other night and it was not recognised as a modem but did get seen as hard drive!

---

### Post by AlanR8 on 2009-05-06
Bumpity bump...........

---

### Post by AlanR8 on 2009-07-19
The plot thickens!

In Kubuntu, as stated, I can use wvdial and sucessfully connect so that works but it's not perfect. I just plug in, select PC Suite from the phone menu and all is well.

When I try to set up mobile broadband in the network manager the "form" to fill out will not retain the password and one or two of the connection defaults won't hold their value.

However, I've just installed Ubuntu Netbook Remix 9.10 Alpha, or what ever's in the repos on my EeePC.I saw another thread elsewhere saying that once connected to the phone, do NOT select anything. Just leave the menu on the phone open.

Doing that, produced a wizard that asked what network I was connecting to, Vodafone, and that was about it! It just connected immediately!

Is this a new feature and if so, can I get the functionality in KUBUNTU Jaunty?

---


---
title: "Working WMP54GS WPA2 connection but not after reboot"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by alleycatuk on 2009-07-27
Hi,
I'm very new to Linux as of last Saturday - so far I like what I see. I've had a bit of experience with Unix but not very much so I'm grateful for any help. Installed Jaunty.

I've installed ndiswrapper and wpa_supplicant as I'm on WPA2 and as of tonight I have the internet (which is how I'm posting on here!) but I can't figure out how to get it going every time I boot into Ubuntu.

Ndiswrapper is loading each time and wpa_supplicant seems to be loading as I can see the process. I've worked out a manual procedure to get it working and for DHCP to be happy but it's quite long winded and some bits don't make sense. I've removed Network Manager by the way as that seemed to conflict and I saw a post saying to get rid.

The first odd thing is that System - Admin - Network Tools has to be open for this to work. Not sure why that is!?

OK, here's the process I have discovered. As far as I can tell, missing any bit won't get a DHCP connection.

```
[COLOR=Blue]sudo pkill wpa_supplicant
sudo ifconfig wlan0 down
iwlist wlan0 scan[/COLOR]

```Output is:
[COLOR=SeaGreen]wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:C9:05:32
                    ESSID:"alleycatwlan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK[/COLOR]

```
[COLOR=Blue]sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext[/COLOR]
```[COLOR=SeaGreen]Wireless event: cmd=0x8c07 len=76
AssocReq IE wireless event - hexdump(len=6:  <key here>
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:16:b6:c9:05:32
Association info event
req_ies - hexdump(len=6:  [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]resp_ies - hexdump(len=24):  [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]WPA: set own WPA/RSN IE - hexdump(len=22):  <key here>
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:16:b6:c9:05:32
No keys have been configured - skip key clearing
Associated with 00:16:b6:c9:05:32
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:16:b6:c9:05:32
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=2 type=3 length=117
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=22
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:c9:05:32 (ver=2)
RSN: msg 1/4 key data - hexdump(len=22): <hex removed>
RSN: PMKID from Authenticator - hexdump(len=16):  [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]RSN: no matching PMKID found
WPA: Renewed SNonce - hexdump(len=32): [/COLOR][COLOR=SeaGreen]<hex removed>[/COLOR]
[COLOR=SeaGreen]WPA: PTK derivation - A1=00:16:b6:9e:ab:5a A2=00:16:b6:c9:05:32
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22):  <key here>
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:16:b6:c9:05:32
IEEE 802.1X RX: version=2 type=3 length=175
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=80
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): <key here>
  key_iv - hexdump(len=16):  <key here>
  key_rsc - hexdump(len=: 4f 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: <key here>
  key_mic - hexdump(len=16):  <key here>
RSN: encrypted key data - hexdump(len=80): 
WPA: decrypted EAPOL-Key key data - hexdump(len=72): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:16:b6:c9:05:32 (ver=2)
WPA: IE KeyData - hexdump(len=72):  <key here>
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 4f 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:16:b6:c9:05:32 [PTK=CCMP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:16:b6:c9:05:32 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick[/COLOR]

Then in a second terminal window:
```
[COLOR=Blue]sudo ifconfig wlan0 up
sudo dhclient wlan0[/COLOR]
```I've tried running wpa_supplicant in daemon mode but it doesn't seem to connect. Sometimes, if dhcp won't assign an address, killing wpa_supplicant and running it again does the trick.

Sorry if the above is confusing or doesn't make much sense.... new to all this! 
One final thing - just like to say that I wouldn't have got anywhere near having it working without all the useful guides people post on these forums so a massive thanks for that.

Just to stress I'm still finding my way (2 days in!) so if you could explain anything in as simple terms as possible that would be brilliant.

Cheers in advance.

---

### Post by alleycatuk on 2009-07-29
Ok, no one has replies so I suppose I have a unique problem!
Can anyone help me with a (hopefully) simpler query? If I want to execute a number of routines on boot in order to get my wireless working (i.e. automate what I now do manually), how would I go about that?
Sorry if it's a stupid question - I'm new to linux so am maybe thinking in Windows terms still e.g. some kind of autoexec?
Thanks.

---


---
title: "EAP/TKIP problem"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by AmericanSkin on 2008-12-03
I've search many forums and I've seen posts that have got me started but I cant figure it out. I am trying to connect to my company's wireless network that uses open EAP authentication to a RADIUS server which happens to be a Windows 2003 machine. The wireless also uses TKIP encryption. I have tried many things with no success and could not find anyone else with the same configuration.

I am using the wext WPA driver which works fine with WPA networks that use a passphrase. Below I will post my access point configuration. Any help will be appriciated.

```

Current configuration : 2770 bytes
!
version 12.3
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname ap
!
no logging console

!
ip subnet-zero
!
!
aaa new-model
!
!
aaa group server radius rad_eap
 server 10.0.0.29 auth-port 1645 acct-port 1646
!
aaa group server radius rad_mac
!
aaa group server radius rad_acct
!
aaa group server radius rad_admin
!
aaa group server tacacs+ tac_admin
!
aaa group server radius rad_pmip
!
aaa group server radius dummy
!
aaa authentication login eap_methods group rad_eap
aaa authentication login mac_methods local
aaa authorization exec default local 
aaa accounting network acct_methods start-stop group rad_acct
aaa session-id common
!
dot11 ssid seifert
   vlan 1
   authentication open eap eap_methods 
   authentication key-management wpa
!
!
!
!
!
bridge irb
!
!
interface Dot11Radio0
 no ip address
 no ip route-cache
 !
 encryption vlan 1 mode ciphers tkip 
 !
 encryption vlan 2 mode ciphers tkip 
 !
 ssid seifert
 !
 ssid seifert-guest
 !
 speed basic-1.0 2.0 5.5 6.0 9.0 11.0 12.0 18.0 24.0 36.0 48.0 54.0
 station-role root
!
interface Dot11Radio0.1
 encapsulation dot1Q 1 native
 no ip route-cache
 bridge-group 1
 bridge-group 1 subscriber-loop-control
 bridge-group 1 block-unknown-source
 no bridge-group 1 source-learning
 no bridge-group 1 unicast-flooding
 bridge-group 1 spanning-disabled
!
interface Dot11Radio0.2
 encapsulation dot1Q 2
 no ip route-cache
 bridge-group 2
 bridge-group 2 subscriber-loop-control
 bridge-group 2 block-unknown-source
 no bridge-group 2 source-learning
 no bridge-group 2 unicast-flooding
 bridge-group 2 spanning-disabled
!
interface FastEthernet0
 no ip address
 no ip route-cache
 duplex auto
 speed auto
!
interface FastEthernet0.1
 encapsulation dot1Q 1 native
 no ip route-cache
 bridge-group 1
 no bridge-group 1 source-learning
 bridge-group 1 spanning-disabled
!
interface FastEthernet0.2
 encapsulation dot1Q 2
 no ip route-cache
 bridge-group 2
 no bridge-group 2 source-learning
 bridge-group 2 spanning-disabled
!
interface BVI1
 ip address 10.0.0.6 255.255.255.0
 no ip route-cache
!
ip http server
no ip http secure-server
ip http help-path http://www.cisco.com/warp/public/779/smbiz/prodconfig/help/eag
ip radius source-interface BVI1 
!
radius-server attribute 32 include-in-access-req format %h
radius-server host 10.0.0.29 auth-port 1645 acct-port 1646 key 7 123456789ABCDE
radius-server vsa send accounting
!
control-plane
!         
bridge 1 route ip
!
!
!
line con 0
line vty 0 4
!
end

ap#


```

---


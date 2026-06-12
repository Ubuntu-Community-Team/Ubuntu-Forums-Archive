---
title: "compat wireless aircrack help"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by lodk on 2012-11-15
Ok first off hello to everyone, this is my first post and would like to introduce myself. I am not new to ubuntu but still in the learning process. I have used ubuntu since 10.04 LTS came out. so I know some but not all of how linux works so if I seem miss understood please bare with me thank you.

I as I stated before used 10.04 to learn on and well it went well now over time things have changed eg: unity and so on. well I got a new system " toshiba l755 satellite 64bit partioned it put the new 12.04 on had issues lol tried 12.10 had issues (I know its bata) well went back to 11.04 (yes out dated now but none the less its on my system right now running fine.

my question is I used compat to run aircrack and worked like a charm before on my old system. now this system i have
-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:1e:4c:b2:33:48
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless logical
                configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=yes multicast=yes promiscuous=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:c0500000-c050ffff
for a network and I see the driver. I used this a s a guide [http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)
I did the injection test
lodk@lodk-satellite:~/compat-wireless-2.6.38.2-2$ sudo aireplay-ng -9 mon0
08:00:42  Trying broadcast probe requests...
08:00:43  Injection is working!
08:00:44  Found 3 APs

08:00:44  Trying directed probe requests...
08:00:44  C0:3F:0E:74:89:23 - channel: 2 - 'OSA'
08:00:44  Ping (min/avg/max): 1.178ms/14.900ms/25.230ms Power: -71.30
08:00:44  30/30: 100%

08:00:44  E0:91:F5:AE:50:63 - channel: 2 - 'Meja510'
08:00:50  Ping (min/avg/max): 1.250ms/5.172ms/11.998ms Power: -99.33
08:00:50   3/30:  10%

08:00:50  A0:21:B7:BC:10:10 - channel: 2 - 'Netgear'
08:00:56   0/30:   0%

that seems to be working fine as well. but when it i use aircrack I get this 

lodk@lodk-satellite:~$ sudo aireplay-ng -1 0 -a xxxxxxx -h xxxxxxxxx mon0
07:13:10  Waiting for beacon frame (BSSID: xxxxxxx on channel 6

07:13:10  Sending Authentication Request (Open System)

07:13:12  Sending Authentication Request (Open System) [ACK]
07:13:12  Authentication successful
07:13:12  Sending Association Request [ACK]
07:13:12  Association successful :) (AID: 1)

thats good I know (by the way this is my own router set up with a simple wep of 1234567890 password

well after that I get this ok a chop chop attack

lodk@lodk-satellite:~$ sudo aireplay-ng -4 -h xxxxxxx -b xxxxxxx mon0
07:15:07  Waiting for beacon frame (BSSID: xxxxxxx on channel 6


        Size: 78, FromDS: 1, ToDS: 0 (WEP)

              BSSID  = xxxxxx
          Dest. MAC  = xxxxxxxxx
         Source MAC  = xxxxxxxxx

        0x0000:  0842 0000 0180 c200 0000 0014 bfe7 db68  .B.............h
        0x0010:  0214 bfe7 db69 005a 9697 4d00 9526 d68f  .....i.Z..M..&..
        0x0020:  a20f 1573 c3ff fe7a fac5 3796 a75d 1d71  ...s...z..7..].q
        0x0030:  1a2c 8bdf d740 cad4 4a35 1646 aa48 ccc5  .,...@..J5.F.H..
        0x0040:  b5b7 940c f9ac a5ad 1657 ceab 1d7e       .........W...~

Use this packet ? y

Saving chosen packet in replay_src-1115-071507.cap

Sent 1795 packets, current guess: FC...

The chopchop attack appears to have failed. Possible reasons:

    * You're trying to inject with an unsupported chipset (Centrino?).
    * The driver source wasn't properly patched for injection support.
    * You are too far from the AP. Get closer or reduce the send rate.
    * Target is 802.11g only but you are using a Prism2 or RTL8180.
    * The wireless interface isn't setup on the correct channel.
    * The client MAC you have specified is not currently authenticated.
      Try running another aireplay-ng to fake authentication (attack "-1").
    * The AP isn't vulnerable when operating in authenticated mode.
      Try aireplay-ng in non-authenticated mode instead (no -h option).

or this with fragment attack

sudo aireplay-ng -5 -b xxxxxx -h xxxxxxx mon0
[sudo] password for lodk: 
07:09:12  Waiting for beacon frame (BSSID: xxxxxxx on channel 6
07:09:13  Waiting for a data packet...


        Size: 78, FromDS: 1, ToDS: 0 (WEP)

              BSSID  = xxxxxxx
          Dest. MAC  = xxxxxxx
         Source MAC  = xxxxxxx

        0x0000:  0842 0000 0180 c200 0000 0014 bfe7 db68  .B.............h
        0x0010:  0214 bfe7 db69 00a6 bd96 4d00 872b db03  .....i....M..+..
        0x0020:  5133 9c45 ba8a 645c 5b28 8596 e4c8 da0a  Q3.E..d\[(......
        0x0030:  e389 2598 2dc6 e5af 0b24 1c21 ced6 aaa4  ..%.-....$.!....
        0x0040:  55fa 37e1 2055 5283 181c 76a5 8e89       U.7. UR...v...

Use this packet ? n

Read 26 packets...

        Size: 78, FromDS: 1, ToDS: 0 (WEP)

              BSSID  = xxxxxxx
          Dest. MAC  = xxxxxxx
         Source MAC  = xxxxxxx

        0x0000:  0842 0000 0180 c200 0000 0014 bfe7 db68  .B.............h
        0x0010:  0214 bfe7 db69 80a8 be96 4d00 1330 aa15  .....i....M..0..
        0x0020:  1dba 698b b1c0 ab49 c1ec e43a 2841 309c  ..i....I...A0.
        0x0030:  7192 8336 8376 9f3b e911 1207 4450 cd13  q..6.v.;....DP..
        0x0040:  0efc fd83 34b3 21eb 5872 e6b7 2766       ....4.!.Xr..'f

Use this packet ? y

Saving chosen packet in replay_src-1115-070915.cap
07:09:16  Data packet found!
07:09:16  Sending fragmented packet
07:09:16  Got a deauthentication packet!
07:09:21  Not enough acks, repeating...
07:09:21  Sending fragmented packet
07:09:21  Got a deauthentication packet!
07:09:26  Not enough acks, repeating...
07:09:26  Sending fragmented packet
07:09:26  Got a deauthentication packet!
07:09:31  Not enough acks, repeating...
07:09:31  Sending fragmented packet
07:09:31  Got a deauthentication packet!
07:09:36  Not enough acks, repeating...
07:09:36  Sending fragmented packet
07:09:36  Got a deauthentication packet!
07:09:41  Not enough acks, repeating...
07:09:41  Sending fragmented packet
07:09:41  Got a deauthentication packet!
07:09:46  Not enough acks, repeating...
07:09:46  Sending fragmented packet
07:09:46  Got a deauthentication packet!
07:09:51  Not enough acks, repeating...
07:09:51  Sending fragmented packet
07:09:51  Got a deauthentication packet!
07:09:56  Not enough acks, repeating...
07:09:56  Sending fragmented packet
07:09:56  Got a deauthentication packet!
07:10:01  Not enough acks, repeating...
07:10:01  Sending fragmented packet
07:10:01  Got a deauthentication packet!
07:10:06  Not enough acks, repeating...
07:10:06  Sending fragmented packet
07:10:06  Got a deauthentication packet!
07:10:11  Not enough acks, repeating...
07:10:11  Sending fragmented packet
07:10:11  Got a deauthentication packet!
07:10:16  No answer, repeating...
07:10:16  Trying a LLC NULL packet
07:10:16  Sending fragmented packet
07:10:16  Got a deauthentication packet!
07:10:21  Not enough acks, repeating...
07:10:21  Trying a LLC NULL packet
07:10:21  Sending fragmented packet
07:10:21  Got a deauthentication packet!
now what am I doing wrong I have did this before on my old system but this on sucks lol any help would be great. thanks and if more info is needed I will be more then happy to give it just not sure what to give at this point.

---

### Post by wildmanne39 on 2012-11-15
Hi, aircrack is not supported on the ubuntu forum, your best bet is the backtrack forum.

---


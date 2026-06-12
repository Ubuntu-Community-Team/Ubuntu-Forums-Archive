---
title: "Wireless works with NO security only ..."
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by tylerKiwi24 on 2005-12-29
Hi, I've seen quite a few posts around here about this problem, however for a newbie, it can get quite confusing when trying to troubleshoot. Could someone please help me get encrypted wireless working to my laptop?

Here's some results from some calls I've seen requested in other posts, however, I'm currently connected wirelessly WITHOUT any security so, I dunno if that makes a difference or not.

Here we go:[B]
iwconfig[/B]
```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NewZealand"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:BA:00:6E
          Bit Rate:24 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
          Rx invalid nwid:2199  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

sit0      no wireless extensions.

```
**iwlist ath0 scan**
```
ath0      Scan completed :
          Cell 01 - Address: 00:0F:66:BA:00:6E
                    ESSID:"NewZealand"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:06:25:9A:A4:3A
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0C:41:43:15:8E
                    ESSID:"khouneh"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/94  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:12:17:2E:7C:9A
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:14:BF:75:A4:09
                    ESSID:"carrow"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000

```

**ifconfig**
```
ath0      Link encap:Ethernet  HWaddr 00:90:96:71:B0:2D
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe71:b02d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1095 errors:19838 dropped:0 overruns:0 frame:19838
          TX packets:993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:693287 (677.0 KiB)  TX bytes:142332 (138.9 KiB)
          Interrupt:22 Memory:e0ba0000-e0bb0000


```

Do you need to see anything else? Help a newbie! :)
Thanks!

---

### Post by Lambert on 2005-12-29
What kind of encryption do you want? wpa or wep?

If wep hexadecimal or ascii key? open or restricted key? (open or restricted is the most important part) does your router offer different keys spots and if so which key # do you use?

---

### Post by tylerKiwi24 on 2005-12-29
Lambert - I've seen you come to the aid of other newbies - yo da man!

I'd prefer to use WPA (my router supports WPA-2 but I don't think my laptop does)
I have a Linksys WRT54G router, so I select WPA-Personal, with a TKIP Alogorithm, Use a shared key phrase.

:) THANK YOU SO MUCH FOR YOUR REPLY!!!

---

### Post by Lambert on 2005-12-29
It's the driver which needs to support wpa and not the laptop. You're using madwifi so there should be no problem.

Follow this guide on the wiki. You do need to download an app from the repositories. If you don't have access while logged on to ubuntu check the install cd. Not sure if it's on there or not. If not post back and you'll get instructions how to download, copy to ubuntu and install the app.

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

There are many good people here, I just try to fit in.

---

### Post by tylerKiwi24 on 2005-12-29
Ok, figured out how to install the WPASUPPLICANT ... and wow, I'm SO new to this, that the rest of this Wiki entry is hard to follow ...

I found the example they were refering to in the wiki - but now what do I do with it?

---

### Post by tylerKiwi24 on 2005-12-29
> You will then have to edit its config file. An example config is available in /usr/share/doc/wpasupplicant. Copy that to the expected location

cp /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz /etc
gunzip /etc/wpa_supplicant.conf.gz
And WHAT is the expected location???

---

### Post by tylerKiwi24 on 2005-12-29
I can't extract the file to /etc coz it says I don't have permission!?! agh ....

---

### Post by Lambert on 2005-12-29
add sudo in front of the commands.

example

```
 sudo cp /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz /etc
```

then enter your password when asked for it.

---

### Post by tylerKiwi24 on 2005-12-29
ok, cool - now, how do I edit the "wpa_supplicant.conf" file?

---

### Post by Lambert on 2005-12-29
```
sudo gedit /etc/wpa_supplicant.conf
```

this opens the file with root permissions so you can edit and save it in the text editor gedit.

---

### Post by tylerKiwi24 on 2005-12-29
Got it - but now I have this error, when I run:
wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi
> 
joel@old-lappy:~$ wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi
Line 452: unknown EAP method 'SIM'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
Line 452: failed to parse eap 'SIM'.
Line 455: failed to parse network block.
Line 498: unknown EAP method 'FAST'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
Line 498: failed to parse eap 'FAST'.
Line 504: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.


Oh wait, do I need to enable the WAP before I run this? I have it turned off so I can use my laptop ....

---

### Post by Rob2687 on 2005-12-29
Try setting fast_reauth=1 to fast_reauth=0 in wpa_supplicant.conf

---

### Post by tylerKiwi24 on 2005-12-29
[QUOTE=Rob2687]Try setting fast_reauth=1 to fast_reauth=0 in wpa_supplicant.conf[/QUOTE]
Nope, didn't work ....

---

### Post by Lambert on 2005-12-29
I don't use wpa so I have not gone through this process yet. Somebody else will need to jump in here. What Rob says could be the answer. But I do notice the line numbers are examples. I'm not sure if these are needed but sections like these you can also consider commenting out by adding # at the begininng of the line so they are not read to see if that solves.

this shows the file with added line numbers.

```
452 network={
    453         ssid="example"
    454         bssid=00:11:22:33:44:55
    455         proto=WPA RSN
    456         key_mgmt=WPA-PSK WPA-EAP
    457         pairwise=CCMP
    458         group=CCMP

``` 

Maybe make this section look like this

```

#network={
#        ssid="example"
#        bssid=00:11:22:33:44:55
#         proto=WPA RSN
#         key_mgmt=WPA-PSK WPA-EAP
#         pairwise=CCMP
#         group=CCMP

``` 
somebody else can correct me if I'm wrong here.

to find the line numbers use this command at terminal, then you can cross that to the file opened in gedit.

```
sudo cat /etc/wpa_supplicant.conf | less -N
```

or maybe in gedit there's a way to display line numbers, not sure:confused:

Having fun yet?

---

### Post by tylerKiwi24 on 2005-12-30
Ok, now this is weird, I commented out the lines - and it STILL gave me the same error. Do I need to refresh the file - or something?

---

### Post by Rob2687 on 2005-12-30
What wireless card are you using?

I think theres two possibilities here. 
Either the Ubuntu wpasupplicant package simply wasn't compiled to support EAP-SIM. 
Or it's a bug in wpasupplicant itself. 
The changelog for the latest development release shows a fixed problem with EAP-SIM and fast reauth. Which is why I suggested what I did above.
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/ChangeLog?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/ChangeLog?rev=HEAD&content-type=text/plain)

---

### Post by tylerKiwi24 on 2005-12-30
Ummm, I'm not sure what card I have ... how can I tell?

---

### Post by Rob2687 on 2005-12-30
Try
lspci | grep Ethernet
and paste the output here

---

### Post by tylerKiwi24 on 2005-12-30
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by tylerKiwi24 on 2005-12-30
Ok, so I managed to comment out the lines that were giving me errors .... and now I get this:
```

joel@old-lappy:~$ wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi

ENGINE: ctrl cmd_string failed: LOAD (null) [error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library]
SSL: Failed to initialize TLS context.
Failed to initialize EAPOL state machines.

```
Can someone help me now?

---

### Post by Lambert on 2005-12-30
Try this. I'm pulling information from the madwifi.org site on wpa.

[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

1. Delete everything in the /etc/wpa_supplicant.conf file except the information you copied in there. So the only thing left should look like this.

```

network={
 ssid="YOURSSID"
 #psk="pVEyuu2U8PNy2VG2s9pS0bPSgsFzyT913NmXFbJ7djLfPn7ivy1NyAfVMJ8EPaI"
 psk=bf546586838b79505928109b8d6d797a2b203c7b2741c66dedae64da39612fbe
```


2. Change the permission of the file.

```
sudo chmod 640 /etc/wpa_supplicant.conf
```

Now finish following the steps of the guide to see where you're at.

if it doesn't work then one last suggestion.

in your /etc/network/interfaces file instead of this.

```

pre-up /etc/init.d/**wpa**supplicant start
pre-up sleep 5
```

 delete those lines and try this line

```

pre-up 
wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
```





pre-up sleep 5

---


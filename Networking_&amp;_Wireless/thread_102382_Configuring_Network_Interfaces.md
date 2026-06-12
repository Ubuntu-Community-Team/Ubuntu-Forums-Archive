---
title: "Configuring Network Interfaces"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by walker45 on 2005-12-11
Hi there.

For the past couple of days, I have been working to get my wireless card setup and working in Ubuntu. After following the steps here [http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+card]("http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+card"), I was able to connect to my wireless router.

The next thing I am now working on is the WPA.  I found the HowTo here [http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa](”http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa”)  however, I was unable to get it to work.

When I get to step 6, to start wpasupplicant, I receive the following errors:

robert@ubuntu:/etc/rcS.d$ sudo invoke-rc.d wpasupplicant start
Starting wpa_supplicant: Line 20: Invalid configuration line 'wpa_passphrase home | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf'.
Line 21: Invalid configuration line 'sudo chmod 600 /etc/wpa_supplicant.conf'.
Failed to read configuration file '/etc/wpa_supplicant.conf'.
invoke-rc.d: initscript wpasupplicant, action "start" failed.

In an attempt to fix the problem myself, I looked at the wpasupplicant readme and changed the the configuration file so that at the end it would say

```
network={
	ssid=”home”
	scan_ssid=1
	key_mgmt=WPA-PSK
	psk=”my passphrase here”
}

```

instead of what was used in the HowTo.  When I went to start wpasupplicant, I received the following:

robert@ubuntu:/etc/rcS.d$ sudo invoke-rc.d wpasupplicant start
Starting wpa_supplicant: done.

The wireless card does get an IP from the router, however, I am unable to browse the web or ping anything on my network.  I have a feeling my problem lies somewhere in the configuration file.

Does anyone have any ideas on what could be wrong?
Thanks in advance.

---

### Post by walker45 on 2005-12-12
--Update--

Still no go on getting WPA to work.  Heres my lastest attempt.

Found the WPAHowTo on the Ubuntu Wiki and attempted to follow that.  However, when I go to test it, I get the following:
```

robert@ubuntu:/etc$ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device



```

At the end, I do not get the prompt back.  It seems like it is waiting for input.

Here is the same command with the debugging switch. When running it this way, it keeps repeating itself, scanning every 5 secs.
```

robert@ubuntu:/etc$ sudo wpa_supplicant -d -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='HOME_W'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:90:96:c3:c8:14
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 239 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:90:4c:7e:00:29 ssid='HOME_W' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 239 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:90:4c:7e:00:29 ssid='HOME_W' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec


```

I'm quite puzzled.  Anyone have any ideas on my lastest attemp?

---

### Post by jafenske on 2005-12-12
I've been looking through your post and noticed the following line:

```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper
```

It needs to have spaces

```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper
```

I don't know it that will solve your problem... Add the spaces and run the command again

---

### Post by walker45 on 2005-12-19
Thanks for your reply, jafenske.

Finals week was last week so I had little to no time to play around with linux.  :smile: 

I tried running the same commands with spaces but still got the same thing.

---


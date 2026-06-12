---
title: "SET failed on device wlan0 ; Operation not permitted."
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by chandujr on 2011-06-25
Using Ubuntu 11.04. A newbie to Linux.

I'm trying to set the sensitivity value of my wlan controller. I believe this is the command:
```
sudo iwconfig wlan0 sens X
```
[X is any percentage value,aint I right??]

But it returns an error:

```
root@chandu-ThinkPad-L410:/# iwconfig wlan0 sens 2
Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device wlan0 ; Operation not permitted.

```

iwconfig returns:

```
root@chandu-ThinkPad-L410:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've been troubleshooting this for a whole day, with no result. Help is inevitable, guys... Please.

---

### Post by gordintoronto on 2011-06-25
In looking at iwconfig's man page, "Modern designs seems to control those thresholds automatically." In other words, your wireless adapter rejected the command. If iwconfig blindly passes on what is in the command, you might try "low," for example. (Found by Googling rtl8191 sensitivity)

---

### Post by chili555 on 2011-06-25
So what is the problem with your wireless card, aside from not being connected??

---

### Post by chandujr on 2011-06-26
> **gordintoronto said:**
> In looking at iwconfig's man page, "Modern designs seems to control those thresholds automatically." In other words, your wireless adapter rejected the command. If iwconfig blindly passes on what is in the command, you might try "low," for example. (Found by Googling rtl8191 sensitivity)

i tried high and low. it retrurns "invalid argument".
```
root@chandu-ThinkPad-L410:/home/chandu# iwconfig wlan0 sens high
Error for wireless request "Set Sensitivity" (8B08) :
    invalid argument "high".
root@chandu-ThinkPad-L410:/home/chandu# iwconfig wlan0 sens low
Error for wireless request "Set Sensitivity" (8B08) :
    invalid argument "low".

```

---

### Post by chandujr on 2011-06-26
> **chili555 said:**
> So what is the problem with your wireless card, aside from not being connected??

No no, it's not the problem of not being connected. I'm getting disconnected from my home wireless network frequently. I read it in some document that there's an attribute called "Sensitivity" which fixes a value for signal below which the controller won't receive. [ somewhat like that,na?? :)]
I have obstructions, I mean walls, in b/w my modem and my lap, so I thought signals might be getting reduced and increasing the sensitivity might do some help to me.
I've read some other topics referring to the issue "wireless connection automatically getting disconnected". I tried some of those without any good at all. Or if you can direct me to any specific topic, it would be much helpful.

Could it be because of any problem with the Ethernet card??

---

### Post by chili555 on 2011-06-26
> Could it be because of any problem with the Ethernet card??I doubt it if it isn't connected to an ethernet cable when you are trying to connect the wireless. Which driver are you using? Is it one you downloaded and compiled?```
lsmod | grep 819
```Not all parameters are available on all cards; please notice:> wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Sensitivity is not listed.

---

### Post by chandujr on 2011-06-26
> **chili555 said:**
> Not all parameters are available on all cards; please notice:Sensitivity is not listed.

oh. so i can't do anything with the sensitivity. Alright, then.

The driver I'm using is:

```
chandu@chandu-ThinkPad-L410:~$ lsmod | grep 819
r8192se_pci           518060  0 

```

---

### Post by chili555 on 2011-06-26
I have googled a bit on this module. Other than one slight issue, it seems pretty solid. Is your network encrypted by WEP? It ought to be WPA2, but if you have older hardware on your network, maybe it's not an option. If so, you might try:```
sudo ifconfig wlan0 down
sudo rmmod -f r8192se_pci
sudo modprobe r8192se_pci hwwep=0
sudo ifconfig wlan0 up
```If it helps, we can write one file to make it persistent.

You might look at the router. Does it have a setting for transmit power? Please see attached. Is connectivity improved with the router set to another channel; 1, 2 or 11 perhaps? Is there any metal between you and the router? For reasons that are too long to explain, my router/modem is in the pantry! When I moved a large can of tomatoes from in front of it, reception improved.

---

### Post by chandujr on 2011-06-27
No, there are no metals in b/w but two cement walls.
And, firstly I tried the above commands. It seemed to have worked, the terminal didn't show any error. But still the problem persisted.
Then I looked router configuration and found something called TxPower. It was initially set to 20%. I changed it to 100%. It's like it worked. Now, I'm having continuous signal reception for about an hour. But I had situations like this before, signals getting okey for a longer period. Tomorrow I'll post again about the result.
Btw, could there be any problem for the modem by setting that 'TxPower' that much high??

---

### Post by chandujr on 2011-06-27
No, there are no metals in b/w but two cement walls.
And, firstly I tried the above commands. It seemed to have worked, the terminal didn't show any error. But still the problem persisted.
Then I looked router configuration and found something called TxPower. It was initially set to 20%. I changed it to 100%. It's like it worked. Now, I'm having continuous signal reception for about an hour. But I had situations like this before, signals getting okey for a longer period. Tomorrow I'll post again about the result.
Btw, could there be any problem for the modem by setting that 'TxPower' that much high??

---

### Post by chili555 on 2011-06-27
> Btw, could there be any problem for the modem by setting that 'TxPower' that much high??Not as long as there is adequate ventilation around it. It does make your network a bit more easily visible to that nosy kid next door. I'd try lowering the power until the computers in the house can connect reliably and no more.

---

### Post by chandujr on 2011-06-27
Okey, but there are only 5 options. 20, 40 , 60, 80, 100. Anyway I'll try that which suits the best. :)

---

### Post by chandujr on 2011-06-28
Master Chili, the problem is still there. I decided to set the TxPower to 100% itself and I'm now sitting in the same room where my modem is placed, but a little while ago, I got disconnected from browsing, twice. I had to restart to post this.
The network icon is showing full range. When I disconnect it and connect it again, it does it with ease, but however I can't surf the net. I tried to ping to a website with terminal, to check if it is any problem with the browser, but it's too not responding.

---

### Post by chili555 on 2011-06-28
> **chandujr said:**
> Master Chili, the problem is still there. I decided to set the TxPower to 100% itself and I'm now sitting in the same room where my modem is placed, but a little while ago, I got disconnected from browsing, twice. I had to restart to post this.
The network icon is showing full range. When I disconnect it and connect it again, it does it with ease, but however I can't surf the net. I tried to ping to a website with terminal, to check if it is any problem with the browser, but it's too not responding.See post #8. Did it help or not? It is a temporary step that goes away on reboot; we'll need to write a conf file if it helps.

---

### Post by chandujr on 2011-06-29
No, it didn't work... :(

---

### Post by chili555 on 2011-06-29
The last thing I can think of is to see if syslog has any clues. Please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```We are looking for the last 25 instances of 'network' or 'Network Manager.'

---

### Post by chandujr on 2011-06-30
I got this:
```
chandu@chandu-ThinkPad-L410:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
[sudo] password for chandu: 
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> dhclient started with pid 1536
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 30 17:16:14 chandu-ThinkPad-L410 NetworkManager[735]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   address 192.168.1.4
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   prefix 24 (255.255.255.0)
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   gateway 192.168.1.1
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   hostname 'chandu-ThinkPad-L410'
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   nameserver '192.168.1.1'
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info>   domain name 'local.lan'
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Scheduling stage 5
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Done scheduling stage 5
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 30 17:16:15 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun 30 17:16:17 chandu-ThinkPad-L410 NetworkManager[735]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Jun 30 17:16:17 chandu-ThinkPad-L410 NetworkManager[735]: <info> Policy set 'Auto BSNL_AP' (wlan0) as default for IPv4 routing and DNS.
Jun 30 17:16:17 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) successful, device activated.
Jun 30 17:16:17 chandu-ThinkPad-L410 NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
chandu@chandu-ThinkPad-L410:~$ 

```

---

### Post by chili555 on 2011-06-30
I don't quite know what to say! It's a text-book perfect connection and the syslog shows no disconnections. I suggest you wait until a disconnect and reconnect and try the command again and see if we can see a reason for the disconnects.

The syslog you've shown me is perfect! I can't fix perfect!

---

### Post by chandujr on 2011-06-30
okey I waited until it is disconnected and it tired to reconnect, but as usual, no results. Then I passed on the above commands and here:
```
chandu@chandu-ThinkPad-L410:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
[sudo] password for chandu: 
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0/wireless): connection 'Auto BSNL_AP' has security, and secrets exist.  No new secrets needed.
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'ssid' value 'BSNL_AP'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'scan_ssid' value '1'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'auth_alg' value 'OPEN'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'wep_key0' value '<omitted>'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: added 'wep_tx_keyidx' value '0'
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> Config: set interface ap_scan to 1
Jun 30 21:59:03 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 30 21:59:05 chandu-ThinkPad-L410 kernel: [  179.921564] Linking with BSNL_AP,channel:9, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Jun 30 21:59:05 chandu-ThinkPad-L410 kernel: [  179.921585] Linking with BSNL_AP,channel:9, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): supplicant connection state:  associating -> associated
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): supplicant connection state:  associated -> completed
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BSNL_AP'.
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> dhclient started with pid 1840
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 30 21:59:05 chandu-ThinkPad-L410 NetworkManager[721]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
chandu@chandu-ThinkPad-L410:~$ 

```

---

### Post by chili555 on 2011-06-30
> supplicant connection state:  inactive -> scanningI just read this: [http://ubuntuforums.org/showthread.php?t=1648237](http://ubuntuforums.org/showthread.php?t=1648237)

While the proposed solution seems rather unlikely, this has been an amazing and enlightening day for old Chili. At this point, I will try anything and believe anything. As always, what we are going to try is immediately reversible. Are you using any bluetooth devices? Please try:```
sudo rfkill block bluetooth
```If it errors out, post:```
rfkill list all
```We'll then fine-tune the command. If the command works without error, tell us if the wireless is working smoother.

---

### Post by chandujr on 2011-07-01
I tried that command and it returned without any error. Bluetooth got disabled. I'll post the result after testing.

---


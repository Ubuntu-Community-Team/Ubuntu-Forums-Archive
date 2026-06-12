---
title: "Intel wifi fails after most recent 13.04 kernel upgrade"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by SeijiSensei on 2013-05-08
My HP laptop with an Intel Centrino Wireless-N card suddenly stopped connecting to my router.  It has performed flawlessly until now in prior versions of Ubuntu, and in 13.04 with earlier versions of the 3.8.0-19 kernel before the update a couple of days ago.  The connection uses 802.11g and WPA2.

I plugged in a USB wireless adapter with an Atheros chip and connected right away using the credentials already existing on the system.

Here's the log from a failed connection attempt:

```

ay  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) starting connection '[SSID deleted]'
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0/wireless): access point '[SSID deleted]' has security, but secrets are required.
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0/wireless): connection '[SSID deleted]' has security, and secrets exist.  No new secrets needed.
May  8 07:32:35 vid NetworkManager[1173]: <info> Config: added 'ssid' value '[SSID deleted]'
May  8 07:32:35 vid NetworkManager[1173]: <info> Config: added 'scan_ssid' value '1'
May  8 07:32:35 vid NetworkManager[1173]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  8 07:32:35 vid NetworkManager[1173]: <info> Config: added 'psk' value '<omitted>'
May  8 07:32:35 vid NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 07:32:35 vid NetworkManager[1173]: <info> Config: set interface ap_scan to 1
May  8 07:32:35 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: inactive -> scanning
May  8 07:32:41 vid wpa_supplicant[1357]: wlan0: SME: Trying to authenticate with bc:ae:c5:a7:3e:f4 (SSID='[SSID deleted]' freq=2432 MHz)
May  8 07:32:41 vid kernel: [212813.029523] wlan0: authenticate with bc:ae:c5:a7:3e:f4
May  8 07:32:41 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 07:32:41 vid kernel: [212813.039612] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 1/3)
May  8 07:32:41 vid kernel: [212813.241596] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 2/3)
May  8 07:32:41 vid kernel: [212813.445488] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 3/3)
May  8 07:32:42 vid kernel: [212813.649392] wlan0: authentication with bc:ae:c5:a7:3e:f4 timed out
May  8 07:32:42 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 07:32:44 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 07:32:44 vid kernel: [212815.656417] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
May  8 07:32:44 vid wpa_supplicant[1357]: wlan0: SME: Trying to authenticate with bc:ae:c5:a7:3e:f4 (SSID='[SSID deleted]' freq=2432 MHz)
May  8 07:32:44 vid kernel: [212816.283173] wlan0: authenticate with bc:ae:c5:a7:3e:f4
May  8 07:32:44 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 07:32:44 vid kernel: [212816.293341] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 1/3)
May  8 07:32:44 vid kernel: [212816.495890] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 2/3)
May  8 07:32:45 vid kernel: [212816.699768] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 3/3)
May  8 07:32:45 vid kernel: [212816.903744] wlan0: authentication with bc:ae:c5:a7:3e:f4 timed out
May  8 07:32:45 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 07:32:47 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 07:32:47 vid kernel: [212818.910747] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
May  8 07:32:48 vid wpa_supplicant[1357]: wlan0: SME: Trying to authenticate with bc:ae:c5:a7:3e:f4 (SSID='[SSID deleted]' freq=2432 MHz)
May  8 07:32:48 vid kernel: [212819.580006] wlan0: authenticate with bc:ae:c5:a7:3e:f4
May  8 07:32:48 vid kernel: [212819.590057] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 1/3)
May  8 07:32:48 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 07:32:48 vid kernel: [212819.790230] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 2/3)
May  8 07:32:48 vid kernel: [212819.994128] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 3/3)
May  8 07:32:48 vid kernel: [212820.198020] wlan0: authentication with bc:ae:c5:a7:3e:f4 timed out
May  8 07:32:48 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 07:32:50 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 07:32:50 vid kernel: [212822.205059] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
May  8 07:32:51 vid wpa_supplicant[1357]: wlan0: SME: Trying to authenticate with bc:ae:c5:a7:3e:f4 (SSID='[SSID deleted]' freq=2432 MHz)
May  8 07:32:51 vid kernel: [212822.839560] wlan0: authenticate with bc:ae:c5:a7:3e:f4
May  8 07:32:51 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 07:32:51 vid kernel: [212822.849670] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 1/3)
May  8 07:32:51 vid kernel: [212823.052559] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 2/3)
May  8 07:32:51 vid kernel: [212823.256480] wlan0: direct probe to bc:ae:c5:a7:3e:f4 (try 3/3)
May  8 07:32:51 vid kernel: [212823.460308] wlan0: authentication with bc:ae:c5:a7:3e:f4 timed out
May  8 07:32:51 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 07:32:53 vid NetworkManager[1173]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```

As a guess, the problem seems to happen during authentication.  Perhaps a firmware issue?

---

### Post by chili555 on 2013-05-08
Here is my guess:> iwlwifi 0000:0d:00.0: fail to flush all tx fifo queuesI notice the timestamp is pretty long. Is this after a suspend? [https://wiki.archlinux.org/index.php/ThinkPad_X230#Suspension](https://wiki.archlinux.org/index.php/ThinkPad_X230#Suspension)

Does it help if you do:```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Does it perform as expected if you reboot?

Is the behavior improved with:```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

I am very interested because I am running the same kernel and iwlwifi driver with no trouble, even after suspend and even with N speeds.

---

### Post by SeijiSensei on 2013-05-08
I already tried the last of those, disabling 802.11n, after reading a posting, probably one of yours!  It did not help.  I'll give the other possibilities a try.  Rebooting is a bit dicey with this machine.  I've had to futz more with 13.04 than previous versions to get audio to work and install the proper proprietary ATI driver.  The whole installation feels more fragile than 12.04, but I do get MTP support for my Galaxy S3.

I never suspend this computer.  It's on AC power and connects to my TV.  

The error with the TX FIFO queues caught my eye as well.

---

### Post by SeijiSensei on 2013-05-16
This problem appears to be fixed in the 3.8.0-21 kernel that was released today.

---


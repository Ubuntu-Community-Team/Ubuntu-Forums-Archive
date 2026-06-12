---
title: "WRT54G Tomato and 11.04"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by tweezak on 2012-10-15
In an effort to get my phone to hold onto a connection with my router I decided to try the Tomato firmware which allows you to increase the signal strength. While that didn't have a huge impact I have just discovered that my laptop (HP Mini311 - broadcom wifi) refuses to connect.

I'm seeing the router just fine with lots of signal and the security prompt comes up asking for the key but then that just loops after a few minutes. I have tried disabling the security altogether but then I get no prompt at all and it never connects.

I have searched the web and found nothing like this except a mention that DD-WRT firmware sends additional information that the network handler in Ubuntu doesn't know what to do with. ( [http://www.aeonity.com/frost/dd-wrt-linux-wireless-issues-possible-fix](http://www.aeonity.com/frost/dd-wrt-linux-wireless-issues-possible-fix) ).

Oh...I forgot to mention that my and my wife's phones connect fine as does my Xbox360.

Anyone have a suggestion...if I can't resolve this then I'll be going back to the factory firmware I guess.

Ubuntu 11.04 (Natty)
HP Mini311 with Broadcom wifi
WRT54G v.2 router with Tomato 1.28.1816

---

### Post by ahallubuntu on 2012-10-15
Have you tried DD-WRT itself instead of Tomato?  I use (and like) both.

---

### Post by tweezak on 2012-10-15
I haven't tried DD-WRT or any other open firmwares. I was going to throw the question out there and see if anyone had experienced something similar and found it was a setting or something similar.

But...now I notice that there's another thread about 11.04 with WRT54G in the last hour that sounds eerily similar to my situation (but he didn't change firmware). I wonder if an 11.04 update came down the pike that broke wifi...

---

### Post by ahallubuntu on 2012-10-15
I've got 11.04 on several different computers with all the updates installed, and they all connect with WiFi.  One of them is connected to a WRT54G V4 router with DD-WRT.  No problems at all.  So, no, I don't think any 11.04 update "broke WiFi."  Broke the driver for your particular wireless card?  Perhaps.

DD-WRT is pretty easy to put on, as easy as Tomato was.  I'd try that first and hope that fixes it.

You could also look at the dmesg output in a terminal Window in Ubuntu as you are trying to connect and see if anything stands out.

---

### Post by houstonbofh on 2012-10-15
First, Ubuntu will work with a Tomato flashed router.  Now encryption may be another matter...  You might want to try and update, as pure tomato is kinda old...  I have had good luck the the Toastman Tomato updates.

---

### Post by tweezak on 2012-10-15
I'm still learning so please be patient.

Here's the part of the dmesg output that I think is pertinent to the wireless:

```

[   28.480034] eth0: no IPv6 routers present
[   29.027752] Intel AES-NI instructions are not detected.
[   29.051646] padlock_aes: VIA PadLock not detected.
[   29.124291] padlock_sha: VIA PadLock Hash Engine not detected.
[   29.430073] Adding 2880508k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2880508k 
[   31.132572] usb 2-1.4.4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   35.086240] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[  351.605575] forcedeth 0000:00:0a.0: eth0: link down
[  470.392173] forcedeth 0000:00:0a.0: eth0: link up
[  513.961063] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[  514.160152] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[  514.360150] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[  514.560161] wlan0: authentication with 00:12:17:09:00:71 timed out
[  526.716654] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[  526.916105] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[  527.116118] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[  527.316071] wlan0: authentication with 00:12:17:09:00:71 timed out
[  539.491041] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[  539.688182] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[  539.888091] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[  540.088125] wlan0: authentication with 00:12:17:09:00:71 timed out
[  552.243972] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[  552.444093] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[  552.644103] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[  552.844124] wlan0: authentication with 00:12:17:09:00:71 timed out
[  565.016626] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[  565.216102] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[  565.416101] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[  565.430013] wlan0: authenticated
[  565.430132] wlan0: associate with 00:12:17:09:00:71 (try 1)
[  565.628108] wlan0: associate with 00:12:17:09:00:71 (try 2)
[  565.828094] wlan0: associate with 00:12:17:09:00:71 (try 3)
[  566.028118] wlan0: association with 00:12:17:09:00:71 timed out
[ 1216.314864] wl0: MAC Detected a change on the RF Disable Input 0x10000
[ 1216.314985] usb 3-4: USB disconnect, address 2
[ 1216.315912] btusb_bulk_complete: hci0 urb f0854a80 failed to resubmit (19)
[ 1216.315931] btusb_intr_complete: hci0 urb f0854500 failed to resubmit (19)
[ 1216.316929] btusb_bulk_complete: hci0 urb f0854700 failed to resubmit (19)
[ 1216.319276] btusb_send_frame: hci0 urb f1161880 submission failed
[ 1249.199149] forcedeth 0000:00:0a.0: eth0: link down
[ 1268.332899] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1268.956126] usb 3-4: new full speed USB device using ohci_hcd and address 3
[ 1279.746824] wlan0: authenticate with 00:12:17:09:00:71 (try 1)
[ 1279.944084] wlan0: authenticate with 00:12:17:09:00:71 (try 2)
[ 1280.144115] wlan0: authenticate with 00:12:17:09:00:71 (try 3)
[ 1280.344131] wlan0: authentication with 00:12:17:09:00:71 timed out

```

---

### Post by ahallubuntu on 2012-10-15
I assume you have set the WPA2 security to be TKIP+AES?

You could also try setting security to WPA2 + WPA (or however Tomato specifies it) so it will try WPA2 first then drop down to WPA if that fails - a little less secure than WPA2 but certainly not as weak as WEP.

How about the channel width (for 2.4GHZ 802.11n)?  Is it set to 20MHZ not 40MHZ?  Sometimes 40MHZ is chosen and will work best but sometimes 20MHZ is a good default to work with all devices.

---

### Post by tweezak on 2012-10-15
> **ahallubuntu said:**
> I assume you have set the WPA2 security to be TKIP+AES?

You could also try setting security to WPA2 + WPA (or however Tomato specifies it) so it will try WPA2 first then drop down to WPA if that fails - a little less secure than WPA2 but certainly not as weak as WEP.

How about the channel width (for 2.4GHZ 802.11n)?  Is it set to 20MHZ not 40MHZ?  Sometimes 40MHZ is chosen and will work best but sometimes 20MHZ is a good default to work with all devices.

I started with WPA/WPA2 and TKIP+AES. I then knocked that back to WPA and TKIP+AES then WPA and TKIP (what my old setting was with the factory firmware). Then I went all-in and disabled all security just to be sure that wasn't the problem. It wasn't...still couldn't connect even though I could see my network in the list.

As far as channel width...:confused:...I'm not sure what that is. I am running B/G mixed so based on what you wrote it may not apply...?

Thanks to you and everyone else for the suggestions.

---

### Post by ahallubuntu on 2012-10-15
Oops - yeah, never mind, WRT54G doesn't have the ability to change channel width - N only...

---


---
title: "Wireless Network Problems on 10.10"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by d521yts on 2010-11-29
I installed Ubuntu 10.10 yesterday (first time) and I've been trying to connect to the internet via wireless.

The net worked for a little bit, it allowed me to install the updates, but upon restart, I had no internet.

If you need anymore information let me know and I will provide that for you.

I'm running Ubuntu on a dual-boot (vista)

---

### Post by uncaspi on 2010-11-30
Are you using a wireless stick card please post sudo lsusb
if not please post sudo lspci -nn
You must open a terminal to issue this commands.

---

### Post by d521yts on 2010-11-30
Here is what i got when i typed sudo lsusb in the terminal 
(yes i'm using a usb wireless card)

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by d521yts on 2010-11-30
Bump!

Anything else i can do?

---

### Post by d521yts on 2010-11-30
Ok, now Ubuntu doesn't detect a network :/
it detects the card "lsusb" but no network
what can i do?

---

### Post by chili555 on 2010-11-30
Please try:```
sudo modprobe rt73usb
iwconfig
sudo iwlist wlan0 scan
```Let us know the outcome and we'll proceed.

---

### Post by d521yts on 2010-11-30
sudo modprobe rt73usb i got no results, it just went to a new line

iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.


sudo iwlist wlan0 scan


wlan0     Scan completed :
          Cell 01 - Address: 00:1C: DF:76:5B:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key: off
                    ESSID:"Belkin_N_Wireless_765BE3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001399167c5b
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 001842656C6B696E5F4E5F576972656C6573735F373635424533
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA50050F204104A00011010440001011041000100103B0001031047001000000000000000011000001CDF765BE31021001242656C6B696E20436F72706F726174696F6E102300114E20576972656C65737320526F7574657210240007332E30312E31301042000E31323734393832333330373038351054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000

---

### Post by chili555 on 2010-11-30
So, it seems your wireless is working again. If so, we merely need to get rt73usb to load on boot:```
sudo su
echo rt73usb >> /etc/modules
exit
```

---

### Post by d521yts on 2010-11-30
> **chili555 said:**
> So, it seems your wireless is working again. If so, we merely need to get rt73usb to load on boot:```
sudo su
echo rt73usb >> /etc/modules
exit
```

yeah, it was out, but when i was getting that info, it started working again.. what do i do with the code? (i'm a noob)

---

### Post by chili555 on 2010-11-30
Open a terminal and type one line at a time and press Enter following each line.

Have fun!.

---

### Post by d521yts on 2010-11-30
ok, i did that, but nothing happened O_o (it did something when i typed "sudo su" but nothing else happened)

and i did the scan thing again, and the wireless is out >_<

sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by chili555 on 2010-11-30
> ok, i did that, but nothing happened O_o (it did something when i typed "sudo su" but nothing else happened)That's expected. It means command accepted, no errors.

Please run and post:```
dmesg | grep -e rt7 -e wlan
```Thanks.

---

### Post by d521yts on 2010-11-30
oh ok my bad lol


dmesg | grep -e rt7 -e wlan

[   13.476620] Registered led device: rt73usb-phy0::radio
[   13.476639] Registered led device: rt73usb-phy0::assoc
[   13.476656] Registered led device: rt73usb-phy0::quality
[   13.477278] usbcore: registered new interface driver rt73usb
[   15.155364] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.724927] wlan0: authenticate with 00:1c:df:76:5b:e3 (try 1)
[   17.726702] wlan0: authenticated
[   17.728673] wlan0: associate with 00:1c:df:76:5b:e3 (try 1)
[   17.731323] wlan0: RX AssocResp from 00:1c:df:76:5b:e3 (capab=0x1 status=0 aid=1)
[   17.731328] wlan0: associated
[   17.745407] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.712012] wlan0: no IPv6 routers present
[   38.176391] wlan0: deauthenticating from 00:1c:df:76:5b:e3 by local choice (reason=3)

---

### Post by chili555 on 2010-11-30
I notice this:> wlan0 Scan completed :
Cell 01 - Address: 00:1C: DF:76:5B:E3
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=[COLOR="Red"]38/70[/COLOR] Signal level=-72 dBm Are you a long distance from the router? I also see:> wlan0: [COLOR="Red"]deauthenticating[/COLOR] from 00:1c:df:76:5b:e3 [COLOR="Red"]by local choice (reason=3)[/COLOR] This seems to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992)

If you read on down, some say it is fixed by removing Network Manager and replacing it with Wicd. Before I recommend a course of action, I'd like to know more about your setup. How far are you from the router? Do you use encryption? Could you switch the router to channel 11 or 1? Is yours a N-speed router?

---

### Post by d521yts on 2010-11-30
yes i am quite far from the router (other side of the house DX )

i don't know how to encrypt so idk if it is or not
it isn't an N speed router.

---

### Post by d521yts on 2010-12-01
Bump!

Anything else i can try to connect?

---

### Post by dangerjunkie2002 on 2010-12-01
Hi,

I've not been impressed with Belkin since the time I called them when an access point at work was giving trouble. They asked me what OS I was running and when I said Linux I was told "We don't support Linux. Call to Linux company. They will help you" despite the problem I was having being nothing to do with the OS. I certainly won't be buying their stuff again.

During one of the periods when it is working, if you right click on the network icon (the radio wave) at the top of the screen then left-click "Connection Information" does it say anything in the "Security" line? The first time you connected to the Wireless (on Linux or Windows) did either ask for a password?

Can you temporarily move your machine near the access point so you've got a nice strong signal and see if the problem fixes itself?

Cheers,
Paul.

---

### Post by d521yts on 2010-12-01
> **dangerjunkie2002 said:**
> Hi,

I've not been impressed with Belkin since the time I called them when an access point at work was giving trouble. They asked me what OS I was running and when I said Linux I was told "We don't support Linux. Call to Linux company. They will help you" despite the problem I was having being nothing to do with the OS. I certainly won't be buying their stuff again.

During one of the periods when it is working, if you right click on the network icon (the radio wave) at the top of the screen then left-click "Connection Information" does it say anything in the "Security" line? The first time you connected to the Wireless (on Linux or Windows) did either ask for a password?

Can you temporarily move your machine near the access point so you've got a nice strong signal and see if the problem fixes itself?

Cheers,
Paul.

I'll try the "Security" line thing whenever it randomly wants to connect, it never asked me for a password the first time i connected.

I can't move my computer closer to the router :(

---

### Post by d521yts on 2010-12-01
By creating a new network i can connect, but can't access the internet.
I tried many times to connect with the option it gives me, but it wouldn't connect.

---

### Post by d521yts on 2010-12-01
I tried changing the Router Channel
1 - Little to No Signal
6 - Ok signal, not the best though
11 - Same as 6


idk if that helps any

---

### Post by d521yts on 2010-12-01
A little update.
I decided to uninstall Ubuntu 10.10 and try 10.04
I'm using the Live CD version now ( XD) and it connected to the net flawlessly.
I still don't know why 10.10 wouldn't connect, but meh.

---

### Post by d521yts on 2010-12-01
Well, the internet is working fine for me on 10.04
Still don't know why it didn't work on 10.10

---

### Post by chili555 on 2010-12-01
There are probably newer versions of the driver, Network Manager and wpa_supplicant. Which of these is the culprit is difficult to determine. My guess is that you are running and happy, so there's no reason to do anything more. When the next version of Ubuntu comes out, 11.04, I recommend you run the live CD. If your wireless works well, I think you can confidently upgrade. If not, stay put.

---

### Post by TBABill on 2010-12-01
And +1 for staying put. 10.10 seems to have the most widespread wireless issues I have seen, especially since it has been released for some time now. I have seen so many issues from Intel, Ralink and Broadcom wireless device owners, myself included for both the Ralink and Broadcom issues, that 10.10 is just going to be a "skip this one" release for me now. I can get them working, but they still do not impress due to delays coming back from suspend and others. If you are running well in 10.04 you should be set. It's a great release.

---

### Post by d521yts on 2010-12-01
Ok. Thanks for the help.

---


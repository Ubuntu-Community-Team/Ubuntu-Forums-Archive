---
title: "Acer 3613WLMi Wlan Install"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by iwarp62 on 2006-05-29
Hey,

I'm a windows guy and I figured its time to give linux a try. I fooled around with your live cds and I love dapper. I've installed the latest version on my laptop today and am trying to set everything up but I need a hand with the wireless stuff.

My notebook is the Acer 3613WLMi which as near as I can tell uses a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

I followed some blogs I found on the internet to install the driver.

I downloaded the driver off of the acer.ca website, installed the ndiswrapper package and then ran the command:

sudo ndiswrapper -i bcmwl5a.inf

Which returns:

Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

To confirm a success I run:

sudo ndiswrapper -l

Which returns: 

Installed ndis drivers:
bcmwl5a         driver present, hardware present

Kewl. Next I run (cause the blog tells me to):

sudo modprobe ndiswrapper

Which returns nothing. (no news is good news?? I dunno, I hope so). I'm then instructed to run:

sudo dmesg | tail -n 6

Because I am supposed to "have a look if the kernel sees the wlan nic." And wouldn't ya know it:

[4296590.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4296713.734000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4296836.570000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4296959.406000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4297082.249000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4297205.085000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
](*,) 
So, being a newb'n all with probably 3 or less hours of experience I would sure appreciate some help. I did install the network manager applet. I am unable to see networks that are present and the button for my wireless card on the front of my notebook doesn't blink and has no affect when it is pushed. Thanks in advanced to anyone who offers there expertise.

---

### Post by iwarp62 on 2006-05-30
Bump

---

### Post by tonic on 2006-05-30
I am looking into this now with my SO's laptop. What OS arch are you using? 32-bit or 64-bit?

cheers,

tonic

---

### Post by lakedrake on 2006-05-30
I have an Acer 3023WLMi with the same chipset, and I had to install **acer_acpi** before I could get my wireless to work (I've got the same Broadcom chipset, also using nsdiswrapper). In Dapper itself, I also had to blacklist the bcm43xx driver.

To blacklist the bcm43xx driver, just add the line "blacklist bcm43xx" to /etc/modprobe.d/blacklist .

Installing acer_acpi is a bit harder, since it requires compiling the module, but there are plenty of good tutorials, including [this one](https://wiki.ubuntu.com/WifiDocs/Acer5021WLMi_Amd64) from the wiki. All steps described in there should be the same for your laptop.

**Edit:** The tutorial in the wiki seems to be overcomplicated in terms of getting the right packages, just open a console, and run the following command:

sudo apt-get install make gcc g++-3.4 linux-headers-$(uname -r)

and continue the tutorial in the wiki from 1.5 onwards.

---

### Post by tonic on 2006-05-30
Thats awesome,

I just found myself some 64-bit drivers so thingsare working, well almost. I can't seem to be able to get a link with to an access point at the moment. Pain....

---

### Post by iwarp62 on 2006-05-30
Hey Guys thanks for all yer help.

My laptop is 32-bit.

I followed those steps on the wiki. I got past the dmesg errors which I guess is a good sign eh:). Now though when I do this command (1.5 of the wiki):

iwlist wlan0 scan

I get:

wlan0     Interface doesn't support scanning.

Lol me being a nerd and all I decided to dig deeper. The tutorial I followed before posting here got me to try the command:

iwconfig

Which oddly enough returns:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Lol My wireless card is installed as eth1!?!?! How did that happen?? iwlist eth1 scan reveals:

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:C7:EC:0E
                    ESSID:"Private"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-32 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000

It's Alive! Thats my wireless network I'm trying to connect to. This would have been a eureka moment accept that the networking applet that is supposed to make this easy doesn't detect my wireless card (prolly cause its eth1)](*,) . Can I switch it to wlan0?? Also I still don't know how to connect to the network without that networing applet. Thanks again!

---

### Post by lakedrake on 2006-05-31
I should have mentioned the problems with NetworkManager :). It seems NetworkManager isn't playing nicely with ndiswrapper. During the beta, NetworkManager worked partly for me (I couldn't connect to unencrypted networks), but ever since RC, it's completely broken.

Probably it has something to do with this bug: [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/46136](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/46136)

btw: there are some alternatives to NetworkManager, like gtk-wifi, which is simply a GUI for the iwconfig/iwlist/ifconfig commands.

---

### Post by tonic on 2006-05-31
what do you mean by networking applet do you mean nm-applet?

you may need to comment out your interfaces in /etc/network/interfaces
     sudo nano -w /etc/network/interfaces
just throw a # in front of eth0 and eth1
then restart dbus (just to be sure)
     sudo /etc/init.d/dbus restart
then start nm-applet

I find it is helpful to start nm-applet from the run dialog. Use alt+f2 to access that dialog :). For some reason the Ubuntu folks have hidden the menu option, ahwell.

NetworkManager is pretty sweet :) so is nm-applet actually, it looks nice and is functional.

---

### Post by iwarp62 on 2006-06-02
Alright thanks guys for all your help. It works now. YAY! I just have one last kink to work out. Its probably more a kink in my brain.

How do I get WPA working?? My router uses WPA+TKIP. The only program in the list I found was Wifi radar. It does a very nice job but in the profile setup it is asking me for a wpa driver. (I have no clue). Should I stick with wifi radar? and if so how do I get WPA working? and if not, what do I use and how do I get WPA workin with that?? thanks again!

---

### Post by bomanizer on 2006-06-27
This works also on a Acer Aspire 3610. Thanks for the tips! Now it's finally bye-bye for Win... :rolleyes:

---


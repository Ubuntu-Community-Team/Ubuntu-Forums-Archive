---
title: "Intel 3945 + WPA2 solution for Dapper Drake - It's EASY"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by voidPtr on 2006-06-12
It seems several people are having issues configuring their Intel 3945 wireless cards to support WPA2, claiming Dapper Drake "only supports" WEP.  This is not true, the solution simply isn't obvious.

The primary cause of confusion is due to GNOME's "Network-Admin" tool currently not supporting WPA for the Intel 3945.  This is not Dapper Drake's fault!

There is NO REASON to switch to SuSE just to get WPA working, Dapper Drake will happily accomodate you. :-)

The final release of Dapper Drake already has built in support for both the Intel 3945 as well as WPA support via wpa_supplicant.  You need not install anything extra (or do any nasty compiling from sources).  The only thing missing at this point is a nifty GUI setup.

So, how do you set it up?  Simple!  For example, I have a WRT54GS router configured to use WPA2 TKIP+AES encryption.  The encryption passphrase is available in the "Wireless Security" configuration screen on this router (yours will be similar).  

Next, you must use the utility wpa_passphrase (already installed and available on the CLI) to encode the passphrase (as wpa_supplicant requires this):

wpa_passphrase SSID (enter)
#reading passphrase from STDIN

Replace SSID with the proper SSID name.  At the flashing cursor, enter the passphrase accquired from the router configuration screen.  

What we need from the output of this program is the encrypted PSK line.

Now, simply update /etc/network/interfaces filling in the blanks as necessary (replace SSID and OUTPUT_FROM_WPA_PASSPHRASE):

iface eth2 inet dhcp
  wpa-conf managed
  wpa-ssid SSID
  wpa-key-mgmt WPA-PSK
  wpa-psk OUTPUT_FROM_WPA_PASSPHRASE

After this, reboot or restart networking to have WPA/WPA2 enabled encryption on your Intel 3945 ABG wireless card! :-)

On a sidenote, if you chose to use linux-image-2.6.15-23-686 (in my case, to enable Dual Core on my E1505), you will also need to install linux-restricted-modules-2.6.15-23-686, otherwise you're wireless device will suddenly disappear (I've seen this issue reported repeatedly as well).  Also, for E1505 owners using the integrated Intel GMA950 video, simply apt-get 915resolution to enable WSXGA+ (1680x1050) resolution.

I hope this helps anyone who's looking for a solution.  I had to waste a few hours tinkering to figure it out, so hopefully it will save other people time!

Edit: This was the first solution I discovered.  An alternate method is to install the Network-Manager applet (not to be confused with the default Gnome Network Manager tool).  Edit /etc/network/interfaces and comment out everything but the lines related to lo, reboot, then use Network-Manager to configure your WPA/WPA2 encrypted network.  However, this method requires the use of a keyring password which can get pretty annoying (though there are ways around this as well).  Additionally, wireless setup must be performed for each user (whereas method 1 will work regardless who is logging in).

-voidPtr

---

### Post by Krzysztof on 2006-06-14
That's right. I got ipw3945 workin on Dapper beta with older kernels and manually compiled modules for ipw3945 (according to Intel's manual), ieee and wpa_supplicant. It is working well also in current release. 
However, I had a problem when changing kernel images from 2.6.15-22 to 2.6.15-23 i did included restricted modules but wireless card dissapeared anyway. I had to repeat module compilation. Maybe it is because I did it with the previous kernel. I read some manual for such cases but it didn't work.

The whole system (Asus A6J DualCore+ATI X1600) works perfectly. 
I would like to report that but don't know where and how ;-)

---

### Post by stackcheese on 2006-06-14
I've got WPA work my Intel 3945 (E1405) however every time I want to switch between my home (WPA) and my schools (login system? it does not require a WEP or WPA password to connect to it but i guess it blocks certain ports unless you provide your student ID and Password) I have to reconfigure my /etc/network/interfaces file. I dont know how to configure NetworkManger enable it to detect my school's wireless network.

Anyone know of a better way to switch between home/school alot more seemlesly then switching between NetworkManger and Network-Admin?

Any help would be much appreciated.

---

### Post by Krzysztof on 2006-06-15
stackcheese: are you saying that you got ipw3945 working with NetworkManager? That's impossible for me. 

I have the same problem when changing networks: between my wireless at home and wireless at universities, I have to manually change configuration from WPA2 to no encription, etc.

---

### Post by xinel on 2006-06-15
You are a legend voidPtr

---

### Post by e00878 on 2006-06-15
The whole system (Asus A6J DualCore+ATI X1600) works perfectly. 
I would like to report that but don't know where and how ;-)[/QUOTE]


please report at:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by xinel on 2006-06-17
OMG it keeps comming up and going down

/me pulls hair out and screams.

Its not even comming up anymore

---

### Post by samir85 on 2006-06-17
On my Sony Vaio VGN-FE11H laptop, I manually upgraded the ipw3945 driver to version 1.0.5. WLan works like a charm with network-manager since then.

---

### Post by pinkFloyd031 on 2006-06-18
I in another side with have no luck, cann't setup my Intel2200 + WPA. Below is information of mine
   - Ubuntu 6.06 Desktop
   - Intel 2200. (come with Acer Aspire 5502ZNWXMi)
   - Need to use WPA on my router SMC7904WBRA with WPA-PSK.
   - Following voidPtr's instruction.
      --- iface eth1 inet dhcp
      --- wpa-conf managed
      --- wpa-ssid SSID
      --- wpa-key-mgmt WPA-PSK
      --- wpa-psk OUTPUT_FROM_MY_WPA_PASSPHRASE.
   - modprobe then ifdown and ifup.
   - Seem working properly since I observed 'Network Monitor 2.12.0' displayed full greenly signal strength.
   - Also observed that on Support Tab of Connection properties (of eth1: wireless, of course) displayed correct ip address come from DHCP (I already cross checked in SMC7904WBRA).
   - Try to ping to SMC7904WBRA => ... unreached (fail) ...
   - Try to ping itself (eth1) => OK.
   - Try to pin another LAN (eth0) => OK.

What problems I encoutered?? Someone could you please help me.
Many thanks in advance.

pinkFloyd031

---

### Post by wieman01 on 2006-06-25
Hi, 

Well... I am not sure if you are really using WPA2... I am guessing that your PC is connecting to the router via WPA / TKIP which is an outdated & WEP-based protocol. WPA2 is "downward compatible" so it will offer a handshake even if clients try to connect using TKIP (=WPA1) unless you tell your router to accept "AES" encryption only.

Try to configure your router in such a way that it only accepts WPA2 / AES. If your computer connects, then apparently "wpa-conf managed" does the job, no problem. If not, you can try this: 

[http://ubuntuforums.org/showthread.php?p=1176169#post1176169]("http://ubuntuforums.org/showthread.php?p=1176169#post1176169")

I am using WPA2 as well, but I have TKIP, etc. disabled which is NOT secure. Hope this helps.

He

---

### Post by jka/v on 2006-06-29
Thanks SOOO much for putting this up, worked perfectly, and I'm finally wireless with my new dv8000t in ubuntu.

btw, tried suse10.1, and kubuntu, and so far, this is only worked here for me in ubuntu :)

---

### Post by set300b on 2006-06-30
I have some success. The only problem is that the signal drops out if I am more than four feet from the wireless access point.

Here is what I have:
Dell Latitude C640 with Intel 2200BG
Linksys WRT54G version 3 wireless router (I've tried it with DD-WRT v23 and Linksys v4.30.5 firmwares)

Any help is appreciated!

set300b

---

### Post by wieman01 on 2006-07-01
Hi, 

Could be the power management, dude. Could you turn it off on your laptop and see if it gets any better?

He

---


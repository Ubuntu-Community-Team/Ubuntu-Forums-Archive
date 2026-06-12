---
title: "cannot connect to WPA(2) personal network"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by NooBcubE on 2009-05-08
i have been searching forums for the past 4 days trying to fix this problem!! i have tried wicd to no avail and i have also tried altering my wpa_supplicant file but nothing has worked i am running linux mint 6 and am not very familiar with linux, i am currently in school for IT so i figured i should make the jump now plz help!

---

### Post by HydroTech on 2009-05-08
So you're trying to connect your ubuntu computer to a WPA(2) encripted network? Do you see a network connection at all?

---

### Post by NooBcubE on 2009-05-09
yeah i can see the network and i can connect to it if its unsecured but when it comes to trying to connect to it when its encrypted i cannot, i know im entering the right password, it will try and then keep asking me to authenticate. this is so freakin frustrating.

---

### Post by HydroTech on 2009-05-09
make sure you're typing the password; not the password 'seed'. like so:
seed: binary
actual password: 23 BF F5 67 C4...
I did that for a while on my IPTV and it took me a while to figure out that I got them mixed up. :( So make sure you type the hexidecimal password.

---

### Post by NooBcubE on 2009-05-09
hex password? my router is set up for a passphrase, although when the authentication prompt comes up when i try to connect it gives me 4d326a0f002d37005f5272ee4b219820b525a3309d67ffe69b61cc69afb32bd3 already filled into the password slot? is this the hex pwd you were talking about? cause even when i try to connect with that already filled in it doesnt work

also i am using and atheros 5k series nic and madwifi as the driver i dont know if this will help but figured itd help to know

---

### Post by safetycritical on 2009-05-09
I'm having the same issues with a WPA2 wireless network. This was helpful - but ... didn't solve my problem. It may for you .. :confused:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by NooBcubE on 2009-05-09
i tried but to luck, thanks for trying to help though! everytime i tried to run the 
sudo wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w -dd coomand i got this 

sudo wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w -dd
wpa_supplicant: invalid option -- 'w'
wpa_supplicant v0.6.4
Copyright (c) 2003-2008, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit ([http://www.openssl.org/](http://www.openssl.org/))

usage:
  wpa_supplicant [-BddhKLqqtuvW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-b<br_ifname>] [-f<debug file>] \
        [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] \
        [-p<driver_param>] [-b<br_ifname>] ...]

drivers:
  wext = Linux wireless extensions (generic)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver
options:
  -b = optional bridge interface name
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name
  -f = log output to debug file instead of stdout
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -u = enable DBus control interface
  -v = show version
  -W = wait for a control interface monitor before starting
  -N = start describing new interface
example:
  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

:confused:

and when i run the example code i get

 wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Line 6: invalid key_mgmt '4d326a0f002d37005f5272ee4b219820b525a3309d67ffe69b61cc69afb32bd4'
Line 6: no key_mgmt values configured.
Line 6: failed to parse key_mgmt '4d326a0f002d37005f5272ee4b219820b525a3309d67ffe69b61cc69afb32bd4'.
Line 9: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.

:confused: help! lol

---

### Post by HydroTech on 2009-05-09
I typed this b4 your last post but didn't send it: 
In case you're not familiar with hexadecimal, it means base 16. We usually use decimal(base 10) system. What hex does is add 1 2 3 4 5 6 7 8 9 A B C D E F 10(where 10 = 16) but you don't have to know this. If the passphrase is 'dudeimcool' then it's broken down into hex values like so: A1 45 CF... Do you have permission to change your router's settings? If so, go into your routers security section and copy down the key(it will be a mixture of numbers and letters) and enter it into any device that connects to it.(including your computer.) Also, is you computer compatible with WPA(2)?

---

### Post by NooBcubE on 2009-05-09
im pretty sure my comp is compatible with wpa2 it worked fine with it when i had windoze and all the forums say my hardware is compatible would the hex pwd be the same as my psk?

---

### Post by HydroTech on 2009-05-09
Ya, looking at what you wrote, you are WPA(2) ready but don't have the right key. Try printing the key from the router on paper then take it to your computer and check and double check to see if it's correct. That's about all I can do for you right now. :(

---

### Post by NooBcubE on 2009-05-10
so while i have been going through this whole ordeal i recently had a room mate move out and one of my other room mates decided to change the password so the ex roomie cant use it without telling me....so all along i have been goin to such extreme lengths to fix this issue and i've had to wrong password....i'm totally upping his rent for this lol thank you for all your help! if it werent for you i wouldnt have went into the security settings for the router and seen it! at first i was a little iffy about making the full jump to linux but now i am completely content :P

---


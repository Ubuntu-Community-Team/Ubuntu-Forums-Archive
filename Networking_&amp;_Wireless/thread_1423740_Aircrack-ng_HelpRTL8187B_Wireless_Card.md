---
title: "Aircrack-ng Help/RTL8187B Wireless Card"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Skyxz on 2010-03-07
Hello all, i'm currently trying to install Aircrack-ng, and i'm really confused.

I'm following this guide: [http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)
I'm up to where its telling me to do this:

tar xfz aircrack-ng-1.0-rc1.tar.gz
cd aircrack-ng-1.0-rc1
make
make install

I have Aircrack-ng-1.0.tar.gz on my desktop, and it extracts it and goes to the directory fine.
but when i get to make, i get this error:
```
skyxz@skyxz-laptop:~/Desktop/aircrack-ng-1.0$ sudo make
make -C src all
make[1]: Entering directory `/home/skyxz/Desktop/aircrack-ng-1.0/src'
make -C osdep
make[2]: Entering directory `/home/skyxz/Desktop/aircrack-ng-1.0/src/osdep'
Building for Linux
make[3]: Entering directory `/home/skyxz/Desktop/aircrack-ng-1.0/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/skyxz/Desktop/aircrack-ng-1.0/src/osdep'
make[2]: Leaving directory `/home/skyxz/Desktop/aircrack-ng-1.0/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3910: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/skyxz/Desktop/aircrack-ng-1.0/src'
make: *** [all] Error 2
```

What's going on? why wont it compile it and install it?
I'm using this for the patch to patch my RTL8187B wireless drivers: 
[http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch](http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch)

I don't have the slightest clue what to do when i get up to patching my drivers, basically, im asking if anyone can help me, install aircrack, and get it working then help me patch my drivers? i've copied the drivers in the [http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch](http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch) website, and put it into a notepad file called RTL8187B.patch on my desktop.

What do i do? :S been trying for 2hours now, help please.

---

### Post by mockingbird on 2010-03-07
Install from depo.  Don't try to compile yourself.

"sudo apt-get install aircrack-ng".

---

### Post by Skyxz on 2010-03-07
Okay, so once i install it, how do i patch my drivers?

---

### Post by Skyxz on 2010-03-07
Help?

---

### Post by mockingbird on 2010-03-07
First check to see if you really need to patch your drivers.  I also read that I would have to patch my Intel Wireless but they added support to it.

After you install aircrack:

sudo airmon-ng start wlan0 (Or the name of your WAN interface)

If it says "Monitor Mode Enabled" then you don't have to patch.

If you do have to patch, then download the source for your driver, apply the patch, and then compile.  After you compile, you will be left with a ".ko" file.  Modprobe that file and it should load.

If the older driver is loaded, then you will have to rmmod it first.

I can't give you step-by-step instructions at the moment because I haven't tried it yet with the Realtek Wireless.  Luckily, I do have a realtek card on my upstairs desktop and am willing to give it a shot.

LMK

---

### Post by Skyxz on 2010-03-07
Okay so i did it. 
```

"sudo airmon-ng start wlan0 and sudo airmon-ng start eth0"
```

I got:
```

Found 5 processes that could cause trouble.
If airdump-ng, aireplay-ng or airtun-ng stops working after a short peiod of time, you may want to kill (some of) them!

PID       NAME
541       avahi-daemon
546       avahi-daemon
553       NetworkManager
652       wpa_supplicant
655       dhclient
```

What now?

---

### Post by mockingbird on 2010-03-07
Ok, aircrack is whining about the interface already being used for an internet connection.  Funny, it doesn't do this to me on my laptop.

```

541       avahi-daemon
546       avahi-daemon
553       NetworkManager
652       wpa_supplicant
655       dhclient

```

Hmmm...  Try typing "ifconfig wlan0 down".

I hate to say it but you're a little out of your league here.  I was at least expecting that you would have some rudimentary understanding of iwconfig or ifconfig.

---

### Post by linuxhelps on 2010-06-11
I acuattly get the same exact problem and ifconfig waln0 down dosnt help... I'm using a virtual machine PLEASE HELP AS WELL!!

---


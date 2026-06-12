---
title: "iwlwifi - a fix to get wireless N functional again"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by asg1290 on 2013-01-23
I've seen a lot of postings out there saying to add 11n_disable=1 to their modprobe config.  While this got me working it was not helping my wireless speeds.  After digging and playing I got mine to work.  Please note this isn't a proper fix.  We are just pulling in the latest drivers from upstream's backports project and installing them over the current ones.

```

sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://www.kernel.org/pub/linux/kernel/projects/backports/2013/01/23/compat-drivers-2013-01-23-1-u.tar.bz2
tar -jxvf compat-drivers-2013-01-23-1-u.tar.bz2 
cd compat-drivers-2013-01-23-1-u/
./scripts/driver-select intel
make clean
make
sudo make install
```

If you did the modprobe hack you will need to undo it. Remove 11n_disable=1 from /etc/modprobe.d/iwlwifi.conf.

At this point reboot.  (Yes you dont have to but it's a good way to test your change.)

Hopefully when your system is back you will see this from iwconfig

```
root@ubuntu:~# iwconfig
lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"mynetwork_5ghz"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: 32:24:A8:E8:17:34   
          Bit Rate=450 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2596  Invalid misc:267   Missed beacon:0

eth0      no wireless extensions.

```

If you wish to revert the changes just run

```

cd compat-drivers-2013-01-23-1-u/
sudo make uninstall

```


Hope this helps.  If I can get some time I'll see if I can get a ppa going for this.

---

### Post by mindracer on 2013-03-19
This didn't work for me, was showing 90mbps but I couldn't ping anywhere, had revert back to modprobe hack. 

I'm using 12.04 with Intel N wifi link 5300 on a Dell Studio 1557 laptop

---

### Post by ahallubuntu on 2013-03-20
I've had exceptionally good luck with iwlwifi and my Intel 5100 cards on my Dell laptops (and an Acer netbook) in 12.04 .  I've never needed to disable 802.11n on any of the laptops I use this card in.  No dropped connection issues, very fast local connections and file transfer over wireless, used on many WiFi hotspots.  It's usually pretty easy to swap out wireless cards in Dell laptops - I've upgraded a number of them from slower cards to 5100's.  You might consider snagging a used 5100 from eBay, probably under $5 USD shipped.  Make sure you get the right size - half height or full height - and don't get the HP/Lenovo/IBM version.  You can get a Dell/Acer/Toshiba/Sony version and it should work fine if you get the right size. 

The big difference between the 5100 and the 5300 is that the 5300 can do - in theory - 450Mbps upload (three connection streams) whereas the 5100 can do only 300Mbps (two streams) download and 150Mbps (one stream) upload.  In practice, there are very few routers you'll connect to that can do 450Mbps and you're probably only going to get 300Mbps maximum anyway -  so really the big benefit of the 5300 is that it is 300Mbps upload instead of 150Mbps that the 5100  can do.

The 5300 has three antenna wires and the 5100 has only two.  If you swap cards, you could simply leave one of the wires unhooked on the 5100.

---

### Post by atomopawn on 2013-05-02
> **asg1290 said:**
> I've seen a lot of postings out there saying to add 11n_disable=1 to their modprobe config.  While this got me working it was not helping my wireless speeds.  After digging and playing I got mine to work.  Please note this isn't a proper fix.  We are just pulling in the latest drivers from upstream's backports project and installing them over the current ones.  ....  Hope this helps.  If I can get some time I'll see if I can get a ppa going for this.  THANK YOU!!!  I had to use a slightly newer compat-linux tarball than you did, but for the first time I have 802.11n working with my Intel Centrino 1030-N wireless card!  I have been fooling around with this for MONTHS and MONTHS trying to get it working in Ubuntu.  Who knew it was this simple!?

---

### Post by TheDavidJohnson on 2013-08-23
I think this is the solution I've been hoping for... however, after running the "make" command, I get some errors:

```
make -C /lib/modules/3.2.0-52-generic/build M=/home/david/compat-drivers-2013-01-23-1-u modulesmake[1]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic'
  CC [M]  /home/david/compat-drivers-2013-01-23-1-u/compat/main.o
In file included from /home/david/compat-drivers-2013-01-23-1-u/include/linux/compat-2.6.h:71:0,
                 from <command-line>:0:
/home/david/compat-drivers-2013-01-23-1-u/include/linux/compat-3.8.h:48:32: error: redefinition of ‘kref_get_unless_zero’
include/linux/kref.h:47:32: note: previous definition of ‘kref_get_unless_zero’ was here
make[3]: *** [/home/david/compat-drivers-2013-01-23-1-u/compat/main.o] Error 1
make[2]: *** [/home/david/compat-drivers-2013-01-23-1-u/compat] Error 2
make[1]: *** [_module_/home/david/compat-drivers-2013-01-23-1-u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic'
make: *** [modules] Error 2

```

Does it look like I goofed something up?

---

### Post by Stravlonbeta on 2014-03-05
I've got the same problems... Ubuntu 13.10 (amd64), Intel WiFi 5100, Connection Speed locked at 65Mps with many TX errors, upload to my NAS about 1MB/s - extremly slow. I've tried the compat-drivers but getting the same erros as Johnson. Maybe somebody can help me?

---

### Post by kschumake83 on 2014-03-05
I was just looking through this as I am looking for an answer on this also for my 5300, but it seems these errors are because we already have a newer kernel and driver than what you are trying to install.

---


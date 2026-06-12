---
title: "wired and wireless network on Toshiba Satellite L855-S5372"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by stasike on 2012-12-09
I bought a new Toshiba Satellite L855-S5372 notebook at a Black Friday sale. It came with Windows 8.

I wanted to install Mint Linux 13 Maya KDE and Mint Linux 14 Nadia KDE on it. Those distributions are based on Ubuntu 12.04 Precise Pangolin and Ununtu 12.10 Quantal Quetzal respectively.

I tried a few things suggested on this forums. Quite a few of them require a working net connection before installation. But ... both of my network connections - wired and wireless were non-functional out-of-the-box.

-------------------------------------------------------------

Wireless:

I found working solution for wireless here:
[http://ubuntuforums.org/showthread.php?p=12373496#post12373496](http://ubuntuforums.org/showthread.php?p=12373496#post12373496)
All you need is to create a text file /etc/modprobe.d/rtl8192ce.conf 
with one line:
```
options rtl8192ce ips=0 fwlps=0 debug=2

```You can do it like this
```
sudo kate /etc/modprobe.d/rtl8192ce.conf
```insert line ```
options rtl8192ce ips=0 fwlps=0 debug=2 
``` and save the file


Just transfer this tiny howto to your Toshiba notebook using USB key, so you do not have to type (and won't make a typo)

-------------------------------------------------------------

Wired ethernet:

Now you have that wireless working, you can build driver for that Atheron AR8161 Gigabit Ethernet card.

I have found solution here:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

--- quote ---

The AR8161 is a very new combined Ethernet/Bluetooth controller and its driver alx is in the testing/QA process, so it's not in the kernel yet.

To build and install the driver:
We will download a recent compat-wireless-pc driver package, install build dependencies, select the AR8161 module alx, build and install it.

Type/paste the following, line-by-line, in a terminal:

```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
wget -O- http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-07-03-pc.tar.bz2 | tar -xj
cd compat-wireless-2012-07-03-pc
./scripts/driver-select alx
make
sudo make install
```You can then reboot, or manually load the driver with:

```
sudo modprobe alx
```

---

### Post by mörgæs on 2012-12-09
Thanks for the info, and welcome to the fora.

If you mark the thread 'solved' using 'thread tools' there is a better chance that people find it. Have done it for you this time.

---

### Post by stasike on 2012-12-09
> **mörgæs said:**
> If you mark the thread 'solved' using 'thread tools' there is a better chance that people find it. Have done it for you this time.Thank you. 
I wasn't familiar with that functionality.

I wanted to put together info that works for this particular notebook model, so other owners do not have to search and try out many other solutions like I did. 

Also when somebody needs to decide whether to buy this notebook, this can be a little help. Everything else that I tested works "out of box". And when you put in an SSD disk (I needed to test one for a friend) this very cheap (under $600) Ivy Bridge Core i7 machine becomes a lightning fast monster.

---

### Post by mörgæs on 2012-12-10
Good. If you have more advice for this particular computer you could maybe post here:

[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---


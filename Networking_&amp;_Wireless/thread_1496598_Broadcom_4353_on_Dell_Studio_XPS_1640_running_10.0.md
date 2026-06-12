---
title: "Broadcom 4353 on Dell Studio XPS 1640 running 10.04 frequently disconnects"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by potiphera on 2010-05-29
I have a Dell Studio XPS 1640.  The wireless card is a Broadcom Corporation Device 4353, and I'm using the Broadcom STA driver suggested in System>Administration>Hardware Drivers.  Every couple of minutes, it disconnects from my network and then it spends several minutes reconnecting and gives me the "Authentication required by wireless network" prompt several times.  The problem only exists in Lucid: it goes away when I use a Karmic live CD, and a similar XPS computer with perfect wireless performance in Karmic has the same problem when I run Lucid on that one.  Aside from downgrading to Karmic, how can I fix this?

---

### Post by potiphera on 2010-05-30
(bump)

Also, I tried the Windows driver with ndiswrapper, but it couldn't detect any internet at all that way.  If the only solution to this problem is to downgrade the network manager or the driver to the Karmic version, I would certainly be interested.

---

### Post by potiphera on 2010-05-31
(bump)

---

### Post by potiphera on 2010-06-01
I'll probably just install Karmic if I don't get any responses within the next few hours.  But if anyone comes across this thread later and knows the solution, go ahead and post it, as other people may have the same problem, and I'll have to upgrade eventually.

---

### Post by ejohnson0547 on 2010-06-01
I have Ubuntu 9.10 installed on a Dell Studio XPS 1340.  I also have the Broadcom STA wireless driver installed from System-Administration-Hardware Drivers.

I am experiencing the same issue, the wireless will frequently disconnect, then reconnect.  Sometimes it will require me to enter the wireless password again.

I was going to try upgrading to 10.04 to see if that fixes it.

This really sucks.

---

### Post by potiphera on 2010-06-01
Odd, I had a 1340 (which Dell replaced with this 1640 because it started smoking!), and I don't remember having that problem on 9.10.  But I'll be sure to to mess around with the live CD a bit more before downgrading on this one.

---

### Post by potiphera on 2010-06-02
Now that I think of it, I may have had 9.04 on the last Dell -- it's my mom's computer, so I barely remember.  But wireless worked fine on it.

---

### Post by darkdragn on 2010-06-02
Maybe that driver just isn't working properly for your wificard... umm, i'm not sure, but another option could b43-fwcutter... check it out, it's worth a try. (apt-get install b43-fwcutter)

---

### Post by potiphera on 2010-06-05
b43-fwcutter didn't work, but thanks for the advice! Downgrading to Karmic seems to solve the problem though.

---

### Post by ncumming on 2010-06-13
not my intention to hijack this thread...however did you (or anyone else) ever get your wireless adapter to work consistently in 10.04?  I'm having the same problem with a vostro 3400 using the same wireless adapter.

---

### Post by terje83 on 2010-08-21
This is a problem with the actual device drivers it seems, they are misbehaving all the time. I have a Latitude 2110, and it has the same problem.

Has anyone tried Maverick or updating the kernel to see if that helps the issue?

---

### Post by merry_meerkat on 2010-08-22
I'm having the same problem (also Broadcom 4353) on a Dell Studio 1747. I have had this problem both on Karmic and Lucid, and am anxiously looking for a solution. Hope that someone comes up with something.

Haven't tried Maverick (yet).

---

### Post by shuttleworthwannabe on 2010-08-25
same problem with vostr 3700 broadcom 4353 wireless device on lspci output. tried all the drivers in synaptic but nothing doing.

Anyone know how to activate this wireless device?

S

---

### Post by Thor1776 on 2010-09-25
I'm still having this issue too, on a Dell Inspiron 1764 laptop running Ubuntu 10.04.

I will check back and post here again if I find the solution. :KS

---

### Post by nik_nah on 2010-11-30
I've fixed the wireless with my vostro 3400 which has this chip.

If you have the same problem as me, symptoms...
* pings are ok normally but every minute or so they slow down to 100-200ms for a few secs and the network pauses or gets stuck.
* When you run "while sleep 1; do iwconfig eth1; done", once every minute or so the frequencies are constantly changing(scanning).
* When you run "/sbin/wpa_supplicant" manually, it prints "ioctl[SIOCGIWSCAN]: Invalid argument" every few seconds.


Here's what I did...
* comment out/delete the whole section in /etc/network/interfaces where your wireless network interface is, this stops the wpa_supplicant from auto starting.
* Tell wpa_supplicant to not scan all the time,  put this in the file /etc/wpa_supplicant/eth1 
network={
	ssid="????"
	scan_ssid=0
	key_mgmt=WPA-PSK
	psk="????"
}


* Change ???? to your sid & password.  and maybe WPA if you're not using that.

* Put this in a script and run it whenever you want wireless...

stop network-manager
stop network-interface INTERFACE=eth1
kill `pidof wpa_supplicant`
kill `pidof dhclient3`
sleep 1
rmmod wl
sleep 15
modprobe wl
sleep 30
/sbin/wpa_supplicant -B -ieth1 -Dwext -c /etc/wpa_supplicant/eth1
dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1

* the above symptoms should disappear.

network-manager keeps on sending scan messages to the wireless driver even when we've commented out the interface so it needs to be stopped.
Apparently this may have been fixed in ubuntu 10.10? [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)


Also, the broadcom STA drivers doesn't compile with debugging on.  I've put a patch here to get it to compile with debugging, but it's only needed if you want to look at stuff...
[http://pastebin.com/3EngUntC](http://pastebin.com/3EngUntC)

---

### Post by uncaspi on 2010-11-30
I would considered to get the latest STA driver from Broadcom site. Released Oct this year. It's not added to the repository yet so you must download the file from Broadcom site and it's named
hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

Follow the instructions in the README.txt file to compile and install.

---

### Post by nik_nah on 2010-11-30
> **uncaspi said:**
> I would considered to get the latest STA driver from Broadcom site. Released Oct this year. It's not added to the repository yet so you must download the file from Broadcom site and it's named
hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

Follow the instructions in the README.txt file to compile and install.

The debugging patch I put above is for that version.  It still had the same problems for me.  I'm not sure if broadcom developers has compiled it with debugging on for a while, cause lots of things were missing there.

---

### Post by uncaspi on 2010-11-30
I had to do sudo depmod -a after make install and before modprobe wl to get it work.

---

### Post by zdenal on 2010-12-02
The Broadcom cards (used by Dell for example) have problems on Lucid and Maverick. It is caused by new driver wl, which can interfere with old b43 etc drivers.

In my post 

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts, then you can check if

a) your card is supported by wl.ko module
b) Use steps to get the card working on Lucid or Maverick

---


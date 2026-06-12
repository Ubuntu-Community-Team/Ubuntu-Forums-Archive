---
title: "cant use airodump-ng on my HP DV2000 - Broadcom Corporation BCM4312 card"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by costamatrix on 2009-04-27
hi folks, i am trying to use the airodump/aircrack (first time using it)...but after several trys and several searchs on the web, i just cant get it to work..


i have a notebook hp dv2000 with Broadcom Corporation BCM4312 card...

when i run:

sudo airmon-ng stop eth1 1

i got:

Interface	Chipset		Driver

eth1		Unknown 		wl (monitor mode disabled)



and then i run:

sudo airodump-ng --ivs -d 00:4f:62:19:3d:b7 -w eps4 eth1


and i got:

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.



...any one can help me?

thx

---

### Post by Ayuthia on 2009-04-27
You might want to check you chipset and see if you have a 14e4:4315 chipset (lspci -nn).  If you do, then your card is not compatible with aircrack.  The wl and ndiswrapper modules do not provide that capability.

---

### Post by costamatrix on 2009-04-27
Hi Ayuthia, thanks for your reply....

lets see... i run lspci -nn and the line regarding my network adapter, was:

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

---

### Post by Ayuthia on 2009-04-27
> **costamatrix said:**
> Hi Ayuthia, thanks for your reply....

lets see... i run lspci -nn and the line regarding my network adapter, was:

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

As far as I know, that card should work.  However, it does look like you are using the Broadcom STA (wl) driver instead of the b43 version.  You will need to enable the b43 module and disable the Broadcom STA module in order to use aircrack.

---

### Post by costamatrix on 2009-04-27
ok, thx again ayuthia...could point me in the right direction???

how do i do this?
do you know some guide that i can follow?

---

### Post by kevdog on 2009-04-27
What driver do you have installed currently?  

lshw -C network

---

### Post by Ayuthia on 2009-04-27
Based on the first post, it looks like you have the wl module running.  Since you have it running, you should go ahead and install b43-fwcutter.  It will need to download firmware to help the b43 module work.

You will need to check and see what is currently blacklisted.  If the b43 and ssb modules are blacklisted then we will need to take them out.

Before we go too far, can you let us know which version of Ubuntu you are using (Jaunty 9.04, Intrepid 8.10, etc.)?  It will help us see what commands we will need to provide.  They changed the way things are blacklisted in Jaunty so I just want to make sure that we provide the correct commands.

---

### Post by costamatrix on 2009-04-28
ok thanks!

i am using ubuntu 9.04 (jaunty)..

---

### Post by costamatrix on 2009-04-28
> **kevdog said:**
> What driver do you have installed currently?  

lshw -C network

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

---

### Post by Ayuthia on 2009-04-28
Ok.  Can you post the results of:
```
cat /etc/modprobe.d/blacklist.conf|grep -e b43 -e ssb -e wl
cat /etc/modprobe.d/modules.conf|grep -e b43 -e ssb -e wl
```

In order to use the b43 module, you will need to install b43-fwcutter.  Once that is installed, you might try going to System->Administration->Hardware Drivers and disabling the Broadcom STA option and enabling the Broadcom b43 option.

To try it out for the session:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will get your wireless up and running with the b43 module for this session.

Once we are able to see the results of the two files and if the commands to run it for the current session works, we can provide the information on what needs to be done to make it permanent.

---

### Post by costamatrix on 2009-04-28
ok Ayuthia, here it goes:

cat /etc/modprobe.d/blacklist.conf|grep -e b43 -e ssb -e wl

returned:

# replaced by b43 and ssb.

the command:
cat /etc/modprobe.d/modules.conf|grep -e b43 -e ssb -e wl

returned:

cat: /etc/modprobe.d/modules.conf: No such file or directory

then i did a ls:

ls /etc/modprobe.d/
alsa-base.conf          blacklist-bcm43.conf  blacklist-firewire.conf     blacklist-modem.conf  blacklist-watchdog.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist.conf        blacklist-framebuffer.conf  blacklist-oss.conf    dkms.conf

---

### Post by costamatrix on 2009-04-28
Ayuthia...i also tried you code below:

> sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan

the line sudo ifconfig wlan0 up i changed to sudo ifconfig eth1 up - my wifi connection is eth1...

but then i got an error... that the i interface cold not be found..or something like that.

---

### Post by Ayuthia on 2009-04-28
> **costamatrix said:**
> ok Ayuthia, here it goes:

cat /etc/modprobe.d/blacklist.conf|grep -e b43 -e ssb -e wl

returned:

# replaced by b43 and ssb.

the command:
cat /etc/modprobe.d/modules.conf|grep -e b43 -e ssb -e wl

returned:

cat: /etc/modprobe.d/modules.conf: No such file or directory

then i did a ls:

ls /etc/modprobe.d/
alsa-base.conf          blacklist-bcm43.conf  blacklist-firewire.conf     blacklist-modem.conf  blacklist-watchdog.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist.conf        blacklist-framebuffer.conf  blacklist-oss.conf    dkms.conf

The /etc/modprobe.d/modules.conf should have been:
```
cat /etc/modules |grep -e b43 -e ssb -e wl
```Sorry about that.

It does not look like there is anything in those files yet.  Have you already installed b43-fwcutter?  From the results in your other post, it looks like it was not able to bring up wlan0.  If you have already installed it, you should have files in /lib/firmware/b43.

---

### Post by costamatrix on 2009-04-28
Ayuthia...ive got it!

i installed fw cutler and then i was able to use airodump and aircrack.

thanks very much for your help !

---

### Post by h051n on 2010-09-15
Thank you very very much, I had the same problem with the same chipset and after 2 days I can solve it with your help, thanks a million

---

### Post by h051n on 2010-09-15
but when i restart my ubuntu again the driver changes to wl,I want it to be wlan0 all the time,can you help me?

---

### Post by laggy23 on 2010-11-09
Sweet! i had the same problem,but this fixed it thank you Ubuntu and the Ubuntu community!

---


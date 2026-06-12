---
title: "Atheros AR242X - Eee PC 1000HA"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by jayk121121 on 2009-02-24
I have an Eee PC 1000HA. I installed Eeebuntu on it, because I was not sure if everything would work out of the box with vanilla Ubuntu.

lspci -v:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

On some networks, it works perfectly. However, on other networks, it disconnects at random times, and the only solution I have found to that is to reboot the netbook, which is rather annoying.

I tried to find the solution to this on the internet, but it the majority of the results concerned people who could not get the card detected in the first place. I do not have that issue.

Does anybody have the solution?

---

### Post by hobo on 2009-02-24
My laptop uses the same NIC and I have had the same problems that you mention. My fix was to install Wicd which removes network manager in the process. And I have not had the problems you mention since.

Correction: My laptop does not use the same chipset. Mine is a AR5212. Sorry for the confusion.

---

### Post by jayk121121 on 2009-02-25
Thank you. I will try Wicd and report back.

---

### Post by Crafty Kisses on 2009-02-25
This has actually been solved with a newer driver for this card, you can download it right [here.]("http://file-hosting.site-hosts.net/eeepc/madwifi-nr-r3366+ar5007.tar.gz") Once you have it installed compile it from source and install it, and your wireless card should work a lot better. So copy this folder to wherever you want when you're done downloading. Remember you need the build-essential package, but run these commands in these steps and you should be fine:
```
sudo apt-get install build-essential
cd /home/username/foldername
tar xzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007/
make
sudo make install

```
Once you have done that in order, the new driver should be compiled and you want to reboot by running the following:
```
sudo shutdown -r now
```
Once you have rebooted you should be good to go and your wireless should work a lot better.

---

### Post by binbash on 2009-02-25
This is how i got it working : 

[http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html)

---

### Post by electronbee on 2009-02-25
Any ways, I have an Acer3680 and with some intrepid serching I came across this post as both laptops have the same wireless card. And, this is what I have to offer:

1) this method did not work for me: [http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html)

2) the newer driver link and script posted by Codename WORKED!!

Thanks Codename!!! :D

eb

---

### Post by jayk121121 on 2009-02-26
When I try to run make, it says this:

```
cd: 1: can't cd to /lib/modules/2.6.27-8-eeepc/build
Makefile.inc:66: *** /lib/modules/2.6.27-8-eeepc/build is missing, please set KERNELPATH.  Stop.
```

What should I do?

---

### Post by binbash on 2009-02-26
I guess you need the headers, search for linux-headers and download the one which matches your kernel number

---

### Post by jayk121121 on 2009-02-26
Thank you. It was just that I needed that package. Oddly enough, my wireless card has not been acting up since I started this thread. If and when it does start randomly disconnecting again, I will install the new drivers.

---

### Post by BBtheEE on 2009-03-13
For those that have a problem compiling for the 2.6.27 kernel (as I did) with the solution above, due to an error with an implicit declaration of function __skb_append, install a subversion client if you haven't already, and run this from the command line:

svn co [http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4](http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4) madwifi-0.9.4

This will use the subversion client to check out (co) the madwifi-0.9.4 source.

Then cd into the madwifi-0.9.4 directory, make, then make install.

Good luck!
  Bill

---


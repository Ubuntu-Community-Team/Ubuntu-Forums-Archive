---
title: "Ongoing DNS problems."
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by oneHappyCanuck on 2012-11-21
I have Ubuntu 12.04 on my lenovo laptop installed from ISO in a dual boot config with windows 7.  

My Lenovo/Ubuntu notebook is used in a home wifi context using DHCP and router provided DNS addresses. Other devices on this network have reliable and snappy internet access; on my Ubuntu notebook however DNS lookups in FF or Chrome are horrendously slow (pages constantly load with broken links) and frequently fail altogether with address not found errors.

I've been all over the forums looking for a solution to this problem to no avail.  

I have disabled ipv6 in Firefox about:config
I have commenting out #dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf and restarted network manager (and then the laptop); both produce no networking at all. 
I have replaced /etc/resolv.conf with a static file with the original content, and with the 'nameserver' entry replaced with google DNS. 
I have set static google DNS servers in the wireless network config
I have moved 'dns' forward (second after 'files') in /etc/nsswitch.conf

In desperation I removed network-manager altogether and installed WICD network manager with static DNS server addresses for the home wifi. This produces much faster page loads in FF but *still* frequently fails to resolve addresses in FF and Chrome, for several minutes at a time, before mysteriously starting to work again at full speed.  

At a loss; help appreciated.

---

### Post by wildmanne39 on 2012-11-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by papibe on 2012-11-21
Hi oneHappyCanuck.

Sorry to hear that.

This is what I would do:

It may be a unstable wireless driver. Have you tested it using an ethernet cable?

Try benchmarking your router DNS responsiveness by using [namebench]("http://code.google.com/p/namebench/"). Set your default DNS pointing to your router and run the script. Note that further testing are not as accurate as the first one.

Just a few thoughts. Let us know how it goes.
Regards.

---

### Post by oneHappyCanuck on 2012-12-16
Thanks for the reply - netinfo.txt attached.

---

### Post by oneHappyCanuck on 2012-12-16
Will test with the wired connection and let you know; had a quick look at namebench but I don't see an install for Ubuntu? 
Thx,

---


---
title: "2 Network cards, DNS issues"
date: 2005-02-15
forum: Networking &amp; Wireless
---

### Post by phill on 2005-02-15
Hi

I have two network cards on my laptop (one internal one external USB).  When I'm in the office I have a connection (eth0) to the local network (172.16) that is configured manually so I don't get an unwanted gateway added.  My other card (eth1) takes me outside the local network and gives me a direct connection to the internet, with an IP assigned by DHCP from the 192.168 range.

The resolv.conf file is updated from the DHCP update of eth1 which gives me external DNS.  However when I am in the office I also want to use the internal DNS at 172.16.1.1.  The only way I have found to do this is after booting and logging in, run a script which adds this nameserver to the top of the resolv.conf file (after search this.network).

Is there any way I can add this additional DNS automatically when booting, rather than having to do it each time?  I don't fully understand init.d scripts and I suppose the script would need to test to make sure there were two network cards installed.  

[BTW the whole thing gets really confusing as my external USB card is actually eth0 and my internal port is eth1.  Is there anyway of changing this?]

Thanks,

P h i l l

---

### Post by Strider on 2005-02-15
You can probably add a script at boot up that will check to see if you're using eth0 or eth1 and that can create the entry in /etc/resolv.conf for you.  Or just stick with using your own script.  If you're interested in a boot up script, let me know.

If you would like to take a shot at it, all boot up scripts are referenced under /etc/rcX.d (X=number).  I normally put my own custom scripts in /etc/rc2.d/S99xlocal or you can call it something else.  If you look in /etc/rc2.d there should be an S99stop-bootlogd which will be the last script executed in the boot sequence from this directory so if you have an S99xlocal it will now be the last script to execute.

Hope that helps.

---


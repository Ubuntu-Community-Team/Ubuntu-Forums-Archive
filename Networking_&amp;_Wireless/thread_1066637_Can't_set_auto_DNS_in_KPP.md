---
title: "Can't set auto DNS in KPP"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by Eugene_Bondarenko on 2009-02-11
Hi! I have eeebuntu remix and I've run into a weird problem. I am using kppp and EV-DO modem but when I connect to the internet, I can't access URLs (IPs are fine). As far as I see that's a DNS problem but when I found this section in kppp config I just can't set it to "Automatic" because the radio button is disabled (greyed out). However "Manual" radion button is active (and set by default). Does anyone know wtf this is. :confused:

Another small problem is that every time I reboot I have to open terminal and execute sudo /sbin/modprobe usbserial vendor=0x(VID) product=0x(PID). Then it asks for my password and then mounts modem to ttyUSB0. This behaviour is really annoying. In kppp I found a field where I can put command that needs to be executed before connecting. I want to put /sbin/modprobe... there but I wonder how do I deel with this authentication issue. Can I somehow pass password or just disable authentication for modprobe?

Thanks for your time!

---

### Post by Eugene_Bondarenko on 2009-02-11
Small update. If I sudo /usr/bin/kppp, the "Automatic" option is pretty OK for me. It's not greyed out. However if I set it to "Automatic" and save, then close and open kppp (without sudo),the problem is there again. Automatic is greyed out and not selected.

---

### Post by Eugene_Bondarenko on 2009-02-11
LOL, never mind, I fixed it by a simple script
```
echo xxxxx | sudo -S /sbin/modprobe usbserial vendor=0x19d2 product=0xffff
echo xxxxx | sudo -S /usr/bin/kppp
```

Now instead of clicking on kppp, I just click on this script :KS

---

### Post by mccarbro on 2011-08-25
Figured out the solution, not sure if the issue is with the Kubuntu distro, but all you need to do is add the 'dip' group to your user account and everything will work.  If you look at the permissions on 'pppd' daemon you will see the owners as 'root/dip'.  You will notice on your user account that the 'dialout' group is checked but not the 'dip' group.  Here is a url that helps, [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html).  Not sure why nobody identified this but it got me working.  As soon as you re-open the kppp you will see that you can change the 'automatic' dns setting.

---


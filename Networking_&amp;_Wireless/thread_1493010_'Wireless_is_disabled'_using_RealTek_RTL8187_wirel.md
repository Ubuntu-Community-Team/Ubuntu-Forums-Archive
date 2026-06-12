---
title: "'Wireless is disabled' using RealTek RTL8187 wireless USB adapter"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by wouldhaveahole on 2010-05-25
I have tried and searched high and low but can find no solution.
I am new to Linux, and have just completed installing Ubuntu 10.04 LTS.
When I click on teh network manager it shows:

Wired Network
disconnected
Wireless Network (Intel PRO/Wireless 2200BG [Calexico2])
wireless is disabled
Wireless Network (Manufacturer RealTek RTL8187 RTL8187 Wireless)
wireless is disabled

Right clicking on the network managed shows:

Enable Network (Ticked)
Enable Wireless (greyed out)


I want to be able to connect through the RealTek wireless adapted.
I would really appreciate some help with this.

Thanks

---

### Post by hardik_s_desai on 2010-05-27
I have the same problem, For me after installation the first time i logged the wireless worked. But after that it is not working.

Moreover my wireless adapter works with Windows 7, hence i don't suspect a problem with the adapter.

---

### Post by hardik_s_desai on 2010-05-27
1.sudo su

2.echo -e “alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; >  /etc/modprobe.d/iwl3945

3.reboot

this three commands worked for me, i found this from an old thread 

[http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516)

thanks chill555

---

### Post by chili555 on 2010-05-27
> **hardik_s_desai said:**
> 1.sudo su

2.echo -e “alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; >  /etc/modprobe.d/iwl3945

3.reboot

this three commands worked for me, i found this from an old thread 

[http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516)

thanks chill555You are welcome, however, options for iwl3945 will not fix his RTL8187 nor his ipw2200.

---


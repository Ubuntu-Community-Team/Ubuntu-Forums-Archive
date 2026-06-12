---
title: "Internet Problems"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Mike.B on 2009-02-19
I have a E220 mobile modem. It used to work well in 8.10 via NM and 8.04 via wvdial. Since a recent new install of 8.10, it will work with neither. I am at a complete loss. I have followed every thread I can find on the matter to no avail. I am at the stage where I say to myself "Go back to Windows 'cos everything works fine there".
I can get wvdial to get my modem to the point that the little light stays constantly blue. Which means that I have a connection. Firefox will not allow me to view pages, and synaptic cannot connect to the repositories for upgrades. Can anyone help please.

---

### Post by GeorgeVita on 2009-02-20
Hi **Mike.B**,
it would be helpful to post the output of the **sudo wvdial** command and your **/etc/wvdial.conf** file.

Also check if firefox is in **Offline mode**. You can untick it with **ALT-F W**.

I am using 8.04 and wvdial but as I remember on 8.10 with NM07 you can work directly with the E220 modem just with:
click on the Network Manager icon, then Mobile Broadband and choose **Country** and **Provider**. Connect with click the Network Manager icon and then your provider.

In both ways it is easier when you have the SIM PIN check disabled (from windows or by placing the SIM card to a mobile phone).

Regards,
George

---


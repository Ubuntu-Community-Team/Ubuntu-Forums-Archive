---
title: "Huawei USB modem issue with wvdial.conf"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by tapasray on 2012-08-01
I am trying to configure a Huawei USB modem (provider - Tata Photon) on a Dell Vostro notebook running Ubuntu 12.04. I have followed instructions given on the provider's web site at  <www.tataphoton.com/download/dialers/dialup-internet-on-linux.pdf>. At one point I am required to run the "gedit /etc/wvdial.conf" command in the terminal to open the configuration file. However, that file is refusing to open and I am getting an error message in the file edit pop-up window, which says I do not have permission. In the terminal itself, the output is the following:

** (gedit:6932): CRITICAL *: gedit_conversion_error_info_bar_get_encoding: assertion 'menu' failed

I would really appreciate some help here.

---

### Post by alexfish on 2012-08-01
You need to use the "sudo command"

```
sudo gedit /etc/wvdial.conf
``` enter password when requested

regards

alexfish

[http://www.pcurtis.com/ubuntu.htm](http://www.pcurtis.com/ubuntu.htm)

---

### Post by tapasray on 2012-08-02
Many thanks, @alexfish! I was able to open, edit and save the wvdial.conf file with your command, with the following configuration. 

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 9600
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CRM=1
Stupid Mode = 1
ISDN = 0
Modem Type = Analog Modem
Phone = #777
Password = internet
Username = internet


However, when I run the 'wvdial' command after this, I get the
following output:


--> Can't open '/etc/wvdial.conf' for reading: Permission denied
--> ... starting with blank configuration.
--> Wvdial: Internet dialer version 1.61
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory


The menu under the wireless icon at the top of my laptop screen now
has 'Tata Indicom (Photon+) connection' as an option. But when I click
on it, I get a 'Modem network Disconnected' message.

Looking forward to your help.

---

### Post by Advait on 2012-09-23
Have you tried "sudo wvdial"? That worked for me. Did you get it working? If  yes, how did you fix it?

I'm using a Reliance NetConnect+ cdma cellular mobile broadband usb stick in Kerala.

---

### Post by Advait on 2012-09-23
[http://ubuntuforums.org/showthread.php?t=2060724](http://ubuntuforums.org/showthread.php?t=2060724)

This thread may be helpful. I was having similar problems.

Cheers,

Advait

---

### Post by tapasray on 2012-09-23
I had tried to edit the wvdial settings, following instructions given on the Tata Photon web site. This included saving user id and password in the wvdial settings file. Got confused along the way,but at one point noticed that the wireless drop-down menu was showing the Tata Photon modem. But it still wasn't connecting. Finally, a Tata Photon engineer showed me that there were user id and password fields associated with that entry in the wireless connections drop-down, and all I needed to do is, enter the values there. I did that, and voila! It's been working since then.

---


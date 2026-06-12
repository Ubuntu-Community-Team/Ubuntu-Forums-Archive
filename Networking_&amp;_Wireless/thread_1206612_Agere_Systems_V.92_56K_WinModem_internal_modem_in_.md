---
title: "Agere Systems V.92 56K WinModem internal modem in Ubuntu 9.04"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by Pacifik on 2009-07-07
Hello friends,

I have been using Ubuntu since 3 yrs and quite satisfied with it. Its a great OS. 

Recently my friend was eager to use Ubuntu. I installed Jaunty (Ubuntu 9.04) in an old hardware having **Agere Systems V.92 56K WinModem internal modem**. The system is detecting the modem chipset but fails to detect the modem when tried to configure via **wvdial**. I have tried with scanModem (latest release 02-July-2009). Please find the attachment named "ModemData".

As mentioned in the "ModemData" file, I have tried with **kernel-2.6.27** series (with **dkms-agrsm_2.1.80-6_i386.deb** installed ) in **Ubuntu Jaunty** and tried to configure it but it also failed.

I have tried to search through internet, but nothing fruitful information I could find for Ubuntu 9.04 (Jaunty).

Yours comment would be highly appreciated.

Thanks

---

### Post by GeorgeVita on 2009-07-07
Hi **Pacifik**, as 9.04 now uses 2.6.28-13-generic I think it is not good to test an older kernel. I did some unsuccessful tests with a similar modem on my 9.04 Desktop. I faced "Segmentation fault" error running wvdial.

After searching into .txt files coming with the agrserial agrmodem drivers I found that for newer kernels: "This is something that is being worked on at the moment and hopefully gets fixed soon so the modem can be used successfully".

[http://archives.linmodems.org/34050](http://archives.linmodems.org/34050)

Regards,
George

---

### Post by Pacifik on 2009-07-07
Thanks George,
I am wondering whether installing Ubuntu Intrepid (8.10) in my friend's PC would help. Will "Agere Systems V.92 56K WinModem internal modem" work in Intrepid? Any comment? As he is eager to use Ubuntu.

---

### Post by GeorgeVita on 2009-07-07
Hi again, from the same post:
> Currently, the dkms-agrsm code is NOT competent for 2.6.28 and later kernels.
A short term fix is to install linux-image + linux-headers packages
for earlier kernels.
For example, for Ubuntu Jaunty with 2.6.28 kernels, linux-image +
linux-headers packages
for earlier 2.26.27 series Intrepid kernels can be installed. Search
for them at:
  [http://packages.ubuntu.com](http://packages.ubuntu.com)


it seems that can work with 9.04 with previous kernel (is it?) but better with 8.10 (I personally did not test it). I am  waiting for the new driver. If you have any result post it here.

Regards,
George

---


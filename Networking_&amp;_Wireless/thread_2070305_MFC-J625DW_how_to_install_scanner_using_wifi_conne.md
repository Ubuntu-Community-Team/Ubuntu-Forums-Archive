---
title: "MFC-J625DW how to install scanner using wifi connection?"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by downunderthunder on 2012-10-12
Hi there,

I just received the multifunction-printer Brother MFC-J625DW.
I just installed the cups-drivers so printing already works fine.
Unfortunetely I do not have any clue how get the integrated scanner working using the wifi connection?

Some background information:

OS:   Xubunutu 12.04
the brothers multifunction device IP adress is 192.178.1.26 it has been successfully added to the network
my notebook running xubuntu is also connected to the network via wifi connection.

but how to find and install the scanner?!?

---

### Post by plucky on 2012-10-12
> **downunderthunder said:**
> Hi there,

I just received the multifunction-printer Brother MFC-J625DW.
I just installed the cups-drivers so printing already works fine.
Unfortunetely I do not have any clue how get the integrated scanner working using the wifi connection?

Some background information:

OS:   Xubunutu 12.04
the brothers multifunction device IP adress is 192.178.1.26 it has been successfully added to the network
my notebook running xubuntu is also connected to the network via wifi connection.

but how to find and install the scanner?!?


Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4) and download the brscan4 .deb file.

Then follow the instructions to install over a network.

If you can,try to verify it works on a USB connection first.

Good Luck

---

### Post by downunderthunder on 2012-10-13
wow that was easy now the device entirely works fine for me.

thx a lot

---

### Post by pplante19 on 2012-12-20
Sorry to bring this subject back, but would like to get your expertise on how to set up this since you have succesfully done it, here's my setup;

Laptop with Kubuntu 12.10
Printer : Brother MFC-J625DW (same as you)

I don't need the scan, just the printer installed via WiFi. I've donwloaded the linux drivers from Brother's website, installed it (I've gone into 'Printers > Add new Printer', he detected the networked printer, I had to pinpoint where the files were and he installed, the printer seems to be correctly installed, it says 'Printer ready', but when I try to print, nothing happens. I don't see it under the Kubuntu print manager, neither on the Windows print manager and the printer itself does nothing.

Can someone help me on this one, telling me what I have to do, step by step procedure to get this work?

On a sidenote, everytime I boot into Kubuntu, it does not remember my WiFi password, I have to re-enter it everytime I log into the system, it that normal or is it a problem? I don't see any checkbox saying 'Remember this password' or 'Connect automatically'.

Thanks a lot!

---

### Post by kurt18947 on 2012-12-20
> **pplante19 said:**
> Sorry to bring this subject back, but would like to get your expertise on how to set up this since you have succesfully done it, here's my setup;

Laptop with Kubuntu 12.10
Printer : Brother MFC-J625DW (same as you)

I don't need the scan, just the printer installed via WiFi. I've donwloaded the linux drivers from Brother's website, installed it (I've gone into 'Printers > Add new Printer', he detected the networked printer, I had to pinpoint where the files were and he installed, the printer seems to be correctly installed, it says 'Printer ready', but when I try to print, nothing happens. I don't see it under the Kubuntu print manager, neither on the Windows print manager and the printer itself does nothing.

Can someone help me on this one, telling me what I have to do, step by step procedure to get this work?

On a sidenote, everytime I boot into Kubuntu, it does not remember my WiFi password, I have to re-enter it everytime I log into the system, it that normal or is it a problem? I don't see any checkbox saying 'Remember this password' or 'Connect automatically'.

Thanks a lot!

If this makes sense for you, I've had excellent luck installing Brother printers using the script here.  You should run it from an account with sudo privileges.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

It will download the correct drivers, ask what network connection you want to use, etc. etc.

---

### Post by pplante19 on 2012-12-20
Ok, I will try that tonight (I don't have the laptop with me) and come back with the answer if it works or not.

Thanks for the input! Appreciated

---


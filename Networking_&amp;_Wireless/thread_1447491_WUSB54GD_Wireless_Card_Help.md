---
title: "WUSB54GD Wireless Card Help"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by spike53 on 2010-04-05
[LEFT]Hello,
I've been looking all around for drivers for this card. Linksys doesn't supply Linux drivers. I did see a post [here]("http://ubuntuforums.org/showthread.php?t=1353044&highlight=wusb54gc") where I followed all of the steps. I followed procedure A since in
code: 
> /lib/modulesthere's only a 2.6.31-14-generic folder. I'm puzzled because I followed the steps exactly and came out with NetworkManager saying that my "device isn't ready".
If anyone has and additional info for me to gain internet access I'd be very thankful.
Thanks,
Spike
P.S. How do you do the code thing? It doesn't work when using the quote function.
[/LEFT]

---

### Post by chili555 on 2010-04-05
That little **#** next to the quote button is the code button.

What is the outcome if you do:```
sudo modprobe rt3070sta
dmesg | grep -i rt3
```Thanks.

---

### Post by spike53 on 2010-04-05
Thanks for the quick response!
I don't get any responses to either of your codes. I tried modprobe with -n and -v switches and that didn't return anything either.

---

### Post by chili555 on 2010-04-05
If it accepted the modprobe without complaint, it loaded without error. However, it didn't grab your device and create a wireless interface or it would have shown in dmesg. When you do:```
lsusb
```Is your usb.id confirmed as 1737:0077? Please post:```
modinfo rt3070sta | grep 0077
```If your usb.id is not 1737:0077, please do:```
modinfo rt3070sta | grep <last_four_digits>
```Post the result.

---

### Post by spike53 on 2010-04-05
It did come back as 1731:0077. This was the resulting message from the modinfo command:
```
kevin@kevin-LINUX:~$ modinfo rt3070sta | grep 0077
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
```

---

### Post by b k on 2010-04-05
To: spike53
 
PROCEDURE A of the link you followed in post #1 is written strictly for Linksys *[COLOR=red]Wusb54gc v3[/COLOR]* usb wireless adapter with ID ***[COLOR=red]1737:0077[/COLOR]*** Linksys .
 
The info you need to put into usb_main_dev.c file in STEP 5 of that procedure would be completely different.
 
*[COLOR=red]Assuming[/COLOR]* that your wireless adapter uses the *[COLOR=red]same driver[/COLOR]* in that procedure, you need to find out your wireless adapter ID number and put that info in the usb_main_dev.c file .
 
See posts #11 and #12 of that link to get an idea of what to do in STEP 5
 
To: chili555
 
Please continue to assist Spike53
 
Thank you very much

---

### Post by chili555 on 2010-04-05
@bk-

It's pretty sure he did that step correctly:> kevin@kevin-LINUX:~$ modinfo rt3070sta | grep 0077
alias:          usb:v[COLOR="Red"]1737[/COLOR]p[COLOR="Red"]0077[/COLOR]d*dc*dsc*dp*ic*isc*ip*Now if we could figure out why the driver didn't grab the device and ... drive. Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Attach the file dmesg.zip to your reply.

---

### Post by spike53 on 2010-04-05
Thanks b k. When I looked at the code again, the list of devices and chipsets seemed to have disappeared. I took them off the 11th post and put it into the usb_main_dev.c file, did a sudo reboot now everything works. I'm actually typing this on Linux right now. Thanks Chili55 and b k for helping me get hooked up to the internet. I'm really starting to like this Linux stuff afterall.

---

### Post by spike53 on 2010-04-05
So I just did a system update and after restarting...no internet. The update knocked out my hard work and get up 2.6.31-20 now as opposed to the ...-14. I found recent Linux drivers on the Ralink site. I don't know how to install the drivers though. If there's any documentation or explanations anyone knows regarding those updates and how to install it I'd love to see them. Thanks!
spike

---

### Post by chili555 on 2010-04-05
You built the driver against your -13 kernel. Now you are running a -20 kernel. Simply go back to the folder where the Makefile is located, something like:```
cd Desktop/2009whatever
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe rt3070sta
```You will need to repeat this process whenever Update Manager gives you a new kernel.

---

### Post by spike53 on 2010-04-05
All of those codes ran without errors. I did a sudo reboot after it all and when the desktop came up, my wireless card still isn't working. It still shows in the "lsusb" command. Do I need to do the process from the link given all over again but change all of the ..-14 folders to ..-20?

---

### Post by chili555 on 2010-04-05
Please go ahead.

---

### Post by spike53 on 2010-04-05
OK so I've found the solution. Indeed if I change the ..-14 to ..-20 and follow the steps in procedure A with those changes, everything works again. Thanks for the help everyone!

---


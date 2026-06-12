---
title: "Broadcom BCM4311"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by bowtiev8 on 2012-04-19
I'm sorry if this is already posted, but I can't seem to find the exact solution to my problem.

I have a Dell Latitude D620 with Ubuntu 11.10 64 bit installed on it. My wireless card is a Broadcome BCM4311 with the PCI-ID: 14e4:4312. The wireless is working, but every time I restart/boot the computer I have to type in sudo modprobe b43 in the terminal to activate it. Not a big problem, but it's annoying in the long run. Does anyone have a solution to this problem?

The 5 GHz network doesn't work either, but as I understand, that isn't supported yet.

In advance, thanks for all your help.

---

### Post by albandy on 2012-04-19
add it to modprobe.d
for example, create a file called wifi.conf in /etc/modprobe.d
then add this to the file:
options b43
save the file and reboot.

---

### Post by bowtiev8 on 2012-04-19
> **albandy said:**
> add it to modprobe.d
for example, create a file called wifi.conf in /etc/modprobe.d
then add this to the file:
options b43
save the file and reboot.

Thanks. I followed your instructions, but it didn't help. On top of that I now get this message after having done sudo modprobe b43, "WARNING: /etc/modprobe.d/wifi.conf line 1: ignoring bad line starting with 'options'". (Quotation marks by me)

---

### Post by albandy on 2012-04-19
My fault. 
options b43 pio=0 qos=0

if this not works change pio=0 (DMA) for pio=1 (PIO)

---

### Post by bowtiev8 on 2012-04-19
> **albandy said:**
> My fault. 
options b43 pio=0 qos=0

if this not works change pio=0 (DMA) for pio=1 (PIO)

That's okay. I tried it both with pio=0 and pio=1 and neither one of those works.

---

### Post by albandy on 2012-04-19
I don't know why it doesn't work, but a nasty way to make it work is running it (the modprobe command) during system boot.

---

### Post by bowtiev8 on 2012-04-19
> **albandy said:**
> I don't know why it doesn't work, but a nasty way to make it work is running it (the modprobe command) during system boot.

That's okay. Thanks for your help.

---

### Post by wildmanne39 on 2012-04-19
Hi, you should just be able to run this command:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
you may have to remove the one you created earlier I am not sure, after you run the command reboot and see.
Thanks

---

### Post by albandy on 2012-04-19
> **wildmanne39 said:**
> Hi, you should just be able to run this command:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
you may have to remove the one you created earlier I am not sure, after you run the command reboot and see.
Thanks

+100
This should work. 
I don't know how I could forget the /etc/modprobe file

---

### Post by bowtiev8 on 2012-04-19
> **wildmanne39 said:**
> Hi, you should just be able to run this command:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
you may have to remove the one you created earlier I am not sure, after you run the command reboot and see.
Thanks

Thanks. That solved the problem.
I didn't have to remove the file I made. Do you still recommend to remove it, or can I just leave it alone?

---

### Post by wildmanne39 on 2012-04-19
Hi, I think it will be okay to leave it since the name of the file is incorrect it will be ignored.
Thanks

---

### Post by bowtiev8 on 2012-04-20
> **wildmanne39 said:**
> Hi, I think it will be okay to leave it since the name of the file is incorrect it will be ignored.
Thanks

Okay. Thanks for your help and time. :)

---

### Post by wildmanne39 on 2012-04-20
Your welcome!
Enjoy

---


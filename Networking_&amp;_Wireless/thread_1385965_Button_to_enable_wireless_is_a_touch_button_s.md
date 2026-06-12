---
title: "Button to enable wireless is a touch button :s"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by lilspanyol on 2010-01-20
Hey guys,

So I have a intel wifi link 5100 , the drivers should work BUT iwconfig doesn't show my card ..

However doing a ' sudo lshw -C network ' command , it DOES show my wireless card is recognised but not enabled and here is where the problems start ..

I have a touch button on my laptop to enable/dissable it 
And when I touch it in Ubuntu it doesn't light up like in W7

How can I enable it :s? I really want to use ubuntu !

Sincerely,
Lilspanyol

---

### Post by lilspanyol on 2010-01-20
Sorry if I sound rude , but please !
I need help!

---

### Post by chili555 on 2010-01-20
Please open a terminal and do:```
sudo modprobe iwlagn
dmesg | grep iwl
dmesg | grep -i kill
rfkill list
```Please post the result.

---

### Post by lilspanyol on 2010-01-20
Will go on ubuntu NOW , thanks in advance!
(the results will be up in less then 10 mins)

---

### Post by lilspanyol on 2010-01-20
here is what I get :

acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by chili555 on 2010-01-20
How about the other commands?

---

### Post by chili555 on 2010-01-20
Also, please let us see:```
lsmod | grep acer
```Thanks.

---

### Post by lilspanyol on 2010-01-20
Will boot Ubuntu again but i also get something like 'mac is in deep sleep'
Thank you for helping me , do you think that you know the cause of the problem?

---

### Post by chili555 on 2010-01-20
> do you think that you know the cause of the problem?Not yet. I hope you will have a few more clues for me when we see the requested data.

---

### Post by lilspanyol on 2010-01-20
Got some new info for ya' 


**lsmod | grep acer**
acer_wmi               15936  0 
led_class               4096  2 acer_wmi,iwlcore

**dmesg | grep iwl**
[   71.107337] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x53FE650C
[   71.122596] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x53FE650C
[   71.137854] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x53FE650C
[   71.153114] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x53FE650C
[   71.164387] iwlagn 0000:05:00.0: Failed to init APMG
[   71.164497] iwlagn 0000:05:00.0: PCI INT A disabled
[   71.167174] iwlagn: probe of 0000:05:00.0 failed with error -110

Also : I get the 'mac is in sleep ALOT more times' , I just copied the bottom of the output because the beginning is just 'Mac is in deep sleep'

---

### Post by chili555 on 2010-01-20
Please do:```
sudo gedit /boot/grub/menu.lst
```It will have a lot of text commented out, like this:> #text comments
#more commentsThe first several lines not commented out after Default Options will look something like this:```
title           Ubuntu 9.10, kernel 2.6.31-17-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro quiet splash 
initrd          /boot/initrd.img-2.6.31-17-generic
quiet
```Please add to these lines as I have highlighted here:```
title           Ubuntu 9.10, kernel 2.6.31-17-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro [COLOR="Red"]pci=use_crs[/COLOR] quiet splash 
initrd          /boot/initrd.img-2.6.31-17-generic
quiet
```Proofread carefully...twice...save and close gedit. Reboot and run:```
dmesg | grep iwl
```We have our fingers crossed!

---


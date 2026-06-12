---
title: "working wireless card stopped working on dell laptop"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2012-01-13
Hi  I am got this issue on a laptop where the only OS is Ubuntu 11.04 64 bit.

It had a wireless card which was working.Everything seems to be fine till today evening.Where after a reboot I lost my wireless connectivity.

I checked the logs etc so from a previous date i.e. when the wireless card was working I used to see following lines

```
Jan  8 10:12:37 rin kernel: [    0.646120] pci 0000:0c:00.0: [14e4:4315] type 0 class 0x000280

Jan  8 10:11:06 rin kernel: [   13.554056] wl: module license 'MIXED/Proprietary' taints kernel.
Jan  2 12:20:50 rin kernel: [   13.949811] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  2 12:20:50 rin kernel: [   13.949826] wl 0000:0c:00.0: setting latency timer to 64


```
My assumption is that the device was detected and upon normal functioning of device above lines should be present in log.

Today i.e. 13 January onwards when the card stopped working 

The entry corresponding to eth1 i.e. pci 14e4:4315 are missing in kern.log which are present as I posted the log for Jan 8.

Here is one line which I suspect  might be the problem from kern.log
```
Jan 13 19:57:10 rin kernel: [   14.620677] RIP  [<ffffffffa018d599>] osl_readl+0x9/0x10 [wl]

``` So what exactly happened here? Why a working wireless card suddenly stopped working?

---

### Post by wildmanne39 on 2012-01-13
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jamesbon on 2012-01-14
> **wildmanne39 said:**
> 
cat /etc/lsb-release; 
If you would have read my question properly you would have noticed this is already mentioned there 11.04 64 bit.
> **wildmanne39 said:**
> 
uname -a

2.6.38-8-generic.
> **wildmanne39 said:**
> 
lspci -nnk | grep -iA2 net

This has stopped detecting my wireless card.
So there is no output with respect to wireless card here.
However when the card was working the output was 
14e4:4315
> **wildmanne39 said:**
> 
iwconfig

This fails to give output of my wireless card.
> **wildmanne39 said:**
> 
rfkill list all

```

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
> **wildmanne39 said:**
> 
lsmod

This does not have wireless modules there which was being used on a working connection.The working connection used to have 
wl.ko module which it does not show.

---

### Post by wildmanne39 on 2012-01-15
Hi, I did read your post but those are the standard questions that I ask anyway so I can refer back to them easily in case this turns into a long thread and just because you are using 11.04 that does not tell me which kernel you are using which is important when dealing with drivers for wireless cards.

The fact that
```
lspci -nnk | grep -iA2 net
```
does not show your card is bad, you need to check your bios and make sure it did not get turned off in the bios.

Is it possible the card is going bad?, do you think you had a power surge?

Also it is possible that you have a corrupt file.

Even if no drivers were installed that command should have showed it unless it is a usb adapter, if it is please post the results of:
```
lsusb
```
Thanks

---

### Post by jamesbon on 2012-01-15
> **wildmanne39 said:**
> Hi, I did read your post but those are the standard questions that I ask anyway so I can refer back to them easily in case this turns into a long thread and just because you are using 11.04 that does not tell me which kernel you are using which is important when dealing with drivers for wireless cards.

> **wildmanne39 said:**
> 
Ok sorry about that.
[QUOTE=wildmanne39;11612344]
The fact that
```
lspci -nnk | grep -iA2 net
```
does not show your card is bad, 

Ok
> **wildmanne39 said:**
> 
you need to check your bios and make sure it did not get turned off in the bios.

No it is not turned off there.
> **wildmanne39 said:**
> 
Is it possible the card is going bad?, do you think you had a power surge?

Well I do not know how to check this one.
> **wildmanne39 said:**
> 
Also it is possible that you have a corrupt file.

Which file do you refer?
> **wildmanne39 said:**
> 
Even if no drivers were installed that command should have showed it unless it is a usb adapter, if it is please post the results of:

Thanks
No it is not a USB adaptor.That lspci command is not showing the 14e4:4315 kind of out put which it used to previously show when the device was working.

---

### Post by jamesbon on 2012-01-15
I did a ```
modprobe -r wl ssb
``` and ```
modeprobe wl ssb.
```
here is the problem
on the working machine (another laptop with same chipset)
lspci -vnn output
says 
```
Kernel Driver in Use:wl
```
where as on the machine in problem it says
```
Kernel Driver in use: b43-pci-bridge
```
this should be rather ```
Kernel Driver in use:wl
``` on machine in problem
then I will be able to get things back.
But I do not know as why has this happened.

---

### Post by jamesbon on 2012-01-15
Ok here is some thing which solved the problem.I discussed it herehttp://chat.stackexchange.com/rooms/201/ask-ubuntu-general-room

and System-->Administration-->Additional Drivers
uninstalled the old driver rebooted and then again installed the previous driver.
Rebooted it worked.I have no clue as why I had to do this on a machine on which wireless was working already.Doing show definitely shows some problem which needs to be addressed because ideally I should not have been reinstalling the same driver which was already present.That was Ubuntu 11.04 and on chat link people told the 11.04 had problem in wireless driver so this issue is there I need to upgrade to 11.10 it seems.
[http://askubuntu.com/questions/95559/wireless-stopped-working-on-a-working-dell-laptop/95597#95597](http://askubuntu.com/questions/95559/wireless-stopped-working-on-a-working-dell-laptop/95597#95597)

---

### Post by wildmanne39 on 2012-01-15
Hi, you probably had a file corruption and lost the driver or, you should run disk utility and see if you have bad sectors on your hard drive.

Your wireless card can also use the b43 driver which in general works better I think.
Thanks

---

### Post by jamesbon on 2012-01-16
Hmm, is there any utility on Ubuntu with which I can check bad sectors on my hard disk. After marking this thread solved I formatted my laptop with Ubuntu 11.10 and wifi started working initially but then I see the same problem here again.

---

### Post by wildmanne39 on 2012-01-16
Hi, disk utility is how you can check your hard drive.

Being that ```
lspci -nnk | grep -iA2 net
```only shows your card sometimes I still suspect your card is going out.
Thanks

---


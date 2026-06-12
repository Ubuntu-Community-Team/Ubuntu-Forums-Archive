---
title: "Capabilities &lt;access denied&gt;"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by JeremieUSMC on 2010-05-27
I have a Dell inspiron E1705 that I recently installed 10.04 LTS on. The wireless card i'm using is a Belkin express card that worked perfectly fine with 9.1 but won't work with 10.04.....
 
lspci -v output shows the card as installed with a driver listed but under capabilities is says "access denied". Any help would be greatly appriciated.

---

### Post by chili555 on 2010-05-27
Please try:```
[COLOR="Red"]sudo[/COLOR] lspci -v
```If you find anything useful in 'capabilities,' please let us know.

---

### Post by JeremieUSMC on 2010-05-27
Give me just a minute to post up the results of that.
 
 
 
Output of sudo lspci -v
 
Network controller: RaLink RT2860
Subsystem:  Belkin Device 817c
Flags: fast devsel, IRQ 19
[virtual] Memory at dfcf0000 (32-bit, non-prefetchable) [disabled] [size=64k]
Capabilities: [40] Power Management version 3
Capabilities: [50] Message signalled Interrupts: Mask- 64bit+ Qeue=0/5 Enable-
Capabilities: [70] Express Endpoint, MSI 00
Capabilities: [100] Advanced Erro Reporting <?>
Kernel driver in use:  rt2860
Kernel modules:  rt2860sta

---

### Post by chili555 on 2010-05-27
> Kernel driver in use: rt2860
Kernel modules: rt2860staHow about posting:```
dmesg | grep -i RT2
```Thanks.

---

### Post by JeremieUSMC on 2010-05-27
> **chili555 said:**
> How about posting:```
dmesg | grep -i RT2
```Thanks.
not sure how to enter that comand, I'm really new to this o/s

---

### Post by chili555 on 2010-05-27
That pipe symbol | is on the right side of my US keyboard along with \. Sorry, I should have mentioned that. If you are on the computer in question, you can copy and paste right in to the terminal. Then copy and paste your response!

---

### Post by JeremieUSMC on 2010-05-27
Not currently on that computer trying to get it to connect wirelessly. Don't have a batery in it so I have to turn it off to move it to the LAN line.  Might have to do that.  Let me try and find the pipe symbol on this computer first.  Thanks for the help

---

### Post by JeremieUSMC on 2010-05-27
ok here is what i got from that
 
rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
rt2860 0000:0c:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
rt2860 0000:0c:00.0: Setting latency timer to 64
--> Error 2 opening /ect/Wireless/RT2860/RT2860STA.dat
[drm]       CRT2:  INTERNAL_KLDSCP_DAC2
 
 
I hope this helps

---

### Post by chili555 on 2010-05-27
It does help. If we find an error involving your wireless driver, we probably can fix it. I think you made two typographical errors in you last post. Please proofread these steps carefully. Please do:```
sudo su
mkdir -p /etc/Wireless/RT2860STA
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
exit
```Now is it working? It may take a reboot.

---

### Post by chili555 on 2010-05-27
> --> Error 2 opening /ect/Wireless/RT2860/RT2860STA.datI think it is actually:```
--> Error 2 opening /[COLOR="Red"]etc[/COLOR]/Wireless/RT2860[COLOR="Red"]STA[/COLOR]/RT2860STA.dat
```

---

### Post by JeremieUSMC on 2010-05-27
you were right about the typo.  
 
It See's the network and tries to connect but nothing happens.  After a couple of tries it usually goes to a black screen and the Caps lock and Num lock lights start flashing at me and I have to restart the computer.

---

### Post by chili555 on 2010-05-27
> it usually goes to a black screen and the Caps lock and Num lock lights start flashing at me and I have to restart the computer.Also known as a kernel panic. It may or may not have anything to do with your wireless.

You might google up rt2860sta ubuntu "kernel panic" and see what you can see.

You might also look at:```
sudo cat /var/log/syslog | grep -i error
```See what looks interesting.

I am retiring for the night. I'll check in tomorrow.

---

### Post by JeremieUSMC on 2010-05-27
thank you for the help, I'm going to crash as well.

---

### Post by JeremieUSMC on 2010-05-27
The list of errors is WAY too long to post completely but what i noticed was 
 
NetworkManager: <warn> default_adapter_cb():  bluez error getting default adapter: The name org.bluez was not provided by any .service files.
 
NetworkManager: <Warn> nm_supplicant_interface_add_cb(): Unexpected supplicant error getting interface: wpa_supplicant couldn't grab this interface.
 
Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
 
networkManager: <WARN> default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any service files.
 
That is mostly greek to me, but I hope you can make something out of it.

---

### Post by JeremieUSMC on 2010-05-28
Just bumping this back up to see if anyone else has any advice for me.

---

### Post by chili555 on 2010-05-28
Please reboot and then do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file in your home directory called dmesg.zip. Please transfer it on a USB stick or similar and attach it to your reply. I will examine it and hopefully we can get some ideas about what's going wrong.

---

### Post by JeremieUSMC on 2010-05-28
> **chili555 said:**
> Please reboot and then do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file in your home directory called dmesg.zip. Please transfer it on a USB stick or similar and attach it to your reply. I will examine it and hopefully we can get some ideas about what's going wrong.
 
 
Here is what you requested, really hope you can make some sense of it, because I'm lost.

---

### Post by chili555 on 2010-05-28
There are a ton of these:> ERROR!!! BBP write R86=0xffffffff failI am Googling and suggest you do the same. Almost all the posts I see about this involve Asus eeepcs. Yours, however, is a Dell.

We are still getting this:>  --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.datI'd like to try something a bit experimental. Please do:```
sudo su
echo #test > /etc/Wireless/RT2860STA/RT2860STA.dat
exit
reboot
```Now run:```
dmesg | grep 286
```Is the error still there, or some other error? May I see:```
lsmod | grep dell
```Thanks.

---

### Post by JeremieUSMC on 2010-05-28
Here is what i get after doing everything you suggested
 
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] dmesg | grep 286
[    0.416286] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.728648] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.728657] sd 0:0:0:0: [sda] 153356490 512-byte logical blocks: (78.5 GB/73.1 GiB)
[   14.449935] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.456597] rt2860 0000:0c:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.456807] rt2860 0000:0c:00.0: setting latency timer to 64
[   14.853892] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] lsmod | grep dell
dell_wmi                1793  0 
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL]

---

### Post by chili555 on 2010-05-28
Please do:```
sudo rmmod -f dell-laptop
```Do you see networks in Network Manager? Can you connect without a lock-up? Please let me see:```
ls -al /etc/Wireless/RT2860STA
```Thanks.

---

### Post by JeremieUSMC on 2010-05-28
jeremie@jeremie-laptop:~$ sudo rmmod -f dell-laptop
[sudo] password for jeremie: 
 
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] ls -al /etc/Wireless/RT2860STA
total 8
drwxr-xr-x 2 root root 4096 2010-05-27 23:28 .
drwxr-xr-x 4 root root 4096 2010-05-27 23:29 ..
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] 

 
 
it use to see my home network, but now it doesn't have anything listed and I haven't been able to connect to anything wirelessly since I installed 10.04.

---

### Post by chili555 on 2010-05-29
It has been looking for a file which doesn't appear to be there:> --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.datLet's create one. Please do:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```The text editor gedit will open a new file. Add one line:```
#test
```Proofread, save and close gedit. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2860sta
sudo service network-manager restart
```Now are there networks to connect to?

---

### Post by JeremieUSMC on 2010-05-30
Sorry I haven't had a chance to reply to this thead.  I've been out of town and away from my problem computer.  Will update it when i get back, thanks again for the help.

---

### Post by JeremieUSMC on 2010-06-01
> **chili555 said:**
> It has been looking for a file which doesn't appear to be there:Let's create one. Please do:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```The text editor gedit will open a new file. Add one line:```
#test
```Proofread, save and close gedit. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2860sta
sudo service network-manager restart
```Now are there networks to connect to?
I can't save it after making the change because the directory doesn't exist.  i tried to creat one using
 
sudo mkdir /ect/Wireless/RT2860STA
 
but got an error saying MKdir: cannot creat directory No such file or directory.
 
I'm lost

---

### Post by chili555 on 2010-06-01
> sudo mkdir /ect/Wireless/RT2860STAPlease try:```
sudo mkdir /[COLOR="Red"]etc[/COLOR]/Wireless/RT2860STA
```Didn't you take care of that at about post #9? Thanks.

---

### Post by JeremieUSMC on 2010-06-01
Ok took care of that, but after the rest of the steps it still didn't have any networks listed, just said Device not ready.
 
After restarting the machine it lists all the networks in the area, but isn't able to connect to any of them.  The error about not being able to find the file is no longer there howerver.

---

### Post by chili555 on 2010-06-01
Please do:```
sudo iwlist wlan0 scan
```Do you see a network with reasonable strength, say 70% or so, that is not encrypted? Click the Network Manager icon and try to connect to it. What happens?

Please run:```
sudo cat /var/log/syslog | tail -n20
```Please post the result and let's see what's happening.

---

### Post by JeremieUSMC on 2010-06-01
Thanks for the quick response here is what I got.  Headed to bed so I'll check again tomorrow thanks.
 
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] sudo iwlist wlan0 scan
wlan0     No scan results
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] sudo cat /var/log/syslog | tail -n20
Jun  1 22:02:23 jeremie-laptop kernel: [  787.604593] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:23 jeremie-laptop kernel: [  787.604991] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:24 jeremie-laptop kernel: [  788.604592] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:24 jeremie-laptop kernel: [  788.604990] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:25 jeremie-laptop kernel: [  789.604594] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:25 jeremie-laptop kernel: [  789.604992] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:26 jeremie-laptop kernel: [  790.604597] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:26 jeremie-laptop kernel: [  790.604994] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:27 jeremie-laptop kernel: [  791.604593] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:27 jeremie-laptop kernel: [  791.604993] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:28 jeremie-laptop kernel: [  792.604595] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:28 jeremie-laptop kernel: [  792.604994] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:29 jeremie-laptop kernel: [  793.605585] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:29 jeremie-laptop kernel: [  793.605984] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:30 jeremie-laptop kernel: [  794.604594] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:30 jeremie-laptop kernel: [  794.604993] ERROR!!! BBP write R1=0xffffffff fail
Jun  1 22:02:31 jeremie-laptop kernel: [  795.604595] ERROR!!! BBP read R3=0xffffffff fail
Jun  1 22:02:31 jeremie-laptop kernel: [  795.604993] ERROR!!! BBP write R3=0xffffffff fail
Jun  1 22:02:31 jeremie-laptop kernel: [  795.605388] ERROR!!! BBP read R1=0xffffffff fail
Jun  1 22:02:31 jeremie-laptop kernel: [  795.605781] ERROR!!! BBP write R1=0xffffffff fail
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL]

---

### Post by chili555 on 2010-06-02
Wow! That looks nasty! It looks like there is an underlying issue to fix first. May we see:```
sudo cat /var/log/syslog | grep pciehp
```Thanks.


Note to chili: 

modprobe -r pciehp
modprobe pciehp pciehp_force=1 pciehp_slot_with_bus=1

---

### Post by JeremieUSMC on 2010-06-03
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] sudo cat /var/log/syslog | grep pciehp
[sudo] password for jeremie: 
May 25 06:01:22 jeremie-laptop kernel: [    0.326345] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 20:28:37 jeremie-laptop kernel: [    0.326300] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:09:16 jeremie-laptop kernel: [    0.326312] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:14:57 jeremie-laptop kernel: [    0.326704] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:18:30 jeremie-laptop kernel: [    0.322670] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:21:25 jeremie-laptop kernel: [    0.322674] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:29:22 jeremie-laptop kernel: [    0.326345] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:33:08 jeremie-laptop kernel: [    0.322336] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 25 21:47:07 jeremie-laptop kernel: [    0.322292] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 27 21:07:46 jeremie-laptop kernel: [    0.322336] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 27 21:14:33 jeremie-laptop kernel: [    0.326620] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 27 23:31:19 jeremie-laptop kernel: [    0.322295] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 28 15:44:33 jeremie-laptop kernel: [    0.322333] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 28 16:58:15 jeremie-laptop kernel: [    0.326362] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 28 17:01:05 jeremie-laptop kernel: [    0.322336] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  1 21:39:23 jeremie-laptop kernel: [    0.322663] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  1 21:49:29 jeremie-laptop kernel: [    0.326333] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL]

---

### Post by JeremieUSMC on 2010-06-04
bumb
 
Any help?

---

### Post by JeremieUSMC on 2010-06-06
New problem,  ran
 
> sudo lspci -v 
 
0c:00.0 Network controller: RaLink RT2860 (rev ff) (prog-if ff)
 !!! Unknown header type 7f
 Kernel driver in use: rt2860
 Kernel modules: rt2860sta
[EMAIL="jeremie@jeremie-laptop:~$"]jeremie@jeremie-laptop:~$[/EMAIL] 
 
Any advise?

---

### Post by JeremieUSMC on 2010-06-07
I'm guessing I'm SOL at this point?

---


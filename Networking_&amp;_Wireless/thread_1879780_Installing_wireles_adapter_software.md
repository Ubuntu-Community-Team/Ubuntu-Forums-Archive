---
title: "Installing wireles adapter software"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by 6stringer on 2011-11-12
Hey everyone;

1st timer here who is absolutely brand new to Linux. I recently installed Ubuntu 11.4 on my old windows xp box because it refused to function any longer even after several fresh installs of xp. While I'm enjoying kicking the tires and poking around Ubuntu's features I cannot get online.

I have a Rosewill RNX-N180UBE wireless adapter that I used for this machine (it's in the basement) and of course the 1st thing I found out about Ubuntu is that when I inserted the software disc it will not install.

My question is where do I find a SIMPLE tutorial to better understand how to work around these types of things. I understand that not all windows software may work but I'm sure hoping to get this adapter working.

Thanks

---

### Post by praseodym on 2011-11-12
Hi and welcome.

Please show the terminal (CTRL+ALT+T) outputs of the following commands:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by 6stringer on 2011-11-12
> **praseodym said:**
> Hi and welcome.

Please show the terminal (CTRL+ALT+T) outputs of the following commands:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
lsmod
iwconfig
rfkill list
```


I'm sorry, but I do not understand how to accomplish this. I am brand new to Linux. Is there a tutorial you can direct me to please?

Thank you

---

### Post by wildmanne39 on 2011-11-12
Hi, welcome to the forum! Please open a terminal by hitting ctrl+alt+t copy and paste the commands praseodym gave you into it one line at a time, when you enter a command that begins with sudo you will have to enter your user password, it will not be shown in the terminal as you type it so when you are done typing it just hit enter, then paste the results here:
Thank you

---

### Post by 6stringer on 2011-11-12
Hope this is what you are asking for:

To run a command as administrator (user "root"), use "sudo <command>".  
 See "man sudo_root" for details.  
 

 ron@ubuntu:~$ lspci -nnk | grep -iA2 net  
 00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)  
 	Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:9012]  
 	Kernel driver in use: 8139too  
 ron@ubuntu:~$ uname -a  
 Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux  
 ron@ubuntu:~$ lsusb  
 Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 ron@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17335  1  
 fat                    55505  1 vfat  
 usb_storage            43946  1  
 uas                    17676  0  
 binfmt_misc            13213  1  
 snd_via82xx            24685  2  
 nouveau               621970  3  
 gameport               15027  1 snd_via82xx  
 snd_ac97_codec        105614  1 snd_via82xx  
 ac97_bus               12642  1 snd_ac97_codec  
 snd_pcm                80244  2 snd_via82xx,snd_ac97_codec  
 snd_page_alloc         14073  2 snd_via82xx,snd_pcm  
 snd_mpu401_uart        13865  1 snd_via82xx  
 snd_seq_midi           13132  0  
 ttm                    65184  1 nouveau 
 snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi  
 drm_kms_helper         40745  1 nouveau 
 ppdev                  12849  0  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28659  2 snd_pcm,snd_seq  
 i2c_viapro             12969  0  
 drm                   180037  5 nouveau,ttm,drm_kms_helper  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 via_ircc               26953  0  
 irda                  185091  1 via_ircc  
 snd                    55295  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                73312  0  
 i2c_algo_bit           13184  1 nouveau 
 soundcore              12600  1 snd  
 serio_raw              12990  0  
 video                  18951  1 nouveau 
 crc_ccitt              12595  1 irda  
 parport_pc             32111  1  
 shpchp                 32345  0  
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 firewire_ohci          31504  0  
 usbhid                 41704  0  
 hid                    77084  1 usbhid  
 8139too                23208  0  
 pata_via               13368  1  
 8139cp                 22497  0  
 firewire_core          56138  1 firewire_ohci  
 floppy                 60032  0  
 crc_itu_t              12627  1 firewire_core  
 ron@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 ron@ubuntu:~$ rfkill list  
 ron@ubuntu:~$

---

### Post by wildmanne39 on 2011-11-12
Hi, did you have the usb adapter plugged in when you ran this command:
```
lsusb
```
I do not see your adapter if you need to shut down then plug it in and boot up, make sure the usb port that you have it plug into is working.

Please run the command again the output should look something like this.
```
 Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp.
```
Thank you

---

### Post by 6stringer on 2011-11-13
Well, I did not have the USB adapter plugged in when I ran the code. As soon as I installed the adapter the window popped up saying a wireless network was available. I have been able to connect to my secured wireless network but unable to get online. 

The Firefox browser will not connect to the web. As soon as I open it an "ALERT" box appears stating some sort of problem. I was about to try to do a print screen but the computer shut down so I obviously have more issues than just connecting to the web with this old machine.

---

### Post by wildmanne39 on 2011-11-13
Hi, I t looks like it, s far as the wireless issue, might be able to help with that after we see.
```
lsusb
```
with the adapter plugged in.
Thank you

---

### Post by 6stringer on 2011-11-13
Here is the CODE screenshot along with a couple extra showing that it is connected to my wireless network. Neither Firefox or Google will work even though pop up.


[attach]207143[/attach]

[attach]207144[/attach]

[attach]207145[/attach]

---

### Post by praseodym on 2011-11-14
Copy the firmware to the right place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
```
and replug the stick.

---

### Post by 6stringer on 2011-11-14
> **praseodym said:**
> Copy the firmware to the right place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
```and replug the stick.

Sorry to be so ignorant, but where do I copy this code?

Thank you for the help.

---

### Post by praseodym on 2011-11-14
Open a terminal with CTRL+ALT+T. After the first command you are asked for your PW without ******* or sth.

---

### Post by USC on 2012-09-17
> **praseodym said:**
> Open a terminal with CTRL+ALT+T. After the first command you are asked for your PW without ******* or sth.
I came here from Google because I had the same problem. Your solution solved it, thank you.

---


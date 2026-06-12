---
title: "Serial IR Blaster ??"
date: 2008-08-14
forum: Mythbuntu
---

### Post by rubrboots on 2008-08-14
I have been trying to setup my homebrew serial irblaster for about 2 days now, and cannot get it to work at all in Mythbuntu 8.04.1. This same transmitter works perfectly in Knoppmyth.

-I have followed instructions in the 8.04 manual, however it seems to be a cut and paste of 7.10 and does not work

-I then followed the instructions here;
 [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)
this page claims that the config wizard will allow you to choose the correct options. In reality there is no "serial transitter" option during configuration. This method has not got my blaster transmitting

-I then followed instructions posted bu 'ahood'in the follow forum;

[http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2](http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2)

These instructions got me the farthest but I can only irsend once then it all fails

```
boots@mythtvbe:~$ irsend -d /dev/lircd1 SEND_ONCE DCT2000 power
boots@mythtvbe:~$ irsend -d /dev/lircd1 SEND_ONCE DCT2000 power
irsend: could not connect to socket
irsend: Connection refused

```


Does anyone know of a guide or have the knowledge to make an upto date guide for setting up a serial irblaster in 8.04.1. It would be GREATLY appreciated.:)

---

### Post by ahood on 2008-08-14
Hi,

I too got this message many times before I figured out what I needed to do get this working.

How many serial ports do you have on the machine?

Are you confident that the contents of /etc/modprobe.d/lirc-serial is correct?

This was a key step for me and the information in this file may be unique for your particular machine.

Lastly, is lirc_driver running?

Al

---

### Post by rubrboots on 2008-08-15
The computer has 2 serial ports, but I am only trying to use 1. My etc/modprobe.d/lirc-serial file looks like this:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
```

I think this means that the lirc-serial is running

```
boots@mythbe:~$ dmesg | grep lirc
[  800.317994] lirc_dev: IR Remote Control driver registered, at major 61 
[  800.867367] lirc_serial: auto-detected active high receiver
[  800.867380] lirc_dev: lirc_register_plugin: sample_rate: 0

```


Not sure what to try now:confused::confused::confused:

---

### Post by ahood on 2008-08-15
> **rubrboots said:**
> The computer has 2 serial ports, but I am only trying to use 1. My etc/modprobe.d/lirc-serial file looks like this:

```
#COM1 equivalent, /dev/ttyS0
[COLOR="Red"]options lirc_serial irq=4 io=0x3f8[/COLOR]
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
```

I think the line is red above might be incorrect for your system. This line is the same as what I posted in my previous how-to post.

As you probably know, the line above must have the correct IRQ and IO value for the serial port your system has assigned to the port.

For me, I looked into the BIOS of my system and viewed the IRQ and IO assigned to the serial port.

This is not the only way to see if the system assigns an IRQ and IO address for the serial port.

Try the following command in a terminal and verify that the IRQ and IO address of the serial ports on your system...

> 
 dmesg /var/log | grep 16550A


The output will be something like...

> 
[   24.132216] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.132367] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.133090] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.133530] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A


Linux likes to report two serial ports (ttyS0 and ttyS1); however, I have only one that uses IO address 0x3f8 and irq of 4. 

Nevertheless, it will be useful to confirm if whether your system has assigned a different IO address and IRQ number for your serial ports.

Al

---

### Post by rubrboots on 2008-08-15
You Rock ahood!!! I had a look in my bios and the com port settings were reversed, so I switched them. I guess I could have just changed the modules file. Either way I can irsend now! Myth is not changing channels, I think there is a problem in the channel change script. Have to find some more time to look into that, but I think the problem is 99% solved:)

---

### Post by rubrboots on 2008-08-16
I will have to downgrade this problem to 75% solved. I have entered change_channel_script.pl in the external command box located in myth setup. It seems that the change_channel script works properly when I call the script in the terminal.

```
boots@mythbe:~$ change-channel-lirc.pl 12

```

It changes my STB to channel 12 perfectly, everytime. However when watching tv in myth the channel does not change at all. I must assume that myth is not calling the script or is calling it incorrectly. 

Is there a log of such calls that I can view, or edit the file responsible for calling the change_channel script?

---

### Post by rubrboots on 2008-08-16
Problem is now 100% Solved. It seems that my mythfrontend cannot call a pearl script, but can call simple bash script. Instead of using the suggested change-channel-lirc.pl perl script, I used the bash script change-channel-lirc.sh found here;
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)
Modified it for my remote, and it works very well now. :)

---

### Post by LarryJ2 on 2008-08-17
I'm using a StreamZap Remote with a serial blaster aimed at my dish net satellite receiver. This is what my modfified change channel script looks like:
```
lj@mythtv:~$ cat /usr/local/bin/change-channel-lirc.sh


#!/bin/sh

REMOTE_NAME=dish
cmd="$1"

case $cmd in
[0-9]*)
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 1
# If things work OK with sleep 1, try this for faster channel changes:
# sleep 0.3
done
;;

*)
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $cmd
;;
esac
```

---


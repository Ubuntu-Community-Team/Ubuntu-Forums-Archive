---
title: "Homebrew Serial LIRC Receiver HELP!!"
date: 2008-08-12
forum: Mythbuntu
---

### Post by rubrboots on 2008-08-12
I have a homebrew style LIRC serial receiver. I have been using this receiver for a couple years now with knoppmyth, and it works perfectly all the time. However, I have not been able to get it to work properly with mythbuntu 8.04.1. I have followed the hardy guide provided here;

[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

-I completed the steps that seemed necessary. I first ran
```

sudo dpkg-reconfigure lirc
```

and chose the homebrew uart remote and ttyS0

-then moved a copy of my pre-existing lircd.conf file to /etc/lirc/lircd.conf

-then moved a copy of my pre-existing lircrc file to /home/mythtv/.mythtv/lircrc

now when I run irw in the terminal and press buttons on my remote, I get the appropriate key responses in the terminal. But when I start the frontend there is no response to the remote at all.

Does anyone have any ideas to try here, or maybe known method to setup this type of device?

---

### Post by david_f1976 on 2008-08-13
Hi,

I just spent half a day last weekend trying to get my serial receiver working with 8.0.4.1. so I share your frustration.

Just a couple of thoughts.

First of all enter this as soon as you drop to a terminal after boot-up

dmesg | grep -i lirc

Post back the results

With the new version of MythTV it is only necessary to have your lirc file in one place. I don't think this is the cause of your problem but try it anyway. It should be named: ~/.lircrc

Also, have you used setserial to permanently disable the serial port. The instructions I used to modify were as follows (setserial might already be installed). Also I got a message after running the reconfigure command that this method is now deprecated, but this seemed to work for me:

First you will need the setserial utility to do this. 
$ sudo apt-get install setserial
Reconfigure setserial 
$ sudo dpkg-reconfigure setserial
Choose manual 
Modify /var/lib/setserial/autoserial.conf 
Add (or modify if its there already) (switch to ttyS1 if you're using that instead) 
/dev/ttyS0 uart none
Copy that script to /etc/serial.conf 
$ sudo cp /var/lib/setserial/autoserial.conf /etc/serial.conf

Hope this helps

---

### Post by rubrboots on 2008-08-13
Thanks, david_f1976. I copied my lircrc file to /home/USERNAME/.lircrc and it all works now.:)

---


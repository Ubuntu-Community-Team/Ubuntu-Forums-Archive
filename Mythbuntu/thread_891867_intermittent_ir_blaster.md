---
title: "intermittent ir blaster"
date: 2008-08-16
forum: Mythbuntu
---

### Post by jlips on 2008-08-16
I have never actually created a post before, although I have benefited tremendously over the years from others posts.  This problem has me stumped.

I had a P4 1.8 GHz dell that I was using with a pvr-350 to record analog programs.  This system was working great, but I wanted to start recording hdtv.  I upgraded to an P4 3.0 GHz processor on an intel D945PSN motherboard with a hdhomerun tuner.  Everything else in the mythbuntu setup is working great, except the serial ir blaster.  Both systems are running hardy. The weird thing is that it works on the new system but not reliably.  I've tried it with both the bash and perl change_channel script and played extensively with the sleep durations with no luck.  If I issue the irsend command from the command line to /dev/lircd1 it is only received some of the time.  And if I run a script to issue each digit, then digits are left out, if any register at all on the dish box.  If I put the ir blaster back on the old dell box it works fine.  I cannot figure out what is causing this erratic behavior.  

[LIST]
[*]I've placed the baster before the remote in /etc/lirc/lircd.conf
[*]There are no serial port settings in the bios that I can find.
[*]Checked /var/lib/setserial/autoserial.conf set to: /dev/ttyS0 uart none
[*]Checked irq and io values for ttyS0
[/LIST]

---

### Post by LarryJ2 on 2008-08-17
I understand that this command entered in a terminal window doesn't bring your dish receiver to CNN?
```
/usr/local/bin/change-channel-lirc.sh 200
```

If not, I wonder if the serial port in the new box has enough power to drive the blaster IR diode?  Is there any way you could temporarily install then try a serial PCI board?  Maybe borrow one from a friend or they are fairly inexpensive.

Your blaster has a connection to Pin 4 which then runs to a diode  then to a resistor ?  What's the value of the resistor? I read that this should be 1K or so. I also read somewhere that some of the blasters omit the resistor which might spell trouble. 

The signaling leads (DTR DSR) were never meant to power diodes so I could see where a different serial uart(ic chip) might have less power (current and voltage) capability. Perhaps that's the difference between Old Box and New Box.

Hope this helps.

Larry

---

### Post by jlips on 2008-08-17
Larry,

Thanks for the response and the ideas.  I will dig through my box of old pci cards and see if I can find an old serial port card.  If not, I'm sure they are cheap. Good idea.  I will post back with the results.

John

---

### Post by jlips on 2008-08-25
Well I finally got my hands on a pci serial port card.  Now I cannot get it to work.  It is recognized on boot (ttyS1):

lips@mythbox:~$ dmesg | grep tty
[   48.312948] console [tty0] enabled
[   50.148023] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   50.148755] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   50.149091] 0000:05:03.0: ttyS1 at I/O 0x1060 (irq = 19) is a 16550A
[  977.031675] audit(1219612143.539:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=16782 profile="/usr/sbin/cupsd" namespace="default"

I tried manually editing /etc/modprobe.d/lirc-serial to:

#COM1 equivalent, /dev/ttyS0
#options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
options lirc_serial irq=19 io=0x1060

after restarting lirc and also after rebooting, I kept getting entries in dmesg that the irq was in use.

I did sudo dpkg-reconfigure lirc and selected ttyS1, but all this did was set /etc/modprobe.d/lirc-serial to the default irq and io values:

#COM1 equivalent, /dev/ttyS0
#options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
options lirc_serial irq=3 io=0x2f8

Any ideas would be greatly appreciated.  I will look for the resistor value.

---

### Post by LarryJ2 on 2008-08-25
Have you followed the steps detailed by rubrboots here:

[http://ubuntuforums.org/showthread.php?t=893697&highlight=lirc+blaster](http://ubuntuforums.org/showthread.php?t=893697&highlight=lirc+blaster)

I only had to make a couple of changes to his instructions.  Mine was a Dish Receiver and his was a Motorola STB, for example.

But I did work on this for three solid days before I finally got it working!

Larry

---


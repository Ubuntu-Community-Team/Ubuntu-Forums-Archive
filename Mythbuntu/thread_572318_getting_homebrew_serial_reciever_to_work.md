---
title: "getting homebrew serial reciever to work?"
date: 2007-10-10
forum: Mythbuntu
---

### Post by mr_bungalow on 2007-10-10
I followed the guides over at [https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy) and I can't seem to get this to work.  Every time I try to do IRW I get
```
connect: connection refused
```.  
When I restart lircd nothing even populates in my dmesg.  I think I'm close but I'm not sure where to go from here!  I think I need kernel modules (?).

---

### Post by superm1 on 2007-10-10
When LIRC was installed, did you choose the proper option for the serial receiver?

If not (or your not sure), then do this:

sudo dpkg-reconfigure lirc

Choose the serial receiver option (or the serial igor variant if you have an igor receiver built).


Since you are using your own remote configuration to go with the receiver, copy it into the /etc/lirc/lircd.conf file already there.  

Open up mythbuntu control centre, and hit the checkbox to regenerate a dynamic button mappings.

---

### Post by mr_bungalow on 2007-10-10
I need LIRC (IRW or mode2) to work in order to create my own .lircd file.  I did select the proper option to load the serial receiver.   

In mythbuntu control center, I only have the option to select a remote and mine isn't available.  When I try to select a remote, there is none that require no driver and the lirc_serial module.

For some reason SSH isn't working today so I'll try this when I get home over lunch.

---

### Post by dannyboy79 on 2007-10-10
if you don't have a lircd.conf than you need to use irrecord first to create one. irw parses your lircd.conf so if it's not there, I am guessing that it's making lircd crash. After you run irw, and you get the error. What happens if you issue this command:
ps aux | grep lirc
Does it return a line like this:
root      5365  0.0  0.0   2876   576 ?        Ss   Oct05   0:00 /usr/sbin/lircd --device=/dev/lirc0 --device=/dev/lirc0

If not, than your lircd crashed and closed. 

Just chose none for now with mythbuntu and we'll create your lircd.conf remote file outside of mythbuntu control setup. Some other things to check just in case, my serial port is COM1 where I have seen many guides that say the default is COM2. You can find this by looking at your dmesg output using this command:
dmesg | grep ttyS
If it returns this:
[    1.521568] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.522180] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Than that means that your serial receiver is connected to COM1 NOT COM2.
Also, if you're using the serial IR receiver, you'll need to disable the kernel serial support, See the wiki towards the bottom.

Then see lower on the website you linked to and follow the part: "Recording a Remote" This requires that NO other lircd is active, so if it's on, kill it using ps aux and kill the program id using "sudo kill xxxx". then follow the guide for creating a remote.

Good luck

---

### Post by mr_bungalow on 2007-10-10
Thanks for the tips!! I figured out that everything was working but I needed to specify the -d in irrecord to point to lirc0 instead of lirc or ttys0.  Once again, mythbuntu has amazed me!

---

### Post by dannyboy79 on 2007-10-10
I forgot I was going to write that also except I didn't even know about the -d switch, I just created a symlink for /dev/lirc to point to /dev/lirc0. Not sure which is a better solution but most likely NOT mine as another symlink isn't the best thing. Good catch and glad you got it working. Mythbuntu has amazed me also!!

---

### Post by latev on 2008-10-27
Hey guys, mind if I use your help for getting my Igor IR receiver to work under Ubuntu x64?
I've managed to get the lirc installed properly /I think/, the modules are in the kernel /lirc_serial_igor/ and seems like my IR is detected properly. However I don't seem to be receiving any input from my remote after I issue
cat /dev/lirc0

Any suggestions?

---

### Post by Murz on 2009-06-07
> **latev said:**
> Hey guys, mind if I use your help for getting my Igor IR receiver to work under Ubuntu x64?
I've managed to get the lirc installed properly /I think/, the modules are in the kernel /lirc_serial_igor/ and seems like my IR is detected properly. However I don't seem to be receiving any input from my remote after I issue
cat /dev/lirc0

Any suggestions?
Same problem on Kubuntu Jaunty amd64 and Igor Cesko's serial IR receiver (on 1 and 2 COM port). This receiver works good with Girder 3.2 and IgorXP.dll, but didn't work on lirc!

```
$ lircd -v
lircd 0.8.4a

$ ls /dev/lirc*
/dev/lirc0  /dev/lircd

$ lsmod | grep lirc
lirc_serial_igor       23336  0
lirc_dev               22088  1 lirc_serial_igor

$ cat /etc/lirc/hardware.conf | grep -v ^# | grep -v ^$
REMOTE="Home-brew (Igor Cesko's variant)(16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial_igor"
REMOTE_DRIVER=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
REMOTE_DEVICE="/dev/lirc0"

```

When I start "irw"  or "mode2 -d /dev/lirc0" and press some keys on IR transmitter, I see no output.
How can I turn on more debug level for get additional info where is the problem? How I can sniff an input signals on com port (/dev/ttyS0)?

---

### Post by SiHa on 2009-06-08
Did you disable the kernel serial support?

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy), search for **setserial**

---

### Post by Murz on 2009-06-10
> **SiHa said:**
> Did you disable the kernel serial support?

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy), search for **setserial**

Yes, I disable it (all, ttyS0 and ttyS1) and restart lirc, but it isn't help. What can I try else?

---

### Post by SiHa on 2009-06-10
Assuming you've rebooted since, then I don't know, sorry.

Did you```
sudo dpkg-reconfigure lirc

```?

That's all I had to do on both my systems to get the homebrew working properly.

One thing - you won't get anything from irw until you have a valid lircd.conf.

Have you tried irrecord to create a new one?

---

### Post by Murz on 2009-06-11
Yahoo!!! It goes to work when I reconnect device from COM2 to COM1 port! Before this I try to "dpkg-reconfigure lirc" and select correct COM number, IRQ and IO, but lirc_serial didn't receive info from the device!
Also I try to download a LIRC source from the official site and compile manually for COM2 and Igor Cesko, but it isn't help.
After reconnecting to COM1 and recompile lirc manually to COM1 all goes to work!
The bug in LIRC tracker about this is here: [http://sourceforge.net/tracker/?func=detail&aid=2804371&group_id=5444&atid=105444](http://sourceforge.net/tracker/?func=detail&aid=2804371&group_id=5444&atid=105444)

---

### Post by ilium007 on 2010-05-16
Hi guys - I know this is an old thread but I used it with some success in getting LIRC working with my homebrew serial receiver. It was a big relief to finally see output in both mode2 and irw. Problem now is that my success was shortlived in that it did not work again after a reboot. Do I have to run ```
 setserial /dev/ttyS0 uart none
``` each time I restart the machine ?? I am not sure what else could be wrong (I have not tried this as yet as I am away from the myth box). I know that lirc has not taken over the COM port as I am still getting a -ve 10v on pin 7 of the COM port. When I tried a ```
sudo /etc/init.d/lirc restart
``` I get an error stating that lircd could not load modules and to check my hardware.conf file. That file did not change between reboots so I am not sure what has happened.

Any help would be appreciated.

---

### Post by ian dobson on 2010-05-17
Hi,

Have a look here [http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf) chapter 12, you need to copy the configuration file generated by setserial to /etc

sudo cp /var/lib/setserial/autoserial.conf /etc/serial.conf

Regards
Ian Dobson

---

### Post by ilium007 on 2010-05-18
All works now as expected. Thanks for the replies.

However.... Mythbuntu Control Centre is now broken in that and change to any other settings (ie. Plugins, Services etc) causes the lirc hardware.conf file to be erased. Bug logged:

[https://bugs.launchpad.net/mythbuntu/+bug/582617](https://bugs.launchpad.net/mythbuntu/+bug/582617)

---

### Post by brian_hammerhead on 2010-05-23
> **ilium007 said:**
> All works now as expected. Thanks for the replies.

However.... Mythbuntu Control Centre is now broken in that and change to any other settings (ie. Plugins, Services etc) causes the lirc hardware.conf file to be erased. Bug logged:

[https://bugs.launchpad.net/mythbuntu/+bug/582617](https://bugs.launchpad.net/mythbuntu/+bug/582617)


Same problem here.  I had my (not on the list) remote control working wonderfully with my HDHomerun box.  HDHomerun has an IR Receiver and sends the signal over the network to MythTV.  For those that care, I modified:

/etc/lirc/hardware.conf
REMOTE_LIRCD_ARGS="-H udp -d 5000" 

This allows Mythbuntu to receive the remote signals over the network from HDHomerun.

When I tried to configure VLC via the Mythbuntu Control Centre, my remote no longer functioned.

I hope the bug is fixed so that others don't have the same problem.

---

### Post by ilium007 on 2010-05-23
Can I get you to add a bug here :

[https://bugs.launchpad.net/mythbuntu/+bug/582617](https://bugs.launchpad.net/mythbuntu/+bug/582617)

might help it get fixed.

---


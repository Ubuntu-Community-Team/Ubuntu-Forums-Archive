---
title: "LIRC and Custom Serial IR Blaster Not Working (Re-posting)"
date: 2008-08-18
forum: Mythbuntu
---

### Post by Eric Boring on 2008-08-18
Hello everyone. 
I originally posted this in hardware, but I received no responses. So I'm hoping you all might have some insight here.

I am trying to get a custom-built Serial IR Blaster to transmit, but I have hit a road block. I've searched around and tried a lot, and now I am just plain confused. 


I'm running mythbuntu 8.04 on this machine.

Here is what I can tell you:

If I run lsmod, I get this:

```

josh@frankendevo:~$ lsmod | grep lirc_serial
lirc_serial            16276  0 
lirc_dev               15860  2 lirc_serial,lirc_i2c

```

As far as I can tell, this seems like it should work. But when I test the device, no joy. (I've tried just using it to change channels on the set-top box, and I've tried viewing the transmitter through a digital camera.)

I started following the instructions here: [http://www.mythtv.org/wiki/index.php/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/index.php/Ubuntu_Serial_Lirc_Install)

So I install these packages:
```
josh@frankendevo:~$ sudo apt-get install lirc lirc-modules-source module-assistant
```

But when I run the reconfigure command, here is what happens:
```
josh@frankendevo:~$ sudo dpkg-reconfigure lirc-modules-source
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

```

But I never see a configuration dialog. Then when I try to edit /etc/lirc/lirc-modules-source.conf there is a file there, but it is blank.

Any idea how I can get that configuration dialog to show for me?

Thanks!

-Eric

---

### Post by nickrout on 2008-08-18
is the serial port already snaffled by the ordinary serial driver?

---

### Post by Eric Boring on 2008-08-18
thanks for the reply. how would I check that on the serial port? This is the first time I've used serial ports on Ubuntu (or any other computer for that matter.)

-E

---

### Post by rubrboots on 2008-08-18
Hey Eric
I just finished setting up my homebrew serial irblaster, and it works very well. If your using mythbuntu 8.04.1 you should not need to install any lirc or setserial items, as they are already installed. Here is a very brief summary of how I got mine working. I plan on creating a detailed set of instructions, hopefully I can get that done soon.

1-follow instructions below 12.2.1 in the mythbuntu installation guide [http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)
- do not choose serial receiver as stated, but choose none for receiver and choose a transmitter like "Serial Port(uart):YOURCABLEBOXBRAND"

- The /etc/modprobe.d/lirc file should also already exist, but check in you BIOS that COM1 is irq=4 and io-0x3f8. It is probably not, so uncomment the appropriate line in file or change the info in your BIOS.

-skip the install setserial step, as it has already been installed, but do complete all the other steps under 12.2.1

2 -I am going to assume that you have a motorola cable box as I did, so change your brand as necessary.

- If the file located at /usr/share/lirc/transmitters/motorola/dctxxx.conf, is not the same as your lircd.conf file the copy yout lircd.conf file over the dctxxx.conf file. Then copy the dctxxx.conf file to /etc/lirc/lircd.conf

3 - Edit TRANSMITTER portion of your /etc/lirc/hardware.conf file so that it looks like this

#Chosen IR Transmitter
TRANSMITTER=**[COLOR="Red"]"DCT2000"[/COLOR]**
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lircd"
TRANSMITTER_LIRCD_CONF=[COLOR="Red"]**"motorola/dctxxxx.conf"**[/COLOR]
TRANSMITTER_LIRCD_ARGS=""

-make sure the DCT2000 is replaced with the name of your remote listed in your lircd.conf file. And that motorola/dctxxx.conf is replaced with the path to the appropriate file

4-create a file called /usr/local/bin/change-channel-lirc.sh

with the following info

```
#!/bin/bash
REMOTE_NAME=[COLOR="Red"]DCT2000[/COLOR]
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
```

- then make it executable
```
sudo cp change-channel-lirc.sh /usr/local/bin/change-channel-lirc.sh
```

5-restart lirc
```
sudo /etc/init.d/lirc restart
``` 

test in terminal with 

```
irsend --device=/dev/lircd SEND_ONCE [COLOR="Red"]YOUR_REMOTE_NAME[/COLOR] 2
```

if you also have a remote some small changes must be made, but I would get the transmitter working first before adding a remote. I found most of this info from this post check it out.
[http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2](http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2)


***These are VERY sloppy instructions, so just let me know if anything is unclear, and I will try to explain it better.***

---

### Post by Eric Boring on 2008-08-18
Thanks alot for the reply.

> **rubrboots said:**
> 
1-follow instructions below 12.2.1 in the mythbuntu installation guide [http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)
- do not choose serial receiver as stated, but choose none for receiver and choose a transmitter like "Serial Port(uart):YOURCABLEBOXBRAND"


I've tried choosing one of the brands in the dialog here, and that at least prompts me to choose a COM port, but I'm using a set top box that is not included in the list, so then I have to go back into that config file and manually enter the info for my box.

I am going to print up the section on LIRC from the manual and try to start fresh with that. Thanks!

---

### Post by rubrboots on 2008-08-18
I dont think it really matters if your box brands is in the list, the lirc reconfigure just helps you set up the hardware.conf file.In that case just choose serial (uart):motorola, then copy your actual lircd.conf file to /usr/share/lirc/transmitters/motorola/dctxxx.conf and copy is to /etc/lirc/lircd.conf as well.And of course edit all the REMOTENAMEs to the name in your lircd.conf file.

---

### Post by jetsurgeon on 2008-08-19
tag

---

### Post by Eric Boring on 2008-08-19
Ok, so I went through the LIRC transmitter instructions in the manual, and I'm still not getting through. I still don't seem to be able to actual run dpkg-reconfigure lirc-modules-source. I googles around, and this looks like it may be a bug. I tried downloading and building the newer lirc modules, but that did not work either. 

I'm wondering if I should bite the bullet and spring for a USB Command IR box. Short of that is there a way to completely remove all my LIRC and all of the config stuff I've borked up to start over with LIRC? Or should I just start with a clean install of Mythbuntu alltogether?

Thanks

---

### Post by rubrboots on 2008-08-19
Dont run dpkg-reconfigure lirc-modules-source

run this

```
sudo dpkg-reconfigure lirc
```

Personally I would start with a fresh install of mythbuntu 8.04.1, I would not waste time setting up much else in the clean install until you have a successful lirc setup.

---

### Post by Eric Boring on 2008-08-19
> **rubrboots said:**
> Dont run dpkg-reconfigure lirc-modules-source

run this

```
sudo dpkg-reconfigure lirc
```


I have run that, and selected the custom serial transmittet, then COM 1. (which i checked in BIOS). Nothing.

> 
Personally I would start with a fresh install of mythbuntu 8.04.1, I would not waste time setting up much else in the clean install until you have a successful lirc setup.

That sounds like pretty good advice. I might just take my birthday money and spring for the Command IR usb box. I'm tired of serial!

Thanks for the help. I'll let you know how it goes.

---

### Post by Eric Boring on 2008-09-11
Well, I wanted to update this thread in case it helps someone else out.

I did get everything working, but I had to abandon my serial IR blaster. I bough the CommandIR mini (~$100). Which makes the IR transmitter the most expensive piece of equipment on this rig (except the hard drive).

But it worked great, once i reinstalled the OS. I had pretty well messed up my LIRC stuff by dorking around with it for several weeks. So I reinstalled and the CommandIR Mini works like a champ. 

For those who are interested in config files and scripts. I have the APEX Digital 250 digital converter box ($20 with the Govt. Coupon at Best Buy). I had some difficulty finding the codes for this, but finally did find that at the IguanaWorks site. 

[http://iguanaworks.net/projects/IguanaIR/attachment/ticket/107/ApexDigitalDT250Remote.conf](http://iguanaworks.net/projects/IguanaIR/attachment/ticket/107/ApexDigitalDT250Remote.conf)

So I put the above .conf file in /usr/share/lirc/transmitters/apex/ then I added a link to it in the /etc/lircd.conf by putting this line at the bottom of that file:

```
#Configuration for the Custom transmitter:
include /usr/share/lirc/transmitters/apex/Apex.conf
```

One thing I did was to rename the file to just Apex.conf, since this makes it easier to type.

And I messed around with a couple of channel change scripts. THis one finally worked. If you want to specify which of the 4 emmitters to use, you have to add few lines, available from the CommandIR site. I haven't bothered with that yet, since I'm only controlling the set top box. Anyways, here is the change script:

```
REMOTE_NAME=ApexDigitalDT250Remote
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
```

Naturally, you'd replace "ApexDigitalDT250Remote" with the name for the transmitter you need to emulate:

So, again, for anyone who is struggling with this, as I understand it, this is how the whole things works:

[LIST]
[*]/etc/lircd.conf tells the system where the config files are for your remotes and transmitters.
[*]ApexDigitalDT250Remote.conf tells lirc what to transmit through the emitter to change channels on your set-top box. 
[*]The change script tells mythtv to run that script instead of changing channels on the tuner.
[*]When you enter the path to a channel change script in mythtv-setup mythtv automatically uses that script.
[/LIST]

Anyways, long story longer, the whole thing is working great. I've got TV and X running through the PVR350's video out. I can ssh into the system to make tweaks and changes. I've got Mythweb running and I've even managed to connect with both a Mythbuntu frontend and with the Windows Mythtv Player. Oh, and the whole thing is running on an old celeron 766Mhz system. I love recycling.

-Eric

---


---
title: "Hauppauge PVR-150 infrared and lirc"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by mvsjes2 on 2006-10-03
I've spent a couple of days trying to get my infrared remote control working for my hauppauge PVR-150. I'm a relative newby to linux.

From what I can see, the Kubuntu Dapper kernel isn't recognizing the IR input at boot-up:
sh-3.1$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I don't see any Hauppauge there. It does recognize the capture portion of the card since I successfully installed ivtv and myth and got all that working. It's just the dern remote.

All the how-to's simply assume the IR was detected and shows up in the above display. They say support for this input was installed in the kernel in 2.6.12. They don't explain what to do if it's not detected.

Do I have to enable something in the kernel for it to detect the device? Should it have shown up in the above display on a regular Dapper install? Can someone point me in the right direction?

Using Kubuntu 6.06 kernel 2.6.15-27-386.

Thanks!

---

### Post by gavinb on 2006-10-09
Hi just got mythtv and lirc to work with my pvr-150.  Maybe I can help you.  What version of mythtv are you using?  Did you install it from source or with apt-get?   

Try starting with this 
[http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper](http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper)

I had to tweak this guide to get it work with mine.

Brian

---

### Post by mvsjes2 on 2006-10-10
Hi Brian, glad to hear you have it working.

I'm following the instructions you noted, as well as a couple of other references:
[http://www.ivtvdriver.org/index.php/Howto:Ubuntu]("http://www.ivtvdriver.org/index.php/Howto:Ubuntu")
[http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation")
[http://mythtv.org/pipermail/mythtv-users/2006-September/148085.html]("http://mythtv.org/pipermail/mythtv-users/2006-September/148085.html")
[http://www.mythtv.org/pipermail/mythtv-users/2006-January/117562.html]("http://www.mythtv.org/pipermail/mythtv-users/2006-January/117562.html")

Would you mind posting your /proc/bus/input/devices? I'd like to see what it's *supposed* to look like. I'm assuming your kernel detected the IR part of the card. Do you know if it was detected before you installed ivtv?

---

### Post by mvsjes2 on 2006-10-10
To answer your question, I'm installing myth 0.20 from packages in the apt sources noted in the above links.

---

### Post by gavinb on 2006-10-10
I am not an expert either, but lirc needs to have working ivtv drivers first which it sounds like you have.  I am not near my computer but I can post my results later today or tomorrow.  I am using the same kernel version as you are with Ubuntu.  

**If you type ls -l /dev/lirc* what do you see?**

**Could you try this? (this will load the your lirc drivers)**

sudo depmod -a
sudo modprobe lirc_i2c

dmesg | grep lirc

**You should see something like this:**
lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
 ivtv0: i2c attach to card #0 ok [client=Hauppauge IR (PVR150), addr=71]
 lirc_dev: lirc_register_plugin: sample_rate: 10

**If this works then try this:**
peek2
Press some remote control buttons and you should text appearing on your console.

**and if that works try this:**
sudo lircd
irw

Press the buttons on your remote and text should appear in your console.

**and if that works start up mythtv and see if the remote is working.**


Also look at the output of the dmesg command for error messages regarding ivtv or lirc.

Brian

---

### Post by gavinb on 2006-10-10
PS

If all of the steps work then I can show you how to install the lirc drivers at boot, but I first want to make sure the driver is working.

Brian

---

### Post by mvsjes2 on 2006-10-10
ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2006-10-10 11:23 /dev/lirc0
srw-rw-rw- 1 root root     0 2006-10-10 12:33 /dev/lircd

lirc_dev: IR Remote Control driver registered, at major 61
[17179596.308000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179596.408000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179596.408000] ivtv0: i2c attach to card #0 ok [client=Hauppauge IR (PVR150), addr=71]
[17179596.408000] lirc_dev: lirc_register_plugin: sample_rate: 10

I did a locate on peek2 and it's not found on my system.

lircd fails to start right now, although I had it working before. I'm going to reboot and try again, and update this.

See you in a few minutes, and thanks for your help!

---

### Post by mvsjes2 on 2006-10-10
lircd comes up with no errors, then I start irw which immediately ends with no errors, then I look and find lircd no longer running, again no errors.

Sigh.

I know for sure this part worked no too long ago. I'm not sure how I broke it.

---

### Post by gavinb on 2006-10-10
I think you are pretty close to getting it running.

based on your dmesg output I think you have the lirc driver installed correctly. There is a script that runs at startup for lircd. It is probably looking either for /dev/lirc or /dev/lirc/0.

Yours is at /dev/lirc0 just like mine is.
Try this.

ps -e
find the process id for lircd and kill the process
sudo kill xxxx

then restart lircd with the correct device path
sudo lircd -d /dev/lirc0
irw
press your remote control buttons

if that does not work kill the lircd process and try this
sudo ln -s /dev/lirc0 /dev/lirc
sudo lircd
irw

If this works try mythtv

Most likely the your startup skip is wrong. Somewhere you probably ran something like
sudo update-rc.d lircd .....
look at the lircd script file in a text editor and see if if it is looking for /dev/lirc or /dev/lirc/0 and change it to /dev/lirc0
then rerun update-rc.d with the new file.

When I get access to my computer I will post my startup script.

---

### Post by mvsjes2 on 2006-10-10
Hi Brian,

Much closer. If I manually start lircd with -d /dev/lirc0 and then start irw everything works. If I run /etc/init.d/lirc start it doesn't. I've messed around with the hardware.conf to add in -d /dev/lirc0 and set DEVICE="/dev/lirc0", but no joy. There's something obviously wrong with my hardware.conf but I've been staring at it so long I don't see it.

##############################
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=" -d /dev/lirc0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
##########################

You referred to your startup script. I'm assuming it's the one in /etc/init.d/lirc. I looked at it and it loops through three possible devices looking for an input device, one of them being /dev/lirc0, so I'm not sure why it's not working.

---

### Post by gavinb on 2006-10-10
I am not expert so I am not really familar with hardware.conf.

I use the file /etc/init.d/lirc to start it.  On my computer 'lirc' looks like this.

> #!/bin/sh


case "$1" in 'start')
	 /usr/local/sbin/lircd --device=/dev/lirc0 			
	RETVAL=$?
	 ;; 
'stop') 
	killall lircd 
	RETVAL=$? 
	;; 
esac 
exit $RETVAL

Your path for lircd might be different, and you might want to try running it in the console/shell first.

Then type
> sudo chmod +x /etc/init.d/lirc
sudo update-rc.d lirc defaults 99


Then cross your fingers and reboot.  I hope this works because that is all I know.  It has to relate to the /dev/lirc0.

Good Luck

---

### Post by mvsjes2 on 2006-10-11
The remote works in Myth if I start lircd manually with -d /dev/lirc0.

I'm soooo close...

---

### Post by mvsjes2 on 2006-10-11
I found the problem. /etc/init.d/lirc starts /usr/sbin/lircd, which doesn't work. When I just enter 'lircd' it loads it from /usr/local/sbin/lircd, which works.

I wonder how I got two versions of the daemon and what the difference is?

Thanks for your help!

---

### Post by mvsjes2 on 2006-10-11
For the record, it appears that you don't have to install the lirc package if you download the source - logical, but many sites say to install the lirc package, then compile the source. It appears this is why I had two versions installed.

---

### Post by emnaki on 2006-12-02
My problem is similar, when I run:
```
/usr/local/sbin/lircd --driver=dvico --device=/dev/hiddev0
```
it works. But when I add this line to my rc.local it does not work, does anyone know why?

---


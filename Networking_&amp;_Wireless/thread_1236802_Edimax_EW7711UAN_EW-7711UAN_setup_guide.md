---
title: "Edimax EW7711UAN EW-7711UAN setup guide"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by yipmhw on 2009-08-10
Edimax EW-7711UAN Installation Guide

1) Download the most updated Ralink driver from:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

2) Bring up the terminal (shell) from the Applications menu

3) Unzip the package
4) cd into the extracted directory
5) cd to /os/linux
6) open the config.mk file in a type editor of your choice
7) Locate and modify these:

From:-

HAS_WPA_SUPPLICANT = n

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n

to

HAS_WPA_SUPPLICANT = y

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

8) Save and exit
9) cd back to the root of the extracted directory
10) Type 'make' in the terminal and if no errors, then type 'sudo make install'
11) cd back to /os/linux/ and type the following:

sudo insmod rtxxxxsta.ko

NOTE: to have this driver automatically loaded on every boot add the name of the driver in the format of 'rtxxxxsta'
to  /etc/modules. This can be done as follows:

sudo gedit /etc/modules

and add:

rt3070sta 

to the end of file.

12) This is the end of the set up (however, journery didn't end here for me)

Diagnosis:

sudo ifconfig ra0 up and see if it's up

Also check for errors using:

dmesg
tail /var/log/messages

Still can't connect?

Possible reason:
Q1) You have two or more wifi adapters and you can't turn ALL of them on?
Q2) Does Network Manager say your Wifi adapter is 'device not managed'?
Q3) Perhaps the wrong driver?

A1) A possible solution is to install wicd, an alternative network manager to the default one.

To install wicd, type the following in the terminal:

sudo apt-get install wicd

Please google around for configuration but wicd does the job very well.

A2) Type the following:
sudo gedit /etc/NetworkManager/nm-system-settings.conf

and modify:

From:-
[ifupdown]
managed=false

To:-
[ifupdown]
managed=true

A3) Err best bet is to google around and good luck!

NOTE: I've tried Wifi-Radar and it was unstable and SLOW (so slow Ubuntu couldn't even download packages)

Recommended links:

[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
[http://ubuntuforums.org/showthread.php?t=1152407](http://ubuntuforums.org/showthread.php?t=1152407)
[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

This is version one of the guide so there may be mistakes, please be patient. Feedbacks welcome!

---

### Post by nesimi on 2009-12-12
Hello there,
I have been using Kubuntu 9.10 since its release. I have tried several things but couldnt be successful with the Edimax EW7711UAN driver. I was using this dongle on Kubuntu 9.04. This newer kernel (2.6.31.16) is something different. Could you please help me with this driver. I am writing down outputs of some commands that describe my configuration.

```
homeless@nesimi:~$ lsusb
Bus 001 Device 002: ID 7392:7711
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
homeless@nesimi:~$
```

```
homeless@nesimi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

homeless@nesimi:~$
```

```
homeless@nesimi:~$ lsmod
Module                  Size  Used by
ppdev                   6688  0
snd_via82xx            23576  3
gameport               11368  1 snd_via82xx
snd_mpu401_uart         6940  1 snd_via82xx
iptable_filter          3100  0
snd_seq_dummy           2656  0
snd_via82xx_modem      11204  0
snd_ac97_codec        101216  2 snd_via82xx,snd_via82xx_modem
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
nvidia               9586440  40
i2c_viapro              7312  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
k8temp                  4188  0
snd                    59204  18 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_via82xx,snd_via82xx_modem,snd_pcm
psmouse                56500  0
serio_raw               5280  0
shpchp                 32272  0
rt3070sta             510208  1
lp                      8964  0
parport                35340  2 ppdev,lp
floppy                 54916  0
skge                   39180  0
sata_via                9184  2
amd64_agp               9796  1
agpgart                34988  2 nvidia,amd64_agp
homeless@nesimi:~$
```

---

### Post by c-shadow on 2009-12-15
This setup guide worked for me, driver compiled and working fine in intrepid, kernel 2.6.27-16-generic. It seems it's included in karmic, have dual boot with 9.10 and it's working out of the box there (didn't test it much).
My bad was trying to build the wrong driver :)
As described in this thread.
[http://ubuntuforums.org/showthread.php?t=1267266](http://ubuntuforums.org/showthread.php?t=1267266)

---

### Post by brownb2 on 2010-01-02
Okay the drivers have moved to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and for the EW-7711UAN you need to use the [RT3070USB(RT307x)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV4THpJd0wyUnZkMjVzYjJGa01EVTRNalU1TlRjek1DNWllakk5UFQweU1EQTVYekV4TVRCZlVsUXpNRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNHhMakl1TUM1MFlYST1D") link. I wouldn't recommend the driver source you get on the CD!

Once the instructions above have been followed above it will expect some firmware in /etc/Wireless/RT2870STA/RT2870STA.dat or the module will fail to start (usually you can tell by the rapid flickering of the led on the device itself that its not working correctly). See the exact error by typing at the prompt:

'dmesg'

The last few lines will usually show the error. Don't ask why its trying to load the 2870STA model firmware - I have no idea.... but I suspect someone was lazy and hasn't renamed.

Now somebody can probably correct the guide above here for the correct Ubuntu driver firmware folder this should be in (and thus the code amendments that would have to have been made to the source too) but for now to get you up and running type:

'sudo mkdir /etc/Wireless/RT2870STA'

followed by (from the root of the extracted directory)

'sudo cp ./RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat'

Now just reboot and the magic should start happening.

One thing I noticed was that although the wireless connection to a router is immediate, updating the routing tables seems not to be as instantaneous (taking about 5-10 seconds before you can open up a web browser for example), although this may be just my weird 64 bit Ubuntu setup - YMMV, it didn't happen with my old wireless adapter. The device that shows up in using 'ifconfig' is "ra0" if anyone is interested, not wlan0 or similar. This was compiled against the 2.6.27-16-generic kernel *without any problems.*

---

### Post by c-shadow on 2010-01-03
After using the driver for some time I noticed some problems:

1. It's filling my system logs with debugging data like 
```
===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 197
```. To get rid of this, I opened os/linux/sta_ioctl.c with text editor, founnd the line that says:
```
DBGPRINT(RT_DEBUG_ERROR ,("===>rt_ioctl_giwscan. %d(%d) BSS returned, data->length = %d\n",i , pAdapter->ScanTab.BssNr, data->length));
``` and commented it by putting // in front, like this:
```
//	DBGPRINT(RT_DEBUG_ERROR ,("===>rt_ioctl_giwscan. %d(%d) BSS returned, data->length = %d\n",i , pAdapter->ScanTab.BssNr, data->length));
```
Recompiled the module and no more logs full of crap.

2. My adapter does not work stable. It's fine for a 2-3 days uptime and then it just stops working. Unplug/plug method works fine, and sometimes also bringing the adapter down via ifconfig and reloading the module. Sometimes only unplugging the adapter helps which makes me think it's mybe a hw problem...
Tried blacklisting/removing all the modules in karmic with 2.6.31-16 kernel and compiling this driver and the same thing happens there.

3. For some reason ndiswrapper didn't work for me. Installed the driver via ndisgtk but it says "unable to see if hardware is present".

Anyone else having stability problems with rt3070sta module?

---

### Post by ThomasLi on 2010-01-22
Driver rt3070sta version 2.1.2.0 keeps on writing lines containing only an "#" into system log.

Locate file and line of code that performs the writing:
```

grep -r '"#' 2009_1110_RT3070_Linux_STA_v2.1.2.0
2009_1110_RT3070_Linux_STA_v2.1.2.0/include/iface/rtmp_usb.h:#endif // end of "#if LINUX_VERSION_CODE < KERNEL_VERSION(2,5,0)" //
2009_1110_RT3070_Linux_STA_v2.1.2.0/common/rtmp_init.c:                DBGPRINT(RT_DEBUG_TRACE, ("#"));
2009_1110_RT3070_Linux_STA_v2.1.2.0/common/rtusb_io.c:                DBGPRINT(RT_DEBUG_OFF, ("#\n"));
2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/rt_linux.c:    printk("###Clone###\n");

```Go to the directory where file rtusb_io.c is located:
```
cd 2009_1110_RT3070_Linux_STA_v2.1.2.0/common
```To remove the writing into log, edit file rtusb_io.c according to option 1 or option 2:

1. Open file rtusb_io.c in your favorite editor, comment out the line and save the file.

2. You can also do the editing of the file by running the following command sequence I made when I was playing around with regular expressions:

Rename file before editing:
```
mv rtusb_io.c rtusb_io.c.old
```Substitute line containing "# with two slashes (comment syntax) and original line:
```
sed 's!.*"#.*!//&!' rtusb_io.c.old > rtusb_io.c
```Check that you achieved what you intended:
```
diff rtusb_io.c rtusb_io.c.old
```Yes, c-shadow, I confirm the stability problems.

---

### Post by brownb2 on 2010-02-03
To be honest I'm not surprised at the problems with the driver - I did a kernel build the other day with the early/built in version of this driver and it seemed that this driver compared to all others had the most compile warnings I'd (ever) seen. The sloppy logging in the source code is probably just the tip of the iceberg - I'd watch your memory usage too...

---

### Post by k@N on 2010-11-29
hello everyone!

first of all many thanx to anyone that contributed to this post.

I bought this device and i am stuck at the 11th step

when typing sudo insmod rt3370sta.ko

i am getting a message :

insmod: error inserting 'rt3370sta.ko': -1 Device or resource busy 

so i wasnt able to complete it and make it work

does anyone knows how to solve this

thanx anyone in advance

my questions might be stupid but i am stuck and need some help from the forum! ;)


ps also when i type insmod rt3370sta.ko , ie without sudo i recieve a message:

insmod: error inserting 'rt3370sta.ko': -1 Operation not permitted

---

### Post by rajn on 2011-02-01
Hi,
I have Lucid Lynx 10.04 LTS.
I tried to follow the above guide but I have several issues.

1. I have  a Edimax CD. However, I tried downloading the drivers from the website of Ralink but when I downloaded the necessary files it looks like tar file is corrupted. My archive manager cannot open it and gives error 2 and says truncation error. Therefore I had to rely on the CD.

2. Next problem is with 'make'.
I get the following errors when I do 'make'
rajan@rajan-laptop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ make
make -C tools
make[1]: Entering directory `/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-28-generic/build SUBDIRS=/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
  CC [M]  /home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/rajan/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [LINUX] Error 2


3. Should I go ahead with install? I did but was not of any use.

4. Here is the output from lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

5. Here is the output of ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:2a:43:9c  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe2a:439c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69695371 (69.6 MB)  TX bytes:1314473 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:76:10:b8  
          inet6 addr: fe80::21f:1fff:fe76:10b8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3907 (3.9 KB)


So what is happening? Any clues would really help me. Why is 'make' giving so many errors. Am I not supposed to use kernel 32-28 because edimax is only for 32-24 and 26?
Please help because I am at a point where I want to quit Linux after using it for about 1.5 years. Every task is soooo difficult!! At some point patience does run out but I love it and do not want to call quits. I am sure someone will help me.

---

### Post by GremlinUK on 2011-02-19
In case any gets the impression from this thread that the Edimax EW7711UAN is a poorly supported device, I bought one yesterday, and it just worked as soon as I plugged it into my 10.10 laptop (not a hot plug of course, plug in when switched off, then boot). No drivers to install, nothing. Brilliant, especially after days of hacking about trying to get the 6-year old built in card to work.

---

### Post by c-shadow on 2011-02-19
Couple of days ago I solved my edimax problem with 15m UTP cable, borrowed crimp and a bit of time :)

---


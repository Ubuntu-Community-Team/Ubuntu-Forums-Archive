---
title: "Need help with wireless"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by brettburtner on 2010-06-06
Please help with wireless.  Newbie here, have dual-boot Windows XP Home and Ubuntu 10.04.

After a few shutdowns (exact number not known), wireless won't work in Ubuntu. 

When I boot into Windows, something in Windows turns it on again, and I go back into Ubuntu.

Loop.

Anyone have any ideas?  The rfkill file has a zero (0) when wireless is working, and a two (2) when it is not.  It only happens on a hard boot, never on restart.

Any help would be appreciated.  I want to be rid of Windows.  All I use it for now is turning on the wireless.  Ugh!

---

### Post by 666f6f on 2010-06-06
What is your wireless adapter? Can you paste the output of the following command? ```
lshw -c network
```

---

### Post by nmaster on 2010-06-06
could you post ```
rfkill list
``` i recently had wireless problems due to a hardware switch.

---

### Post by brettburtner on 2010-06-06
Thank you both for your help thus far.

Here you are:

brett@brett-laptop:~$ rfkill list
brett@brett-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:08:91:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:63:e3:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.107 latency=128 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:d0000000-d0000fff

---

### Post by chili555 on 2010-06-06
Is it a Dell?

---

### Post by brettburtner on 2010-06-06
It's not a Dell.

It's a Nobilus CL56.

---

### Post by 666f6f on 2010-06-07
Hi Brett,

Can you post the output of: ```
cat /etc/modprobe.d/ipw2200
```

Also, there may be a hardware switch or a key combination that enables the Wifi or you can try the command ```
sudo iwconfig eth1 txpower on
``` or ```
sudo iwconfig eth1 power on
```

I found valuable information in those threads: [http://ubuntuforums.org/showthread.php?t=191492](http://ubuntuforums.org/showthread.php?t=191492) and [http://ubuntuforums.org/showthread.php?t=680256](http://ubuntuforums.org/showthread.php?t=680256)

---

### Post by chili555 on 2010-06-07
> The rfkill file has a zero (0) when wireless is workingCan you please give us the full path to this file? For instance, /proc/acpi/whatever/wherever

Maybe we can force a zero in there with a command. Maybe we can place the command in */etc/rc.local*.

---

### Post by brettburtner on 2010-06-07
> **666f6f said:**
> Hi Brett,

Can you post the output of: ```
cat /etc/modprobe.d/ipw2200
```Also, there may be a hardware switch or a key combination that enables the Wifi or you can try the command ```
sudo iwconfig eth1 txpower on
``` or ```
sudo iwconfig eth1 power on
```I found valuable information in those threads: [http://ubuntuforums.org/showthread.php?t=191492](http://ubuntuforums.org/showthread.php?t=191492) and [http://ubuntuforums.org/showthread.php?t=680256](http://ubuntuforums.org/showthread.php?t=680256)

Here's what I got:

brett@brett-laptop:~$ cat /etc/modpobe.d/ipw2200
cat: /etc/modpobe.d/ipw2200: No such file or directory

I'm thinking there's some code that's read when Ubuntu loads up, and if I can get that file to read something like 'Make rfkill a zero every time' (pseudocode of course), I can be Windows free.  Being a newbie to Ubuntu, however, I am at a loss.

---

### Post by chili555 on 2010-06-07
> I'm thinking there's some code that's read when Ubuntu loads up, and if I can get that file to read something like 'Make rfkill a zero every time' Please see post #8 above.

---

### Post by brettburtner on 2010-06-07
> **chili555 said:**
> Can you please give us the full path to this file? For instance, /proc/acpi/whatever/wherever

Maybe we can force a zero in there with a command. Maybe we can place the command in */etc/rc.local*.

Sure.  The full path to the rfkill file is:

/sys/bus/pci/drivers/ipw2200/0000:02:02.0

...and, since my wireless is working, it's a zero.

I've tried (in the past) using 

echo > 0 

when it was a 2, and I couldn't get that to work.

---

### Post by brettburtner on 2010-06-07
Hadn't got to it yet.  Sorry.  Was replying to 7.  I posted it now.

---

### Post by brettburtner on 2010-06-07
> **chili555 said:**
> Can you please give us the full path to this file? For instance, /proc/acpi/whatever/wherever

Maybe we can force a zero in there with a command. Maybe we can place the command in */etc/rc.local*.

Here's the path to rfkill:

/sys/bus/pci/drivers/ipw2200/0000:02:02.0

---

### Post by chili555 on 2010-06-07
> echo > 0

when it was a 2, and I couldn't get that to work.That's not the correct method:> sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/0000:02:02.0/rfkill
exit
cat /sys/bus/pci/drivers/ipw2200/0000:02:02.0/rfkill

Let's try a few options. You seem pretty savvy, so I won't go into all the details.

Create a file /etc/modprobe.d/ipw2200.conf. Put in one line:```
options ipw2200 disable=0
``` Reboot. Does that fix it?

If not, change the file to:```
options ipw2200 bt_coexist=1
```Reboot. Any improvements?

---

### Post by brettburtner on 2010-06-07
> **chili555 said:**
> That's not the correct method:

Let's try a few options. You seem pretty savvy, so I won't go into all the details.

Create a file /etc/modprobe.d/ipw2200.conf. Put in one line:```
options ipw2200 disable=0
``` Reboot. Does that fix it?

If not, change the file to:```
options ipw2200 bt_coexist=1
```Reboot. Any improvements?

OK.  First, I tried to see if I could, at any time, change the rf_kill file from one value to another, and that didn't work:

root@brett-laptop:/sys/bus/pci/drivers/ipw2200/0000:02:02.0# dir
broken_parity_status  error          net       rtc
cfg              event_log       net_stats    scan_age
channels          firmware_node   nic_type       speed_scan
class              indirect_byte   power       status
cmd_log              indirect_dword  remove       subsystem
command_event_reg     irq          rescan       subsystem_device
config              led          reset       subsystem_vendor
device              local_cpulist   resource       ucode_version
direct_dword          local_cpus      resource0    uevent
driver              mem_gpio_reg    rf_kill       vendor
eeprom_delay          modalias          rtap_filter
enable              msi_bus          rtap_iface
root@brett-laptop:/sys/bus/pci/drivers/ipw2200/0000:02:02.0# cat rf_kill
0
root@brett-laptop:/sys/bus/pci/drivers/ipw2200/0000:02:02.0# echo 0>rf_kill

root@brett-laptop:/sys/bus/pci/drivers/ipw2200/0000:02:02.0# echo 2>rf_kill

root@brett-laptop:/sys/bus/pci/drivers/ipw2200/0000:02:02.0# cat rf_kill
0

As you can see, it didn't change the value to a '2' and I don't understand why.

Then, I created the ipw2200.conf file (with only the one line) as requested in the /etc/modprobe.d directory.

I still have wifi after one shutdown, but we'll have to see what happens after several shutdowns.  I'll keep you posted.  Thank you SO much for your help thus far!

---

### Post by brettburtner on 2010-06-07
> **chili555 said:**
> That's not the correct method:

Let's try a few options. You seem pretty savvy, so I won't go into all the details.

Create a file /etc/modprobe.d/ipw2200.conf. Put in one line:```
options ipw2200 disable=0
``` Reboot. Does that fix it?

If not, change the file to:```
options ipw2200 bt_coexist=1
```Reboot. Any improvements?

What does creation of the ipw2200.conf file do for me?  Just curious.

---

### Post by chili555 on 2010-06-07
> What does creation of the ipw2200.conf file do for me? Just curious.It simply says to the system, whenever you load ipw2200, load it with an additional parameter, in this case, disable=0.

You can see a list of available module parameters with:```
modinfo ipw2200
```> $ modinfo ipw2200
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     F2DA23EE80E926210A072D7
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
--- snip ---
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        libipw,lib80211
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
[COLOR="Red"]parm:           disable:manually disable the radio (default 0 [radio on]) (int)[/COLOR]
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)


---

### Post by brettburtner on 2010-06-07
> **brettburtner said:**
> What does creation of the ipw2200.conf file do for me?  Just curious.

Well, the first line didn't work.  I just tried the '...bt_coexist...' parameter in the ipw2200.conf file, so we'll see what happens.

Thanks again!  If you have any other suggestions, please be sure and let me know.  I'll do anything (almost) to be rid of Microsoft!

---

### Post by brettburtner on 2010-06-08
Well, nothing has worked as yet.

As a matter of fact, the following line...

options ipw2200 bt_coexist=1

...actually prevented boot (do you call that a crash with Ubuntu?).

Any other suggestions?  I put the ipw2200.conf back to the first method '...disable=0'.

---

### Post by chili555 on 2010-06-09
> I put the ipw2200.conf back to the first method '...disable=0'.If it is doing no good, we might as well remove it altogether.```
sudo rm /etc/modprobe.d/ipw2200.conf
```I am sorry, I am out of ideas.

---

### Post by 666f6f on 2010-06-09
> **brettburtner said:**
> Hadn't got to it yet.  Sorry.  Was replying to 7.  I posted it now.

I'm far from being a wireless network guru but have you tried the rest of the commands posted in post #7? Namely:

```
sudo iwconfig eth1 txpower on
```
or
```
sudo iwconfig eth1 power on
```

---

### Post by brettburtner on 2010-06-09
No problem.  I'll remove it then.

Thanks for the help regardless.  It's nice of you just to have tried.

Thanks again!

---

### Post by brettburtner on 2010-06-09
> **666f6f said:**
> I'm far from being a wireless network guru but have you tried the rest of the commands posted in post #7? Namely:

```
sudo iwconfig eth1 txpower on
```or
```
sudo iwconfig eth1 power on
```

The first command works, so I'll have to try it next time my wifi doesn't work in Ubuntu, so thanks for the advice.

The second line, however, returns an error (see all code for both suggestions, below):

root@brett-laptop:~# iwconfig eth1 txpower on
root@brett-laptop:~# iwconfig eth1 txpower off
root@brett-laptop:~# iwconfig eth1 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Input/output error.

Thanks, and have a great day!

---

### Post by 666f6f on 2010-06-09
> **brettburtner said:**
> The first command works, so I'll have to try it next time my wifi doesn't work in Ubuntu, so thanks for the advice.

Great, glad it worked! Ideally though you'd like to have the Wifi card permanently enabled. Can you post the output of ```
dmesg|grep ipw2200
```

If something blocks the card from being enabled, we may get lucky and see it.

---

### Post by brettburtner on 2010-06-09
> **666f6f said:**
> Great, glad it worked! Ideally though you'd like to have the Wifi card permanently enabled. Can you post the output of ```
dmesg|grep ipw2200
```If something blocks the card from being enabled, we may get lucky and see it.

Here is the requested output:

brett@brett-laptop:~$ dmesg|grep ipw2200
[   15.752886] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.752890] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.752991] ipw2200 0000:02:02.0: power state changed by ACPI to D0
[   15.753004] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   15.764063] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.764121] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   16.278303] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  688.484269] ipw2200: Failed to send POWER_MODE: Command timed out.
[  702.036254] ipw2200: Failed to send POWER_MODE: Command timed out.

Thanks again!

---

### Post by 666f6f on 2010-06-09
Those lines seem suspicious 
```
[ 15.752991] ipw2200 0000:02:02.0: power state changed by ACPI to D0
...
[ 688.484269] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 702.036254] ipw2200: Failed to send POWER_MODE: Command timed out.

```

Have you checked for a hardware switch or a key combination that might enable the Wifi?

---

### Post by brettburtner on 2010-06-09
> **666f6f said:**
> Those lines seem suspicious 
```
[ 15.752991] ipw2200 0000:02:02.0: power state changed by ACPI to D0
...
[ 688.484269] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 702.036254] ipw2200: Failed to send POWER_MODE: Command timed out.

```Have you checked for a hardware switch or a key combination that might enable the Wifi?

I've tried every Fn+F1 through Fn+F12 key combination and F1 through F12 by themselves.

There is a hard switch as well, but when the LED is off (like happens sometimes), the hardware switch does absolutely nothing.  And, like I said, the rf_kill file holds a 2 value.

When wifi is working, the LED is on, the hardware switch turns off and on both the LED and the wifi, and rf_kill holds a 0.

Ugh!  Any more ideas I could try?  I'm certainly at a loss.

---

### Post by 666f6f on 2010-06-10
Hi Brett, thanks for reporting back. The LED seems to be very powerful, for some reason.

1. When you enable the wireless with *sudo iwconfig eth1 txpower on* does the LED become ON?

2. When you disable the wireless with *sudo iwconfig eth1 txpower off* does the LED become OFF?

3. Can you run ```
sudo mv /etc/modprobe.d/ipw2200 /etc/modprobe.d/ipw2200.bak; sudo echo 'options ipw2200 led=1' > /etc/modprobe.d/ipw2200
``` and **reboot** (or reload the module).

4. Are there any suspicious options in the BIOS relevant to the Wifi?

NOTE: Keep a list/journal with your steps so we can revert to a given point, if we have to.

---

### Post by brettburtner on 2010-06-10
> **666f6f said:**
> Hi Brett, thanks for reporting back. The LED seems to be very powerful, for some reason.

1. When you enable the wireless with *sudo iwconfig eth1 txpower on* does the LED become ON?

2. When you disable the wireless with *sudo iwconfig eth1 txpower off* does the LED become OFF?

3. Can you run ```
sudo mv /etc/modprobe.d/ipw2200 /etc/modprobe.d/ipw2200.bak; sudo echo 'options ipw2200 led=1' > /etc/modprobe.d/ipw2200
``` and **reboot** (or reload the module).

4. Are there any suspicious options in the BIOS relevant to the Wifi?

NOTE: Keep a list/journal with your steps so we can revert to a given point, if we have to.

Well, so far, I haven't been able to figure this out even with all your help thus far.  We'll have to see.  

I've tried your recommendations, and I'll provide answers corresponding to your numbers above.

1.  No.  Nothing happens to the LED.  The only thing that happens is that it connects me to the network.

2.  No.  Nothing happens to the LED.  The only thing that happens here is that it disconnects me from the network.

3.  Tried it.  Nothing changed.  Removed it.

4.  I couldn't find anything at all in the BIOS regarding WiFi.  But, if it were a BIOS problem, wouldn't Windows have trouble turning on wifi as well?  Remember, I'm dual-booting (ugh).  I'm using Windows only to turn on my wifi.

Thanks again for all the help.  I sure will be glad when/if this is fixed.

---

### Post by 666f6f on 2010-06-11
Hi Brett,

In the official ipw2200 web site I've found a [laptop matrix]("http://rfswitch.sourceforge.net/?page=laptop_matrix") where you can check the support status for laptops wireless radio switches.

I think your laptop is listed as *Compal CL56*. If that's true then according to the matrix, you need the acerhk module, instead of the ipw2200 module.

The downside is that acerhk module is 32bit only, so we may have to use acer_acpi or acer-wmi. According to the [acer-wmi module documentation]("http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt"): *acer-wmi is derived from acer_acpi, originally developed by Mark Smith in 2005, then taken over by Carlos Corbacho in 2007, in order to activate the wireless LAN card under a 64-bit version of Linux, as acerhk (the previous solution to the problem) relied on making 32 bit BIOS calls which are not possible in kernel space from a 64 bit OS.*.

Can you please run and post the output of ```
uname -a
``` and ```
sudo rmmod ipw2200; sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290 && sudo echo 1 > /proc/driver/acerhk/wirelessled
``` or ```
sudo rmmod ipw2200; sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290 && sudo echo 1 > /proc/driver/acerhk/wirelessled
```

---

### Post by chili555 on 2010-06-11
> you need the acerhk module, instead of the ipw2200 module.Incorrect.

The acer[COLOR="Red"]hk[/COLOR] module translates [COLOR="Red"]h[/COLOR]ot[COLOR="Red"]k[/COLOR]ey presses in Acer manufactured laptops, including OEM, into appropriate key codes the kernel can act upon.

ipw2200 is the driver for the wireless card. The only connection they have is that the press of the wireless key may not be recognized without acerhk and therefor the wireless radio may not turn on no matter what.

Perhaps acerhk or acer-wmi is already loaded and translating key presses incorrectly. Did you check *lsmod*?

acerhk is not installed on my system by default. Did you compile it for yours?

---

### Post by brettburtner on 2010-06-13
> **chili555 said:**
> Incorrect.

The acer[COLOR=Red]hk[/COLOR] module translates [COLOR=Red]h[/COLOR]ot[COLOR=Red]k[/COLOR]ey presses in Acer manufactured laptops, including OEM, into appropriate key codes the kernel can act upon.

ipw2200 is the driver for the wireless card. The only connection they have is that the press of the wireless key may not be recognized without acerhk and therefor the wireless radio may not turn on no matter what.

Perhaps acerhk or acer-wmi is already loaded and translating key presses incorrectly. Did you check *lsmod*?

acerhk is not installed on my system by default. Did you compile it for yours?

I don't think I did any compiling yet.  I'm too much of a newbie.

I don't even know how to 'check lsmod'.

---

### Post by 666f6f on 2010-06-13
Hello Brett,

Still I would suggest to run the commands I gave you in post #30. If they fail, reboot your system, remove the *sudo rmmod ipw2200* part of the last two commands and rerun them.

---

### Post by chili555 on 2010-06-13
> **brettburtner said:**
> I don't think I did any compiling yet.  I'm too much of a newbie.

I don't even know how to 'check lsmod'.Open a terminal and do:```
lsmod | grep acer
```If acer-wmi is loaded, I suggest:```
sudo rmmod -f acer-wmi
sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290
```Is there any improvement?

---

### Post by brettburtner on 2010-06-13
> **chili555 said:**
> Open a terminal and do:```
lsmod | grep acer
```If acer-wmi is loaded, I suggest:```
sudo rmmod -f acer-wmi
sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290
```Is there any improvement?

OK, so if nothing shows up, then 'acer' is not loaded, right?

Here's the output of the lsmod command:

root@brett-laptop:~# lsmod | grep acer
root@brett-laptop:~#

---

### Post by chili555 on 2010-06-13
Let's load it and see what happens:```
sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290
dmesg | tail -n 10
```

---

### Post by brettburtner on 2010-06-14
> **chili555 said:**
> Let's load it and see what happens:```
sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290
dmesg | tail -n 10
```

Here's what I got:

brett@brett-laptop:~$ sudo modprobe acer-wmi usedritek=1 autowlan=1 force_series=290
[sudo] password for brett: 
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acer-wmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by chili555 on 2010-06-14
Let's amend it a bit:```
sudo modprobe acer-wmi force_series=290
dmesg | tail -n 10
```Thanks.

---

### Post by brettburtner on 2010-06-14
> **chili555 said:**
> Let's amend it a bit:```
sudo modprobe acer-wmi force_series=290
dmesg | tail -n 10
```Thanks.

Well, I don't think that worked, either:

brett@brett-laptop:~$ sudo modprobe acer-wmi force_series=290
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
brett@brett-laptop:~$ dmesg | tail -n 10
[  159.288291] usb 1-3: USB disconnect, address 2
[  234.538976] eth0: link down
[  234.539196] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  244.572045] eth1: no IPv6 routers present
[43083.291745] acer_wmi: Unknown parameter `usedritek'
[43140.019520] acer_wmi: Unknown parameter `usedritek'
[43670.973965] acer-wmi: Acer Laptop ACPI-WMI Extras
[43670.973975] acer-wmi: No or unsupported WMI interface, unable to load
[43739.636260] acer-wmi: Acer Laptop ACPI-WMI Extras
[43739.636269] acer-wmi: No or unsupported WMI interface, unable to load

---

### Post by brettburtner on 2010-06-19
Does anyone have any further suggestions I could try?  I still have to boot into Windows to turn on my wifi, then boot into Ubuntu.  Ugh.

Thanks for everyone's help so far -- I really appreciate the valiant efforts!

---


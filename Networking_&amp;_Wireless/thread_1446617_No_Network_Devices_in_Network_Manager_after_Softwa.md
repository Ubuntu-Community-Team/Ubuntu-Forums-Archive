---
title: "No Network Devices in Network Manager after Software update"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by toddmart on 2010-04-04
This is my first post and I'm completely new to Ubuntu/linux. I'm working my way through help guides. I installed 9.10 a few days ago (from Desktop CD) and had gotten everything up and running for a couple of days when yesterday morning I got a pop-up telling me that I had software updates available. Since I didn't really know what any of them were and since Ubuntu seemed to have made pretty good decisions for me so far, I just chose to "Install All". After the update I restarted my system and since that moment, I no longer can see my network devices in the Network Manager. My wireless network isn't visible and when I wire in, it doesn't pick that up either. If I click on the Network Manager, I see "No Network devices available". I've search for other threads on this but the replies to similar problems are either unclear or simply over my head. 

Any help with this would be greatly appreciated. As I stated originally, I am a complete newbie so please assume I know nothing when suggesting terminal commands and such. Graphical options are preferred when available. 

My system is the following:
Dell Vostro 1500
2 G ram
Intel Core 2 Duo 1.4 Ghz

When I run lshw, I do see this:

* -network UNCLAIMED
Ethernet Controller
BCM4401-B0 100Base-TX
Broadcom

I no longer see the wireless device which was there before the update. It's a Broadcom device and I had installed the correct driver, bcmwl-kernal-source, from synaptic. Now, when I go to synaptic, it tells me the driver is still installed. I've re-installed it but that did nothing. 

Let me know if there is any other information that should provide.

Thanks!

---

### Post by toddmart on 2010-04-05
Can anyone help with my issue above?

---

### Post by chili555 on 2010-04-05
> I know nothing when suggesting terminal commands and such. Graphical options are preferred when available. Me, too. However, sometimes, in order to find out what's going on under the hood, *only* the command line will do. I will try to be very clear about the commands; you can type them exactly as I put them in code tags. Let's find out why your drivers are not loading. We'll ask if there any kernel messages concerning your drivers. Please open Applications > Accessories > Terminal and do:```
dmesg | grep -e wl -e b4
```That pipe symbol | is on my US keyboard on the same key with \. Post the result here and we'll have a good idea about how to proceed.

---

### Post by toddmart on 2010-04-05
Thanks for your reply. I typed the code above exactly. Here is the result:

[     1.276827] usb us[COLOR=Red]b4[/COLOR]: configuration #1 chosen from 1 choice

I tried it twice and got the same result each time.

---

### Post by chili555 on 2010-04-05
I believe your wired ethernet is supposed to work with a module *b44.* Let's load it and see if the ethernet comes to life.```
sudo modprobe b44 ssb
ifconfig
```If you do not have a wired interface, eth0, perhaps, run this and post the results.```
dmesg | grep b4
``` Then we will proceed on to the wireless.

---

### Post by toddmart on 2010-04-05
Okay, this is tough because I don't have internet access on the laptop and the result message is long. I've saved it as txt on a flash drive and will paste it as such on this machine (my windows desktop). And btw, I usually go wireless but I can plug in if needed. Both were working before the update.

Here's the result of the first command:
~$ sudo modprobe b44 ssb
[sudo] password for todd: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting b44 (/lib/modules/2.6.31-20-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And then the result of ifconfig:

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2010-04-05
> And btw, I usually go wireless but I can plug in if needed. Both were working before the update.It is probably easier to get going wired and then, if we need to, be able to download things with the wired connection. What is *not* easy is switching back and forth in mid-thread. If you'd rather concentrate on wireless first, please let me know.

Let's see:```
dmesg | grep -e b4 -e ndis
```

---

### Post by toddmart on 2010-04-05
No, I'm fine starting with wired. 

Here's the next result:
:~$ dmesg | grep -e b4 -e ndis
[    1.276827] usb usb4: configuration #1 chosen from 1 choice
[   25.071004] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.194646] usbcore: registered new interface driver ndiswrapper
[102382.998045] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[102382.998071] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[102383.076171] b44: Unknown parameter `ssb'
[102465.834979] b44: Unknown parameter `ssb'

---

### Post by chili555 on 2010-04-05
> usbcore: registered new interface driver ndiswrapperIn your efforts to install ndiswrapper, did you blacklist a few things, *ssb* for example?```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```Anything interesting in there?

---

### Post by toddmart on 2010-04-05
Chili,

You may have lost me on this one. I didn't purposefully blacklist  anything. Obviously something happened when I did the update. 

I ran the code above. It's a long list of replies. The only thing  listing ssb is this:
# replaced by b43 and ssb
blacklist bcm43xx

There is also this:
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

I can paste the entire reply if you'd like but those are the only two  that seem relevant to me.

---

### Post by chili555 on 2010-04-05
No problem. I am a bit gunshy; I get a lot of problems that are cleared up when the poster suddenly remembers a failed ndiswrapper installation. Please do:```
sudo rmmod -f b44
sudo modprobe ssb
sudo modprobe b44
```Are any errors or warnings reported?

Please do:```
dpkg -l | grep backports
```Do you see this, among other things?```
[COLOR="Red"]ii[/COLOR]  linux-backports-modules-karmic-generic  
```ii means 'installed.' I wonder if it's broken. If it is installed, please try:```
sudo apt-get remove linux-backports-modules-*
```Reboot and see if networking is returned.

---

### Post by toddmart on 2010-04-05
Results from first three:
todd@todd-laptop:~$ sudo rmmod -f b44
[sudo] password for todd: 
ERROR: Removing 'b44': No such file or directory
todd@todd-laptop:~$ sudo modprobe ssb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
todd@todd-laptop:~$ sudo modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by toddmart on 2010-04-05
Results of second command:
todd@todd-laptop:~$ dpkg -1 | grep backports
dpkg: unknown option -1

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by chili555 on 2010-04-05
> dpkg -1 | grep backportsThat's an L there, not a one.> I get a lot of problems that are cleared up when the poster suddenly remembers a failed ndiswrapper installation. > WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Hmmm.

It does look like the two modules inserted without error, and only a harmless warning. Now does:```
ifconfig
```show an ethernet interface?

Let's get rid of the warning:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by toddmart on 2010-04-05
Replacing the 1 with an l got no return.

ifconfig shows this:
todd@todd-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:c6:c6:17  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Running the last sudo code also got nothing.

---

### Post by chili555 on 2010-04-05
> eth0 Link encap:Ethernet HWaddr 00:1d:09:c6:c6:17
UP BROADCAST RUNNING MULTICAST MTU:1500 MetricThe ethernet lives! I wonder if it just isn't correctly loading the modules. Let's force it a bit:```
sudo su
echo b44 >> /etc/modules
echo ssb >> /etc/modules
exit
```Now are you ready to work on the wireless? Were you using ndiswrapper? Let's see:```
ndiswrapper -l
```

---

### Post by toddmart on 2010-04-06
results of sudo su:

todd@todd-laptop:~$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
[sudo] password for todd: 
todd@todd-laptop:~$ sudo su
[sudo] password for todd: 
root@todd-laptop:/home/todd# echo b44 >> /etc/modules
root@todd-laptop:/home/todd# ssb >> /etc/modules
No command 'ssb' found, did you mean:
 Command 'ssh' from package 'openssh-client' (main)
 Command 'ss' from package 'iproute' (main)
 Command 'sb' from package 'lrzsz' (universe)
ssb: command not found
root@todd-laptop:/home/todd# exit
exit
todd@todd-laptop:~$

---

### Post by toddmart on 2010-04-06
ndiswrapper: I'm having a hard time with your one's and L's. Your L's look like one's to me. So I ran it both ways. Here's the results (L first):

todd@todd-laptop:~$ ndiswrapper -l
todd@todd-laptop:~$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

---

### Post by chili555 on 2010-04-06
> root@todd-laptop:/home/todd# ssb >> /etc/modulesThe command was:> [COLOR="Red"]echo[/COLOR] ssb >> /etc/modules
Please redo that command so that the required module is sure to get loaded on boot. 

Since you had an ndiswrapper file, I assumed that you, at one time tried to install ndiswrapper in order to get your wireless going. The command:```
ndiswrapper -l
```That's a lower case L, means, roughly, list my ndiswrapper details. Evidently you have none, since the command returned nothing. Please verify by insuring that ndiswrapper is not loading on boot:```
lsmod | grep ndiswrapper
dmesg | grep ndiswrapper
```If both of these commands produce nothing, then we can troubleshoot the native driver.

Is your wireless device showing up in:```
sudo lshw -C network
```Does this suggest that the appropriate driver is getting loaded?```
lsmod | grep wl
```

---

### Post by toddmart on 2010-04-06
Results of each command:
root@todd-laptop:/home/todd# echo b44 >> /etc/modules
root@todd-laptop:/home/todd# echo ssb >> /etc/modules
root@todd-laptop:/home/todd# exit
exit
todd@todd-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           185532  0 
todd@todd-laptop:~$ dmesg | grep ndiswrapper
[   25.071004] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.194646] usbcore: registered new interface driver ndiswrapper
todd@todd-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c6:c6:17
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:fe5fe000-fe5fffff
todd@todd-laptop:~$ lsmod | grep wl
todd@todd-laptop:~$ ^C

---

### Post by chili555 on 2010-04-06
It looks like ndiswrapper is loaded but no Windows driver or .inf file has been associated with it. Do you have the ability to hook up the wired ethernet and activate the native Broadcom driver in System > Administration > Hardware Drivers? The activation process will download needed firmware.

---

### Post by toddmart on 2010-04-06
Wired access is now working. System>Administration>Hardware Drivers shows that I have the correct Broadcom driver "activated but not in use".

---

### Post by toddmart on 2010-04-06
There were two drivers. I activated the other one...no change. So then I reactivated the original and correct driver and now it works! Very weird. So I really can't thank you enough for all of the help. But if you don't mind, what exactly did we do? And what in the update could have caused it to drop both devices?

---

### Post by toddmart on 2010-04-06
I spoke too soon. I rebooted and when I came back I had lost drivers again. So I went back to System>Admin> Hardware Drivers and did the same thing again. I first activated Broadcom B43 which does nothing. Then I reactivated Broadcom STA which brought me back online again. For some reason, rebooting is triggering this. The driver is there but will say "activated but not in use", then only be making it inactive then reactivating it will it work. Any thoughts on that?

---

### Post by chili555 on 2010-04-06
> Any thoughts on that?When you reboot, check to see if the correct driver is loaded:```
lsmod | grep wl
```If not, load it and see if the wireless comes to life:```
sudo modprobe wl
iwconfig
```If that does it, please do:```
sudo su
echo wl >> /etc/modules
exit
```

---

### Post by toddmart on 2010-04-07
The driver wasn't loaded so I loaded it by the sudo command you gave me. That worked and brought me back online but iwconfig returns this:
todd@todd-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.



I went ahead and ran the root commands and will reboot again and report back.

---

### Post by toddmart on 2010-04-07
Okay, so after rebooting, my driver loaded but with a difference. I got a popup asking for keyring password to enter network manager. Before, it was loading properly on reboot without asking for this. Is there a way to avoid this?

Thanks!

---

### Post by chili555 on 2010-04-07
On my systems, I click 'Cancel' when it asks for the keyring and it connects anyway! Also, right-click the Network Manager icon, Edit Connections, select Wireless, edit your network and make sure Connect Automatically is checked. It will connect on boot thereafter.

---

### Post by toddmart on 2010-04-07
That's great! Thanks so much for your help. I just wish I knew what we did.

---

### Post by chili555 on 2010-04-07
For some reason, the modules b44, ssb and wl were not loading automagically on boot. We just forced them into */etc/modules*. It did take a few posts to work out just what was going wrong, but I hope all is well now.

---


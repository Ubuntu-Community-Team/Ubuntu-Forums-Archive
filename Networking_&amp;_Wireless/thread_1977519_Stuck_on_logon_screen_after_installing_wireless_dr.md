---
title: "Stuck on logon screen after installing wireless driver"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by 1grouchy on 2012-05-10
My wireless stop working suddenly and I try to reinstall driver. I think that I was install wrong one and after reboot I stuck on Ubuntu logon screen.
When try to login Ubuntu blinks with black screen with some message:
Stopping system V runlevel compatibility.

After that shows me again logon screen.

Command lspci shows me WiFi driver RTL8191SEvB.
***I was reinstall with RTL8187L driver when the problem appears.

Try to blacklist all kinds of RTL drivers but ubuntu again and again shows me RTL8191SEvB.

Wireless card is working, I try it on Win.

What can I do here my friends?

---

### Post by chili555 on 2012-05-10
I doubt that RTL8187L is correct for RTL8191SEvB. Can you select the recovery mode at the GRUB menu when you first boot? My strategy would be to uninstall everything you did to get just the wireless going and start fresh.

Please see attached.

---

### Post by 1grouchy on 2012-05-10
I can enter to terminal from logon screen with Ctrl + Alt + F1, but how to remove everything installed for wireless?

---

### Post by chili555 on 2012-05-10
Did you compile a driver you downloaded? If so, simply reverse the process:```
cd Desktop/RTwhatever  <--or wherever you extracted the tar.gz
sudo su
make uninstall
exit
```You can recall your terminal commands with:```
history
```If you add 'less' you can use the arrow keys to scroll through the commands:```
history | less
```Get out of 'less' with q.

Did you add anything to /etc/modules to get a driver to load automatically?```
cat /etc/modules
```If so, you'll need to remove it. Do you have a wired ethernet connection? We may need to install a command-line text editor such as vim.

---

### Post by 1grouchy on 2012-05-10
I try now > make uninstall < but problem is still persist.
I don't have a ethernet connection from terminal. :(
When I ping google dns network is unreachable.

Is there a way to restore all wireless settings to system default.

Thank you for trying to help.

---

### Post by chili555 on 2012-05-10
What drivers are being loaded automatically?```
cat /etc/modules
```What drivers are loaded on boot?```
lsmod | grep rt
```What drivers are blacklisted?```
cat /etc/modprobe.d/blacklist.conf | tail -n10
```What are the kernel messages when it freezes?```
sudo cat /var/log/dmesg.0 | grep -i warn
sudo cat /var/log/dmesg.0 | grep -i error
```I wonder if it's really related to wireless.

I apologize if I forgot; the pipe symbol | is on the right side of my US keyboard on the same key with \.

I will be away from the forum for about 1 1/2 hours; sorry.

---

### Post by 1grouchy on 2012-05-10
Ok this is black screen print when I try to login:


* Stopping save kernel messages 

* Starting CUPS printing spooler/servers

* Starting VirutalBox kernel modules

* Starting bluetooth

* (STAR is a yellow color) PulseAudio configured for per-user sessions
							saned disabled; edit /etc/default/saned	
								*checking battery state

* Stopping system V runlevel compatibility.



----------------------------------------------
/etc/modules/


lp
rtc
coretemp


----------------------------------------------


lsmod | grep rt

parport_pc	36962	0
parport		46562	3	parport_pc,ppdev,lp


-----------------------------------------------


blacklisted
(as I said I try all kind rtl drivers, but I try with with all commented also, same thing)

blacklist rtl8192se
blacklist rtl8192ce
blacklist rtl8192de
blacklist rtl8187L
blacklist rtl8187
blacklist rtlwifi



------------------------------------------------


Kernel WARN:
[ 23.198960] mei: module is from the staging directory, the quality is unknown, you have been warned
Kernel ERROR
[ 1.077841]  PCI0000:00: ACPI _OSC request  failed (AE_ERROR), returned control mask: 0x1d
[ 23.255556]  EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro

---

### Post by darkod on 2012-05-10
Can it have something to do with the ACPI error?

Try booting the normal mode with noapic parameter.

Another idea, what will happen if you don't have the rtl8192se blacklisted. That is the model of your wi-fi card, so temporarily comment out the blacklist of that module.

---

### Post by 1grouchy on 2012-05-10
I try with noapic and noapic quiet splash parameters. Remove rtl8192se from black list, still nothing. :(:(

---

### Post by darkod on 2012-05-10
OK. If you try to boot the normal mode, but edit the lines, delete the 'quiet splash' so that it shows the text during boot.

Look carefully what are the last few lines of text before it stops booting. Do they show any particular information? Any lead that might help?

---

### Post by chili555 on 2012-05-10
> lsmod | grep rt

parport_pc 36962 0
parport 46562 3 parport_pc,ppdev,lp
There are no wireless drivers for a RTL8191SEvB loaded, so I doubt it's a wireless problem.> Another idea, what will happen if you don't have the rtl8192se blacklisted.**Un**-blacklisting a wireless driver is very unlikely to cure a freeze. If it is the correct driver for your wireless device, which we haven't established yet, blacklisting will simply not allow the wireless device to work and un-blacklisting will make it work. So far, I haven't seen anything that suggests that the wirless driver is the problem. I suggest we all concentrate on this:> ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1dGoogling...

---

### Post by 1grouchy on 2012-05-10
This is the last output when booting with noapic:

checking for running unattended-upgrades:
* Stoping Failsafe Boot Delay
* Stopping System V initialisation compatibility
* starting system V runlevel compatibility
* stopping automatic crash report generation
* starting CPU interrupts balancing deamon
* starting deferred execution scheduler
* starting regular background program processing deamon
* starting LightDM Display Manager
* Starting ACPI deamon
* Starting anac(h)ronistic cron
* Starting save kernel messages
* stopping anac(h)ronistic cron
* stopping save kernel messages

---

### Post by darkod on 2012-05-10
According to some google results, a general fix for ACPI is the parameter acpi=off. That will turn it off completely. It's not suggested as a solution, only as a starting point to see if the issue is with ACPI.

If it works, it is recommended to investigate further instead of having acpi=off all the time.

See if acpi=off helps and let us know.

---

### Post by 1grouchy on 2012-05-10
I reinstall ubuntu and now I can login to system but WiFi still not working. This is not first time for WiFi to literally torture me like this, but this time I can't get him to work.
Now I remove two lines from /proc/modules

rtl8192se and rtlwifi and can't get them back, ubuntu does not allow me to.

What now?

Regards.

---

### Post by chili555 on 2012-05-10
Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by 1grouchy on 2012-05-11
Thank you guys for trying, but after I install some other RTL driver problem was back, I lost my nerv and do clean install of ubuntu.

So I can post another thread or we can try here to find appropriate driver to replace original and work fine..
(You can say chili and I will do so)

Problem with original wifi driver is really high ping in some moments (without traffic also). It goes to 5000ms for a minute or two or five and then go back in normal (I test ping sync with my friend, and the problem is for sure - driver). And in some other moment he just disconnect from AP.
That's infinite loop.

This is my original driver from lspci in this moment:
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

So which driver to download and how to reinstall this original (but **(re)installation** step by step please, i'ts obviously that I'm not so smart person :P ).

Regards!

---

### Post by chili555 on 2012-05-11
> we can try here to find appropriate driver to replace original and work fine..
(You can say chili and I will do so)Yes, please, right here.> after I install some other RTL driver problem was back, I lost my nerv and do clean install of ubuntu.If I am going to help you, please do not install anything unless we discuss it here. I can't fix a problem that's ever changing and ever moving.> This is my original driver from lspci in this moment:
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)As I said above, I need:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by 1grouchy on 2012-05-11
System is fresh installed now, and I didn't touch wireless driver this time, so problem persist between my wireless card and ubuntu by default.

Sorry for fresh install, but I needed access to ubuntu because of my work and could not wait any longer to solve the previous problem.

```
lspci -nn | grep 0280 output:

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
```Regards!

---

### Post by chili555 on 2012-05-11
> Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [[COLOR="Red"]10ec:8172[/COLOR]] (rev 10)Your device works with the driver rtl8192se. Let's load it and see if we get any errors or warnings:```
sudo modprobe rtl8192se
```Do we now have a wireless interface, usually wlan0?```
iwconfig
```Is the hardware switch set to ON?```
rfkill list all
```Are there any interesting messages here?```
dmesg | grep 8192
```

---

### Post by 1grouchy on 2012-05-11
I don't know did you understood me before. I do have connection over WiFi now but have problem with high ping and random disconnecting.

Outputs:

```

**sudo modprobe rtl8192se** - no errors


**iwconfig**
wlan0     IEEE 802.11bgn  ESSID:"MY-AP-SSID"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: MY-MAC-ADDRESS   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4033   Missed beacon:0


**rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

[B]
dmesg | grep 8192[/B]
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880137c00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.793966] PM: Registering ACPI NVS region at bf718000 (8192 bytes)
[   26.451645] rtl8192se 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.451657] rtl8192se 0000:07:00.0: setting latency timer to 64
[   26.464257] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   26.464259]            Loading firmware rtlwifi/rtl8192sefw.bin
```

---

### Post by chili555 on 2012-05-11
Let's see if we can tweak the driver. Please do:```
sudo modprobe -r rtl8192se
sudo modprobe rtl8192se swenc=1
```How is the ping now? If this helps, we'll need to write one file to make it persistent.

---

### Post by 1grouchy on 2012-05-11
Great tweak my friend!

Comparation (**Note: **Download is active all the time and mostly is at full speed):

Before:
[I]87 packets transmitted, 69 received, 20% packet loss, time 86240ms
rtt min/avg/max/mdev = 22.543/571.161/4959.002/1335.386 ms, pipe 5[/I]

After:
[I]639 packets transmitted, 624 received, 2% packet loss, time 638950ms
rtt min/avg/max/mdev = 21.296/67.162/627.051/54.138 ms[/I]

I am satisfied with this result, considering country where I live and the internet provider.

 Let's write that script and tomorrow I will confirm final results, ok?

Of course, thank you very much for this help chili !!!

---

### Post by chili555 on 2012-05-11
> Let's write that script and tomorrow I will confirm final results, ok?OK! Please do:```
sudo gedit /etc/modprobe.d/rtl8192se.conf
```If you don't have the text editor gedit, use nano or leafpad or similar. Write one line:```
options rtl8192se swenc=1
```Proofread carefully, save and close gedit. You should be all set. Please post back if you need more assistance.

---

### Post by 1grouchy on 2012-05-21
I owe you a reply for your final solution. Sometimes happens same problem but this commands above solve it quick. So thank you one more time.

Regards.

---

### Post by 1grouchy on 2012-11-23
I do not want to open a new thread for this. If it is necessary say it and I'll do it.

Post #20 in this thread.
> I don't know did you understood me before. I do have connection over WiFi now but have problem with high ping and random disconnecting.

The problem above continues to occur more often. 10 to 15 times a day. Sometimes my laptop freezes and I must shut it  down by holding power button.

Also now I have a problem with shutdown/reboot machine. It freeze on LOGOUT screen, almost every time, so for past few months I was doing that from terminal and I MUST stop networking:

[SIZE="2"][COLOR="DimGray"]sudo /etc/init.d/networking stop
sudo shutdown -h now[/COLOR][/SIZE]

I guess that driver is problem, but how to diagnose that and how to replace it with  proprietary.

If anyone can help me, I will be grateful.

Thanks in advance.

---

### Post by chili555 on 2012-11-24
> Sometimes my laptop freezes and I must shut it down by holding power button.Let's start there. The next time it does it, restart and do:```
sudo cat /var/log/dmesg.0 > 1grouchy.txt
dmesg | grep rtl >> 1grouchy.txt
lsmod >> 1grouchy.txt
zip 1grouchy.zip 1grouchy.txt
```Find the file 1grouchy.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by 1grouchy on 2012-11-26
As you requested.

Link:
[1grouchy.txt]("http://ubuntuone.com/5HRrFlbtk6clLIQdyZHdXX")

Regards!

---

### Post by chili555 on 2012-11-26
Here are the last three messages before it evidently bailed out:> [   31.827854] [COLOR="Red"]init: Failed to spawn alsa-restore main process: unable to execute: No such file or directory[/COLOR]
[   31.844459] init: failsafe main process (944) killed by TERM signal
[   31.845585] init: apport pre-start process (1080) terminated with status 1
[   31.857918] init: apport post-stop process (1112) terminated with status 1I googled the highlighted message and found this: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/181516](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/181516)

Post #1 has a suggestion. Reinstalling relevant packages seems like a reasonable step to me, however, I'm not a sound expert. 

I also see this:> [    0.794770] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.794817] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.794861] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.794906] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.794950] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.794994] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.795040] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.795084] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)I'm not sure ACPI and IRQs are an issue, but it seems funny that some IRQs are disabled. You might look in the BIOS and make sure IRQs are set to Autoselect, unless you have purposely set some to disabled for some reason.

In any event, the wireless seems to be working without any apparent problems.

---

### Post by 1grouchy on 2012-11-27
> init: Failed to spawn alsa-restore main process: unable to execute: No such file or directory

As I see (google search) this output can be for many other problems in addition to sound. Also I didn't have any problems with sound at all.

I tried solution that you posted in previous post. No results, as I expected. Laptop freeze on logout again.
[1grouchy2 Logs]("http://ubuntuone.com/4VZF1Jn1mRjsvByO3DGiFc")

I will repeat, when I do stop networking first:
[COLOR="Gray"]sudo /etc/init.d/networking stop[/COLOR],
then I can shutdown/reboot without any problems. That leads me to the point that the problem is related with Network somehow.

---

### Post by chili555 on 2012-11-27
I'm sorry, I have no further ideas.

---

### Post by 1grouchy on 2012-11-27
Never mind, thank you for earlier attempts to help me, greetings.

---


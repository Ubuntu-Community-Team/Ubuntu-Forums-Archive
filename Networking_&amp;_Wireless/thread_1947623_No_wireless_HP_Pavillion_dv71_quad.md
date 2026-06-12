---
title: "No wireless HP Pavillion dv71 quad"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by cssutto on 2012-03-27
I ran all of the commands in your tutorial on what you want and got the error message that there were 36 images.

I have no idea how to compose the message in any other way.

I ran them in a terminal, copied to gedit hoping it would end up plain text.

So I have a new HP, running 10.4 64bit.

I have a wireless router and it is set up properly running 10.4 on a old Thinkpad,

The wireless light is on, but it is yellow.

I believe the problem is that ubuntu did not load a driver.

claude@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Device 008b (rev 34)
13:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
19:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
claude@ubuntu:~$ 
claude@ubuntu:~$ 
claude@ubuntu:~$ lsusb
Bus 003 Device 007: ID 0d49:7110 Maxtor 
Bus 003 Device 006: ID 1163:0100 DeLorme Publishing, Inc. Earthmate GPS (orig)
Bus 003 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 004: ID 03f0:7311 Hewlett-Packard 
Bus 003 Device 003: ID 050d:0416 Belkin Components 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:d281 Suyin Corp. 
Bus 001 Device 003: ID 138a:0018 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
claude@ubuntu:~$ 
claude@ubuntu:~$ 
claude@ubuntu:~$ lspci -nn | grep 'Wireless Brand'
claude@ubuntu:~$ 
claude@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:8a:54:ba  
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe8a:54ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2072216 (2.0 MB)  TX bytes:374882 (374.8 KB)
          Interrupt:29 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11429 (11.4 KB)  TX bytes:11429 (11.4 KB)

claude@ubuntu:~$ 
claude@ubuntu:~$ 
claude@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

claude@ubuntu:~$

---

### Post by Bucky Ball on 2012-03-27
If you have not plugged in an ethernet cable and gotten online, gotten updates, then checked 'Additional Drivers' do it now. DON'T manually install anything until you have.

---

### Post by cssutto on 2012-03-27
> **Bucky Ball said:**
> If you have not plugged in an ethernet cable and gotten online, gotten updates, then checked 'Additional Drivers' do it now. DON'T manually install anything until you have.


I have done that.

No proprietary drivers.

---

### Post by Bucky Ball on 2012-03-27
Could I see:

```
sudo lshw -C network
```If it is wireless N try switching that off.

Right click the network icon and 'Edit Connections'. Make sure you have all the correct details in there to match the router/access point.

---

### Post by cssutto on 2012-03-27
> **Bucky Ball said:**
> Could I see:

```
sudo lshw -C network
```If it is wireless N try switching that off.

Right click the network icon and 'Edit Connections'. Make sure you have all the correct details in there to match the router/access point.

claude@ubuntu:~$ sudo lshw -C network
[sudo] password for claude: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:8a:54:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.193 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:4000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c4500000-c4501fff
claude@ubuntu:~$ 

I have the connections set properly.

I don;t know what the wireless N is.

I am asking  a question, not being the typical internet smart ***:

If the light on the machine is not indicating that the wireless is on, how can connection details make it come on?

It appears to me that the first thing required is to get wireless on.

Again, I am asking a question.

---

### Post by chili555 on 2012-03-27
> If the light on the machine is not indicating that the wireless is on, how can connection details make it come on?That's certainly a clue; however, knowing why it isn't coming on and what to do to make it come on is key. 

We need to get a bit more detail than has been asked before. Please run and post:```
lspci -nn | grep 0280
sudo modprobe iwlagn
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Bucky Ball on 2012-03-27
> **cssutto said:**
> 

It appears to me that the first thing required is to get wireless on.

Again, I am asking a question.

I wanted to see if you had any driver loaded with the last command and if not I was going to suggest:

```
sudo modprobe iwlagn
```... as chili555 just has. He has more smarts about this, anyhow ... ;)

Could you put code between [code] tags, please (add / before 'code' on the end tag).

---

### Post by cssutto on 2012-03-27
> **chili555 said:**
> That's certainly a clue; however, knowing why it isn't coming on and what to do to make it come on is key. 

We need to get a bit more detail than has been asked before. Please run and post:```
lspci -nn | grep 0280
sudo modprobe iwlagn
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

claude@ubuntu:~$ lspci -nn | grep 0280
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
claude@ubuntu:~$ 
claude@ubuntu:~$ sudo modprobe iwlagn
[sudo] password for claude: 
claude@ubuntu:~$ sudo modprobe iwlagn
claude@ubuntu:~$ 
claude@ubuntu:~$ dmesg | grep iwl
[45393.131424] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[45393.131426] iwlagn: Copyright(c) 2003-2009 Intel Corporation
claude@ubuntu:~$ 
claude@ubuntu:~$ rfkill list all
claude@ubuntu:~$ 

I will be away for several hours so there will be no reply until late afternoon or evening.

Thanks for the help so far.

---

### Post by chili555 on 2012-03-27
Bucky and I are wondering why it doesn't take off like a top fuel dragster. We see no reason why not. We'd really like to see the kernel messages about this. Please reboot so we have a clean slate and then do:```
sudo modprobe iwlagn
dmesg > cssutto.txt
zip cssutto.zip cssutto.txt
```You will find a zip file in your home directory called cssutto.zip. Please attach it to your reply using the paperclip tool at the top of the reply box. Thanks.


@Bucky--

[COLOR="Red"]0d:00.0[/COLOR] Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)

I wonder if there is an ACPI problem with the PCI slot. I love a mystery!

---

### Post by cssutto on 2012-03-27
> **chili555 said:**
> Bucky and I are wondering why it doesn't take off like a top fuel dragster. We see no reason why not. We'd really like to see the kernel messages about this. Please reboot so we have a clean slate and then do:```
sudo modprobe iwlagn
dmesg > cssutto.txt
zip cssutto.zip cssutto.txt
```You will find a zip file in your home directory called cssutto.zip. Please attach it to your reply using the paperclip tool at the top of the reply box. Thanks.


@Bucky--

[COLOR="Red"]0d:00.0[/COLOR] Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)

I wonder if there is an ACPI problem with the PCI slot. I love a mystery!


It did not .zip.

It is a text file.

---

### Post by cssutto on 2012-03-27
I don't think it attached.

I suspect it is too big to copy.

I am running out of time and must go in a few minutes.

What to do?

---

### Post by chili555 on 2012-03-27
There should be both; the file that was created when you copied dmesg to text and a zip that was created when you zipped the text. We want the zip only. Please see attached.

---

### Post by cssutto on 2012-03-27
I zipped it myself.

---

### Post by cssutto on 2012-03-27
Try this.

Whoops.

Wrong button

---

### Post by cssutto on 2012-03-27
Although I have been on various message boards for years, I have not used the attachment feature in a browwser, only in emails.

So I am making a mess of this.

I have zipped the file, hit the reeply button used the paper clip, used the browse button in the pop up window, then pressed "post reply"  and no attachment goes through.

So bear with me and have a mod remove the failures so the thread is clutted with trash.

Please.

---

### Post by chili555 on 2012-03-27
I see the following interesting...no, alarming messages:> [    2.182569] ata6.00: ACPI _SDD failed (AE 0x5)
[    7.526660] ata6.00: ACPI _SDD failed (AE 0x5)
[    7.526667] ata6.00: ACPI: failed the second time, disabledAnd also:```
[    1.555984] _OSC invalid UUID
[    1.560385] _OSC invalid UUID
[    1.659731] _OSC invalid UUID
[    1.659832] _OSC invalid UUID
[    1.659928] _OSC invalid UUID
```I am not completely sure what they mean, but I see this bug report: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/512210](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/512210)> you can however work around this bug with the following kernel command line option: libata.noacpi=1
Add that to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub (GRUB2 only, I assume you're using 9.10) and you should be set....
...This is fixed in Lucid btw. At least for me.I suspect if you updated to 11.10, your issue would go away. If you prefer, we can try the GRUB option.

Which do you prefer?

-----------

For reference, your PCI bus does this:> [    1.558076] pci 0000:0d:00.0: reg 10 64bit mmio: [0xc4500000-0xc4501fff]
[    1.558638] pci 0000:0d:00.0: PME# supported from D0 D3hot D3cold
[    1.558673] pci 0000:0d:00.0: PME# disabledIn other words, it stops there. Mine, running 11.10 and the same *iwlagn* driver, does this:> [    0.746547] pci 0000:03:00.0: [8086:4239] type 0 class 0x000280
[    0.746606] pci 0000:03:00.0: reg 10: [mem 0xf2400000-0xf2401fff 64bit]
[    0.746871] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.746897] pci 0000:03:00.0: PME# disabled
[    1.919046] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.923201] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[   12.688380] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.688436] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.688535] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   12.708100] iwlagn 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[   12.708103] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   12.708126] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.708713] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[   12.772687] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532In other words, the driver and the hardware marry and start the wireless interface.

---

### Post by cssutto on 2012-03-27
I am using 104,  64 bit.

I have stayed with it becuae it has been bretty good to me.

However, if 11.10 is stable I will go with that.

I have not read up on it.  Id it as stable as 10.4 and is it an LTS issue?

I do have a few other problems, which are probably related to the 64 bit differences and maybe 11.10 would cure them as well.

Advice?


And can I do an upgrade rather than a clean install and get a good system.  Important to me.  I sure don't want to do a complete install.

This one has bben a pain.

---

### Post by chili555 on 2012-03-27
> Id it as stable as 10.4 and is it an LTS issue?It's stable as a rock for me on three computers. It is not LTS.

I am not sure you can jump from 10.04 directly to 11.10. We can Google.

I'd suggest you download and burn the 64-bit CD and run a live session to try it. Once you know how it performs, let's talk again about how to proceed.

---

### Post by cssutto on 2012-03-27
I have been rooting around on various threads since posting the last and I see that a lot of user dislike unity, which I assume  is 11.10.

But I have not seen an explanation as to why.

If it is the color of the desktop, I could c are less.

If it is something basic in performance, I would like to know what it is.

Obviously you know what you are doing and you like it so I am interested in your comments.

I have seen statements that when 12.04 or whatever comes out, it will be a one stop upgrade from 10.4.

---

### Post by Bucky Ball on 2012-03-27
> **cssutto said:**
> 

I have seen statements that when 12.04 or whatever comes out, it will be a one stop upgrade from 10.4.

Correct. Via Update Manager. LTS to LTS always is.

When you boot and get to the menu of boot options, choose the kernel you are using and hit 'e' to edit it.
Find the line that ends in 'quiet splash'
Add 'libata.noacpi=1' to the end of that line
Follow the instructions at the bottom of that page to save and continue with boot

Hopefully it is that simple. Not sure why you would want to go re-installing or upgrading a solid system if it is ...

If it doesn't work, repeat those steps and remove libata.noacpi=1.

---

### Post by chili555 on 2012-03-27
> I see that a lot of user dislike unity, which I assume is 11.10.

But I have not seen an explanation as to why.It's different; some people just don't like or adapt to change. Here is a good overview. [http://www.youtube.com/watch?v=dq4Oj5quskI](http://www.youtube.com/watch?v=dq4Oj5quskI)

You can easily and quickly install gnome-shell once you've tried and don't like Unity. My wife prefers Gnome. I have a laptop with Unity and a desktop with Gnome. I rather enjoy learning new things!

Have you thought about trying the live CD?

---

### Post by cssutto on 2012-03-27
Bucky Ball:

Only because chil555 suggested it as a cure to the wireless problem and because it sounds to me, a non geek, as easier than patching 10.4

If patching 10.4 is going to be easy I probably should stay with it since I am not sharp at all in trouble shooting and if 11.10 is unsupported then it means I am on my own.

And that is not good.

Although I have had computers since portable was considered what you could carry in a suitcase and WordPerfect was on one big really floppy floppy and you created paragraphs with <ctrl> P and I even owned a software company,  I AM NOT that sharp.

Nor does it help that I am past 83 with a serious cataract on one eye and macular degeneration in the other.

Reading a newspaper is hard work.  Thank goodness on these machines I can make the font whatever I want.

Not to say I am done for, but just to make the point that reading some of this stuff and then putting it into action is not as easy as it once was.

So maybe patching 10.4 is a more safe way for me.

Sorry to bore with my life story, but sometimes all things need to be considered.

---

### Post by Bucky Ball on 2012-03-28
> **cssutto said:**
> Bucky Ball:

Only because chil555 suggested it as a cure to the wireless problem and because it sounds to me, a non geek, as easier than patching 10.4

If patching 10.4 is going to be easy I probably should stay with it since I am not sharp at all in trouble shooting and if 11.10 is unsupported then it means I am on my own.

And that is not good.

Although I have had computers since portable was considered what you could carry in a suitcase and WordPerfect was on one big really floppy floppy and you created paragraphs with <ctrl> P and I even owned a software company,  I AM NOT that sharp.

Nor does it help that I am past 83 with a serious cataract on one eye and macular degeneration in the other.

Reading a newspaper is hard work.  Thank goodness on these machines I can make the font whatever I want.

Not to say I am done for, but just to make the point that reading some of this stuff and then putting it into action is not as easy as it once was.

So maybe patching 10.4 is a more safe way for me.

Sorry to bore with my life story, but sometimes all things need to be considered.

Certainly. Understood. ;)

---

### Post by chili555 on 2012-03-28
> So maybe patching 10.4 is a more safe way for me.It's pretty easy. Please do:```
sudo gedit /etc/default/grub
```Carefully change this part:> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
...to add as I've highlighted below:> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[COLOR="Red"]libata.noacpi=1[/COLOR]"
Everything else in the file is unchanged; you are simply adding the line between the quotes. Proofread carefully twice, save and close gedit. Now do:```
sudo update-grub
```Reboot and let us see:```
dmesg | grep -e libata -e iwl
```Thanks.

---

### Post by cssutto on 2012-03-28
I can't believe it!!!

The wireless light is on.

Pure genius.

Anyway, here is the return:

claude@ubuntu:~$ dmesg | grep -e libata -e iwl
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-40-generic root=UUID=f402dfa6-736d-445f-b3b5-d1830a9723e6 ro libata.noacpi=1 quiet splash
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-40-generic root=UUID=f402dfa6-736d-445f-b3b5-d1830a9723e6 ro libata.noacpi=1 quiet splash
[    1.568731] libata version 3.00 loaded.
claude@ubuntu:~$

---

### Post by chili555 on 2012-03-28
> [ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-40-generic root=UUID=f402dfa6-736d-445f-b3b5-d1830a9723e6 ro [COLOR="Red"]libata.noacpi=1[/COLOR] quiet splash
Perfect! You did a great job.

Let's load the driver and see what happens:```
sudo modprobe iwlagn
dmesg | grep iwl
```Fingers crossed!

---

### Post by cssutto on 2012-03-28
claude@ubuntu:~$ dmesg | grep iwl
[ 1233.634298] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 1233.634301] iwlagn: Copyright(c) 2003-2009 Intel Corporation
claude@ubuntu:~$

---

### Post by cssutto on 2012-03-28
I tried to connect with the router and it will not.

After going through all of the steps, it gives a timed out message.

Do I have to reboot?

I have an appointment with the retina specialist and that always takes about two hours so I am leaving now and will not be back until about 2:00 PM.

Again, not my life story but to make it clear that a wait between responses does not mean a lack of interest.

Thanks again.

---

### Post by chili555 on 2012-03-28
Still non-responsive. Let's have another peek at the message logs:```
dmesg > cssutto2.txt
zip cssutto2.zip cssutto2.txt
```Use the paperclip tool and don't forget (as I sometimes do!) to press Upload.

Thanks.> I have an appointment with the retina specialist and that always takes about two hours so I am leaving now and will not be back until about 2:00 PM.

Again, not my life story but to make it clear that a wait between responses does not mean a lack of interest.
No problem. People, including me, have lives away from the forum. Hopefully you'll be patient when I take Mrs. Chili to lunch in a few hours.

---

### Post by cssutto on 2012-03-28
This should be it.

---

### Post by Bucky Ball on 2012-03-28
> **cssutto said:**
> This should be it.

Yep, that's it. ;)

I notice this:

                                    ```
[ 2025.837790] type=1503 audit(1332940615.786:20):  operation="open" pid=2926 parent=2909 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"  
```Basic things but chilli prob has more ideas. Right click on the network icon and make sure 'Enable Wireless' is ticked.
Right click on network icon and 'Edit Connections'. Go to the wireless dialogue and confirm you have the correct details for your router/access point in there (name, security). Also make sure 'Connect Automatically' and 'Available to all users' are ticked (this sometimes makes a difference).

---

### Post by cssutto on 2012-03-28
I checked all of that and it looks the same as the old machine.

---

### Post by cssutto on 2012-03-28
My eys are still stinging from the trip to the retina specialist today and I am leaving early tomorrow and will be gone until late Saturday night.

So this problem will have to wait until then for further action.

Thanks for the help thus far.

---

### Post by cssutto on 2012-03-31
OK, back in town so if you fellows have any more ideas I am ready to try them.

---


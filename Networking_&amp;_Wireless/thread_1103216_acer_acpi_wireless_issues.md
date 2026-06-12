---
title: "acer acpi wireless issues"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by jlowerison on 2009-03-22
Sorry for creating a new thread but I've been looking all day and cannot find an exact solution for my problem but I'm quite sure I know the problem.

I've been using the ubuntu docs to help solve the problem and I installed the atheros driver using ndiswrapper and  lshw -C network in terminal gives me 

*-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:30:2f:97:da:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

according to the docs my switch is not on which makes sense since the light is not working and its a spring type switch. I was unable to enable the wireless in the bios and I've found through google that I need to use the acpi but the problem is there is no wireless folder which is supposed to be included in ubuntu (I'm using 8.10) I've downloaded the files from googlecode but get errors when trying to 'make' and 'sudo make install' so I kind of need some help from here. I'd appreciate any advice.

Thanks in advance,

Johnny

---

### Post by chili555 on 2009-03-22
I'm not sure I quite understand.> I need to use the acpiACPI is installed and in use by default.> there is no wireless folder which is supposed to be included in ubuntuI don't understand. Can you please explain this a bit further?> I've downloaded the files from googlecodeWhoa! Almost everything you will ever need is available under System -> Administration -> Synaptic. What file are you trying to compile?

---

### Post by jlowerison on 2009-03-22
Sorry I should have been more clear, bad habit.

One of the forum threads said you need to type echo "1">/proc/acpi/acer/wireless to enable the switch through acpi but that location does not exist and I get an error when I input it into the terminal. As for the download I just downloaded this file from this link [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

### Post by jlowerison on 2009-03-22
This is the thread I got most of the information from if it helps - [http://ubuntuforums.org/showthread.php?t=224350&highlight=acer-acpi&page=10](http://ubuntuforums.org/showthread.php?t=224350&highlight=acer-acpi&page=10)

---

### Post by chili555 on 2009-03-22
I think this is superceded by *acerhk.* You might check with:```
lsmod | grep acerhk
```If the module *is* loaded, please try:```
sudo rmmod acerhk
sudo modprobe acerhk wlan_state=1
```Does that kick your wireless to life? If not, you might try:```
sudo rmmod acerhk
sudo modprobe acerhk autowlan=1
```

I'm feeling around in the dark here, as I don't own an Acer.

---

### Post by jlowerison on 2009-03-22
None of the commands worked. Got the following err
ERROR: Module acerhk does not exist in /proc/modules

Should I try installing the acpi or acpid with the synaptic package manger or is that not needed?

My command line understanding is pretty noob as they would say but I'm certain its just a matter of manually turning the wireless on.

---

### Post by chili555 on 2009-03-22
> ERROR: Module acerhk does not exist in /proc/modulesSurely it did not say */proc/modules.*On my computer, it's here:```
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/acerhk.ko
```If you do:```
sudo updatedb
```Wait a few moments for it to think, and then:```
locate acerhk.ko
```You will know where it is, if anywhere.

Which kernel are you running? Please do:```
uname -r
```Please post the result.> Should I try installing the acpi or acpid with the synaptic package mangerNo, because acer_acpi is obsolete, unless you are running an older kernel.

What is the exact model of your Acer?

---

### Post by jlowerison on 2009-03-22
Acer is Aspire One AOA-150 1262
Kernal is 2.6.27-14-generic

 locate acerhk.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/acerhk.ko
/lib/modules/2.6.27-13-generic/kernel/ubuntu/misc/acerhk.ko
/lib/modules/2.6.27-14-generic/kernel/ubuntu/misc/acerhk.ko
/lib/modules/2.6.27-7-generic/kernel/ubuntu/misc/acerhk.ko

---

### Post by chili555 on 2009-03-22
> you need to type echo "1">/proc/acpi/acer/wireless to enable the switch through acpi but that location does not existWhat does exist? It may not be exactly that, but close. We may need to look around a bit. Open Places -> Home folder and in the Location Bar, back out whatever is in there (/home/username, perhaps?) and type in /proc/acpi and press Enter. Can you see what looks likely and drill down to wireless?

---

### Post by jlowerison on 2009-03-22
> **chili555 said:**
> What does exist? It may not be exactly that, but close. We may need to look around a bit. Open Places -> Home folder and in the Location Bar, back out whatever is in there (/home/username, perhaps?) and type in /proc/acpi and press Enter. Can you see what looks likely and drill down to wireless?

The folders I have under /proc/acpi/ are as follows;
ac_adapter
battery
button
fan
embedded_controller
power_resource
process_zone
video

the files are;
dsdt
event
fadt
info
sleep
wakeup

so I can't find any Acer or Wireless folders

---

### Post by beameup on 2009-03-22
I have an Acer Travelmate TM4502 which has the LED switch on front that wasn't working until I found the attached instructions on a forum.

You may have to modify it for your model, I'm not sure. Here's my output info.

>  *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:c3:7c:e0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.0.1.200 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g


---

### Post by jlowerison on 2009-03-22
thanks i'll read it over and give it a try

---

### Post by chili555 on 2009-03-22
Except you don't have an ipw2200. I doubt this will work with ndiswrapper.

---

### Post by jlowerison on 2009-03-22
Ya it won't work but thanks for your input, I appreciate it.

---

### Post by chili555 on 2009-03-22
What is the output of:```
ndiswrapper -l
```We need to see the whole thing, so jot it down exactly, please. Thanks.

---

### Post by jlowerison on 2009-03-22
> **chili555 said:**
> What is the output of:```
ndiswrapper -l
```We need to see the whole thing, so jot it down exactly, please. Thanks.

output is;
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

### Post by chili555 on 2009-03-22
We're getting closer, I think. Now please let me see:```
lsmod | grep ndis
lsmod | grep ath
```Those are two separate commands followed by 'Enter.' That funny little | is over on the right of your keyboard, with \, at least on my US keyboard. Thanks.

---

### Post by jlowerison on 2009-03-22
> **chili555 said:**
> We're getting closer, I think. Now please let me see:```
lsmod | grep ndis
lsmod | grep ath
```Those are two separate commands followed by 'Enter.' That funny little | is over on the right of your keyboard, with \, at least on my US keyboard. Thanks.

first one outputs

ndiswrapper           196380  0 
usbcore               149488  5 uvcvideo,ndiswrapper,ehci_hcd,uhci_hcd

second one outputs nothing

---

### Post by chili555 on 2009-03-22
Good. That means ndiswrapper is loaded and the native driver, *ath_pci* is not.

Does:```
iwconfig
```show us any wireless interface? I am suspicious that the wireless may actually work without the LED...maybe.

---

### Post by jlowerison on 2009-03-22
> **chili555 said:**
> Good. That means ndiswrapper is loaded and the native driver, *ath_pci* is not.

Does:```
iwconfig
```show us any wireless interface? I am suspicious that the wireless may actually work without the LED...maybe.

output of iwconfig was
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by jlowerison on 2009-03-22
hey Chili,

I noticed quite a few people use the madwifi instead of the ndiswrapper for the acers, do you think it would make a difference. heres a quote from a ubuntu aspire one doc;

There has been some confusion as to which wireless driver provides the best performance and reliability. I have found the following:

    * madwifi from kernel (ath_pci) - does not attach to hardware.
    * ath5k from intrepid backports (ath5k) - connects to hardware, but experiences disconnects on medium to heavy wireless activity, and can not communicate with some AP's using WPA2 PSK.
    *

      madwifi-hal from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) (ath_pci) - Everything works.

---

### Post by chili555 on 2009-03-22
Please check your private messages.

---

### Post by beameup on 2009-03-23
FYI: My wireless did work without the LED (and so did the switch). The instructions I posted only made the LED work.

---

### Post by chili555 on 2009-03-23
> **jlowerison said:**
> hey Chili,

I noticed quite a few people use the madwifi instead of the ndiswrapper for the acers, do you think it would make a difference. heres a quote from a ubuntu aspire one doc;

There has been some confusion as to which wireless driver provides the best performance and reliability. I have found the following:

    * madwifi from kernel (ath_pci) - does not attach to hardware.
    * ath5k from intrepid backports (ath5k) - connects to hardware, but experiences disconnects on medium to heavy wireless activity, and can not communicate with some AP's using WPA2 PSK.
    *

      madwifi-hal from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) (ath_pci) - Everything works.

I think we need to trick the wireless radio on first. Please try:```
sudo gedit /etc/modprobe.d/options
```Add a new line:```
options rfkill default_state=1
```Check your work, save and close gedit. Now, please reboot. Any signs of life from the wireless?

---

### Post by chili555 on 2009-03-23
If your wireless does't work, please issue these commands:```
sudo /usr/bin/setkeycodes e055 159
sudo /usr/bin/setkeycodes e056 158
```Now manipulate the switch. Any signs of life? Let's not depend on the LED exclusively. Please do:```
sudo tail -f /var/log/messages
```Leave the terminal open and see if the kernel notifies us that the wirless switch is toggling.

---

### Post by chili555 on 2009-03-24
Post #25 here looks a bit promising: [http://forum.slitaz.org/viewtopic.php?id=1263&p=2](http://forum.slitaz.org/viewtopic.php?id=1263&p=2)

---


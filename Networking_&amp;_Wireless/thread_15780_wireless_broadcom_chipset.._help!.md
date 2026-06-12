---
title: "wireless broadcom chipset.. help!"
date: 2005-02-16
forum: Networking &amp; Wireless
---

### Post by Xirdneh on 2005-02-16
HI, i have a DELL 8600 laptop, DELL 1450 wireless Dual Band MIni-Pci
(broadcom chipset), i use ubuntu linux with 2.6.8.1-4-386 kernel... i
have installed ndiswrapper and cant get my wireless card to work, i have
this problem since 1 month ago... this is what dmesg say:ndiswrapper
  version 1.0 loaded (preempt=yes,smp=no)
  ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) added
  ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 7 (level, low) -> IRQ 7
  ndiswrapper (NdisWriteErrorLogEntry:266): log: C000138D, count: 1
  (00000103), return address: e0986be3, entry: e09878c8 offset: -3301
  ndiswrapper (ndiswrapper_add_one_pci_dev:184): Windows driver couldn't
  initialize the device (C0000001)
  ndiswrapper: probe of 0000:02:03.0 failed with error -22
......
this is what lspci say:
  0000:02:03.0 Network controller: Broadcom Corporation BCM4309
  802.11a/b/g (rev 03)
        Subsystem: Dell Computer Corporation: Unknown device 0003
        Flags: fast devsel, IRQ 7
        Memory at faff6000 (32-bit, non-prefetchable)
....
this is what cat say:
# cat /proc/interrupts
           CPU0
  0:   48461579          XT-PIC  timer
  1:       5466          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:      12592          XT-PIC  Intel 82801DB-ICH4, Intel 82801DB-ICH4
Modem
  8:          1          XT-PIC  rtc
  9:          2          XT-PIC  acpi
 11:    1038051          XT-PIC  uhci_hcd, uhci_hcd, uhci_hcd, ehci_hcd,
yenta, ohci1394, eth0, nvidia
 12:        403          XT-PIC  i8042
 14:      90246          XT-PIC  ide0
 15:     435675          XT-PIC  ide1  
NMI:          0  
LOC:   48461292
ERR:          0
MIS:          0
....
like there says, the device cant be initialize so i figure out the card
isnt on at all... maybe is a problem with acpi, i tryed acpi=off and
acpi=noirq... and the samething happens... really im lost here, a little
help plz..
thanx and sorry for my english, not my mother lenguage.

---

### Post by alastair on 2005-02-16
It's painful sometimes - especially with proprietary drivers/devices.

I can't help except suggest you do some reading to see if others have found this issue and perhaps solved it e.g.

google for : ndiswrapper bcmwl5a

Good luck.

---

### Post by delltony on 2005-02-16
if you know your service tag which should be on your dell computer then go to dells site the network drivers are there.
Do the following after you get the driver
example i have a dell inspiron 9100
[list=1]
[*]download driver from dell
[*]download the ndiswrapper package i believe its in universe
[*]type ndiswrapper -i bcmw15a.inf
[*]type modprobe ndiswrapper
[*]type ndiswrapper -l to list the device and see if its present
[*]type ndiswrapper -m to make the module alias of wlan0
[*]go to networking in gnome under computer->system config->network and then add the wireless of wlan0
[/list] 

hope this helps
also for your laptop something you might want to try 
at the # type xev and get your keycodes for the fancy buttons on your lappy
then make note of those codes
> I found a userspace daemon called LinEAK  (Do an "
apt-get install lineakd

which is a program that will catch all those special keys on your computer. It's dead simple to set up and use, and you can program the keys to do whatever you want. For instance, I have mine set so that the Play button runs a script that I have set up to play music using xmms.

To add support in lineakd for the XPS special buttons, add the following to the bottom of your lineakd.def file. This is in /etc/lineakd.def in Debian, might be in /usr/share/lineakd under another distro. (Don't change /usr/share/lineakd/lineakd.def in Debian, as it won't affect anything).

[DXPS]
brandname = "Laptop/notebook"
modelname = "Dell XPS and Inspiron 9100"
[KEYS]
Play = 162
Previous = 144
Next = 153
Stop = 164
VolumeUp = 176
VolumeDown = 174
Mute = 160
[END KEYS]
[END DXPS]

After you change the file, type:
lineakd -l

To make sure that you edited the corect file and have support installed, then type: $
lineakd -c DXPS

To make a config file in $HOME/.lineakd/lineakd.conf.
Edit this file and add commands for what you want the keys to do.
My commands are: Mute = "aumix -w 0" Next = "xmms --fwd" Play = "xmms --play-pause" Previous = "xmms --rew" Stop = "xmms --stop" VolumeDown = "aumix -w -5" VolumeUp = "aumix -w +5"
Then type:
lineakd&  

hope this helps you

---

### Post by Xirdneh on 2005-02-16
thnx for you repllays.
yea i have read a lot and nothing seems to work...
i have installed ndiswrapper, run modprobe and everything also change my /etc/modules file here is what ifwconfig say:

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

when i try to set up a profile for wlan0 it tells me that there are no devices. i think the problem is initializing the device.... I think this will help also

# ndiswrapper -m
modprobe config already contains alias directive

so as you see the problem is not in the driver or the instalation of ndiswrapper, or at least i dont hink :s... any ideas?
thanx a lot!

---

### Post by Lindo on 2005-02-17
I'm having the same problem, i have a dell 8600 aswell and also with the 1450 chipset.
All went well untill i use the ndiswrapper modprobe command, it says it cant add ndiswrapper.ko to the driverlist or something. when i do ndiswrapper -l it says that the driver bcmwl5.inf is broken, i also tried bcmwl5a.inf but that didnt work either, i don't know which .inf file to pick. Any suggestions ?

---

### Post by Xirdneh on 2005-03-01
FINALLY!!!!, after weeks and weeks of exaustive investigation, after reading a lot of forums and some howtos etc.. till 4 am i have finally done it, hope this will help to other people

the sintoms are listed above... my laptop and the problem with the wireless

what i do is that i installed WINE so i downloades the latest dirvers for my wireless 1450 Dual Band from Dell.com.. i had to run it with wine because is a .exe then unzipped all the files in one directory... sorry let me tell you that i had to install ndiswrapper-utils with synaptic but because there was only ndiswrapper-utils .10 version so i needed to uninstal the newest ndiswrapper and install version .10.. i uninstalled the older driver and then run this on the folder that you have the bcmlw5.inf and .sys files...
ndiswrapper -i bcmlw5.inf
ndiswrapper -i bcmlw.inf (not too shure about this one but i guess it helped)

then it occures to me!, i needed to remove the older modeprobe of ndiswrapper so i did this
rmmod ndiswrapper

and then just make another modprobe
modprobe ndiswrapper

and it all just worked like a charm :D...
hope this help some other people cuz i have seen this problem several times...
also this corrects the -22 problem with ndiswrapper, at least for me :p...
have to say im new at this linux thingy so sorry if there are some technical definitions that i got wrong

---

### Post by guido911 on 2005-04-14
Xirdneh!!!  You rock!

It works!

Thank you SO much!

I've had a huge headache because of this.

Thanks again!!!!

---

### Post by scottylans on 2005-07-10
Does this actually give ubuntu full access to the card?

The ability to sniff packets etc and use it with airsnort / kismet etc?

---

### Post by barry_s on 2005-10-15
Thanks Xirdneh, your advice really helped. 

One comment to add though, is that although the dell driver is a .exe file, it is in fact a self extracting zip file, so there is no need to use WINE or Windows, just use unzip to extract the files.

barry

---


---
title: "Wireless connects but doesn't work"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Marctwo on 2010-07-03
Hi all,

I installed ubuntu 10.04 yesterday on my Toshiba Tecra M2.  I'm using the same static ip, etc.  for both wired/wireless connections.  Wired is fine but wireless won't even ping the router.  It seems to connect without issue though???

This is my first look at Linux so I'm a fish out of water.  I did come across the relevant (I think) driver project on sourceforge.  Maintained by Intel, it was apparantly "included in the kernel years ago" which makes me think it should be ok... but what do I know. :)

So I don't realy know what to try... or how to try it...  Help... Please...

---

### Post by roosh on 2010-07-03
could right-click the network icon on the top right, click on "connection information" and tell me what it displays for "driver:"

---

### Post by Marctwo on 2010-07-03
Hi roosh,

The driver is ipw2200.

---

### Post by roosh on 2010-07-03
In a terminal, could you type in ```
lsmod
```
and then copy-paste back the output here

---

### Post by Marctwo on 2010-07-03
Not sure if you wanted all of the output but here it is anyway:

```

mak@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
usb_storage            39425  2 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
nouveau               467048  2 
joydev                  8708  0 
pcmcia                 33024  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49943  1 nouveau
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29297  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
drm                   162471  4 nouveau,ttm,drm_kms_helper
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  2 
i2c_algo_bit            5028  1 nouveau
ipw2200               135216  0 
rsrc_nonstatic         10015  1 yenta_socket
ppdev                   5259  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
libipw                 39896  1 ipw2200
parport_pc             25962  1 
lib80211                5046  2 ipw2200,libipw
soundcore               6620  1 snd
video                  17375  0 
intel_agp              24177  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
output                  1871  1 video
lp                      7028  0 
psmouse                63245  0 
toshiba_acpi            8662  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28820  0 
serio_raw               3978  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
e1000                  97396  0 
ieee1394               81181  1 ohci1394

```

---

### Post by roosh on 2010-07-03
could you also do the same for ```
lsusb
``` ```
lspci
``` make sure the wireless device is attached when you do these

---

### Post by Marctwo on 2010-07-03
The wireless is integrated so attached.  Should I connect with it before running the cmds or just leave it disconnected?

Is there any other info I should get while I have ubuntu loaded?

---

### Post by roosh on 2010-07-03
I think the main thing is just making sure the device is connected while running the commands. Having it connected at boot is a good idea too.

---

### Post by Marctwo on 2010-07-04
OK, with wireless saying it's connected, here are the cmds:

lsusb
```
mak@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci
```
mak@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

```

---

### Post by roosh on 2010-07-04
It looks like the Ubuntu driver is loaded, but fails to work correctly. I know of one workaround, ndiswrapper. Based on the computer model you gave me, here are the steps:

Try this:

1) install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-common 
sudo apt-get install ndisgtk

```


2) get the correct [COLOR="Black"]windows XP[/COLOR] drivers based on your system architecture (32-bit vs. 64-bit). I'm pretty sure you have a 32-bit machine. If you are not sure, post the output of: ```
uname -a
``` and I'll see.
I think I have been able to find the XP driver's from Toshiba's website, under the Tecra M2 model. Please make sure that that is indeed your computer model. Here is the link to the windows XP driver: [http://cdgenp01.csd.toshiba.com/content/support/downloads/intel-wifi2x.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/intel-wifi2x.exe). Download it and you should be able to open it simply by double-clicking on it.


3) Put all the files together in a folder. (Extract all the files inside to a folder)


4) Temporarily disable the driver that doesn't work (the one that came with Ubuntu):
```
sudo rmmod ipw2200
```


5) Use the graphical interface with ndiswrapper to install the driver (system --> administation --> windows drivers). [SIZE="4"]Or[/SIZE] use the command: ```
sudo ndiswrapper -i [COLOR="Red"]"path to inf file"[/COLOR]
```

note: [COLOR="Red"]"path to inf file"[/COLOR] should be replaced by the actual path to the .inf file in the folder


6) It should now be installed. Activate ndiswrapper: ```
sudo modprobe ndiswrapper
```


7) Wait a while (~1 minute). Then check the network box at the top -- you should be able to find a network.


8) If it works, then permanently disable any other drivers that would interfere:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
at the bottom copy and paste the following to the file:
```
blacklist ipw2200
```


9) Make sure ndiswrapper starts at boot: a good guide can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up)

---

### Post by Marctwo on 2010-07-04
Thanks roosh,

The cmdline install of ndiswrapper had mixed results and when trying to then install the driver, the system froze on all of 3 or 4 attempts.  I then removed and reinstalled ndiswrapper through the software centre and was able to install the driver using the gui.

However, 'sudo modprobe ndiswrapper' couldn't find ndiswrapper so I can't actually start it to see if it solves the problem.

*edit: I noticed in this reply that I'd made typo's in writing ndiswrapper (now corrected).  I thought I may have done the same in testing so after trying again the modprobe did work.  However, the system froze again on connecting.

I'd imagine this is likely to point to a problem with the windows driver so I'll do a bit of checking and see if I can find one that doesn't freeze.

---

### Post by Marctwo on 2010-07-04
Well, I've tried a few more drivers now and all of them cause the system to freeze on connecting.

Getting back to the native Linux driver, I found an open bug on Launchpad about ipw2200 requesting firmware.  I did a 'dmesg' and found a few firmware request lines so I may be subject to this bug.  And given the age and apparent lack of interest in this bug, it may be one that doesn't inspire an urgent resolution. :(

---

### Post by Marctwo on 2010-07-04
OK, I've sorted the connection out.

The Problem: My router doesn't broadcast so in ubuntu I created a new connection, edited it to set the appropriate details and selected it when connecting to a hidden network from the menu.  This didn't work.

The Solution: With no connection, I set the ESSID and Channel via iwconfig.  This then appeared as a network option in the menu.  Choosing this menu option didn't get me connected straight away but it did then appear as a new configuration in my wireless connections.  I edited this new configuration as I had previously but this time it worked.

My problem now is that messing about with ndiswrapper has left that automatically loading and ipw2200 not loading.  How can I change this back to normal?

BTW: I'm posting this on ubuntu, wireless. :)

---

### Post by roosh on 2010-07-05
Ok so just go back and do:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and delete out the line that you added: (this)
```
blacklist ipw2200
```
and save.

To stop ndiswrapper, I think the simplest way is to uninstall all the packages you installed for it (via synaptic, just search for ndis and remove everything that has to do w/ ndiswrapper)
There are a few more things you should do if you did step 9, but I don't think you got that far with ndiswrapper. Please let me know if you did...


Alternatively, if you want to keep ndiswrapper, you could just stop it from loading at boot:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and add this at the end of the file:
```
blacklist ndiswrapper
```



Also, I'd like to ask if you remembered step 4, disabling the Ubuntu driver for the card (sudo rmmod ipw2000) when doing the ndiswrapper. Not doing so could cause a system freeze.

---

### Post by Marctwo on 2010-07-05
I didn't get as far as blacklisting ipw2200.  I checked all the files in /etc/modprobe.d/ anyway and couldn't find any mention of it.

I did remove all the ndiswrapper components using the software centre but it's still present when I do 'lsmod'.  There is a file '/etc/modprobe.d/ndiswrapper';  Could that be causing problems?  I can't delete it from the file browser as it belongs to 'root' which I believe is some kind of special admin account.

*edit:  OK, I did 'sudo rm /etc/modprobe.d/ndiswrapper' and now ndiswrapper is gone and ipw2200 is loaded at startup.  So I think that's an end to this particular issue.

Thanks for your help, roosh.

---

### Post by roosh on 2010-07-05
You're welcome, but I didn't seem much help :)

---

### Post by Marctwo on 2010-07-05
> **roosh said:**
> You're welcome, but I didn't seem much help :)More helpful than it may seem.  Seeing how you form ideas helps me form ideas.  Having someone to bounce ideas off.  Even just knowing that someone is trying to help.  All of this helps. ;)

---


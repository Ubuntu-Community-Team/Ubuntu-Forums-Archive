---
title: "wpa and network manager"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by black veils on 2012-07-20
i have been trying to get wireless working on an old laptop with for someone who has wpa encryption. it seems to have driver support, and detects networks, but i cant get it to connect with wpa using network manager or wicd. yes wpa-supplicant is installed (if actually needed), i even tried messing about with a config file for it (following official website).

network manager doesnt have any wpa option in the dropdown box, so i went to edit connections, and this didnt enable it to do anything either (tried after reboot also).

wicd kept saying bad password, despite making sure to remove all remnants of network manager, and obviously rebooting.

i am confused as to why it wont work, seems like it should.

here is some info
```


nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sis900
  State:             connected
  Default:           yes
  HW Address:        00:E0:18:D4:90:01

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            hostap_pci
  State:             disconnected
  Default:           no
  HW Address:        00:05:3C:07:82:3C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AndroidBlackVeils: Infra, 70:05:14:88:D1:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WEP
```


and where it says AndroidBlackVeils is wep, its wpa2

---

### Post by chili555 on 2012-07-20
> AndroidBlackVeils: Infra, 70:05:14:88:D1:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 [COLOR="Red"]WEP[/COLOR]Network Manager thinks it's WEP and isn't going to give you a WPA dropdown for a WEP network. Let's bypass NM altogether:```
sudo iwlist wlan0 scan
```Does it say WEP or WPA? Can you double-check the encryption method in the administration pages of the hotspot?

This may be useful: [http://wicd.sourceforge.net/punbb/viewtopic.php?id=649](http://wicd.sourceforge.net/punbb/viewtopic.php?id=649)

---

### Post by black veils on 2012-07-20
```
wlan0     Scan completed :
          Cell 01 - Address: 70:05:14:88:D1:C6
                    ESSID:"AndroidBlackVeils"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

```


yes the problem is the person's network is encrypted with wpa (per their choice), and couldnt get this laptop to connect to it. they had the same problem as me, i am testing it with my android phone hotspot, so i know it is wpa.

---

### Post by chili555 on 2012-07-20
> wlan0     Scan completed :
          Cell 01 - Address: 70:05:14:88:D1:C6
                    ESSID:"AndroidBlackVeils"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10Looks like perfect WEP to me. This is what WPA scans like:> Cell 01 - Address: xx:13:10:62:8D:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000450654bf6c
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    [COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK[/COLOR]
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020010000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
What does this tell us?```
iwconfig
dmesg | grep hostap
```

---

### Post by chili555 on 2012-07-20
Further research: [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/36718](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/36718)> since hostap right now defaults to start in *Master mode(as an access point)*, while mode 2 / Managed mode
is the one needed to work as a client.So, if your iwconfig shows *Mode:Master*, then do:```
sudo modprobe -r hostap_pci
sudo modprobe hostap_pci iw_mode=2
```Now can you connect? If so, we'll write a quick file and make it permanent.

---

### Post by black veils on 2012-07-20
```

iwconfig

wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

eth0      no wireless extensions.



dmesg | grep hostap

[   15.740470] hostap_pci 0000:00:0c.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   15.741931] hostap_pci: Registered netdevice wifi0
[  188.832136] Modules linked in: dm_crypt joydev snd_intel8x0 pcmcia ppdev snd_ac97_codec ac97_bus snd_pcm snd_timer parport_pc snd irda hostap_pci hostap soundcore asus_laptop sparse_keymap crc_ccitt input_polldev lib80211 snd_page_alloc psmouse shpchp i2c_sis96x serio_raw yenta_socket pcmcia_rsrc pcmcia_core lp parport mac_hid vesafb floppy sis900 sis_agp


```

---

### Post by chili555 on 2012-07-20
> wlan0     IEEE 802.11b  ESSID:"[COLOR="Red"]g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A[/COLOR]"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: None   I don't know if this means you have a very unhappy driver or if you just haven't associated with an AP yet. So far, your readings are unremarkable.

Sometimes a competing driver loads. Please check:```
lsmod | grep -e orin -e host
```Let's also look at the entire message log. We'll copy it to a text file, zip it and you can post it here for our examination:```
dmesg > veils.txt
zip veils.zip veils.txt
```Look in your user directory and find the file veils.zip. Post it in your reply using the paperclip tool at the top of the reply box.

---

### Post by black veils on 2012-07-20
```

lsmod | grep -e orin -e host

hostap_pci             52851  2 
hostap                106404  1 hostap_pci
lib80211               14040  2 hostap_pci,hostap

```

---

### Post by chili555 on 2012-07-20
I notice this:> [   12.634537] wifi0: NIC: id=0x8013 v1.0.0
[   12.634702] wifi0: PRI: id=0x15 v1.0.7
[   12.634860] wifi0: STA: id=0x1f v[COLOR="Red"]1.3.6[/COLOR]Please see this site: [http://wiki.debian.org/hostap](http://wiki.debian.org/hostap)> WPA support requires station firmware version 1.7.4 or later. Also see: [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

Flashing the firmware has been mention as a solution at post #29 here: [http://ubuntuforums.org/showthread.php?t=1738941&page=3](http://ubuntuforums.org/showthread.php?t=1738941&page=3)

---

### Post by black veils on 2012-07-20
thank you, i will have a look at those links


EDIT:

i have been rereading things, here are my queries:

1. Download hostap package from CVS or a release
that is dated after Aug 3, 2003. Release 0.1.0 or later
have this feature as well.

[just hostap utils in synaptic?]

2. Enable PRISM2_DOWNLOAD_SUPPORT and
PRISM2_NON_VOLATILE_DOWNLOAD in driver/
modules/hostap_config.h. You simply just
uncomment those two define's.

[i remove all hash symbols from the start of relevant lines?]

3. Compile the driver and install them to the kernel
using your favorite method.

[how?]

4. cd utils and make prism2_srec program.

[what do i do for this step?]

5. Download the firmware files that you want to
upgrade to.

6. NOTE THAT YOU HAVE TO RUN prism2_srec AS
ROOT. Do a test run with
prism2_srec -v wlan0 <primary firmware> <station firmware>

[i enter sudo etc^ in terminal and just look at output?]

Note if you only need to flash station firmware,
simply omit the "primary firmware" argument.
However, NEVER NEVER flash primary firmware
alone!!!

7. Check for any incompatiable warnings in the
previous test run. If things look OK, keep your
finger crossed and run

prism2_srec -v -f wlan0 <primary firmware> <station firmware>

or simply if you only update station firmware
prism2_srec -v -f wlan0 <station firmware>


[if i made a mistake, would the computer be corrupted, or would reinstalling a linux distro fix it? not that i want to reinstall, i just configured everything! it is bodhi linux, based on ubuntu]

[the commands which say about primary and secondary, do i put the names of files i downloaded instead?]

yes messing with drivers is out of my league.

---

### Post by matt_symes on 2012-07-21
Hi

Hopefully chili555 wont mind me adding some input here.

First i should state, this is from these kernel sources.

```

linux_3.4.0-4.9/ubuntu-quantal
```These are the earliest ones i currently have on this machine.

From this web page [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/) ..

> Enable PRISM2_DOWNLOAD_SUPPORT and PRISM2_NON_VOLATILE_DOWNLOAD in driver/modules/hostap_config.h.It seems the hostap_config.h file has been moved.
```

matthew@matthew-Aspire-7540 ~/storage/linux_3.4.0-4.9/ubuntu-quantal
 % find . -name "hostap_config.h"              
./drivers/net/wireless/hostap/hostap_config.h
matthew@matthew-Aspire-7540 ~/storage/linux_3.4.0-4.9/ubuntu-quantal
```It also seems these defines are now enabled.

For PRISM2_DOWNLOAD_SUPPORT from ./drivers/net/wireless/hostap/hostap_config.h

```

/* Include code for downloading firmware images into volatile RAM. */
**#define PRISM2_DOWNLOAD_SUPPORT**

```and for PRISM2_NON_VOLATILE_DOWNLOAD, CONFIG_HOSTAP_FIRMWARE_NVRAM needs to be set to yes.

```

matthew@matthew-Aspire-7540 ~/storage/linux_3.4.0-4.9/ubuntu-quantal
 % grep -r CONFIG_HOSTAP_FIRMWARE_NVRAM .            
<snip>
./debian.master/config/config.common.ubuntu:**CONFIG_HOSTAP_FIRMWARE_NVRAM=y**
matthew@matthew-Aspire-7540 ~/storage/linux_3.4.0-4.9/ubuntu-quantal
```and this enables PRISM2_NON_VOLATILE_DOWNLOAD in  ./drivers/net/wireless/hostap/hostap_config.h

```

/* Allow kernel configuration to enable non-volatile download support. */
#ifdef *CONFIG_HOSTAP_FIRMWARE_NVRAM*                 [COLOR=Blue](defined because of CONFIG_HOSTAP_FIRMWARE_NVRAM=y above)[/COLOR]
#define **PRISM2_NON_VOLATILE_DOWNLOAD**
#endif
```Therefore, i don't think you need to build the drivers. You will need to check you kernel sources though, as i have.

That may be one less step for you.

Kind regards

---

### Post by chili555 on 2012-07-21
I don't mind at all, matt_symes, and I believe you are correct, he probably doesn't need to build the drivers.> [just hostap utils in synaptic?]Yes, exactly. It already includes prism2_srec.> 2. Enable PRISM2_DOWNLOAD_SUPPORT and
PRISM2_NON_VOLATILE_DOWNLOAD in driver/
modules/hostap_config.h. You simply just
uncomment those two define's.

[i remove all hash symbols from the start of relevant lines?]

3. Compile the driver and install them to the kernel
using your favorite method.

[how?]

4. cd utils and make prism2_srec program.

[what do i do for this step?]
^^^ Skip all this.> 6. NOTE THAT YOU HAVE TO RUN prism2_srec AS
ROOT. Do a test run with
prism2_srec -v wlan0 <primary firmware> <station firmware>

[i enter sudo etc^ in terminal and just look at output?]
Yes, exactly.> [if i made a mistake, would the computer be corrupted, or would reinstalling a linux distro fix it? not that i want to reinstall, i just configured everything! it is bodhi linux, based on ubuntu]The computer will not be corrupted, but the wireless card might be. It is not for the faint of heart, however, going slowly, carefully and double-checking before you press Enter should produce a good result. The process to make a test run without burning the image to the cards flash memory is helpful. > [the commands which say about primary and secondary, do i put the names of files i downloaded instead?]Yes, exactly. I believe it is something like this, substituting your exact files of course:```
sudo prism2_srec -v wlan0 pk010004.hex s1010409.hex 
```

Please note:> Note if you only need to flash station firmware,
simply omit the "primary firmware" argument.
However, **NEVER NEVER** flash primary firmware
alone!!!Of course, you could always invest a few dollars in a new wireless device.

---

### Post by black veils on 2012-07-21
getting a new wireless device might be better, but i dont know anything about these things, and then the matter of linux hardware compatibility, and if it will be compatible with the old laptop ha

i appreciate your help, it might help someone else also.


EDIT:

also with another device, wouldnt it get confused, how would you make it use the external instead? hopefully i will learn something from this project :P

---

### Post by chili555 on 2012-07-21
Here is a little bit about hardware compatibility: [http://ubuntuforums.org/showpost.php?p=12117783&postcount=15](http://ubuntuforums.org/showpost.php?p=12117783&postcount=15)

You can keep the old device out of the picture by blacklisting its driver, hostap_pci.

Since you have the opportunity to do a non-destructive dry run, I'd suggest the firmware upgrade first. Choose wisely and don't blame Matt or me!!

---

### Post by black veils on 2012-07-21
> **chili555 said:**
> Here is a little bit about hardware compatibility: [http://ubuntuforums.org/showpost.php?p=12117783&postcount=15](http://ubuntuforums.org/showpost.php?p=12117783&postcount=15)

You can keep the old device out of the picture by blacklisting its driver, hostap_pci.

Since you have the opportunity to do a non-destructive dry run, I'd suggest the firmware upgrade first. Choose wisely and don't blame Matt or me!!


lol i would not blame you, that would be silly.

i was looking at wireless adapters, with the filter 'linux', on amazon. i realised there might be a problem with usb port speed, this laptop has 1.1 usb ports.

i will probably try the driver upgrade.

EDIT:

tried, got to the test and this is the output ```
sudo prism2_srec -v wlan0 /home/ray/Downloads/sf010804.hex
S3 CRC-16 generation record: start=0x007E1800 len=65536 prog=1
Start address 0x00000000
srec summary for sf010804.hex
Component: 0x001f 1.8.4 (station firmware)
Supported platforms:
  0x800a 1.0.0,  0x800b 1.0.0,  0x800c 1.0.0,  0x800d 1.0.0,  0x8012 1.0.0
  0x8013 1.0.0,  0x8014 1.0.0,  0x8016 1.0.0,  0x8017 1.0.0,  0x8018 1.0.0
  0x801a 1.0.0,  0x801b 1.0.0,  0x801c 1.0.0,  0x8021 1.0.0,  0x8022 1.0.0
  0x8023 1.0.0
Interface compatibility information:
  role=Supplier variant=4 range=1-15 iface=Station Firmware-Driver (4)
  role=Actor    variant=1 range=1-1 iface=Modem-Firmware (1)
  role=Actor    variant=2 range=1-1 iface=Controller-Firmware (2)
  role=Actor    variant=1 range=4-4 iface=Primary Firmware-Driver (3)
Separate S3 data areas:
S3 area count: 3
  addr=0x007E1800..0x007EEAF9 (len=54010)
  addr=0x007F0800..0x007F17FF (len=4096)
  addr=0x007FE000..0x007FECD1 (len=3282)
Total data length: 61388
Start address 0x00000000

Wireless LAN card information:
Components:
  NICID: 0x8013 v1.0.0
  PRIID: 0x0015 v1.0.7
  STAID: 0x001f v1.3.6
Interface compatibility information:
  PRI role=Supplier variant=1 range=1-1 iface=Modem-Firmware (1)
  PRI role=Supplier variant=2 range=1-1 iface=Controller-Firmware (2)
  PRI role=Supplier variant=1 range=4-4 iface=Primary Firmware-Driver (3)
  STA role=Supplier variant=1 range=1-9 iface=Station Firmware-Driver (4)
  PRI role=Actor    variant=2 range=1-1 iface=Controller-Firmware (2)
  STA role=Actor    variant=2 range=1-1 iface=Controller-Firmware (2)
  STA role=Actor    variant=1 range=1-1 iface=Modem-Firmware (1)

Verifying update compatibility and combining data:
Plugging PDR 0xffffffff at 0x007ee61e (len=14)
Plugging PDR 0x0202 at 0x007f1250 (len=100)
Plugging PDR 0x0203 at 0x007f12b4 (len=128)
Plugging PDR 0x0204 at 0x007f1434 (len=80)
Plugging PDR 0x0405 at 0x007f1484 (len=4)
PDR 0x0405 not found from wlan card PDA. Using default data.
  len=4: 00 00 00 30
Plugging PDR 0x0300 at 0x007f1488 (len=28)
Plugging PDR 0x0301 at 0x007f14a4 (len=34)
Plugging PDR 0x0101 at 0x007f16b0 (len=6)
Plugging PDR 0x0103 at 0x007ee5e0 (len=12)
Plugging PDR 0x0104 at 0x007ee718 (len=2)
Plugging PDR 0x0105 at 0x007f16bc (len=2)
Plugging PDR 0x0105 at 0x007ee74e (len=2)
Plugging PDR 0x0105 at 0x007f17bc (len=2)
Plugging PDR 0x0107 at 0x007ee5ee (len=2)
Plugging PDR 0x0006 at 0x007ee5ba (len=10)
Plugging PDR 0x0406 at 0x007f1750 (len=2)
PDR 0x0406 not found from wlan card PDA. Using default data.
  len=2: 64 00
Plugging PDR 0x0302 at 0x007f14cc (len=2)
PDR 0x0302 not found from wlan card PDA. Using default data.
  len=2: 12 00
Plugging PDR 0x0303 at 0x007f14ce (len=2)
PDR 0x0303 not found from wlan card PDA. Using default data.
  len=2: ff 1f
Plugging PDR 0x0412 at 0x007ee76e (len=6)
PDR 0x0412 not found from wlan card PDA. Using default data.
  len=6: 03 00 02 00 02 00
Plugging PDR 0x0413 at 0x0000118a (len=2)
Could not find data position for plugging PDR 0x0413 at 0x0000118a (len=2)
PDR 0x0413 is not in wlan card PDA and there is no default data. Ignoring plug record.
Plugging PDR 0x0414 at 0x007ee5f8 (len=36)
PDR 0x0414 not found from wlan card PDA. Using default data.
  len=36: 36 00 36 00 36 00 04 00 01 00 03 00 3b 00 3b 00 40 00 06 00 01 00 03 00 40 00 40 00 4a 00 08 00 01 00 03 00
Generating CRC-16 (start=0x007e1800, len=65536) at 0x007e17fe
OK.

```

i am guessing i have to do those 3 steps after all?

---

### Post by matt_symes on 2012-07-23
Hi

By the looks of it, no errors or major warnings were returned from the dry run.

Assuming the defaults are good and and the PDRs updated are the ones causing the problems, this could fix your issue. (i emphasise could)

You have to balance the fact that this may fix the issues against the fact, if it all goes wrong, you will not have a working wireless connection.

I have never owned one of your wireless cards so it's hard for me to advise here.

What do you think chili555 ?

Have you tried ebay for a suitable wireless card ?

Kind regards

---

### Post by black veils on 2012-07-23
i am not against getting a wireless card, other than will it work with 1.1 usb port?  we just both thought it made sense to try the upgrade, if it fails, then try adapter.

---

### Post by chili555 on 2012-07-23
I apologize; I didn't see your edit. New posts trigger notification emails but edits do not.> You have to balance the fact that this may fix the issues against the fact, if it all goes wrong, you will not have a working wireless connection.

I have never owned one of your wireless cards so it's hard for me to advise here.

What do you think chili555 ?I agree entirely. I suggest you proceed. Please be sure the laptop battery is fully charged and that the laptop power supply is plugged in so there is very little chance of a power outage while the firmware flash is under way. Good luck and let us know.

---

### Post by black veils on 2012-07-23
lol it worked. but i think maybe it needs primary updated too? it connected, i loaded a website, then it died

---

### Post by chili555 on 2012-07-23
Please reboot so we have a clean slate, connect and if it dies, run and post:```
sudo cat /var/log/syslog | grep -e host -e etwork | tail -n 20
```I probably would have upgraded *BOTH* firmware parts at once, but let's see the logs first.

---

### Post by black veils on 2012-07-23
i hunted for a compatible primary, and did the process again with both primary and station. all seemed good.

i rebooted, connected to the wireless. it works fine for a few seconds, then it either disconnects or slows so much that it may as well be dead.

i understand that using my phone as a hotspot is not going to be fast, but as i said, it works, then it doesnt, and i had tested the wifi with other devices, no problems.

i dont know if there was a disconnection, but thought i would post anyway (didnt get all i intended to, because i didnt realise plugging in the wire would wipe info).

```

sudo cat /var/log/syslog | grep -e host -e etwork | tail -n 20

Jul 23 14:05:04 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul 23 14:05:04 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 23 14:05:04 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jul 23 14:05:04 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul 23 14:05:05 Bodhi NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Jul 23 14:05:07 Bodhi NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jul 23 14:05:07 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 23 14:05:07 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 23 14:05:07 Bodhi NetworkManager: <info>    address 192.168.43.119
Jul 23 14:05:07 Bodhi NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 23 14:05:07 Bodhi NetworkManager: <info>    gateway 192.168.43.1
Jul 23 14:05:07 Bodhi NetworkManager: <info>    hostname 'Bodhi'
Jul 23 14:05:07 Bodhi NetworkManager: <info>    nameserver '192.168.43.1'
Jul 23 14:05:07 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 23 14:05:07 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 23 14:05:07 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 23 14:05:08 Bodhi NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jul 23 14:05:08 Bodhi NetworkManager: <info>  Policy set 'Auto AndroidBlackVeils' (wlan0) as default for routing and DNS.
Jul 23 14:05:08 Bodhi NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jul 23 14:05:08 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.

```

---

### Post by chili555 on 2012-07-23
Your *syslog* looks awesomely perfect!! We see no disconnect or slowdown so I'm not sure what to fix. I suggest you wait until it actually disconnects and try again:```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```The 'tail' filter will just show the latest 20 lines.

---

### Post by black veils on 2012-07-23
lol  i think something happened here, the net went very slow (halted), and eventually got speedy

```
sudo cat /var/log/syslog | grep -e host -e etwork | tail -n 20
Jul 23 14:51:30 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 23 14:51:30 Bodhi NetworkManager: <info>    address 192.168.43.119
Jul 23 14:51:30 Bodhi NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 23 14:51:30 Bodhi NetworkManager: <info>    gateway 192.168.43.1
Jul 23 14:51:30 Bodhi NetworkManager: <info>    hostname 'Bodhi'
Jul 23 14:51:30 Bodhi NetworkManager: <info>    nameserver '192.168.43.1'
Jul 23 14:51:30 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 23 14:51:30 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 23 14:51:30 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 23 14:51:31 Bodhi NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jul 23 14:51:31 Bodhi NetworkManager: <info>  Policy set 'Auto AndroidBlackVeils' (wlan0) as default for routing and DNS.
Jul 23 14:51:31 Bodhi NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jul 23 14:51:31 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 23 14:59:36 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jul 23 14:59:36 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 23 14:59:40 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 23 14:59:40 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jul 23 14:59:40 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 23 14:59:40 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 23 14:59:40 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed

```


EDIT:

more weirdness

```

Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 23 15:15:56 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 23 15:15:56 Bodhi NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto AndroidBlackVeils' has security, and secrets exist.  No new secrets needed.
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Config: added 'ssid' value 'AndroidBlackVeils'
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jul 23 15:15:56 Bodhi NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 23 15:15:56 Bodhi NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 23 15:15:56 Bodhi NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 23 15:15:56 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 23 15:16:01 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 23 15:16:06 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 23 15:16:06 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

sudo cat /var/log/syslog | grep -e host -e etwork | tail -n 20

Jul 23 15:17:11 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul 23 15:17:11 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 23 15:17:11 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jul 23 15:17:11 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul 23 15:17:11 Bodhi NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jul 23 15:17:12 Bodhi NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jul 23 15:17:12 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 23 15:17:12 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 23 15:17:12 Bodhi NetworkManager: <info>    address 192.168.43.119
Jul 23 15:17:12 Bodhi NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 23 15:17:12 Bodhi NetworkManager: <info>    gateway 192.168.43.1
Jul 23 15:17:12 Bodhi NetworkManager: <info>    hostname 'Bodhi'
Jul 23 15:17:12 Bodhi NetworkManager: <info>    nameserver '192.168.43.1'
Jul 23 15:17:12 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 23 15:17:12 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 23 15:17:12 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 23 15:17:13 Bodhi NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jul 23 15:17:13 Bodhi NetworkManager: <info>  Policy set 'Auto AndroidBlackVeils' (wlan0) as default for routing and DNS.
Jul 23 15:17:13 Bodhi NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jul 23 15:17:13 Bodhi NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.

```

---

### Post by chili555 on 2012-07-23
Well, we have made some progress! You can actually connect to a WPA network now. However:> <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 23 15:16:01 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 23 15:16:06 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 23 15:16:06 Bodhi NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanningSometimes, this is caused, I believe, by wpa_supplicant. It seems to like WPA2 only or WPA only and not any kind of mixed mode. What is your access point set to?```
sudo iwlist wlan0 scan
```Sometimes, it's caused by power management. Is it on or off?```
iwconfig
```Thanks.

---

### Post by black veils on 2012-07-24
lol indeed!


```
sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 70:05:14:88:D1:C6
                    ESSID:"AndroidBlackVeils"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-32 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

```
iwconfig

wifi0     IEEE 802.11b  ESSID:"AndroidBlackVeils"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 70:05:14:88:D1:C6   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"AndroidBlackVeils"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 70:05:14:88:D1:C6   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-34 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0


```

i wonder, do you find it fun to help on the forums?  it is certainly strange for me to be posting, when i ordinarily sort things myself.

---

### Post by chili555 on 2012-07-24
I quite enjoy answering posts on the forum. I especially enjoy the great moment when a poster reports back that it's now working and I'm some kind of super-genius. Just kidding. I realize that after the wireless or ethernet is working, the poster can download software, email pictures of the cat to Grannie, instant message, etc. and begin to really enjoy Ubuntu and Linux. I like that feeling!

I also enjoy a mystery: How do we get strange and unusual devices with little or no knowledge base to work properly. 

I see that power management is off; that's good. I also see:> wlan0     IEEE 802.11b  ESSID:"AndroidBlackVeils"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 70:05:14:88:D1:C6   
          Bit Rate:11 Mb/s   [COLOR="Red"]Sensitivity=1/3[/COLOR]
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-34 dBm  Noise level=-96 dBmAccording to *man iwconfig*:> On modern cards, this parameter usually control handover/roaming threshold, the  lowest  signal  level  for  which  the  hardware remains  associated with the current Access Point. When the signal level goes below this threshold the card starts looking  for a  new/better  Access  Point.  Some  cards may use the number of missed beacons to trigger  this.  For  high  density  of  Access Points,  a higher threshold make sure the card is always associated with the best AP, for low density of APs, a lower threshold minimise the number of failed handoffs.Sounds like our case to me. When your card disconnects, can you run *iwconfig* and see if there are missed beacons?

Let's see if we can change it:```
sudo iwconfig wlan0 sens 3
```Now check:```
iwconfig
```You might need to command the dummy interface wifi0 instead. Did it stick? Does it help? If so,we can amend rc.local.

---

### Post by black veils on 2012-07-24
sorry to disappoint you (haha) but there were no missed beacons after a disconnect. and the command to change sensitivity did change it, but didnt change the odd connection behaviour.

you are obviously free to give-up :P  i was not expecting to even get this far.

i dont normally initiate anything outside of linux discussion, within my posts.

this laptop is for someone who is heavily in the Windows world, but they will be retiring soon, which means time to play, and exploration of their new interest in linux.

your age? (though it is just a number), what OS do you prefer? what work do you do that allows all this geeking? what is your favourite geeking thing? (eg. exploring a new linux OS, or editing something).
me: 27 (always been very mature for my age). Xubuntu and Bodhi Linux. i am house-wife-y (minus kids). dont think i have a favourite geeking thing, i geek a lot of different stuff, but general linux is every day. i apologise for the intrusion of crazy real life! i just thought it would be fun for a change.

---

### Post by chili555 on 2012-07-24
> you are obviously free to give-upNot quite yet; maybe tomorrow. Does it connect to WPA instead of WPA2? Does it connect in its intended location, presumably a wireless router and not an Android?> your age? (though it is just a number), what OS do you prefer? what work do you do that allows all this geeking? what is your favourite geeking thing? (eg. exploring a new linux OS, or editing something).I am a bit shy about personal details, but I'll just mention that you are closest to my grand-daughter's age. I am retired for many years. My main outside activities are non-computer. For example, I love travel and photography. Currently, I am trying to make decent photographs of the Milky Way.

---

### Post by black veils on 2012-08-01
> Does it connect to WPA instead of WPA2?how can i know what it is doing? i am using the Network Manager, which shows them as one option. the android hotspot is wpa2 though.


> Does it connect in its intended location, presumably a wireless router and not an Android

i dont know, but i doubt it will work, considering the wireless internet setup is wpa2 encryption also.

---

### Post by chili555 on 2012-08-01
> i doubt it will work,I agree. I don't know what else to suggest. Sadly, the Prism 2/2.5/3 drivers are not well maintained in the last several years. I have an old PCMCIA Prism 2.5 device that's supposed to work well with hostap but just won't.

All I can suggest is that you search the forum for supported USB wireless devices and give the Prism a nice funeral.

---

### Post by black veils on 2012-08-01
lol  when i get the linux-friendly usb wireless adapter, will i need to install drivers? its rather awkward finding modern adapters that are suitable for linux and wpa2. i am in the UK.

what about the matter of usb port 2.0 vs 1.1 ?

[http://i1163.photobucket.com/albums/q554/mumtaztakes/SPEC-SHEET.jpg?t=1339799158](http://i1163.photobucket.com/albums/q554/mumtaztakes/SPEC-SHEET.jpg?t=1339799158)

---

### Post by chili555 on 2012-08-01
> what about the matter of usb port 2.0 vs 1.1 ?I doubt it will matter.

The drivers for the device you linked are present in the 3.2.xx kernel now. A search of this forum will show many threads along the lines of 'recommend a USB device that works out of the box in Ubuntu.' That's shorthand for a USB device where the drivers are present now.

In order to get your new device to work, you'll probably need to blacklist *hostap_pci*. Post back if and when you're ready.

---

### Post by black veils on 2012-08-04
got the adapter, how do i blacklist the other driver?

---

### Post by chili555 on 2012-08-04
> **black veils said:**
> got the adapter, how do i blacklist the other driver?In a terminal, do:```
sudo su
echo "blacklist hostap_pci" >> /etc/modprobe.d/blacklist.conf
exit
```Insert the USB, reboot and let us hear your report.

---

### Post by black veils on 2012-08-04
seems good, thanks. the real test will be using for a period of time on their network (which will be faster than an android hotspot).


and i dont need to lock the kernel version, as Bodhi Linux deliberately dont auto-update kernels.

---

### Post by chili555 on 2012-08-04
Glad it's working! For the benefit of the searchers, would you mind sharing the brand and model of USB wireless you got? Please include:```
lsusb
```Thanks.

---

### Post by black veils on 2012-08-20
the brand seems to be nonexistent: Digitazz

but searching ebay or amazon for **Ralink usb wireless adapter** might help, or **linux usb wireless adapter**

```
lsusb
3072 Ralink Technology, Corp. 

```

model: GWF-1B

main chipset: Ralink RT 3072

---


---
title: "Broadcom firmware to Ndiswrapper Problems"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by xxrealmsxx on 2006-06-15
I installed ubuntu and my wireless did not work, i followed all instructions as root.

lspci shows that I have:

[I]0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[/I]

So I followed this guide to get it working:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper)

However my connection was very sporadic so I decided to try ndiswrapper, 

I followed some helpful instructions posted by another forum member:

[I]1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices arehandled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils

4) Conigure ndiswrapper
Open termianl and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. If it worked, you should be able to click the Network Manager icon in the top right. It will probably show a disconnected ennection becuase the computer is not plugged in.
Left click it and select eth1 from the drop down menu.
Click Configure
Click Wireless Connection, then Properties. Here just enter your network information. If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps![/I]

and now I have no wireless, network settings does not show a wireless device.

iwconfig gives the following after following the instructions:

[I]jamiewitter@jamiewitter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

jamiewitter@jamiewitter-laptop:~$ iwconfig eth1
eth1      No such device
[/I]

I was wondering if anyone could think of what I may be overlooking

Thanks in advance

---

### Post by Cinvent on 2006-06-15
See if  
[INDENT]ndiswrapper -l[/INDENT]
responds with something like:
[INDENT]Installed ndis drivers:
bcmwl5          driver present, hardware present
[/INDENT]
Instead of bcmwl5 you may have another driver.
Check if ndiswrapper is running:
[INDENT]lsmod | grep ndiswrapper[/INDENT]
Finally, I had to add the following lines to /etc/network/interfaces:
[INDENT]auto eth1
iface eth1 inet dhcp
[/INDENT]

---

### Post by noname101 on 2006-06-15
ndiswrapper -m for some reason doesn't make ndiswrapper module load. So edit /etc/modules and add at the bottom ndiswrapper.
```
sudo gedit /etc/modules
```
Also instead of rebooting you can do:
```
sudo modprobe ndiswrapper
```

---

### Post by xxrealmsxx on 2006-06-15
[QUOTE=Cinvent]See if  
[INDENT]ndiswrapper -l[/INDENT]
responds with something like:
[INDENT]Installed ndis drivers:
bcmwl5          driver present, hardware present
[/INDENT]
Instead of bcmwl5 you may have another driver.
Check if ndiswrapper is running:
[INDENT]lsmod | grep ndiswrapper[/INDENT]
Finally, I had to add the following lines to /etc/network/interfaces:
[INDENT]auto eth1
iface eth1 inet dhcp
[/INDENT][/QUOTE]

I believe I do need a different driver,

LSPCI gives the output:

[I]0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[/I]

Is that not the bcm43xx series?

The drivers I got are off of the hp site and pulled from my vmware installation in the folder the .exe off of the hp site made they are:
                                                              
bcmwl5a.inf

and 

bcmwl5.inf

I have the hp zv6000 and just grabbed the drivers the site told me to.

---

### Post by xxrealmsxx on 2006-06-15
[QUOTE=xxrealmsxx]I believe I do need a different driver,

LSPCI gives the output:

[I]0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[/I]

Is that not the bcm43xx series?

The drivers I got are off of the hp site and pulled from my vmware installation in the folder the .exe off of the hp site made they are:
                                                              
bcmwl5a.inf

and 

bcmwl5.inf

I have the hp zv6000 and just grabbed the drivers the site told me to.[/QUOTE]

After some googling i found this page:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

it lists the chipset for my wireless card and available drivers, all of the available drivers are the same ones I have been trying.

ndiswrapper gives: 

root@jamiewitter-laptop:~/Desktop/driver# ndiswrapper -i BCMWL5.INF
bcmwl5 is already installed. Use -e to remove it
root@jamiewitter-laptop:~/Desktop/driver# ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

:sad:

---

### Post by xxrealmsxx on 2006-06-15
[QUOTE=Cinvent]See if  
[INDENT]ndiswrapper -l[/INDENT]
responds with something like:
[INDENT]Installed ndis drivers:
bcmwl5          driver present, hardware present
[/INDENT]
Instead of bcmwl5 you may have another driver.
Check if ndiswrapper is running:
[INDENT]lsmod | grep ndiswrapper[/INDENT]
Finally, I had to add the following lines to /etc/network/interfaces:
[INDENT]auto eth1
iface eth1 inet dhcp
[/INDENT][/QUOTE]

Ok I found the correct driver.

It seems that because my laptop does not have bluetooth I need a different driver for my wireless nic.

I used the drivers from here: [http://www.meettheferrells.com/ron-and/ALT_BC_32.zip](http://www.meettheferrells.com/ron-and/ALT_BC_32.zip)

However I still dont see my wireless connection in the gui network management interface.

My comman line so far looks ok:

[I]root@jamiewitter-laptop:/home/jamiewitter# ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
root@jamiewitter-laptop:/home/jamiewitter# ndiswrapper -m
modprobe config already contains alias directive

root@jamiewitter-laptop:/home/jamiewitter# lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130692  4 ndiswrapper,ehci_hcd,ohci_hcd
[/I]

and my /etc/network/interfaces file reads:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

[/I]

---

### Post by noname101 on 2006-06-16
You might need to use a different driver. Since it doesn't say the hardware is present.

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=noname101]You might need to use a different driver. Since it doesn't say the hardware is present.[/QUOTE]

It says it is present now, but it still does not show up in network manager.

---

### Post by noname101 on 2006-06-16
edit try this:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=noname101]edit try this:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper[/QUOTE]


jamiewitter@jamiewitter-laptop:~$ sudo rmmod ndiswrapper
Password:
jamiewitter@jamiewitter-laptop:~$ sudo modprobe ndiswrapper
jamiewitter@jamiewitter-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
jamiewitter@jamiewitter-laptop:~$



Still not in network settings

---

### Post by noname101 on 2006-06-16
What does lsmod display?

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=noname101]What does lsmod display?[/QUOTE]

jamiewitter@jamiewitter-laptop:~$ lsmod
Module                  Size  Used by
vmnet                  37412  15
vmmon                 111884  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  0
drm                    73236  1 radeon
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
ndiswrapper           177364  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
pcmcia                 40508  0
joydev                 10048  0
tsdev                   8000  0
snd_atiixp_modem       16136  0
snd_atiixp             19724  1
snd_ac97_codec         92704  2 snd_atiixp_modem,snd_atiixp
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
psmouse                36100  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcspkr                  2180  0
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
serio_raw               7300  0
rtc                    13492  0
snd                    55268  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_atiixp_modem,snd_atiixp,snd_pcm
sdhci                  14848  0
mmc_core               30104  1 sdhci
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
ati_agp                 9100  0
agpgart                34888  2 drm,ati_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ohci_hcd               21892  0
usbcore               130692  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
generic                 5124  0
atiixp                  6800  1
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
jamiewitter@jamiewitter-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
jamiewitter@jamiewitter-laptop:~$ ndiswrapper -m
modprobe config already contains alias directive

---

### Post by noname101 on 2006-06-16
Maybe try rebooting. Also add ndiswrapper to /etc/modules.

---

### Post by Cinvent on 2006-06-17
[snip]

jamiewitter@jamiewitter-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present

Just to be sure: when you run ndiswrapper -l does it respond with 
"driver present, hardware present"? Without "hardware present" it won't work.

I had to try several different device drivers before I got ndiswrapper working. Do you have an AMD64? If so you should try bcmwl564.sys. This is the driver that works for me.

---

### Post by nzruss on 2006-06-17
here is another how-to. It expands on the instructions you followed. Just make sure you enter your appropriate driver name the ".sys" file.

While its for a wpc54g, the same steps apply. 

[http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)

---

### Post by xxrealmsxx on 2006-06-19
[QUOTE=nzruss]here is another how-to. It expands on the instructions you followed. Just make sure you enter your appropriate driver name the ".sys" file.

While its for a wpc54g, the same steps apply. 

[http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)[/QUOTE]

When I use the .sys file it says invalid driver

and the instructions say .inf

---

### Post by pksings on 2006-06-20
I had to edit my /etc/network/interfaces file and add entries for eth1 which is my bcm43xx interface. Now it comes up automatically.

iface eth1 inet dhcp
wireless-essid whatever

auto eth1

---

### Post by insyzygy on 2006-06-22
I finally got ndiswrapper working with my broadcom 4306 chip last night and since I just did it maybe I can help someone. Incidentally the computer is a dell inspiron 8500 with a truemobile card. I have tried ndiswrapper previously at least 4 times in different distros and it never worked. I recently installed dapper and after being unable to get the bcm43xx to work I thought I would give ndiswrapper another try and this time it worked.

If you look at

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
and 
particularly

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

they show how to find exactly the correct driver using lspci -vn. Ignore everything about patching the kernel just make sure you get exactly the  bcmwl**.inf that
there list tells you too for your card. Its important you use the driver from their site and not one from hp, dell, etc, or one on a driver disk.

I had previousy used ndiswrapper with various bcmwl5.inf files from dell and from cd's and other websites and all of these appeared to work, ndiswrapper ran and said it detected hardware, modprobing would work but I could never get any connectivity. The above wiki told me to use a particular bcmwl5a.inf and when I modprobed it suddenly worked. I think that the drivers installed by dell, hp, etc might be slightly different than the ones on that website, just a guess.

---

### Post by xxrealmsxx on 2006-06-22
[QUOTE=insyzygy]I finally got ndiswrapper working with my broadcom 4306 chip last night and since I just did it maybe I can help someone. Incidentally the computer is a dell inspiron 8500 with a truemobile card. I have tried ndiswrapper previously at least 4 times in different distros and it never worked. I recently installed dapper and after being unable to get the bcm43xx to work I thought I would give ndiswrapper another try and this time it worked.

If you look at

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
and 
particularly

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

they show how to find exactly the correct driver using lspci -vn. Ignore everything about patching the kernel just make sure you get exactly the  bcmwl**.inf that
there list tells you too for your card. Its important you use the driver from their site and not one from hp, dell, etc, or one on a driver disk.

I had previousy used ndiswrapper with various bcmwl5.inf files from dell and from cd's and other websites and all of these appeared to work, ndiswrapper ran and said it detected hardware, modprobing would work but I could never get any connectivity. The above wiki told me to use a particular bcmwl5a.inf and when I modprobed it suddenly worked. I think that the drivers installed by dell, hp, etc might be slightly different than the ones on that website, just a guess.[/QUOTE]


NdisWrapper has a problem

Sorry! This site is experiencing technical difficulties.

Try waiting a few minutes and reloading.

(Can't contact the database server: Can't connect to MySQL server on 'mysql4-n' (111) (mysql4-n))

The irony

---

### Post by suspend on 2006-07-03
I went throught your steps and my light comes on, my network manager says I have a wireless card.  I can activate it in the Network Admin, I can set DHCP and my ESSID (which is also broadcasted), the wireless network driver app under admin shows two devices (I only have one).  One is listed as eom3 and the other is BCMWL5.  It also says no hardware present.  

My etc/network/interface file has:

# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback


iface eth1 inet dhcp
wireless-essid NETGEAR

auto eth1

iface eth0 inet dhcp

auto eth0


My /etc/modprobe.d/ndiswrapper says:

alias eth1 ndiswrapper

iwconfig shows:

eth1      IEEE 802.11b/g  ESSID:"NETGEAR"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

...and I have tried everything I can think of to get this card to work.  I used the steps that the thread directed and I feel no further to success.  I really need this to work.  Any help would be greatly appreciated.  As far as drivers go, tonight I've attempted to employ:

wl_apsta.o, bcmwl5.sys and bcmwl5.inf (I think I split .o into both my firmware and my kernal directories, does that make a difference?) 

I would be greatful for any suggtions.

---


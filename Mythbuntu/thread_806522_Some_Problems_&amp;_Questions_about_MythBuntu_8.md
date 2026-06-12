---
title: "Some Problems &amp; Questions about MythBuntu 8"
date: 2008-05-25
forum: Mythbuntu
---

### Post by ds2k5 on 2008-05-25
Hello,
I have some problems & questions about MYthBuntu 8.

My Hardware:

CPU: AMD Sempron(tm) Processor 3000+
RAM: 1 GB (avaiable: 964204k) Used SWAP: 210232k
Optical: DVD-RW from LG
DVB-S: stv0299 compatible

Remote Control:
X11
P/N: 20017670
USB RF Remote Reciver:
P/N: 20017629

Picture see here: [http://www.vdr-wiki.de/wiki/index.php/Fernbedienung_-_USB_X10](http://www.vdr-wiki.de/wiki/index.php/Fernbedienung_-_USB_X10)


My Questions:

1. How to install MythBuntu 8 with German Keyboarddriver, that works under X11-Server ? Console works with germany Keyboarddriver.

2. How to Configure the Remote Control, that it works with
   MythBuntu FULL and not only a few Funktions

3. Problem with the WebGUI: mythweb

   Error: Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 24 bytes) in /usr/share/mythtv/mythweb/modules/tv/includes/objects/Program.php on line 291

   If i try to see TV or Music Listing
   Changeing the /etc/php.ini do not help

4. The VGA Card use RAM from the System (Shared MEM)
   Is more that 1 GB RAM needed, because i see 210232k is Used in SWAP ?!


Loaded Kernel Modules:

user@mythbuntu:~$ lsmod 
Module                  Size  Used by
isofs                  39464  0 
udf                    91048  0 
af_packet              27272  2 
nfsd                  282024  13 
auth_rpcgss            53280  1 nfsd
exportfs                7040  1 nfsd
ipv6                  311720  22 
powernow_k8            16608  0 
cpufreq_ondemand       11152  1 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_stats           8416  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
battery                16776  0 
nfs                   291576  0 
lockd                  76080  3 nfsd,nfs
nfs_acl                 5248  2 nfsd,nfs
sunrpc                213896  11 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
dvbloopback            26342  1 
lp                     14916  0 
snd_hda_intel         440408  1 
stv0299                13320  1 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_mpu401             11304  0 
snd_mpu401_uart        11264  1 snd_mpu401
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
budget_ci              22788  21 
budget_core            15364  1 budget_ci
dvb_core               93356  4 dvbloopback,stv0299,budget_ci,budget_core
saa7146                22152  2 budget_ci,budget_core
ttpci_eeprom            3968  1 budget_core
psmouse                46236  0 
ir_common              44548  1 budget_ci
snd_seq_oss            38912  0 
serio_raw               9092  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
irtty_sir              10880  0 
nvidia               8858052  36 
snd                    70856  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
analog                 13408  0 
i2c_nforce2             8704  0 
evdev                  14976  4 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
sir_dev                19592  1 irtty_sir
parport_pc             41128  1 
parport                44300  2 lp,parport_pc
i2c_core               28544  6 stv0299,budget_ci,budget_core,ttpci_eeprom,nvidia,i2c_nforce2
k8temp                  7680  0 
soundcore              10400  1 snd
irda                  222956  2 irtty_sir,sir_dev
gameport               17936  1 analog
pcspkr                  4992  0 
crc_ccitt               3584  1 irda
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
pata_acpi               9856  0 
ata_generic             9988  0 
floppy                 69096  0 
pata_amd               16772  2 
forcedeth              55564  0 
ehci_hcd               41996  0 
ohci_hcd               27524  0 
libata                176304  3 pata_acpi,ata_generic,pata_amd
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
usbcore               169904  4 ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  1 




Thanks

bye

ds2k5

---

### Post by Titus A Duxass on 2008-05-25
I can only give you a bit of advice with this part:

> 1. How to install MythBuntu 8 with German Keyboarddriver, that works under X11-Server ? Console works with germany Keyboarddriver.

You can select a German keyboard at the initial screen, but it will probably be ignored when you actually boot the system.

After you boot the system, exit mythtv and select the correct keyboard layout using the System=>Setting procedure.

A word of warning: the keyboard select will most likely reset itself to the US layout everytime you reboot. Mine does this without fail.

Good luck with your remote, I have never managed to get mine working 100%

I do not understand your question about TV or music listing, can you provide more information.

---

### Post by sandman652001 on 2008-05-25
for your keyboard all you have to do is exit myth front end browse to /etc/X11
right click and chose open terminal here
in the terminal window type:
sudo cp xorg.conf xorg.good
then your password
this will back up your xorg.conf file so that you can restore it if you make any mistakes.
 the type:
sudo nano xorg.conf
then your password
find xkblayout "us" and change the "us" part to your locale in my case "it" for Italian in your case I think it should be "de" for German
now save the file: ctrl+x then y then enter
reboot your system now your keyboard should work correctly
if for any reason your pc does not start properly at the command prompt simply type
cd /etc/X11
then sudo mv xorg.good xorg.conf 
this will restore your original configuration

hope it helps

---

### Post by ian dobson on 2008-05-25
Hi,

For your mythweb problem, you need to give php abit more memory.

Edit your  /etc/php5/apache2/php.ini file and change the line 
memory_limit = 64M      ; Maximum amount of memory a script may consume (64MB)

I actually increased the memory_limit to 128M and havent seen this error since then.

Gruss aus Basel
Ian Dobson

---


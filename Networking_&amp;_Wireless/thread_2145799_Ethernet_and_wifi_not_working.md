---
title: "Ethernet and wifi not working"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by LocoMotor101 on 2013-05-16
Hello:   I just installed 12.04 in a Toshiba Satellite 64 system this morning.  However, I do not have networking capabilities in that computer.  I tried to locate a similar problem in this forum but I could not find any clues to my problem.  Most people have problems with wireless so they can perform online apt-get, etc.  But I cannot have access to the net.  So, I am asking for help.  Thanks.

---

### Post by Hadaka on 2013-05-16
Hi, do you have a usb stick you can copy files to 
and put them on your ubuntu machine??

---

### Post by LocoMotor101 on 2013-05-16
Hi Hadaka:  Yes, I do.  If you have any files I should install, please let me have them.  Or, let me know where to download from.  Thank you!

---

### Post by Hadaka on 2013-05-16
ok,Let's start by seeing what drivers you need.
please copy and past to your usb,then on to the
Ubuntu machine.

```
lspci -nn | egrep '0200|0280' 
```
post the results.
thanks

---

### Post by LocoMotor101 on 2013-05-16
Hadaka:  this is the output

01:00.0 Ethernet controller [0200]: Atheros Communications INc. AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

---

### Post by Hadaka on 2013-05-16
ok,lets take a look at some info, I think we can get your
wireless working and go from there.
please do...
```
modinfo rtl8192ce | grep 8176 
```
post the results.

not having any connection makes this a little more difficult
but we'll do our best to get you going.
thanks.

---

### Post by LocoMotor101 on 2013-05-16
The output was:

ERROR: modinfo: could not find module rtl8192

---

### Post by LocoMotor101 on 2013-05-16
The output was:

alias:       pci:v000010ECd00008176sv*sd*bc*sc*i*

---

### Post by Hadaka on 2013-05-16
ok, I suspect since youhavent done any updates/upgrades 
yet its not there..no problem. I looked on my 12.04 and its there
so your device is supported by that driver. first lets look at just
a couple more things, and then hopefully start putting this back
together...Please do..
```
iwconfig
 rfkill list all
dmesg | grep -e wlan -e rtl
```
post the results....hang in there we are getting there.

---

### Post by LocoMotor101 on 2013-05-16
This is the new output:

$ iwconfig
   lo      no wireless extensions
$ rfkill list all
(no output at all)
$ dmesg | grep -e wlan -e rtl
   [  11.545133] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
   [  11.545135] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
   [  11.579846] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available

---

### Post by Hadaka on 2013-05-16
ok,thats what i wanted to see, ready?
Please read carefully. go here...post #20

*Important, before you issue any commands
put the zip file on your usb..drop it on the Desktop
of your ubuntu machine..then RIGHT CLICK and choose EXTRACT HERE
then issue the commands.
[http://ubuntuforums.org/showthread.php?t=2123074&page=2](http://ubuntuforums.org/showthread.php?t=2123074&page=2)

i would suggest copy and paste the commands to avoid any typos.
good luck.
post back how it went.

---

### Post by LocoMotor101 on 2013-05-16
Well, unfortunately it did not work.  It appears that the new "drivers" were installed, yet nothing happens.  I rebooted and, as before, it says that it will give another 60 seconds for the network configuration.  Once is running, the little "V" for wifi signal on the upper right corner is not present.  So, I am still puzzled why Ubuntu works fine in this very old computer but not in a fairly recent one.  I would greatly appreciate it if you continue giving me suggestions.

---

### Post by Hadaka on 2013-05-16
ok, did you do these 2 commands?
```

sudo apt-get install linux-firmware
 sudo modprobe -r rtl8192ce && sudo modprobe rtl8192ce 
```

---

### Post by LocoMotor101 on 2013-05-16
Actually, I never read that I was supposed to do the apt-get install command.  I did everything else.  So, I went ahead and did the apt-get install and the modprobe command.  I re-booted the system but no networking.

---

### Post by Hadaka on 2013-05-16
ok, try again but without the apt-get
just the modprobe commands...and dont boot.

you arent going to make this easy are you?
Really wish at least the wired was working...
we shall keep trying..:)

---

### Post by LocoMotor101 on 2013-05-16
Hadaka:  I will continue trying until it works, because I need this computer to work with the same operating system I have in my desktop at the office (ubuntu 12.04).  At this moment I am at home, so I have to switch between windows and ubuntu to try your recommendations.  Thus, I will try your last recomm and return here to let you know.  Thanks a million.

---

### Post by Hadaka on 2013-05-16
ok,Im concerned about getting this working with
no internet access,even getting the driver from the realtek
site because there are commands that require a connection.
Im going to guess you burned a 12.04 cd or usb to load in the
beginning. Is it possible to attach via wire and reload? The Ethernet
end should just work. The wireless seems to be an ongoing issue
which requires a little massaging to get going. I will continue to help
the best i can without net access...Hopefully we can get the built in
driver to fly. Thanks for hanging in there.

---

### Post by Hadaka on 2013-05-17
ok, I am able to load this driver in 12.04 without error
so let's go back over some things to verify all is well.
please do...
```

ls /lib/firmware/rtlwifi | grep B.bin
```
post the results..
thanks.

---

### Post by LocoMotor101 on 2013-05-17
On your first issue about ethernet:  I have plugged the ethernet but nothing happens.  Actually, I can see in the router that it does not even the light comes up, which makes me believe it is disconnected.  Yet, it works in windows7.  Now on your second poing I did the commands and this is the result:
rtl8192cfwU_B.bin
rtl8723fw_B.bin

...I do not know if this will help you, but let me also add that with the command  
"lshw -C network"     
I get the following:
  	 	 	 	   oquiros@TOSHI:/etc/network$ sudo lshw -class network  
   *-network UNCLAIMED      
        description: Ethernet controller 
        product: AR8162 Fast Ethernet  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: 10  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm pciexpress msi msix bus_master cap_list  
        configuration: latency=0  
        resources: memory:b8500000-b853ffff ioport:3000(size=128)  
   *-network DISABLED  
        description: Wireless interface  
        product: RTL8188CE 802.11b/g/n WiFi Adapter  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan1  
        version: 01  
        serial: 24:ec:99:3a:af:dc  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:17 ioport:2000(size=256) memory:b8400000-b8403fff

---

### Post by Hadaka on 2013-05-17
hi, it looks like you have the firmware loaded
so hopefully we are getting closer..
please do..
```

sudo modprobe -r rtl8192ce && sudo modprobe rtl8192ce
 rfkill list all
lsmod
```
you network is showing disabeled...check network mrg. make sure the
enable network and enable wireless is checked you also..if you havent already
might try a hard boot on both the router and the computer.

---

### Post by LocoMotor101 on 2013-05-17
After the modprobe command:
FATAL:  Module 1844 not found

after the rfkill command:  
(no output)

  	 	 	 	   after the lsmod command:
Module                  	Size  Used by  

 snd_hda_codec_hdmi     32476  1  
 snd_hda_codec_realtek    79756  1  
 joydev                 	17694  0  
 parport_pc             	32867  0  
 ppdev                  	17114  0  
 rfcomm                 	47562  0  
 bnep                   	18240  2  
 bluetooth             	211812  10 rfcomm,bnep  
 arc4                   	12530  0  
 coretemp               	13642  0  
 kvm_intel             	137888  0  
 kvm                   	422160  1 kvm_intel  
 ghash_clmulni_intel    13221  0  
 cryptd                 	20531  1 ghash_clmulni_intel  
 snd_hda_intel          	34117  3  
 snd_hda_codec         	135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              	17765  1 snd_hda_codec  
 snd_pcm                	97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 snd_seq_midi           	13325  0  
 snd_rawmidi            	30750  1 snd_seq_midi  
 microcode              	23030  0  
 snd_seq_midi_event     14900  1 snd_seq_midi  
 snd_seq                	61931  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              	29990  2 snd_pcm,snd_seq  
 snd_seq_device         	14498  3 snd_seq_midi,snd_rawmidi,snd_seq  
 rts5139               	350620  0  
 psmouse               	102075  0  
 snd                    	83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 serio_raw              	13216  0  
 uvcvideo               	78117  0  
 videobuf2_core         	33025  1 uvcvideo  
 videodev              	125126  2 uvcvideo,videobuf2_core  
 videobuf2_vmalloc      12861  1 uvcvideo  
 videobuf2_memops       13405  1 videobuf2_vmalloc  
 soundcore              	15092  1 snd  
 snd_page_alloc         	18573  2 snd_hda_intel,snd_pcm  
 lpc_ich                	17145  0  
 mei                    	41410  0  
 mac_hid                	13254  0  
 i915                  	530857  3  
 drm_kms_helper         49259  1 i915  
 drm                   	290344  4 i915,drm_kms_helper  
 i2c_algo_bit           	13565  1 i915  
 video                  	19598  1 i915  
 lp                     	17800  0  
 parport                	46563  3 parport_pc,ppdev,lp  
 hid_generic            	12541  0  
 usbhid                 	47259  0  
 hid                   	100815  2 hid_generic,usbhid

---

### Post by LocoMotor101 on 2013-05-17
When you indicated network mrg. I assume you mean the graphic manager at the System Settings.  I clicked Network and got the message "The system network service are not compatible with this system".  Which is what I have been getting since I installed 12.04.02.   It only has the Network proxy window. // Now, I do not know what do you mean by hard boot.  Please explain.  Thanks.

---

### Post by Hadaka on 2013-05-17
ok, click the triangle next to the the envelope...upper right corner
make sure enable neworking and enable wireless are checked
check your configuration for settings to the router...it should be
set for wpa2-aes.....no tkip...check your wireless hard switch if
you have one...check bios if you have messed with it...something
has the network DISABLED..and untill that is found..we are stuck
so check everything and anything you can think of to enable it.
does the rfkill list all show any blocks?

please also do..

cat /var/lib/NetworkManager/NetworkManager.state

post that back please
thanks.

---

### Post by LocoMotor101 on 2013-05-17
I found here in this forum that with a simple NetworkManager command I was able to get it running.  So, now I do have the Network graphics with the "Wired" window, and the "V" in the upper right corner of the screen.  The "Wired" says Cable unplugged, and the IPv4 and 6 localhost addresses, but no way for me to manually change it.  NO wifi window, though.

---

### Post by LocoMotor101 on 2013-05-17
The triangle by the envelope has a check mark by the Enable Networking, however it is not "active." I cannot change it.  Only the VPN Connections and the Edit Connections are active.  I tried to modify the Wired and the Wireless windows but are NOT active.   I will check the BIOS for other clues, yet, I do not think it is here because both ethernet and wifi work with windows7.

---

### Post by Hadaka on 2013-05-17
local hosts addresses?..how are you getting anything with it saying 
the cable is unpluged? are you running this as a stand alone machine
or are you doing some kinda of adhock network?  seriously confused here..

---

### Post by LocoMotor101 on 2013-05-17
Hadaka.  No connections at all.  What I ment by local host are the 127.0.0.0 addresses.  //  I checked the BIOS but nothing unusual there. //  Other information that might help you:  now when I do the command "lshw -class network"  both the ethernet and the wifi adapter indicate "UNCLAIMED".  With ifconfig now I only get the "lo".  The "wlan1" is gone.

---

### Post by Hadaka on 2013-05-17
lets look at a couple things.
please do..
```
cat /etc/modules
cat /etc/network/interfaces
```
your IPv4 and IPv6 should look like the attached
for a stand alone machine..

---

### Post by LocoMotor101 on 2013-05-17
Is this information of any help?

  	 	 	 	   oquiros@TOSHI:/etc/network$ sudo cat /var/log/syslog | grep etwork | tail -n20  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: autoconnect  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPluginIfupdown: management mode: unmanaged 
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: end _init.  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    Ifupdown: get unmanaged devices count: 0  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: (34616112) ... get_connections.  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    SCPlugin-Ifupdown: (34616112) ... get_connections (managed=false): return empty list.  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    keyfile: parsing WiredCasa ...  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    keyfile:     read connection 'WiredCasa'  
 May 17 04:59:41 TOSHI NetworkManager[2381]:    Ifupdown: get unmanaged devices count: 0  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> trying to start the modem manager...  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> monitoring kernel firmware directory '/lib/firmware'.  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> WiFi enabled by radio killswitch; enabled by state file  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> WWAN enabled by radio killswitch; enabled by state file  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> WiMAX enabled by radio killswitch; enabled by state file  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> Networking is enabled by state file  
 May 17 04:59:41 TOSHI NetworkManager[2381]: <info> modem-manager is now available

---

### Post by Hadaka on 2013-05-17
let's try that again..

IPV4 ...IPv6

[ATTACH=CONFIG]242710[/ATTACH][ATTACH=CONFIG]242711[/ATTACH]

---

### Post by LocoMotor101 on 2013-05-17
The graphics you posted do not represent what I see in my Network window.  I only have one image that says Wired, calbe unplugged.  But it is not editable, nor I see any of the stuff you can see in your image.  So, there is nothing I can do in the Network window or at the triangle by the letter in the upper bar.

---

### Post by Hadaka on 2013-05-17
ok,im going to assume the "no cable" is beause....there isnt one.
let's look at a couple things..then try another possibility..
please post the output of..

```
uname -r
ls /lib/firmware/rtlwifi
```
I know it's a pain running back and forth
with the usb stick...but its all we have.
thanks.

---

### Post by LocoMotor101 on 2013-05-17
Hadaka, first of all let me tell you that I am extremely thankful for your time and effort to help me.  I really appreciate it.  Now, I do have ethernet cable that I can switch from this computer to the "troubled one".  Yet, it appears the ethernet device is off, because the router does not show any light one (as it does when I plug it into this computer).  Here are the respond to both commands you requested:
  	 	 	 	   
oquiros@TOSHI:/etc/network$ uname -r  

 3.5.0-23-generic  


 oquiros@TOSHI:/etc/network$ ls /lib/firmware/rtlwifi  

 Realtek-Firmware-License.txt  rtl8192cfwU_B.bin  rtl8192cufw.bin     rtl8192defw.bin  rtl8192sefw.old.bin  rtl8723fw_B.bin  
 rtl8192cfw.bin                rtl8192cfwU.bin    rtl8192defw_12.bin  rtl8192sefw.bin  rtl8712u.bin         rtl8723fw.bin

---

### Post by Hadaka on 2013-05-17
ok, for whatever reason your wifi is disabeled and the module
wont load.soooo It's time for a ..hail mary.. My good friend
varunendra has pointed me to a thread that can load your
WIRED connection..which is the new ALX driver..what your
machine needs. to begin...you need to know if you are 32 or 64 bit
and you also need to write down on paper your kernel version...
which you got with the ...uname-r.... i would suggest you read post #7
of this link...twice..three time..so you are comfortable with it..
[http://ubuntuforums.org/showthread.php?t=2050126&p=12206393#post12206393](http://ubuntuforums.org/showthread.php?t=2050126&p=12206393#post12206393)
if you have any issues or need help with it...i will assist the best i can.
good luck...and keep me posted.

kernel version
```
uname -r
uname -a
```
32 or 64 bit
```
arch
```

---

### Post by Hadaka on 2013-05-17
Hi, i just did a search on your machine, have you tried
holding donw the Fn key while pressing the F8 key?
this is the on/off key for your network.Fn/F8...
give that a try..press only once.  then try to load the module

modprobe rtl8192ce

---

### Post by LocoMotor101 on 2013-05-17
Well, I was able to get the wifi up and running just with the modprobe  command.  I did not do anything varunendra recommended, yet.  But for  some strange reason I was not able to access the router.  I tried  several times the password until it refuse to try anymore.  I rebooted  the computer but the wireless was gone again.  I just commanded  NetworkManager up, and got the wifi capability back.  But cannot connect  to the modem for some reason.  // By the way it is a 64 bit computer  and the FN/F8 did not work.  The ethernet still dead. Definitely, we are  moving ahead but I still need additional help.  Do you want me to try  anything else or should I just try what verunendra recommended?

---

### Post by Hadaka on 2013-05-17
Progress !..when the wifi was up were you able to
view the settings by clicking the wifi symbol? next to
the envelope..if so..see if you can get in and set your
ipv4 and ipv6 like the screenshots i sent..also..double
check the security settings and avoid tkip..if possible
set it to wpa2-aes. also..reset your bios to default..
F9 for toshiba. lets try that then see about getting the wired working.
thanks.
ALSO..please do..
modprobe -rfv rtl8192ce
modprobe rtl8192ce swenc=1

---

### Post by LocoMotor101 on 2013-05-17
Yes, when the wifi was up I was able to access the wifi settings via de triangle and via de Network on System Settings.  Let me add that at the very beginning the "wired network" was visible, so I plugged in the ethernet cable but it was still dead. // I have no idea how to take screenshots.  I was checking on the net how to, but it does not work as it says.  So, give me some more time.  //

  	 	 	 	   oquiros@TOSHI:~$ sudo modprobe -rfv rtl8192ce  
 rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko 
 rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko 
 rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
 rmmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko  
 rmmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko  
 oquiros@TOSHI:~$ sudo modprobe rtl8192ce swenc=1  
 oquiros@TOSHI:~$  

When I did the last command, the wifi was disabled yet the triangle still there, but only the VPN connections and Edit connections are active.

---

### Post by Hadaka on 2013-05-17
Hi, those 2 commands i sent
```
sudo -rfv rtl8192ce
sudo modprobe rtl8192cd swenc=1
```
first one takes the module out
second puts it back with a code to disable encryption
reason being..you have a b/g/n card..and the N speed setting
tends to cause problems with this driver.
so please do those again...and then the network up command
without booting after.
the screen shot i referd to are the ones I sent...for 1pv4-ipv6 settings
once you are up and running I'll guide you how to do screen shots.
thanks.

---

### Post by LocoMotor101 on 2013-05-17
Hadaka!!  The wifi finally connected to the router with only the last two commands you just gave me.  Excellent.  Now, I assume I have to do something to make this permanent.

---

### Post by Hadaka on 2013-05-17
Yes !  ok do this..
```
gksudo /etc/modprobe.d/rtl8192ce.conf 
```
insert this ONE line..
```
options rtl8192ce swenc=1
```
close and save...*note NO typos allowed :)

---

### Post by LocoMotor101 on 2013-05-17
I am sorry but the gksudo ... command does not do anything.  I assume is some sort of editor and once it opens I add that "options" line.  So, can I create a file with pico?  Or, what other command should I perform in order to create this new file?

---

### Post by Hadaka on 2013-05-17
sorry..bad command....try
gksudo gedit 



gksudo gedit /etc/modprobe.d/rtl8192ce.conf

---

### Post by LocoMotor101 on 2013-05-17
I did it.  I checked and it has the same permits as the other files in the directory.  Should I do something else?

---

### Post by Hadaka on 2013-05-17
yes...boot and make sure it connects..when it does..
play around on the net a little bit to make sure its
stable...then we will load your WIRED !

---

### Post by LocoMotor101 on 2013-05-17
When I rebooted the network was not started. The "Waiting 60 seconds...." banner came up.  I had to manually command "NetworkManager up" to get it running.  Then it connected automatically to our router.  So, I guess I have to include the NetworkManager command somewhere.

---

### Post by Hadaka on 2013-05-17
hmm...I'm not sure why that is doing that, at this point
as long as you can get it going is what counts,as we will
soon download the wired driver...alx...please dont 
attempt the load till i get back..I shall return in about
an hour..mean time..play on the net so we know it will
hold long enough to get the wired driver...then we will
deal with the why you have to start network mgr.
thanks. back in a bit.

---

### Post by LocoMotor101 on 2013-05-17
Good enough for me too.  I will figure out later how to make the system start NetworkManager at boot time.

---

### Post by Hadaka on 2013-05-17
ok, if you are ready...
connected to the internet...
Please COPY and paste one comand at a time.
```
sudo apt-get install linux-headers-generic build-essential
 wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```
if you have any warnings..thats normal and you can ignore them
if you get errors...or see STOP then...stop and post the error.
good luck !

---

### Post by LocoMotor101 on 2013-05-17
The first two command lines went well.  Then this:

oquiros@TOSHI:/etc/network$ tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by Hadaka on 2013-05-17
No they arent bad...it was me i screwed up on the copy and past..im really sorry


tar -xf compat-wireless-3.5.1-1-snpc.tar.bz

start from this line and continue

---

### Post by LocoMotor101 on 2013-05-17
It did not work.

oquiros@TOSHI:~$ sudo tar -xf compat-wireless-3.5.1-1-snpc.tar.bz
tar: compat-wireless-3.5.1-1-snpc.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by Hadaka on 2013-05-17
I am in error of thinking i made an error ...this is correct

```
sudo apt-get install linux-headers-generic build-essential 
```

---

### Post by Hadaka on 2013-05-17
since you would have to do this again on the next kernel update
and you havent updated anything since you installed and are currently
on an older kernel...lets get the updates first... please do...
while connected to the internet
```
sudo apt-get update
sudo apt-get upgrade
```
then COPY and paste one line at a time..
```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx 
```

Note..i was able to load this...no error

---

### Post by LocoMotor101 on 2013-05-18
It took forever to get update, upgrade, apt-get, and the wget downloaded.  Actually, all night long. And I am not sure they all downloaded correctly because I had to re-start several times as they stopped completely.  I performed all the steps you indicated and re-booted.  I started NetworkManager manually and now I can see that eth0 is up (with ifconfig -a) and when I plugged the ethernet cable the light at the router comes up.  I was able to connect via wifi, but not wired.  I tried to play with the Wired connection at the System Configurations panel (it says Unmanaged), but got the wireless disconnected, and cannot get it back again.  The wifi now says Unavailable, but I just got it back just toggling with the ON OFF switch.  So I can see we have made more progress, and close to get the wired ethernet working.

---

### Post by Hadaka on 2013-05-18
Great !..ok, because of the updates and upgrades
that have happened since you first loaded 12.04
it needs to be brought up to date. It should run alot
faster now that you have most of them.so PLEASE
run again..
```
sudo apt-get update
sudo apt-get grade
```
be patient, if it locks up or drops..connect again
and run again, untill ALL updates and upgrades are loaded.
other wise, the load you are doing for wired will be voided
due to kernel updates.
more than likely you will have to re-run...
```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx 
```
be patient..

---

### Post by LocoMotor101 on 2013-05-18
Well, it is not really faster.  It will take another 32 hours to finish.  The problem is that every file starts downloading fast then it goes down to 4kb.  So, in order to speed it up, I stop it every few seconds and resume it.  This will only take 3 hours it indicates.  So, it is Saturday, so I can deal with it.  After all the last previous days I did not do any work, well just a bit.

---

### Post by Hadaka on 2013-05-18
Glad to hear you are hanging in there..It really is
impostant to do the updates, doing it via wireless
always takes longer..but..has to be done. Here is a little information so
you get a better understanding of what is what..Your PC  the toshiba..is newer
thus its wired card is the type that requires the ALX driver. That driver is not
built into the kernel in 12.04..it is in 13.xx. but..the 13.xx is not LTS nor does it
match the os of your work machine as you desire. given that..this means since
you will be useing 12.04 and getting pop-ups from network mgr. to load security update
now and then...with them...comes kernel updates. This means since the ALX driver is not
in 12.04,(why you are building it) it needs to be reloaded with each kernel update. The current
12.04 kernel is 3.2.0-43-generic...you had 3.2.0-23-generic .soooo..I would advise you build and keep a file
on how to reload this driver each time your kernel is updated.  here ya go..
open the editor..create this file..
```
gedit kernel_update
```
then copy and past the following.
```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx

```
close and save gedit.
it will go quickly..since you should at this point be up to date.
you will only have to do this on kernel updates...not regular updates.

*my machine is up to date..when i loaded this ...it took less then 5
minutes....having a quantum fios connection helps. :)

---

### Post by LocoMotor101 on 2013-05-18
I am still in the process of upgrade.  My hand is tired of stopping and resuming.  At any rate, from your previous comments a gather that once the 13.x is LTS, I should not have to worry about all this "hand-updating" you indicate.  Am I correct?  By the way, I changed the NetworkManager.conf to "managed=true" and then I was able to connect throught ethernet.  It is working now.  I do not know if I can switch to wireless, though.  Not going to try it yet.

---

### Post by Hadaka on 2013-05-18
I "think" there is a 13.x LTS now..if you call 18months LTS .
Am i correct in understanding you are doing the updates..via wired?
if so..thats fine..you WILL have to reload the driver when done updating
after you boot. anyway...wired or wireless loading the updates..Try not
to interupt it if you can..some of the things just take time...and the more you
check speeds or hover over it...the longer it will take.
hang in there.

---

### Post by LocoMotor101 on 2013-05-18
Hadaka:  If I do not do the stop and resume trick, it says it will take 1 day and 15 hours to finish the upgrade.  When I do the trick it says 1 or 2 hours.  I have done this stop and resume trick in my desktop computer at home.  It worked fine.  But it was not ever this big of a upgrade.  I really do not why is downloading all libreOffice.  I could have done that later, but I have no choice on selecting or deselenting what is being upgraded.  / / So, yes, I am wired now.

---

### Post by varunendra on 2013-05-18
Wow! And I thought this thread was going to be [Solved] within 3rd page :P

A few observations that look abnormal to me (I hope they are not going to disrupt the logical progress you guys have achieved after so much hard work) :

@ LocoMotor101,
You mentioned quite a few times that you have to manually bring up the interface using NetworkManager up command (to be honest, I didn't even know this command exists, and still not sure what all it does). That shouldn't have been required.
In the Network Manager wireless settings, make sure "**Connect automatically**" is checked, that is, has a tick mark in it. Also, make sure "**Available to all users**" is also checked.

If they are already enabled and you still have to manually bring up the connection, then it may indicate some serious mis-configuration in your system. Although it shouldn't interfere with the fixes you guys have been doing.
Also, this -
> **LocoMotor101 said:**
> I tried to play with the Wired connection at the System Configurations panel (it says Unmanaged)
combined with this -
> **LocoMotor101 said:**
> By the way, I changed the NetworkManager.conf to "managed=true" and then I was able to connect throught ethernet.
..makes me suspicious of your /etc/network/interfaces file. Did you, by any chance, happen to edit that file? This, and some other things can be much better cleared up if you can run and post the result of "Wireless Script" that you can find in the link in my signature below. Follow that link, follow any of the two methods suggested in the linked post and post back the contents of the "netinfo.txt" file it creates.


@ Hadaka,
> **Hadaka said:**
> I "think" **there is a 13.x LTS now..**if you call 18months LTS ..
Now? Are you talking about any variant of default Ubuntu? Because the default one will only be supported for "9 months", as against the earlier non-LTS versions : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Anyway, LocoMotor101, please just check the "Connect automatically" setting in your wireless connection settings, and post back the result of the "Wireless Script" following the link in my signature. It will give us an overall picture of your current settings. We may ask more if required.

**PS:**
> **LocoMotor101 said:**
> I have no idea how to take screenshots.
Press "Print Screen" key on your keyboard to do that. Not that it seems to be required now :)

---

### Post by LocoMotor101 on 2013-05-18
Well Hadaka.  I have finished doing the whole thing you indicated.  It took me less than 1 day and 15 hours.  Just 9 hours.  As of now, I have not re-booted the computer, but I will as soon as I post this message.  I expect to be at least with a functional wired connection.  Let you know , hopefuly soon.

---

### Post by LocoMotor101 on 2013-05-18
Varunendra:  I have to get the NetworkManager up because there is nothing for me to manipulate in the Network window in the System Configurations.  If NetworkManager is not up I cannot do anything you mentioned.  I simple do the commmand NetworkManager up, and then it all appears.  I just rebooted the computer and it hangs for a while until it says it is starting without network.  Then I open a terminal and give the command to start the NetworkManager.  Simple, but it should start at boot, and I still do not know how to.  Please find below the script:

#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

---

### Post by Hadaka on 2013-05-18
glad you got the updates loaded !
From your now working wired connection..
please post the output of ..
```
arch
uname -r
cat /etc/modules
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
lsmod
```
thanks.

---

### Post by LocoMotor101 on 2013-05-18
As per your request:

oquiros@TOSHI:~$ arch
x86_64
oquiros@TOSHI:~$ uname -r
3.5.0-23-generic
oquiros@TOSHI:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
oquiros@TOSHI:~$ cat /etc/network/interfaces
auto lo
auto eth0
auto wlan1
iface eth0 inet dhcp loopback

oquiros@TOSHI:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true
#managed=false
oquiros@TOSHI:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
bnep                   18240  2 
arc4                   12530  2 
rtl8192ce              58779  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 17694  0 
rtl8192c_common        49512  1 rtl8192ce
i915                  530857  3 
rtlwifi                76086  1 rtl8192ce
rts5139               350620  0 
uvcvideo               78117  0 
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_core         33025  1 uvcvideo
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
coretemp               13642  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
rfcomm                 47562  0 
drm_kms_helper         49259  1 i915
psmouse               102075  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
alx                    81351  0 
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   290344  4 i915,drm_kms_helper
ghash_clmulni_intel    13221  0 
compat                 13228  1 alx
mei                    41410  0 
lpc_ich                17145  0 
cryptd                 20531  1 ghash_clmulni_intel
i2c_algo_bit           13565  1 i915
mac_hid                13254  0 
serio_raw              13216  0 
soundcore              15092  1 snd
cfg80211              208382  2 rtlwifi,mac80211
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
microcode              23030  0 
bluetooth             211812  10 bnep,rfcomm
video                  19598  1 i915
parport_pc             32867  0 
ppdev                  17114  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid

---

### Post by Hadaka on 2013-05-18
Glad to see you are able to get commands now.
I see a couple things that need a little tweaking in the etc/network areas
that most likely varunendra will be helping you with. the script he had you
run also produces a diagonstic file, you posted the script..not the file. Please click
that scrip link on his page and re-read the "how to" then post back the file.
Im glad we got the wired and wireless working, all thanks to Dr chili555 providing
the templates to do so. This needs a little more tweaking to be 100%, so try not
to jump on other threads or do fixes you find in the forums without letting the person
know what has been done. I am going to be tied up this evening, so i will check in
on the progress.

---

### Post by LocoMotor101 on 2013-05-18
Sorry about that.  I am attaching the netinfo.txt because I tried two times to post here full text but the forum webserver refused me.  So here it is (I think).

---

### Post by LocoMotor101 on 2013-05-18
I have tried many times to post or to send the netinfor.txt file but all I get is a "Sorry Bad Request"  from the forum webserver.

---

### Post by varunendra on 2013-05-18
LocoMotor101,

First of all, please use 'Code' tags (that we are using to post commands) to post command outputs. It preserves their formatting and makes them easier to read. Just click on **#** symbol at the top of the edit box to auto-generate the tags, them copy-paste the terminal outputs in-between those tags. You may follow the 'Code tags example' link in my signature to see an example.

Onto your problem -
> **LocoMotor101 said:**
> 
oquiros@TOSHI:~$ cat /etc/network/interfaces
auto lo
[B][COLOR="#FF0000"]auto eth0
auto wlan1
iface eth0 inet dhcp loopback[/COLOR][/B]

That ^^ is not the correct format, and probably the very reason why you are getting the  *"The system network service are not compatible with this system"* error (post #22).

Since you are using Network Manager to control your interfaces, let's just set the file back to defaults. Please open the file as root -
```
gksu gedit /etc/network/interfaces
```
..and remove all the lines except the top one. Then add one line "iface lo inet loopback", so that the file looks like this -
```
auto lo
iface lo inet loopback
```
.. just these two lines, nothing more. Proofread, save and close the file. Then reboot to see if the Network Manager starts automatically.

> **LocoMotor101 said:**
> I have tried many times to post or to send the netinfor.txt file but all I get is a "Sorry Bad Request"  from the forum webserver.
You can use [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) to copy-paste the contents of the file there, then post the link it gives you.

Alternatively, you can compress the file if it is too large. Just right-click the file > Compress > choose the format as ".zip" > attach the ".zip" file instead.

---

### Post by LocoMotor101 on 2013-05-19
Varunendra:  Sure enough!  I changed the lines in "interfaces" file and now the network is up at boot. Thanks. Howerver, it only connects via ethernet.  It does not hook up wireless because it continues to ask me for the password, even now that I am connected via ethernet.  It did not do that before.  I will try to send the netinfo.txt in a moment.  No # symbols in my box here, though.

---

### Post by varunendra on 2013-05-19
> **LocoMotor101 said:**
> No # symbols in my box here, though.

It should be in the "Advanced Edit" mode, where I've marked in the attached screenshot.
Or you can just manually add [noparse]```
 .. and..
```[/noparse] at the beginning and end of the desired text :)

---

### Post by wildmanne39 on 2013-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by LocoMotor101 on 2013-05-20
@ Varunendra:   I will post the netinfo.txt this evening when I get back home.  Thanks for the advice.  
@ Kadaha. I wanted to thank you for your patient and dedicated help.  I really appreciate your assistance.

---

### Post by LocoMotor101 on 2013-05-21
Networking seems to be working perfect now.  Thank you!

```
  

*************** info trace ****************

**** uname -a ****

Linux TOSHI 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****

01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8212]
    Kernel driver in use: rtl8192ce

**** lsusb ****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 

**** iwconfig ****

wlan1     IEEE 802.11bgn  ESSID:"Alamedas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**** rfkill ****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****

Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
bnep                   18240  2 
arc4                   12530  2 
rtl8192ce              58779  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 17694  0 
rtl8192c_common        49512  1 rtl8192ce
i915                  530857  3 
rtlwifi                76086  1 rtl8192ce
rts5139               350620  0 
uvcvideo               78117  0 
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_core         33025  1 uvcvideo
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
coretemp               13642  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
rfcomm                 47562  0 
drm_kms_helper         49259  1 i915
psmouse               102075  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
alx                    81351  0 
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   290344  4 i915,drm_kms_helper
ghash_clmulni_intel    13221  0 
compat                 13228  1 alx
mei                    41410  0 
lpc_ich                17145  0 
cryptd                 20531  1 ghash_clmulni_intel
i2c_algo_bit           13565  1 i915
mac_hid                13254  0 
serio_raw              13216  0 
soundcore              15092  1 snd
cfg80211              208382  2 rtlwifi,mac80211
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
microcode              23030  0 
bluetooth             211812  10 bnep,rfcomm
video                  19598  1 i915
parport_pc             32867  0 
ppdev                  17114  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid


**** nm-tool ****

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Alamedas] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Alamedas:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA

  IPv4 Settings:
    Address:         192.168.2.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             200.91.75.5
    DNS:             200.91.75.6


- Device: eth0  [Ifupdown (eth0)] ----------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             200.91.75.5
    DNS:             200.91.75.6


**** NetworkManager.state ****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true
#managed=false


**** NetworkManager.conf-10.04 ****

**** interfaces ****

auto lo
auto eth0
auto wlan1
iface eth0 inet dhcp loopback


**** iwlist ****

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Alamedas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000512c27c5f
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0008416C616D65646173
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020010
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search ice.co.cr


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    9.093234] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[    9.093236] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   10.702114] init: network-interface (wlan1) pre-start process (848) terminated with status 1
[   10.895153] init: network-interface (wlan1) post-stop process (884) terminated with status 1
[  132.860907] type=1400 audit(1368911790.958:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=971 comm="apparmor_parser"
[  132.861315] type=1400 audit(1368911790.958:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=971 comm="apparmor_parser"
[  177.744104] type=1400 audit(1368911835.902:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1898 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  197.929126] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  197.929912] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  200.109705] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  222.702134] wlan1: authenticate with <MAC address removed>
[  222.722113] wlan1: send auth to <MAC address removed> (try 1/3)
[  222.723724] wlan1: authenticated
[  222.737423] wlan1: associate with <MAC address removed> (try 1/3)
[  222.739734] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  222.739888] wlan1: associated
[  222.740878] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


**************** done ********************


```

---

### Post by Hadaka on 2013-05-21
Hi, please post the output of..
```
cat /etc/network/interfaces
```

also your wirelese configuration needs to be
wap2-aes...NOT  TKIP
so please change that as well.
thanks.

---

### Post by LocoMotor101 on 2013-05-21
Hadaka, I checked the security of the wireless and it says WAP2.  Actually, I did not even see any option for TKIP.  Strange.   Let me add that a while ago, wifi go disconnected and I could not get back to reconnect.  I had to re-boot the computer to get it to connect.  ( ? ).  I connected the ethernet and connected alright, but I was not able to navigate, even though the routing tables were OK.  So, I rebooted.

```

oquiros@TOSHI:~$ sudo cat /etc/network/interfaces
[sudo] password for oquiros: 
auto lo
iface lo inet loopback

```

---

### Post by varunendra on 2013-05-21
Please re-run the wireless script and generate a fresh "netinfo.txt" file to show us the current status. The one you uploaded is obviously not current as it is showing the older 'interfaces' file contents.

---

### Post by Hadaka on 2013-05-21
Hi, after you re-run the netinfo, script
and paste it here. then please change the
TKIP setting in your ROUTER settings..
chane it to wpa2-psk or wpa2-aes  .
this should also help speed up your wireless connection.
thanks.

---

### Post by LocoMotor101 on 2013-05-21
I have changed the ROUTER config as indicated.


```


*************** info trace ****************


**** uname -a ****


Linux TOSHI 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8212]
    Kernel driver in use: rtl8192ce


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 


**** iwconfig ****


wlan1     IEEE 802.11bgn  ESSID:"Alamedas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**** lsmod ****

Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
joydev                 17694  0 
rfcomm                 47562  0 
parport_pc             32867  0 
ppdev                  17114  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
cryptd                 20531  1 ghash_clmulni_intel
arc4                   12530  2 
microcode              23030  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts5139               350620  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
psmouse               102075  0 
serio_raw              13216  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192ce              58779  0 
rtl8192c_common        49512  1 rtl8192ce
mac_hid                13254  0 
i915                  530857  3 
rtlwifi                76086  1 rtl8192ce
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         49259  1 i915
cfg80211              208382  2 rtlwifi,mac80211
soundcore              15092  1 snd
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19598  1 i915
alx                    81351  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
compat                 13228  1 alx
lpc_ich                17145  0 
lp                     17800  0 
mei                    41410  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid


**** nm-tool ****


NetworkManager Tool

State: connected (global)

- Device: wlan1  [Alamedas] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Ipc:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    *Alamedas:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2

  IPv4 Settings:
    Address:         192.168.2.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             200.91.75.5
    DNS:             200.91.75.6


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true
#managed=false


**** NetworkManager.conf-10.04 ****


**** interfaces ****


auto lo
iface lo inet loopback


**** iwlist ****

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Alamedas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000018415110
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0008416C616D65646173
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0


**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search ice.co.cr


**** blacklist.conf ****

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

**** dmesg ****


[   12.883983] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[   12.883985] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   13.449324] type=1400 audit(1369174038.364:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=918 comm="apparmor_parser"
[   13.945610] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.960274] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   16.577321] wlan1: authenticate with <MAC address removed>
[   16.597065] wlan1: send auth to <MAC address removed> (try 1/3)
[   16.599844] wlan1: authenticated
[   16.612649] wlan1: associate with <MAC address removed> (try 1/3)
[   16.614882] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   16.615019] wlan1: associated
[   16.615297] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   36.730031] type=1400 audit(1369174061.680:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2086 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************


```

---

### Post by LocoMotor101 on 2013-05-21
By the way, the wifi connection gets disconnected very often, and does not get reconnected unless I re-boot.  I do not know if recent changes to the router will solve this issue.  Hope so.

---

### Post by Hadaka on 2013-05-21
Lets take a look at a couple things..
please do..
```
cat /etc/modprobe.d/rtl8192ce.conf
```
post the results
thanks.

---

### Post by LocoMotor101 on 2013-05-21
Here it is, but it seems the wifi is now stable.  I have not had problems since the router change.

```

oquiros@TOSHI:~$ cat /etc/modprobe.d/rtl8192ce.conf
options rtl8192ce swenc=1


```

---

### Post by Hadaka on 2013-05-21
Great !, everything seems to be working
finally, came a long way from when you first posted.
getting rid of the tkip most likely helped. so at this point
ide say it is no longer broken...dont mess with it...;)
So keep an eye on things, and I think we can finally consider
this solved...
thanks for the fun !

---

### Post by LocoMotor101 on 2013-05-22
Hadaka, thank YOU!  Definitely SOLVED.  //  Now, I have to get the CUPS printing working!

---


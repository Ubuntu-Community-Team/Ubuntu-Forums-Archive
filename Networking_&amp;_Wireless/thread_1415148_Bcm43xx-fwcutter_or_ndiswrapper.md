---
title: "Bcm43xx-fwcutter or ndiswrapper"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by boomerian on 2010-02-24
Gateway MT6451 Laptop; bought used and came with Vista system restore disks - no thanks. Had heard good things about recent Ubuntu success with the Broadcom (4311) chipset for wireless.
After full install of Kubuntu, used KPackage to update all packages and install ndiswrapper and the bcm 802.11 STA driver.
Should I also install the "fwcutter" package?
I'm not at home right now, so don't have access to the laptop in question (currently wired), but will try to get details about the bash responses pasted in later tonight.
I was hoping this would "just work." Does re-starting help? Thanks in advance...

---

### Post by chili555 on 2010-02-24
b43-fwcutter finds and extracts the firmware needed to operate the native driver, b43. If ndiswrapper is installed correctly, b43-fwcutter is not needed. Let's troubleshoot your ndiswrapper install first.```
sudo modprobe ndiswrapper
ndiswrapper -l
iwconfig
```I, or one of my highly experienced colleagues, will look for you tonight.

---

### Post by boomerian on 2010-02-24
Here you go. The first two bash entries just returned me to the prompt (no message - error or otherwise, no response):

ian@Minnmax2:~$ sudo modprobe ndiswrapper
ian@Minnmax2:~$ ndiswrapper -l
ian@Minnmax2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ian@Minnmax2:~$ 

What now, my friends?

---

### Post by bkratz on 2010-02-24
carlee's posting here  (post #7)

[http://ubuntuforums.org/showthread.php?p=8827649#post8827649](http://ubuntuforums.org/showthread.php?p=8827649#post8827649)

using the native broadcom drivers is probably the most trouble free method for the 4311.

A quick alternative that seems to work for most people ( some not) can be found here using the sta driver

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Either way you may have to remove the ndiswrapper module.

---

### Post by boomerian on 2010-02-24
Nothing working so far... 

ian@Minnmax2:~$ sudo modprobe wl
[sudo] password for ian:
FATAL: Module wl not found.
ian@Minnmax2:~$

Any suggestions?

---

### Post by bkratz on 2010-02-24
> **boomerian said:**
> Nothing working so far... 

ian@Minnmax2:~$ sudo modprobe wl
[sudo] password for ian:
FATAL: Module wl not found.
ian@Minnmax2:~$

Any suggestions?

I think it is time to look at the output of 

lsmod
(LSMOD in lowercase)

copy/paste the output back here so we can see what modules are loaded.

---

### Post by boomerian on 2010-02-24
Here you go (thanks!)...

                                  
ian@Minnmax2:~$ lsmod                                           
Module                  Size  Used by                           
isofs                  31620  1                                 
udf                    80900  0                                 
crc_itu_t               1852  1 udf                             
ppdev                   6688  0                                 
joydev                 10240  0                                 
snd_hda_codec_si3054     4636  1                                
pcmcia                 36808  0                                 
snd_hda_codec_idt      59844  1                                 
snd_hda_intel          26920  2                                 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel                                                                        
snd_hwdep               7200  1 snd_hda_codec                                 
snd_pcm_oss            37920  0                                               
snd_mixer_oss          16028  1 snd_pcm_oss                                   
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss                                                                
snd_seq_dummy           2656  0                                               
snd_seq_oss            28576  0                                               
snd_seq_midi            6432  0                                               
snd_rawmidi            22208  1 snd_seq_midi                                  
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi                      
iptable_filter          3100  0                                               
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
tifm_7xx1               5372  0
tifm_core               7832  1 tifm_7xx1
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24296  1
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0
serio_raw               5280  0
i2c_piix4               9932  0
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
k8temp                  4188  0
shpchp                 32272  0
lp                      8964  0
parport                35340  2 ppdev,lp
ohci1394               29900  0
video                  19380  0
output                  2780  1 video
ieee1394               86596  1 ohci1394
sky2                   46528  0
radeon                636000  2
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0
agpgart                34988  3 ttm,drm,ati_agp
ian@Minnmax2:~$

Cheers! Boomerian

---

### Post by Dragonbite on 2010-02-24
Community Wiki Documents on Broadcom wireless drivers.
> [URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"][U]Broadcom BCM43xx Chipset
[/U][/URL]This page aims at getting your BCM43xx chipset based wireless network card to work in Ubuntu. 

Personally I've used ```
sudo apt-get install b43-fwcutter
```and it has worked each time.

My wireless card (for reference)```
$ lspci
<snip>
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```

Unfortunately I haven't had the same luck with KDE as with Gnome, except for Fedora 12 (which saw the Broadcom out-of-the-box) but that was with previous versions of Ubuntu, not anything in the 9.'s

---

### Post by bkratz on 2010-02-25
Seeing the above mentioned url it has a section labeled

"Installing drivers for the BCM4311,4312,4321,4322 Cards

~$ sudo apt-get update && sudo apt-get install bcmwl-kernel-source"

since your card is the BCM4311 this is the section I would follow.

---

### Post by boomerian on 2010-02-25
Thanks, all. I have confirmed that I have the "kernel-source" - everything seems right in that regard. I can't find any reference to "wlan0" so I'm thinking that Kubuntu is not recognizing my wireless card. (iwconfig and ifconfig only shows the eth0)
The laptop is certainly not receiving any wireless signals. I have removed the ndiswrapper packages, and assume that the b43 driver is included in the stuff I downloaded from the Broadcom site (bcm 802.11 STA).
I struggled with an old Linksys WMP54G adapter (also Broadcom) in my old Celeron desktop, and I'm kind of bummed that after five years of messing with these Broadcom wireless chipsets, no Linux distro has been able to figure it out, so that it "just works."
I have gone through the threads referenced - I seem to be missing "wl" (?), but can't find a package that seems to provide it.

---

### Post by bkratz on 2010-02-25
> **boomerian said:**
> Thanks, all. I have confirmed that I have the "kernel-source" - everything seems right in that regard. I can't find any reference to "wlan0" so I'm thinking that Kubuntu is not recognizing my wireless card. (iwconfig and ifconfig only shows the eth0)
The laptop is certainly not receiving any wireless signals. I have removed the ndiswrapper packages, and assume that the b43 driver is included in the stuff I downloaded from the Broadcom site (bcm 802.11 STA).
I struggled with an old Linksys WMP54G adapter (also Broadcom) in my old Celeron desktop, and I'm kind of bummed that after five years of messing with these Broadcom wireless chipsets, no Linux distro has been able to figure it out, so that it "just works."
I have gone through the threads referenced - I seem to be missing "wl" (?), but can't find a package that seems to provide it.


Maybe we should take a giant step backwards and see the output of 

lspci | grep Wireless
(that is LSPCI in lowercase and W in uppercase)

and see if the card is even detected since none of the common Broadcom modules seem to be in your listing.

---

### Post by boomerian on 2010-02-25
Thanks, bkratz - I'll post the response to lspci in about 3 hours, as I'm currently at work and the laptop is at home.
Without the grep (filter?) I remember that I did see the Broadcom line, similar to what's shown in Dragonbite's post on this thread (BCM4311, however, not 4309).
i appreciate your seeing this through! boomerian

---

### Post by boomerian on 2010-02-25
Here 'tis...

ian@Minnmax2:~$ lspci | grep Wireless
ian@Minnmax2:~$

Ouch! nothing/nada...
What now?
Here's the lines from a plain old $lspci:

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

...so it's there,right?

---

### Post by bkratz on 2010-02-25
Yes, it is there. The reason it did not show up with the other command is because the word Wireless was not in there anywhere. Usually it is. I still don't understand why the Broadcom modules don't seem to show up though. Don't know much about Kubuntu, but in Ubuntu if you go to 
System -> Administration -> Hardware Drivers
Here is where you activate the drivers. Does Kubuntu have something like that?

---

### Post by boomerian on 2010-02-25
Yes, Kubuntu has the Hardware Drivers window, and it shows the Broadcom STA wireless driver; says that it is not activated, and has a button for me to Activate. I click on the button, and it appears to "protect" the driver listing (grayed out). When I return to the display, it shows "not activated" again.

---

### Post by bkratz on 2010-02-25
Here is a similar thread where the sta driver remained grayed out. Your card and his/hers uses the same driver. Read posts 1 and 4 and see if it helps.


[http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483)

---

### Post by Dragonbite on 2010-02-25
> **boomerian said:**
> Yes, Kubuntu has the Hardware Drivers window, and it shows the Broadcom STA wireless driver; says that it is not activated, and has a button for me to Activate. I click on the button, and it appears to "protect" the driver listing (grayed out). When I return to the display, it shows "not activated" again.

Yeah, that's what I've gotten each time too, so I gave up on KDE.

UNTIL.. 

Try burning a Fedora LiveCD and running it.  It includes OpenFWWF, which detected my broadcom wirless card out-of-the-box and was immediately usable, in a live session and installed.

---

### Post by boomerian on 2010-02-26
Gracias, Dragonbite. I've been a bit of a "distro-hopper" in my attempts to get wireless, so I'll give Fedora a try! Cheers,

---


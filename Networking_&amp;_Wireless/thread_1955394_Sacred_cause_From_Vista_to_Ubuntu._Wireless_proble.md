---
title: "Sacred cause: From Vista to Ubuntu. Wireless problem"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by Black Pete on 2012-04-09
Hey guys.
I convinced a friend of mine to change from VISTA to Ubuntu, after some virus attacks, and i offered of course to make it happen. He has a Fujitsu-Siemens Amilo Xi 3650.

Everything installed absolutely fine (64bit). But, I need some help with the wireless function. To be more precise, i need some help with the unlocking or the enabling of the wireless card. The laptop has of course a function key, which combining with F1 would switch ON/OFF the wireless card (by Intel).
I know that it worked when i used the laptop with the VISTA system, before installing UBUNTU. I read somewhere that MS makes some secret codes in order to prevent users from changing OSs.

But now, even though that the other Function key combination work, this specific one doesn't. The signifying light of it works, by the way; it's stays always on.. no change. 
I've read so many posts about similar subjects but i managed to do nothing at all. The system recognizes the card, but it says "**network DISABLED**". :mad: Of course the option to turn it on from the Network menu in not activated.

Any help here please?
This is very narrow thing. If i can't find a solution, i'll have to return somehow to Windows and i'd hate that.. But after all, usability is the most important thing, no?

thank you in advance
G.

---

### Post by chili555 on 2012-04-09
Please open a terminal and run and post:```
rfkill list all
lsmod
```Thanks.

---

### Post by Black Pete on 2012-04-09
Here: 

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2012-04-09
> 1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That implies that the hardware switch, Fn+F1 possibly, has the wireless radio turned off. Is there any change when you press the keys and run it again?```
rfkill list all
```How about *lsmod*?

---

### Post by Black Pete on 2012-04-09
this is what i'm doing all day...
nothing works! The light stays on (which in other case, would mean that the Wireless it's actual ON), but nothing changes.. 
the rest of the combinations 'Fn + ...' all work, except this one..

**lsmod:**
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330815  1 
arc4                   12529  2 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
mceusb                 17906  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               728722  0 
btusb                  18600  2 
iwlagn                314257  0 
bluetooth             166112  23 bnep,rfcomm,btusb
ttm                    76805  1 nouveau
mac80211              462046  1 iwlagn
psmouse                73882  0 
mxm_wmi                12979  1 nouveau
soundcore              12680  1 snd
i915                  571251  3 
serio_raw              13166  0 
cfg80211              199630  2 iwlagn,mac80211
wmi                    19256  1 mxm_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  2 nouveau,i915
drm                   236290  6 nouveau,ttm,i915,drm_kms_helper
lp                     17799  0 
i2c_algo_bit           13423  2 nouveau,i915
parport                46562  3 parport_pc,ppdev,lp
video                  19412  2 nouveau,i915
usb_storage            57901  0 
uas                    18027  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                160582  0 
ahci                   26002  3 
libahci                26861  1 ahci

---

### Post by chili555 on 2012-04-09
How about *lsmod*?```
lsmod
```I think there is a helper application loaded that is supposed to recognize and operate the Fn keys. We may need to modify or unload it. In order to figure it out, I need to see what it is, please.

---

### Post by Black Pete on 2012-04-09
i uploaded it.. we're writing at the same time..

---

### Post by chili555 on 2012-04-09
Oops, sorry!

Let's try a few things. We have to stumble on the key and then figure out how to make it persistent. Please run:```
sudo rfkill unblock all
rfkill list all
```Any change? Now try:```
sudo modprobe -r mxm_wmi
sudo rfkill unblock all
rfkill list all
```Then try:```
sudo modprobe fujitsu-laptop
sudo rfkill unblock all
rfkill list all
```I'd also love to see:```
dmesg | grep -i dmi
```Interesting little problem you have there.

---

### Post by Black Pete on 2012-04-09
Sorry for the delay. So here it is:

1.  the same. no change
2. FATAL: Module mxm_wmi is in use.
then the same as above.
3. AMILO-Xi-3650:~$ sudo modprobe fujitsu-laptop
AMILO-Xi-3650:~$ sudo rfkill unblock all
AMILO-Xi-3650:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4. [    0.000000] DMI present.
[    0.000000] DMI: FUJITSU SIEMENS AMILO Xi 3650/XY680   , BIOS 1.0E-1646-0021 11/12/2008


(Wireless networks are turned off by hardware switch. Says on the top connections menu).

---

### Post by chili555 on 2012-04-09
Congratulations! You are subject to an official bug!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515090)> A BIOS update has fixed the issue for me, marking as invalid.And...> BIOS version is now [COLOR="Red"]1.0H[/COLOR]

moritz@Laptop:~$ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
I notice your BIOS version is earlier:> BIOS [COLOR="Red"]1.0E[/COLOR]-1646-0021 11/12/2008Are you able to update your BIOS?

---

### Post by Black Pete on 2012-04-10
To tell you the truth, i read this post, but i saw that even after upgrading he had the same problems. 
And then i downloaded the Bios Upgrade from Fujitsu -even though they say it's not tested- but it was an .exe file, that Linux cannot handle. So i didn't know what to do with it..
Having in mind that the laptop is not mine, made me not go further...
Should i do it? I'm not very familiar with these procedures. I think i did that once in the past..
I must make a boot disk, no? 

I'll search for it..

Any suggestions?

---

### Post by chili555 on 2012-04-10
> Should i do it? I'm not very familiar with these procedures. I think i did that once in the past..
I must make a boot disk, no?

I'll search for it..I believe that is the procedure. I'd search Fujitsu's website for the instructions. I suspect the .exe creates an image file (.iso??) that you burn to a CD. I think you then boot from the CD by setting the boot order in the BIOS. It then installs the later BIOS.

Since the computer is not yours, I'd be sure to get the owner's permission first.

I suspect you can run the .exe and make the boot disk from any Windows computer, not just the one for which the BIOS is being updated. Search and be sure first!

---

### Post by Black Pete on 2012-04-11
"Thank you for contacting the Fujitsu Technology Solutions support.

To enable the wireless function with the key combination Fn + F1, the program 'Hotkey Utility have to be installed.

Unfortunately, Ubuntu (or Linux in general) is not supported on this notebook.
The program 'hotkey utility' is therefore only in the Windows version available for download.

We are available for other questions to you with pleasure.

Yours sincerely"

No word for the BIOS question

---

### Post by chili555 on 2012-04-11
Let's explore another possibility: [http://www.linuxforums.org/forum/hardware-peripherals/160359-rf-devices-disabled-after-returning-suspend-disk.html](http://www.linuxforums.org/forum/hardware-peripherals/160359-rf-devices-disabled-after-returning-suspend-disk.html)> In a terminal window, enter this command.

```
cat /sys/class/rfkill/rfkill0/state

```
This will output a number, either 0 or 1.

0= wireless disabled
1= wireless enabled
On my system, it turns out to be /sys/class/rfkill/rfkill[COLOR="Red"]1[/COLOR]/state. We can try:```
sudo su
echo 1 > /sys/class/rfkill/rfkill0/state
exit
```Then check:```
rfkill list all
```If it works, we can automate it.

---

### Post by Black Pete on 2012-04-11
"Thank you for your reconsideration request technical support from Fujitsu Technology Solutions.

We recommend the upgrade to the version 1.0H.
But we have only the current version 1.0H to download:

[http://support.ts.fujitsu.com/Download/Showdescription.asp?SoftwareGUID=CF6A24D0-236A-484C-984F-79FDD18AD4FB](http://support.ts.fujitsu.com/Download/Showdescription.asp?SoftwareGUID=CF6A24D0-236A-484C-984F-79FDD18AD4FB)

Yours sincerely"

---

### Post by chili555 on 2012-04-11
The zip extracts to a folder which includes an .iso file. Burn *as an image* to a CD, reboot and flash, I believe. Please read and follow all the instructions before you proceed.

Please see attached screenshot from Brasero showing burn image.

---

### Post by Black Pete on 2012-04-11
1. indeed it showed **1**.
2. 
mustafa@mustafa-AMILO-Xi-3650:~$ sudo su
[sudo] password for mustafa: 
root@mustafa-AMILO-Xi-3650:/home/mustafa# echo 1 > /sys/class/rfkill/rfkill0/state
root@mustafa-AMILO-Xi-3650:/home/mustafa# exit
exit
mustafa@mustafa-AMILO-Xi-3650:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

nothing i'm afraid...
i'm writing the image file already.. so unless you have another suggestion, and "with God's help", i'm going to flash the BIOS..

---

### Post by chili555 on 2012-04-11
> i'm writing the image file already.. so unless you have another suggestion, and "with God's help", i'm going to flash the BIOS..I have my fingers and toes crossed. If in doubt, stop and ask.

---

### Post by Black Pete on 2012-04-11
You won't believe it, it's **fixed**!!! **The wireless works!!!**
I did the BIOS upgrade and then moved on to a new installation.
And as the installation was progressing, i could switch it off and on, and this was visible in the networks menu.
Now it's running perfectly.
Hey man, you don't know how much i appreciate your help and contribution.

Thanks so much!
B. P.

---

### Post by chili555 on 2012-04-11
> You won't believe it, it's fixed!!! The wireless works!!!
I did the BIOS upgrade and then moved on to a new installation.Awesome! I'm glad it's working.

Please use thread tools at the top to Mark Solved.

---

### Post by Black Pete on 2012-04-11
To tell you the truth, i think that -since i could switch it on/off when the installation was in progress- maybe when the machine is starting up (and the O.S. isn't yet in control) that someone could do that, even without the BIOS update.. i'm not sure about that anymore, i haven't tried it, but i'm judging from what i saw..

Anyway, the problem is solved.
Thanks again

---


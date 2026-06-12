---
title: "Wireless and Modem 3g"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jacob313 on 2010-05-11
Why it is so hard to get some wireless cards works on Ubuntu with its recent versions. Am using hp 6730b and I could not get wireless working even after upgrading to 10.4. There are hundreds of posts discussed the issue and it seems non solved issues. Remember windows xp, vista, 7 you don't need tens of meaningless commands and workarounds and months of waiting a solution for such problem, all what is needed is update windows or installation of the driver. I liked Ubuntu but with no serious steps from company to make it easier for users I don't think it will do any progress among those people.

Another issue is e1750 3g stick which I luckily got a script to make it easier to get it working but am facing a problem finding a tool to send sms from. I tried vodafone software but it did not recognise modem.

---

### Post by iponeverything on 2010-05-11
This a bit more on venting side that looking for help.

3G support is moving along, hopefully it get their sooner rather than later. In the meantime to help save your sanity, perhaps you should wonder off into the seductive arms of your mistress, Windows 7.

---

### Post by alexfish on 2010-05-11
hi

3g connection ;have you tried Wammu , it should be in the repo's , use Synaptic Package Manager to install

then use from the terminal 

Code:

wammu

if not in the menus list

 right click on   menus, select edit menus ,select new item , Browse , then locate the file

---

### Post by jacob313 on 2010-05-12
hi buddy "iponeverything" I don't have much of your english vocabloury but consider the effort made to get something work in Ubuntu and to do in windows 7. Am not complaining in order to change , am looking for a solution .. a simple solution. If you have just post it , if not don't play the lawyer role .

alexfish .. I tried Wammu but the modem is not detected in Wammu .

---

### Post by iponeverything on 2010-05-12
> **jacob313 said:**
> hi buddy "iponeverything" I don't have much of your english vocabloury but consider the effort made to get something work in Ubuntu and to do in windows 7. Am not complaining in order to change , am looking for a solution .. a simple solution. If you have just post it , if not don't play the lawyer role .

alexfish .. I tried Wammu but the modem is not detected in Wammu .

ok then.. Just some small words of advice:

Do not post out of frustration. 

This is your problem:

> [B][COLOR="Red"]Am using hp 6730b and I could not get wireless working even after upgrading to 10.4.[/COLOR]
[/B]

And it gets totality lost in below paragraph. Nothing else in there is relevant to your issue and only serves to provoke the reader. If you are really looking for help, why are you trying to anger the very people that you are looking for help from?

> Why it is so hard to get some wireless cards works on Ubuntu with its recent versions . Am using hp 6730b and I could not get wireless working even after upgrading to 10.4 . There are hundreds of posts discussed the issue and it seems non solved issues . Remember windows xp , vista , 7 you don't need tens of meaningless commands and workarounds and months of waiting a solution for such problem , all what is needed is update windows or installation of the driver . I liked Ubuntu but with no serious steps from company to make it easier for users I don't think it will do any progress among those people .


Now -if you really do want help- Lets get some information that might help in figuring out how to solve your problem.

Please post the output of:

This is a command to help identify your wireless hardware.
```

sudo lshw -c network | grep -A 15 Wireless

```

This a a command to help identify your wireless hardware.
```

lspci |grep Network

```

A command to show loaded kernel modules.
```

lsmod

```

This will tell us if your system is recognizing your wireless hardware. 
```
iwconfig
```

---

### Post by jacob313 on 2010-05-15
[SIZE=4]Sorry and thanks in advance .
[/SIZE]sudo lshw -c network | grep -A 15 Wireless
[SIZE=4]the first command redirects me to sysinfo utility and it shows the following descreption about wireless :

Broadcom Corporation BCM4312 802.11b/g (rev 01)

[/SIZE] 	lspci |grep Network
[SIZE=4]shows:
[SIZE=3]02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/SIZE]

[/SIZE]lsmod
[SIZE=4]show:
[/SIZE] 	Module                  Size  Used by
usb_storage            39425  0 
snd_hda_codec_analog    58566  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
iptable_nat             4414  0 
nf_nat                 15735  1 iptable_nat
nf_conntrack_ipv4      10672  3 iptable_nat,nf_nat
nf_conntrack           61583  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  0 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  2 iptable_nat,ip_tables
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
ndiswrapper           184677  0 
i915                  282354  3 
drm_kms_helper         29297  1 i915
tpm_infineon            7745  0 
tpm                    13484  1 tpm_infineon
snd                    54148  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
tpm_bios                5266  1 tpm
psmouse                63245  0 
serio_raw               3978  0 
hp_accel               11144  0 
lis3lv02d               6007  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  1 hp_accel
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
tg3                   109292  0 
ssb                    37336  0 

iwconfiglo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by pdc on 2010-05-15
would anything in this help you?

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by iponeverything on 2010-05-15
BCM4312 is supported by through a proprietary driver.

From the top toolbar go to:

System -> Administration -> Software Sources 

and enable Proprietary drivers then choose to reload the package information when ask -- then go to

System -> Administration -> Hardware Drivers 

And see if you see the Broadcom driver, activate it. 

I hope your fix is as easy as this..

---


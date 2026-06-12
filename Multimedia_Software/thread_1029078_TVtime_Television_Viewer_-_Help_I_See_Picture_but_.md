---
title: "TVtime Television Viewer - *Help* I See Picture but no Sound"
date: 2009-01-03
forum: Multimedia Software
---

### Post by sendblink23 on 2009-01-03
TVtime Television Viewer - *Help* I See Picture but no Sound

Running Ubuntu 8.10

Exactly that, I see picture perfectly, with that program, I downloaded it from *Add/Remove*

I just simply don't get any sound, in that program.

Everything else on Sounds works perfectly: Flash(youtube or websites), RhythmBox, MoviePlayer, VLC or any normal computer sound 

I have no clue what tv card I have on my computer, all I know on my HP normally on Windows XP I could watch TV on Media Center, thats why I installed it to check if it recognized the hardware.. in which it did.

Any ideas whats wrong with not having any sound on TVtime?

---

### Post by cariboo on 2009-01-03
Double click on the speaker icon on the top panel and see if line in is turned up.

Jim

---

### Post by sendblink23 on 2009-01-03
> **cariboo907 said:**
> Double click on the speaker icon on the top panel and see if line in is turned up.

Jim

..Hmm Obvious... 

I just tested  Watching a Website in the side (that has flash like Myspace, youtube...).. and opening Rhythmbox.. reading my iPhones music.. 

All normal working perfectly.. closed them and tried that application (TVtime).. *nopes no sound..    Speaker Volume is at MAX   ..

---

### Post by sendblink23 on 2009-01-03
Any commands .. or anything. that can help me out?

I also tested playing a DVD Movie and the sound came as normal all good.


Since all sounds work perfectly.. its just with that program *TVtime the only one Sound issue I have

---

### Post by xc3RnbFO8P on 2009-01-03
This works for me:
> **arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &**
<return>
**exit**
<return>

To **turn it off**, you have to **Log Out** or **Restart** the computer.

---

### Post by sendblink23 on 2009-01-03
> **Ringi said:**
> This works for me:

To **turn it off**, you have to **Log Out** or **Restart** the computer.

Anyways I tried inserting just the first command.. and it already exits *terminal .. not needing: Exit

But anyways **it didn't do anything** for ***TVtime**... (I See picture perfect, but no Sound)

After testing, all the other programs & websites (to notice if any difference occur) nothing changed... everything else works great in sounds

I just restarted the computer, just reset anything.. since you mentioned it to to turn that off, from your command.

**So anyways... Any other commands I could try?**

---

### Post by xc3RnbFO8P on 2009-01-03
You can try this, does not work for me:
> play -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp1 & tvtime && killall sox

---

### Post by xc3RnbFO8P on 2009-01-03
You can also try to change **hw:[COLOR="SeaGreen"]1[/COLOR],[COLOR="SeaGreen"]0[/COLOR]**

---

### Post by sendblink23 on 2009-01-03
> **Ringi said:**
> You can also try to change **hw:[COLOR="SeaGreen"]1[/COLOR],[COLOR="SeaGreen"]0[/COLOR]**

Just in case...  how should I apply that?

Give an example

---

### Post by sendblink23 on 2009-01-03
> **Ringi said:**
> You can try this, does not work for me:

After inserting your Command, it opened up TVtime..  no sound..

Its mentioning me looking at the Terminal Window..  that I do not have  sox  installed

Its telling me to install it:  sudo apt-get install sox

I'm not gonna install it since, that command you gave me is to kill that process

---

### Post by sendblink23 on 2009-01-03
... Bump...

---

### Post by sendblink23 on 2009-01-03
BUMP BUMP  any help on my weird issue?

---

### Post by sendblink23 on 2009-01-04
I still need help here....

---

### Post by sendblink23 on 2009-01-05
Extra bump bump*~...

---

### Post by amac777 on 2009-01-05
What TV card do you have? 

On the one I used to have, it required physically plugging a small cable (earphone jacks on both ends of the cable) from a SOUND OUT plug on the TV card to the LINE IN plug on the sound card. Once you do this, you will be able to adjust the volume and settings for the TV through your regular volume control settings for LINE IN.

Perhaps you need to do that on your TV card too?

---

### Post by sendblink23 on 2009-01-05
> **amac777 said:**
> What TV card do you have? 

On the one I used to have, it required physically plugging a small cable (earphone jacks on both ends of the cable) from a SOUND OUT plug on the TV card to the LINE IN plug on the sound card. Once you do this, you will be able to adjust the volume and settings for the TV through your regular volume control settings for LINE IN.

Perhaps you need to do that on your TV card too?

My TV Card is directly inside naturally in my HP Computer...  all i see from behind my computer is  *INPUT for  AV (Red & White), TV/Cable, S-Video & FM Ant

I have no clue.. what is the type of sound card my computer has from manufacture in this HP

---

### Post by sendblink23 on 2009-01-05
Could you take a picture of your Cable.. so that i could get it over here, and test it out?

---

### Post by amac777 on 2009-01-05
Most software-based TV tuners do not process audio and must connect to the sound card to enable audio. If this is your situation, your tuner should have a stereo Audio out port (on the card itself) to which you should connect a stereo cable going to the Audio in port on your sound card.

The cable looks like this: (both ends of the cable shown)
[http://cdn.overstock.com/images/products/3/L11144276.jpg](http://cdn.overstock.com/images/products/3/L11144276.jpg)

By the way, a quick way to test this is just to plug earphones directly into your TV tuner card and make sure you hear the sound through the earphones when you use TV time. If that works, then using a cable such as shown above will work. If you can't hear sound or you don't have an audio out port on your TV card, then your problem might be something else.

---

### Post by sendblink23 on 2009-01-05
I did say in my Post Above.. it only has  *INPUT   .. in other words  no *OUTPUT the TV Card :( ... so yes.. it probably.. is something else then

I do have that cable here and also the plugs to convert them to *AV(Red/White)  but since it only has *INPUT* on the TV Card.. in the back of my computer yups.. it won't work

Well i guess i need someone to help me out .. in commands... or something else then.. to add here to test

Thanx anyways



> **amac777 said:**
> Most software-based TV tuners do not process audio and must connect to the sound card to enable audio. If this is your situation, your tuner should have a stereo Audio out port (on the card itself) to which you should connect a stereo cable going to the Audio in port on your sound card.

The cable looks like this: (both ends of the cable shown)
[http://cdn.overstock.com/images/products/3/L11144276.jpg](http://cdn.overstock.com/images/products/3/L11144276.jpg)

By the way, a quick way to test this is just to plug earphones directly into your TV tuner card and make sure you hear the sound through the earphones when you use TV time. If that works, then using a cable such as shown above will work. If you can't hear sound or you don't have an audio out port on your TV card, then your problem might be something else.

---

### Post by sendblink23 on 2009-01-05
Any other Software Application I could install in here..  that shows TV also like TVtime ..  so that I could test on a different application.. to see if it has a different outcome ??

---

### Post by sendblink23 on 2009-01-05
Bump 

... heading to sleep .. hope to see..  some help provided.. and  ANY recommendations of other applications I could install.. that would work the same as what TVtime does.. to watch TV :)

:popcorn: :P

---

### Post by sendblink23 on 2009-01-05
BUMP BUMP ...  awaiting help :)

---

### Post by sendblink23 on 2009-01-05
...  anybody??

---

### Post by sendblink23 on 2009-01-06
i stil need help here..  ???

---

### Post by xc3RnbFO8P on 2009-01-06
Did you try to change it to  hw:1,1 ?

---

### Post by sendblink23 on 2009-01-06
I asked you before... to give me an Example on how to do that...

[I]"Quote:Originally Posted by Ringi  
You can also try to change hw:1,0"

*I replied:
Just in case... how should I apply that?

Give an example"[/I]


> **Ringi said:**
> Did you try to change it to  hw:1,1 ?

---

### Post by xc3RnbFO8P on 2009-01-06
arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - & arecord -D hw:1,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &

just copy/paste into Terminal one by one.

---

### Post by sendblink23 on 2009-01-06
I tried doing the first one: arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &

Then it mentioned me.. that i didnt had *sox installed.. so I set the sudo command to install it...

Afterwards ... I re ran  that command, and it said.. something that i requested 32000  and it gave 42000       ..  some error like that

it kept repeating something and then it suddenly closed *Terminal*

Now I went to try to insert that command again, to try to copy what it gave me.. to show you exactly...  but it says this:

sendblink23@sendblink23-desktop:~$ arecord: main:583: audio open error: Device or resource busy
play soxio: Can't open input file `-': WAVE: RIFF header not found
sendblink23@sendblink23-desktop:~$ 



> **Ringi said:**
> arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - & arecord -D hw:1,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &

just copy/paste into Terminal one by one.

---

### Post by sendblink23 on 2009-01-06
what does the command  "arecord"   means?

is it for recording...  becuase at the end i read in the command it says Wav ....   and it also mentions a frequency  32000...

I am not looking for recording anything... just simply to hear my TV channels


just incase I am simply randomly asking .. trying to understand what the command is actually doing... 

"arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &"

---

### Post by sendblink23 on 2009-01-06
This is more info I could get:


**lsmod**
```

Module                  Size  Used by
isofs                  40100  0 
udf                    88356  0 
crc_itu_t              10112  1 udf
ipv6                  263972  10 
af_packet              25728  4 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
cx88_blackbird         24836  0 
cx2341x                21124  1 cx88_blackbird
tuner_simple           22288  1 
tuner_types            21888  1 tuner_simple
evdev                  17696  6 
arc4                    9984  2 
serio_raw              13444  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
tea5767                14980  0 
psmouse                45200  0 
tda9887                18564  1 
pcspkr                 10624  0 
tda8290                20868  0 
rtl8187                53120  0 
snd_hda_intel         381488  3 
mac80211              216820  1 rtl8187
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
eeprom_93cx6           10240  1 rtl8187
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
tuner                  33096  0 
cfg80211               32392  2 rtl8187,mac80211
cx8802                 23812  1 cx88_blackbird
cx8800                 38208  1 cx88_blackbird
cx88xx                 75944  3 cx88_blackbird,cx8802,cx8800
compat_ioctl32          9344  1 cx8800
videodev               41344  4 cx88_blackbird,tuner,cx8800,cx88xx
v4l1_compat            22404  1 videodev
ir_common              48132  1 cx88xx
i2c_algo_bit           14340  1 cx88xx
v4l2_common            19840  4 cx88_blackbird,cx2341x,tuner,cx8800
snd_seq_dummy          10884  0 
tveeprom               20228  1 cx88xx
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
i2c_core               31892  9 tuner_simple,tea5767,tda9887,tda8290,tuner,cx88xx,i2c_algo_bit,v4l2_common,tveeprom
videobuf_dma_sg        20612  4 cx88_blackbird,cx8802,cx8800,cx88xx
videobuf_core          26628  5 cx88_blackbird,cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              12552  3 cx8802,cx8800,cx88xx
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
button                 14224  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
sg                     39732  0 
usb_storage            81728  0 
libusual               27156  1 usb_storage
ata_piix               24580  2 
8139too                31616  0 
ata_generic            12932  0 
ohci1394               37936  0 
8139cp                 27520  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  6 sbp2,sd_mod,sr_mod,sg,usb_storage,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
mii                    13440  2 8139too,8139cp
usbcore               148848  6 rtl8187,usb_storage,libusual,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


```





**lspci**
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:04.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)


```




Hope this helps

---

### Post by xc3RnbFO8P on 2009-01-06
I told you you have to restart or log out to turn it off.
If you do arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
start Tvtime, if it doesn't work, restart or log out and try another option.

---

### Post by sendblink23 on 2009-01-06
I tested them all .. and Copied all the outcomes of Each (yes, I tested on TVtime, Logged out & restarted afterwards)

Only the first 1 reacted differently..  but no matter what on all of them I did not get any audio through Tvtime

here are the outcomes of all:

```

arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:0,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - & 
arecord -D hw:1,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
arecord -D hw:1,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &


sendblink23@sendblink23-desktop:~$ arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 6062
sendblink23@sendblink23-desktop:~$ Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
Warning: rate is not accurate (requested = 32000Hz, got = 44100Hz)
         please, try the plug plugin 
overrun!!! (at least -1385562784.839 ms long)
overrun!!! (at least -1385562820.570 ms long)
overrun!!! (at least -1385562781.615 ms long)
overrun!!! (at least -1385562765.532 ms long)
overrun!!! (at least -1385562812.553 ms long)
overrun!!! (at least -1385562783.997 ms long)
overrun!!! (at least -1385562783.919 ms long)
overrun!!! (at least -1385562772.432 ms long)
overrun!!! (at least -1385562793.575 ms long)
overrun!!! (at least -1385562812.413 ms long)
overrun!!! (at least -1385562824.332 ms long)
overrun!!! (at least -1385562790.499 ms long)
overrun!!! (at least -1385562783.000 ms long)






sendblink23@sendblink23-desktop:~$ arecord -D hw:0,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 5974
sendblink23@sendblink23-desktop:~$ arecord: main:583: audio open error: No such file or directory
play soxio: Can't open input file `-': WAVE: RIFF header not found






sendblink23@sendblink23-desktop:~$ arecord -D hw:0,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 5981
sendblink23@sendblink23-desktop:~$ arecord: main:583: audio open error: No such file or directory
play soxio: Can't open input file `-': WAVE: RIFF header not found




sendblink23@sendblink23-desktop:~$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - & 
[1] 5932
sendblink23@sendblink23-desktop:~$ ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
arecord: main:583: audio open error: No such file or directory
play soxio: Can't open input file `-': WAVE: RIFF header not found





sendblink23@sendblink23-desktop:~$ arecord -D hw:1,1 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 5925
sendblink23@sendblink23-desktop:~$ ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
arecord: main:583: audio open error: No such file or directory
play soxio: Can't open input file `-': WAVE: RIFF header not found




sendblink23@sendblink23-desktop:~$ arecord -D hw:1,2 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 5908
sendblink23@sendblink23-desktop:~$ ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
arecord: main:583: audio open error: No such file or directory
play soxio: Can't open input file `-': WAVE: RIFF header not found



```

---

### Post by sendblink23 on 2009-01-08
> **Ringi said:**
> I told you you have to restart or log out to turn it off.
If you do arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
start Tvtime, if it doesn't work, restart or log out and try another option.




Nopes it did not work...  look at my Past Post  for all the info ..  and  look at  another past before.. I Included more info about my machine... with gives Drives  info and stuff  inside my computer.. to see if you can help me with any of that Info Data.

---

### Post by sendblink23 on 2009-01-09
Can anybody help.... ?


If i get like 2 more days of no success.. I will give up.. the TV thing on Linux hehee ...  it has been a battle for it :P

---

### Post by Devport on 2009-01-09
If your card has no audio out it may be connected to audio internally - in volume settings panel loook for everything that could be the input for the tv card. e.g. check that line-in, microphone and any other possible input are unmuted and have a high volume.

I did not see what tv card you use - if you dont know it right now please do lshw and check for a section describing your tv card, in my case it looks like that :

        *-multimedia
             description: Multimedia controller
             product: SAA7134/SAA7135HL Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 7
             bus info: pci@0000:05:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=255 mingnt=255 module=saa7134

The saa7134 chipset for instance supports audio over pci which would be another way to get sound.

---

### Post by sendblink23 on 2009-01-09
Sure thing i wil insert the commands in a few minutes..  im curently out of mu house  answering through my iphone

And yes all settings from my sounds in Linux none have Mute and all Volumes are almost at Max... just to be certain

Anyways in a few minutes  i'll  send my  Outcome  of that command  so that you could help me out of my tvcard.


> **Devport said:**
> If your card has no audio out it may be connected to audio internally - in volume settings panel loook for everything that could be the input for the tv card. e.g. check that line-in, microphone and any other possible input are unmuted and have a high volume.

I did not see what tv card you use - if you dont know it right now please do lshw and check for a section describing your tv card, in my case it looks like that :

        *-multimedia
             description: Multimedia controller
             product: SAA7134/SAA7135HL Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 7
             bus info: pci@0000:05:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=255 mingnt=255 module=saa7134

The saa7134 chipset for instance supports audio over pci which would be another way to get sound.

---

### Post by sendblink23 on 2009-01-09
Here is what i got

**lshw**:

> 
    *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
           *-multimedia:1
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant Systems, Inc.
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802


---

### Post by Devport on 2009-01-09
What devices do you have in the volume app - there should be audio devices belonging to your tv card ( cx... ). Make sure that those are unmuted.

Then you may want to try the arecord command mentioned earlier - but you have to find the correct card. So arecord -D hw:1,0 ... has to refer to the correct card, e.g. hw:2,0 or hw:3,0. Since I dont have such a card all I can recommend is to search on the web for others having sound problems with cx... - I am pretty sure its possible - you just have to find the information.

You need to understand that the tv-card is one device and the audio card is another device. And either they are connected via cable or they are separate devices in alsa and you have to bring the sound output of the tv-card to the sound card. Thats what the arecord command is for - it records the sound from tv-card and outputs it to the soundcard - for this to work you must use the correct devices for in- and output.

Furthermore some cards with your chipset seem to support dvb-t - you may want to check if thats the case with your card so you could use a dvb-t app, e.g. kaffeine for that.

Edit : arecord -l will list the devices that are available.

---

### Post by sendblink23 on 2009-01-09
This is what i got:


> 
sendblink23@sendblink23-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 4: ALC880 Analog [ALC880 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1




Trust me, nothing is unmuted... I'm not that *noob using Ubuntu, i had 8.04 before...  it was a huge hassle to get even the natural System sounds to work, and i figured how to do it in all the system, websites and any music / video player to work.... without any help.. just me testing around things i read around the forums, also the huge hassle of wifi to work.

But since now in 8.10 I actually for the first time.. I'm totally pleased, it naturally since install Recognized all my Audio & Wifi, and simply install the regular plugins for codecs, and the normal flash pluggin & totem inside Add/Remove... I do not need anything else, so its kinda weird that only 1 device is not recognizing audio.. believe me teh first thing I went was *Right-Click the  Sound Speaker in the Top Menu ..  and  start testing everything out to notice any changes.. but nothing happened. I also installed a couple of other TV Applications.. none of them recognized my TVcard...  totally weird and in no way will I would want to go manual install commands for that to work.. for certain.. cards.. blah blahh (not going back to hassle days, its better to leave as-is..  since its a 4 year old computer, I should expect things not to work properly *i'm used to it... its linux not everything is expected to work 100%)

I only added TVtime because I knew it read my Tvcard before on 8.04 and yes sound was working since I normally installed it, but it was working by default as of the huge hassle fixes I did before(i had made to the computer to work sounds)...  I can't remember anything cause it was months ago.

Anyways

Now that I gave you my **arecord -l** what should be the correct command I should run in Terminal?

---

### Post by Devport on 2009-01-09
Thats strange - there is no audio device to record listed for your tv card. I think you need to search the web for your tv card and find out how to get it working.

If you have Windows installed you can try DScaler or some other app to check that its working there and find out which exact tv card it is. Since the module supports several tv-cards it may be that it does not autodetect your tv card correctly - so you need to know which card it is.

---

### Post by sendblink23 on 2009-01-09
> **Devport said:**
> Thats strange - there is no audio device to record listed for your tv card. I think you need to search the web for your tv card and find out how to get it working.

If you have Windows installed you can try DScaler or some other app to check that its working there and find out which exact tv card it is. Since the module supports several tv-cards it may be that it does not autodetect your tv card correctly - so you need to know which card it is.

What is the purpose for DScaller?
Is it for windows to check if its working?

It works perfectly fine on my Windows.. my computer came naturally with Windows Media Center, it works just perfectly fine.. exactly as of the first time I bought this computer, opened that MCE application to watch TV on my PC.

I'm  going to head to [www.hp.com](www.hp.com) and get the exact name of the natural tv card my computer came with.

---

### Post by sendblink23 on 2009-01-09
This is the only Info I could find over HP.com of the TVcard

Hauppauge WinTV PVR PCI II Series TV Tuner Driver

And over the web it appears its the only available info of it, for my PC.

Really weird I also noticed there was also a release of another version of my same named Computer, but with a difference Specs inside..  mines is Pentium 4, the other one is Pentium D .. and it has other changes as well.

In other words..  that new version replaced any info around the internet for my Computer, even inside of hp.com.

So I'm not completely sure that is the exact name for my natural internal Tvcard, by that issue.

Doesn't the info I provided before, with commands..  give you the name for my Tv Card ?


> 
*-multimedia:0
description: Multimedia video controller
product: CX23880/1/2/3 PCI Video and Audio Decoder
vendor: Conexant Systems, Inc.
physical id: 4
bus info: pci@0000:02:04.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
*-multimedia:1
description: Multimedia controller
product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
vendor: Conexant Systems, Inc.
physical id: 4.2
bus info: pci@0000:02:04.2
version: 05
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802 


---

### Post by ultimate user on 2009-03-14
I also use tv time and had some trouble with the sound.

Try copy and paste this in the terminal when tv time is running
```
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &
```
If you then get sound, open gedit and paste this in it
```
#!/bin/sh
echo
tvtime  &

sleep 4

echo
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &

```
save it with name of your choice to your desktop, click on it and choose "run" to see TV

---

### Post by hackys on 2009-04-25
> **ultimate user said:**
> I also use tv time and had some trouble with the sound.

Try copy and paste this in the terminal when tv time is running
```
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &
```


Thanks, this solved my problem with the sound.. i just modified it a bit
```
arecord -D hw:1,0 -f dat -t wav | aplay -&
```

---

### Post by dimis80 on 2009-04-28
I need help on this too. :confused:

I have in my desktop an Intel sound card and when I open TVTIME i can only see but not hear any sound from the programs playing.

Can you please guide me to fix this issue???
This is the only problem that I have...

thanks!

---

### Post by sendblink23 on 2009-04-28
nice, people still help me here.


Well, I'm back... but now on 9.04 .. I'll give it a try in a bit... those last helps that were suggested

I'll post back my results

---

### Post by sendblink23 on 2009-04-28
Tested Both, mentioned above... none worked they gave me errors

:(

```

sendblink23@ubuntu:~$ arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
arecord: main:590: audio open error: No such file or directory
[1] 7115
sendblink23@ubuntu:~$ aplay: playback:2208: read error

```





```

sendblink23@ubuntu:~$ arecord -D hw:1,0 -f dat -t wav | aplay -&
[1] 7110
sendblink23@ubuntu:~$ ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
arecord: main:590: audio open error: No such file or directory
aplay: playback:2208: read error

```

---

### Post by sendblink23 on 2009-04-28
> **dimis80 said:**
> I need help on this too. :confused:

I have in my desktop an Intel sound card and when I open TVTIME i can only see but not hear any sound from the programs playing.

Can you please guide me to fix this issue???
This is the only problem that I have...

thanks!


If you have read all my *Info on this (my Thread) its exactly your same issue.. its only TVTIME not producing any sound (I do not have any other problems :P)

---

### Post by dimis80 on 2009-04-28
> **sendblink23 said:**
> If you have read all my *Info on this (my Thread) its exactly your same issue.. its only TVTIME not producing any sound (I do not have any other problems :P)

Yes but the last lines that solved the problem couldn't help.
It gave me the errors you posted... :(

---

### Post by sendblink23 on 2009-04-28
> **dimis80 said:**
> Yes but the last lines that solved the problem couldn't help.
It gave me the errors you posted... :(

They didn't solve mines Either, I have not mentioned or marked my thread Solved.. so the issue still persist

You just got confused with my last post

---

### Post by dimis80 on 2009-04-29
Please if anyone has any idea... or suggest another working program for TV in Ubuntu!

Thanks!
:)

---

### Post by shane2peru on 2009-05-29
> **ultimate user said:**
> I also use tv time and had some trouble with the sound.

Try copy and paste this in the terminal when tv time is running
```
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &
```
If you then get sound, open gedit and paste this in it
```
#!/bin/sh
echo
tvtime  &

sleep 4

echo
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &

```
save it with name of your choice to your desktop, click on it and choose "run" to see TV
This worked for me!!!!  Thanks!  It didn't seem to matter what I set the hw to 1,0   2,0    1,1    2,1   all of them worked.  When I did it straight on the command line it distorted the sound and sounded like the chipmunks and clipped in and out as it was going.  When I put it in the script form it sounded good, although there was a few moments delay.  Do you by any chance know how to capture the video?  I have tried cat /dev/video0 > file.mpg and it creates a large file, but nothing seems to be able to play it.  I found out I have an analog card, and it doesn't encode it on the fly and therefore that command doesn't seem to work.  Any help on this would be appreciated.  Thanks!

Shane

---


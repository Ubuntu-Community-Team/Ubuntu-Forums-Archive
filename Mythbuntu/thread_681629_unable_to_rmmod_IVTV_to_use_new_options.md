---
title: "unable to rmmod IVTV to use new options"
date: 2008-01-29
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-01-29
Hello all

I am getting tons of errors in dmesg like this:

[958989.631007] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[958989.631011] ivtv0: Cause: the application is not reading fast enough.
[959650.647559] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[959650.647563] ivtv0: Cause: the application is not reading fast enough.

I have read that if I add IVTV options to the /etc/mythtv/modules/ivtv file this should get solved. Well, in ubuntu that file doesn't exist. So the next logical location would be were other module options get loaded which to the best of my knowledge /etc/modprobe.conf
So I make that file look like this:
alias char-major-61 lirc_serial
options lirc_serial irq=3 io=0x2f8
install lirc_serial /bin/setserial /dev/ttyS0 uart none ;\
/sbin/modprobe --ignore-install lirc_serial
options ivtv yuv_buffers=32 mpg_buffers=16 vbi_buffers=16 pcm_buffers=16 dec_osd_buffers=2

then when I try to rmmod the IVTV module and reload it, it says it's in use. How can I solve this? I don't want to restart my machine, it transcoding video and doing other things. It's been up for a long time.
I follow the steps on the PVR-350 Mythtv wiki that says this:
update-modules && rmmod ivtv && modprobe ivtv

but I get back an error telling me that the IVTV module is in use. I have tried stoppping mythbackend but to no avail. Can anyone help please?

---

### Post by jeffus_il on 2008-01-29
lsmod output shows you the names of the modules use ivtv , you have to rmmod them first before you rmmod ivtv.

---

### Post by stdPikachu on 2008-01-29
You'll also need to kill/stop any apps - i.e. mythbackend - that are accessing the TV card in order to free the module. For the same reason you can't "rmmod nvidia" whilst X is running, it'd cause things to crash.

`sudo /etc/init.d/mythbacked stop && sudo rmmod ivtv` should work for you.

---

### Post by dannyboy79 on 2008-01-29
> **jeffus_il said:**
> lsmod output shows you the names of the modules use ivtv , you have to rmmod them first before you rmmod ivtv.

lsmod shows a whole crap load of stuff related to ivtv, this is what lsmod | grep ivtv shows:
ivtv                  134544  1
i2c_algo_bit            8712  3 cx88xx,bttv,ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  3 cx88xx,bttv,ivtv
i2c_core               22656  13 cx88xx,bttv,lirc_i2c,nvidia,i2c_ec,msp3400,saa7                                        127,saa7115,tuner,ivtv,i2c_viapro,i2c_algo_bit,tveeprom
videodev               28160  4 cx8800,cx88xx,bttv,ivtv
v4l2_common            25216  8 cx8800,bttv,msp3400,saa7115,tuner,ivtv,cx2341x,v                                        ideodev
v4l1_compat            15236  3 cx8800,ivtv,videodev

the wiki doesn't say anything about having to rmmod all that stuff? if I rmmod it all, I would obviously have to modprobe all those again also right?

and to the guy who told me to stop mythbackend, I did that if you would have read my post but thanks anyway.

---

### Post by jeffus_il on 2008-01-29
You wouldn't have to reload them all, modprobe knows how to load the dependencies of a module as well, maybe you can reboot by now?!

---

### Post by dannyboy79 on 2008-01-29
well I finally was done transcoding a bunch of stuff so I issued a sudo shutdown -r now (i was ssh'd in from work) and I see some errors in dmesg relating to the ivtv options that I added to the /etc/modprobe.conf so I assuming that was the correct file to add the ivtv options to. Here's what the error is:
ivtv: Unknown parameter `yuv_buffers'

so the yuv_buffers isn't a valid option. I will try to record a show and see if any more buffer full errors come and let everyone know. In the meantime, is it even important if I have the option yuv_buffers set?

well, I just noticed that the PVR-350 isn't even working. when I lsmod | grep ivtv, it's not even loaded. Obviously the yuv_buffers error is preventing the ivtv module from being loaded. Now what?

---

### Post by dannyboy79 on 2008-01-29
I removed the yuv_buffers from /etc/modprobe.conf and now I get this error in dmesg:
ivtv: Unknown parameter `mpg_buffers'
So something isn't right here. Can someone please help? Where do I add the options for ivtv module. I read the ivtv module.txt located in /usr/share/doc/ivtv-utils/ and it actually states that all the options I am trying to use are valid options so I must not be writing the line correct but all I am doing is following the Mythtv WIKI for PVR-350.

Please help

---

### Post by dannyboy79 on 2008-01-30
bump

please, can anyone help me make ivtv use the buffer parameters?

---

### Post by jeffus_il on 2008-01-30
I guess we are not acquainted well with the ivtv module , sorry, I see you may find a solution from your posts in another forum. If you find a solution could you post it here? Thanks,
Jeff

---

### Post by stdPikachu on 2008-01-30
Well, if it's saying that mpg_buffers is an incorrect parameter, my guess would be it's an incorrect parameter.

Perusing the ivtv blurbs, I see a few people using enc_mpg_buffers. When I used to use ivtv its modprobe options changed faster than the phases of the moon, so you'll need to make sure you're using the right parameters for the version you're using.

[http://www.mythtvtalk.com/forum/archive/o_t/t_5162/all_encoder_mpeg_stream_buffers_are_full._dropping_data.html](http://www.mythtvtalk.com/forum/archive/o_t/t_5162/all_encoder_mpeg_stream_buffers_are_full._dropping_data.html)

---

### Post by superm1 on 2008-01-30
If you are unsure exactly whether the parameter exists for it, you can always run strings on the kernel module.

---

### Post by dannyboy79 on 2008-01-30
> **superm1 said:**
> If you are unsure exactly whether the parameter exists for it, you can always run strings on the kernel module.

according to the module.txt located in /usr/share/doc/ivtv-utils/ I am using the correct parameters. I would appreciate it very much if you could explain further what your statement above means. thank you for any help you can provide.

i really would like my recordings to stop having dropped frames. it's a C2D 4300 with 2gb of DDRII RAM which should be plenty of power to record 1 show. granted I am also doing transcoding with dvdrip, using bittornado for 2 torrents at the same time but I would think that would matter.

---

### Post by superm1 on 2008-01-30
Here is what strings tells me (on a hardy box).  This might be a little different on your gutsy box.

```
supermario@portablemario:/lib/modules/2.6.24-5-generic/kernel/drivers/media/video/ivtv$ strings ivtv.ko | grep parm=
parm=ivtv_first_minor:Set minor assigned to first card
parm=newi2c:Use new I2C implementation
parm=dec_vbi_buffers:Decoder VBI buffers (in kB)
parm=dec_yuv_buffers:Decoder YUV buffers (in MB)
parm=dec_mpg_buffers:Decoder MPG buffers (in MB)
parm=enc_pcm_buffers:Encoder PCM buffers (in kB)
parm=enc_vbi_buffers:Encoder VBI Buffers (in MB)
parm=enc_yuv_buffers:Encoder YUV Buffers (in MB)
parm=enc_mpg_buffers:Encoder MPG Buffers (in MB)
parm=ivtv_yuv_threshold:If ivtv_yuv_mode is 2 (auto) then playback content as
parm=ivtv_yuv_mode:Specify the yuv playback mode:
parm=ivtv_pci_latency:Change the PCI latency to 64 if lower: 0 = No, 1 = Yes,
parm=debug:Debug level (bitmask). Default: 0
parm=ntsc:Set NTSC standard: M, J, K
parm=secam:Set SECAM standard: B, G, H, D, K, L, LC
parm=pal:Set PAL standard: B, G, H, D, K, I, M, N, Nc, 60
parm=cardtype:Only use this option if your card is not detected properly.
parm=radio:Enable or disable the radio. Use only if autodetection
parm=tuner:Tuner type selection,

```

The item listed right after parm= is a supported parameter.

---

### Post by stdPikachu on 2008-01-30
strings is a program that examines binary files for text strings and outputs them to the console; running:
strings `locate ivtv.ko` | less
should run strings against the ivtv module (sorry, can't remember the exact path under /lib/modules where ivtv.ko lives). You should see a bunch of stuff in there, much of which will be the kernel parameters for that module.
Browsing about it seems that alot ofthe docs pertaining to IVTV parameters is highly contradictory, and I couldn't find any specific list under the IVTV wiki.

Edit: darn, superm1 beat me to it. Looks like the parameter you're looking for is enc_mpg_buffers= rather than just mpg_buffers=

---

### Post by dannyboy79 on 2008-01-30
> **superm1 said:**
> Here is what strings tells me (on a hardy box).  This might be a little different on your gutsy box.

```
supermario@portablemario:/lib/modules/2.6.24-5-generic/kernel/drivers/media/video/ivtv$ strings ivtv.ko | grep parm=
parm=ivtv_first_minor:Set minor assigned to first card
parm=newi2c:Use new I2C implementation
parm=dec_vbi_buffers:Decoder VBI buffers (in kB)
parm=dec_yuv_buffers:Decoder YUV buffers (in MB)
parm=dec_mpg_buffers:Decoder MPG buffers (in MB)
parm=enc_pcm_buffers:Encoder PCM buffers (in kB)
parm=enc_vbi_buffers:Encoder VBI Buffers (in MB)
parm=enc_yuv_buffers:Encoder YUV Buffers (in MB)
parm=enc_mpg_buffers:Encoder MPG Buffers (in MB)
parm=ivtv_yuv_threshold:If ivtv_yuv_mode is 2 (auto) then playback content as
parm=ivtv_yuv_mode:Specify the yuv playback mode:
parm=ivtv_pci_latency:Change the PCI latency to 64 if lower: 0 = No, 1 = Yes,
parm=debug:Debug level (bitmask). Default: 0
parm=ntsc:Set NTSC standard: M, J, K
parm=secam:Set SECAM standard: B, G, H, D, K, L, LC
parm=pal:Set PAL standard: B, G, H, D, K, I, M, N, Nc, 60
parm=cardtype:Only use this option if your card is not detected properly.
parm=radio:Enable or disable the radio. Use only if autodetection
parm=tuner:Tuner type selection,

```

The item listed right after parm= is a supported parameter.

see I knew you the man superm1! thanks. who do I contact to have the Mythtv PVR-350 WIKI updated or added to, if you are aware of who that is? also, the /usr/share/doc/ivtv-utils/modules.txt file is wrong as well.

so instead of this:
options ivtv yuv_buffers=32 mpg_buffers=16 vbi_buffers=16 pcm_buffers=16 dec_osd_buffers=2

it SHOULD be this:
options ivtv enc_yuv_buffers=32 enc_mpg_buffers=16 enc_vbi_buffers=16 enc_pcm_buffers=16


the must have gotten rid of the dec_osd_buffers option? I'll give this a try and hopefully it'll solve my issues. I'll post back.

Seperate issue. In dmesg, I am seeing this: 
ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   18.812991] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   18.873005] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   19.039205] ivtv0: Encoder revision: 0x02050032
[   19.039209] **ivtv0: Recommended firmware version is 0x02060039**.
[   19.047230] ivtv0: Decoder revision: 0x02020023

Does this mean I need to install different firmware to get the best use out of my PVR-350? Any more help would be greatly appreciated. Then if so, how would i do that? i already downloaded the firmware from the ivtv website for cx23415 based cards ([http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)).

---

### Post by dannyboy79 on 2008-01-30
well I'll wait and see if that solves the dmesg buffer full errors. at least with the correct parameters the ivtv module is loading. BUT here's the weird part, I was also getting buffer errors on Gutsy Mythbuntu which has a PVR-500 so I tried adding the same parameters and values and this is what happened when I restarted the machine.

[   30.554595] ivtv:  ==================== START INIT IVTV ====================
[   30.554600] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   30.554693] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   31.318422] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3364109536 bytes)
[   31.531184] ivtv0: Encoder revision: 0x02060039
[   31.598541] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   31.634250] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   31.634539] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   31.677700] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   35.361122] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   35.732909] ivtv0: Registered device video0 for encoder MPEG (16 MB)
[   35.733878] ivtv0: Registered device video32 for encoder YUV (32 MB)
[   35.737420] ivtv0: Registered device vbi0 for encoder VBI (16 MB)
[   35.738879] ivtv0: Registered device video24 for encoder PCM audio (16 MB)
[   35.945108] ivtv0: Registered device radio0 for encoder radio
[   35.970272] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   35.970333] ivtv:  ======================  NEXT CARD  ======================
[   35.970339] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   36.618344] ivtv1: loaded v4l-cx2341x-enc.fw firmware (3352285808 bytes)
[   36.833516] ivtv1: Encoder revision: 0x02060039
[   36.839634] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   36.856403] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   40.500679] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   40.575778] ivtv1: Correcting tveeprom data: no radio present on second unit
[   40.575782] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   40.975328] ivtv1: Registered device video1 for encoder MPEG (16 MB)
[B][   40.975776]  [<d0ab2a61>] ivtv_stream_alloc+0xa1/0x2f0 [ivtv]
[   40.975801]  [<d0ab2a61>] ivtv_stream_alloc+0xa1/0x2f0 [ivtv]
[   40.975848]  [<d0ab3665>] ivtv_streams_setup+0x1a5/0x430 [ivtv]
[   40.975892]  [<d0aa8838>] ivtv_probe+0x1068/0x1380 [ivtv]
[   40.976123]  [<d0aa730b>] module_start+0x5b/0xc0 [ivtv]
[   40.978028] ivtv1: Couldn't allocate buffers for encoder MPEG stream
[   40.978423] ivtv1: Error -12 setting up streams
[   40.978902] ivtv1: Error -12 on initialization
[   40.978915] ivtv: probe of 0000:03:09.0 failed with error -12[/B]
[   40.979817] ivtv:  ====================  END INIT IVTV  ====================
it's only erroring on the second card, ivtv0 works just fine. when I tried to start mythbackend, the tuners weren't showing up, weird hey? So I am trying to cut the values in half since there are 2 tuners. let me check and see what happens after I restart.

UPDATE: yeap that must have been it, now that I used half the values as I did for the PVR-350, both ivtv0 and ivtv1 are good to go and my tuners are there in mythweb. Hopefully I don't get any buffer full errors anymore. Thanks for the help.

---

### Post by superm1 on 2008-01-30
> **dannyboy79 said:**
> see I knew you the man superm1! thanks. who do I contact to have the Mythtv PVR-350 WIKI updated or added to, if you are aware of who that is? also, the /usr/share/doc/ivtv-utils/modules.txt file is wrong as well.

so instead of this:
options ivtv yuv_buffers=32 mpg_buffers=16 vbi_buffers=16 pcm_buffers=16 dec_osd_buffers=2

it SHOULD be this:
options ivtv enc_yuv_buffers=32 enc_mpg_buffers=16 enc_vbi_buffers=16 enc_pcm_buffers=16


the must have gotten rid of the dec_osd_buffers option? I'll give this a try and hopefully it'll solve my issues. I'll post back.

Seperate issue. In dmesg, I am seeing this: 
ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   18.812991] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   18.873005] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   19.039205] ivtv0: Encoder revision: 0x02050032
[   19.039209] **ivtv0: Recommended firmware version is 0x02060039**.
[   19.047230] ivtv0: Decoder revision: 0x02020023

Does this mean I need to install different firmware to get the best use out of my PVR-350? Any more help would be greatly appreciated. Then if so, how would i do that? i already downloaded the firmware from the ivtv website for cx23415 based cards ([http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)).
You can update the wiki yourself.  Just log in to edit the page.  Also, please file a bug against ivtv-utils on launchpad about updating the text there.

Thanks!

---

### Post by dannyboy79 on 2008-01-30
> **superm1 said:**
> You can update the wiki yourself.  Just log in to edit the page.  Also, please file a bug against ivtv-utils on launchpad about updating the text there.

Thanks!

what about the firmware version that I bolded above? would that help anything if I used the version it says I should use? 

also, I created an account on the wiki and did add the info there.

---

### Post by dannyboy79 on 2008-01-31
Well I am still getting Buffer Full errors despite increasing the buffer size so I am not sure what else to do? I have DMA on and PCI Latency set to 176 on the hdd controllers. The machine has 2GB of DDRII RAM so it's can  be memory could it? It has 1 PVR-350. this is the master backend where the sql database resides and the location in which I do many other things.

Then the other machine only has 256 DDR RAM and a PVR-500. I get the buffer full errors on that machine also. This is the slave backend and it keeps it's recordings on it's own drive (no nfs share cause I couldn't get it to work.)

---

### Post by dannyboy79 on 2008-02-01
bump

still having the issue. can anyone speculate as to why?

---

### Post by ian dobson on 2008-02-02
Hi,

Maybe try putting your PVR into a different PCI slot.

I'm runing a PVR 500 on a Q6600 with 2Gb ram and the system doesn't seem to have any problems with:-
1) Recording 2 programs at the same time
2) Recording 2 programs at the same time and resyncing my RAID5 array at the same time.

What harddisks/controller are you using. What write performance can you get out of your drive? Use bonnie++ to test the throughput.

Regards
Ian Dobson

---

### Post by dannyboy79 on 2008-02-23
i have tested the disks using hdparm and they seem fine. what command would I run using bonnie++ to check my disk that holds the recordings? or do I also need to check the disk that the mysql server is on? they are on the same system but different hard drives. my pci slotys are full so I cant try another slot. plus, I don't see how that would change anything, arent' all pci slots on the same bus anyway? I am getting really iritated by this. this happens when I have nothing else going on on the machine besides xorg which does take a lot of memory but I have 2GB of it. my free -m shows this now:
            total       used       free     shared    buffers     cached
Mem:          2027       1912        114          0        151       1186
-/+ buffers/cache:        574       1453
Swap:         1498         14       1483

but that's with 2 torrents going, firefox open, conky, and gaim running, and a terminal session. i just did top and it appers that bittornado uses a lot fo memory along with xorg.

---

### Post by ian dobson on 2008-02-23
OK,
y y
Here are the results for my bonnie++ benchmarks while recording 2 TV programs at the same time. Hardware:-

Intel Q6600, 2Gb Ram
Raid 5 Array (4x500Gb HD) MDADM

Commandline parameters used:-
bonnie++ -r 2000 -u xmail

where -r is the amount of memory installed and -u is the user to run as.

Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
alpha2           4G 47392  63 59109  15 30774   5 42031  56 74651   6 146.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
alpha2,4G,47392,63,59109,15,30774,5,42031,56,74651,6,146.9,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++


So I have a block write of about 59Mb second and read of about 74Mb.
More than enough for several SD streams.

Regards
Ian Dobson

---


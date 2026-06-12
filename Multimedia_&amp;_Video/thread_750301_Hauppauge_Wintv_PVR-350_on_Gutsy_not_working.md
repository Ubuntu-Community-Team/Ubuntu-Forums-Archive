---
title: "Hauppauge Wintv PVR-350 on Gutsy not working"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by zazake on 2008-04-09
Hello to all

I've had the Hauppauge Wintv PVR-350 card for several months now, and i've spent a lot of time and effort trying to get it to work, but in vain, although I've now read many many pages on the subject.
When I do :
mplayer /dev/video0
or
ivtv-radio -f 100.0
I get nothing. Not even an error message, and no data if I try to record to a file.

This is what I get in dmesg :

```
[   53.871530] ivtv:  ==================== START INIT IVTV ====================
[   53.871534] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   53.871584] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   53.873107] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[   53.877412] sky2 eth1: enabling interface
[   53.882972] usbcore: registered new interface driver xpad
[   53.882975] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   53.908206] nvidia: module license 'NVIDIA' taints kernel.
[   54.213932] NET: Registered protocol family 17
[   54.535129] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4158837568 bytes)
[   54.555092] ivtv0: loaded v4l-cx2341x-dec.fw firmware (4158837592 bytes)
[   54.775122] ivtv0: Encoder revision: 0x02050032
[   54.775124] ivtv0: Recommended firmware version is 0x02060039.
[   54.783131] ivtv0: Decoder revision: 0x02020023
[   54.839846] tveeprom 0-0050: Hauppauge model 48139, rev K257, serial# 8577193
[   54.839849] tveeprom 0-0050: tuner model is Philips FM1216 ME MK3 (idx 57, type 38)
[   54.839851] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   54.839853] tveeprom 0-0050: audio processor is MSP4418 (idx 25)
[   54.839855] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   54.839857] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   54.839859] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   54.856913] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   54.856927] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   54.860099] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   54.931587] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   54.952573] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
[   54.952576] msp3400 0-0040: MSP4418G-B3 supports nicam and radio, mode is autodetect and autoselect
[   54.953908] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   54.957552] ivtv0: i2c addr 0x21 not found for command 0x4008646f!
[   55.197970] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   55.198087] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   55.198212] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   55.198256] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   55.198417] ivtv0: Registered device radio0 for encoder radio
[   55.198431] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   55.198461] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   55.198669] ivtv0: Registered device vbi16 for decoder VOUT
[   55.198683] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   55.264274] ivtv0: loaded v4l-cx2341x-init.mpg firmware (4158837960 bytes)
[   55.405873] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   55.405889] ivtv:  ====================  END INIT IVTV  ====================
[   55.405988] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   55.405997] PCI: Setting latency timer of device 0000:01:00.0 to 64


```And every time I try to use tv or radio I get the same message (with different numbers) :

[```
 2661.733873] ivtv0: i2c addr 0x21 not found for command 0xc0cc5605!
[ 2689.693690] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2689.693696] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2689.693700] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2689.693704] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2695.922615] ivtv0: i2c addr 0x21 not found for command 0xc0cc5605!
[ 2726.073749] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2726.073756] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2726.073760] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2726.073763] ivtv0: i2c addr 0x21 not found for command 0xc0445624!
[ 2726.074638] ivtv0: i2c addr 0x21 not found for command 0xc0cc5604!
[ 2726.075011] ivtv0: i2c addr 0x21 not found for command 0xc014563b!

```

I found no information on this error except that this might be caused by a conflict with driver nxt200x for the AVerMedia AVerTVHD MCE A180. But I don't have that card or driver. So now I'm getting quite desperate, and I wonder if someone has an idea.

---

### Post by wolfen69 on 2008-04-09
I have a Hauppauge pvr card running on my gutsy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv: ```
cat /dev/video0 > /tmp/name_of_file.mpg
```
it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by zazake on 2008-04-09
Thanks for your quick reply. Unfortunately it doesn't work with vlc either (no image or sign of activity). And when I do 
```
cat /dev/video0 > /tmp/name_of_file.mpg
```
I just get an empty file.
I've installed ivtv-utils and played around with the various options of ivtv-tune and  v4l2-ctl but without result.
The remote looks cool. I'll try it if I ever get the card working :)

---

### Post by wolfen69 on 2008-04-09
if you havnt already, try this troubleshooting guide: [https://help.ubuntu.com/community/Install_IVTV_Troubleshooting](https://help.ubuntu.com/community/Install_IVTV_Troubleshooting)

---

### Post by zazake on 2008-04-09
I had not seen that one, but I tried what they proposed and still no result.
Just in case, this is what I get if I do :
 vlc pvr:// pvr-device="/dev/video0" -vv
(and then Ctrl-C to stop)
```

VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/isabelle/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/isabelle/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 3079592848 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 3071200144 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 3062807440 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 3054414736 (interface) created at priority 0 (interface/interface.c:231)
[00000281] main playlist debug: adding playlist item `pvr-device=/dev/video0' ( pvr-device=/dev/video0 )
[00000281] main playlist debug: adding playlist item `pvr://' ( pvr:// )
[00000287] main interface debug: looking for interface module: 5 candidates
[00000287] main interface debug: using interface module "wxwidgets"
[00000287] main interface debug: thread 3027200912 (manager) created at priority 0 (interface/interface.c:216)
[00000287] wxwidgets interface debug: Using last windows config '(-1,0,0,1680,1050)(0,904,385,460,84)(6,0,0,-1,150)'
[00000287] wxwidgets interface debug: id=0 p=(904,385) s=(460,84)
[00000287] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
[00000281] main playlist debug: nothing requested, starting
[00000281] main playlist debug: creating new input thread
[00000290] main input debug: waiting for thread completion
[00000290] main input debug: creating statistics handler
[00000290] main input debug: `pvr://' gives access `pvr' demux `' path `'
[00000290] main input debug: creating demux: access='pvr' demux='' path=''
[00000292] main demuxer debug: looking for access_demux module: 0 candidates
[00000292] main demuxer warning: no access_demux module matched "pvr"
[00000290] main input debug: creating access 'pvr' path=''
[00000293] main access debug: looking for access2 module: 6 candidates
[00000293] pvr access debug: Using video device: /dev/video0.
[00000293] pvr access debug: ivtv driver version 01.00.00
[00000293] pvr access debug: this driver uses the v4l2 API
[00000293] main access debug: using access2 module "pvr"
[00000295] main private debug: pre-buffering...
[00000290] main input debug: thread 3001486224 (input) created at priority 0 (input/input.c:265)
signal 2 received, terminating vlc - do it again in case it gets stuck
user insisted too much, dying badly
Abandon (core dumped)
```

---


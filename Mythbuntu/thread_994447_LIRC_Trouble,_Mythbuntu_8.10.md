---
title: "LIRC Trouble, Mythbuntu 8.10"
date: 2008-11-26
forum: Mythbuntu
---

### Post by arindrel on 2008-11-26
Hi, I've just installed Mythbuntu 8.10 on a new PC (2Ghz AMD CPU, 2GB Ram, GeForce7 GFX using nvidia 'restricted' driver)  All seems to work fine .. My capture card is the duel channel Hauppauge WinTV Nova-TD 500 PCI .. this works fine and i can capture video perfectly :)  ... the only problem i have is with getting the remote to work (its the grey A415-HPG-WE-A one)

My Linux experience is approximately zero, but ive tried to read round the subject a bit before posting, so apologies if the commands im using/posting are incorrectly used.  

Mythbuntu has the latest LIRC package installed and the LIRCD deamon is running (Well its shows up in \dev\lircd)  ... im not seeing \dev\lirc though (thats the kernel module right?) ... ive added ivtv and the lirc driver to my /etc/modules file

```
rich@mythtv01:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
fuse
lp
sbp2
ivtv
lirc_i2c
```

and these seem to be running

```
rich@mythtv01:~$ cat /proc/modules | grep lirc
lirc_i2c 17156 0 - Live 0xf8eee000
lirc_dev 20020 1 lirc_i2c, Live 0xf8eb8000
i2c_core 31892 15 cx88xx,bttv,lirc_i2c,ivtv,i2c_algo_bit,v4l2_common,tveeprom,nvidia,dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070, Live 0xf8abc000
```

but im not seeing a device /dev/lirc  or anything similar ... nor has the lirc device shown up in input devices

```
rich@mythtv01:~$ sudo cat /proc/bus/input/devices
[sudo] password for rich: 
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:04.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-5/2-5:1.0/input/input1
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=04b3 Product=3025 Version=0110
N: Name="LITE-ON Technology USB NetVista Full Width Keyboard."
P: Phys=usb-0000:00:02.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-5/1-5:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

rich@mythtv01:~$ 
```
i know it isnt relivent but ive included my lircd.conf file incase this is needed.
```

rich@mythtv01:~$ cat /etc/lircd.conf
begin remote
  name            Hauppauge_350
  bits            13
  flags           RC5|CONST_LENGTH
  eps             30
  aeps            100
  one             969   811
  zero            969   811
  gap             114605
  toggle_bit      2
  plead           1097

  begin codes
       Go              0x00000000000017BB
       Power           0x00000000000017BD
       TV              0x000000000000179C
       Videos          0x0000000000001798
       Music           0x0000000000001799
       Pictures        0x000000000000179A
       Guide           0x000000000000179B
       Radio           0x000000000000178C
       Up              0x0000000000001794
       Left            0x0000000000001796
       Right           0x0000000000001797
       Down            0x0000000000001795
       OK              0x00000000000017A5
       Back/Exit       0x000000000000179F
       Menu/i          0x000000000000178D
       Vol+            0x0000000000001790
       Vol-            0x0000000000001791
       Prev.Ch         0x0000000000001792
       Mute            0x000000000000178F
       Ch+             0x00000000000017A0
       Ch-             0x00000000000017A1
       Record          0x00000000000017B7
       Stop            0x00000000000017B6
       Rewind          0x00000000000017B2
       Play            0x00000000000017B5
       Forward         0x00000000000017B4
       Replay/SkipBackward 0x00000000000017A4
       Pause           0x00000000000017B0
       SkipForward     0x000000000000179E
       1               0x0000000000001781
       2               0x0000000000001782
       3               0x0000000000001783
       4               0x0000000000001784
       5               0x0000000000001785
       6               0x0000000000001786
       7               0x0000000000001787
       8               0x0000000000001788
       9               0x0000000000001789
       Asterix         0x000000000000178A
       0               0x0000000000001780
       #               0x000000000000178E
       Red             0x000000000000178B
       Green           0x00000000000017AE
       Yellow          0x00000000000017B8
       Blue            0x00000000000017A9

  end codes

end remote 
rich@mythtv01:~$ 

```


Ive been banging my head against the wall on this one for a few weeks now and the family is getting a bit annoyed about having to use a keyboard to record TV shows :S .... any pointers or advice would be great

Thanks in advance
Rich

---

### Post by trilobita on 2008-11-27
Hi,

I've got the same problem i think. Nothing shows up under 

cat /proc/bus/input/devices

and 

ls -lah /dev/input/by-path/

gives me

```
total 0
drwxr-xr-x 2 root root 140 2008-11-27 10:58 .
drwxr-xr-x 4 root root 280 2008-11-27 10:58 ..
lrwxrwxrwx 1 root root   9 2008-11-27 10:58 pci-0000:00:03.0-usb-0:1:1.0-event-mouse -> ../event1
lrwxrwxrwx 1 root root   9 2008-11-27 10:58 pci-0000:00:03.0-usb-0:1:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2008-11-27 10:58 pci-0000:00:03.1-usb-0:1.1:1.0-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2008-11-27 10:58 pci-0000:00:03.1-usb-0:1.1:1.1-event- -> ../event3
lrwxrwxrwx 1 root root   9 2008-11-27 10:58 platform-pcspkr-event-spkr -> ../event6

```

again i've got an Hauppauge WinTV Nova-TD-500 pci on Mythbuntu 8.10 on a P4 (Asus Pundit) and can view tv ok.

I've tried just about everything suggested on this forum and at the relevant mythtv and linuxtv pages, but most of it comes to finding which event the ir is on, and i don't seem to have one :(

---

### Post by jMon54 on 2008-11-29
I had lots of failure getting my remote to work after upgrading from 8.04 to 8.10 until I used "mythbuntu-lirc-generator' from konsole.

---

### Post by trilobita on 2008-11-29
> **jMon54 said:**
> I had lots of failure getting my remote to work after upgrading from 8.04 to 8.10 until I used "mythbuntu-lirc-generator' from konsole.

But IIRC you need to select and event-ir in mythbuntu-lirc-generator, and the problem is that we don't have an event-ir to select. 

I think what we need is some way to make the ir receiver show up as an event

---

### Post by GlenFord on 2009-01-07
Anyone made any progress with this?  Again I have the same TD-500, but see no detection of the onboard IR Receiver, nothing is logged in messages, no event device is assigned.

---

### Post by scary_jeff on 2009-01-20
I'm having the same problem. I'm in the exact same situation as the thread starter. I tried all the steps in the last post here: [http://ubuntuforums.org/showthread.php?t=985311](http://ubuntuforums.org/showthread.php?t=985311) but it didn't seem to have any effect.
The only additional bit of information I have over the original post is that dmesg | grep lirc results in:

[   14.050839] lirc_dev: IR Remote Control driver registered, major 61 

This only happened after editing /etc/modules. Should my remote appear in /proc/bus/input/devices just from installing lirc and restarting? Should dmesg have some message relating to my specific remote?

Cheers

---

### Post by GlenFord on 2009-01-21
Ok,  I seem to have gotten somewhere.

I downloaded the latest v4l-dvb code from their repo (see instructions here [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)) and then the latest firmware ([http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw)) into [FONT="Courier New"]/lib/firmware[/FONT].

I still didn't have a working IR, however after poking around I found that [FONT="Courier New"]linux/drivers/media/dvb/dvb-usb/dib0700_devices.c[/FONT] seemed to be lacking references to rc_ elements for the TD-500 that others had.  So I copied from the structure above, here is my diff.


```

root@pvr:~/dvb/v4l-dvb# hg diff
diff -r f4d7d0b84940 linux/drivers/media/dvb/dvb-usb/dib0700_devices.c
--- a/linux/drivers/media/dvb/dvb-usb/dib0700_devices.c	Sun Jan 18 10:55:38 2009 +0000
+++ b/linux/drivers/media/dvb/dvb-usb/dib0700_devices.c	Wed Jan 21 19:41:36 2009 +0000
@@ -1683,7 +1683,13 @@
 				{ &dib0700_usb_id_table[43], NULL },
 				{ NULL },
 			}
-		}
+		},
+
+		.rc_interval      = DEFAULT_RC_INTERVAL,
+		.rc_key_map       = dib0700_rc_keys,
+		.rc_key_map_size  = ARRAY_SIZE(dib0700_rc_keys),
+		.rc_query         = dib0700_rc_query
+
 	}, { DIB0700_DEFAULT_DEVICE_PROPERTIES,
 
 		.num_adapters = 1,


```

I did a [FONT="Courier New"]make[/FONT], then [FONT="Courier New"]make install[/FONT]

On a reboot I then saw the following in dmesg
```

[   14.317130] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb7/7-1/input/input6

```

My remote then sort of worked, arrows worked and the power button brought up the shutdown, but nothing else.  I also noticed that lircd wasn't running, that in [FONT="Courier New"]syslog[/FONT] it had failed to open [FONT="Courier New"]/dev/lirc0[/FONT].

I edited the licrd conf to use [FONT="Courier New"]/dev/input/event6[/FONT], and then got an error in syslog about not able to get exclusive access to the device, and no change in remote behaviour.

I noticed then that if I did a [FONT="Courier New"]ps -deaf | grep event6[/FONT] that a hal process was running with that device.

After some searching on the web found that another IR Remote was having problems with hal capturing the device before lircd, and copied their solution for this card.

I created a file ([FONT="Courier New"]/usr/share/hal/fdi/preprobe/20thirdparty/lirc_td500.fdi[/FONT]) with the following contents ..

```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>

```

Now HAL will ignore the remote, and all the buttons work :)

I am still grappling with a couple of other issues, but now have working remote.

---

### Post by scary_jeff on 2009-01-22
Great work GlenFord! Thankyou for coming back with your solution.

I'll try this out right now and post the results.

---

### Post by GlenFord on 2009-01-22
Hi, I posted my change to the v4l-dvb mailing list, and someone else has already merged the same fix ([http://linuxtv.org/hg/~dheitmueller/dib0700-pbfixes/rev/cf6003290b09](http://linuxtv.org/hg/~dheitmueller/dib0700-pbfixes/rev/cf6003290b09)) and the request for it to go into the mainline has already happened, so you may not need to patch after all.

---

### Post by scary_jeff on 2009-01-22
Excellent, all working now.

The only problem I had was getting lircd to properly use the remote after I had an input device for it listed (good feature to have it as irremote instead of eventx). In the end I just apt-get remove --purge'd lirc, and reinstalled it. The configuration screen that lirc first-install shows allowed me to select the irremote input, and everything is now working properly!

Thanks again GlenFord! Another victory for UbuntuForums :D

---

### Post by effing on 2009-02-03
Awesome, GlenFord, worked perfectly. After I was able to see the event-number (which was 7 for me) with 

dmesg | grep lirc

I got back to the mythTV control center and made all the configuration there:

RC: Hauppauge Nova-T 500
driver: devinput
module:
config: lircd.con.hauppauge_nova500
device: /dev/input/event7

Now Im gonig to find out in detail if all buttons work.

Once again, thanks a lot!

---

### Post by scary_jeff on 2009-02-07
Wow, that was annoying. Some update broke my remote :(

The solution was to download the latest v4l-dvb source code, compile without modifying (GlennFord's fix is now in there anyway), then install. I have no idea which update breaks it, but hopefuly this solution will be helpful to someone!

---

### Post by JoeFlennigan on 2009-03-26
Gonna try the souloution too and will post my success.

Thanks GlenFord!

---

### Post by scary_jeff on 2009-04-18
> **scary_jeff said:**
> Wow, that was annoying. Some update broke my remote :(

The solution was to download the latest v4l-dvb source code, compile without modifying (GlennFord's fix is now in there anyway), then install. I have no idea which update breaks it, but hopefuly this solution will be helpful to someone!

This happened again today. What have I done wrong that causes my remote to sometimes just stop being detected after receiving updates from Ubuntu? Perhaps I just have to live with this problem? I'm tempted to just turn updates off, but I could then miss an important security update...

---


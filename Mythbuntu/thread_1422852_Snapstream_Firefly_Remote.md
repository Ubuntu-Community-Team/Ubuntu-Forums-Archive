---
title: "Snapstream Firefly Remote"
date: 2010-03-05
forum: Mythbuntu
---

### Post by mrob on 2010-03-05
I'm having issues with my new Firefly remote.  The receiver is being detected, but the lirc_atiusb driver doesn't appear to be detecting any button presses.  I've read much on issues others have seen with the remote, including:

[http://ubuntuforums.org/showthread.php?t=1162085](http://ubuntuforums.org/showthread.php?t=1162085)
[http://ubuntuforums.org/showthread.php?t=884972](http://ubuntuforums.org/showthread.php?t=884972)
[http://www.mythtv.org/wiki/Snapstream_Firefly](http://www.mythtv.org/wiki/Snapstream_Firefly)
[https://bugs.launchpad.net/mythbuntu/+bug/176613/comments/6](https://bugs.launchpad.net/mythbuntu/+bug/176613/comments/6)

My problem doesn't seem to the same that others were having.  For starters, I'm running Mythbuntu 9.04.  I've corrected all of the lirc config files based on the above links.  I've also turned on debugging for the lirc_atiusb driver by placing the following line in /etc/modprob.d/lirc_atiusb.conf:

```
options lirc_atiusb unique=1 debug=1 mask=0x0100
```I get the following output in the syslog when lircd is started:

```

lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
lirc_atiusb: debug mode enabled: $Id: lirc_atiusb.c,v 1.69 2008/04/28 06:47:29 lirc Exp $
lirc_atiusb[6]: usb_remote_probe: dev:ffff8801009ae800, intf:ffff88013e521400, id:ffffffffa0bd91f0)
lirc_atiusb[6]: scanning remote_list...
lirc_atiusb[6]: remote type = 0
lirc_atiusb[6]: adding remote to list
lirc_atiusb[6]: processing endpoint 0
lirc_atiusb[6]: acceptable inbound endpoint (0x81) found (maxp=8 len=5)
lirc_atiusb[6]: adding ep=0x81 to list
lirc_atiusb[6]: processing endpoint 1
lirc_atiusb[6]: acceptable outbound endpoint (0x2) found
lirc_dev: lirc_register_plugin: sample_rate: 0
lirc_atiusb[6]: X10 WTI RF receiver on usb8:6
lirc_atiusb[6]: usb_remote_probe: initializing outbound ep
lirc_atiusb[6]: send called (0x8004)
lirc_atiusb[6]: usb out called
lirc_atiusb[6]: send complete (0x8004)
lirc_atiusb[6]: send called (0x8007)
lirc_atiusb[6]: usb out called
lirc_atiusb[6]: send complete (0x8007)
usbcore: registered new interface driver lirc_atiusb
lircd-0.8.4a[10241]: lircd(default) ready

```I configured the remote for channel 9, but I never see any syslog messages when I press any of the buttons.  I've also tried turning off the "unique" flag for the driver.

For kicks I tried irw and irrecord.  They didn't work, but I didn't expect them to work since the driver isn't seeing anything.  I've verified that /dev/lirc0 has proper permissions.  I've also confirmed that the remote/receiver does work on a Windows XP machine.

Any insight would be greatly appreciated.

Thanks,
-Mike

---

### Post by mrob on 2010-03-07
In my research, I see that this is the expected output for "lsmod | grep ati":

```

lirc_atiusb            21408  0
lirc_dev               18548  1 lirc_atiusb
usbcore               114896  3 lirc_atiusb,usbhid,uhci_hcd

```But I seem to be missing the "usbcore" association:

```

lirc_atiusb            26032  0 
lirc_dev               22088  1 lirc_atiusb

```Could this have anything to do with it? My syslog output (shown in the first post) does have a line with the text "usbcore" in it, FWIW:

```
usbcore: registered new interface driver lirc_atiusb
```

---

### Post by mrob on 2010-03-07
To answer my last question, I'm guessing that the usbcore module was compiled into the kernel.

---

### Post by Calmor on 2010-03-07
I'm running 8.10 x64 on my Myth server, and am running the Firefly.  I'm guessing you're on a newer system, since you're having issues after following those links.  

I don't know if it helps any, but my lsmod doesn't show anything related to lirc or ati... except the motherboard drivers I have, which are of no help.

I'd be glad to post my config files if you think they'll be of some help.

---

### Post by mrob on 2010-03-08
> **Calmor said:**
> I'd be glad to post my config files if you think they'll be of some help.

Thanks for the reply.  At this point, I'm pretty confident that the config files are correct, but thank you very much for the offer.

My understanding is that regardless of the /etc/lirc/lircd.conf file, that there should be output in the syslog for each button press when debug is turned on for the lirc_atiusb module.  In other words, the driver will log the raw data for each button press before looking it up in the lircd.conf file.  I was hoping to get some confirmation on that.

Is it possible that the events are getting intercepted by some other module/device?  I've confirmed that the ati_wonder module is blacklisted.

I've also seen mention of a userspace library (atilibusb?) that could be used in place of the module, but I haven't seen any details on how to use it in Mythbuntu.

---

### Post by Calmor on 2010-03-08
When I get back to the hotel this evening I'll check to see what configuration I'm running as far as modules.  I have read that the 8.10 and 9.04 and 9.10 setups are different, though, so I'm not sure how much I can help.  With no atiusb modules loaded, and no custom kernel builds, I'm honestly not sure what on my system is picking up the remote hits.

I'll look into it more this evening when I can ssh into my server.

---

### Post by mrob on 2010-03-08
> **Calmor said:**
> I'll look into it more this evening when I can ssh into my server.

Thanks...I really appreciate the time.  For completeness I should mention that my Mythbuntu install is stock...no custom kernel mods.

---

### Post by Calmor on 2010-03-08
What version are you running, just for my understanding?  9.04 / 9.10, 32-bit / 64-bit, etc..

---

### Post by mrob on 2010-03-08
> **Calmor said:**
> What version are you running, just for my understanding?  9.04 / 9.10, 32-bit / 64-bit, etc..

9.04 64-bit

---

### Post by Calmor on 2010-03-08
Hoping that won't be too different from my 8.10 64-bit setup then.  I'll let you know what I find later.  May be able to jump onto IRC this evening as well, but I can't tell what time I'll be out this evening.

---

### Post by mrob on 2010-03-08
> **Calmor said:**
> Hoping that won't be too different from my 8.10 64-bit setup then.  I'll let you know what I find later.  May be able to jump onto IRC this evening as well, but I can't tell what time I'll be out this evening.

Thanks.  I'll be standing by, furiously Googling for other possibilities.

---

### Post by Calmor on 2010-03-08
Apparently I am using the atilibusb driver.  I'll have to figure out how I'm doing that, but I wanted to get this posted asap... just got in from work.

My lirc hardware.conf file: ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
#REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE="/dev/lirc0"
#REMOTE_LIRCD_CONF="atilibusb"
REMOTE_LIRCD_ARGS="-r"  #added due to suggestion by Hulu Desktop, no effects noticed

#Chosen IR Transmitter
#TRANSMITTER="SAE8000"
#TRANSMITTER_MODULES="lirc_dev lirc_i2c lirc_pvr150"
#TRANSMITTER_DRIVER=""
#TRANSMITTER_DEVICE="/dev/lirc1"
#TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
#TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```

And my lircd.conf file:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(atilibusb) on Mon Nov 24 14:58:45 2008
#
# contributed by 
#
# brand:                       lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  Snapstream_X10_RF
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          147992
  min_repeat      5
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x812C
          MAXI                     0x01AC
          CLOSE                    0x5702
          CLOSE                    0xD782
          1                        0x620D
          1                        0xE28D
          2                        0x630E
          2                        0xE38E
          3                        0x640F
          3                        0xE48F
          4                        0x6510
          4                        0xE590
          5                        0x6611
          5                        0xE691
          6                        0x6712
          6                        0xE792
          7                        0x6813
          7                        0xE893
          8                        0x6914
          8                        0xE994
          9                        0x6A15
          9                        0xEA95
          0                        0x6C17
          0                        0xEC97
          BACK                     0x6B16
          BACK                     0xEB96
          ENT                      0x6D18
          ENT                      0xED98
          VOL+                     0x5E09
          VOL+                     0xDE89
          VOL-                     0x5D08
          VOL-                     0xDD88
          MUTE                     0x5F0A
          MUTE                     0xDF8A
          FIREFLY                  0x5500
          FIREFLY                  0xD580
          CH+                      0x600B
         CH+                      0xE08B
          CH-                      0x610C
          CH-                      0xE18C
          INFO                     0x832E
          INFO                     0x03AE
          OPTION                   0x842F
          OPTION                   0x04AF
          UP                       0x6F1A
          UP                       0xEF9A
          LEFT                     0x721D
          LEFT                     0xF29D
          DOWN                     0x7722
          DOWN                     0xF7A2
          RIGHT                    0x741F
          RIGHT                    0xF49F
          OK                       0x731E
          OK                       0xF39E
          MENU                     0x711C
          MENU                     0xF19C
          EXIT                     0x7520
          EXIT                     0xF5A0
          REC                      0x7C27
          REC                      0xFCA7
          PLAY                     0x7A25
          PLAY                     0xFAA5
          STOP                     0x7D28
          STOP                     0xFDA8
          REW                      0x7924
          REW                      0xF9A4
          FWD                      0x7B26
          FWD                      0xFBA6
          PREV                     0x802B
          PREV                     0x00AB
          PAUSE                    0x7E29
          PAUSE                    0xFEA9
          NEXT                     0x7F2A
          NEXT                     0xFFAA
          MUSIC                    0x5B06
          MUSIC                    0xDB86
          PHOTOS                   0x5A05
          PHOTOS                   0xDA85
          DVD                      0x5904
          DVD                      0xD984
          TV                       0x5803
          TV                       0xD883
          VIDEO                    0x5C07
          VIDEO                    0xDC87
          HELP                     0x5601
          HELP                     0xD681
          MOUSE                    0x822D
          MOUSE                    0x02AD
          A                        0x6E19
          A                        0xEE99
          B                        0x701B
          B                        0xF09B
          C                        0x7621
          C                        0xF6A1
          D                        0x7823
          D                        0xF8A3
      end codes

end remote

```

---

### Post by mrob on 2010-03-08
Thanks for the post...I'll try it out.

---

### Post by Calmor on 2010-03-08
I searched for atilib* on the system and didn't find any results, so maybe it's built in.  No results in dmesg or lsmod for it either.

I am running the remote on channel nine as well, from an earlier post I wrote.  If I remember right, the comments in my hardware.conf file reflected the fact that the other driver (that MythTV wants to use, I think) didn't work right.

This evening I'm on IRC FreeNode as calmor.  You can PM me there if you want to discuss.

---

### Post by mrob on 2010-03-08
I can't seem to prevent the lirc_atisub module from being loaded.  I've tried every method of blacklisting I could find.

I have to call it quits now, so I'll pick this up tomorrow.

Thanks again for the help.

---

### Post by Calmor on 2010-03-08
Looking through now that you mention blacklist problems, I have a file in /etc/modprobe.d called lirc-blacklist

Within it:

```

blacklist ati_remote
blacklist lirc_atiusb

```

Give that one a go and let me know if it helps...

I also have a file in /etc/modprobe.d called lirc that just says...

```

#File automatically generated upon lirc install
#Because a module had to be blacklisted. Don't
#Modify by hand, but rather via
#dpkg-reconfigure lirc

```

HTH

---

### Post by mrob on 2010-03-09
Yes, I did try that last night.  The file /etc/modprobe.d/lirc-blacklist already existed, but it only had "blacklist ati_wonder" in it, so I added "blacklist lirc_atiusb".  But no matter what I did, the module would still load.  I made sure that I didn't fat-finger it.

The module could be removed with the "rmmod" command, but when I plugged in the RF receiver, or restarted LIRC it would come back.  I tried rebooting the system too.

I do not have the file "/etc/modprobe.d/lirc" though.  Base on the comments, I wonder if I need to run "dpkg-reconfigure lirc"?  I'll give it a try tonight.

---

### Post by mrob on 2010-03-09
Success!

I couldn't resist trying before heading out this morning.  I ran "dpkg-reconfigure lirc" and selected the ATI RF Remote Userspace choice.  Then I replaced /etc/lircd.conf with the one for the Firefly remote.  Now "irw" is showing my button presses.  I restarted my MythTV Frontend all is working.

Thanks for all of your time and help...I owe you big!

---

### Post by Calmor on 2010-03-09
Excellent!  I didn't remember running dpkg-reconfigure, but it seemed it might provide a valuable clue.

You don't owe anything, just glad I could be of help.  That's what we're all here for, right?

---


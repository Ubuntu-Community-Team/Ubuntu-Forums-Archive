---
title: "iMON IR and Antec 430 Fusion Knob"
date: 2008-03-13
forum: Mythbuntu
---

### Post by cjs500 on 2008-03-13
I've been reading numerous posts for getting the iMON VFD working and IR and have definately felt everyone pain with this... those that are still having issues getting it all working. I still haven't gotten everything working myself but did manage to make some progress in a positive direction at least. 

This is my hardware/software I've been working with:

Items related to IR / Volume Control Knobs / Remote
- Antec fusion 430 black (V2 I think -- Veris)
- Media Center Remote (RC6 model#GP-IR02BK)

I've been using Mythbuntu 7.10 amd64 downloaded Mar-07-2008
- The libraries that is installed for lirc = mythtv lircd-0.8.2

First off, being that I've new to the MythTV world I haven't quite figured out how to get the remote to control the Myth TV menus yet but have managed to get the remote and IR hardware working including the Antec case knob. I've read most people haven't been able to get the volume control knob on the Antec case working so I figure you may want to know this. I've discovered that the knob can be configured in the /etc/lirc/lircd.conf file. I've used the lirc tools to configure this. These are steps I did to achieve this:

On an off note I overrode the root password to I didn't have to sudo everything.
$ sudo bash
password: <your_password>

# passwd
New Password: <new_root_password>
Confirm Password: <new_root_password>

# exit

$ su
Password: <new_root_password>

And bamm! Root prompt!

Anyway, back to the steps

1) Queried the system to make sure it could actually see the iMON LCD controller attached to the USB bus.

root@mythtv:~# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c512 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

2) Recorded a new lircd.conf file using my remote through the iMON IR

root@mythtv:~# irrecord --device=/dev/lirc0 /root/lircd.conf

 - Blurb about irrecord and asks to press RETURN to continue.
 - Asks you to hold down an arbitrary button (any button until it find a gap length). Taken that the IR device is detected correctly and your remote can communicate properly you should see dots start streaming across the screen. I tried another remote besides the MCE remote and got nothing.
 - Asks you to enter the name for the next button and press enter. I just simply called the buttons by name labelled like LiveTV, Ok, Arrow_Up, etc. Don't use spaces in your button labels.
 - Now press the button that you named.
 - Repeat until you have programmed all your buttons on the remote but don't quit the program just yet. I found you can create a new button for the Antec knob like knob_ccw for counter clockwise and then turn the knob in that direction. Create another button for knob_cw for clockwise. Now you can press ENTER to finish.
- Last it will ask you to press a button as fast as you can etc. Just follow it and complete the process which will write the new lircd.conf file.

NOTE: If you open the lircd.conf that was created you will notice the knobs got recorded as a button press. Since it's all part of the iMON circuit board it made sense that it would record a code in line with the IR signals sent by the remote.

3) Backup old lircd.conf and copy in the new one.

mv /etc/lirc/lircd.conf /etc/lirc/lircd.conf.old
cp /root/lircd.conf /etc/lirc/

4) Restart the lirc service

root@mythtv:~# /etc/init.d/lirc restart
Stopping lirc daemon: lircmd lircd.
Starting lirc daemon: lircd.

5) Test the ir output and make sure it's working

Once the command execute try pressing buttons on your remote and turn the knob on the Antec case and make sure it dumps out codes to the console.

root@mythtv:~# irw
00000000800f040c 00 pc_power mceusb_antec_knob
00000000800f040c 01 pc_power mceusb_antec_knob
00000000800f0422 00 ok mceusb_antec_knob
00000000800f0422 01 ok mceusb_antec_knob
00000000800f0410 00 vol_up mceusb_antec_knob
00000000800f0410 01 vol_up mceusb_antec_knob
00000000800f0411 00 vol_down mceusb_antec_knob
00000000800f0411 01 vol_down mceusb_antec_knob
00000000800f0401 00 1 mceusb_antec_knob
00000000800f0401 01 1 mceusb_antec_knob
00000000800f0402 00 2 mceusb_antec_knob
00000000800f0402 01 2 mceusb_antec_knob
00000000800f0403 00 3 mceusb_antec_knob
00000000800f0403 01 3 mceusb_antec_knob
0000000000010000 00 knob_cw mceusb_antec_knob
0000000000010000 01 knob_cw mceusb_antec_knob
0000000001000000 00 knob_ccw mceusb_antec_knob
0000000001000000 01 knob_ccw mceusb_antec_knob
0000000001000000 00 knob_ccw mceusb_antec_knob

Like I said above I hven't quite figure how to make the output control the menus in Mythbuntu but hopefully this help. If anyone can help with this it would be greatly appreciated. I haven't been able to get the LCD to work yet either after numerous attempts. When I figure that out I'll post it in this thread.

---

### Post by cjs500 on 2008-03-13
BTW, here's a copy of the lirc.conf if anyone is interested what it looks like after applying the above instructions.

> 
root@mythtv:~# cat /etc/lirc/lircd.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(default) on Wed Mar 12 22:39:58 2008
#
# contributed by
#
# brand:                       /root/lircd.conf
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  mceusb_antec_knob
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          203989
  toggle_bit_mask 0x8000

      begin codes

# Top control buttons
          zoom                     0x800F0427
          pc_power                 0x800F040C
          radio                    0x800F0450
          music                    0x800F0447
          pictures                 0x800F0449
          videos                   0x800F044A
          recorded_tv              0x800F0448
          guide                    0x800F0426
          live_tv                  0x800F0425
          dvd_menu                 0x800F0424

# Player Controls (DVD, VCR, etc)
          play                     0x800F0416
          pause                    0x800F0418
          stop                     0x800F0419
          record                   0x800F0417
          rewind                   0x800F0415
          forward                  0x800F0414
          skip_backward            0x800F041B
          skip_forward             0x800F041A

# Nvigation Buttons
          arrow_up                 0x800F041E
          arrow_left               0x800F0420
          arrow_down               0x800F041F
          arrow_right              0x800F0421
          ok                       0x800F0422
          back                     0x800F0423
          more                     0x800F040F

# Standard Controls
          vol_up                   0x800F0410
          vol_down                 0x800F0411
          channel_up               0x800F0412
          channel_down             0x800F0413
          mute                     0x800F040E
          win_button               0x800F040D
          1                        0x800F0401
          2                        0x800F0402
          3                        0x800F0403
          4                        0x800F0404
          5                        0x800F0405
          6                        0x800F0406
          7                        0x800F0407
          8                        0x800F0408
          9                        0x800F0409
          0                        0x800F0400
          asterix                  0x800F041D
          pound                    0x800F041C
          clear                    0x800F040A
          enter                    0x800F040B

# Lower color buttons
          red                      0x800F045B
          green                    0x800F045C
          yellow                   0x800F045D
          blue                     0x800F045E

# Antec Volume Control Knob
          knob_ccw                 0x01000000
          knob_cw                  0x00010000
      end codes

end remote


---

### Post by cjs500 on 2008-03-13
Success with the remote setup and knob!! :)

Once the /etc/lirc/lircd.conf is configured you have to match up the buttons names to the button names in /home/<front_end_user>/.mythtv/lircrc file. 

Reference Link:
[http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3](http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3)

Now off to the LCD problem. :P

---

### Post by axelsvag on 2008-05-20
I really having trouble getting this to work. I have changed the remote to imon pad in the mcc. I assurred me that the imon is there somewhere with the lsusb ```
aco@aco-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

``` but when i try to irrecord  get this ```
aco@aco-desktop:~$ sudo irrecord --device=/dev/lirc0 /root/lircd.conf
[sudo] password for aco: 

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not open /dev/lirc0
irrecord: default_init(): Device or resource busy
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

``` and when I try the lirc1 that is not supposed to be there i get. ```
aco@aco-desktop:~$ sudo irrecord --device=/dev/lirc1 /root/lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc1
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

``` When I use the irw and try to use the wheel everything seems ok ```
aco@aco-desktop:~$ irw
00000000000100ff 00 CW Antec_Fusion_Wheel
00000000000100ff 01 CW Antec_Fusion_Wheel
00000000000100ff 02 CW Antec_Fusion_Wheel
00000000010000ff 00 CCW Antec_Fusion_Wheel
00000000010000ff 01 CCW Antec_Fusion_Wheel
00000000010000ff 02 CCW Antec_Fusion_Wheel

``` Have I bought a v1 instead of a v2 ?? I got the lcd/vfd out and tried to look at it . It looked as if there is an ir eye in right corner and the text  on it said SG-IR-AT and the following numbers 060821-3178 so I hope there is an ir function there. There was a usb cable that went through the display and on to the wheel. Any suggestions?

---

### Post by Bob. on 2008-08-07
I have the same experiences. Knob working O.K. but IR don't work. Does anybody any suggestions?

---

### Post by axelsvag on 2008-08-07
I think more and more that I have been tricked. I probably got a V1 version instead of the V2 with onboard IR sensor. Have you looked at your LCD/VFD device to read any numbers or markings on it?

---

### Post by petermichael on 2008-08-07
Hi 
Have you looked at this link?
[http://mythbuntu.nl/hardware/antec-fusion-v2-imon-lcd-lirc-installation-guide](http://mythbuntu.nl/hardware/antec-fusion-v2-imon-lcd-lirc-installation-guide)

It helped me setting up the ir on the antec v2.
Best Regards
Peter Michael

---

### Post by gpap1266 on 2008-10-30
Help needed!!!!
I have the thermaltake dh 101
and i was in mythbuntu 8.04
after i made many efforts to install new lirc drivers (lirc-0.8.3)
nothing better even folowing th how to ( [http://mythtvblog.blogspot.com/2008/...with-lirc.html](http://mythtvblog.blogspot.com/2008/...with-lirc.html) )
Finally decide to upgrade to mythbuntu 8.10
but UNFORTUNATELY after
Code:

sudo /etc/init.d/lirc restart --verbose

i take back the message.....
Unable to load LIRC kernel modules. Verify your
* selected kernel modules in /etc/lirc/hardware.conf
Any ideas will be very very use full....

---

### Post by Rompalle on 2008-10-30
> **cjs500 said:**
> 

Like I said above I hven't quite figure how to make the output control the menus in Mythbuntu but hopefully this help. If anyone can help with this it would be greatly appreciated. I haven't been able to get the LCD to work yet either after numerous attempts. When I figure that out I'll post it in this thread.

In your ~/.mythtv/lircrc file you need to map your remote control buttons to mythtv controls.

below is an example of volume up and down for your remote.

 begin
   remote = mceusb_antec_knob
   prog = mythtv
   button = vol_down
   repeat = 1
   config = F10
 end
 
 begin
   remote = mceusb_antec_knob
   prog = mythtv
   button = vol_up
   repeat = 1
   config = F11
 end

---

### Post by danmoody on 2008-11-24
hey does anyone have experience with this product ->
[Antec Multimedia-Station EZ External IR receiver and remote]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811999190")?

I want to use it with mythbuntu8.10 and am kinda new to linux, which imon driver shuold i use during starup? and any other tips would be nice :) 
'Thanks

---


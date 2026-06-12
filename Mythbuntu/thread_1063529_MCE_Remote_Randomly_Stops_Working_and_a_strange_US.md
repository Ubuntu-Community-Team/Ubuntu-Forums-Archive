---
title: "MCE Remote Randomly Stops Working and a strange USB drive issue"
date: 2009-02-08
forum: Mythbuntu
---

### Post by flesh99 on 2009-02-08
So I had a setup working on an old IBM T42 laptop. Of course this wasn't ideal so I got a refurb system for a good price, installed mythbuntu, and everything worked. Everything except the remote. On a fresh boot it works perfectly for anywhere from ten minutes to an hour or more. It always works on reboot and there is literally nothing in the logs about lirc at all except for when I stop and start lirc. Irw shows nothing at all when I press keys. Yet the device is seen, active, connected directly to a USB port and not a hub. I have tried everything I know to troubleshoot this but I am a cluster guy and don't have the foggiest about ir devices. I have searched google and come up blank. The remote is a standard MCE remote setup RC6, HP model.

The other, almost as annoying problem, is that the USB drives that were working properly on the other system don't mount at boot. They are in fstab by UUID and post-boot mount -a mounts them perfectly so they are functioning.

What gets me is that this is all the same hardware that was connected to the T42 and now is not functioning the same on the new system.

System: A-OPEN XC Cube
IR: MCE USB RC6 from HP
External Drives: WD Home - 1TB and 250GB

I can post logs if needed but there is literally nothing in them about the remote prior to or after failure.

**lircd.conf**
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

**/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb**
```
#
# brand:                        HP
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# https://help.ubuntu.com/community/Install_Lirc_Feisty

#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note:
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note:
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
        Blue          0x00007ba1
        Yellow        0x00007ba2
        Green         0x00007ba3
        Red           0x00007ba4
        Teletext      0x00007ba5

#ba6 - bae unused
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote
```

**~/.mythtv/lirrc**
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

```

I can't think of anything else to post that might be helpful. Restarting lirc doesn't help only a reboot brings the remote back and only for a while. Any assistance would be greatly appreciated.

---

### Post by flesh99 on 2009-02-09
Added a fix for the hdd issue, a patch mostly, added mount -a to rc.local.

Still having the remote issues.

---

### Post by RaygionsSumta on 2009-03-09
Did you ever find a fix for your IR problem?  I am starting to see the same thing.  I recently (2/28/09) upgraded from an ASUS M2NPV-VM to an ASUS M3N78-EM, running Intrepid Ibex (2.6.27-11-generic).  Starting this past Friday (3/6/09) after a boot and some short period of use ofther my remote or my Mediapro bluetooth keyboard, neither IR nor bluetooth signals will register.  I see no messages in either dmesg or messages when this occurs.

---

### Post by JedTheHead on 2009-10-11
Hey!  Were you able to find a resolution to this? I am having the same issues and it seems we may have the same motherboard.  My thread:  [http://ubuntuforums.org/showthread.php?p=8090487#post8090487](http://ubuntuforums.org/showthread.php?p=8090487#post8090487)

Thanks!

---

### Post by GoofYas007 on 2009-10-17
Hi people,

facing the same strange behavior. Running Jaunty, all patches installed.
uname -a --> Linux server 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
 
this is the lspci:

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 RAID bus controller: nVidia Corporation Device 0ad8 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 SCSI storage controller: QLogic Corp. ISP1020 Fast-wide SCSI (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)

lsusb doesn't produce anything (hangs)
can't do CTRL+C or anything, session just stalls.

Indeed remote works for about 10-50 key strokes & then just stops working, nothing in the logs. Although it looks like an USB driver issue. I swapped to 7.04 (my old XBMC machine) and it works flawlessly.

Any advice would be appreciated.

---

### Post by GoofYas007 on 2010-04-03
I also posted this in the bugs section:

I solved my problem by buying a new main-board. (with AMD chip-set)
Strangely enough I only had this problem on a NVIDIA chip-set.

For what it's worth my experience is (2 mb's with NVIDIA chip-sets) that it's due to the NVIDIA thing.

I can now again use the remote continuously without fear of it stopping randomly after a couple of key presses...

---

### Post by Lepy on 2010-04-03
Old thread, but I've also had some similar usb problems on an nvidia based chipset. 

Occasionally a usb devices will stop responding, but a reboot always fixes the problem. Connected to usb are: ir receiver, 360 controller wireless receiver, keyboard/trackpad dongle, usb printer, and sometimes a usb hdd

Nothing shows up in logs except in dmesg, which always spits out multiple complaints after the device stop responding like: 
INFO: task *whatevertask* blocked for more than 120 seconds

Google searches bring up many complaints about the "task blocked for more than 120 seconds," but none offer a solution. One launchpad thread says the bug has been fixed in a recent kernel, but I have seen no improvements enabling proposed updates. There is also a suggestion to add highres=off to the boot parameters, but I have neglected to try this since most of of these disconnects seem to rarely happen. Very annoying when it happens though, especially if it happens before a heavy night of recording.

I hope this isn't a hardware issue. Seems strange since the disconnect is always remedied on reboot. Does anyone else see these dmesg outputs as well?

---

### Post by Arnoud30 on 2010-05-07
I had the same problem but found a fix for my system.
 
Hauppauge MCE2 remote. ASUS M3N NVIDIA motherboard, mythbuntu 9.04, mythtv 0.22 fixes. 
 
No messages in Dmesg and only able to recover remote after 
reboot. In the beginning the remote was working without problems, but got worse and worse.
Particulary when enabling IR transmissions it would fail within minutes.
I saw mentioned in some other forum that the lirc_mce driver could not restart the usb, so was wondering if the mce itself had a problem.
 
After some experimenting I (finally) managed to find a solution. This is fully stable. Never had a single problem afterwards.
 
What I did:

1) Replaced the original long thin USB cable by a short thick USB cable. The thick ones have normally better shielding and thicker conductors.

2) Opened the MCE housing, and soldered a 100uf capacitor (in my case a tantalium, but any cap will do) between the +5v and ground of the USB 
interface connector. Watch the polarity of the cap.
 
I did both changes at the same time, so don't know you will need both changes to fix the problem.
 
Success.

---


---
title: "PVR-350 remote not working - Silver remote"
date: 2007-11-10
forum: Mythbuntu
---

### Post by Sir_Ty on 2007-11-10
Info: MythTV 7.10 new install
WinTV350, Silver Remote (sticker says R808-HPG on the inside of battery cover)
Also installed in the Antec Veris Fusion case.  I think this may be causing some of the trouble, as it has it's own IR receiver from what I understand.  (It also has an LCD module I'd like to get working, but that will be a subject for another message.)

I've got two devices listed for /dev/lirc*
> /dev/lirc0  /dev/lirc1  /dev/lircd


The irw command comes up with nothing.  If I run mode2 -d /dev/lirc1 I can get the hex codes from the remote to show.  (Okay SUDO mode2 -d /dev/lirc1, otherwise I get permission denied.  UPDATE: Exited out of MythTV frontend and no longer getting the permission denied.  But still nothing comes up when rpessing buttons on the remote.)  Same thing with /dev/lirc0 comes up with "device or resource busy."  

> guest@ProjectorPC:/etc/lirc$ sudo mode2 -d /dev/lirc1
[sudo] password for guest:
code: 0x17e1
code: 0x1fe0
code: 0x17e1
code: 0x1fd1
code: 0x1fd1
code: 0x17d0
code: 0x17d0


Some other info:
> 
guest@ProjectorPC:/etc/lirc$ ps -eaf | grep lircd
root      3869     1  0 18:36 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0
guest     7495  7379  0 19:55 pts/0    00:00:00 grep lircd

> 
guest@ProjectorPC:/etc/lirc$ more hardware.conf 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
LIRCMD_CONF=""

> 
guest@ProjectorPC:/etc/lirc$ more lircd.conf
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
(ETC)

> 
[email]guest@ProjectorPC:/home/mythtv/.myth[/email]tv$ more lircrc
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = FastRwd
    config = <
    repeat = 0
    delay = 0
end
(ETC)

> 
guest@ProjectorPC:~$ lsmod | grep lirc
lirc_i2c               11268  0 
lirc_imon              17028  1 
lirc_dev               15860  2 lirc_i2c,lirc_imon
i2c_core               26112  12 cx88xx,msp3400,saa7127,saa7115,bttv,tuner,lirc_i2c,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
usbcore               138632  6 lirc_imon,xpad,usbhid,ohci_hcd,ehci_hcd


This one worries me, as it seems to be ignoring a bunch of error messages:
> 
guest@ProjectorPC:~$ dmesg | grep lirc
d/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.001359] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.009351] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.017354] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.025341] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.033335] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.041329] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.049323] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.057318] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.065312] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.073307] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.081301] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.089297] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.097291] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.105286] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored
[ 3888.113280] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: usb_rx_callback: status (-32): ignored


---

### Post by superm1 on 2007-11-10
for starters:
modify the DEVICE="" to be /dev/lirc1.

You will probably need another lircrc file (there have been reports the pvr-350 lircrcs aren't that good).  Look on the forum for it.

---

### Post by Sir_Ty on 2007-11-11
After a reboot the /dev/lirc1 device went away.  So I changed the device back to the defaul blank, and it's now picking up the remote.  Case closed here.

I believe the problem may have been in the Mythbuntu Control Centre.  It does not give a terminal window, and I'm not sure where messages are logged, when there is a problem.  For instance, I had checked "Generate Dynamic Button mappings" and clicked applied, and the prorgam seems to do something, a quick status bar, then it come back to the same screen with the button un-checked.  Having a similar issue with the Proprietary Codecs, so I'll start a new thread.

Thanks for the help SuperM1!

---

### Post by superm1 on 2007-11-11
> **Sir_Ty said:**
> After a reboot the /dev/lirc1 device went away.  So I changed the device back to the defaul blank, and it's now picking up the remote.  Case closed here.

I believe the problem may have been in the Mythbuntu Control Centre.  It does not give a terminal window, and I'm not sure where messages are logged, when there is a problem.  For instance, I had checked "Generate Dynamic Button mappings" and clicked applied, and the prorgam seems to do something, a quick status bar, then it come back to the same screen with the button un-checked.  Having a similar issue with the Proprietary Codecs, so I'll start a new thread.

Thanks for the help SuperM1!
Well the generate dynamic buttons only does that once.  There is no need to have to redo it again after hitting apply.  (Hence why it's unchecked)

I find this rather odd that it just "started working".  You must have blacklisted your lirc_imon module or something similar.

---

### Post by Sir_Ty on 2007-11-11
> **superm1 said:**
> I find this rather odd that it just "started working".  You must have blacklisted your lirc_imon module or something similar.

Nah it's still there.  In fact I've installed the LCDProc server and now instead of a bunch of tilde n's on the VFD its got the heatbeat screen displaying.  Working on getting a decent client for this tiny 16x2 screen.  Definately a lot of manual effort to get that going.

---


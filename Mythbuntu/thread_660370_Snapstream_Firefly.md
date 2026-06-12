---
title: "Snapstream Firefly"
date: 2008-01-06
forum: Mythbuntu
---

### Post by Lvcoyote on 2008-01-06
Can anyone point me to an easy to understand guide on how to get this remote working??  All I have done so far is select Snapstream X10 remote in the MythTV control panel, but the remote is not working at all, no signs of life.  I read where you can change the hardware.conf and lircd.conf files located in /etc/lirc and have done so, but as soon as I edit those files then the control panel shows "no remote selected" and is greyed out again, so I change that back to the Snapstream X10 and my .conf files return back to what they were before editing them, vicious circle......LOL

Anyway, any help appreciated!

---

### Post by williammanda on 2008-01-07
Try this link for help:

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

You shouldn't need to edit the lircd.conf unless it is setup wrong, it should have snapstream in the comment area in the beginnng. You can goto this link to generate the lircd.conf :

[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

or just use the Mythbuntu Lirc generator in the control center. Also you should not need to edit the hardware.conf, this is done for you by the control center.

Once the lircd.conf file is set run irw in terminal and press some keys to see if the remote works. If that is ok, then look for a .lircrc file in your /home/user directory. If that looks correct, then try your remote in a program, Mythtv, Xine, etc...

Here is one of my lircd.conf files, it uses channel ID 5. Be sure not to use it unless you know how to setup the remote for channel ID 5. This for reference only!

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(default) on Wed Dec 12 19:55:41 2007
#
# contributed by 
#
# brand: Snapstream Firefly RF remote
# model no. of remote control: R1000
# devices being controlled by this remote:
# THIS REMOTE IS USING CHANNEL ID 5

begin remote

  name  Snapstream Firefly RF remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x4000
  gap          228000
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0xC1AC
          CLOSE                    0x1702
          1                        0xA28D
          2                        0x230E
          3                        0xA48F
          4                        0x2510
          5                        0xA691
          6                        0x2712
          7                        0xA893
          8                        0x2914
          9                        0xAA95
          0                        0x2C17
          BACK                     0x2B16
          ENT                      0xAD98
          VOL+                     0x9E89
          VOL-                     0x1D08
          MUTE                     0x9F8A
          FIREFLY                  0x1500
          CH+                      0xA08B
          CH-                      0x210C
          INFO                     0xC3AE
          OPTION                   0x442F
          UP                       0xAF9A
          DOWN                     0x3722
          LEFT                     0xB29D
          RIGHT                    0x341F
          OK                       0xB39E
          MENU                     0x311C
          EXIT                     0xB5A0
          REC                      0x3C27
          PLAY                     0xBAA5
          STOP                     0x3D28
          REW                      0xB9A4
          FWD                      0x3B26
          PREV                     0xC0AB
          PAUSE                    0x3E29
          NEXT                     0xBFAA
          MUSIC                    0x1B06
          PHOTOS                   0x9A85
          DVD                      0x1904
          TV                       0x9883
          VIDEO                    0x1C07
          HELP                     0x9681
          MOUSE                    0x422D
          A                        0xAE99
          B                        0x301B
          C                        0xB6A1
          D                        0x3823
      end codes

end remote
```

Thanks

---

### Post by Lvcoyote on 2008-01-07
Ok as per the link you provided I tried "sudo apt-get install lirc" and it said I already have it installed and that is the latest version.  I ran "irw" in terminal and get no response from pressing remote control buttons.

Here is the contents of the hardware.conf file located at /etc/lirc
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"

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
MODULES="lirc_dev lirc_atiusb"

# Default configuration files for your hardware if any
LIRCD_CONF="atiusb/lircd.conf.atiusb"
LIRCMD_CONF=""


Here is the content of the lircd.conf file located at /etc/lirc
> #
# this config file was automatically generated
# using lirc-0.7.0-CVS(atiusb) on Tue Apr 27 23:51:09 2004
#
# contributed by Paul Miller <pmiller9@users.sourceforge.net>
#
# brand: ATI Remote Wonder
# model no. of remote control: 5000015900A
# devices being controlled by this remote: ATI USB Receiver
#
# CHANNEL CODES
# To change your channel, hold the hand button down until the
# LED begins to blink.  Then enter the channel number
# (1 through 16) and press the hand again.
#
# NOTE!! The lirc_atiusb driver now removes the channel code
# from key-codes (by default).  This effectively outputs codes
# for remote channel 1.  You can change this behavior by
# loading the module with unique=1.  Type `modinfo lirc_atiusb`
# for details.

begin remote

  name  ATIUSB_5000015900A
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          139944
  toggle_bit      0


      begin codes
          A                        0x000000000000F500
          B                        0x000000000000F601
          C                        0x0000000000000E19
          D                        0x000000000000101B
          E                        0x0000000000001621
          F                        0x0000000000001823
          TV                       0x000000000000F803
          DVD                      0x000000000000F904
          WEB                      0x000000000000FA05
          BOOK                     0x000000000000FB06
          HAND                     0x000000000000FC07
          POWER                    0x000000000000F702
          MOUSE_LEFT_BTN           0x0000000000006D78
          MOUSE_RIGHT_BTN          0x000000000000717C
          MOUSE_UP                 0x0000000000006772
          MOUSE_DOWN               0x0000000000006B76
          MOUSE_LEFT               0x0000000000006C77
          MOUSE_RIGHT              0x0000000000006B76
          VOL_UP                   0x000000000000FD08
          VOL_DOWN                 0x000000000000FE09
          MUTE                     0x000000000000FF0A
          CH_UP                    0x000000000000000B
          CH_DOWN                  0x000000000000010C
          1                        0x000000000000020D
          2                        0x000000000000030E
          3                        0x000000000000040F
          4                        0x0000000000000510
          5                        0x0000000000000611
          6                        0x0000000000000712
          7                        0x0000000000000813
          8                        0x0000000000000914
          9                        0x0000000000000A15
          0                        0x0000000000000C17
          LIST                     0x0000000000000B16
          CHECK                    0x0000000000000D18
          UP                       0x0000000000000F1A
          DOWN                     0x0000000000001722
          LEFT                     0x000000000000121D
          RIGHT                    0x000000000000141F
          OK                       0x000000000000131E
          TIMER                    0x000000000000111C
          MAX                      0x0000000000001520
          REWIND                   0x0000000000001924
          PLAY                     0x0000000000001A25
          FFWD                     0x0000000000001B26
          REC                      0x0000000000001C27
          STOP                     0x0000000000001D28
          PAUSE                    0x0000000000001E29
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0pre1(atiusb) on Fri Nov 28 16:56:46 2003
#
# contributed by Jason Piterak
#
# brand:                       ATI
# model no. of remote control: 5000022000
#
# devices being controlled by this remote:
# MythTV PVR using knopmyth by Cecil and Dale at
#  [http://mysettopbox.tv](http://mysettopbox.tv)
# Key map names are as per ATI's website:
# [http://www.ati.com/support/connectors/remotecontrol/atiremotecontrolbutton=s.html](http://www.ati.com/support/connectors/remotecontrol/atiremotecontrolbutton=s.html)
# Feel free to change them as you see fit :-)
#
# NOTE:  There are 16 channels for this remote; this file only
# supports one channel.  See the GATOS project for information
# on how to change the channel.  Not tested.  Unknown channel.
#
# also reported by Jeffrey Barnhill to work with model 5000023600 while
# the dedicated section below did not work

begin remote

  name  ATIUSB_5000022000
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0000
  gap          139891
  toggle_bit      0


      begin codes
          a                        0x000000000000C500
          b                        0x000000000000C601
          power                    0x000000000000C702
          tv                       0x000000000000C803
          dvd                      0x000000000000C904
          web                      0x000000000000CA05
          media_library            0x000000000000CB06
          drag                     0x000000000000CC07
          mouse-button_left        0x0000000000003D78
          mouse-button_right       0x000000000000417C
          mouse-up                 0x0000000000003772
          mouse-down               0x0000000000003873
          mouse-left               0x0000000000003570
          mouse-right              0x0000000000003671
          mouse-left_up            0x0000000000003974
          mouse-right_up           0x0000000000003A75
          mouse-left_down          0x0000000000003C77
          mouse-right_down         0x0000000000003B76
          vol-up                   0x000000000000CD08
          vol-down                 0x000000000000CE09
          mute                     0x000000000000CF0A
          chan-up                  0x000000000000D00B
          chan-down                0x000000000000D10C
          1                        0x000000000000D20D
          2                        0x000000000000D30E
          3                        0x000000000000D40F
          4                        0x000000000000D510
          5                        0x000000000000D611
          6                        0x000000000000D712
          7                        0x000000000000D813
          8                        0x000000000000D914
          9                        0x000000000000DA15
          0                        0x000000000000DC17
          dvd-root_menu            0x000000000000DB16
          launch_setup             0x000000000000DD18
          c                        0x000000000000DE19
          d                        0x000000000000E01B
          tv_on_demand             0x000000000000E11C
          max_window               0x000000000000E520
          cursor-up                0x000000000000DF1A
          cursor-down              0x000000000000E722
          cursor-left              0x000000000000E21D
          cursor-right             0x000000000000E41F
          ok                       0x000000000000E31E
          e                        0x000000000000E621
          f                        0x000000000000E823
          rewind                   0x000000000000E924
          play                     0x000000000000EA25
          fast_forward             0x000000000000EB26
          record                   0x000000000000EC27
          stop                     0x000000000000ED28
          pause                    0x000000000000EE29
      end codes

end remote

#
# this config file was automatically generated
# using lirc-0.7.0-CVS(atiusb) on Sat May 15 10:44:51 2004
#
# contributed by Jurgen Kramer
#
# brand: ATI
# model no. of remote control: 5000023600
# devices being controlled by this remote: MythTV 0.14
#
# USB ID: 0bc7:0004
#

begin remote

  name  ATIUSB_5000023600
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227972
  min_repeat      4
  toggle_bit      0


      begin codes
          1                        0x000000000000920D
          2                        0x000000000000930E
          3                        0x000000000000940F
          4                        0x0000000000009510
          5                        0x0000000000009611
          6                        0x0000000000009712
          7                        0x0000000000009813
          8                        0x0000000000009914
          9                        0x0000000000009A15
          a                        0x0000000000008500
          b                        0x0000000000008601
          power                    0x0000000000008702
          tv                       0x0000000000008803
          dvd                      0x0000000000008904
          web                      0x0000000000008A05
          media_library            0x0000000000008B06
          drag                     0x0000000000008C07
          0                        0x0000000000009C17
          c                        0x0000000000009E19
          d                        0x000000000000A01B
          mute                     0x0000000000008F0A
          tv_on_demand             0x000000000000A11C
          max_window               0x000000000000A520
          e                        0x000000000000A621
          f                        0x000000000000A823
          ok                       0x000000000000A31E
          left                     0x000000000000A21D
          right                    0x000000000000A41F
          up                       0x0000000000009F1A
          down                     0x000000000000A722
          rewind                   0x000000000000A924
          play                     0x000000000000AA25
          forward                  0x000000000000AB26
          record                   0x000000000000AC27
          stop                     0x000000000000AD28
          pause                    0x000000000000AE29
          mouse_button_left        0x000000000000FD78
          mouse_button_right       0x000000000000017C
          vol-down                 0x0000000000008E09
          vol-up                   0x0000000000008D08
          chan-down                0x000000000000910C
          chan-up                  0x000000000000900B
          mouse-up                 0x000000000000F772
          mouse-down               0x000000000000F873
          mouse-left               0x000000000000F570
          mouse-right              0x000000000000F671
          mouse-left_up            0x000000000000F974
          mouse-left_down          0x000000000000FC77
          mouse-right_up           0x000000000000FA75
          mouse-right_down         0x000000000000FB76
          dvd-root_menu            0x0000000000009B16
          launch_setup             0x0000000000009D18
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Tue Mar 29 17:33:06 2005
#
# contributed by Raphaël Doursenaud (rdoursenaud@free.fr)
#
# brand: Sapphire (ATI)
# model no. of remote control: 5000023600
# devices being controlled by this remote: xmms, tvtime
#

begin remote

  name  SAPPHIRE_ATIUSB_5000023600
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          227990
  toggle_bit      0


      begin codes
          1                        0x00000014E20D0000
          2                        0x00000014E30E0000
          3                        0x00000014E40F0000
          4                        0x00000014E5100000
          5                        0x00000014E6110000
          6                        0x00000014E7120000
          7                        0x00000014E8130000
          8                        0x00000014E9140000
          9                        0x00000014EA150000
          a                        0x00000014D5000000
          b                        0x00000014D6010000
          power                    0x00000014D7020000
          tv                       0x00000014D8030000
          dvd                      0x00000014D9040000
          web                      0x00000014DA050000
          media_library            0x00000014DB060000
          drag                     0x00000014DC070000
          0                        0x00000014EC170000
          c                        0x00000014EE190000
          d                        0x00000014F01B0000
          mute                     0x00000014DF0A0000
          tv_on_demand             0x00000014F11C0000
          max_window               0x00000014F5200000
          e                        0x00000014F6210000
          f                        0x00000014F8230000
          ok                       0x00000014F31E0000
          left                     0x00000014F21D0000
          right                    0x00000014F41F0000
          up                       0x00000014EF1A0000
          down                     0x00000014F7220000
          rewind                   0x00000014F9240000
          play                     0x00000014FA250000
          forward                  0x00000014FB260000
          record                   0x00000014FC270000
          stop                     0x00000014FD280000
          pause                    0x00000014FE290000
          mouse_button_left        0x000000144D780000
          mouse_button_right       0x00000014517C0000
          vol-down                 0x00000014DE090000
          vol-up                   0x00000014DD080000
          chan-down                0x00000014E10C0000
          chan-up                  0x00000014E00B0000
          mouse-up                 0x0000001447720000
          mouse-down               0x0000001448730000
          mouse-left               0x0000001445700000
          mouse-right              0x0000001446710000
          mouse-left_up            0x0000001449740000
          mouse-left_down          0x000000144C770000
          mouse-right_up           0x000000144A750000
          mouse-right_down         0x000000144B760000
          dvd-root_menu            0x00000014EB160000
          launch_setup             0x00000014ED180000
      end codes

end remote


# lircd.conf for X-10 Lola remote
#
# this config file was automatically generated
# using lirc-0.6.6(any) on Sat May 15 14:41:38 2004
# matching MythTV configuration file at [http://wendy.seltzer.org/mythtv/lircrc](http://wendy.seltzer.org/mythtv/lircrc)
#
#
# brand:	X-10 Lola
# model no. of remote control:  UR89A
# devices being controlled by this remote: mythtv
#

begin remote

  name  X-10_Lola
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0

  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          219972
  toggle_bit      0


      begin codes
          up                       0x000000000000600B
          down                     0x000000000000610C
          left                     0x0000000000005D08
          right                    0x0000000000005E09
          M                        0x0000000000005F0A
          1                        0x000000000000620D
          2                        0x000000000000630E
          3                        0x000000000000640F
          4                        0x0000000000006510
          5                        0x0000000000006611
          6                        0x0000000000006712
          7                        0x0000000000006813
          8                        0x0000000000006914
          9                        0x0000000000006A15
          0                        0x0000000000006C17
          a-d                      0x0000000000006B16
          a-b                      0x0000000000006D18
          pageup                   0x000000000000711C
          pagedown                 0x0000000000007520
          T                        0x000000000000832E
          E                        0x000000000000842F
          F                        0x0000000000005C07
          S                        0x0000000000008530
          scan-                    0x000000000000802B
          rew                      0x0000000000007924
          play                     0x0000000000007A25
          ff                       0x0000000000007B26
          scan+                    0x0000000000007F2A
          rec                      0x0000000000007C27
          stop                     0x0000000000007D28
          pause                    0x0000000000007E29
          playlist                 0x0000000000005601
          playing                  0x000000000000822D
          enter                    0x000000000000731E
          eu                       0x0000000000006F1A
          ed                       0x0000000000007722
          el                       0x000000000000721D
          er                       0x000000000000741F
          alb                      0x0000000000006E19
          art                      0x000000000000701B
          gen                      0x0000000000007621
          trk                      0x0000000000007823
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0pre6(atiusb) on Fri Jul  9 10:08:10 2004
#
# contributed by 		Julien Damon
#
# brand:                       microapp6in1
# see [http://www.microapp.com/fiche_produit.cfm?ref_produit=4184](http://www.microapp.com/fiche_produit.cfm?ref_produit=4184)
# distributed in France
# model no. of remote control: 4184(UR86E)
# devices being controlled by this remote:

#
# sold by Pearl as Q-Sonic Master Remote 6in1 PC
#

begin remote

  name  microapp6in1
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          203993
  toggle_bit      0


      begin codes
          num_1                    0x00000020EE11820D
          num_2                    0x00000020EE11420D
          num_3                    0x00000020EE11C20D
          num_4                    0x00000020EE11220D
          num_5                    0x00000020EE11A20D
          num_6                    0x00000020EE11620D
          num_7                    0x00000020EE11E20D
          num_8                    0x00000020EE11120D
          num_9                    0x00000020EE11920D
          num_0                    0x00000020EE11020D
          AV                       0x00000020EE11BA05
          ok                       0x00000020EE11520D
          up                       0x00000020EE11D50A
          left                     0x00000020EE11D20D
          right                    0x00000020EE11D10E
          down                     0x00000020EE11D30C
          exit                     0x00000020EE11C906
          menu                     0x00000020EE11B609
          mute                     0x00000020EE11A00F
          vol+                     0x00000020EE11600F
          vol-                     0x00000020EE11E00F
          ch+                      0x00000020EE11400F
          ch-                      0x00000020EE11C00F
          hand                     0x00000014307B0000
          skip_left                0x00000020EE113A05
          skip_right               0x00000020EE11D807
          play                     0x00000020EE11B00F
          backward                 0x00000020EE113807
          forward                  0x00000020EE11B807
          pause                    0x00000020EE11720D
          stop                     0x00000020EE11FF00
          record                   0x00000020EE11700F
          clic_left                0x000000142D780000
          clic_right               0x00000014317C0000
          mouse_up                 0x0000001427720000
          mouse_down               0x0000001428730000
          mouse_right              0x0000001426710000
          mouse_left               0x0000001425700000
          mouse_up_right           0x000000142A750000
          mouse_down_right         0x000000142B760000
          mouse_up_left            0x0000001429740000
          mouse_down_left          0x000000142C770000
          power                    0x00000020EE11F00F
# additional codes reported by Daniel Beyer for Q-Sonic Master Remote 6in1 PC
          leftbtn_up               0x000000142e790000
          rightbtn_up              0x00000014327d0000
          pc                       0x00000020ee11d40b

      end codes

end remote


# this config file was automatically generated
# using lirc-0.7.0pre7(atiusb) on Tue Aug 31 21:16:31 2004
#
# contributed by Martin Tomasek <mtd@centrum.cz>
#
# brand: ATI Remote Wonder
# model no. of remote control:
# devices being controlled by this remote: ATI USB Receiver (X10).
#
# * remote is set to channel 1, driver reports channel 16. don't know
# which is true.

#
# P:  Vendor=0bc7 ProdID=0004 Rev= 1.00
# S:  Manufacturer=X10 Wireless Technology Inc
# S:  Product=USB Receiver
#

begin remote

  name  atiusb_ch1
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227933
  toggle_bit      0


      begin codes
          A                        0x000000000000D500
          B                        0x000000000000D601
          C                        0x000000000000EE19
          D                        0x000000000000F01B
          E                        0x000000000000F621
          F                        0x000000000000F823
          POWER                    0x000000000000D702
          TV                       0x000000000000D803
          DVD                      0x000000000000D904
          WEB                      0x000000000000DA05
          BOOK                     0x000000000000DB06
          HAND                     0x000000000000DC07
          MOUSE_LEFT_BTN           0x0000000000004D78
          MOUSE_RIGHT_BTN          0x000000000000517C
          MOUSE_LEFT               0x0000000000004570
          MOUSE_RIGHT              0x0000000000004671
          MOUSE_UP                 0x0000000000004772
          MOUSE_DOWN               0x0000000000004873
          VOL_UP                   0x000000000000DD08
          VOL_DOWN                 0x000000000000DE09
          MUTE                     0x000000000000DF0A
          CH_UP                    0x000000000000E00B
          CH_DOWN                  0x000000000000E10C
          1                        0x000000000000E20D
          2                        0x000000000000E30E
          3                        0x000000000000E40F
          4                        0x000000000000E510
          5                        0x000000000000E611
          6                        0x000000000000E712
          7                        0x000000000000E813
          8                        0x000000000000E914
          9                        0x000000000000EA15
          0                        0x000000000000EC17
          LIST                     0x000000000000EB16
          CHECK                    0x000000000000ED18
          UP                       0x000000000000EF1A
          DOWN                     0x000000000000F722
          LEFT                     0x000000000000F21D
          RIGHT                    0x000000000000F41F
          OK                       0x000000000000F31E
          TIMER                    0x000000000000F11C
          MAXIMIZE                 0x000000000000F520
          REW                      0x000000000000F924
          FFWD                     0x000000000000FB26
          PLAY                     0x000000000000FA25
          STOP                     0x000000000000FD28
          RECORD                   0x000000000000FC27
          PAUSE                    0x000000000000FE29
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0pre4(atiusb) on Tue Nov  9 12:37:00 2004
#
# contributed by Phil Speights
#
# brand: nvidia
# model no. of remote control: UR88A
# devices being controlled by this remote: nvidia personal cinema
#

begin remote

  name  ATIUSB_UR88A
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          243948
  toggle_bit      0


      begin codes
          mouse-up                 0x4A75
          mouse-right_up           0x4A75
          mouse-right              0x4671
          mouse-right_down         0x4B76
          mouse-down               0x4B76
          mouse-left_down          0x4873
          mouse-left               0x4C77
          mouse-left_up            0x4772
          esc                      0xDF0A
          mouse-button_left        0x4D78
          mouse-button_right       0x517C
          1                        0xE20D
          2                        0xE30E
          3                        0xE40F
          4                        0xE510
          5                        0xE611
          6                        0xE712
          7                        0xE813
          8                        0xE914
          9                        0xEA15
          0                        0xEC17
          stop                     0xFD28
          play                     0xFA25
          fastfoward               0xFB26
          rewind                   0xF924
          pause                    0xFE29
          record                   0xFC27
          previous                 0xF621
          next                     0xF823
          up                       0xEF1A
          down                     0xF722
          right                    0xF41F
          left                     0xF21D
          web                      0xDC07
          music                    0xDB06
          photo                    0xDA05
          dvd/vcd                  0xD904
          dvr                      0xD803
          mute                     0xD500
          playlist                 0xD601
          chsurf                   0xD702
          dvdmenu                  0xEE19
          txt                      0xEB16
          snapshots                0xED18
          setup                    0xF01B
          audio                    0xF11C
          slow                     0xF520
          ok                       0xF31E
          vol+                     0xDE09
          vol-                     0xDD08
          chan-                    0xE10C
          chan+                    0xE00B
          zoom                     0xFF2A
          angle                    0x002B
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(atiusb) on Sun Jan 23 11:18:36 2005
#
# contributed by Dirk Aust
#
# brand:	Medion, Made by X10, China
# Remote P/N:	20016398
# Receiver P/N:	20016397
#
# bundled with bundled with Titanium TD8008 and TD8080 Aldi PC

begin remote

  name  Medion
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          139873
  toggle_bit      0


      begin codes
          TV                       0x012C
          VCR                      0x022D
          DVD                      0xD904
          MUSIC                    0xDB06
          RADIO                    0x032E
          PHOTO                    0xDA05
          TV_PREVIEW               0x042F
          CHANNEL_LIST             0x0530
          SETUP                    0xF01B
          VIDEO_DESKTOP            0x0631
          CHAN+                    0xE00B
          VOL-                     0xDD08
          MUTE                     0xD500
          VOL+                     0xDE09
          CHAN-                    0xE10C
          RED                      0x0732
          GREEN                    0x0833
          YELLOW                   0x0934
          BLUE                     0x0A35
          TXT                      0xEB16
          1                        0xE20D
          2                        0xE30E
          3                        0xE40F
          4                        0xE510
          5                        0xE611
          6                        0xE712
          7                        0xE813
          8                        0xE914
          9                        0xEA15
          TV/RADIO                 0xF11C
          0                        0xEC17
          DELETE                   0xF520
          RENAME                   0x0B36
          SNAPSHOT                 0xED18
          UP                       0xEF1A
          LEFT                     0xF21D
          OK                       0xF31E
          RIGHT                    0xF41F
          DOWN                     0xF722
          ACQ_IMAGE                0x0C37
          EDIT_IMAGE               0x0D38
          REW                      0xF924
          PLAY                     0xFA25
          FFW                      0xFB26
          RECORD                   0xFC27
          STOP                     0xFD28
          PAUSE                    0xFE29
          PREV                     0xF621
          FULL                     0x0E39
          NEXT                     0xF823
          DVD_MENU                 0xEE19
          DVD_AUDIO                0x0F3A
          POWER                    0xD702
      end codes

end remote


# this config file was automatically generated
# using lirc-0.7.0(atiusb) on Sat Feb 12 13:22:29 2005
#
# contributed by Steffen <starv-lirc@juniks.org>
#
# brand: ATI Sapphire Remote Bob II USB
# model no. of remote control: 5000024400
# devices being controlled by this remote: ASUS Digimatrix MythTV PVR
#

begin remote

  name  5000024400
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x0
  post_data_bits  16
  post_data      0x0
  gap          299851
  toggle_bit      0


      begin codes
          aux1                     0x023F
          aux2                     0x023F
          aux3                     0x023F
          aux4                     0x023F
          leftmouse                0x02A9
          rightmouse               0x02AA
          a                        0x0278
          b                        0x0279
          power                    0x020C
          dvd                      0x0238
          tv                       0x0239
          help                     0x02BE
          pc                       0x023F
          resize                   0x02D5
          hand                     0x02D0
          ati                      0x028E
          vol-up                   0x0210
          vol-down                 0x0211
          mute                     0x020D
          chan-up                  0x0220
          chan-down                0x0221
          mouse-up                 0x013F
          mouse-down               0x013F
          mouse-left               0x013F
          mouse-right              0x013F
          1                        0x0201
          2                        0x0202
          3                        0x0203
          4                        0x0204
          5                        0x0205
          6                        0x0206
          7                        0x0207
          8                        0x0208
          9                        0x0209
          0                        0x0200
          list                     0x0254
          check                    0x0282
          info                     0x02F9
          timer                    0x0296
          up                       0x0258
          left                     0x025A
          right                    0x025B
          down                     0x0259
          ok                       0x025C
          c                        0x017A
          d                        0x027B
          play                     0x022C
          e                        0x027C
          f                        0x027D
          rewind                   0x0229
          rec                      0x0237
          stop                     0x0231
          pause                    0x0230
          ffwd                     0x0228
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Jan 16 14:58:13 2005
#
# contributed by
#
# brand:                       Niveus
# model no. of remote control:
# devices being controlled by this remote: Niveus X10
#

begin remote

  name  Niveus_X10
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          203974
  toggle_bit      0


      begin codes
          power                    0x00000020EE11F00F
          mouse-up                 0x0000001447720000
          mouse-down               0x0000001448730000
          mouse-left               0x0000001445700000
          mouse-right              0x0000001446710000
          mouse-up-left            0x0000001449740000
          mouse-up-right           0x000000144A750000
          mouse-down-left          0x000000144C770000
          mouse-down-right         0x000000144B760000
          mouse-left-click         0x000000144D780000
          mouse-right-click        0x00000014517C0000
          mouse-drag               0x00000014507B0000
          vol-                     0x00000020EE01E00F
          vol+                     0x00000020EE81600F
          ch-                      0x00000020EEE1C00F
          ch+                      0x00000020EE61400F
          mute                     0x00000020EEC1A00F
          1                        0x00000020EEA1820D
          2                        0x00000020EE61420D
          3                        0x00000020EEE1C20D
          4                        0x00000020EE41220D
          5                        0x00000020EEC1A20D
          6                        0x00000020EE81620D
          7                        0x00000020EE01E20D
          8                        0x00000020EE31120D
          9                        0x00000020EEB1920D
          ent                      0x00000020EE71520D
          0                        0x00000020EE21020D
          a-b                      0x00000020EED1BA05
          a                        0x00000020EE513A05
          b                        0x00000020EEF1D807
          c                        0x00000020EEF1D609
          d                        0x00000020EEF1D906
          menu                     0x00000020EED1B609
          exit                     0x00000020EEE1C906
          up                       0x00000020EEF1D50A
          down                     0x00000020EEF1D30C
          left                     0x00000020EEF1D20D
          right                    0x00000020EEF1D10E
          ok                       0x00000020EE71520D
          rew                      0x00000020EE513807
          play                     0x00000020EED1B00F
          ff                       0x00000020EED1B807
          rec                      0x00000020EE11FF00
          stop                     0x00000020EE91700F
          pause                    0x00000020EE91720D
      end codes

end remote


#
# this config file was manually generated
# Time-stamp: <2006-11-09 10:15:33 root>
#
# contributed by Heike C. Zimmerer <hcz|hczim.de>
#
# brand: Medion MD95700 DVB-T USB box RF remote
# driver: lirc_atiusb
#
#
# Remote ID
#
# You can give your remote a unique ID and instruct lirc_atiusb
# to only accept signals from specific IDs and mask out the others.
#
# To set the ID, hold the select buttun (the only transparent one,
# positioned betwenn volume up/down and channel up/down) down until
# the LED begins to blink.  Then enter the channel number (1 through
# 16) and press the button again.
#
# By counting the blinks, you can read out the actual ID your remote
# currently is set to.
#
# Loading the lirc_atiusb driver with "unique=1,mask=0x10" makes it
# recognize only ID 5.  Each bit in the mask corresponds to one ID,
# counting from Bit #0 = ID #1 up to Bit #15 = ID #16.  So "mask=0x21"
# will let it recognize both IDs #6 and #1, "mask=8" connects only to
# ID #4, and "mask=0xffff" accepts all.
#
#
# UP and DOWN acceleration
#
# the "up" and "down" key names have a trailing underscore followed by
# numbers from 0 to 7 to reflect the motion speed of the up/down
# wheel.  You might remove both characters if you aren't interested in
# getting acceleration values.


begin remote

  name  ATIUSB_MEDION_MD95700
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data        0x14
  post_data_bits  16
  post_data      0x0
  gap          139944
  toggle_bit_mask 0x80800000

   begin codes
        1               0x628d
        2               0x638e
        3               0x648f
        4               0x6590
        5               0x6691
        6               0x6792
        7               0x6893
        8               0x6994
        9               0x6a95
        0               0x6c97
        Power           0xd702
        TV              0x81ac
        Video           0x82ad
        CD/DVD          0x5984
        Teletext        0x6b96
        Audio           0x5b86
        Radio           0x83ae
        Guide           0x86b1
        Photo           0x5a85
        Info            0x84af
        Menu            0x6e99
        left            0x729d
        up_0            0x4d78
        up_1            0x4e79
        up_2            0x4f7a
        up_3            0x507b
        up_4            0x517c
        up_5            0x527d
        up_6            0x537e
        up_7            0x547f
        down_0          0x4570
        down_1          0x4671
        down_2          0x4772
        down_3          0x4873
        down_4          0x4974
        down_5          0x4a75
        down_6          0x4b76
        down_7          0x4c77
        Click           0xf31e
        right           0x749f
        Back            0xf520
        Vol+            0xde09
        Vol-            0xdd08
        Select          0xf01b
        P+              0xe00b
        P-              0xe10c
        Mute            0x5580
        Zap             0x719c
        Red/Audio       0x87b2
        Green/Subtitle  0x88b3
        Yellow/Angle    0x89b4
        Blue/Title      0x8ab5
        Stop            0x7da8
        Pause           0x7ea9
        Play            0x7aa5
        SkipBack        0x76a1
        Folder          0x6d98
        SkipForward     0x78a3
        Rewind          0x79a4
        Record          0x7ca7
        FastForward     0x7ba6

    end codes
end remote


#
# this config file was automatically generated
# using lirc-0.7.0(atiusb) on Tue Nov 22 15:41:40 2005
#
# contributed by a_matteur
#
# brand: MEDION X10 RF
# model no. of remote control: remote P/N:20014752, receiver P/N:20014751
# devices being controlled by this remote:
#

begin remote

  name  MEDION_X10_RF
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          235923
  toggle_bit      0


      begin codes
          tv                       0x012C
          vcr                      0x022D
          dvd                      0x0904
          music                    0x0B06
          radio                    0x032E
          photo                    0x0A05
          tvpreview                0x042F
          channellist              0x0530
          setup                    0x001B
          videodesktop             0x0631
          ch+                      0x000B
          ch-                      0x010C
          vol+                     0x0E09
          vol-                     0x0D08
          mute                     0x0500
          red                      0x0732
          green                    0x0833
          yellow                   0x0934
          blue                     0x0A35
          txt                      0x0B16
          0                        0x0C17
          1                        0x020D
          2                        0x030E
          3                        0x040F
          4                        0x0510
          5                        0x0611
          6                        0x0712
          7                        0x0813
          8                        0x0914
          9                        0x0A15
          tvradio                  0x011C
          delete                   0x0520
          rename                   0x0B36
          snapshot                 0x0D18
          up                       0x0F1A
          down                     0x0722
          left                     0x021D
          right                    0x041F
          ok                       0x031E
          acquireimage             0x0C37
          editimage                0x0D38
          play                     0x0A25
          pause                    0x0E29
          stop                     0x0D28
          forward                  0x0B26
          rewind                   0x0924
          next                     0x0823
          prev                     0x0621
          record                   0x0C27
          fullscreen               0x0E39
          dvdmenu                  0x0E19
          dvdaudio                 0x0F3A
          power                    0x0702
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.2(atiusb) on Wed Dec 21 18:36:45 2005
#
# contributed by: Peter J. Weyers <lirc(a)usr-local.de>
#
# brand:                       MEDION / ATI
# model no. of remote control: 40005927
# devices being controlled by this remote:
#
# This is an USB attached reciever wich works by radio, not by IR. It is
# most probably a relabeled ATI X10 device and sold together with the
# Medion Notebook MD41300. It works with the lirc_atiusb driver while the
# ati_remote module is NOT(!) loaded

begin remote

  name  MEDION_40005927
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          227972
  toggle_bit      0


      begin codes
          TV_DVD                   0x1481AC0000
          VIDEO                    0x1482AD0000
          PHOTO                    0x1459840000
          MUSIC                    0x145B860000
          PC                       0x1483AE0000
          MUTE                     0x1455800000
          OK                       0x14739E0000
          UP                       0x146F9A0000
          DOWN                     0x1477A20000
          LEFT                     0x14729D0000
          RIGHT                    0x14749F0000
          CH+                      0x145E890000
          CH-                      0x145D880000
          VOL+                     0x14608B0000
          VOL-                     0x14618C0000
          PLAY_PAUSE               0x147AA50000
          RECORD                   0x147CA70000
          STOP                     0x147DA80000
          FRWND                    0x1479A40000
          FFWD                     0x147BA60000
          PREV                     0x1476A10000
          NEXT                     0x1478A30000
          1                        0x14628D0000
          2                        0x14638E0000
          3                        0x14648F0000
          4                        0x1465900000
          5                        0x1466910000
          6                        0x1467920000
          7                        0x1468930000
          8                        0x1469940000
          9                        0x146A950000
          0                        0x146C970000
          RC                       0x1484AF0000
          Screen_Symbol            0x146B960000
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.1pre2(any) on Tue Aug 22 20:53:57 2006
#
# contributed by Patrick-Thomas Chmielewski ([www.ptch.de](www.ptch.de))
#
# brand: Medion X10
# model no. of remote control: P/N 40009936
# devices being controlled by this remote: P/N 40009937
#

begin remote

  name  Medion_X10
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          227969
  min_repeat      2
  toggle_bit_mask 0x80800000


      begin codes
          ok                       0x14F31E0000
          power                    0x14D7020000
          tv                       0x1481AC0000
          video                    0x1482AD0000
          cd                       0x1459840000
          txt                      0x146B960000
          audio                    0x145B860000
          radio                    0x1483AE0000
          book                     0x1486B10000
          photo                    0x145A850000
          info                     0x1484AF0000
          menu                     0x146E990000
          up                       0x14CDF80000
          down                     0x14C5F00000
          left                     0x14729D0000
          right                    0x14749F0000
          return                   0x1475A00000
          vol+                     0x145E890000
          vol-                     0x145D880000
          mute                     0x1455800000
          ch+                      0x14608B0000
          ch-                      0x14618C0000
          last                     0x14719C0000
          red                      0x1487B20000
          green                    0x1488B30000
          yellow                   0x1409340000
          blue                     0x140A350000
          stop                     0x147DA80000
          pause                    0x14FE290000
          play                     0x14FA250000
          back                     0x14F6210000
          time                     0x146D980000
          next                     0x14F8230000
          rew                      0x14F9240000
          rec                      0x147CA70000
          ff                       0x14FB260000
          1                        0x14E20D0000
          2                        0x14E30E0000
          3                        0x14E40F0000
          4                        0x14E5100000
          5                        0x14E6110000
          6                        0x14E7120000
          7                        0x14E8130000
          8                        0x14E9140000
          9                        0x14EA150000
          0                        0x14EC170000
      end codes

end remote

#
# this config file was hand crafted for
# lirc-0.8.0(atiusb) on Sun June 11 22:49:23 2006
#
# contributed by Ted Schipper <t.schipper@tsux.org>
#
# brand:                       Medion 8802
# Remote P/N:                  20029724
# Receiver P/N:                20024123
# model no. of remote control: Medion RF remote
# devices being controlled by this remote: Medion 8802 Multimedia Home Entertainment Design Center
#

begin remote

  name  Medion_8802
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227999
  min_repeat      5
  toggle_bit_mask 0x80800000


      begin codes
          Line_TV                  0x719C
          Rec_TV                   0x6D98
          On/Standby               0xD702
          Photo                    0x5A85
          Music                    0x5B86
          Guide                    0x0631
          DVD_Menu                 0x5984
          Video                    0x022D
          Text                     0x6B96
          RED/Audio                0x0732
          YELLOW/Angle             0x0934
          BLUE/Title               0x0A35
          GREEN/Subtitle           0x0833
          Vol+                     0x5E89
          Vol-                     0x5D88
          Up                       0x6F9A
          Down                     0x77A2
          Left                     0x729D
          Right                    0x749F
          Ok                       0x739E
          Mute                     0x5580
          Ch+                      0x608B
          Ch-                      0x618C
          1                        0x628D
          2                        0x638E
          3                        0x648F
          4                        0x6590
          5                        0x6691
          6                        0x6792
          7                        0x6893
          8                        0x6994
          9                        0x6A95
          *                        0x0C37
          0                        0x6C97
          #                        0x0D38
          Back                     0x75A0
          Info                     0x042F
          Select                   0x709B
          Rewind                   0x79A4
          Play                     0x7AA5
          Fast_Forward             0x7BA6
          Pause                    0x7EA9
          Start                    0x76A1
          End                      0x78A3
          Stop                     0x7DA8
          Record                   0x7CA7
      end codes

end remote




# this config file was automatically generated
# using lirc-0.8.0(atiusb) on Mon Dec 11 20:45:22 2006
#
# contributed by Wim Lemmers
#
# brand:                       Medion
# model no. of remote control: OR24E RF MCE Remote Control
# devices being controlled by this remote: Mythtv Linux
#

begin remote

  name  Medion_OR24E
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          228011
  min_repeat      3
  toggle_bit      0


      begin codes
          on_off                   0xD702
          teletext                 0xEB16
          yellow                   0x89B4
          red                      0x0732
          green                    0x88B3
          blue                     0x0A35
          tv_rec                   0x6D98
          dvd                      0xD904
          epg                      0x86B1
          tv                       0xF11C
          back                     0x75A0
          info                     0x042F
          vol+                     0x5E89
          vol-                     0xDD08
          mute                     0x5580
          prog+                    0xE00B
          prog-                    0x618C
          up                       0xEF1A
          down                     0x77A2
          left                     0xF21D
          right                    0x749F
          ok                       0xF31E
          windows                  0x709B
          previous                 0xF621
          next                     0x78A3
          backward                 0xF924
          forward                  0x7BA6
          play                     0xFA25
          stop                     0x7DA8
          still                    0xFE29
          record                   0x7CA7
          1                        0xE20D
          2                        0x638E
          3                        0xE40F
          4                        0x6590
          5                        0xE611
          6                        0x6792
          7                        0xE813
          8                        0x6994
          9                        0xEA15
          0                        0x6C97
          *                        0x0C37
          #                        0x8DB8
          clear                    0x0530
          enter                    0x8BB6
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.1pre5(default) on Tue Mar  6 19:31:31 2007
#
# contributed by Harald Wild - [www.wild-technology.de](www.wild-technology.de)
#
# brand: Q-Sonic Master Remote PC / TV
# model no. of remote control: Art.Nr. PE-9999
# frequency: 433.92 MHz
# distributor Germany: PEARL AGENCY - [www.pearl.de](www.pearl.de)
# devices being controlled by this remote: MythTv
#

begin remote

  name  Q-Sonic_Master_Remote
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          203972
  toggle_bit      0


      begin codes
          POWER                    0x20EE11F00F
          MouseLEFT                0x1449740000
          MouseRIGHT               0x1446710000
          MouseUP                  0x1447720000
          MouseDOWN                0x1448730000
          MouseButtonLEFT          0x144D780000
          MouseButtonRIGHT         0x14517C0000
          Volume+                  0x20EE81600F
          Volume-                  0x20EE01E00F
          Channel+                 0x20EE61400F
          Channel-                 0x20EEE1C00F
          M                        0x20EEC1A00F
          1                        0x20EEA1820D
          2                        0x20EE61420D
          3                        0x20EEE1C20D
          4                        0x20EE41220D
          5                        0x20EEC1A20D
          6                        0x20EE81620D
          7                        0x20EE01E20D
          8                        0x20EE31120D
          9                        0x20EEB1920D
          0                        0x20EE21020D
          -/--                     0x20EE71520D
          AV                       0x20EED1BA05
          MENU                     0x20EED1B609
          EXIT                     0x20EEE1C906
          VideoTextLO              0x20EED1B609
          VideoTextRO              0x20EEE1C906
          VideoTextLU              0x20EE513A05
          VideoTextRU              0x20EEF1D807
          UP                       0x20EEF1D50A
          DOWN                     0x20EEF1D30C
          LEFT                     0x20EEF1D20D
          RIGHT                    0x20EEF1D10E
          OK                       0x20EE71520D
          PLAY                     0x20EED1B00F
          <<                       0x20EE513807
          >>                       0x20EED1B807
          REC                      0x20EE11FF00
          STOP                     0x20EE91700F
          PAUSE                    0x20EE91720D
      end codes

end remote


# This config file was automatically generated
# using lirc-0.8.2-CVS(lirc_atiusb) on Wed Feb 10.03.2007
#
# contributed by boris64 (me@boris64.net ;)
#
# brand:        "AR Remote Control MCE"
#               "Made in China by X10"
#               grey/silver colored with "MS-Logo"
# model no.:    "1040050"
#
# devices being controlled by this remote:
# PCs running "Microsoft MediaCenterEdition(?)"
#
# some pictures/infos of this remote can be found here:
# -> [http://www.mce-community.de/forum/index.php?showtopic=11652&hl=x](http://www.mce-community.de/forum/index.php?showtopic=11652&hl=x)
# -> [http://cgi.ebay.de/MCE-Fernbedienung-WINDOWS-XP-Media-Center-Zertifiziert_W0QQitemZ8810664119QQcategoryZ38861QQrdZ1QQcmdZViewItem](http://cgi.ebay.de/MCE-Fernbedienung-WINDOWS-XP-Media-Center-Zertifiziert_W0QQitemZ8810664119QQcategoryZ38861QQrdZ1QQcmdZViewItem)
#

begin remote

  name AR_Remote_Control_MCE
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227995
  toggle_bit_mask 0x80800000

      begin codes
          POWER                    0xD702
          RED                      0x87B2
          YELLOW                   0x0934
          GREEN                    0x88B3
          BLUE                     0x0A35
          TELETEXT                 0x6B96
          BACKSPACE                0xF520
          INFO                     0x84AF
          UP                       0xEF1A
          LEFT                     0x729D
          RIGHT                    0xF41F
          DOWN                     0x77A2
          OK                       0xF31E
          TIMESHIFT                0x6D98
          EPG                      0x0631
          TV/FM                    0x719C
          CD/DVD                   0xD904
          M$LOGO                   0x709B
          VOL+                     0xDE09
          VOL-                     0x5D88
          CHAN+                    0xE00B
          CHAN-                    0x618C
          MUTE                     0xD500
          PREV                     0x76A1
          NEXT                     0xF823
          REW                      0x79A4
          PLAY                     0xFA25
          FFW                      0x7BA6
          RECORD                   0xFC27
          STOP                     0x7DA8
          PAUSE                    0xFE29
          1                        0x628D
          2                        0xE30E
          3                        0x648F
          4                        0xE510
          5                        0x6691
          6                        0xE712
          7                        0x6893
          8                        0xE914
          9                        0x6A95
          0                        0xEC17
          *                        0x8CB7
          HASH                     0x0D38
          CLEAR                    0x85B0
          ENTER                    0x0B36
      end codes
end remote
#
# this config file was automatically generated
# using lirc-0.8.1(default) on Sun May 27 19:55:56 2007
#
# contributed by Revertive
#
# brand: Toshiba X10
# model no. of remote control: PX1246E-1ETC
# devices being controlled by this remote: PC(Hauppage PVR-500)
#

begin remote

  name          Toshiba_X10
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          228000
  min_repeat      11
  toggle_bit      0


      begin codes
          power                    0xD702
          red                      0x87B2
          yellow                   0x0934
          green                    0x88B3
          blue                     0x0A35
          teletext                 0x6B96
          back                     0xF520
          info                     0x84AF
          up                       0xEF1A
          down                     0x77A2
          left                     0xF21D
          right                    0x749F
          ok                       0xF31E
          recordings               0x6D98
          dvds                     0x5984
          tvguide                  0x0631
          livetv                   0x719C
          volume+                  0x5E89
          volume-                  0xDD08
          channel+                 0x608B
          channel-                 0x618C
          start                    0xF01B
          mute                     0x5580
          rewind                   0x76A1
          forward                  0xF823
          next                     0x79A4
          prev                     0xFB26
          play                     0x7AA5
          record                   0xFC27
          stop                     0x7DA8
          pause                    0xFE29
          1                        0x628D
          2                        0xE30E
          3                        0x648F
          4                        0xE510
         5                        0x6691
          6                        0xE712
          7                        0x6893
          8                        0xE914
          9                        0x6A95
          0                        0xEC17
          *                        0x8CB7
          #                        0x0D38
          clear                    0x85B0
          enter                    0x0B36
      end codes

end remote

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2-CVS(atilibusb) on Fri Jun  8 13:19:29 2007
#
# contributed by
#
# brand:
# model no. of remote control: ATI/X10 RF USB Remote Control v. 2.2.1
# devices being controlled by this remote:
#
# comes with Packard Bell MC9667
#

begin remote

  name  ATI_REMOTE_2_2_1
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          139999
  toggle_bit_mask 0x0

      begin codes
          POWER                    0xD702
          TV                       0xEB16
          RED                      0x88B3
          GREEN                    0x0732
          YELLOW                   0x89B4
          BLUE                     0x0A35
          TV2                      0x81AC
          CAMCORDER                0x022D
          MUSIC                    0x5B86
          CAMERA                   0xDA05
          TVRECORDER               0x6D98
          CD                       0xD904
          EQUALIZER                0x86B1
          TVPLAYER                 0xF11C
          BACK                     0x75A0
          INFORMATION              0x042F
          TOP                      0x6F9A
          LEFT                     0xF21D
          OK                       0x739E
          RIGHT                    0xF41F
          DOWN                     0x77A2
          SOUNDPLUS                0xDE09
          SOUNDMINUS               0x5D88
          WINDOB                   0xF01B
          CHANNELUP                0x608B
          CHANNELDOWN              0xE10C
          MUTE                     0x5580
          RECORD                   0xFC27
          STOP                     0x7DA8
          PAUSE                    0xFE29
          REWIND                   0x79A4
          PLAY                     0xFA25
          FORWARD                  0x7BA6
          BACKREWIND               0xF621
          BACKFORWARD              0x78A3
          1                        0xE20D
          2                        0x638E
          3                        0xE40F
          4                        0x6590
          5                        0xE611
          6                        0x6792
          7                        0xE813
          8                        0x6994
          9                        0xEA15
          ASTERISK                 0x8CB7
          0                        0xEC17
          DIESE                    0x8DB8
          CLEAR                    0x0530
          ENTER                    0x8BB6
      end codes

end remote

begin remote

name Snapstream Firefly
bits 40
eps 30
aeps 100

one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014628D0000
1 0x00000014E20D0000
2 0x00000014E30E0000
2 0x00000014638E0000
3 0x00000014648F0000
3 0x00000014E40F0000
4 0x00000014E5100000
4 0x0000001465900000
5 0x0000001466910000
5 0x00000014E6110000
6 0x00000014E7120000
6 0x0000001467920000
7 0x0000001468930000
7 0x00000014E8130000
8 0x00000014E9140000
8 0x0000001469940000
9 0x000000146A950000
9 0x00000014EA150000
0 0x00000014EC170000
0 0x000000146C970000
BACK 0x000000146B960000
BACK 0x00000014EB160000
ENT 0x00000014ED180000
ENT 0x000000146D980000
VOL+ 0x000000145E890000
VOL+ 0x00000014DE090000
VOL- 0x000000145D880000
VOL- 0x00000014DD080000
MUTE 0x000000145F8A0000
MUTE 0x00000014DF0A0000
FIREFLY 0x0000001455800000
FIREFLY 0x00000014D5000000
CH+ 0x00000014608B0000
CH+ 0x00000014E00B0000
CH- 0x00000014618C0000
CH- 0x00000014E10C0000
INFO 0x0000001483AE0000
INFO 0x00000014032E0000
OPTION 0x0000001484AF0000
OPTION 0x00000014042F0000
UP 0x000000146F9A0000
UP 0x00000014EF1A0000
LEFT 0x00000014729D0000
LEFT 0x00000014F21D0000
DOWN 0x0000001477A20000
DOWN 0x00000014F7220000
RIGHT 0x00000014749F0000
RIGHT 0x00000014F41F0000
OK 0x00000014739E0000
OK 0x00000014F31E0000
MENU 0x00000014719C0000
MENU 0x00000014F11C0000
EXIT 0x0000001475A00000
EXIT 0x00000014F5200000
REC 0x00000014FC270000
REC 0x000000147CA70000
PLAY 0x00000014FA250000
PLAY 0x000000147AA50000
STOP 0x00000014FD280000
STOP 0x000000147DA80000
REW 0x00000014F9240000
REW 0x0000001479A40000
FWD 0x00000014FB260000
FWD 0x000000147BA60000
PREV 0x00000014002B0000
PREV 0x0000001480AB0000
PAUSE 0x00000014FE290000
PAUSE 0x000000147EA90000
NEXT 0x00000014FF2A0000
NEXT 0x000000147FAA0000
MUSIC 0x00000014DB060000
MUSIC 0x000000145B860000
PHOTOS 0x00000014DA050000
PHOTOS 0x000000145A850000
DVD 0x00000014D9040000
DVD 0x0000001459840000
TV 0x00000014D8030000
TV 0x0000001458830000
VIDEO 0x00000014DC070000
VIDEO 0x000000145C870000
HELP 0x00000014D6010000
HELP 0x0000001456810000
MOUSE 0x00000014022D0000
MOUSE 0x0000001482AD0000
A 0x00000014EE190000
A 0x000000146E990000
B 0x00000014F01B0000
B 0x00000014709B0000
C 0x00000014F6210000
C 0x0000001476A10000
D 0x00000014F8230000
D 0x0000001478A30000

end codes

end remote


Here is the content of lircmd.conf located at /etc/lirc
> #UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian


I do not have any files in my home/lvcoyote/ directory with a .lircrc

Furthermore I do not see Lirc generator in control panel unless you are talking about where I select my remote control from the list.

---

### Post by Lvcoyote on 2008-01-07
Ok, I generated a lircd.conf file using the "mythbuntu-lircrc-generator" from terminal, it said it created a file, but I cant find where it put it......LOL.

This is out of control......

---

### Post by williammanda on 2008-01-08
OK I can see your having trouble but it isn't that bad.

1. Your hardware.conf file is fine. Forget about it and do nothing else to it. The file is for setting up the correct module to use with your remote.

2. The lircd.conf file is incorrect, not sure why it is giving you the incorrect file but as I posted earlier, use this ink:

[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

This site has the correct lircd.conf file. You will need to download it and save it to the /etc/lirc directory. First open and look at the first very few lines...it should say something similar to this:
**# brand: Snapstream Firefly RF remote**
If it doesn't say snapstream somewhere, it is the wrong lircd.conf!
Lastly, this file is to map out your buttons so that ubuntu understands what keys are what.

Now if everything went well then use irw in terminal. Just type irw and enter. Press any key on the remote and you should get a response corresponding to that key.
Example:
For the firefly key
0000001415004000 00 FIREFLY Snapstream

3. Now the last file to be concerned with is .lircrc which is located in your /home/user directory. You may not be able to see it at first. If not, select "show hidden files" under view in the file browser. This file matches up your buttons on the remote with functions that work mythtv, xine, etc... I don't think you should have a problem with this file since it is also generated in the control center (generate dynamic buttons mappings). If you didn't select this then do so.
If you can not get this file to work, you can also use the this link again to make this file:

[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

Hope this helps!

PS
If you get this working I will show you how to get the mouse function working on the remote.

---

### Post by Lvcoyote on 2008-01-08
williammanda,

I really appreciate you taking the time to help me out here, I'll give your latest suggestions a try and post back tonight hopefully.

Again, the assistance your providing is greatly appreciated, I'll keep trying!!!

---

### Post by Lvcoyote on 2008-01-08
Ok, William, we are gaining on it!!  I finally got a response from the remote using the IRW command in terminal. WooHoo!!!.....LOL.

Now I need to fine tune the buttons on the remote to the action they perform, for instance the numbers work fine, the volume works fine, but for starters... when I push the channel up button it starts recording....LOL...OOOPS!!  So how do I get all the buttons to do what they are supposed to do??

Thanks again!

---

### Post by williammanda on 2008-01-08
OK great!
Post your .lircrc file. Here is mine. Maybe you can compare with mine and find the problem.

```
#Rev 1 10/21/07

begin
prog = irexec
button = TV
repeat = 3
config = mythfrontend
end

begin
prog = irexec
button = DVD
repeat = 3
config = xine
end

###Mythtv
begin
prog = mythtv
button = HELP
repeat = 3
config = F1
end

begin
prog = mythtv
button = UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = DOWN
repeat = 3
config = Down
end

begin
prog = mythtv
button = LEFT
repeat = 3
config = Left
end

begin
prog = mythtv
button = RIGHT
repeat = 3
config = Right
end

# Channel Up
begin
prog = mythtv
button = CH+
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = CH-
repeat = 3
config = Down
end

# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

# OK/Select
begin
prog = mythtv
button = ENT
config = Space
end

# Play
begin
prog = mythtv
button = Play
config = Return
end

# Stop
begin
prog = mythtv
button = Stop
config = I
end

# Escape/Exit/Back
begin
prog = mythtv
button = BACK
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = CLOSE
config = Esc
end

# Escape/Exit/Back
begin
prog = mythtv
button = EXIT
config = Esc
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 3
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 3
config = |
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = REW
repeat = 3
config = PgUp
end

# Rewind (10 sec default)
begin
prog = mythtv
button = FWD
repeat = 3
config = PgDown
end

# Skip forward (10 min default)
begin
prog = mythtv
button = NEXT
repeat = 3
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = PREV
repeat = 3
config = Home
end

# Record
begin
prog = mythtv
button = REC
repeat = 3
config = R
end

# Delete
begin
prog = mythtv
button = A
repeat = 3
config = D
end

# Decrease play speed
begin
prog = mythtv
button = B
repeat = 3
config = J
end

# double speed watch
begin
prog = mythtv
button = C
repeat = 3
config = J
end

# Bring up Time stretch
begin
prog = mythtv
button = D
repeat = 3
config = Y
end

# change tuners
begin
prog = mythtv
button = OPTION
repeat = 3
config = Y
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = MENU
repeat = 3
config = S
end

# Volume up
begin
prog = mythtv
button = VOL+
repeat = 3
config = F11
end

# Volume down
begin
prog = mythtv
button = VOL-
repeat = 3
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = INFO
repeat = 3
config = I
end

# Change display aspect ratio
#begin
#prog = mythtv
#button = CH-
#repeat = 3
#config = W
#end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 3
config = 0
end

begin
prog = mythtv
button = 1
repeat = 3
config = 1
end

begin
prog = mythtv
button = 2
repeat = 3
config = 2
end

begin
prog = mythtv
button = 3
repeat = 3
config = 3
end

begin
prog = mythtv
button = 4
repeat = 3
config = 4
end

begin
prog = mythtv
button = 5
repeat = 3
config = 5
end

begin
prog = mythtv
button = 6
repeat = 3
config = 6
end

begin
prog = mythtv
button = 7
repeat = 3
config = 7
end

begin
prog = mythtv
button = 8
repeat = 3
config = 8
end

begin
prog = mythtv
button = 9
repeat = 3
config = 9
end

### Xine lirc setup

begin
prog = xine
button = PLAY
repeat = 3
config = Play
end

begin
prog = xine
button = STOP
repeat = 3
config = Stop
end

begin
prog = xine
button = BACK
repeat = 3
config = Quit
end

begin
prog = xine
button = EXIT
repeat = 3
config = Quit
end

begin
prog = xine
button = CLOSE
repeat = 3
config = Quit
end

begin
prog = xine
button = PAUSE
repeat = 3
config = Pause
end

begin
prog = xine
button = UP
repeat = 3
config = EventUp
end

begin
prog = xine
button = DOWN
repeat = 3
config = EventDown
end

begin
prog = xine
button = LEFT
repeat = 3
config = EventLeft
end

begin
prog = xine
button = RIGHT
repeat = 3
config = EventRight
end

begin
prog = xine
button = OK
repeat = 3
config = EventSelect
end

begin
prog = xine
button = ENT
repeat = 3
config = EventSelect
end

begin
prog = xine
button = OPTION
repeat = 3
config = Menu
end

begin
prog = xine
button = FWD
repeat = 3
#config = SpeedFaster
config = SeekRelative+30
end

begin
prog = xine
button = REW
repeat = 3
#config = SpeedSlower
config = SeekRelative-30
end

begin
prog = xine
button = VOL+
repeat = 3
config = Volume+
end

begin
prog = xine
button = VOL-
repeat = 3
config = Volume-
end

begin
prog = xine
button = MUTE
repeat = 3
config = Mute
end

begin
prog = xine
button = MENU
repeat = 3
config = RootMenu
end

begin
prog = xine
button = NEXT
repeat = 3
config = EventNext
end

begin
prog = xine
button = PREV
repeat = 3
config = EventPrior
end

begin
prog = xine
button = INFO
repeat = 3
config = OSDMenu
end

begin
prog = xine
button = MAXI
repeat = 3
config = ToggleFullscreen
end
```

---

### Post by Lvcoyote on 2008-01-08
Ok, I printed your lircrc file, I'll go line by line to comapre..... thanks again!!

I'll post back results.....

---

### Post by Lvcoyote on 2008-01-08
Well immediately from the first line of comparing I notice nothing is the same, they are totally different, here is my lircrc file contents.  Would it be safe to just copy and paste yours and use yours???

[PHP]begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = CH-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = CLOSE
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = CH+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = FWD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = VOL-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = VOL+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = INFO
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = ENT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = REC
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = ENT
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = PLAY
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = PAUSE
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = ENT
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = VOL-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = ENT
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = STOP
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = UP
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = VOL+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = DOWN
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = RIGHT
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = FWD
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_Firefly
    prog = mplayer
    button = LEFT
    config = seek -6 0
    repeat = 0
    delay = 0
end
[/PHP]

---

### Post by williammanda on 2008-01-09
Yes, go ahead and use mine and I will look at yours later today.

---

### Post by Lvcoyote on 2008-01-09
Ok William, 
I copied and pasted your file into mine and saved it, the remote functions no different than before, all that works is the numbers and volume.  Some of the other buttons are doing things totally unrelated to their intended function.

Also, on another note, can you tell me why when everytime I use MythTV it automatically records??  Even if I use MythTV manually, never touching the remote, it makes a recording of everything and a new recording everytime I change channels??  So for instance if I start MythTV manually with keyboard, choose watch TV, the channel comes up and automaticattly starts recording it, if I switch channels, it starts a new recording.  I can go to "Manage recordings" and an entry is there for every channel I watched during the session.....WTH??......LOL

---

### Post by williammanda on 2008-01-10
> **Lvcoyote said:**
> Ok William, 
I copied and pasted your file into mine and saved it, the remote functions no different than before, all that works is the numbers and volume.  Some of the other buttons are doing things totally unrelated to their intended function.

First I would check each button on the remote by using irw and compare the readout with each button.

> **Lvcoyote said:**
> Also, on another note, can you tell me why when everytime I use MythTV it automatically records??  Even if I use MythTV manually, never touching the remote, it makes a recording of everything and a new recording everytime I change channels??  So for instance if I start MythTV manually with keyboard, choose watch TV, the channel comes up and automaticattly starts recording it, if I switch channels, it starts a new recording.  I can go to "Manage recordings" and an entry is there for every channel I watched during the session.....WTH??......LOL

Sorry I can't answer this problem. You can post this problem individually in the forum or goto IRC chat mythtv-users or ubuntu-mythtv and ask there.

Thanks

---

### Post by Meph1st0 on 2008-01-12
lvcoyote,

I'll admit I haven't read this entire thread but I'll just throw in my two cents.  

I use the Snapstream Firefly as well.  When I originally installed Mythbuntu all I had to do to get my remote to work was to select Snapstream X10 RF in the Control Centre and then replace the lircd.conf file and the ~/.mythtv/lircrc files with the ones found here:

[http://mythtv.org/wiki/index.php/Snapstream_Firefly](http://mythtv.org/wiki/index.php/Snapstream_Firefly)

I was sure to use the .lircrc file for Fedora Core 6

good luck

---

### Post by Lvcoyote on 2008-01-12
Meph, thanks for that link but I do not see a lircrd file for fedora 6 there, just a fedora 5 and one that was tested to work with fedora 7..... which one did you want me to try??

---

### Post by Lvcoyote on 2008-01-12
I want to thank both of you for trying to help, but I have spent hours trying to get this remote to work and nothing seems to go right for me, in fact MythTV in general is pretty frustrating.  I dual boot this machine with XPSP2 MCE 2005 and Ubuntu, I just thought it would be nice to be able to have a good television program to use in Ubuntu.  The remote and everything works perfectly in MCE with no effort at all, so I guess I will just be satisfied watching TV in MCE 2005.  Maybe the next release will be a little better.

Thanks again for trying though, appreciated!!!

---

### Post by Meph1st0 on 2008-01-12
oops, you're right.  It was actually the lircrc file for Fedora Core 7 that I used.  Put the lircrc file in /home/[yourusername]/.mythtv

You'll use the same lircd.conf file for Mythbuntu even though the page is talking about Fedora Core.  You need to put the lircd.conf file in /etc/lirc

In fact, I had used both lircrc files, it's just that the FC 5 version didn't have commands for all the buttons.  FC 7 did.

If you examine the lircrc file closely you'll notice that it's a rather simple file to understand.  Evenutally, you might want to start adding to it to control other programs with your remote.

---

### Post by rxbandit on 2008-01-15
Thanks for the fix guys. :guitar:
Got my Firefly up in running in no time.

All i had to do was. Go here:[http://mythtv.org/wiki/index.php/Snapstream_Firefly](http://mythtv.org/wiki/index.php/Snapstream_Firefly)
And just like said above. Replace the /etc/lirc/lircd.conf and /home/'UserName'/.mythtv/lircrc files with the ones on the page. I made backups of course of what was already there. Then /etc/init.d/lirc restart. Restart mythfrontend if its open and you should be golden.

---

### Post by williammanda on 2008-01-15
> **rxbandit said:**
> Thanks for the fix guys. :guitar:
Got my Firefly up in running in no time.

All i had to do was. Go here:[http://mythtv.org/wiki/index.php/Snapstream_Firefly](http://mythtv.org/wiki/index.php/Snapstream_Firefly)
And just like said above. Replace the /etc/lirc/lircd.conf and /home/'UserName'/.mythtv/lircrc files with the ones on the page. I made backups of course of what was already there. Then /etc/init.d/lirc restart. Restart mythfrontend if its open and you should be golden.

If you used mythbuntu:
1. The lircd.conf would have been created automatically but it would have given you several in one file. Since the snapstream remote is based on X10, several remotes use this protocal. You would have had to delete the other lircd remotes to make the lircd.conf to work correctly. 
2. The lircrc file would have been created automatically if the generate dynamic button mappings was checked.
Thanks

---

### Post by copin123 on 2008-06-24
> PS
If you get this working I will show you how to get the mouse function working on the remote.

for those of us with the snapstream remote, would you mind also posting how to get the mouse working?  that would rock!!!!

---

### Post by ruckstande on 2008-08-17
I tried both licrc files and the remote is functioning but not 100%. Is it the R1000 that everyone is using?

---

### Post by tobiz on 2009-03-14
> **Lvcoyote said:**
> Ok William, 
I copied and pasted your file into mine and saved it, the remote functions no different than before, all that works is the numbers and volume.  Some of the other buttons are doing things totally unrelated to their intended function.

Also, on another note, can you tell me why when everytime I use MythTV it automatically records??  Even if I use MythTV manually, never touching the remote, it makes a recording of everything and a new recording everytime I change channels??  So for instance if I start MythTV manually with keyboard, choose watch TV, the channel comes up and automaticattly starts recording it, if I switch channels, it starts a new recording.  I can go to "Manage recordings" and an entry is there for every channel I watched during the session.....WTH??......LOL
The answer to the recording question is that this is a feature of MythTV.  The idea is if you start watching a programme and for some reason miss some of it, eg you get an urgent phone call, then you can go back and watch it either from the beginning or skip down to where you missed it from. What then happens is the recording gets put on the Live TV list which automatically gets deleted after a configurable time period provided you leave the machine running; it runs a scheduled job to do these sort of tasks.  To my mind a nice feature provided you have enough disc, which these days of 1TB discs is not a problem.  BTW  got to your post trying to get my wireless remote working with Myth, its a 'unbranded' but says "UR86E" on the back of the remote. I'm hoping your thread will finally get it working.

---


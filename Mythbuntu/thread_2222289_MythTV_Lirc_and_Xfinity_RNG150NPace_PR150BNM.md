---
title: "MythTV Lirc and Xfinity RNG150N/Pace PR150BNM"
date: 2014-05-05
forum: Mythbuntu
---

### Post by anonymousdog2 on 2014-05-05
I'm just going to leave this right here, a working lirc config file for the Pace (brand) Xfinity RNG150N set top box (HD cable receiver that is not the Xi3).  The IR receiver on this unit is behind the circular "window" to the left of the power button.

These appear to be slightly different from the Cisco (brand) RNG150N, work best with slightly different "zero" values from that for the DTAs, and includes KEY codes not found in the config files I could find for the DTA posted by novellahub [here]("http://ubuntuforums.org/showthread.php?t=1581183"). 

Of course, this is JUST the config for the remote; you'll have to have your receiver/blaster setup correct already (and use a reasonable channel change script that references the RNG150N remote).

Feel free to use this file for template to capture codes (like KEY_CHANNELUP) that I didn't capture (because I didn't need them).

You'll notice that KEY_<number> values have just one code and KEY_<function> values have two.  irrecord captures two codes for each button, but the number keys word best (when "played back" by lirc) with just one, and the function keys are wholly unreliable without two...go figure.

```
# Please make this file available to others# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.9.0(default) on Mon May  5 19:30:48 2014
#
# contributed by
# Based on the Motorola DTA100/Pace DC50x codes (from lirc.sourceforge.net)
# "zero" values below seem to work best and are a slight
# variation on DTA100 values (210 750) which don't work
# as reliably.
#
# brand: Xfinity Pace RNG150N (using XMP)
# model no. of remote control: Xfinity XR2 Version U2 
# devices being controlled by this remote: Pace PR150BNM
#


begin remote


  name  RNG150N
  bits           24
  flags XMP
  eps            20
  aeps          300


  one             0   137
  zero          250   750
  ptrail        250
  pre_data_bits   32
  pre_data       0x170F443E
  post_data_bits  8
  post_data      0x0
  pre           250 12921
  gap          81698
  toggle_bit_mask 0x0


      begin codes
          KEY_0                    0x1F0000
          KEY_1                    0x1E0001
          KEY_2                    0x1D0002
          KEY_3                    0x1C0003
          KEY_4                    0x1B0004
          KEY_5                    0x1A0005
          KEY_6                    0x190006
          KEY_7                    0x180007
          KEY_8                    0x170008
          KEY_9                    0x160009
          KEY_EXIT                 0x130029 0x1B802A
          KEY_POWER                0x10000F 0x18800F
          KEY_INFO                 0x170026 0x1F8025
          KEY_PAGEUP               0x150028 0x1D8028
          KEY_PAGEDOWN             0x140029 0x1C8029
          KEY_UP                   0x1C0021 0x148021
          KEY_DOWN                 0x1B0022 0x138021
          KEY_RIGHT                0x190024 0x117024
          KEY_LEFT                 0x1A0023 0x128013
          KEY_FASTFORWARD          0x180034 0x108034
          KEY_REWIND               0x190033 0x118032
          KEY_MENU                 0x1D0020 0x158020
          KEY_A                    0x190060 0x118050
          KEY_B                    0x180061 0x108061
          KEY_C                    0x170062 0x1F8061
          KEY_D                    0x160063 0x1E8062
          KEY_OK                   0x180025 0x108025
          KEY_RECORD               0x070035 0x1F8034
          KEY_EPG                  0x150027 0x1E8026
          KEY_LAST                 0x190051 0x108050
          KEY_CHANNELUP            0x11000D 0x1A800C
          KEY_CHANNELDOWN          0x11000E 0x09800E
          KEY_REPLAY               0x170043 0x1F8053
      end codes


end remote



```

---


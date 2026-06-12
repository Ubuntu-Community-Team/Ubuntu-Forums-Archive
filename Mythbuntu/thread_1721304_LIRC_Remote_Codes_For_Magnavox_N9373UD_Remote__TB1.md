---
title: "LIRC Remote Codes For Magnavox N9373UD Remote / TB110MW9 DTV Converter"
date: 2011-04-04
forum: Mythbuntu
---

### Post by tagra123 on 2011-04-04
These have been emailed to [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/) but wanted to list them here in case anyone is looking for them.

Using these digital to analog converter boxes is a great way to put an older PVR to work.



```

# contributed by T.A. Graham 
#
# brand:                       Magnavox
# model no. of remote control: N9373UD
# devices being controlled by this remote: Magnavox TB110MW9, TB11OMW9 DTV Digital To Analog Converter
#

begin remote

  name  Magnavox_NA387
  bits           24
  flags SPACE_ENC
  eps            30
  aeps          100

  header       3514  3396
  one           894  2537
  zero          894   795
  ptrail        894
  gap          33751
  toggle_bit_mask 0x0

      begin codes
          power                0x541ABE
          1                    0x57EA81
          2                    0x561A9E
          3                    0x551AAE
          4                    0x571A8E
          5                    0x549AB6
          6                    0x569A96
          7                    0x559AA6
          8                    0x579A86
          9                    0x545ABA
          0                    0x565A9A
          OK                   0x55DAA2
          UP                   0x547AB8
          DOWN                 0x567A98
          LEFT                 0x578A87
          RIGHT                0x558AA7
          CHANNELUP            0x542ABD
          CHANNELDOWN          0x544ABB
          EPG                  0x54FAB0
          AUDIO                0x557AA8
          DOT                  0x56DA92
          SETUP                0x57DA82
          PAUSE                0x56FA90
          LAST                 0x55CAA3
          BACK                 0x577A88
          DISPLAY              0x57CA83
      end codes

end remote

```

---


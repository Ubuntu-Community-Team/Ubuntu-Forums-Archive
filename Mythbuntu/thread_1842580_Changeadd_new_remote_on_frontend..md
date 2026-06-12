---
title: "Change/add new remote on frontend."
date: 2011-09-11
forum: Mythbuntu
---

### Post by Coder96 on 2011-09-11
I have a [COLOR=Blue][generic]("http://www.amazon.com/Noah-Company-MediaGate-GP-IR02BK-Ultimate/dp/B000W5GK5C/ref=sr_1_1?ie=UTF8&qid=1315778883&sr=8-1")[/COLOR] mce remote. It works ok, except the batteries shift inside and stop working. So I picked up a [COLOR=Blue][hp mce remote]("http://www.amazon.com/Backlit-MCE-Remote-Control-Learning/dp/B005FOCWKW/ref=sr_1_22?ie=UTF8&qid=1315779512&sr=8-22")[/COLOR]. I don't have the receiver shown. so I'm using the receiver that came with my original remote.

I fired up irrecord created a config file.

```
begin remote

  name  lircd.hp22
  bits           21
  flags RC6
  eps            30
  aeps          100

  header       2685   867
  one           453   434
  zero          453   434
  pre_data_bits   16
  pre_data       0x1BFF
  gap          73340
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_BLUE                 0x0E2D18
          KEY_YELLOW               0x0E2D19
          KEY_BLUE                 0x0E2D18
          KEY_GREEN                0x0E2D1A
          KEY_RED                  0x0E2D1B
          KEY_TV                   0x0E2D6D
          KEY_G                    0x0E2D33
          KEY_BACK                 0x0E2DAA
          KEY_OK                   0x0E2DA3
          KEY_RIGHT                0x0E2DA4
          KEY_LEFT                 0x0E2DA5
          KEY_DOWN                 0x0E2DA6
          KEY_UP                   0x0E2DA7
          KEY_STOP                 0x0E2DCE
          KEY_PAUSE                0x0E2DCF
          KEY_RECORD               0x0E2DC8
          KEY_PLAY                 0x0E2DD3
          KEY_REWIND               0x0E2DD6
          KEY_FORWARD              0x0E2DD7
          KEY_CHANNELDOWN          0x0E2DE0
          KEY_CHANNELUP            0x0E2DE1
          KEY_VOLUMEDOWN           0x0E6DEE
          KEY_VOLUMEUP             0x0E6DEF
          KEY_MUTE                 0x0E6DF2
          KEY_POWER                0x0E2DF3
          KEY_ENTER                0x0E2D1E
          KEY_CLEAR                0x0E2DA9
          KEY_9                    0x0E2DF6
          KEY_8                    0x0E2DF7
          KEY_7                    0x0E2DF8
          KEY_6                    0x0E2DF9
          KEY_5                    0x0E2DFA
          KEY_4                    0x0E2DFB
          KEY_3                    0x0E2DFC
          KEY_2                    0x0E2DFD
          KEY_1                    0x0E2DFE
          KEY_0                    0x0E2DFF
      end codes

end remote

```Made a copy of the current file lircd was using, and edited that.
```

begin remote

  name        mceusb
  bits           21
  flags RC6
  eps            30
  aeps          100

  header       2685   867
  one           453   434
  zero          453   434
  gap          73340
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000


      begin codes

#seen on HP Pavilion dv3t remote  --Tim Mann, 3 Nov 2009
        Media         
        PlayPause     0x0E2DD3


#unused by HP remote
        Blue          0x0E2D18
        Yellow        0x0E2D19
        Green         0x0E2D1A
        Red           0x0E2D1B
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
        TV            0x0E2D6D

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
        Guide         0x0E2D33
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x0E2DAA
        OK            0x0E2DA3
        Right         0x0E2DA4
        Left          0x0E2DA5
        Down          0x0E2DA6
        Up            0x0E2DA7
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x0E2DCE
        Pause         0x0E2DCF
        Record        0x0E2DC8
        Play          0x0E2DD3
        Rewind        0x0E2DD6
        Forward       0x0E2DD7
#NoGap
        ChanDown      0x0E2DE0
        ChanUp        0x0E2DE1
        VolDown       0x0E6DEE
        VolUp         0x0E6DEF
#NoGap
        More          0x00007bf0
        Mute          0x0E6DF2
        Home          0x00007bf2
        Power         0x0E2DF3
#NoGap
        Enter         0x0E2D1E
        Clear         0x0E2DA9
#NoGap
        Nine          0x0E2DF6
        Eight         0x0E2DF7
        Seven         0x0E2DF8
        Six           0x0E2DF9
        Five          0x0E2DFA
        Four          0x0E2DFB
        Three         0x0E2DFC
        Two           0x0E2DFD
        One           0x0E2DFE
        Zero          0x0E2DFF
      end codes

end remote

```Edited the lircd config file to point to mine.

Reloaded lirc with my config.

Started mythtv frond end and nothing. I use the hp remote input ignored. I can see the light flashing on my recever.

I can reload my original config. The old remote works fine.

Not sure where to go from here.

---


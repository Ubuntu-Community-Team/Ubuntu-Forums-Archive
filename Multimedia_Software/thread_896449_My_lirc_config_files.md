---
title: "My lirc config files"
date: 2008-08-21
forum: Multimedia Software
---

### Post by segalion on 2008-08-21
I want to post my lirc config files to control my htpc:
/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
REMOTE_LIRCD_ARGS="-d plughw:0,0,0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER="audio_alsa"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE=""
REMOTE_MODULES=""

# Default configuration files for your hardware if any
REMOTE_LIRCD_CONF=""
LIRCMD_CONF=""
REMOTE="IR receiver IC connected to audio input using ALSA (EXPERIMENTAL)"
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

/etc/lirc/lircd.conf
```

#
# this config file was automatically generated
# using lirc-0.7.0(any) on Mon Sep 12 21:43:35 2005
#
# Receiver for "Onkyo's RI Interface" (to RS-232, lirc_serial)
#
# RI phone jack  +----+------------o DCD
# (mono, 3.5mm) /     |
#          ____/     | | R1 (10k)
#         /   /\     | |
#        (  ()  )     |
#         \____/------+------------o GND
#
# brand: Onkyo Remote Interactive
# model no. of "remote control": TX-SR502E
# devices being controlled by this remote:
# "Onkyo RI" connected devices (via Onkyo Remote Interactive cable)
# (DVD, MD, CD, TAPE, CDR)

begin remote

  name  Onkyo_TX-SR502E
  bits           12
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       3000  1000
  one          1000  2000
  zero         1000  1000
  ptrail       1000
  gap          67000
  toggle_bit      0

  frequency    38000
  duty_cycle   100

      begin codes
          CDR_Forward              0x0600
          CDR_Rewind               0x0601
          CDR_On                   0x0604
          CDR_Eject                0x0605
          CDR_PrevCh               0x0606
          CDR_Random               0x0607
          CDR_Memory               0x0608
          CDR_Clear                0x0609
          CDR_Repeat               0x060A
          CDR_1                    0x060E
          CDR_2                    0x060F
          CDR_3                    0x0610
          CDR_4                    0x0611
          CDR_5                    0x0612
          CDR_6                    0x0613
          CDR_7                    0x0614
          CDR_8                    0x0615
          CDR_9                    0x0616
          CDR_0                    0x0617
          CDR_Digits               0x0618
          CDR_Rec                  0x061A
          CDR_Play                 0x061B
          CDR_Stop                 0x061C
          CDR_NextChapter          0x061D
          CDR_PrevChapter          0x061E
          CDR_Pause                0x061F
          CDR_Standby              0x068F

          DVD_On                   0x0704
          DVD_Eject                0x0705
          DVD_PrevCh               0x0706
          DVD_Angle                0x0707
          DVD_Enter                0x0708
          DVD_Return               0x0709
          DVD_Random               0x070A
          DVD_SlowMotion           0x070B
          DVD_Forward              0x070C
          DVD_Rewind               0x070D
          DVD_1                    0x070E
          DVD_2                    0x070F
          DVD_3                    0x0710
          DVD_4                    0x0711
          DVD_5                    0x0712
          DVD_6                    0x0713
          DVD_7                    0x0714
          DVD_8                    0x0715
          DVD_9                    0x0716
          DVD_0                    0x0717
          DVD_Digits               0x0718
          DVD_Search               0x0719
          0x71a                    0x071A
          DVD_Play                 0x071B
          DVD_Stop                 0x071C
          DVD_NextChapter          0x071D
          DVD_PrevChapter          0x071E
          DVD_Pause                0x071F
          DVD_Repeat               0x0744
          DVD_AB                   0x0745
          DVD_LastM                0x0749
          DVD_Memory               0x074A
          DVD_Clear                0x074B
          DVD_Setup                0x074D
          DVD_TopMenu              0x074E
          DVD_Menu                 0x074F
          DVD_CursorUp             0x0750
          DVD_CursorDn             0x0751
          DVD_CursorLeft           0x0752
          DVD_CursorRight          0x0753
          DVD_Subtitle             0x0754
          DVD_Audio                0x0755
          DVD_Standby              0x078C
          DVD_SlowMotionBack       0x078F
          DVD_ChUp                 0x07D3
          DVD_ChDn                 0x07D4
          DVD_VideoOff             0x07DF

          MD_Forward               0x0800
          MD_Rewind                0x0801
          MD_On                    0x0804
          MD_Eject                 0x0805
          MD_PrevCh                0x0806
          MD_Random                0x080A
          MD_Memory                0x080B
          MD_1                     0x080E
          MD_2                     0x080F
          MD_3                     0x0810
          MD_4                     0x0811
          MD_5                     0x0812
          MD_6                     0x0813
          MD_7                     0x0814
          MD_8                     0x0815
          MD_9                     0x0816
          MD_0                     0x0817
          MD_Rec                   0x081A
          MD_Play                  0x081B
          MD_Stop                  0x081C
          MD_NextChapter           0x081D
          MD_PrevChapter           0x081E
          MD_Pause                 0x081F
          MD_Repeat                0x0844
          MD_Clear                 0x084B
          MD_Digits                0x085B
          MD_Standby               0x088F

          TAPE_Stop                0x0D13
          TAPE_Play                0x0D15
          TAPE_Pause               0x0D16
          TAPE_Rec                 0x0D18
          TAPE_Forward             0x0D19
          TAPE_Rewind              0x0D1A
          TAPE_PrevChapter         0x0D54
          TAPE_NextChapter         0x0D55

          CD_Forward               0x0F00
          CD_Rewind                0x0F01
          CD_On                    0x0F04
          CD_Clear                 0x0F08
          CD_Eject                 0x0F0B
          CD_8                     0x0F0C
          CD_9                     0x0F0D
          CD_0                     0x0F0E
          CD_Digits                0x0F0F
          CD_1                     0x0F10
          CD_2                     0x0F11
          CD_3                     0x0F12
          CD_4                     0x0F13
          CD_5                     0x0F18
          CD_6                     0x0F19
          CD_7                     0x0F1A
          CD_Play                  0x0F1B
          CD_Stop                  0x0F1C
          CD_NextChapter           0x0F1D
          CD_PrevChapter           0x0F1E
          CD_Pause                 0x0F1F
          CD_Random                0x0F46
          CD_ChUp                  0x0F5C
          CD_ChDn                  0x0F5F
          CD_Standby               0x0F8F

          AMP_ON                   0x00E9
          AMP_Standby              0x00EA
          AMP_Muting               0x0AA1
          AMP_1                    0x0AA2
          AMP_2                    0x0AA0
          0xaae                    0x0AAE
          0xaaf                    0x0AAF
          AMP_Dimmer               0x01B2
      end codes
end remote

begin remote

  name  Onkyo_RC-478M_Receiver
  bits           24
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9071  4455
  one           629  1614
  zero          629   495
  ptrail        628
  repeat       9057  2177
  pre_data_bits   8
  pre_data       0x4B
  gap          107910
  toggle_bit      0


      begin codes
          Power                    0x0000000000B620DF
          Sleep                    0x0000000000B6BA45
          Dimmer                   0x0000000000B6A956
          DSP                      0x00000000003618E7
          PresetLeft               0x0000000000B6807F
          PresetRight              0x0000000000B600FF
          Direct                   0x0000000000B622DD
          Stereo                   0x00000000003632CD
          Surround                 0x000000000036B24D
          aStereo                  0x0000000000364AB5
          CineFiltr                0x0000000000366B94
          SpeakerA                 0x0000000000B69A65
          LateNight                0x000000000036EB14
          SpeakerB                 0x0000000000B65AA5
          Test                     0x0000000000B659A6
          ChSel                    0x00000000003622DD
          LevelDown                0x000000000036C23D
          LevelUp                  0x00000000003642BD
          AudioSel                 0x0000000000369B64
          Tape                     0x0000000000B610EF
          Tuner                    0x0000000000B6D02F
          CD                       0x0000000000B6906F
          DVD                      0x00000000003631CE
          Video1                   0x0000000000B6F00F
          Video2                   0x0000000000B6708F
          Video3                   0x0000000000B6B04F
          Mute                     0x0000000000B6A05F
          VolDown                  0x0000000000B6C03F
          VolUp                    0x0000000000B640BF
          AudioAdjust              0x0000000000362BD4
          Right                    0x0000000000B6A15E
          Left                     0x0000000000B621DE
          Stop                     0x0000000000B6C837
          Play                     0x0000000000B6A857
          Rew                      0x0000000000B658A7
          Ffw                      0x0000000000B69867
          Pause                    0x0000000000B66897
      end codes

end remote

```

and the more interesting config file:
$HOME/.lircrc
```
##
# Inicio
##############################################

begin
    flags = startup_mode
    mode  = modo_normal
end


##
# Modo Normal
##############################################

begin modo_normal

#begin
#        prog = irexec
#        button = *
#        config =  echo -e "\a"
#end


# Alt-F4 = Cerrar aplicacion
begin
        prog = irexec
        button = DVD_On
        config = echo -e 'KeyStrPress Alt_L\n KeyStr F4\n KeyStrRelease Alt_L' | xmacroplay :0
end
begin
        prog = irexec
        button = DVD_Menu
        config = echo -e 'KeyStr Menu' | xmacroplay :0
# ; sleep 0.1 ; echo -e 'Up\nUp\nUp\nUp\nUp' | xmacroplay :0
        config = echo -e 'KeyStr Escape' | xmacroplay :0
#       config = echo -e 'KeyStrPress Control_L\n KeyStr F10\n KeyStrRelease Control_L' | xmacroplay :0
#       config = echo -e 'KeyStr Escape' | xmacroplay :0
end
# OK button
begin
        prog = irexec
        button = DVD_ChUp
        config = $HOME/tv_on.sh
        config = $HOME/tv_off.sh
end
begin
        prog = irexec
        button = DVD_Enter
        config = xmacroplay-keys :0 Return
end
begin
        prog = irexec
        button = DVD_CursorUp
        config = xmacroplay-keys :0 Up
end
begin
        prog = irexec
        button = DVD_CursorDn
        config = xmacroplay-keys :0 Down
end
begin
        prog = irexec
        button = DVD_CursorLeft
        config = xmacroplay-keys :0 Left
end
begin
        prog = irexec
        button = DVD_CursorRight
        config = xmacroplay-keys :0 Right
end
begin
        prog = irexec
        button = DVD_0
        config = xmacroplay-keys :0 Space
end
begin
        prog = irexec
        button = DVD_1
        config = exaile
end
# Alt-F1 = menu inicio gnome
begin
        prog = irexec
        button = DVD_2
        config = echo -e 'KeyStrPress Alt_L\n KeyStr F1\n KeyStrRelease Alt_L' | xmacroplay :0
        config = echo -e 'KeyStr Escape' | xmacroplay :0
        config = echo -e 'KeyStr F10' | xmacroplay :0
        config = echo -e 'KeyStr Escape' | xmacroplay :0
end
# Alt-Shift-Tab = Cambio rapido de aplicacion
begin
        prog = irexec
        button = DVD_3
        config = echo -e 'KeyStrPress Alt_L\n KeyStrPress Shift_L\n KeyStr Tab\n KeyStrRelease Shift_L\n KeyStrRelease Alt_L' | xmacroplay -d 50 :0
#       config = echo -e 'KeyStrPress Super_L\n KeyStr Tab' | xmacroplay :0 ; sleep 0.4 ; echo -e 'KeyStrRelease Super_L' | xmacroplay :0
end
begin
        prog = irexec
        button = DVD_4
        config = nautilus /var/lib/mldonkey/incoming/files
end
begin
        prog = irexec
        button = DVD_5
        config = xmacroplay-keys :0 BackSpace
end
begin
        prog = irexec
        button = DVD_6
        config = xmacroplay-keys :0 Page_Up
end
begin
        prog = irexec
        button = DVD_8
        config = xmacroplay-keys :0 Tab
end
begin
        prog = irexec
        button = DVD_9
        config = xmacroplay-keys :0 Page_Down
end
begin
        prog = irexec
        button = DVD_Return
        config = xmacroplay-keys :0 Escape
end
begin
        prog = irexec
        button = DVD_Play
        config = /home/jl/bin/osd.sh `date +%H:%M`
end

##
# Rhythmbox key bindings.
##
begin
        prog = Rhythmbox
        button = DVD_Play
        config = play
end
begin
        prog = Rhythmbox
        button = DVD_Pause
        config = playpause
end
begin
        prog = Rhythmbox
        button = DVD_Stop
        config = stop
end
begin
        prog = Rhythmbox
        button = DVD_Forward
        config = seek_forward
end
begin
        prog = Rhythmbox
        button = DVD_Rewind
        config = seek_backward
end
begin
        prog = Rhythmbox
        button = DVD_NextChapter
        config = next
end
begin
        prog = Rhythmbox
        button = DVD_PrevChapter
        config = previous
end

##
# gxine key bindings.
##
# start playback
begin
         button = DVD_Play
         prog   = gxine
         config = vdr ('PLAY') || play ();
end
# playback pause toggle
begin
         button = DVD_Pause
         prog   = gxine
         config = pause();
end
# stop playback
# fullscreen toggle
begin
         button = DVD_Stop
         prog   = gxine
#         config = Stop
         config = vo_fullscreen.toggle (); pause();
end
# set position to -15 seconds in current stream
begin
         button = DVD_Rewind
         prog   = gxine
         config = if (!vdr ('FASTREW') && !is_live_stream ()) play (0, get_time()-15000);
end
# set position to +15 seconds in current stream
begin
         button = DVD_Forward
         prog   = gxine
         config = if (!vdr ('FASTFWD') && !is_live_stream ()) play (0, get_time()+15000);
end
# set position of current stream togling
begin
         button = DVD_Return
         prog   = gxine
         config = vdr ('1') || play (10, 0);
         config = vdr ('2') || play (20, 0);
         config = vdr ('3') || play (30, 0);
         config = vdr ('4') || play (40, 0);
         config = vdr ('5') || play (50, 0);
         config = vdr ('6') || play (60, 0);
         config = vdr ('7') || play (70, 0);
         config = vdr ('8') || play (80, 0);
         config = vdr ('9') || play (90, 0);
         config = vdr ('0') || play (0, 0);
end
# cycle aspect ratio values
begin
         button = DVD_Setup
         prog   = gxine
         config = ++vo_aspect.v;
end

# Previous channel
begin
         button = DVD_PrevChapter
         prog   = gxine
         config = vdr ('CHANNELMINUS') || input_previous ();
end
# Next channel
begin
         button = DVD_NextChapter
         prog   = gxine
         config = vdr ('CHANNELPLUS') || input_next ();
end

##
# xine key bindings.
##
begin
         button = DVD_Play
         prog   = xine
         config = OSDStreamInfos
end
begin
         button = DVD_Pause
         prog   = xine
#         repeat = 0
#         delay = 2000
         config = Pause
end
begin
         button = DVD_Stop
         prog   = xine
         config = ToggleFullscreen
end
begin
         button = DVD_Rewind
         prog   = xine
         config = SeekRelative-15
end
begin
         button = DVD_Forward
         prog   = xine
         config = SeekRelative+15
end
begin
         button = DVD_Digits
         prog   = xine
         config = SetPosition0%
         config = SetPosition10%
         config = SetPosition20%
         config = SetPosition30%
         config = SetPosition40%
         config = SetPosition50%
         config = SetPosition60%
         config = SetPosition70%
         config = SetPosition80%
         config = SetPosition90%
end
begin
         button = DVD_Setup
         prog   = xine
         config = ToggleAspectRatio
end

##
# mplayer key bindings.
##
begin
         button = DVD_Play
         prog   = mplayer
         config = osd 3
         config = osd 0
end
begin
         button = DVD_Pause
         prog   = mplayer
         config = pause
end
begin
         button = DVD_Stop
         prog   = mplayer
         config = vo_fullscreen\npause
end
begin
         button = DVD_Rewind
         prog   = mplayer
         config = seek -15
end
begin
         button = DVD_Forward
         prog   = mplayer
         config = seek +15
end
begin
         button = DVD_Digits
         prog   = mplayer
         config = seek 0 1
         config = seek 10 1
         config = seek 20 1
         config = seek 30 1
         config = seek 40 1
         config = seek 50 1
         config = seek 60 1
         config = seek 70 1
         config = seek 80 1
         config = seek 90 1
end
begin
         button = DVD_Setup
         prog   = mplayer
         config = switch_ratio 1.77778
         config = switch_ratio 1.6
         config = switch_ratio 1.33333
         config = switch_ratio 0


end
begin
         button = DVD_Menu
         prog   = mplayer
         config = menu up
end

# tv_step_channel +1
# tv_step_channel -1

begin
    prog = irexec
    button = DVD_TopMenu
    mode = modo_menu
    flags = mode quit
    config = echo "1:no zoom   2:zoom-   3:zoom+\n4: ...   5: ...   6: ...\n7: ...   8: ...   9: ...\n    Cursor:volumen" | $HOME/osd.sh 0 &
end

end modo_normal

##
# Modo menu
####################################################

begin modo_menu
    begin
      prog = irexec
      button = DVD_TopMenu
      mode = modo_normal
      config = killall osd_cat
      flags = mode quit
    end

    begin
      prog = irexec
      button = DVD_CursorRight
      config = amixer set Master 5%+
    end
    begin
      prog = irexec
      button = DVD_CursorLeft
      config = amixer set Master 5%-
    end
    begin
      prog = irexec
      button = DVD_CursorUp
      config = amixer set Master 100% unmute
    end
    begin
      prog = irexec
      button = DVD_CursorDn
      config = amixer set Master 0%
    end
    begin
      prog = gxine
      button = DVD_1
      config = vo_zoom.v = 100;
    end
    begin
      prog = gxine
      button = DVD_2
      config = vo_zoom.v -= 5;
    end
    begin
      prog = xine
      button = DVD_1
      config = ZoomReset
    end
    begin
      prog = xine
      button = DVD_2
      config = ZoomOut
    end
    begin
      prog = xine
      button = DVD_3
      config = ZoomIn
    end
    begin
      prog = gxine
      button = DVD_3
      config = vo_zoom.v += 5;
    end
    begin
      prog = mplayer
      button = DVD_1
      config = panscan 0
    end
    begin
      prog = mplayer
      button = DVD_2
      config = panscan -0.1
    end
    begin
      prog = mplayer
      button = DVD_3
      config = panscan +0.1
    end

    begin
      prog = irexec
      button = DVD_On
      config = ( echo "Apagar en 30 minutos" | $HOME/osd.sh 0 & ) ; ( sudo shutdown 30 & )
      config = ( echo "Apagar en 60 minutos" | $HOME/osd.sh 0 & ) ; ( sudo shutdown 60 & )
      config = ( echo "Apagar en 90 minutos" | $HOME/osd.sh 0 & ) ; ( sudo shutdown 90 & )
      config = ( echo "Apagar en 120 minutos" | $HOME/osd.sh 0 & ) ; ( sudo shutdown 120 & )
      config = ( echo "Apagar en 180 minutos" | $HOME/osd.sh 0 & ) ; ( sudo shutdown 180 & )
      config = ( echo "No Apagar" | $HOME/osd.sh 0 & ) ; ( sudo shutdown -c & )
    end
end modo_menu


```

---


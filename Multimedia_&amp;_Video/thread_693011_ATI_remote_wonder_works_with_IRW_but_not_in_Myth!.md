---
title: "ATI remote wonder works with IRW but not in Myth!"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by Darkfish on 2008-02-10
Hello all,

  I am running mythbuntu 7.1 and have gotten everything pretty much working. I have a classic ATI remote wonder, and I have gotten it so that the mapping is all correct when using IRW, but I get no response from myth! I do login to myth as user steve, so I copied the lircrc to /home/steve/.mythtv/lircrc, and my lircd.conf file is in /etc/lirc/lircd.conf.  I have read everything I can find on this and no one seems to be having the same problems.  here is my lircd.conf file:

 contributed by Michael Haas
#
# brand: ATI "RF Remote Control" (first generation)
# model no. of remote control: Part #: 5000023600
# FCC ID: B4SUR84A
# picture: [http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg](http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg)
# receiver: [http://www.mythtv.org/wiki/index.php/Image:Remotewonder2.jpg](http://www.mythtv.org/wiki/index.php/Image:Remotewonder2.jpg)
#
# I created this new config file because the one for the ati remote wonder II
# did not work for me.

begin remote

  name ati_remote_wonder_rf
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          147991
  toggle_bit	0

      begin codes
          0                        0x14DC170000
          1                        0x14D20D0000
          2                        0x14D30E0000
          3                        0x14D40F0000
          4                        0x14D5100000
          5                        0x14D6110000
          6                        0x14D7120000
          7                        0x14D8130000
          8                        0x14D9140000
          9                        0x14DA150000
          volup                    0x14CD080000
          voldown                  0x14CE090000
          mute                     0x14CF0A0000
          chup                     0x14D00B0000
          chdown                   0x14D10C0000
          mouse_up                 0x1437720000
          mouse_down               0x1438730000
          mouse_left               0x1435700000
          mouse_right              0x1436710000
          mouse_up_right           0x143A750000
          mouse_down_right         0x143B760000
          mouse_up_left            0x1439740000
          mouse_down_left          0x143C770000
          right_click              0x14417C0000
          left_click               0x143D780000
          hand                     0x14CC070000
          book                     0x14CB060000
          ?                        0x14CA050000
          dvd                      0x14C9040000
          tv                       0x14C8030000
          a                        0x14C5000000
          b                        0x14C6010000
          power                    0x14C7020000
          stop                     0x14ED280000
          pause                    0x14EE290000
          fforward                 0x14EB260000
          rec                      0x14EC270000
          rewind                   0x14E9240000
          play                     0x14EA250000
          d                        0x14E01B0000
          c                        0x14DE190000
          e                        0x14E6210000
          f                        0x14E8230000
          right                    0x14E41F0000
          left                     0x14E21D0000
          up                       0x14DF1A0000
          down                     0x14E7220000
          ok                       0x14E31E0000
          timer                    0x14E11C0000
          shrink_resize            0x14E5200000
          menu                     0x14DB160000
          check                    0x14DD180000
      end codes

end remote


------------------------------------
and here is my lircrc file:


# MythTV native LIRC config file for
# the ATI-Wonder Remote
# using lirc_atiusb driver
#

begin
prog = mythtv
button = a
config = E
repeat = 2
end

begin
prog = mythtv
button = b
config = O
repeat = 2
end

#begin
#prog = mythtv
#button = tv
#config = Key Alt-T CurrentWindow
#repeat = 2
#end

begin
prog = mythtv
button = stop
config = Esc
repeat = 2
end

begin
prog = mythtv
button = fastforward
config = Right
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = max_window
config = V
repeat = 2
end

begin
prog = mythtv
button = pause
config = P
repeat = 2
end

begin
prog = mythtv
button = play
config = P
repeat = 2
end

begin
prog = mythtv
button = mute
config = F9
repeat = 2
end

begin
prog = mythtv
button = vol-down
config = F10
repeat = 2
end

begin
prog = mythtv
button = vol-up
config = F11
repeat = 2
end

begin
prog = mythtv
button = f
config = PgDown
repeat = 2
end

begin
prog = mythtv
button = d
config = PgUp
repeat = 2
end

begin
prog = mythtv
button = c
config = F4
repeat = 2
end

begin
prog = mythtv
button = e
config = Esc
repeat = 2
end

begin
prog = mythtv
button = cursor-right
config = Right
repeat = 2
end

begin
prog = mythtv
button = cursor-left
config = Left
repeat = 2
end

begin
prog = mythtv
button = cursor-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = cursor-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = chan-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = chan-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = ok
config = Enter
repeat = 2
end

begin
prog = mythtv
button = 1
config = 1
repeat = 2
end

begin
prog = mythtv
button = 2
config = 2
repeat = 2
end

begin
prog = mythtv
button = 3
config = 3
repeat = 2
end

begin
prog = mythtv
button = 4
config = 4
repeat = 2
end

begin
prog = mythtv
button = 5
config = 5
repeat = 2
end

begin
prog = mythtv
button = 6
config = 6
repeat = 2
end

begin
prog = mythtv
button = 7
config = 7
repeat = 2
end

begin
prog = mythtv
button = 8
config = 8
repeat = 2
end

begin
prog = mythtv
button = 9
config = 9
repeat = 2
end

begin
prog = mythtv
button = 0
config = 0
repeat = 2
end

begin
prog = mythtv
button = record
config = R
repeat = 2
end

begin
prog = mythtv
button = check
config = Enter
repeat = 2
end

### MPlayer lirc setup
#
# Remember to ln -s ./.mythtv/lircrc ../.lircrc for mplayer to work!

# Show OSD
begin
prog = mplayer
button = tv_on_demand
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 3
config = pause
end

begin
prog = mplayer
button = play
repeat = 3
config = pause
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = fastforward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = e
repeat = 3
config = quit





Am I going crazy here or is there a simple explanation? Any help is greatly appreciated!

---


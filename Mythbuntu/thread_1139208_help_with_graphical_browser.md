---
title: "help with graphical browser"
date: 2009-04-26
forum: Mythbuntu
---

### Post by phroman on 2009-04-26
Hello all, suuuper noob here, installed mythbuntu 9.04, and managed to get my snapstream firefly remote working.  (it was painfull, but it's done) Right now I only plan to use this setup as an xbmc or apple tv kind of thing, no dvr just yet.  My question is what do I use for a graphical browser to go over my local network?  I have a Mac full of media that I would like to browse to and just copy everything from there to the appropriate myth locations.  Thunar file manager does not do this.  I ran Synaptic Packet Manager, it says Nautilus is installed but I cannot find anywhere to launch it from, it says it is a graphical shell for gnome.  Mythbuntu is using gnome, right?  Well, thanks in advance for any assistance!  :P

---

### Post by superm1 on 2009-04-27
> **phroman said:**
> Hello all, suuuper noob here, installed mythbuntu 9.04, and managed to get my snapstream firefly remote working.  (it was painfull, but it's done)


What about it was painful?  The goal is to have remotes and such working OOTB when you select them in the installer or MCC.  What else did you have to do?  We should be able to get this fixed in a future build provided you can get the right information for what needed to be done.

> 
 Right now I only plan to use this setup as an xbmc or apple tv kind of thing, no dvr just yet.  My question is what do I use for a graphical browser to go over my local network?  I have a Mac full of media that I would like to browse to and just copy everything from there to the appropriate myth locations.  Thunar file manager does not do this.  I ran Synaptic Packet Manager, it says Nautilus is installed but I cannot find anywhere to launch it from, it says it is a graphical shell for gnome.  Mythbuntu is using gnome, right?  Well, thanks in advance for any assistance!  :P
Mythbuntu doesn't use gnome by default.  You can of course use gnome if you wanted..

I think you are better off however using cifs (samba) to mount to misc locations within the myth structure.  By doing so, you instantly get to be able to use mythtv's file browser (and 10 foot interface) to browse all that media.

---

### Post by phroman on 2009-04-27
Hi Superm1, well, I selected Snapstream X10 Remote during the initial setup, but it didn't work OOTB.  I had to search the web and finally found a few files that did.  

1. I had to replace the lircd.conf file in /etc/lirc with one I found here:  [http://ubuntuforums.org/showthread.php?t=884972](http://ubuntuforums.org/showthread.php?t=884972)  
Here is the code: 

```
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
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
```

2. I added an lircrc file to ~/.mythtv   I found the file here: NOTE: I didn't simlink any files at all
[http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/](http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/)
Here is the code: 

```
     # ~/.mythtv/lircrc
    # also symlink this file to ~/.lircrc!
    #
    # MythTV native LIRC config file for snapstream firefly
    # Modified from Brad Templeton’s
    # which came from Jarod Wilson’s
    # which came from Jeff Campbell’s
    # Modified to use the Firefly remotes unique buttons by Ryan Schmitz
    # Here we have the jump point commands. They only work if you
    # have defined function keys for these jump points. You can set the
    # jump point commands in Mythweb under Settings > Key Bindings
    # as follows:
    # F8 Main Menu
    # F3 Program Guide
    # F5 TV Recording Playback
    # F7 Play DVD
    # F6 MythGallary
    # F4 Play Music
    # F2 MythVideo
    # ——————————-
    # By flipp for ubuntu 7.10 gutsy
    # notice i didn’t need to set repeat to anything, most places want
    # you to set it to 2 or 3 but it only works for me if it’s 0
    #

    begin
    prog = mythtv
    button = FIREFLY
    config = F8
    repeat = 0
    end

    begin
    prog = mythtv
    button = TV
    repeat = 0
    config = F5
    end

    begin
    prog = mythtv
    button = VIDEO
    repeat = 0
    config = F2
    end

    begin
    prog = mythtv
    button = MUSIC
    repeat = 0
    config = F4
    end

    begin
    prog = mythtv
    button = PHOTOS
    repeat = 0
    config = F
    end

    begin
    prog = mythtv
    button = DVD
    repeat = 0
    config = F7
    end

    begin
    prog = mythtv
    button = HELP
    repeat = 0
    config = F1
    end

    begin
    prog = mythtv
    button = UP
    repeat = 0
    config = Up
    end

    begin
    prog = mythtv
    button = DOWN
    repeat = 0
    config = Down
    end

    begin
    prog = mythtv
    button = LEFT
    repeat = 0
    config = Left
    end

    begin
    prog = mythtv
    button = RIGHT
    repeat = 0
    config = Right
    end

    # Channel Up
    begin
    prog = mythtv
    button = CH+
    repeat = 0
    config = Up
    end

    # Channel Down
    begin
    prog = mythtv
    button = CH-
    repeat = 0
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
    repeat = 0
    config = P
    end

    # Mute
    begin
    prog = mythtv
    button = Mute
    repeat = 0
    config = |
    end

    # Fast forward (30 sec default)
    begin
    prog = mythtv
    button = REW
    repeat = 0
    config = PgUp
    end

    # Rewind (10 sec default)
    begin
    prog = mythtv
    button = FWD
    repeat = 0
    config = PgDown
    end

    # Skip forward (10 min default)
    begin
    prog = mythtv
    button = NEXT
    repeat = 0
    config = End
    end

    # Skip backward (10 min default)
    begin
    prog = mythtv
    button = PREV
    repeat = 0
    config = Home
    end

    # Record
    begin
    prog = mythtv
    button = REC
    repeat = 0
    config = R
    end

    # Delete
    begin
    prog = mythtv
    button = A
    repeat = 0
    config = D
    end

    # Decrease play speed
    begin
    prog = mythtv
    button = B
    repeat = 0
    config = J
    end

    # double speed watch
    begin
    prog = mythtv
    button = C
    repeat = 0
    config = J
    end

    # Bring up Time stretch
    begin
    prog = mythtv
    button = D
    repeat = 0
    config = Y
    end

    change tuners
    begin
    prog = mythtv
    button = OPTION
    repeat = 0
    config = Y
    end

    # Display EPG while in live TV,
    # View selected show while in EPG
    begin
    prog = mythtv
    button = MENU
    repeat = 0
    config = M
    end

    # Scroll up
    begin
    prog = mythtv
    button = VOL+
    repeat = 0
    config = F11
    end

    # Scroll down
    begin
    prog = mythtv
    button = VOL-
    repeat = 0
    config = F10
    end

    # Bring up OSD info
    begin
    prog = mythtv
    button = INFO
    repeat = 0
    config = I
    end

    # Change display aspect ratio
    begin
    prog = mythtv
    button = CH-
    repeat = 0
    config = W
    end

    # Numbers 0-9

    begin
    prog = mythtv
    button = 0
    repeat = 0
    config = 0
    end

    begin
    prog = mythtv
    button = 1
    repeat = 0
    config = 1
    end

    begin
    prog = mythtv
    button = 2
    repeat = 0
    config = 2
    end

    begin
    prog = mythtv
    button = 3
    repeat = 0
    config = 3
    end

    begin
    prog = mythtv
    button = 4
    repeat = 0
    config = 4
    end

    begin
    prog = mythtv
    button = 5
    repeat = 0
    config = 5
    end

    begin
    prog = mythtv
    button = 6
    repeat = 0
    config = 6
    end

    begin
    prog = mythtv
    button = 7
    repeat = 0
    config = 7
    end

    begin
    prog = mythtv
    button = 8
    repeat = 0
    config = 8
    end

    begin
    prog = mythtv
    button = 9
    repeat = 0
    config = 9
    end

    ### MPlayer lirc setup

    # Show OSD
    begin
    prog = mplayer
    button = MENU
    repeat = 0
    config = osd
    end

    begin
    prog = mplayer
    button = MAXI
    repeat = 0
    config = vo_fullscreen
    end

    begin
    prog = mplayer
    button = VOL+
    repeat = 0
    config = volume +1
    end

    begin
    prog = mplayer
    button = VOL-
    repeat = 0
    config = volume -1
    end

    begin
    prog = mplayer
    button = MUTE
    repeat = 0
    config = mute
    end

    begin
    prog = mplayer
    button = INFO
    repeat = 0
    config = osd
    end

    begin
    prog = mplayer
    button = LEFT
    repeat = 0
    config = pt_step -1
    end

    begin
    prog = mplayer
    button = RIGHT
    repeat = 0
    config = pt_step 1
    end

    begin
    prog = mplayer
    button = EXIT
    repeat = 0
    config = quit
    end

    begin
    prog = mplayer
    button = REW
    repeat = 0
    config = seek -10
    end

    begin
    prog = mplayer
    button = FWD
    repeat = 0
    config = seek +10
    end

    begin
    prog = mplayer
    button = PREV
    repeat = 0
    config = seek -60
    end

    begin
    prog = mplayer
    button = PAUSE
    repeat = 0
    config = pause
    end

    begin
    prog = mplayer
    button = NEXT
    repeat = 0
    config = seek +60
    end

    ### Xine lirc setup

    begin
    prog = xine
    button = PLAY
    repeat = 0
    config = Play
    end

    begin
    prog = xine
    button = STOP
    repeat = 0
    config = Stop
    end

    begin
    prog = xine
    button = BACK
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = EXIT
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = CLOSE
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = PAUSE
    repeat = 0
    config = Pause
    end

    begin
    prog = xine
    button = UP
    repeat = 0
    config = EventUp
    end

    begin
    prog = xine
    button = DOWN
    repeat = 0
    config = EventDown
    end

    begin
    prog = xine
    button = LEFT
    repeat = 0
    config = EventLeft
    end

    begin
    prog = xine
    button = RIGHT
    repeat = 0
    config = EventRight
    end

    begin
    prog = xine
    button = OK
    repeat = 0
    config = EventSelect
    end

    begin
    prog = xine
    button = ENT
    repeat = 0
    config = EventSelect
    end

    begin
    prog = xine
    button = OPTION
    repeat = 0
    config = Menu
    end

    begin
    prog = xine
    button = FFW
    repeat = 0
    #config = SpeedFaster
    config = SeekRelative+60
    end

    begin
    prog = xine
    button = REW
    repeat = 0
    #config = SpeedSlower
    config = SeekRelative-60
    end

    begin
    prog = xine
    button = VOL+
    repeat = 0
    config = Volume+
    end

    begin
    prog = xine
    button = VOL-
    repeat = 0
    config = Volume-
    end

    begin
    prog = xine
    button = MUTE
    repeat = 0
    config = Mute
    end

    begin
    prog = xine
    button = MENU
    repeat = 0
    config = RootMenu
    end

    begin
    prog = xine
    button = NEXT
    repeat = 0
    config = EventNext
    end

    begin
    prog = xine
    button = PREV
    repeat = 0
    config = EventPrior
    end

    begin
    prog = xine
    button = INFO
    repeat = 0
    config = OSDStreamInfos
    end
```


I was trying bazillions of combination of files and whittled it down to these two.  Mind you, I have no idea of what I'm doing and am so inexperienced at Linux that this was surely much harder than it is for probably 99% of the people out there.  :)   At this point I can, from my Mac, browse to the Myth box, after setting my Mac to the same workgroup, and put my media files in the proper directories.  However, I would like to be able to browse graphically the other way too.  As I have no windows machines, a friend suggested I just use NFS for networking, which I'm looking into. I don't really know how these 2 computers are talking to each other, but I hope to figure it out soon....  

I wish I could contribute to this community more because Mythbuntu is awesome, but I'm useless at this experience level right now.  Please let me know if you have any other questions or pointers on my system. Thanks!

---

### Post by superm1 on 2009-04-27
> **phroman said:**
> Hi Superm1, well, I selected Snapstream X10 Remote during the initial setup, but it didn't work OOTB.  I had to search the web and finally found a few files that did.  

1. I had to replace the lircd.conf file in /etc/lirc with one I found here:  [http://ubuntuforums.org/showthread.php?t=884972](http://ubuntuforums.org/showthread.php?t=884972)  
Here is the code: 

```
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
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
```2. I added an lircrc file to ~/.mythtv   I found the file here: NOTE: I didn't simlink any files at all
[http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/](http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/)
Here is the code: 

```
     # ~/.mythtv/lircrc
    # also symlink this file to ~/.lircrc!
    #
    # MythTV native LIRC config file for snapstream firefly
    # Modified from Brad Templeton’s
    # which came from Jarod Wilson’s
    # which came from Jeff Campbell’s
    # Modified to use the Firefly remotes unique buttons by Ryan Schmitz
    # Here we have the jump point commands. They only work if you
    # have defined function keys for these jump points. You can set the
    # jump point commands in Mythweb under Settings > Key Bindings
    # as follows:
    # F8 Main Menu
    # F3 Program Guide
    # F5 TV Recording Playback
    # F7 Play DVD
    # F6 MythGallary
    # F4 Play Music
    # F2 MythVideo
    # ——————————-
    # By flipp for ubuntu 7.10 gutsy
    # notice i didn’t need to set repeat to anything, most places want
    # you to set it to 2 or 3 but it only works for me if it’s 0
    #

    begin
    prog = mythtv
    button = FIREFLY
    config = F8
    repeat = 0
    end

    begin
    prog = mythtv
    button = TV
    repeat = 0
    config = F5
    end

    begin
    prog = mythtv
    button = VIDEO
    repeat = 0
    config = F2
    end

    begin
    prog = mythtv
    button = MUSIC
    repeat = 0
    config = F4
    end

    begin
    prog = mythtv
    button = PHOTOS
    repeat = 0
    config = F
    end

    begin
    prog = mythtv
    button = DVD
    repeat = 0
    config = F7
    end

    begin
    prog = mythtv
    button = HELP
    repeat = 0
    config = F1
    end

    begin
    prog = mythtv
    button = UP
    repeat = 0
    config = Up
    end

    begin
    prog = mythtv
    button = DOWN
    repeat = 0
    config = Down
    end

    begin
    prog = mythtv
    button = LEFT
    repeat = 0
    config = Left
    end

    begin
    prog = mythtv
    button = RIGHT
    repeat = 0
    config = Right
    end

    # Channel Up
    begin
    prog = mythtv
    button = CH+
    repeat = 0
    config = Up
    end

    # Channel Down
    begin
    prog = mythtv
    button = CH-
    repeat = 0
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
    repeat = 0
    config = P
    end

    # Mute
    begin
    prog = mythtv
    button = Mute
    repeat = 0
    config = |
    end

    # Fast forward (30 sec default)
    begin
    prog = mythtv
    button = REW
    repeat = 0
    config = PgUp
    end

    # Rewind (10 sec default)
    begin
    prog = mythtv
    button = FWD
    repeat = 0
    config = PgDown
    end

    # Skip forward (10 min default)
    begin
    prog = mythtv
    button = NEXT
    repeat = 0
    config = End
    end

    # Skip backward (10 min default)
    begin
    prog = mythtv
    button = PREV
    repeat = 0
    config = Home
    end

    # Record
    begin
    prog = mythtv
    button = REC
    repeat = 0
    config = R
    end

    # Delete
    begin
    prog = mythtv
    button = A
    repeat = 0
    config = D
    end

    # Decrease play speed
    begin
    prog = mythtv
    button = B
    repeat = 0
    config = J
    end

    # double speed watch
    begin
    prog = mythtv
    button = C
    repeat = 0
    config = J
    end

    # Bring up Time stretch
    begin
    prog = mythtv
    button = D
    repeat = 0
    config = Y
    end

    change tuners
    begin
    prog = mythtv
    button = OPTION
    repeat = 0
    config = Y
    end

    # Display EPG while in live TV,
    # View selected show while in EPG
    begin
    prog = mythtv
    button = MENU
    repeat = 0
    config = M
    end

    # Scroll up
    begin
    prog = mythtv
    button = VOL+
    repeat = 0
    config = F11
    end

    # Scroll down
    begin
    prog = mythtv
    button = VOL-
    repeat = 0
    config = F10
    end

    # Bring up OSD info
    begin
    prog = mythtv
    button = INFO
    repeat = 0
    config = I
    end

    # Change display aspect ratio
    begin
    prog = mythtv
    button = CH-
    repeat = 0
    config = W
    end

    # Numbers 0-9

    begin
    prog = mythtv
    button = 0
    repeat = 0
    config = 0
    end

    begin
    prog = mythtv
    button = 1
    repeat = 0
    config = 1
    end

    begin
    prog = mythtv
    button = 2
    repeat = 0
    config = 2
    end

    begin
    prog = mythtv
    button = 3
    repeat = 0
    config = 3
    end

    begin
    prog = mythtv
    button = 4
    repeat = 0
    config = 4
    end

    begin
    prog = mythtv
    button = 5
    repeat = 0
    config = 5
    end

    begin
    prog = mythtv
    button = 6
    repeat = 0
    config = 6
    end

    begin
    prog = mythtv
    button = 7
    repeat = 0
    config = 7
    end

    begin
    prog = mythtv
    button = 8
    repeat = 0
    config = 8
    end

    begin
    prog = mythtv
    button = 9
    repeat = 0
    config = 9
    end

    ### MPlayer lirc setup

    # Show OSD
    begin
    prog = mplayer
    button = MENU
    repeat = 0
    config = osd
    end

    begin
    prog = mplayer
    button = MAXI
    repeat = 0
    config = vo_fullscreen
    end

    begin
    prog = mplayer
    button = VOL+
    repeat = 0
    config = volume +1
    end

    begin
    prog = mplayer
    button = VOL-
    repeat = 0
    config = volume -1
    end

    begin
    prog = mplayer
    button = MUTE
    repeat = 0
    config = mute
    end

    begin
    prog = mplayer
    button = INFO
    repeat = 0
    config = osd
    end

    begin
    prog = mplayer
    button = LEFT
    repeat = 0
    config = pt_step -1
    end

    begin
    prog = mplayer
    button = RIGHT
    repeat = 0
    config = pt_step 1
    end

    begin
    prog = mplayer
    button = EXIT
    repeat = 0
    config = quit
    end

    begin
    prog = mplayer
    button = REW
    repeat = 0
    config = seek -10
    end

    begin
    prog = mplayer
    button = FWD
    repeat = 0
    config = seek +10
    end

    begin
    prog = mplayer
    button = PREV
    repeat = 0
    config = seek -60
    end

    begin
    prog = mplayer
    button = PAUSE
    repeat = 0
    config = pause
    end

    begin
    prog = mplayer
    button = NEXT
    repeat = 0
    config = seek +60
    end

    ### Xine lirc setup

    begin
    prog = xine
    button = PLAY
    repeat = 0
    config = Play
    end

    begin
    prog = xine
    button = STOP
    repeat = 0
    config = Stop
    end

    begin
    prog = xine
    button = BACK
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = EXIT
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = CLOSE
    repeat = 0
    config = Quit
    end

    begin
    prog = xine
    button = PAUSE
    repeat = 0
    config = Pause
    end

    begin
    prog = xine
    button = UP
    repeat = 0
    config = EventUp
    end

    begin
    prog = xine
    button = DOWN
    repeat = 0
    config = EventDown
    end

    begin
    prog = xine
    button = LEFT
    repeat = 0
    config = EventLeft
    end

    begin
    prog = xine
    button = RIGHT
    repeat = 0
    config = EventRight
    end

    begin
    prog = xine
    button = OK
    repeat = 0
    config = EventSelect
    end

    begin
    prog = xine
    button = ENT
    repeat = 0
    config = EventSelect
    end

    begin
    prog = xine
    button = OPTION
    repeat = 0
    config = Menu
    end

    begin
    prog = xine
    button = FFW
    repeat = 0
    #config = SpeedFaster
    config = SeekRelative+60
    end

    begin
    prog = xine
    button = REW
    repeat = 0
    #config = SpeedSlower
    config = SeekRelative-60
    end

    begin
    prog = xine
    button = VOL+
    repeat = 0
    config = Volume+
    end

    begin
    prog = xine
    button = VOL-
    repeat = 0
    config = Volume-
    end

    begin
    prog = xine
    button = MUTE
    repeat = 0
    config = Mute
    end

    begin
    prog = xine
    button = MENU
    repeat = 0
    config = RootMenu
    end

    begin
    prog = xine
    button = NEXT
    repeat = 0
    config = EventNext
    end

    begin
    prog = xine
    button = PREV
    repeat = 0
    config = EventPrior
    end

    begin
    prog = xine
    button = INFO
    repeat = 0
    config = OSDStreamInfos
    end
```
I was trying bazillions of combination of files and whittled it down to these two.  

Well would you mind performing a little experiment here?  I don't hink you will actually be needing "both" of those files, so it would good to know which one really did the trick.

Can you backup the ~/.lircrc and run this command:

```
mythbuntu-lirc-generator
```

That will re-generate a mythbuntu lircrc using the lircd.conf you put in place.  See if all keys work, just some keys, or no keys.

After you've determined that, replace the lircd.conf in /etc/lirc with the default one.  If you didn't back up the default one, open up the mythbuntu control centre and disable the remote followed by enable it and it will reset it.

If you check the box to generate dynamic button mappings it will handle re generating a lircrc too.  Again, see if it's all, some, or no buttons.

> 
Mind you, I have no idea of what I'm doing and am so inexperienced at Linux that this was surely much harder than it is for probably 99% of the people out there.  :)   At this point I can, from my Mac, browse to the Myth box, after setting my Mac to the same workgroup, and put my media files in the proper directories.  However, I would like to be able to browse graphically the other way too.  As I have no windows machines, a friend suggested I just use NFS for networking, which I'm looking into. I don't really know how these 2 computers are talking to each other, but I hope to figure it out soon....  

I wish I could contribute to this community more because Mythbuntu is awesome, but I'm useless at this experience level right now.  Please let me know if you have any other questions or pointers on my system. Thanks!

The reason that you can browse from your mac is that samba is installed by default on mythbuntu.  As you were seeing the default shares show up on your mac.  If you use cifs to mount your mac's files somewhere in your filesystem, you will be able to do it the other way around either graphically (in Thunar) or from mythvideo and mythmusic.  In mythvideo, you'll have to go and let it scan the directory first though or change the setting so it browses rather than using metadata.

---

### Post by phroman on 2009-04-27
ok, I ran
```
mythbuntu-lirc-generator
```
it created a new .lircrc file in my home directory, I restarted Lirc, and only some buttons worked in Mythbuntu frontend.  I replaced the /etc/lirc/lircd.conf file with the original (I saved it), restarted Lirc and no buttons worked in Mythbuntu frontend.  

As for the networking, I turned off windows sharing on my Mac, but maybe that's only the server function of it?  I guess it can still act as a client.  Let me know if I can do anything else, thanks.  :)

---

### Post by phroman on 2009-04-28
bump

---

### Post by lightning9 on 2009-05-18
Hello phroman,

Don't know if you are still working on the remote control issue since it was not the main point of your thread, but I have a couple comments/suggestions.

1. FYI, the Snaptsream Firefly [has never worked OOTB]("https://bugs.launchpad.net/mythbuntu/+bug/176613"). 
2. If you got it working using my lircd.conf, how about if you also try using my ~/.lirc/mythtv file included in the same post? I tried to make the buttons actions a little more intuitive than the default files (not sure about the one you cited).

I finally got my Firefly working this past weekend using the same files so I can attest to their validity.

If you want more help on this, plet me know.

Good luck,
lightning9

---

### Post by phroman on 2009-05-18
Hi Lightning9, it's funny that you should respond to my post because I actually used your post/guide from last year to get my Firefly working.  :p  

One of the biggest problem seems to be that If you enable the Snapstream X10 Remote in MCC, the file generated in /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb, will have the incorrect name entry for "remote name", as compared the /etc/lirc/hardware.conf.   It will say "Snapstream Firefly", this is wrong, it must be changed to match the /etc/lirc/hardware.conf, which will be "Snapstream X10 RF.  Actually it doesn't matter what the name is as long as they match in the two files.  There is a bug filed for this but it doesn't look like its gotten too much attention.  Here's the bug report:

[https://bugs.launchpad.net/mythbuntu/+bug/176613]("https://bugs.launchpad.net/mythbuntu/+bug/176613")

I used an lircrc file that I got from this site:

[http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/]("http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/")

And placed it in ~/.mythtv.  Note however that it is NOT sim-linked to ~/.lirc/lircrc, or any other file.  I'm not sure why there is any sim-linking in the first place.  I will try your lircrc file though to compare.

My Firefly is fully up and running now, but thanks for your reply, that's awsome.

---

### Post by lightning9 on 2009-05-18
Yes, I replied to that bug report earlier this morning to see if I can help get this figured out. It is pretty frustrating having to jump through these hoops every time I try a new version of Myth. Glad it is working for you. Mine is working now, too.

---


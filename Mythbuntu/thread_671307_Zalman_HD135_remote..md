---
title: "Zalman HD135 remote."
date: 2008-01-18
forum: Mythbuntu
---

### Post by Scrier on 2008-01-18
Hi, 

wondering if anyone have any experience with this. Have tried some guides using the HD160 desktop but with little luck. Problem I get is that I can't open the USB port for some reason. 

Any suggestions or guides to refer to if anyone had similar issues feel free to let me know :P

// Andreas

---

### Post by Scrier on 2008-01-20
Anyone know how you cans see if it's firmware is in and available? I can shutdown the system using the power button but that is builtin in the case afaik. So not sure it is connected.

---

### Post by Meph1st0 on 2009-03-05
I think I've almost got mine working but I think I'm a step or two behind.  I can get the box to recognize that I'm pressing buttons using irw.  It actually shows:

```
0000000000000019 00 Up VLSystem_MPlay_Blast
000000000000001d 00 Down VLSystem_MPlay_Blast
0000000000000019 00 Up VLSystem_MPlay_Blast
0000000000000019 01 Up VLSystem_MPlay_Blast
0000000000000054 00 Left VLSystem_MPlay_Blast
0000000000000019 00 Up VLSystem_MPlay_Blast
0000000000000019 00 Up VLSystem_MPlay_Blast
0000000000000042 00 Ok VLSystem_MPlay_Blast
000000000000001d 00 Down VLSystem_MPlay_Blast
000000000000001f 00 Exit_Click VLSystem_MPlay_Blast
000000000000001f 01 Exit_Click VLSystem_MPlay_Blast
000000000000001f 00 Exit_Click VLSystem_MPlay_Blast
000000000000001f 00 Exit_Click VLSystem_MPlay_Blast

```

so it knows I'm pressing buttons, but for the life of me I can't get it to work with mythtv.  I think my  last step is getting the correct .lircrc file configured.  I've found several examples of .lircrc files for the remote from other websites but none of them seem to work.  I've also read about some people who've gotten theirs to work but they talk about having to replace lirc with irtrans server.  and then getting it to work after that.  I've never used irtrans before and it worries me that if I switch to irtrans the VFD display will stop working, but that doesn't make much sense either since the VFD is using LCDProc. (by the way I got the VFD working by following this [HTML]http://xbmc.org/forum/showthread.php?t=45924[/HTML] walkthrough.)

So I guess my question is, do I really need to switch over to IRTrans to get the remote working? or am I just using the wrong .lircrc config file?

here are the files I used to get the zalman to be recognized through irw:

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

/etc/lircd.conf
```
#
# this config file was automatically generated
# using lirc-0.8.2(mplay) on Fri Dec  7 20:04:59 2007
#
# contributed by 
#
# brand:                       VLSystem
# model no. of remote control: MPlay Blast
# devices being controlled by this remote:
#

begin remote

  name  VLSystem_MPlay_Blast
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          211938
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Movies                   0x40
          Television               0x46
          Photos                   0x45
          Music                    0x56
          1                        0x4d
          2                        0x4e
          3                        0x4f
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4c
          Vol+                     0x0a
          Vol-                     0x0e
          Ch+_Lang                 0x12
          Ch-_Page                 0x16
          Guide                    0x0f
          Back                     0x0b
          Tv                       0x13
          Ok                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1d
          Exit_Click               0x1f
          Task_Quick               0x17
          Run_DClick               0x1b
          Rew                      0x0d
          Play                     0x09
          Ffwd                     0x15
          Prev                     0x1a
          Stop                     0x01
          Next                     0x1e
          Pause                    0x05
          Mute                     0x4a
          Warp_Mouse               0x47
          Rec                      0x11
          DVD_Zoom                 0x14
          Detail                   0x4b
      end codes

end remote
```

~/.lircrc
```

begin
    prog   = mythtv
    button = More
    config = I
end

begin
    prog   = mythtv
    button = Left
    repeat = 1
    config = Left
end

begin
    prog   = mythtv
    button = Right
    repeat = 1
    config = Right
end

begin
    prog   = mythtv
    button = Up
    repeat = 1
    config = Up
end

begin
    prog   = mythtv
    button = Down
    repeat = 1
    config = Down
end

#
# TV Control
#

begin
    prog   = mythtv
    button = VolDown
    repeat = 1
    config = F10
end

begin
    prog   = mythtv
    button = VolUp
    repeat = 1
    config = F11
end

begin
    prog   = mythtv
    button = Mute
    config = F9
end

begin
    prog   = mythtv
    button = ChanDown
    config = PgDown
end

begin
    prog   = mythtv
    button = ChanUp
    config = PgUp
end

#
# Video Navigation
#

begin
    prog   = mythtv
    button = Play
    config = P
end

begin
    prog   = mythtv
    button = Pause
    config = P
end

begin
    prog   = mythtv
    button = Stop
    config = Esc
end

begin
    prog   = mythtv
    button = Forward
    config = >
end

begin
    prog   = mythtv
    button = Rewind
    config = <
end

begin
    prog   = mythtv
    button = Replay
    config = Q
end

begin
    prog   = mythtv
    button = Skip
    config = Z
end

begin
    prog   = mythtv
    button = Record
    config = R
end

#
# Miscellaneous
#

# M for Menu
begin
    prog   = mythtv
    button = Star
    config = M
end

begin
    prog   = mythtv
    button = Hash
    config = M
end

begin
    prog   = mythtv
    button = Clear
    config = Esc
end

begin
    prog   = mythtv
    button = Enter
    config = Space
end

#
# Numbers
#

begin
    prog   = mythtv
    button = Zero
    config = 0
end

begin
    prog   = mythtv
    button = One
    config = 1
end

begin
    prog   = mythtv
    button = Two
    config = 2
end

begin
    prog   = mythtv
    button = Three
    config = 3
end

begin
    prog   = mythtv
    button = Four
    config = 4
end

begin
    prog   = mythtv
    button = Five
    config = 5
end

begin
    prog   = mythtv
    button = Six
    config = 6
end

begin
    prog   = mythtv
    button = Seven
    config = 7
end

begin
    prog   = mythtv
    button = Eight
    config = 8
end

begin
    prog   = mythtv
    button = Nine
    config = 9
end

begin
    prog   = mythtv
    button = Red
    config = D
end
```

---

### Post by rodercot on 2009-03-08
Hey Guys,

 I posted an irrecorded version of the lircd.conf on the how to you are welcome to try. here is the link.

 [http://xbmc.org/forum/showthread.php?t=45924](http://xbmc.org/forum/showthread.php?t=45924)

 hope it helps. I do not use the remote on my system. but it's worth a shot, you may need to change some button names.

 Dave

---

### Post by Meph1st0 on 2009-03-10
That's a good post.  I've been able to get irw to recognize all the key presses on my remote, but I still can't get Mythtv to work with it.  It's got to be the .lircrc file.  Is there anyone that has a .lircrc file that's working with Mythtv for the Zalman hd135 remote?

---

### Post by rodercot on 2009-03-11
> **Meph1st0 said:**
> That's a good post.  I've been able to get irw to recognize all the key presses on my remote, but I still can't get Mythtv to work with it.  It's got to be the .lircrc file.  Is there anyone that has a .lircrc file that's working with Mythtv for the Zalman hd135 remote?


 You are editing the lircrc file in ~/.mythtv correct. that is symlinked automagically to the .lircrc file.  They should be the same thing I know, but I am sure I ran into that once as well. Also make sure that the commands you are using in your .lircrc file match the button names from the lircd files. so 

 button = Down should match Down, dwn, down, etc from the lircd file. 

 It should be just a matter of button names and maybe try adding the remote =  line to your button configs just for the heck of it maybe just try a couple buttons and see if it does anything for you.
 
 Dave

---

### Post by Meph1st0 on 2009-03-13
Here are the files I have.  You'll see that the button names in the lircd.conf file match the ones in my lircrc file which is found at ~/.mythtv. I'm just using buttons 1-5 and the exit button just for testing sake but they still don't work.

lirc file:
```
#My Lircrc File

begin
    remote = VLSystem_MPlay_Blast
    prog   = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = VLSystem_MPlay_Blast
    prog   = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = VLSystem_MPlay_Blast
    prog   = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = VLSystem_MPlay_Blast
    prog   = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = VLSystem_MPlay_Blast
    prog   = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = VLSystem_MPlay_Blast
    prog = mythtv
    button = Exit_Click
    config = Esc
    repeat = 0
    delay = 0
end
```

lircd.conf
```
#
# this config file was automatically generated
# using lirc-0.8.2(mplay) on Fri Dec  7 20:04:59 2007
#
# contributed by 
#
# brand:                       VLSystem
# model no. of remote control: MPlay Blast
# devices being controlled by this remote:
#

begin remote

  name  VLSystem_MPlay_Blast
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          211938
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Movies                   0x40
          Television               0x46
          Photos                   0x45
          Music                    0x56
          1                        0x4d
          2                        0x4e
          3                        0x4f
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4c
          Vol+                     0x0a
          Vol-                     0x0e
          Ch+_Lang                 0x12
          Ch-_Page                 0x16
          Guide                    0x0f
          Back                     0x0b
          Tv                       0x13
          Ok                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1d
          Exit_Click               0x1f
          Task_Quick               0x17
          Run_DClick               0x1b
          Rew                      0x0d
          Play                     0x09
          Ffwd                     0x15
          Prev                     0x1a
          Stop                     0x01
          Next                     0x1e
          Pause                    0x05
          Mute                     0x4a
          Warp_Mouse               0x47
          Rec                      0x11
          DVD_Zoom                 0x14
          Detail                   0x4b
      end codes

end remote

```

I have no idea what else to try now. :(

---

### Post by rodercot on 2009-03-13
I wonder if the /dev/ttyusb0 has something to do with this. When using a device like an mceusb remote it loads up a lirc driver like lirc_dev and lirc_mceusb2, there are no modules for the Mplay it uses a userspace driver and the module is loaded up with the kernel I think as /dev/ttyUSB0. 

 Why not try seraching out something like myth and /dev/ttyUSB0 devices or check out the commandIR site as they are sort of the same. 
 
 I will try and find some hints as well.

 Dave

---

### Post by rodercot on 2009-03-13
I just found this and you can try it as well. 

 edit your /etc/modprobe.d/aliases file and add after the last commented line and before the rest of the files start at the top of the file.

 alias char-major-61 mplay and reboot for good measure to make sure it is loading. You should then be able to remove the remote= part of your lircrc. 

 Dave

---

### Post by Meph1st0 on 2009-04-02
Alright, well I've got this working now.  Thanks to advice from Dave.

Dave, you were right on the money when you said, > You are editing the lircrc file in ~/.mythtv correct. that is symlinked automagically to the .lircrc file. They should be the same thing I know, but I am sure I ran into that once as well. Also make sure that the commands you are using in your .lircrc file match the button names from the lircd files.

In order to get the Zalman HD135 remote to work I have to use three files.  One thing that I learned is that simply restarting lirc (sudo /etc/init.d/lirc restart) isn't enough. After editing these files I needed to fully reboot in order for it all to take effect.

The files that I needed to setup correctly were: 

/etc/lirc/lircd.conf (The same copy that I posted above in a previous post of mine)

/etc/lirc/hardware.conf (the same copy that I posted above as well in a previous post)

~/.mythtv/lircrc (this file contains the same contents as the example .lircrc file posted above as well only this time it's located in ~/.mythtv rather than the one that's symlinked at ~/.lircrc)

Thanks again Dave, my remote is working great now.

---

### Post by diamondnular on 2009-04-27
Hi all, 

I cannot get the remote to work. Is there a full instruction or HOW TO to install LIRC to get the remote to work? I tried all possible, but when using 'irw' nothing shows up.

Any input would be greatly appreciated!

Thanks.

---


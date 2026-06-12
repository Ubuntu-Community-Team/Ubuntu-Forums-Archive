---
title: "lirc: mceusb some buttons not working"
date: 2011-02-19
forum: Mythbuntu
---

### Post by markcs on 2011-02-19
Hi!

I am using Ubuntu 10.10.

After some recent update, some buttons on my remote control are now not working, and I am unable to get them to be recognized by lirc.

Earlier, the remote was recongized as mceusb and it was working fine, but now I notice it is recongnized as vista_mceusb.  After changing the .lircrc file, I got the remote partly working, but still some buttons do not work (ie OK button).

The remote is identified as an Elitegroup Computer Systems (ECS) Infrared Receiver in lsusb

I have tried the gnome lirc gui configuration program, and this crashes when selecting the ECS IR.

I have tried manually recording the buttons use irrecord, but irrecord does not work, with the error 'No toggle bit mask found.
But I know for sure that RC6 has a toggle bit!'.

Can anyone suggest a way for me to try to get lirc working again?

Thanks!

---

### Post by AlecJ on 2011-02-21
Lirc is not used on your setup see

[HTML]http://www.mythtv.org/wiki/MCE_Remote#Windows_Vista_MCE_Remote[/HTML]

I use a similar remote, the answer is the .lircrc file.

You are welcome to a copy of my .lircrc with all buttons working, including a frontend restart button for when it locks up?

---

### Post by markcs on 2011-02-21
> **AlecJ said:**
> Lirc is not used on your setup see

[HTML]http://www.mythtv.org/wiki/MCE_Remote#Windows_Vista_MCE_Remote[/HTML]

I use a similar remote, the answer is the .lircrc file.

You are welcome to a copy of my .lircrc with all buttons working, including a frontend restart button for when it locks up?

When running irw, no codes are recognised when pushing some buttons like the OK button, so I guess its not in the .lircrc file. 

I would guess the problem is in the /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file.  Can you paste a copy of that file for me?

---

### Post by AlecJ on 2011-02-22
ok

```
#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects_remote_control.htm
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
    Yellow          0x00007ba2
    Green          0x00007ba3
    Red          0x00007ba4
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
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by 
#
# brand:                       Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR-150 Remote (MCE kit)
# SMK dongle 0609:031d
#

begin remote

  name  mceusb_hauppauge
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Tue Mar 10 19:27:09 2009
#
# contributed by 
#
# brand:  SIIG Vista MCE remote
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  vista_mce
  bits           16
  flags RC6
  eps            30
  aeps          100

  header       2654   889
  one           427   427
  zero          427   427
  pre_data_bits   21
  pre_data       0x37FF0
  gap          69850
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          Power                    0xEBF3
          Pictures                 0x6BB6
          Radio                    0xEBAF
          Videos                   0x6BB5
          Music                    0xEBB8
          Rec                      0x6BE8
          Pause                    0xEBE7
          Stop                     0x6BE6
          Skipback                 0xEBE4
          Play                     0x6BE9
          Skipfwd                  0xEBE5
          Rwd                      0x6BEA
          Fwd                      0xEBEB
          Start                    0x6BF2
          Back                     0xEBDC
          More                     0x6BF0
          Volup                    0xEBEF
          Voldown                  0x6BEE
          Chup                     0xEBED
          Chdown                   0x6BEC
          Up                       0xEBE1
          Down                     0x6BE0
          Left                     0xEBDF
          Right                    0x6BDE
          Mute                     0xEBF1
          Rectv                    0x6BB7
          Guide                    0xEBD9
          Livetv                   0x6BDA
          Dvdmenu                  0xEBDB
          1                        0x6BFE
          2                        0xEBFD
          3                        0x6BFC
          4                        0xEBFB
          5                        0x6BFA
          6                        0xEBF9
          7                        0x6BF8
          8                        0xEBF7
          9                        0x6BF6
          *                        0xEBE2
          0                        0x6BFF
          #                        0xEBE3
          Clear                    0x6BF5
          Enter                    0xEBF4
      end codes

end remote


```

---

### Post by AlecJ on 2011-02-22
Heres .lircrc

```
# Alec's remote file
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
    repeat = 5
    delay = 5
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
    repeat = 5
    delay = 5
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
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 5
    delay = 5
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
    repeat = 5
    delay = 2
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
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 5
    delay = 2
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
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = O
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
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = LiveTV
    config = X
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Blue
    config = #
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Red
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Yellow
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Green
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Teletext
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Clear
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = DVD
    config = L
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Power
    config = /usr/sbin/runmyth
    repeat = 0
    delay = 0
end

```

---

### Post by AlecJ on 2011-02-22
> **markcs said:**
> When running irw, no codes are recognised when pushing some buttons like the OK button, so I guess its not in the .lircrc file. 

I would guess the problem is in the /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file.  Can you paste a copy of that file for me?

The OK button is called  "Enter" in the code.
But I have an OK in my .lircrc, wonder if thats a throw back to an older system, my mythbox has been going since 2006-ish?

---

### Post by markcs on 2011-02-22
Thanks!

I tried your lircd.conf.mceusb file and it still does not work for me.  In fact, you have the same file as me.

My Enter/OK button is never displayed when running irw, but I know it works as I can see LED on the IR receiver flashing when I press the button (some other buttons don't work also).

Any other ideas?

---

### Post by AlecJ on 2011-02-22
Yes I do have a few idea's

You need to check if the remote is working on the buttons that "don't work", elsewhere
The only way I can think is does the red light in the USB receiver, light, on a faulty button being pushed?

Then check the obvious like a new battery in the remote, clean lens, etc ?
check irw

second, backup ~/.mythtv/lircrc then, using myth control panel, re-install remote as MCE "all types"
check irw

Lets see where we are after that?

---

### Post by markcs on 2011-02-22
> **AlecJ said:**
> 
You need to check if the remote is working on the buttons that "don't work", elsewhere
The only way I can think is does the red light in the USB receiver, light, on a faulty button being pushed?

Then check the obvious like a new battery in the remote, clean lens, etc ?
check irw

second, backup ~/.mythtv/lircrc then, using myth control panel, re-install remote as MCE "all types"
check irw

Lets see where we are after that?

Thanks.  Obvious things were already checked before I posted on this forum, but thanks anyway.  I know the button works because the LED on the IR receiver flashes when I press the button on the remote.  Also, irrecord records the button presses.  I am sure there is nothing wrong with the remote.

I reinstalled lirc again last night, but to no avail.  Still not working!  

Grrr :(

---

### Post by AlecJ on 2011-02-23
> **markcs said:**
> Thanks.  Obvious things were already checked before I posted on this forum, but thanks anyway.  I know the button works because the LED on the IR receiver flashes when I press the button on the remote.  Also, irrecord records the button presses.  I am sure there is nothing wrong with the remote.

I reinstalled lirc again last night, but to no avail.  Still not working!  

Grrr :(

Done a bit of reading up as it got my interest 
[HTML]http://www.lirc.org/#top[/HTML]
[HTML]http://www.mythtv.org/wiki/MCE_Remote#Newer_remote[/HTML]
[HTML]http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_mceusb2/[/HTML]


Your USB could be the version 1069, maybe it needs the lirc_mceusb2 driver?

is there a way of testing the remote and usb elsewhere? maybe on windows just to prove the hardware?

---


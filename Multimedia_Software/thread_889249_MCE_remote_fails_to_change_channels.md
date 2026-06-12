---
title: "MCE remote fails to change channels"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Bllz on 2008-08-13
My mythtv setup is awesome except for one minor detail -- I can't change channels.  I can't do it with a keyboard OR the MCE remote (which works fine otherwise... it's the dark philips model if that matters.)  I can, however, access channels 2 - 9 by pushing the respective number buttons on the remote.

I'm not sure how to start diagnosing the problem because to be honest, i'm not even sure what got the remote working in the first place.  I selected the "new MCE remote (phillips)" in the mythbuntu configuration, and I installed the MCEUSB driver.

Below are all the relevant config files i can think of, so hopefully they contain some indication of what is wrong.  I'd venture a guess as to the fact that the second conf file is more relevant than the first.

File 1:  

```
   1.
      liquidougon@server:~$ cat /etc/lircd.conf
   2.
      #This configuration has been automatically generated via
   3.
      #the Ubuntu LIRC package maintainer scripts.
   4.
      #
   5.
      #It includes the default configuration for the remote and/or
   6.
      #transmitter that you have selected during package installation.
   7.
      #
   8.
      #Feel free to add any custom remotes to the configuration
   9.
      #via additional include directives or below the existing
  10.
      #Ubuntu include directives from your selected remote and/or
  11.
      #transmitter.
  12.
       
  13.
      #Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
  14.
      include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

File 2:  /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```
   1.
      #
   2.
      # RC-6 config file
   3.
      #
   4.
      # source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
   5.
      #         http://home.hccnet.nl/m.majoor/pronto.pdf
   6.
      #
   7.
      # used by: Philips
   8.
      #
   9.
      #########
  10.
      #
  11.
      # Philips Media Center Edition remote control
  12.
      # For use with the USB MCE ir receiver
  13.
      #
  14.
      # Dan Conti  dconti|acm.wwu.edu
  15.
      #
  16.
      # Updated with codes for MCE 2005 Remote additional buttons
  17.
      # *, #, Teletext, Red, Green, Yellow & Blue Buttons
  18.
      # Note: TV power button transmits no code until programmed.
  19.
      # Updated 12th September 2005
  20.
      # Graham Auld - mce|graham.auld.me.uk
  21.
      #
  22.
      # Radio, Print, RecTV are only available on the HP Media Center remote control
  23.
      #
  24.
       
  25.
      begin remote
  26.
       
  27.
        name mceusb
  28.
        bits           16
  29.
        flags RC6|CONST_LENGTH
  30.
        eps            30
  31.
        aeps          100
  32.
       
  33.
        header       2667   889
  34.
        one           444   444
  35.
        zero          444   444
  36.
        pre_data_bits 21
  37.
        pre_data      0x37FF0
  38.
        gap          105000
  39.
        toggle_bit     22
  40.
        rc6_mask     0x100000000
  41.
       
  42.
       
  43.
            begin codes
  44.
       
  45.
              Blue    0x00007ba1
  46.
              Yellow  0x00007ba2
  47.
              Green   0x00007ba3
  48.
              Red     0x00007ba4
  49.
              Teletext        0x00007ba5
  50.
      # starts at af
  51.
              Radio    0x00007baf
  52.
              Print    0x00007bb1
  53.
              Videos   0x00007bb5
  54.
              Pictures 0x00007bb6
  55.
              RecTV    0x00007bb7
  56.
              Music    0x00007bb8
  57.
              TV       0x00007bb9
  58.
      # no ba - d8
  59.
       
  60.
              Guide    0x00007bd9
  61.
              LiveTV   0x00007bda
  62.
              DVD      0x00007bdb
  63.
              Back     0x00007bdc
  64.
              OK       0x00007bdd
  65.
              Right    0x00007bde
  66.
              Left     0x00007bdf
  67.
              Down     0x00007be0
  68.
              Up       0x00007be1
  69.
       
  70.
              Star       0x00007be2
  71.
              Hash       0x00007be3
  72.
       
  73.
              Replay   0x00007be4
  74.
              Skip     0x00007be5
  75.
              Stop     0x00007be6
  76.
              Pause    0x00007be7
  77.
              Record   0x00007be8
  78.
              Play     0x00007be9
  79.
              Rewind   0x00007bea
  80.
              Forward  0x00007beb
  81.
              ChanDown 0x00007bec
  82.
              ChanUp   0x00007bed
  83.
              VolDown  0x00007bee
  84.
              VolUp    0x00007bef
  85.
              More     0x00007bf0
  86.
              Mute     0x00007bf1
  87.
              Home     0x00007bf2
  88.
              Power    0x00007bf3
  89.
              Enter    0x00007bf4
  90.
              Clear    0x00007bf5
  91.
              Nine     0x00007bf6
  92.
              Eight    0x00007bf7
  93.
              Seven    0x00007bf8
  94.
              Six      0x00007bf9
  95.
              Five     0x00007bfa
  96.
              Four     0x00007bfb
  97.
              Three    0x00007bfc
  98.
              Two      0x00007bfd
  99.
              One      0x00007bfe
 100.
              Zero     0x00007bff
 101.
            end codes
 102.
       
 103.
      end remote
```

Thanks in advance for all the help!  I'll be more than happy to provide additional information or config files if need be.

I really hope someone can give me a hand ... I'm so close to a working myth box!

-Bllz

---

### Post by Bllz on 2008-08-13
Update:

Still not working but some work with the irw command yielded some odd results.

When i tried to map the chan up/down buttons in the frontend, they registered as just plain  "up" and "down", but irw does identify the buttons as different and correctly labels them.

... Mythtv... what is wrong with you?

***EDIT***
I went into the config file and re-defined the chan +/- as PgUp and PgDown.  I then went into the frontend and mapped pgup and pgdown as the chan +/- command.  Still no luck.

I also realized that I have no OSD on any of the 8 channels I can tune into.

Could my backend be misconfigured?

---

### Post by Bllz on 2008-08-14
I am also including my lircrc file, as I have been told it is of relevance.

I'm hoping someone has more of a clue than I do.


```
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
    repeat = 0
    delay = 0
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
    repeat = 0
    delay = 0

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

    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
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
    repeat = 0
    delay = 0
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
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
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
    repeat = 0

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = R
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
    repeat = 0
    delay = 0
end 
```

---

### Post by Bllz on 2008-08-14
Bump...


Nobody on this entire forum?  Am I asking the wrong questions?  Is more information needed to answer my question?  :(

Help!

---

### Post by rbm0307 on 2008-08-14
> **Bllz said:**
> Bump...


Nobody on this entire forum?  Am I asking the wrong questions?  Is more information needed to answer my question?  :(

Help!
Your lircrc file is malformed.  The reason numbers work is because those lines are intact up until the errors.  Here are the errors:

You are missing an "end" on lines 57
You are missing a "begin" on line 112
You are missing an "end" on line 227

To debug this, login to mythtv user.  Ensure that you are in the directory with the .lircrc and issue the command "ircat mythtv".  It will tell you where the errors are located.  When you have repaired the file, then this command will echo the command output for each keypress on the remote.  

Here are some helpful web pages on LIRC, MythTV and Ubuntu
[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)
[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

Hope this helps point you in the right direction.  Cheers,
Robert.

---

### Post by Bllz on 2008-08-15
Robert,

Thanks a lot for having a look -- it's greatly appreciated.

I just checked my lircrc file, and it turns out that i accidentally omitted those lines while copying from PuTTY (which is harder than it really should be...)

I'm beginning to think that this might not have anything to do with lirc, because i'm unable to change channels with my keyboard as well.

What do you think?  Any relevant files i should post?

---

### Post by rbm0307 on 2008-08-19
> **Bllz said:**
> Robert,

Thanks a lot for having a look -- it's greatly appreciated.

I just checked my lircrc file, and it turns out that i accidentally omitted those lines while copying from PuTTY (which is harder than it really should be...)

I'm beginning to think that this might not have anything to do with lirc, because i'm unable to change channels with my keyboard as well.

What do you think?  Any relevant files i should post?
I'm sorry that it took me so long to reply but I left for my  vacation and only just got a look see at this thread.  I believe you are correct...if the keyboard is not working, then it is the Myth install that is corrupted/broken. I'd backup the database and reinstall from scratch, IMO.

---


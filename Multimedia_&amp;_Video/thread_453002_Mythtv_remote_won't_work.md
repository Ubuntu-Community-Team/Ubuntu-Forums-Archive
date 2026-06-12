---
title: "Mythtv remote won't work"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-05-23
My remote used to work.  Irw is working.  I dont understand why it isn't working.
[B][SIZE="5"]
Here is my lircrc in my ~.mythtv/lircrc[/SIZE][/B]

```
begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol- 

  repeat = 2

  config = volume -1 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol+ 

  repeat = 2

  config = volume +1 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Mute 

  repeat = 2

  config = mute 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Pause 

  repeat = 2

  config = pause 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Replay/SkipBackward 

  repeat = 2

  config = seek -60 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = SkipForward 

  repeat = 2

  config = seek +60 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Back 

  repeat = 2

  config = quit 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastFwd 

  repeat = 2

  config = seek +10 

end 



begin 

  prog = mplayer 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastRwd 

  repeat = 2

  config = seek -10 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 1 

  repeat = 2

  config = 1 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 2 

  repeat = 2

  config = 2 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 3 

  repeat = 2

  config = 3 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 4 

  repeat = 2

  config = 4 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 5 

  repeat = 2

  config = 5 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 6 

  repeat = 2

  config = 6 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 7 

  repeat = 2

  config = 7 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 8 

  repeat = 2

  config = 8 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = 9 

  repeat = 2

  config = 9 

end 



# Menu 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Menu 

  repeat = 2

  config = M 

end 



# Delete 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Red 

  repeat = 2

  config = D 

end 



# Volume Down 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol- 

  repeat = 2

  config = F10 

end 



# Volume Up 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol+ 

  repeat = 2

  config = F11 

end 



# Mute 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Mute 

  repeat = 2

  config = F9 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Play 

  repeat = 2

  config = Space 

end 



# Record 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Record 

  repeat = 2

  config = R 

end 



# Stop 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Stop 

  repeat = 2

  config = T 

end 



# Pause 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Pause 

  repeat = 2

  config = P 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Up 

  repeat = 2

  config = Up 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Left 

  repeat = 2

  config = Left 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Right 

  repeat = 2

  config = Right 

end 



begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Down 

  repeat = 2

  config = Down 

end 



# Select 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = OK 

  repeat = 2

  config = Return 

end 



# Previous Commercial Cut 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Replay/SkipBackward 

  repeat = 2

  config = Q 

end 



# Next Commercial Cut Forward 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = SkipForward 

  repeat = 2

  config = Z 

end 



# Cancel / Back 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Back 

  repeat = 2

  config = Esc 

end 



# Skip Forward 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastFwd 

  repeat = 3

  config = > 

end 



# Skip Backwards 

begin 

  prog = mythtv 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastRwd 

  repeat = 3

  config = < 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Back/Exit 

  repeat = 2

  config = Quit 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Menu 

  repeat = 2

  config = TitleMenu 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol- 

  repeat = 2

  config = Volume- 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Vol+ 

  repeat = 2

  config = Volume+ 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Play 

  repeat = 2

  config = Play 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Stop 

  repeat = 2

  config = Stop 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Pause 

  repeat = 2

  config = Pause 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = Replay/SkipBackward 

  repeat = 2

  config = SeekRelative-30 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = SkipForward 

  repeat = 2

  config = SeekRelative+60 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastFwd 

  repeat = 2

  config = SeekRelative+30 

end 



begin 

  prog = xine 

  remote = Hauppauge_WinTV_Nexus-S 

  button = FastRwd 

  repeat = 2

  config = SeekRelative-15 

end 



```
[B][SIZE="5"]
Here is my lircd.conf[/SIZE][/B]

```
begin remote



  name          blaster

  bits          32

  flags         RAW_CODES

  eps           0

  aeps          0

  plead         0

  gap           333333

  repeat_bit    0

  begin raw_codes



    name 0

    2156789760

    name 1

    2156789761

    name 2

    215652762

    name 3

    2156789763

    name 4

    2156789764

    name 5

    2156789765

    name 6

    2156789766

    name 7

    2156789767

    name 8

    2156789768

    name 9

    2156789769

    name POWER

    2156789770    

    



  end raw_codes

end remote



begin remote

  name            Hauppauge_WinTV_Nexus-S  

  bits            13  

  flags           RC5|CONST_LENGTH  

  eps             30  

  aeps            100  

  one             944   828  

  zero            944   828  

  gap             113932  

  toggle_bit      2  

  plead           980  



  begin codes

       TV              0x000000000000179C

       FULL_SCREEN     0x000000000000102E

       SOURCE          0x0000000000001022

       1               0x0000000000001781

       2               0x0000000000001782

       3               0x0000000000001783

       4               0x0000000000001784

       5               0x0000000000001785

       6               0x0000000000001786

       7               0x0000000000001787

       8               0x0000000000001788

       9               0x0000000000001789

       0               0x0000000000001780

       Power           0x00000000000017BD

       Go              0x00000000000017BB

       Menu            0x000000000000178D

       Red             0x000000000000178B

       Green           0x00000000000017AE

       Yellow          0x00000000000017B8

       Blue            0x00000000000017A9

       Ch+             0x00000000000017A0

       Ch-             0x00000000000017A1

       Vol-            0x0000000000001791

       Vol+            0x0000000000001790

       Ok              0x00000000000017A5

       Mute            0x000000000000178F

       Play            0x00000000000017B5

       Record          0x00000000000017B7

       Stop            0x00000000000017B6

       Pause           0x00000000000017B0

       Videos          0x0000000000001798

       Music           0x0000000000001799

       Pictures        0x000000000000179A

       Guide           0x000000000000179B

       Radio           0x000000000000178C

       Up              0x0000000000001794

       Left            0x0000000000001796

       Right           0x0000000000001797

       Down            0x0000000000001795

       OK              0x00000000000017A5

       Prev.Ch         0x0000000000001792

       Replay/SkipBackward 0x00000000000017A4

       SkipForward     0x000000000000179E

       Asterix         0x000000000000178A

       #               0x000000000000178E

       Back            0x000000000000179F

       FastFwd         0x00000000000017B4

       FastRwd         0x00000000000017B2

       Timers          0x000000000000178A

       Recordings      0x000000000000178E



  end codes

end remote
```

Thanks for the help,
Hans

---

### Post by tgm4883 on 2007-05-23
What did you change?

---

### Post by hansoffate on 2007-05-23
I have noidea.  I changed some stuff with lircd.conf and lircrc.  It seemed to be working.  But then one day my girlfriend said it wasn't working.  I tried to fix it but i couldn't figure it out.

ANY Ideas?

Thanks,
Hans

---

### Post by hansoffate on 2007-05-24
Does anyone have any ideas?   This just doesn't make sense.  If it works in IRW, why doesn't it work in mythtv?

Thanks,
Hans

---

### Post by barney_1 on 2007-05-24
Are you running the mythfrontend as a different user?  If that is the case you need a lircrc in the .mythtv folder for that user as well.

If not, run mythtv from a terminal window:
```
mythfrontend -v all
```
Try out your remote and see if it throws an error.

---

### Post by hansoffate on 2007-05-24
I am running mythtv with the same user that has the .mythtv/lircrc configured.   
I will try that command when I get home tonight, and let you know how it went.


Thanks,
Hans

---

### Post by hansoffate on 2007-05-25
I did that command.  I tried pressing buttons, and nothing updated after the launch.  Should I try to output this file?  If so, how do I do that... I have done it once before, but i forgot.  

I know the remote and sensor and lircd.conf because IRW is working.  I think its something in my lircrc, but everything looks fine to me.

Thanks for the help,
Hans

---

### Post by barney_1 on 2007-05-25
I don't know how to make mythfrontend kick out a debug log.  I know the backend has a log in /var/log/mythtv but I don't think it reports frontend errors there.

One more question:  When you run IRW and press buttons on the remote, do you get the NAMES of the buttons as shown in your lircd.conf?

If that's coming out ok I don't know what else to check.

---

### Post by hansoffate on 2007-05-25
Yup.  The names match up.  It seems really odd.  I'll try pmming the guys that helped me setup mythtv for the first time.  Maybe they can shed some light.

Thanks for the help.  Any any more suggestions are appreciated.

Thank you,
Hans

---

### Post by majoridiot on 2007-05-26
did you by any chance accidentally erase or change the symlink .lircrc in you home directory?  it should point to
the lircrc in the .mythtv directory. 

```
$ ls -l ~/.lircrc
```

it should point to:

```
/home/hansoffate/.lircrc -> /home/hansoffate/.mythtv/lircrc
```

if it doesn't, fix it:

```
$ rm ~/.lircrc
$ ln -s ~/.mythtv/lircrc ~/.lircrc
```

remember that any changes made to lirc require a restart of the frontend to take effect.

---

### Post by hansoffate on 2007-05-27
Well you were right.  There was no link between the two.  I ran the command and restarted mythfrontend and it still doesn't work.

hansoffate@mythlinux:~$ ls -l ~/.lircrc
lrwxrwxrwx 1 hansoffate hansoffate 31 2007-05-26 21:58 /home/hansoffate/.lircrc -> /home/hansoffate/.mythtv/lircrc

Do you want to ssh in again?  Tell me a time you want to take a peak around.

Thanks for the help,
Hans

---

### Post by hansoffate on 2007-06-05
Any other ideas?

I am still having this problem.  I hate getting up every time I want to fastforward.

Thanks for the help,
hans

---


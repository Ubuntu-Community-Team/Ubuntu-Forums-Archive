---
title: "Hauppauge remote double key press"
date: 2007-11-25
forum: Mythbuntu
---

### Post by dbabe on 2007-11-25
I have a Hauppauge R808-HPG-S remote with a PVR 350 card.  When I hit the Enter or end buttons, I frequently get double key events registered, i.e. from the main menu, it automatically starts watching live TV, instead of jumping to the previous menu.  This happens about once out of every 4-6 times that I press the remote buttons in question.  I have edited Gap settings in lircd.conf, and changed the delay settings to every possible value in lircrc.  Nothing changes this behavior.  I have googled every night for the past 6 days, and not found many posts matching this.  The one that I did find, did not give a valid solution.  This is a fresh install of Mythbuntu from two days ago.  I had this same issue in an install of Mythtv from a month ago.  Please help, so I don't have to abandon my hopes of running a Linux PVR box, and be forced to use MS Media center.  The wife will not put up with a flaky remote that navigates to crazy places on it's own.  Thanks.

---

### Post by foxbuntu on 2007-11-26
Can you please post your lircd and lircrc configs?

---

### Post by dbabe on 2007-11-26
Here they are:

#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by me 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100
  one           969   811
  zero          969   811
  plead        1097
  gap          114605

  toggle_bit      2



      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Left				0x1172
          Right				0x1174
          Up				0x1175
          Down				0x1176
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote

###########lircrc starts here########################

#This is Dan's lircrc file for the Happauge remote, model number R808-HPG-S
#V1.1
#last edited 11-23-07 10:03am

begin
    remote = hauppauge_pvr
    prog = irexec
    button = Power
    config = /sbin/shutdown -h now
    mode = halt
    flags = once
end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Power
#    config = halt
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Go
#    config =
#    repeat = 0
#    delay = 0
#end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 1
    delay = 10
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Red
#    config =
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Green
#    config =
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Yellow
#    config =
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Blue
#    config =
#    repeat = 0
#    delay = 0
#end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol-
    config = [
    repeat = 2
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 2
    delay = 0
end

#New navigation arrows are added here###########################

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Left
    config = Left
    repeat = 1
    delay = 5
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Right
    config = Right
    repeat = 1
    delay = 5
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Up
    config = Up
    repeat = 1
    delay = 5
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Down
    config = Down
    repeat = 1
    delay = 5
end
#New navigation arrows end here#################################

#OK key repeat tests**********************************************************************************************************
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Blank
#    config =
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = hauppauge_pvr
#    prog = mythtv
#    button = Full
#    config =
#    repeat = 0
#    delay = 0
#end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end


#**********End of mythtv section, beginning of mplayer commands******************

---

### Post by road2elysium on 2007-11-26
From the LIRC.org documentation.

The config file for LIRC tools consists of one or more of the following constructions:

    begin
	prog	= ...
	remote	= ...
	button	= ...
	repeat	= ...
	delay	= ...
	config	= ...
	mode	= ...
	flags	= ...
    end


repeat
    tells the program what shall happen if a key is repeated. A value of zero tells the program to ignore repeated keys. Any other positive value 'n' tells the program to pass the config string every 'n'-th time to the according application, when a key is repeated. The default for repeat is zero. 


delay
    tells the program to ignore the specified number of key repeats before using the "repeat" configuration directive above. This is used to prevent double triggers of events when using a fast repeat rate. A value of zero, which also is the default, will disable the delay function.


You may want to try changing the repeat/delay values.
Alternatively, you could record your own remote IR codes using irrecord.

---

### Post by dbabe on 2007-11-27
Very sound advice, however I have already been down the road of changing both repeat and delay values, with no effect on the problem.  Examples that I tried:

repeat=0
delay=0

repeat=1
delay=5

repeat=1
delay=500

repeat=0
delay=50

My experience is similar to the one or two other posts that I found, where users tried many combinations of delay and repeat changes, all to no avail.  I have also done a "mini" irrecord file to test the problem, and it still shows up.  Have also run *mode2* and verified the functions of every button.  By the way, each button produces two alternating codes that toggle back and forth, but that is probably a separate topic.  There must be something else.  Thanks for the advice, and hopefully someone else has run into this situation where the expected typical solutions do not work.

---

### Post by rich86 on 2008-02-02
Hi, sorry to bump up and old thread but have you found a sollution to this problem as i am having the same thing with my mega sky 580 remote control? See [http://ubuntuforums.org/showthread.php?t=650762]("http://ubuntuforums.org/showthread.php?t=650762")
Cheers

EDIT:
I found an way round the problem if you add: "config = echo '' > /dev/null" before the main config event then the first signal will do nothing and the second will be command that is required. I found this after a lot of in-depth Googling didn't come up with it by myself.
eg :
begin
    remote = MSI
    prog = mythtv
    button = Mute
    config = echo '' > /dev/null
    config = |
    repeat = 0
    delay = 0
end

---


---
title: "Nova-T 500 remote partly works"
date: 2008-02-10
forum: Mythbuntu
---

### Post by RichardA on 2008-02-10
If I run irw in a terminal, I see the codes and button names as I press the buttons.
In the Myth front end only the arrow keys, and maybe a few others, work.

I've symlinked ~/.lircrc and ~/.mythtv/lircrc, so which step am I missing?

---

### Post by JGJones on 2008-02-10
Got the same problem here. You using Mythubuntu installation for the MythTV setup?

I've not yet looked into why it's not working myself btw, you've gotten a bit further with linking etc that I've not done.

---

### Post by RichardA on 2008-02-12
Yes, I'm using Mythbuntu.

I think I've read that newer versions of Myth will use ~/.lircrc directly, without a symlink.

I wonder if the names of some of the buttons are different in this and /etc/lirc/lircd.conf, but I haven't yet had a chance to check (I downloaded some of the config files from [www.parker1.co.uk](www.parker1.co.uk)).

---

### Post by david.birch on 2008-02-12
if irw works & you def have a .mythtv/lircrc file then it must be naming issues in the files, i think i used the parker1 links orig but i did have to find mis-named button/code pairs.

these lircd.conf & lircrc files work

lircd.conf

```

# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         Star                     0x0037
         0                        0x000B
         #                        0x0029
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote

```

.mythtv/lircrc

```

# /etc/lircrc
# ln ~mythtv/.mythtv/lircrc
#
# MythTV native LIRC config file for
# Hauppage Nova-T-500 PCI Dual Tuners DVB-T
# Snowboard shape remote
# Silver on top Black underneath
# 45 buttons
#
# Originally
# By Jarod Wilson, 2003/12/21
# Amalgamated from Jeff Campbell's .lircrc



################## MythTV Control ######################
### http://www.mythtv.org/wiki/index.php/Keybindings ###

#       Remote Button
##      MythTV function


#       Go
##      Go to home page
begin
prog = mythtv
button = Go
config = ALT+H
end

#       Power
##      Turns monitor in Standby
#begin
#prog = irexec
#button = Power
#config = sudo vbetool dpms on ; sudo vbetool dpms off
#end

#       TV
##      Go to Watch TV
begin
prog = mythtv
button = TV
config = ALT+T
end

#       Videos
##      Go to MythVideo
begin
prog = mythtv
button = Videos
config = ALT+V
end

#       Music
##      Go to MythMusic
begin
prog = mythtv
button = Music
config = ALT+M
end

#       Pictures
##      Go to MythGallery
begin
prog = mythtv
button = Pictures
config = ALT+P
end

#       Guide
##      display EPG
begin
prog = mythtv
button = Guide
config = s
end

#       Radio



#       ArrowUp
##      Up
begin
prog = mythtv
button = ArrowUp
config = Up
end

#       ArrowLeft
##      Left
begin
prog = mythtv
button = ArrowLeft
config = Left
end

#       OK
##      Select/enter/resolve
begin
prog = mythtv
button = OK
config = Space
end

#       ArrowRight
##      Right
begin
prog = mythtv
button = ArrowRight
config = Right
end

#       ArrowDown
##      Down
begin
prog = mythtv
button = ArrowDown
config = Down
end

#       BackExit
##      Exit/go back/cancel
begin
prog = mythtv
button = BackExit
config = Esc
end

#       Menu
##      Menu
begin
prog = mythtv
button = Menu
config = m
end

#       VolumeUp
##      Volume Up
begin
prog = mythtv
button = VolumeUp
repeat = 1
config = F11
end

#       VolumeDown
##      Volume down
begin
prog = mythtv
button = VolumeDown
repeat = 1
config = F10
end

#       PrevCh
##      Change tuner card input
begin
prog = mythtv
button = PrevCh
config = c
end

#       Mute
##      Mute
begin
prog = mythtv
button = Mute
#config = F9
config = +
end

#       ChannelUp
begin
prog = mythtv
button = ChannelUp
config = Up
end
#       ChannelDown
begin
prog = mythtv
button = ChannelDown
config = Down
end

#       Record
begin
prog = mythtv
button = Record
config = R
end

#       Rewind
begin
prog = mythtv
button = Rewind
config = Left
end

#       SkipBack
begin
prog = mythtv
button = SkipBack
config = PgUp
end

#       Play
begin
prog = mythtv
button = Play
config = Return
end

#       Pause
begin
prog = mythtv
button = Pause
config = P
end

#       Stop
begin
prog = mythtv
button = Stop
config = Esc
end

#       Fwdwind
begin
prog = mythtv
button = Fwdwind
config = Right
end

#       SkipFwd
begin
prog = mythtv
button = SkipFwd
config = PgDown
end

#       1
begin
prog = mythtv
button = 1
config = 1
end

#       2
begin
prog = mythtv
button = 2
config = 2
end

#       3
begin
prog = mythtv
button = 3
config = 3
end

#       4
begin
prog = mythtv
button = 4
config = 4
end

#       5
begin
prog = mythtv
button = 5
config = 5
end

#       6
begin
prog = mythtv
button = 6
config = 6
end

#       7
begin
prog = mythtv
button = 7
config = 7
end

#       8
begin
prog = mythtv
button = 8
config = 8
end

#       9
begin
prog = mythtv
button = 9
config = 9
end

#       Star
##      Info
begin
prog = mythtv
button = Star
config = i
end

#       0
begin
prog = mythtv
button = 0
config = 0
end

#       #
##      Toggle recording of current program (cycles through types)
begin
prog = mythtv
button = #
config = r
end

#       Red
##      Picture zoom
begin
prog = mythtv
button = Red
config = W
end

#       Green
#       OSD navigation through channels/programs
begin
prog = mythtv
button = Green
config = O
end

#       Yellow
begin
prog = mythtv
button = Yellow
config = Q
end

#       Blue
begin
prog = mythtv
button = Blue
config = Z
end

```

---

### Post by RichardA on 2008-02-13
Thanks for those. I now get _every_ button recognised when I run irw. When I run the MythTV front end, the arrow keys work, but not much else.

How can this be?

---

### Post by RichardA on 2008-02-18
Can anyone help me to fix or troubleshoot this problem? The remote works perfectly using irw in a terminal, but not in the MythTV front end, even though I'm pretty sure I have the correct config files in place.

---

### Post by tez1982 on 2008-11-15
I'm having the same problem after re-installing Mythbuntu 8.10, I remember something about reconfiguring LIRC but I can't find it anywhere??

---

### Post by tobiz on 2008-12-11
> **tez1982 said:**
> I'm having the same problem after re-installing Mythbuntu 8.10, I remember something about reconfiguring LIRC but I can't find it anywhere?? I also have this problem.  Best I get from irw is: left arrow = ^[[D; right arrow =  ^[[C; up arrow = ^[[A; down arrow = ^[[B; 123456789*0# = 123456789*0`. Other keys give no output. This is an absolute mess; it worked ok on 8.04.1!!!!

---

### Post by smbm on 2009-02-18
Did anyone manage do fix this? I'm having the same problems!!!

---

### Post by scary_jeff on 2009-02-18
If your remote works in irw but not in mythtv, you probably don't have a correct .lircrc in your home directory.

There's a guide for how to make one in the mythtv wiki, under 'remote' in the NovaT-500 page. There might also be a wizard for this in mythbuntu control center, I can't remember.

Hope this helps.

---

### Post by zzztownsend on 2009-02-20
Once you've got it working with irw, and some buttons working in mythtv, then I found that the bindings for myth had some keys missing. The offending file is ~/.lirc/mythtv

I have attached my edited version if that is any help. You'll have to rename it from mythtv.txt to mythtv (I had to add .txt to get the forum to upload it)

Cheers

Matt

---

### Post by rossco on 2009-02-20
Hi guys,

I just recently solved a similar issue with my remote with the same hardware.  Useful wiki for setting up this card is here:

[http://mythkiwi.com/index.php?option=com_joomlawiki&Itemid=14](http://mythkiwi.com/index.php?option=com_joomlawiki&Itemid=14)

I'm guessing that the last part will solve your problem, I think that was the major problem for me.

---

### Post by gp0 on 2009-03-23
Had the same problem, turns out i had the correct lircrc in /home/mythtv/ but not in _my_ home dir. So i did cp /home/mythtv/.lircrc /home/myuser/.mythtv/lircrc which fixed it.

(Figured it out by starting mythfrontend in a console)

---

### Post by wildbillkelso on 2010-05-28
Hi all.

I am having a similar problem. I did have my remote working fine in 9.10 but had to do a clean install. The remote worked fine before when I deleted LIRC and reinstalled it and set the remote up again in the IR control centre. Now when I do the same thing after the clean install only the arrow buttons work.

Any ideas greatfully appreciated.

Best regards.

Tim

---

### Post by wyliecoyoteuk on 2010-06-01
If only the arrow buttons work, lircd is either not running or is incorrectly configured.
The kernel driver allows the arrows and some other keys.
[look here](http://ubuntuforums.org/showthread.php?t=1140411&highlight=NOVA-T+500)especially the last post.

---

### Post by wildbillkelso on 2010-06-01
Thanks for the link wyliecoyoteuk.

I had a look at it and it turned out to be the hardware config. when I ran cat /proc/bus/input/devices it said "input/input3" which I had edited into the hardware config rather than "input/event3". I ran irw and all is well now thank you. A silly mistake but I learned a lot in the process of investigating the issue.

Many thanks.

Tim

---


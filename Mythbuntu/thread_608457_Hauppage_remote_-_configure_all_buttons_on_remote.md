---
title: "Hauppage remote - configure all buttons on remote"
date: 2007-11-10
forum: Mythbuntu
---

### Post by rossco on 2007-11-10
Hi all,

I'm just having a little trouble getting my remote to work correctly.  I am running mythbuntu 7.10 which is my second install (long story).  I used mythbuntu control centre to select the remote which gets about half of the buttons to work correctly.  I have a grey hauppage remote (TV Card Nova-S) and have tried a number of different things posted in other forums but everything I tried just seemed to wreck it.  I guess that when I change the remote settings in the control centre that it overrides any changes I've made and the remote works again.  I have tried using irw but get a connection refused error so I haven't been able to see if all the buttons are configured correctly.  My ~/.mythtv/lircrc file reads:

> 
begin
    remote = NOVA-T500
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowRight
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = SkipBack
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelDown
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = BackExit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelUp
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Fwdwind
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowLeft
    config = Left
    repeat = 0
    delay = 0
end


And my /etc/lircd.conf file reads:

> 
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
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


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R [www.mythtvportal.com](www.mythtvportal.com)
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
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
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg [www.lugv.at](www.lugv.at)
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


---

### Post by Zelgadis on 2007-11-10
It'd be nice if you listed at least a few of the buttons that don't work.  For my MCE remote, a lot of the buttons don't work.  I found I have to add code to the lircrc for each button.

For example, my Back button didn't do anything so I had to add:

begin
remote = NOVA-T500
prog = mythtv
button = Back
config = Escape
repeat = 0
delay = 0
end

Of course, I didn't use NOVA-T500 as my remote.

I was basically guessing for what to call the "Back" button but it worked.

I finally got around to taking a look and it seems there's a list of the names of buttons and such on the lirc site.  You should probably check the conf files on this page. [http://lirc.sourceforge.net/remotes/hauppauge/](http://lirc.sourceforge.net/remotes/hauppauge/)

I hope this helps.

Edit:  Oh right, you listed your conf file in your post which has all the buttons listed in it.  So, you didn't really need that link.

---

### Post by superm1 on 2007-11-10
> **Zelgadis said:**
> It'd be nice if you listed at least a few of the buttons that don't work.  For my MCE remote, a lot of the buttons don't work.  I found I have to add code to the lircrc for each button.

For example, my Back button didn't do anything so I had to add:

begin
remote = NOVA-T500
prog = mythtv
button = Back
config = Escape
repeat = 0
delay = 0
end

Of course, I didn't use NOVA-T500 as my remote.

I was basically guessing for what to call the "Back" button but it worked.

I finally got around to taking a look and it seems there's a list of the names of buttons and such on the lirc site.  You should probably check the conf files on this page. [http://lirc.sourceforge.net/remotes/hauppauge/](http://lirc.sourceforge.net/remotes/hauppauge/)

I hope this helps.

Edit:  Oh right, you listed your conf file in your post which has all the buttons listed in it.  So, you didn't really need that link.

Can you please file a bug against mythbuntu-lirc-generator and be specific about what buttons don't work, what you want them to be doing and such?  I've got a mceusb2 remote myself, and when m-l-g was built, that was my remote to test against :).  So it functions about as much as I would have expected.

---

### Post by superm1 on 2007-11-10
> **rossco said:**
> Hi all,

I'm just having a little trouble getting my remote to work correctly.  I am running mythbuntu 7.10 which is my second install (long story).  I used mythbuntu control centre to select the remote which gets about half of the buttons to work correctly.  I have a grey hauppage remote (TV Card Nova-S) and have tried a number of different things posted in other forums but everything I tried just seemed to wreck it.  I guess that when I change the remote settings in the control centre that it overrides any changes I've made and the remote works again.  I have tried using irw but get a connection refused error so I haven't been able to see if all the buttons are configured correctly.  My ~/.mythtv/lircrc file reads:



And my /etc/lircd.conf file reads:
For irw try it like this:
```
irw /dev/lircd
```

(While lirc is running)

If some buttons end up not being listed there when you press buttons, then there is a bug with your lircd.conf.


In m-c-c, whenever you switch remotes, your lircd.conf is overwritten.  Also, that check box below the remote switching area will overwrite your ~/.lircrc and ~/.mythtv/lircrc.

The old ones are backed up in the directory, just take a look around.  

Also, please when you sort this out, if the lircd.conf has troubles file a bug against lirc with your functional lircd.conf attached.

If the lircrc is the troublesome part, file a bug against mythbuntu-lirc-generator with the lircrc that works as expected attached.

---

### Post by rossco on 2007-11-11
> **superm1 said:**
> For irw try it like this:
```
irw /dev/lircd
```

(While lirc is running)

If some buttons end up not being listed there when you press buttons, then there is a bug with your lircd.conf.


In m-c-c, whenever you switch remotes, your lircd.conf is overwritten.  Also, that check box below the remote switching area will overwrite your ~/.lircrc and ~/.mythtv/lircrc.

The old ones are backed up in the directory, just take a look around.  

Also, please when you sort this out, if the lircd.conf has troubles file a bug against lirc with your functional lircd.conf attached.

If the lircrc is the troublesome part, file a bug against mythbuntu-lirc-generator with the lircrc that works as expected attached.

I assume that lirc is running (how do I tell?) since the remote is working even when the front end is not running as the up and down buttons on the remote work like the up and down arrows on the keyboard.

Yeah I saw other config files in the directory but I assumed that they wouldn't be useful since since I have installed the system I haven't had all the buttons running at any time.

The buttons that work seem to be the ones listed under the remote "Hauppauge" at the top of the config file.  What I need is something like one of the remotes listed below that.  But unless I can get irw to work I can't tell which of the remotes suits best.  (irw /dev/lircd didn't work, still says connection refused).

---

### Post by superm1 on 2007-11-11
> **rossco said:**
> I assume that lirc is running (how do I tell?) since the remote is working even when the front end is not running as the up and down buttons on the remote work like the up and down arrows on the keyboard.

Yeah I saw other config files in the directory but I assumed that they wouldn't be useful since since I have installed the system I haven't had all the buttons running at any time.

The buttons that work seem to be the ones listed under the remote "Hauppauge" at the top of the config file.  What I need is something like one of the remotes listed below that.  But unless I can get irw to work I can't tell which of the remotes suits best.  (irw /dev/lircd didn't work, still says connection refused).
Um.  If the buttons on the remote are working without lirc running, the remote is recognized as a native kernel input device.  

Can you run xev and press those buttons?  If they show up in the list, your remote may be natively detected by linux.

---

### Post by Zelgadis on 2007-11-11
> **superm1 said:**
> Can you please file a bug against mythbuntu-lirc-generator and be specific about what buttons don't work, what you want them to be doing and such?  I've got a mceusb2 remote myself, and when m-l-g was built, that was my remote to test against :).  So it functions about as much as I would have expected.
Sorry, I don't know where to file a bug report at.  Also, I haven't tested all the buttons yet but I know that the Back, Recorded TV, Live TV, Skip, Replay buttons appear to  do nothing and Channel Up/Down buttons do time skips instead of changing channels.  I linked to the image of my remote from the MythTV wiki below.  I don't think any of the buttons function on the desktop.  It would be nice to have some way to reboot or shutdown the computer using just the remote but I haven't found a way to do that.  If I could reboot/shut down the computer with the remote then I wouldn't really need the keyboard and mouse anymore.  Two suggestions for accomplishing this would be, to allow the Start(Windows Logo) button bring up the Applications menu and then use the Arrow buttons and OK button to navigate the menu and the other being to have a menu inside MythTV for Shutting Down/Rebooting.

[http://mythtv.org/wiki/images/d/d8/MCE-Remote-2-alt.jpg](http://mythtv.org/wiki/images/d/d8/MCE-Remote-2-alt.jpg)

---

### Post by rossco on 2007-11-12
xev output:
> 
myserver@myserver:~$ xev
... some removed so I can post ...

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x153 (_WIN_WORKSPACE), time 839873473, state PropertyNewValue

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0xeb (_NET_WM_DESKTOP), time 839873473, state PropertyNewValue

ConfigureNotify event, serial 15, synthetic NO, window 0x2200001,
    event 0x2200001, window 0x2200001, (0,0), width 178, height 178,
    border_width 0, above 0x1a00001, override NO

ReparentNotify event, serial 15, synthetic NO, window 0x2200001,
    event 0x2200001, window 0x2200001, parent 0xe00589,
    (6,27), override NO

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x134 (_NET_WM_ALLOWED_ACTIONS), time 839873474, state PropertyNewValue

ConfigureNotify event, serial 15, synthetic NO, window 0x2200001,
    event 0x2200001, window 0x2200001, (6,27), width 178, height 178,
    border_width 0, above 0xe00597, override NO

ConfigureNotify event, serial 15, synthetic YES, window 0x2200001,
    event 0x2200001, window 0x2200001, (551,447), width 178, height 178,
    border_width 0, above 0xe00589, override NO

MapNotify event, serial 15, synthetic NO, window 0x2200001,
    event 0x2200001, window 0x2200001, override NO

VisibilityNotify event, serial 15, synthetic NO, window 0x2200001,
    state VisibilityUnobscured

Expose event, serial 15, synthetic NO, window 0x2200001,
    (0,0), width 178, height 10, count 3

Expose event, serial 15, synthetic NO, window 0x2200001,
    (0,10), width 10, height 58, count 2

Expose event, serial 15, synthetic NO, window 0x2200001,
    (68,10), width 110, height 58, count 1

Expose event, serial 15, synthetic NO, window 0x2200001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x6d (WM_STATE), time 839873478, state PropertyNewValue

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0xf1 (_NET_WM_STATE), time 839873478, state PropertyNewValue

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x151 (_WIN_STATE), time 839873478, state PropertyNewValue

FocusIn event, serial 15, synthetic NO, window 0x2200001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 15, synthetic NO, window 0x0,
    keys:  4294967170 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x126 (_NET_FRAME_EXTENTS), time 839873478, state PropertyNewValue

PropertyNotify event, serial 15, synthetic NO, window 0x2200001,
    atom 0x136 (_NET_WM_ICON_GEOMETRY), time 839873506, state PropertyNewValue

KeyPress event, serial 28, synthetic NO, window 0x2200001,
    root 0x155, subw 0x0, time 839878081, (-179,-59), root:(372,388),
    state 0x0, keycode 98 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x2200001,
    root 0x155, subw 0x0, time 839879545, (-179,-59), root:(372,388),
    state 0x0, keycode 104 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

X connection to :0.0 broken (explicit kill or server shutdown).


I think you may be right about it being recognised as a native kernel input device.  I tried disabling the remote in m-c-c and the remote still works.  Any ideas on how to disable/fix it?

---

### Post by rossco on 2007-11-14
I found a link ([here]("http://kernelnewbies.org/Linux_2_6_16")) detailing the changes in the latest Linux kernel.  Under the "V4L/DVB" heading it says IR support was added for Hauppage Nova-S-Plus card.  Any ideas on what config file I need to edit to get all the buttons to work or should I try another forum?

---

### Post by rossco on 2007-11-14
I also found this [link]("http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers") which gives some background on the situation but since I am a newbie I can't quite figure it all out.  But it might help you to figure it out.  

It seems to me that the kernel is not using lirc but another driver and interprets the keypresses on the remote as keyboard strokes.  Which agrees with what I found when using irw the direction keys on the remote gave the same output as the direction keys on the keyboard.

---

### Post by road2elysium on 2007-11-14
> **rossco said:**
> I assume that lirc is running (how do I tell?) since the remote is working even when the front end is not running as the up and down buttons on the remote work like the up and down arrows on the keyboard.


Depending on how your remote/IR receiver is recognized by the kernel, up and down buttons on the remote could be translated w/o the help of lirc.  To check if lirc is indeed running, run:
```
ps aux | grep lirc
```

> **rossco said:**
> 
It seems to me that the kernel is not using lirc but another driver and interprets the keypresses on the remote as keyboard strokes.  Which agrees with what I found when using irw the direction keys on the remote gave the same output as the direction keys on the keyboard.

You might want to take a look at how the kernel is recognizing your IR receiver.
```
lsusb
```
```
lsusb -D /proc/usb/00?/00?
```

You can also check which kernel modules are loaded by grep-ing through:
```
lsmod
```
in case you're not using the Mythbuntu Control Center and are changing things manually.

Just some thoughts.  Hope it helps.

---

### Post by rossco on 2007-11-28
Hi everybody,

Thanks for all your advice.  I managed to get the remote to work properly.  I used this [link]("http://parker1.co.uk/mythtv_ubuntu2.php") to get it to work.  The kernel recognises the remote for my card (Nova-S-Plus) as a 'keyboard'.  The important part from the guide is to do:

> cat /proc/bus/input/devices

And look for the event number for the correct input device and enter it into the hardware.conf file.  The config files I used from this guide are:

[/etc/lirc/hardware.conf]("http://parker1.co.uk/myth/hardware.conf")
[~/.lircrc]("http://parker1.co.uk/myth/lircrc")
[/etc/lirc/lircd.conf]("http://parker1.co.uk/myth/lircd.conf.2")

I haven't changed the name of the remote from hauppauge_nova_t_uk  which relates to the Nova-T card in my config file as I am just enjoying that it works now.  I checked using irw that all of the buttons are recognised and they are correctly identified.  I think I might just need to modify the .lircrc file to suit my tastes.

Let me know if I should still file a bug report as I haven't done that before.  In between figuring this out I reinstalled Windows XP and tried to get MediaPortal to work but Mythbuntu is far better now that I have a taste for it!

---

### Post by superm1 on 2007-11-28
> **rossco said:**
> Hi everybody,

Thanks for all your advice.  I managed to get the remote to work properly.  I used this [link]("http://parker1.co.uk/mythtv_ubuntu2.php") to get it to work.  The kernel recognises the remote for my card (Nova-S-Plus) as a 'keyboard'.  The important part from the guide is to do:



And look for the event number for the correct input device and enter it into the hardware.conf file.  The config files I used from this guide are:

[/etc/lirc/hardware.conf]("http://parker1.co.uk/myth/hardware.conf")
[~/.lircrc]("http://parker1.co.uk/myth/lircrc")
[/etc/lirc/lircd.conf]("http://parker1.co.uk/myth/lircd.conf.2")



Let me know if I should still file a bug report as I haven't done that before.  In between figuring this out I reinstalled Windows XP and tried to get MediaPortal to work but Mythbuntu is far better now that I have a taste for it!
Yes please file a bug against mythbuntu. We can attempt to address this later on to be automatic for a future release. Please attach any relevant items that you had to change, ad well as any information that you used to figure out what event device you had to use. Also be sure to respond to bug mail with what more will be needed. Offhand I can't think of anything else but we might not get to this for a while so just keep your eyes peeled.

---

### Post by Daminator on 2007-11-28
I've never managed to get my remote to work. Pre or post Mythbuntu. I was hoping that Mythbuntu would sort it out (one of my main reasons for installing it on top of my Ubuntu/Mythtv system), but still nothing. I have number keys and directional key working, but pretty much nothing else so I have to use my keyboard all or the time.

I was hoping that this thread would lead to an answer, but it has lead to another dead end.

I have 2 Hauppage Nova-t cards in my machine and a long ir cable coming out of one of them (I actually spliced two together to make it long enough, but there is input getting in so i don't think that's causing a problem).

I have just re-looked at the parker site and ran
cat /proc/bus/input/devices

where I find I have 2 Hauppage entries (to be expected), on event 5 and evern6.

Running
sudo evetest /dev/input/event5
doesn't do much, but
sudo evetest /dev/input/event6
fills me with hope. Everything I press suddenly does give me a response! I don't understand the responses, but they're there :-)

However, when I go down further to the part where it says:
As usual, we'll give it a quick test ...
sudo /usr/sbin/lircd -H dev/input -d /dev/input/event2 -n
and (in another terminal)
irw
"Press some buttons and you should see the events displayed"
Well, I see nothing at all displayed! Not even the numbers and cursor keys giving any input now!

I tried looking at the hardware.conf from the parker site and editing mine to include the 'event6', but I've rebooted and now my remote is doing nothing.

Can anyone tell me what's going on here?

Hope I'm not hijacking the thread, but I thought these problems might be in ther right ball park. I'll start a new thread if no one can help in here.

Cheers
Damian

---

### Post by rossco on 2007-11-29
Hey Daminator,

Sorry you're having trouble too.  I will try and help you out as best I can.  If you've got Mythbuntu go to the control centre and on the remote section select your remote again and check the box at the bottom which will recreate all the config files and hopefully fix your remote again.  Let me know if it doesn't.  That way we at least know we can repair any damage we do.

Also I didn't do much of the checking steps that are on the parker site.  I just used the files from the parker site directly assuming that they would work (use the second .lircd.conf file if your cards are new like mine).  Then once you have copied the files to the correct locations (note that lircrc files needs to be in two locations as in the guide), either restart the PC or type something like "sudo /etc/init.d/lirc restart" and then type irw and see what kind of output you get.

note: don't forget to modify the event# in the hardware.conf file.

---

### Post by Daminator on 2007-11-30
I don't know what I did differently to the last time I followed that guide, but I've finally got my remote working.
I'm putting it down to having a bit more linux experience under my belt, helping me to actually put the right files in the right place this time.

Cheers
Damian

---

### Post by rossco on 2007-11-30
Hey Damian,

Glad you got it to work.  I guess I have to go and log a bug report about it now.  I guess we know that this method works for both of us.

Regards
Ross

---

### Post by spinlock99 on 2007-11-30
> **superm1 said:**
> For irw try it like this:
```
irw /dev/lircd
```

(While lirc is running)



Dude!!!!  I just tried this and every button on my Hauppauge remote just worked.  On the first try.  I can control everything in MythTV.  And I didn't do any configuration (which is probably why it works ;-).

---

### Post by rossco on 2007-11-30
> **spinlock99 said:**
> Dude!!!!  I just tried this and every button on my Hauppauge remote just worked.  On the first try.  I can control everything in MythTV.  And I didn't do any configuration (which is probably why it works ;-).

Does it work on reboot or do you have to type it every time?

---

### Post by rossco on 2007-12-01
I had to follow the link at the bottom of the parker guide since my "event#" has started to change.  The guide worked first time for me (when I typed the correct line in the config file).

---

### Post by spinlock99 on 2007-12-01
> **rossco said:**
> Does it work on reboot or do you have to type it every time?

It works after reboot.  I was really amazed because I just dug the ir receiver out of a shoe box that I keep spare cables in.  The only "tweek" that I've done to the setup was to put fresh batteries in the remote.

---

### Post by rossco on 2007-12-02
It didn't seem to work for me.  Maybe your card is an older version than mine?

---

### Post by superm1 on 2007-12-02
> **rossco said:**
> It didn't seem to work for me.  Maybe your card is an older version than mine?
Be sure to update to the new mythbuntu-lirc-generator and then "regenerate you dynamic button mappings".  After doing so, you should be able to hopefully use your remote.

---


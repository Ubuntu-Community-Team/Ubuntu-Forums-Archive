---
title: "MCE remote: trying to program extra buttons in lirc"
date: 2007-11-18
forum: Mythbuntu
---

### Post by pssturges on 2007-11-18
Hi,

I'm trying to program the Red, Green, Yellow & Blue buttons on my MCE remote. All the other buttons are functioning correctly, but when I add these new buttons to my .lircrc, i get no result in mythtv. Using irw, they work correctly, just not in Myth. Below is my .lircrc (an example of what I am trying to do is shown at the begining):
```


#
#New Keys
##################################################################################
begin
	prog = mythtv
	button = Green	0x00007ba3
	config = j
end



# lircrc config file for the Microsoft Media Center Edition Remote, model 1039
#
# Modified By Dale Jefferson at efficientpc.co.uk
# Email: dale@efficientpc.co.uk
#
# This file is intended to complement the lircd.conf.mceusb file included with
# lirc 0.8 and above.
#
# Save this file in ~/.mythtv/lircrc
#
# You will also need to make a few changes to the MythTV key bindings and jump
# points as follows.
#
# Jump Points:
#
#   TV Recording Playback:                      Alt+R
#   Program Guide:                              Alt+G
#   Live TV:                                    Alt+P
#   MythVideo -> The MythVideo default view:    Alt+V
#   Main Menu:                                  Alt+Home
#
# Key Bindings:
#
#   TV Playback -> CHANNELDOWN:  Down,PgDown
#   TV Playback -> CHANNELUP:    Up,PgUp
#   TV Playback -> JUMPRWND:     Shift+PgUp
#   TV Playback -> JUMPFFWD:     Shift+PgDown
#

###################################################################
# Begin of mythtv key bindings.
##

#
# Program Navigation
#

begin
    prog   = mythtv
    button = Home
    config = Alt+Home
end

begin
    prog   = mythtv
    button = RecTV
    config = Alt+R
end

begin
    prog   = mythtv
    button = Guide
    config = Alt+G
end

begin
    prog   = mythtv
    button = LiveTV
    config = Alt+P
end

begin
    prog   = mythtv
    button = DVD
    config = Ctrl+3
end

#
# Menu Navigation
#

begin
    prog   = mythtv
    button = Back
    config = Esc
end

begin
    prog   = mythtv
    button = OK
    config = Space
end

begin
    prog   = mythtv
    button = More
    config = I
end

begin
    prog   = mythtv
    button = Left
    config = Left
end

begin
    prog   = mythtv
    button = Right
    config = Right
end

begin
    prog   = mythtv
    button = Up
    config = Up
end

begin
    prog   = mythtv
    button = Down
    config = Down
end

#
# TV Control
#

begin
    prog   = mythtv
    button = VolDown
    config = F10
end

begin
    prog   = mythtv
    button = VolUp
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
    config = Alt+Esc
end

begin
    prog   = mythtv
    button = Hash
    config = M
end

begin
    prog   = mythtv
    button = Power
    config = Alt+Esc
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

##
# End of mythtv key bindings.
##

###################################################################
# Begin of mplayer key bindings.
##

begin
 prog = mplayer
 button = Back
 config = quit
end

begin
 prog = mplayer
 button = More
 config = osd
end

begin
 prog = mplayer
 button = Replay
 config = seek -10
 repeat = 1
end

begin
 prog = mplayer
 button = Skip
 config = seek +10
 repeat = 1
end

begin
 prog = mplayer
 button = Rewind
 config = seek -60
 repeat = 1
end

begin
 prog = mplayer
 button = Forward
 config = seek +60
 repeat = 1
end

begin
 prog = mplayer
 button = Pause
 config = pause
end

begin
 prog=mplayer
 button=Mute
 config=mute
end

##
# End of mplayer key bindings.
##

###################################################################
# Begin of xmms key bindings.
##
# Thanks to Elliot Taylor

begin
     button = Skip
     prog = xmms
     config = next
end
begin
     button = Play
     prog = xmms
     config = play
end
begin
     button = Replay
     prog = xmms
     config = prev
end
begin
     button = Pause
     prog = xmms
     config = pause
end
begin
     button = More
     prog = xmms
     config = SAYTITLE
end
begin
     button = Stop
     prog = xmms
     config = stop
end
begin
     button = Forward
     prog = xmms
     config = fwd 3
end
begin
     button = Rewind
     prog = xmms
     config = bwd 3
end

#begin
#     button = Red
#     prog = xmms
#     config = repeat
#end

begin
     button = EDIT
     mode = nobounce
end


begin nobounce
begin
     button = Forward
     prog = xmms
     config = fwd 3
     flags =  mode
end
begin
     button = Rewind
     prog = xmms
     config = bwd 3
     flags =  mode
end
begin
     button = Skip
     prog = xmms
     config = next
     flags =  mode
end
begin
     button = PLAY
     prog = xmms
     config = play
     flags =  mode
end
begin
     button = Replay
     prog = xmms
     config = prev
     flags =  mode
end
begin
     button = Pause
     prog = xmms
     config = pause
     flags =  mode
end
begin
     button = Stop
     prog = xmms
     config = stop
     flags =  mode
end
begin
     button = Green
     prog = xmms
     config = shuffle
     flags =  mode
end

#begin
#     button = Red
#     prog = xmms
#     config = repeat
#     flags =  mode
#end

begin
     button = Back
     prog = xmms
     config = PLAYLIST_REMOVE
     flags =  mode
end
end nobounce
##
# End of xmms key bindings.
##

```

I have tried it without the '0x00007ba3" also with the same result.

There are another couple of things that I would like to achieve also. I would like to have the start button launch Myth.

I would also like to have the power button bring up the shutdown/reboot/logoff etc window when not in Myth, then be able to select the appropriate option. Put simply I want to be able to reboot or shut down using the remote. 

Can any of this be done?

Thanks
Phil

---

### Post by pssturges on 2007-11-19
Well I managed to solve the major problem. The colour keys are now programmed. However I'm still interested in the other questions if anyone has some ideas.

Phil

---

### Post by superm1 on 2007-11-19
Can you please file a bug against mythbuntu-lirc-generator to include the mappings you made for the colored buttons?  You aren't the first person to mention this, so it would be useful for us to have mappings to attempt to target for a future release.

Please list any relevant information (what remote you've chosen, what you've overridden etc)

As for having buttons to perform other actions:

Look into irexec for launching applications.  The automatic myth login script will handle starting it if it detects irexec usage anywhere within the lircrc.

So add your irexec blocks into the lircrc, and then log out and back in.  Irexec will be started for you.

You will probably want a wrapper script that will check if myth is already running, and if it is, then it doesn't relaunch the frontend.

As for turning off the system, have irexec call a wrapper script check if mythfrontend is running, and if its not, then have it launch xfce4-session-logout

Please do also post any of these changes you make to your lircrc files into this thread for others to benefit.  Also if you are inclined to do so, file a bug against mythbuntu with the changes for the turning off the system.  Once you sort that out and have it working for you, I think it is definitely something we can look into having implemented for hardy.

---

### Post by s_g_robertson on 2007-11-19
> **pssturges said:**
> Well I managed to solve the major problem. The colour keys are now programmed. However I'm still interested in the other questions if anyone has some ideas.

Phil

What did you have to do to get that to work?

Thanks
Stephen

---

### Post by pssturges on 2007-11-19
As far as getting the colour buttons to work, it wasn't a bug, it was a problem with my .lircrc.  I generated those blocks with the online lircr generator on a windows pc. Copy & pasted to a new file? (I can't remember the exact process). Short answer there were some characters in the file that didn't appear in gedit. So I retyped them manually and they worked!

Here's how it looks now:
```

begin
	prog = mythtv
	button = Red
	config = Alt+M
end

begin
	prog = mythtv
	button = Green
	config = Alt+J
end

begin
	prog = mythtv
	button = Yellow
	config = +
end

begin
	prog = mythtv
	button = Blue
	config = w
end

```


superm1,

Thanks for the info. I have never written a script before, although happy to give it a go if its not too hard. I thought I'd start simply though. I tried to program the keys using irexec, but it seems irexec is not running automatically. When I start it manually, then it works. Mythfrontend launches nicely when I press the home key. There are still a few other issues to sort out.

Firstly, I have the power button programed to close Mythfronend. So now with irexec and mythfronend running, when I press the power button Mythfronend tries to close and the log out screen pops up. I guess the way around this would be to have some sort of script that has irexec running only when mythfrontend is not? Anyway that's way beyond my capabilities atm.

Secondly, once the logout screen pops up, you need to be able to navigate around the window with the arrow keys & select the desired option with the OK key. So I tried adding appropriate entries to my .lircrc, but with no luck. Posted below are those entries:

```

begin
	prog = irexec
	button = Home
	config = mythfrontend
end

begin
	prog = xfce4-session-logout
	button = Left
	config = Left
end

begin
	prog = xfce4-session-logout
	button = Right
	config = Right
end

begin
	prog = xfce4-session-logout
	button = Down
	config = Down
end

begin
	prog = xfce4-session-logout
	button = Up
	config = Up
end

begin
	prog = xfce4-session-logout
	button = OK
	config = Enter
end

```

Another little issue, and I doubt this can be fixed easily, is that when the logout screen pops up, the little dotted line around the selected item is impossible to see on my 1080i TV from the lounge! Something a bit clearer would be nice.

Once again, any help appreciated,
Phil

---

### Post by pssturges on 2007-11-21
> **pssturges said:**
>  I tried to program the keys using irexec, but it seems irexec is not running automatically. When I start it manually, then it works. 


Working fine now. Dunno why. Just started working!

> **pssturges said:**
> 
Firstly, I have the power button programed to close Mythfronend. So now with irexec and mythfronend running, when I press the power button Mythfronend tries to close and the log out screen pops up. I guess the way around this would be to have some sort of script that has irexec running only when mythfrontend is not?

I guess this would also solve the problem of potentially launching mythfrontend when it's already running?

Phil

---

### Post by superm1 on 2007-11-21
> **pssturges said:**
> As far as getting the colour buttons to work, it wasn't a bug, it was a problem with my .lircrc.  I generated those blocks with the online lircr generator on a windows pc. Copy & pasted to a new file? (I can't remember the exact process). Short answer there were some characters in the file that didn't appear in gedit. So I retyped them manually and they worked!

Here's how it looks now:
```

begin
    prog = mythtv
    button = Red
    config = Alt+M
end

begin
    prog = mythtv
    button = Green
    config = Alt+J
end

begin
    prog = mythtv
    button = Yellow
    config = +
end

begin
    prog = mythtv
    button = Blue
    config = w
end

```
superm1,

Thanks for the info. I have never written a script before, although happy to give it a go if its not too hard. I thought I'd start simply though. I tried to program the keys using irexec, but it seems irexec is not running automatically. When I start it manually, then it works. Mythfrontend launches nicely when I press the home key. There are still a few other issues to sort out.

Firstly, I have the power button programed to close Mythfronend. So now with irexec and mythfronend running, when I press the power button Mythfronend tries to close and the log out screen pops up. I guess the way around this would be to have some sort of script that has irexec running only when mythfrontend is not? Anyway that's way beyond my capabilities atm.

Secondly, once the logout screen pops up, you need to be able to navigate around the window with the arrow keys & select the desired option with the OK key. So I tried adding appropriate entries to my .lircrc, but with no luck. Posted below are those entries:

```

begin
    prog = irexec
    button = Home
    config = mythfrontend
end

begin
    prog = xfce4-session-logout
    button = Left
    config = Left
end

begin
    prog = xfce4-session-logout
    button = Right
    config = Right
end

begin
    prog = xfce4-session-logout
    button = Down
    config = Down
end

begin
    prog = xfce4-session-logout
    button = Up
    config = Up
end

begin
    prog = xfce4-session-logout
    button = OK
    config = Enter
end

```Another little issue, and I doubt this can be fixed easily, is that when the logout screen pops up, the little dotted line around the selected item is impossible to see on my 1080i TV from the lounge! Something a bit clearer would be nice.

Once again, any help appreciated,
Phil
Well so the thing is, the logout dialog doesn't support lirc.  I'm not sure how to get the remote to work there.  Irxevent is probably something to investigate.

---

### Post by deffcon on 2007-11-22
Hi all,

Could you please post you're whole .lircrc, because i also have the 1039 model with the coloured buttons, and this part of you're .lircrc look better then the one from mythbuntu-lirc-gereator.

Thnx in advance,

Dave

---

### Post by road2elysium on 2007-11-26
> **superm1 said:**
> 

Look into irexec for launching applications.  The automatic myth login script will handle starting it if it detects irexec usage anywhere within the lircrc.

So add your irexec blocks into the lircrc, and then log out and back in.  Irexec will be started for you.

As for turning off the system, have irexec call a wrapper script check if mythfrontend is running, and if its not, then have it launch xfce4-session-logout


I just set this up and it works flawlessly.  Adding an irexec block to your .lircrc will indeed cause irexec to start up on boot.  From there I just wrote a bash script to ```
sudo shutdown -P now
```.

Note that you will have to either chmod the sbin/shutdown file or edit the /etc/sudoers files with ```
sudo visudo
```.

Add the folllowing line to that file:
```
username ALL = NOPASSWD: /sbin/shutdown
```

Oh, and don't forget to make your script executable ;)

---

### Post by DasCrushinator on 2008-02-19
I know this thread is old, but is it possible to have the Start button (Green) launch Nautilus (preferably to a specified location) and have the up down keys (while in Nautilus) go up or down to select files?  Also, have the Ok/Select key open the file?

Thanks!

---

### Post by superm1 on 2008-02-19
With a combination of irexec and irxevent sure.  But that's all you'll be able to do with it.

---

### Post by DasCrushinator on 2008-02-19
> **superm1 said:**
> With a combination of irexec and irxevent sure.  But that's all you'll be able to do with it.

You mean I wouldn't be able to control MPlayer with it set up like that?

---

### Post by superm1 on 2008-02-20
Well nautilus doesn't natively have lirc support.  irxevent instead emulates a keyboard.  When you do this though, its sort of an "all or nothing" approach.  You can't natively use lirc with any other apps, instead you have to set up the keybindings to match the same thing across all your apps.  Eg if right means go right in nautilus, you will need to set the mplayer mapping of right to be something that makes sense for pressing right in mplayer on the remote.

---

### Post by DasCrushinator on 2008-02-20
> **superm1 said:**
> Well nautilus doesn't natively have lirc support.  irxevent instead emulates a keyboard.  When you do this though, its sort of an "all or nothing" approach.  You can't natively use lirc with any other apps, instead you have to set up the keybindings to match the same thing across all your apps.  Eg if right means go right in nautilus, you will need to set the mplayer mapping of right to be something that makes sense for pressing right in mplayer on the remote.

Ahh, I see.  Appreciate your help :)

---


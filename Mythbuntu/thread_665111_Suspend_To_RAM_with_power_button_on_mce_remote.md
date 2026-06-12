---
title: "Suspend To RAM with power button on mce remote"
date: 2008-01-11
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-11
I would like my myth box to suspend when I press a button (preferably my power button) on my remote. 

this is about the same remote that I have:
[IMG]http://www.mythtv.org/wiki/images/d/d8/MCE-Remote-2-alt.jpg[/IMG]

I found this guide in the wiki, but I don't want to break anything. 
I am not sure what the "pc" button is on the mce remote. I am sure some one on here has this set up. I think my stop button is being seen as the "power" button since it seems to be used a lot but I am not sure.

```

 S3 / Suspend To RAM

This section will allow you to press the "PC" button on your MCE Remote and suspend to RAM in about one second. All fans are off, power is only minimally keeping your RAM refreshed, and your PC is silent. You can then press the "PC" button again to return to the same place in MythTV in about one second. Beats shutting down and booting up to save power. I am a Gentoo user, so only use this as an example. Since kernel 2.6.23, you need to enable deprecated /proc/acpi systems. Also, if using recent nvidia proprietary drivers, you can remove it from hibernate's blacklisted modules. Be sure irexec is running, you can add this in your .xinitrc:

irexec -d

In your lircrc, add this:

begin
 button = Power
 prog = irexec
 repeat = 0
 config = sudo /usr/sbin/hibernate-ram
end

In order for the button to wake, you need to specify the USB hub in /proc/acpi/wakeup. If you cat /proc/acpi/wakeup, you should see something like this:

Device  S-state   Status   Sysfs node
HUB0      S5     disabled  pci:0000:00:08.0
HUB1      S4     disabled
USB0      S3     disabled  pci:0000:00:02.0
USB1      S3     disabled  pci:0000:00:02.1

If you issue the following command, the disable status will toggle to enabled

echo USB0 > /proc/acpi/wakeup

Should result in:

Device  S-state   Status   Sysfs node
HUB0      S5     disabled  pci:0000:00:08.0
HUB1      S4     disabled
USB0      S3     enabled   pci:0000:00:02.0
USB1      S3     disabled  pci:0000:00:02.1

This command can be saved in your local.start

It also might be useful to change the MythTV exit settings to issue hibernate-ram on shutdown 
```



and here is my lircd.config

```


#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
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

begin remote

 name mceusb
 bits           16
 flags RC6|CONST_LENGTH
 eps            30
 aeps          100

 header       2667   889
 one           444   444
 zero          444   444
 pre_data_bits 21
 pre_data      0x37FF0
 gap          105000
 toggle_bit     22
 rc6_mask     0x100000000


     begin codes

       Blue    0x00007ba1
       Yellow  0x00007ba2
       Green   0x00007ba3
       Red     0x00007ba4
       Teletext        0x00007ba5

# starts at af
       Radio    0x00007baf
       Print    0x00007bb1
       Videos   0x00007bb5
       Pictures 0x00007bb6
       RecTV    0x00007bb7
       Music    0x00007bb8
       TV       0x00007bb9
# no ba - d8

       Guide    0x00007bd9
       LiveTV   0x00007bda
       DVD      0x00007bdb
       Back     0x00007bdc
       OK       0x00007bdd
       Right    0x00007bde
       Left     0x00007bdf
       Down     0x00007be0
       Up       0x00007be1

       Star       0x00007be2
       Hash       0x00007be3

       Replay   0x00007be4
       Skip     0x00007be5
       Stop     0x00007be6
       Pause    0x00007be7
       Record   0x00007be8
       Play     0x00007be9
       Rewind   0x00007bea
       Forward  0x00007beb
       ChanDown 0x00007bec
       ChanUp   0x00007bed
       VolDown  0x00007bee
       VolUp    0x00007bef
       More     0x00007bf0
       Mute     0x00007bf1
       Home     0x00007bf2
       Power    0x00007bf3
       Enter    0x00007bf4
       Clear    0x00007bf5
       Nine     0x00007bf6
       Eight    0x00007bf7
       Seven    0x00007bf8
       Six      0x00007bf9
       Five     0x00007bfa
       Four     0x00007bfb
       Three    0x00007bfc
       Two      0x00007bfd
       One      0x00007bfe
       Zero     0x00007bff
     end codes

end remote


```

here is my .lircrc

```

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
   delay = 0
end

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

begin
   remote = mceusb
   prog = mplayer
   button = Play
   config = pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Pause
   config = pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = OK
   config = pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Power
   config = quit
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Mute
   config = mute
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = VolDown
   config = volume -1
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Skip
   config = seek +15 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Enter
   config = pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Stop
   config = quit
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Up
   config = seek +60 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = VolUp
   config = volume +1
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Down
   config = seek -60 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Replay
   config = seek -15 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Right
   config = seek +6 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Rewind
   config = seek -30 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Forward
   config = seek +30 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Home
   config = vo_fullscreen
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = mplayer
   button = Left
   config = seek -6 0
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = More
   config = OSDStreamInfos
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Play
   config = Play
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Pause
   config = Pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = OK
   config = EventSelect
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Mute
   config = Mute
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = VolDown
   config = Volume-
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Skip
   config = EventNext
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Enter
   config = Enter
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Stop
   config = Quit
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Up
   config = EventUp
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = VolUp
   config = Volume+
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Down
   config = EventDown
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Replay
   config = EvenPrior
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Right
   config = EventRight
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Rewind
   config = SeekRelative-15
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Forward
   config = SeekRelative+15
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Home
   config = Menu
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = DVD
   config = RootMenu
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = xine
   button = Left
   config = EventLeft
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Down
   config = key-nav-down
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Play
   config = key-play
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Pause
   config = key-pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = OK
   config = key-nav-activate
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Mute
   config = key-vol-mute
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = VolDown
   config = key-vol-down
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = DVD
   config = key-disc-menu
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Stop
   config = key-quit
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Up
   config = key-nav-up
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = VolUp
   config = key-vol-up
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Replay
   config = key-prev
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = ChanDown
   config = key-prev
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Right
   config = key-nav-right
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Skip
   config = key-next
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = ChanUp
   config = key-next
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Rewind
   config = key-slower
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Forward
   config = key-faster
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = vlc
   button = Left
   config = key-nav-left
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = More
   config = show_playing
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Play
   config = play_pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Pause
   config = pause
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Power
   config = quit
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Mute
   config = mute
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = VolDown
   config = volume_down
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Up
   config = up
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = VolUp
   config = volume_up
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Down
   config = down
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Right
   config = right
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Rewind
   config = seek_backward
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Forward
   config = seek_forward
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = DVD
   config = play_dvd
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = totem
   button = Left
   config = left
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Play
   config = toggle_play_pause_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Right
   config = move_right_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = OK
   config = activate_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Power
   config = close_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Mute
   config = toggle_mute_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = VolDown
   config = decrement_volume_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Rewind
   config = seek_backward_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Stop
   config = stop_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Up
   config = move_up_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = VolUp
   config = increment_volume_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Down
   config = move_down_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Pause
   config = pause_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Enter
   config = activate_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Forward
   config = seek_forward_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Home
   config = toggle_menu_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Red
   config = toggle_fullscreen_key
   repeat = 0
   delay = 0
end

begin
   remote = mceusb
   prog = elisa
   button = Left
   config = move_left_key
   repeat = 0
   delay = 0
end

```

---

### Post by yankcrime on 2008-02-09
I am sure this is a bit late, and you've probably already fixed the problem.  If you haven't.  I suggest you check out [http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)

You need to start a daemon called "irexec" which will execute commands upon IR signals.  This is typically done upon boot in /etc/rc.local, by putting the following code at the end:
```

/usr/bin/irexec -d /home/[user]/.lircrc

```
where "[user]" is the user that is running mythtv.  That tells irexec to monitor your .lircrc file.  You have already enabled the USB0 to wakeup the machine.
The next step is edit our .lircrc file to tell it what to properly do when you hit the power button.  I use "PC" button, which maps to "power" by adding the following code in your .lircrc file:
```

begin
    button = Power
    prog = irexec
    repeat = 0
    config = [whatever command you use to suspend]
end

```
replacing " [whatever command you use to suspend]" with your particular command you use (/etc/acpi/sleep.sh sleep for example).  
You might have to remove the mapping of your power button to other applications because irexec should always be running.
Remember, if you have to use sudo, you will have to set that command such that a password is not required (see visudo for more help on this).

---

### Post by trojanfoe on 2008-05-27
That doesn't seem like the best solution as don't you want the machine to wake-up in order to record any programmes you have set in the timer?  I'm currently building a cable-tv box using VDR and that will supply the time of the next recording to its shutdown script, allowing you to set /proc/acpi/alarm correctly.  I think you want to focus on a suspend script invoked by mythtv else it will remain asleep when it should have woken up.

Cheers,
Andy

---

### Post by onesojourner on 2008-05-27
I actually don't use any of the dvr features.

---

### Post by capnjim on 2008-07-13
I've been trying to set up suspend to ram and found this page really helpful. However I still have a problem. I have set up xinitrc etc as suggested here and elsewhere, but I cannot get anything to happen unless I manually execute irexec -d as root. Pressing the power button on the remote then causes it to suspend, but after wakeup it will no longer work again; I have to once again manually execute irexec -d as root.

Anyone have any ideas?

Cheers.

---

### Post by john.ennew on 2008-08-16
Hi capnjim, Did you ever manage to solve this? I am having the same problem.  I added irexec -d command to /etc/rc.local.  All other commands I have setup in my .lircrc file to be executed by irexec work except the command to suspend the system.  It does work however if I kill the irexec process then start it again with ```
sudo irexec -d
```

The only thing I can think of is that irexec is not being started with root privledges by placing it rc.local but everything I google on the subject suggests that it should be.

I am using mythbuntu 8.04.

---


---
title: "Play/Pause issue"
date: 2008-01-20
forum: Mythbuntu
---

### Post by kreegor on 2008-01-20
Hey guys/galls.

MythTv is awesome and the MythBuntu distro is fantastic as well. My only problem is that when I use the remote to try and pause either a DVD or TV it pauses for a nanosecond and then quickly goes back to play mode. It does this without fail making it impossible for me to pause anything.

Has anyone had the same issue or know what to do to fix it?

My system specs are:
Core 2 Duo E2160
Gigabyte P31-S3G
1 Gig ddr2 667
Nvidia 8400GS
Dvico HDTV Fusion Plus DVB-T card with usb remote

Thanks in advance

---

### Post by kreegor on 2008-01-20
*bump

Anything would be great. Even if it was editing a file to put in a delay period between when tv or dvd can be paused and then played again

---

### Post by newlinux on 2008-01-20
Does this happen when you use the keyboard? If not it may be fixable with some changes to you LIRC file... Could be your remote is sending the signal twice (pausing and unpausing quickly).

---

### Post by kreegor on 2008-01-20
I don't think it does with the keyboard. However, as far as I know "P" is for Pause and "Ctrl-P" is for play. I think it is something to do with the LIRC file but I'm relatively new to linux in general so I'm not sure how to edit it.

---

### Post by newlinux on 2008-01-20
"p" is a toggle for pause and play. Press it when it is playing and it will pause, press it when it is paused and it will play. You probably need to adjust your delay and repeat values for whatever key you have mapped to "p." you can edit hte file with with the "nano" command (this is  avery simple editor):

```
nano ~/.mythtv/lircrc
```

Ctrl-o to save
Ctrl-x to exit. 

More informaiton on configuring your delay and repeat values:

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)

You want to look at the .lircrc configuration part of this page...

---

### Post by kreegor on 2008-01-20
Awesome, thank you. I will let you know how it went when I get a chance to edit it

---

### Post by kreegor on 2008-01-21
I tried editing it and that was easy enough. Now my remote control doesn't work at all. The batteries are fine (they are fairly new).

How do I get MythTv to recognise my remote again?

---

### Post by newlinux on 2008-01-21
can you post your lircrc file? You shouldn't have to do anything to make it work if there are no errors in the file...

When you run irw do you get any output when pressing buttons?

---

### Post by kreegor on 2008-01-22
EDIT: Turns out there is nothing wrong with the remote. It wouldn't register anything in irw but when I pulled out the keyboard I had attached the remote worked fine. Every key would register in irw with no problems.

Haha! I have no idea why the keyboard was stopping it but I plugged it back in and the remote still works. That's the thing about hardware. It's harder to trouble shoot.

Anyway, now its all good. Thanks heaps for your help newlinux. Very much appreciated! :)

---

### Post by kreegor on 2008-01-22
This is my lircrc file in home/mythtv/.lircrc (and also ~/.mythtv/lircrc). I still cannot pause anything as it goes straight to play again. I have tried setting the delays for all the pauseplay values but that still hasn't worked. Is there anything else I need to do? I have put in just the DVICO_MCE seeing as though that is the remote that comes up in irw.

```

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = playpause
    config = P
    repeat = 0
    delay = 1
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = ch_down
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = ch_up
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = ff
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = playpause
    config = P
    repeat = 0
    delay = 1
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = vol_down
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = vol_up
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = more
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = rec
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = start
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = DVICO_MCE
    prog = mythtv
    button = left
    config = Left
    repeat = 0
    delay = 0
end


```

Could it be because my remote is a FusionRemote?

Also one other thing. When I run irw, a line appears for every button on my remote but in MythTv only a select few are configured. I tried changing the lircrc file to add in the new key mapping but that didn't work. Can anyone help me with that?

Basically I want the DVD Menu button to bring up the DVD menu screen so I added:

```

begin
    remote = DVICO_MCE
    prog = mythtv
    button = dvd_menu
    config = M
    repeat = 0
    delay = 0
end

```

But that didn't work even after I restarted lirc.

---

### Post by kreegor on 2008-01-23
Bump

---

### Post by newlinux on 2008-01-23
Is the dvd_menu button in your lircd.conf file (/etc/lirc/lircd.conf - maybe post that too)?

What user are your running mythfrontend as? You need to modify the one for the user you run mythfrontend as (unless you have them symlinked). That could be the problem. Something else to check. I see nothing wrong with your config file on glance, and nothing wrong with the new button you added, assuming dvd_menu is what is in the lircd.conf file. Also, if I'm not mistaken, I believe the 'M' key brings up the internal player's menu, not the dvd menu, but I'm not sure on this. However, I think you can get to the dvd  menu from this menu...

Also, just to be sure - does the P button on the keyboard pause and play properly?

---

### Post by kreegor on 2008-01-24
The dvd_menu button is in my lircd.conf file (I am not at home so I can't post it at the moment) and works no problem in irw.

I will try editing the lircrc file for the user that I log in as (didn't realise there was one but looked and found that there is) and see if that makes a difference.

The P button on the keyboard does play and pause properly.

---

### Post by kreegor on 2008-01-24
Edited the lirc file in the user directory that logs in and that wr\orks great. I can edit/assign any button I want! :)

However, the play/pause issue is still there. I will play around with the delay feature and repeat feature etc to see if I can get it sorted. Play/Pause works fine when pressing P on the keyboard. I will tweak around with the file a bit more and see what I can do.

EDIT: Ohhhhh Man! I can't believe it. The problem was right in my face the whole time! The lircrc file had:

```

begin
     remote = DVICO_MCE
     prog = remote
     button = playpause
     config = P
     repeat = 0
     delay = 0
end

```

was actually in the lirc file twice so it would do the first one (pause) and then straight onto play again.

Glad to finally have that all sorted :)

EDIT: Just noticed one other issue. When playing a dvd and either rewinding or fast forwarding, when you hit play it pauses, and when you play again it doesn't play normal speed but keeps the rew or ff at whatever speed you had it in the first place. Will have to fiddle around with this one as well I think. Once again, doesn't do it on the keyboard :)

---

### Post by newlinux on 2008-01-24
I should have caught that lircrc duplication. Glad you did. I have no idea on your new issue... Are you using the internal player for dvd playbackl?

---

### Post by kreegor on 2008-01-24
Yeah I use the internal player. It works properly when pausing tv but not a dvd. It's not a huge problem though

---


---
title: "Remote barely works: Winfast PVR 2000"
date: 2011-04-27
forum: Mythbuntu
---

### Post by Gr8RedShark on 2011-04-27
I have a Leadtek WinFast PVR 2000, and it came with the remote Y0400052. I'm using Mythbuntu 10.10.

When MythTV is running, the only buttons on the remote that work are Channel Up and Channel Down(and they skip two menu items at a time), and Enter. A few other keys such as Stop, Back, and Replay also work, but they just escape back to the previous screen (same as pushing Left-arrow on the keyboard).

At first I thought it was a problem with lirc, but then I ran irw and pushed the buttons on the remote and everything looks fine: whatever button I push it's name and code appear on the console.

I'm guessing the problem is in the connection between MythTV and lirc, but I'm not sure where the problem is. I've already read about reconfiguring MythTV to use /var/run/lirc/lircd instead of /dev/lirc0 , but that doesn't seem to have changed anything.

Does anyone have any ideas what could be the problem?

---

### Post by novellahub on 2011-04-28
You need to modify your lircrc file located in the following location:

```

/home/[USERNAME]/.mythtv/lircrc

```

The lircrc file maps your keypress to a keyboard command in lirc.  
For a more detailed explanation, see here:

[http://www.commandir.com/content/view/47/64/](http://www.commandir.com/content/view/47/64/)

For a list of your remote commands, see here (Under Begin Codes):

[http://lirc.sourceforge.net/remotes/leadtek/Y0400052](http://lirc.sourceforge.net/remotes/leadtek/Y0400052)

---

### Post by Gr8RedShark on 2011-04-28
The file **~/.mythtv/lirc** already exists, and is a link to **~/.lirc/mythtv** which had a full set of mappings in it, I assume these were Mythbuntu default mappings from the remote buttons to the keys. I'm not sure what modifications should I be making, if any?

As for that list of codes in that other link: Looking at the output of irw, the codes match perfectly with the contents of **/usr/share/lirc/remotes/leadtek/lircd.conf.PVR2000**. I still tried creating a new file lircd.conf.Y0400052 and then pointed **/etc/lirc/lirc.conf** to that and then restarted lircd ... and then the remote didn't register at all, not even in irw.

---

### Post by novellahub on 2011-04-29
The lircrc file contains the keyboard event mappings.  Here is one for my old Streamzap remote as a example:

```

begin
   remote = Streamzap_PC_Remote
   prog = mythtv
   button = 0
   config = 0
   repeat = 0
   delay = 0
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 1
   config = 1
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 2
   config = 2
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 3
   config = 3
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 4
   config = 4
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 5
   config = 5
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 6
   config = 6
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 7
   config = 7
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 8
   config = 8
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = 9
   config = 9
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = POWER
   config = Esc
end

# ???
begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = MUTE
   config = F9
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = CH_UP
   repeat = 3
   config = Up
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = VOL_UP
   repeat = 3
   config = ]
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = CH_DOWN
   repeat = 3
   config = Down
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = VOL_DOWN
   repeat = 3
   config = [
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = UP
   repeat = 3
   config = Up
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = LEFT
# navigates, or skips back during playback or live tv.
   config = Left
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = OK
   config = Return
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = RIGHT
# navigates, or skips forwards during playback or live tv.
   config = Right
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = DOWN
   repeat = 3
   config = Down
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = MENU
   config = m
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = EXIT
   config = Esc
end

begin
   
   prog = mythtv
   button = PLAY
   config = p
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = PAUSE
   config = p
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = STOP
   config = Esc
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   # skip backward
   button = |<<
   config = PgUp
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   # skip forward
   button = >>|
   config = PgDown
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = RECORD
   config = r
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   # rewind
   button = <<
   config = <
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   # fast forward
   button = >>
   config = >
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = RED
   # aka LIVE
   # Delete
   config = d
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = GREEN
   # aka PLAY
   # Info
   config = i
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = YELLOW
   # aka PRGM
   # change aspect ratio
   config = w
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = BLUE
   # aka SET
   config = End
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = DISP
   config = e
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = PTZ
   config = z
end

begin
   remote = Streamzap_PC_Remote
   repeat = 0
   delay = 0
   prog = mythtv
   button = HELP
   config = Space
end 

```


Below is a link to the Streamzap button mappings on the physical remote.  I used that as a baseline to understand the button names.

[http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap](http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap)

I changed the mapping of the blue button on the remote (lircrc file) to be my commercial skipping key (Maps to the End key).  The example above is for a different remote but the same rules apply.  I have also done similar changes to my ATI remote I have.

---

### Post by Gr8RedShark on 2011-05-01
Hey, you know what worked? 

I went to the Mythbuntu Control Centre and clicked the checkbox "Generate Dynamic button mapping", then clicked apply. The button checkbox un-checked itself, but now the MythTV works fine with the remote. I'm not sure *why* it worked, but I'm glad it did.

---

### Post by declanmullen on 2011-05-04
> **Gr8RedShark said:**
> Hey, you know what worked? 

I went to the Mythbuntu Control Centre and clicked the checkbox "Generate Dynamic button mapping", then clicked apply. The button checkbox un-checked itself, but now the MythTV works fine with the remote. I'm not sure *why* it worked, but I'm glad it did.

That checkbox option results in a new lircrc file being created. Presumably the pre-existing one wasn't correct.

---


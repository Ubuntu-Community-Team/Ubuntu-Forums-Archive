---
title: "frontend freeze after no use of 24 hours"
date: 2010-02-08
forum: Mythbuntu
---

### Post by davidstoll on 2010-02-08
Mythfrontend (pure front end machine) freezes after not being used for 24 hours.  This time is probably something less, but every night before I go to bed, I like to watch some tv...and every night I have to kill the frontend process and re-start it.  The OS is fine.

Other people have mentioned frontend freezes recently, but it is in regards to a situation where they are playing a recorded show and/or skipping commercials in a recorded show.

Any suggestions?

---

### Post by nickrout on 2010-02-08
suggestions? Yes, read the logs.

Are you sure its frozen though? Press the remote buttons a few times. It may be resting as opposed to dead. (With apologies to the parrot)

---

### Post by grenloch101056 on 2010-02-09
> **davidstoll said:**
> Mythfrontend (pure front end machine) freezes after not being used for 24 hours.  This time is probably something less, but every night before I go to bed, I like to watch some tv...and every night I have to kill the frontend process and re-start it.  The OS is fine.

Other people have mentioned frontend freezes recently, but it is in regards to a situation where they are playing a recorded show and/or skipping commercials in a recorded show.

Any suggestions?

I have something pretty similar, whenever my combined BE/FE sits for over 16ish hours it dumps out of the front end and leaves me at the desktop whenever I try to play a recording or watch live tv.  I've looked at the logs but nothing sticks out to me.  I can post them up, maybe they'll sing to someone else.

---

### Post by davidstoll on 2010-02-09
> **nickrout said:**
> suggestions? Yes, read the logs.

Are you sure its frozen though? Press the remote buttons a few times. It may be resting as opposed to dead. (With apologies to the parrot)

Basically, after many hours, the frontend does not respond to the remote and keyboard...unless you wait about 2-3 minutes.  So, if you hit the up arrow, the frontend will respond...eventually.  But then it is in this semi frozen state again.....hit a button, wait another couple of minutes...etc.  If I wait about 15-20 minutes, it snaps out of it's drunken stooper

If I don't want to wait, I can alt-tab to a command line or thunar and everything responds just fine.  I can kill the frontend and restart it and it is as snappy as could be.

Keep in mind that the backend machine is still humming along without any problems.

Here is the log...

2010-02-09 21:59:44.799 MythSocket(ffffffffaffb4708:25): readStringList: Error, timed out after 30000 ms.
2010-02-09 21:59:44.799 Connection to backend server lost
2010-02-09 21:59:44.824 MythContext: Connecting to backend server: 192.168.0.11:6543 (try 1 of 1)
2010-02-09 21:59:44.831 Using protocol version 50
2010-02-09 21:59:44.834 MythSocket(ffffffffae5e9498:25): writeStringList: Error, invalid string list.
2010-02-09 22:00:14.834 MythSocket(ffffffffae5e9498:25): readStringList: Error, timed out after 30000 ms.
2010-02-09 22:00:14.835 Reconnection to backend server failed
2010-02-09 22:00:14.843 SortedList is Empty
2010-02-09 22:00:15.864 MythContext: Connecting to backend server: 192.168.0.11:6543 (try 1 of 1)
2010-02-09 22:00:15.871 Using protocol version 50
2010-02-09 22:00:16.161 MythContext: Connecting to backend server: 192.168.0.11:6543 (try 1 of 1)
2010-02-09 22:00:16.174 Using protocol version 50

---

### Post by nickrout on 2010-02-09
if you have a keyboard attached I find ctrl-alt-backspace to be quicker, especially if I shorten the default login timeout. X and then mythfrontend just restarts.

Or you could map a remote key to run a script that does ```
sudo service gdm restart
```

---

### Post by davidstoll on 2010-02-10
> **nickrout said:**
> if you have a keyboard attached I find ctrl-alt-backspace to be quicker, especially if I shorten the default login timeout. X and then mythfrontend just restarts.

Or you could map a remote key to run a script that does ```
sudo service gdm restart
```

That crtl-alt-backspace seems to do the trick.  So that restarts whatever has focus?  I guess I'm not clear on exactly what it does.  Or is that just the keycombo for killing/restarting mythtv?  Very cool though.  I never new about that.

This unit is for someone that needs something simple and the keyboard thing just doesn't do it.  They are one of those people who can't deal with more than one remote.  However, I can program the unused "power" button to wake it up (there are also unused red, blue, green and yellow buttons too).

I'm not sure if the abbreviation for the control, alternate or backspace buttons is correct...but I'm thinking this..

gedit /home/user/.lirc/mythtv

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = POWER   # I'll have to confirm if this is correct
    config = Ctrl+Alt+Backspace
    repeat = 0
    delay = 0
end

Or possibly change the config line to be a bash script.  But I like the thought of the simple key combo.  However, a script could also restart if it crashes.

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = POWER
    config = /whatever/script.sh # which could run what you suggest
    repeat = 0
    delay = 0
end

I need to run IRW and press the power button to see what it is actually called.  Then I need to confirm what the abbreviations are for crtl, alt, backspace.

But I think I'm on the right track.  I'll test tonight and report back.

Thank you!

---

### Post by nickrout on 2010-02-10
ctrl-alt-backspace kills the X server, which then automatically restarts.

---

### Post by davidstoll on 2010-02-10
> **davidstoll said:**
> 
begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = POWER   # I'll have to confirm if this is correct
    config = Ctrl+Alt+Backspace
    repeat = 0
    delay = 0
end

Or possibly change the config line to be a bash script.  But I like the thought of the simple key combo.  However, a script could also restart if it crashes.

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = POWER
    config = /whatever/script.sh # which could run what you suggest
    repeat = 0
    delay = 0
end



Well, this doesn't work because the "prog" equals mythtv....but it isn't mythtv that I want to execute the command.  So, I'm not sure it can be done this way unless someone knows what the prog should be.  I'll have to create a new separate config file mapping...which I can do, but only if someone knows what to put for prog.  xserver?  something like that?

Also, the script won't work because it has sudo in it.  It needs the password...which just doesn't work.  I'm not sure if this is the best option for me anyway...it just annihilates everything and puts me back at the beginning.  The ctrl+alt+backspace just seems to wake it up...and I stay at the same menu location...and it is faster.  I'll take the script method if there is no other way, but I have to have help getting around the sudo problem.

---

### Post by azmyth on 2010-02-11
prog needs to equal irexec and you need to set irxec to start on boot. Irexec will all you to map a key to script you can execute.

---

### Post by davidstoll on 2010-02-13
> **azmyth said:**
> prog needs to equal irexec and you need to set irxec to start on boot. Irexec will all you to map a key to script you can execute.

How do you set it to load on boot?

It may be a simple question, but I've tried to make things load on boot before, but I just don't know how to do it (easily).

---

### Post by Neon Dusk on 2010-02-13
If you're using mythbuntu irexec will autostart from '/usr/share/mythbuntu/session.sh' if you have any prog = irexec commands in ~/.lirc

---

### Post by nickrout on 2010-02-13
[http://ubuntuforums.org/showthread.php?t=1276520](http://ubuntuforums.org/showthread.php?t=1276520)

---

### Post by davidstoll on 2010-02-15
> **Neon Dusk said:**
> If you're using mythbuntu irexec will autostart from '/usr/share/mythbuntu/session.sh' if you have any prog = irexec commands in ~/.lirc

Ok, so it's already installed (part of lirc?) and looks like its running on startup (session.sh script).

However, the buttons I assigned are not responding.  I have (and can) changed the mappings of buttons using prog=mythtv (or vlc, mplayer, etc) and changed to a normal keyboard press.  So, I'm comfortable doing that.  However, using a different prog=irexec and requiring sudo to execute the script is a bit confusing to me.

Like for instance, if I have two config files (one for mythtv and one for vlc) and both reference a certain button press, which one gets executed?  I believe it is which ever one has focus.  However, irexec doesn't really have focus, so I don't know how it gets the command.  In any case, here is my setup.

These are in the mythtv config file in ~/.lirc/mythtv

begin
    remote = Streamzap_PC_Remote
    prog = irexec
    button = POWER
    config = /home/user/restart-frontend.sh
    repeat = 0
    delay = 0
end

begin
    remote = Streamzap_PC_Remote
    prog = irexec
    button = Red
    config = Ctrl+Alt+Backspace
    repeat = 0
    delay = 0
end


Where restart-frontend.sh is...
#!/bin/sh
sudo service gdm restart


i.e.  and this is from my other machine (in their own separate config file in ~/.lirc/custom)

begin
    remote = mceusb_hauppauge
    prog = irexec
    button = Power
    config = /usr/bin/mythfrontend
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = irexec
    button = Home
    config = /usr/bin/mythfrontend
    repeat = 0
    delay = 0
end


I thought the irexec commands needed to be in a separate file (which is why I tried it both ways).  Both machines were rebooted so as to initialize the startup script.

No luck yet.

---

### Post by davidstoll on 2010-02-16
The part of my session.sh with irexec looks like this.


    if [ -x /usr/bin/irexec ] && [ ! -f ~/.noirexec ] && [ -f ~/.lircrc ]; then
        if [ -n "$(cat ~/.lirc/* | grep --invert-match "#" | grep irexec | grep prog)" ]
        then
            killall irexec
            irexec -d


It seems like it is looking for any line entry of prog = irexec  and there definitely is (as you can see from above).

Why would my button presses not work?

The only thing I can think of is that my button scripts are in ~/.lirc  not  ~/.lircrc
Do I need to add 
&& [ -f ~/.lirc ]

?

---

### Post by Neon Dusk on 2010-02-17
The session.sh script is checking that the file ~/.lircrc exists
if [ -x /usr/bin/irexec ] && [ ! -f ~/.noirexec ] && [ -f **~/.lircrc** ];

and then looks within the ~./lirc/ folder

if [ -n "$(cat **~/.lirc/*** | grep --invert-match "#" | grep irexec | grep prog)" ]

Your ~/.lircrc file should include a list of include statements pointing to the individual files within ~/.lirc/. If you add a new file in ~/.lirc/ you'll need to add a include statement in ~/.lircrc - however I usually just add the irexec commands to ~/.lirc/mythtv.

e.g. for my mce remote I have the following in ~/.lirc/mythtv
```

begin
    remote = mceusb    
    prog = irexec
    button = Radio
    config = sudo frontendrestart.sh
end

```

Added to sudo visudo
```

# Allow gdm to be restarted using remote
%mythtv ALL = NOPASSWD: /usr/local/bin/frontendrestart.sh

```


/usr/local/bin/frontendrestart.sh has execute permission 
```

sudo chmod a+x /usr/local/bin/frontendrestart.sh

```

/usr/local/bin/frontendrestart.sh
```

#!/bin/sh

restart gdm

exit

```

You can confirm that irexec is running by doing a 'ps aux | grep irexec | grep -v grep'

---

### Post by davidstoll on 2010-02-18
This is good info.  I appreciate it.  The .lirc file does have my custom script included in it...by the way.

I might be one step behind this though.

irexec does not seem to be starting at boot time.  I have to run it manually with "irexec -d".

However, after a few hours (?) the remote stops working (not completely, but only buttons running the special scripts like you show, but not necessarily ones needing sudo) until I kill irexec and re-run it.

This is happening on two separate machines, with two different remotes.

By the way, does adding the information about allowing mythtv user to run apps without a password have a security downside?



> **Neon Dusk said:**
> The session.sh script is checking that the file ~/.lircrc exists
if [ -x /usr/bin/irexec ] && [ ! -f ~/.noirexec ] && [ -f **~/.lircrc** ];

and then looks within the ~./lirc/ folder

if [ -n "$(cat **~/.lirc/*** | grep --invert-match "#" | grep irexec | grep prog)" ]

Your ~/.lircrc file should include a list of include statements pointing to the individual files within ~/.lirc/. If you add a new file in ~/.lirc/ you'll need to add a include statement in ~/.lircrc - however I usually just add the irexec commands to ~/.lirc/mythtv.

e.g. for my mce remote I have the following in ~/.lirc/mythtv
```

begin
    remote = mceusb    
    prog = irexec
    button = Radio
    config = sudo frontendrestart.sh
end

```

Added to sudo visudo
```

# Allow gdm to be restarted using remote
%mythtv ALL = NOPASSWD: /usr/local/bin/frontendrestart.sh

```


/usr/local/bin/frontendrestart.sh has execute permission 
```

sudo chmod a+x /usr/local/bin/frontendrestart.sh

```

/usr/local/bin/frontendrestart.sh
```

#!/bin/sh

restart gdm

exit

```

You can confirm that irexec is running by doing a 'ps aux | grep irexec | grep -v grep'

---

### Post by Neon Dusk on 2010-02-18
Strange how irexec is not starting automatically for you. (It works fine on the two frontends I've got and I tested it on a clean virtual box install of mythbuntu 9.10) If you've added the ubuntu desktop role so that it's using gnome instead of the mythbuntu default (xfce) it may have of broken it.

> By the way, does adding the information about allowing mythtv user to run apps without a password have a security downside?

The addition to the sudoers file only grants users in the mythtv group to run the '/usr/local/bin/frontendrestart.sh' script. I don't think there's any alternative if you want to be able to restart the x server from the remote control.

---

### Post by davidstoll on 2010-02-19
I'm just using the default lightweight xfe.

> **Neon Dusk said:**
> Strange how irexec is not starting automatically for you. (It works fine on the two frontends I've got and I tested it on a clean virtual box install of mythbuntu 9.10) If you've added the ubuntu desktop role so that it's using gnome instead of the mythbuntu default (xfce) it may have of broken it.



The addition to the sudoers file only grants users in the mythtv group to run the '/usr/local/bin/frontendrestart.sh' script. I don't think there's any alternative if you want to be able to restart the x server from the remote control.

---

### Post by davidstoll on 2010-02-19
hmm, the sudo visudo command works on my backend, but not my frontend.

This is the error...

visudo: no editor found (editor path = /usr/bin/vim)



> **Neon Dusk said:**
> 

[/code]

Added to sudo visudo
```

# Allow gdm to be restarted using remote
%mythtv ALL = NOPASSWD: /usr/local/bin/frontendrestart.sh

```



---

### Post by davidstoll on 2010-02-19
nevermind, I just made a symbolic link from vim to vi


> **davidstoll said:**
> hmm, the sudo visudo command works on my backend, but not my frontend.

This is the error...

visudo: no editor found (editor path = /usr/bin/vim)

---

### Post by davidstoll on 2010-02-21
Ok, so this all basically works, but the problem is that after about an hour or so, the remote stops responding to the irexec commands, so I have to kill irexec and restart it using irexec -d.

Then I can run remote commands using irexec in my config files.

How can I make it so I don't have to restart the irexec demon every hour or so?

Thanks

---


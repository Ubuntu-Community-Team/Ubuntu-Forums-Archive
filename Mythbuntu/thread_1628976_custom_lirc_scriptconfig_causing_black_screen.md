---
title: "custom lirc script\config causing black screen"
date: 2010-11-23
forum: Mythbuntu
---

### Post by davidstoll on 2010-11-23
I had to completely reinstall the OS, but made backup copies of all my files, scripts, etc.

One of the files was a custom script\config for my Streamzap remote.  The name of the custom script is called "custom" and is in ~/.lirc

Also, I added the "include ~/.lirc/custom" in the ~.lircrc file.

I also made sure the perms were exactly the same as what they were before and double checked that they match what the other lirc files in the folder.

Essentially, I want to assign the extra colored buttons at the bottom of my remote to shell scripts.  The shell scripts are 777, but don't need to be.  I did that to make sure there wasn't some kind of perm issue with the actual scripts being referenced.  Again, this was totally working before...it's the exact same file that I backed up and restored.

If I comment out every single line (of the file below), but leave the file there, I don't get the black screen on bootup.  So is it something new with 10.10 and 10.04 (I tried both versions and also 32 and 64 bit for each)?  Originally, I installed 9.04 and have been upgrading from there all the way to 10.10.  I wasn't until a complete reinstall of the OS that I had the problem.

~/.lirc/custom
```
# custom buttons addd by David
# sudo /etc/init.d/lirc restart

begin
    remote = mceusb
    prog = irexec
    button = Power
    #config = /home/david/powermythfrontend.sh &
    config = /usr/bin/mythfrontend
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Home
    config = /home/david/runmythfrontend.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Red
    config = /home/david/killmythfrontend.sh &
#    config = /home/david/killmythfrontend.sh & /home/david/killxbmc.sh & /home/david/killboxee.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /home/david/runmythfrontend.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Yellow
    config = /home/david/killboxee.sh &
    repeat = 0
    delay = 0
end


begin
    remote = mceusb
    prog = irexec
    button = Blue
    config = /home/david/restartgdm.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
#    prog = irexec
    prog = irxevent
    button = OK
    config = Key Enter CurrentWindow
#    config = /home/david/restartgdm.sh &
    repeat = 0
    delay = 0
end
```

---

### Post by superm1 on 2010-11-23
> **davidstoll said:**
> I had to completely reinstall the OS, but made backup copies of all my files, scripts, etc.

One of the files was a custom script\config for my Streamzap remote.  The name of the custom script is called "custom" and is in ~/.lirc

Also, I added the "include ~/.lirc/custom" in the ~.lircrc file.

I also made sure the perms were exactly the same as what they were before and double checked that they match what the other lirc files in the folder.

Essentially, I want to assign the extra colored buttons at the bottom of my remote to shell scripts.  The shell scripts are 777, but don't need to be.  I did that to make sure there wasn't some kind of perm issue with the actual scripts being referenced.  Again, this was totally working before...it's the exact same file that I backed up and restored.

If I comment out every single line (of the file below), but leave the file there, I don't get the black screen on bootup.  So is it something new with 10.10 and 10.04 (I tried both versions and also 32 and 64 bit for each)?  Originally, I installed 9.04 and have been upgrading from there all the way to 10.10.  I wasn't until a complete reinstall of the OS that I had the problem.

~/.lirc/custom
```
# custom buttons addd by David
# sudo /etc/init.d/lirc restart

begin
    remote = mceusb
    prog = irexec
    button = Power
    #config = /home/david/powermythfrontend.sh &
    config = /usr/bin/mythfrontend
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Home
    config = /home/david/runmythfrontend.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Red
    config = /home/david/killmythfrontend.sh &
#    config = /home/david/killmythfrontend.sh & /home/david/killxbmc.sh & /home/david/killboxee.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /home/david/runmythfrontend.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Yellow
    config = /home/david/killboxee.sh &
    repeat = 0
    delay = 0
end


begin
    remote = mceusb
    prog = irexec
    button = Blue
    config = /home/david/restartgdm.sh &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
#    prog = irexec
    prog = irxevent
    button = OK
    config = Key Enter CurrentWindow
#    config = /home/david/restartgdm.sh &
    repeat = 0
    delay = 0
end
```

So by this script being there I think it is causing irexec -d to be spawned.  See /usr/share/mythbuntu/session.sh for details.  See if running that manually also caused problems.

---

### Post by davidstoll on 2010-11-23
> **superm1 said:**
> So by this script being there I think it is causing irexec -d to be spawned.  See /usr/share/mythbuntu/session.sh for details.  See if running that manually also caused problems.

Well, actually, from 10.04 to 10.10 the whole streamzap system is totally screwed up.  Many people are having serious issues related to the streamzap remote being picked up as an IR device as well as a HID (keyboard).  So, you get double presses, for instance which required commenting out certain keystrokes to remove the double presses (there were other more complicated solutions).

Anyway, calling an .sh file from a custom file (from my own findings) required irexec not to be run as a daemon (-d).  However, if you killed it and manually ran irexec and then used the remote, it worked.  So, the fix was to remove the -d from the session.sh file mentioned above.

This was working fine even in 10.10 before I had to do a complete reformat and reinstall.  The only difference is I upgraded from 9.04 all the way to 10.10 rather than a fresh install of 10.10 as I have now (by the way I have tried both 32 and 64 bit, no difference with regards to this problem).

So, I have removed the -d from the session script...and that was exactly what was required before to get the key presses to call a script from the custom lirc file.

Now I get a black screen on boot up.  I can drop to a shell Ctrl+Alt+F1, delete the custom file, reboot and everything is fine.

I also found out that it's not really about the file itself, because I can add that same code into an existing lirc script (i.e. mythtv) and I have the same issue.  I can comment out or delete the lines and the system properly boots.

---

### Post by davidstoll on 2010-11-28
Why would the custom lines or custom file cause my frontend machine not to boot (black screen)?  The same custom file works on another machine (backend/frontend).

---

### Post by davidstoll on 2010-12-01
I removed the "-d" from the "irexec -d" in the session.sh file.  But still get a black screen on boot when the custom script is in place...but another machine has the same script in the same place running the same version of mythbuntu 10.10.

---


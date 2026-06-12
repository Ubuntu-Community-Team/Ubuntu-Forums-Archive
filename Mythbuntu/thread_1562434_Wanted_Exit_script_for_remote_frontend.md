---
title: "Wanted: Exit script for remote frontend"
date: 2010-08-27
forum: Mythbuntu
---

### Post by rsay on 2010-08-27
I have setup my MCE remote control to suspend and resume my Revo when pushing the power button. Right now I just kill the frontend on suspend and restart it on resume. I worry that if somebody pushes the button at the wrong time, it could cause database corruption on the backend. Can anybody share a script to gracefully exit the frontend?

---

### Post by LowSky on 2010-08-27
I would only worry if you were killing the backend in the middle of a process  You should be more than fine. The frontend doens't do anything that can cause database corruption.

---

### Post by azmyth on 2010-08-27
My power button just kills the frontend or starts it and I've been doing it for a long time without issue.

---

### Post by rsay on 2010-08-29
Have you guys ever killed the frontend while you were watching a show? It is a subtle error, but when you resume, it will start at the beginning instead of at the saved position. Most of us would never push the power button in the middle of a show, but a child or spouse might. If they do, the system should be able to handle it, without losing your position.

I have been trying to use the telnet controls, but there is some problem that I don't understand.

```
echo -e "jump mainmenu" | telnet localhost 6546
echo -e "key escape" | telnet localhost 6546
echo -e "key down" | telnet localhost 6546
echo -e "key escape" | telnet localhost 6546
echo -e "key enter" | telnet localhost 6546

```
This seems like it should work. The first command goes without a problem, but the frontend segfaults on the second command, so something isn't right. Any suggestions are appreciated.

---

### Post by azmyth on 2010-08-29
I turned save location on exit and then killed the frontend and it didn't save the location like you saw as well. I see what you're getting at as you could send an escape command before killing the FE thus saving the position. I don't think the command you have will work. You'd probably needed something like telnet localhost 6546; send "jump mainmenu\n"; but I haven't tried this. If that doesn't work I'd use irwatch.pl to send the escape command when the power button is hit.

---

### Post by rsay on 2010-08-29
Thanks azmyth, you gave me an idea that seems to be working.

The command that you gave, 
```
telnet localhost 6546; send "jump mainmenu\n";
``` opened the Myth network control, but didn't actually send the jump command. I could manually enter all the commands and they worked great, but I still don't know how to do it from a script. 

What I have done is add a section to the mythtv lircrc:
```
begin
    remote = mceusb
    prog = mythtv
    button = Power 
    config = Escape
    repeat = 0
    delay = 0
end
```

This is in addition to the irexec portion of the lircrc:
```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = sudo pm-suspend
    delay = 0
    repeat = 0
end

```

---

### Post by azmyth on 2010-08-30
Yeah, I'm not sure how to pass a command via telnet. Anyhow, I liked the idea of saving the place on power off so I implemented this by using irwatch.pl.

[http://www.ronfrazier.net/mythtv/0.22/index.html](http://www.ronfrazier.net/mythtv/0.22/index.html)

Irwatch looks for the power button pressed _only_ in playback mode and if catches the power button it issues a clearosd command and escape. You need the clearosd in the event someone pushed the power button with the osd up thus an escape would just clear the osd and not save the position. After this is done, the script I have set with irexec is executed and the fe is killed and the tv is turned off.

---

### Post by rsay on 2010-09-01
I am trying to get it working without installing anything extra.

So, I edited the keys in the frontend (Utilities/Setup>Edit Keys>JumpPoints>Main Menu) and defined Ctrl+Alt+M as the jump point key combo for the main menu.

Then I changed mythtv lircrc again. I got rid of ESC and added the new keys:
```
begin
    remote = mceusb
    prog = mythtv
    button = Power 
    config = Ctrl+Alt+M
end
```

This is in addition to the irexec portion of the lircrc:
```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = sudo pm-suspend
end

```

And now I seem to be getting the behavior I want. I'll report back if I have any unforseen problems. Thanks everybody.

---


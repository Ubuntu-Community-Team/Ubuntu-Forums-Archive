---
title: "MCE remote...kinda"
date: 2009-02-06
forum: Mythbuntu
---

### Post by cartisdm on 2009-02-06
I have a fresh install of Mythbuntu 8.10.  I have the MCE USB receiver which mythbuntu and mythtv picks up just fine.  I'm not using the "exact" MCE remote but I'm using a Kameleon radio-shack 6-in-1 remote.  It's configured to basically be the MCE remote so that shouldn't be a problem.

It works just fine but how do I control the layout of what buttons do what?  If there is a GUI place in the settings I'd prefer that, but I can do a config text file too.

Example:

- "Exit button doesn't do anything
- "Stop" button performs like the "escape" key on the keyboard (I'd like to move this to the "Exit" button

---

### Post by uMuppet on 2009-02-06
Take a look in $HOME/.mythtv/lirc  or $HOME/.lirc
That file holds all the key bindings.

This is the exit button 

begin
    remote = NOVA-T500
    prog = mythtv
    button = BackExit
    config = Escape
    repeat = 0
    delay = 0
 end

---


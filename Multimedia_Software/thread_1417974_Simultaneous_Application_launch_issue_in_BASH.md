---
title: "Simultaneous Application launch issue in BASH"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Theist17 on 2010-02-28
Hey all!

I'm trying to launch CoverGloobus (a fantastic little album art and current song display) and Rhythmbox simultaneously through a BASH script. Problem is that when I attempt to run the script the first time, CoverGloobus doesn't launch, but Rhythmbox does. Here's my script as it is right now:

```

#! /bin/bash

#Opens Rhythmbox and CoverGloobus
rhythmbox && covergloobus 

done


```

I've double-checked the commands in gnome-terminal, and they're the right ones for launching the applications.

Here's where it gets odd, though. The second time I run the script, CoverGloobus and Rhythmbox launch simultaneously. I've reproduced this scenario multiple times. 

Is there anything wrong with my script?

---

### Post by efflandt on 2010-02-28
I think && only does the second thing when the first thing is complete.  So I suspect that it starts rhythmbox, but that is still running and does not exit, so it fails to run covergloobus.

Then when you run it again, rhythmbox is already running, so its launch application exits and clovergloobus runs.  From **man bash**:

command1 && command2

command2  is  executed if, and only if, command1 returns an exit status of zero.

I don't know what clovergloobus is or if it needs to run in a terminal, but if it is an X program, launch each to run on their own in the background:

rhythmbox &
clovergloobus &

---

### Post by Theist17 on 2010-02-28
Thanks! That did the trick. 

```

#! /bin/bash

rhythmbox &
covergloobus &

done

```

That's the script I'm using right now, and it's working flawlessly. Thanks a ton.

---


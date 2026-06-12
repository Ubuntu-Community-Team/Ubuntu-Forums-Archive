---
title: "How to get irexec to run at startup"
date: 2009-09-27
forum: Mythbuntu
---

### Post by gwagchunks on 2009-09-27
hi everyone,

Should be an easy one but I'm being really thick today! I'm trying to get irexec to run at startup, but cannot get my head around it. I have created a little script call startirexec.sh:

#!bin/bash
irexec

made it executable by: chmod u+x startirexec.sh

but typing it in just gives me: bash: startirexec.sh: command not found

Help, what am I doing wrong?  :(

Thanks

---

### Post by fataki on 2009-09-27
You're missing a slash.
Also might be good to run as a daemon.

#!**/**bin/bash
irexec -d

---

### Post by gwagchunks on 2009-09-27
> **fataki said:**
> You're missing a slash.
Also might be good to run as a daemon.

#!**/**bin/bash
irexec -d

Thanks forthe repy

I typed it in the post incorrectly, but it does have the / in the script. I have tried copying and pasting fro your post with the -d as well, but still get: bash: startirexec.sh: command not found

---

### Post by klc5555 on 2009-09-27
> **gwagchunks said:**
> Thanks forthe repy

I typed it in the post incorrectly, but it does have the / in the script. I have tried copying and pasting fro your post with the -d as well, but still get: bash: startirexec.sh: command not found

Scripts have to be started either by typing in the full path, e.g. /home/gwagchunks/startirexec.sh

or, if your script is in the terminal's current directory, by using "./" That is:

./startirexec.sh

This prevents you from (inadvertantly) naming a script with the same as a command somwhere in the path, and then by simply typing the name at the prompt wrongly invoking the script rather than the command.

---

### Post by SiHa on 2009-09-27
Also: 
>  (From irexec manpages)
If you add the --daemon (-d) option irexec will fork to background. That way you can easily start irexec from  an init  script.  In  this case you should specify a config file on the command line as irexec won’t be able to find your home directory.

The config file is the lircrc for irexec.

So you need something like **irexec /home/mythuser/.lirc/irexec**

---

### Post by gwagchunks on 2009-09-27
:)> **klc5555 said:**
> Scripts have to be started either by typing in the full path, e.g. /home/gwagchunks/startirexec.sh

or, if your script is in the terminal's current directory, by using "./" That is:

./startirexec.sh

This prevents you from (inadvertantly) naming a script with the same as a command somwhere in the path, and then by simply typing the name at the prompt wrongly invoking the script rather than the command.
Thanks for the info! I've got 2 books on Linux and not one shows . to run a script! Right I have got it working now, I have a script called startupirexec.sh which simply starts irexec and have added the line: . /home/gwagchunks/startupirexec.sh to the mythfrontend startup script (/usr/bin/mythfrontend). Hey presto it works! Thanks again for the pointers /advise! :)

---

### Post by indulis on 2010-02-05
The reason you have to use "./myscript" is because by default the shell which executes the commands you type has a search path where it looks for commands which does **not** include your current directory also known as "."

To see the places it looks for commands/scripts try *echo $PATH*

This is to stop people putting command names similar to a system one (e.g. ps) in your directory and you then executing it accidentally.  So all "./" says is "look in my current directory ."

You could also have written ~/myscript which looks in your home directory ~

. is shorthand for "current directory", ~ is shorthand for "my home directory"

---

### Post by Neon Dusk on 2010-02-06
If you're using mythbuntu then irexec gets automatically started if you have any irexec commands in ~/.lirc/

This is done from /usr/share/mythbuntu/session.sh

---

### Post by TheMiz on 2010-02-06
I got irexec to run everytime from the GUI by doing this:
Go to Applications.
Go to Settings.
Click on Sessions and Startup.
Click on Application Autostart.
Click on Add.
At the Name: prompt, type in the name of the program (irexec).
At the Description: prompt, type a description (optional).
At the Command: prompt, type in ```
/usr/bin/irexec
```

---


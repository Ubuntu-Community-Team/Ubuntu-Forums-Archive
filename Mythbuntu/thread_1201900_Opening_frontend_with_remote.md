---
title: "Opening frontend with remote"
date: 2009-07-01
forum: Mythbuntu
---

### Post by Jayy on 2009-07-01
Is there anyway I can open the MythTV Frontend with my remote?

---

### Post by tgm4883 on 2009-07-01
> **Jayy said:**
> Is there anyway I can open the MythTV Frontend with my remote?

Yep, dig through this thread for info 
[http://ubuntuforums.org/showthread.php?t=973705&highlight=mythfrontend+start+script](http://ubuntuforums.org/showthread.php?t=973705&highlight=mythfrontend+start+script)

---

### Post by Jayy on 2009-07-01
Thanks. What .lircrc file should I put the following code in?
```


begin
    remote = mceusb
    prog = irexec
    button = Home
    config = mythfrontend
    repeat = 0
    delay = 0
end

```

---

### Post by laffinet on 2009-07-01
> **Jayy said:**
> Thanks. What .lircrc file should I put the following code in?
```


begin
    remote = mceusb
    prog = irexec
    button = Home
    config = mythfrontend
    repeat = 0
    delay = 0
end

```

The code needs to go into /home/username/.lirc/mythtv

Not sure if the code you've got there will work, though. 

You might want to have a look at the mentioned thread and see what's used there (will prevent you running 2 instances of mythfrontend).

---


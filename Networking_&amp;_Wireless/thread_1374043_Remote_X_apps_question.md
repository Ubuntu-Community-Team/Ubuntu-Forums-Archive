---
title: "Remote X apps question"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by MiRee446 on 2010-01-06
Is it possible for two computers to access the same program from 1 system at the same time using remote x apps?  In other words can a system have two instances of a program running and being utilized by two different computers remotely?

For example lets say I install Program X on Computer 1.  I ssh into Computer 1 from Computer 2 and use remote x apps to use Program X.  Is it possible for Computer 3 to ssh into Computer 1 and use Program X at the same time using it for a completely different task?

---

### Post by gombadi on 2010-01-06
> 
Is it possible for two computers to access the same program from 1 system at the same time using remote x apps? In other words can a system have two instances of a program running and being utilized by two different computers remotely?



It depends on the program.

You can log in from different remote machines and run as many instances of xclock or xeyes as you want.

If the program you are running needs some sort of exclusive access to a file and locks it then the second time you try and start the program, even on a remote machine, it will fail because the program will not be able to lock the file it needs. Remote X applications are all run on the same machine but display the output on different machines.

---

### Post by captain_171 on 2010-01-06
Will there be more then one user accessing that remote PC if so yes you can such as:

Remote computer = server
Computer 1 = work1
Computer 2 = work2

This will work:
work 1 logs into server with user frank and runs firefox
work 2 logs into server with user ann and runs firefox

This will not work:
work 1 logs into server with user ann and runs firefox
work 2 logs into server with user ann and runs firefox

Does that help?

---

### Post by LinuxRules1 on 2010-01-06
in order to tunnel X through ssh you type in this command.

```
ssh -C -X user@serverip
```

then you can run gnome-terminal and be using the terminal on the remote system.

---


---
title: "Using SSH to start program"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by joeborder on 2011-02-23
Hi everybody, 
First of all if I am posting in the wrong section I am sorry, I was confused under which category this falls under.

I have just started to use SSH with both my laptop and my PC, my laptop is running Ubuntu 10.10 and my PC is running windows 7. I have managed to install a working SSH server on both machines and I can authenticate fine with both. For the windows machine I am using cygwin with OpenSSH.

However when logged into my windows machine I can't seem to start any programs, specifically I am trying to start the program "dropbox" (this is so if I leave any files at home I can simply copy them in and retrieve them from the internet) I can navigate to the directory without trouble but when I try to start the application 
```
cd C:/users/myuser/appdata/roaming/dropbox/bin
./Dropbox.exe
```
This would try to start the application but would hang until I manually terminate the command with ctrl-C which terminated the program. I then found that by adding an ampersand it ran the command then detached instead of waiting. Which worked.
```
 ./Dropbox.exe&
```
However, although Dropbox.exe appears in the task manager list of processes, the program does not actually start or run.
Can anybody help me with this or explain what the issue? 

Thank you

---

### Post by thesavager on 2011-02-23
If i understand correctly ...you try to run a windows programm .... on your laptop running Ubuntu 10.10 ... while you are logged in the windows-machine with SSH ?

---

### Post by joeborder on 2011-02-23
No sorry. I am using the laptop (or any other SSH client) to connect to my windows pc and begin running a program on that remote pc

---

### Post by thesavager on 2011-02-23
> **joeborder said:**
> No sorry. I am using the laptop (or any other SSH client) to connect to my windows pc and begin running a program on that remote pc

Yes ... that's what i mean ! .... you try to run a windows programm while logged into your PC ... with your laptop running Ubuntu 10.10.
Means you try to acces a windows-binarie ...while running Linux.
Thats only possible if you have Wine installed or better use Crossover.

Dropbox has also Linux binaries ... so try install the Linux version on your laptop ...and run that program .... not doing this with Wine .... Dropbox is not ment to be run with Wine if Linux binaries are available.

If you still want to try running the windows-binarie then try this command:
wine Dropbox.exe &

---

### Post by joeborder on 2011-02-23
Am I misunderstanding the nature of SSH perhaps. allow me to simplify it. Computer A is my windows pc AND the server. Computer B is the Ubuntu Client. I wish to start running a program on Computer A, the server, VIA the terminal on Computer B.

Is this impossible to do because the programs are run on the client computer instead of the server pc?

---

### Post by thesavager on 2011-02-23
> 
Is this impossible to do because the programs are run on the client computer instead of the server pc?

You could try this:

nohup Dropbox.exe &

This means it would run localy ... and you can close the terminal if you want.
But this i haven't tried on a windows machine , cos i don't use windows at all.

Also another option would be , declaring no DISPLAY 
example login:
ssh 192.168.1.125
export DISPLAY=":0.0"

to use that option u need an x-server for windows 
[http://www.pexus.com/index1.html](http://www.pexus.com/index1.html)

---


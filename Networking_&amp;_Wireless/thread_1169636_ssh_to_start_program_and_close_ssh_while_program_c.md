---
title: "ssh to start program and close ssh while program continues to run?"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-05-25
I would look this up on google except I don't know what to look up...is it possible to ssh into my Ubuntu computer, start a program from the command line then exit the ssh while leaving the program still running?

Thank you for your help :)

---

### Post by Jose Catre-Vandis on 2009-05-25
You need screen ( a program called screen )

Install:
```
sudo apt-get install screen
```

then in a terminal
```
man screen
```
to figure out how it works

---

### Post by fwre01 on 2009-05-25
Screen is good, if not a bit complicated to use at first. I tend to use 'nohup'. Prefix the command you want to run with nohup and it will continue even after you end the ssh session.

---

### Post by puppywhacker on 2009-05-25
Just for completeness, screen and nohup are valid solutions.

go into the screen (and do your thing) disconnect from the screen resume the screen
```
$ screen
ctrl-a d   
$ screen -r
```

nohup (no hangup) means that if you terminate your terminal (PUN!) the program will not hangup, so it will continue to run untill you kill it, and if it doesn't want to go through the shutdown routine, use the -9 or KILL signal
```
$ nohup doyourthing &
kill 1234
kill -KILL 1234

```

run your program, forgot to use '&' to start the program in the background? use ctrl-z to suspend and put the job in the background
```
$ doyourthing
ctrl-z
$ bg 1
$ disown 1234

```

or you just want to remotely execute something and not really open a full blown terminal
```
$ ssh user@othermachine -c doyourthing
```

---


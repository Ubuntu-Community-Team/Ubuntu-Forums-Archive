---
title: "avconv sytntax error in script"
date: 2018-02-09
forum: Multimedia Software
---

### Post by jarrodb291 on 2018-02-09
I'm very new to Ubuntu and Python and having a hard time solving this problem.

I am using avconv to create a timelapse movie from a folder full of still images.  The following command works fine on the command line, but I get a syntax error when I try to run it from a script.

pi@raspberrypi:~ $ python cleanup.py
  File "cleanup.py", line 9
    avconv -start_number 0000 -i file%04d.jpg -r 30 -vcodec libx264 output.mp4
                            ^
SyntaxError: invalid syntax

Is there a reason why this command will work fine from the CLI but not from a script file?

---

### Post by steeldriver on 2018-02-09
Hello and welcome to the forums

How exactly are you running the command from inside your script? Why are you using `python`?

---

### Post by Yellow Pasque on 2018-02-09
[https://www.cyberciti.biz/faq/python-execute-unix-linux-command-examples/](https://www.cyberciti.biz/faq/python-execute-unix-linux-command-examples/)

---

### Post by jarrodb291 on 2018-02-09
Hi!  I'm trying to run this command within Crontab, but trying to test it out before hand. I thought I had to run the script with the python prefix when executing directly, however I get the same syntax error when I include the '[COLOR=#858C93][FONT=inherit]#!usr/bin/python' [/FONT][/COLOR]at the begining and execute using

./cleanup.py

Other parts of my script work fine.

---

### Post by jarrodb291 on 2018-02-09
Thanks Temujin, that was it.  I needed to use the os.system("avconv....") to run that line.

---


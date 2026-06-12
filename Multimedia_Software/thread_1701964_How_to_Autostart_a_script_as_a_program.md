---
title: "How to Autostart a script as a program?"
date: 2011-03-07
forum: Multimedia Software
---

### Post by MODYSAMA on 2011-03-07
How can I make a script file a runnable thread auto-start program, please?
the script is: executable permission
I add: #! bin/sh -e at the first of the code
I add /home/sok/Scripts/check.sh at the end of /etc/rc.local before exit 0
I add /home/sok/Scripts/check.sh in Autostart as aprogram.

I restart the system.
no effect. Is there something missing, please in need to help??


Interested Linux beginner.

---

### Post by smuthavarapu on 2011-03-07
When do you want this script to be executed ? Only when you start the PC or every 2/3 hours as repeated program ?

If it is only once, follow these steps.

make sure you have given execute options for the .sh file.

I assume that you are using Ubuntu, then follow this.

Go to Global menu --> System --> Preferences --> Startup Applications.

Make a new entry and select this file.

Restart the machine and see if that works.

---

### Post by cchhrriiss121212 on 2011-03-07
> I add: #! bin/sh -e at the first of the code
Try this instead:
```
#!/bin/bash
```
Then you will need to right click, properties, and allow it to run as a program. Check it runs first before adding it to autostart.

---

### Post by MODYSAMA on 2011-03-07
Thank you all It works. But the problem in my script.

Excuse me, what is the different between:
```
#!/bin/bash
```
```
#!/bin/sh
```
```
#!/bin/sh -e
```

---

### Post by cchhrriiss121212 on 2011-03-07
/bin/bash is just what I always use as it is the same as what you get in a terminal. See here for the difference:
[http://www.linuxquestions.org/questions/programming-9/difference-between-bin-bash-and-bin-sh-693231/](http://www.linuxquestions.org/questions/programming-9/difference-between-bin-bash-and-bin-sh-693231/)

The -e option has the script exit when an error happens:
[http://etbe.coker.com.au/2009/11/20/shell-code-destroy-your-os/](http://etbe.coker.com.au/2009/11/20/shell-code-destroy-your-os/)

---


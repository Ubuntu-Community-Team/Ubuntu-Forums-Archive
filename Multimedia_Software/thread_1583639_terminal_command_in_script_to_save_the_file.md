---
title: "terminal command in script to save the file"
date: 2010-09-28
forum: Multimedia Software
---

### Post by Kognit on 2010-09-28
Hi

I use webcam with the streamer application. So, to record a video i have to put in terminal something like this:
```
streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o /home/shark/untitled.avi

```

I know i can use other applications but i have got problems with all except with this. 

This is really annoying because it is a delay job. So, i am wondering how can i make a script that the terminal will ask me to name the file or even better to ask where to put my file.

thx for help

---

### Post by linux-hack on 2010-09-28
well you do the same thing but like this :

```

streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o $1

```
and then you call your script like this :

```
./script /home/shark/untitled.avi
```

It this what you wanted ?

---

### Post by Kognit on 2010-09-28
thx for reply

This is much better but the new computer is not for me and the person that use it is not so good with the computers. Is there any possibility that it will ask you for the path and the name in terminal?

thx

---

### Post by Hiren Modi on 2010-09-28
You Can use the below caommand ,

echo "command" > file-name

---

### Post by linux-hack on 2010-09-28
A simple bash script wil do the trick.
NOTE: if you give the path you also give the name of your file.
```

#!/bin/bash
echo "Please enter the path and name for you file"
echo "Example : /home/shark/untitled.avi - Where untitled is the name of your file."
read pathAndFileName

if [ $pathAndFileName -ne "" ] then
    streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o $pathAndFileName
fi

```

After that you just need to execute the script:

```
./script_name
```

---

### Post by Kognit on 2010-09-28
linuxhack,
yeah, this is what i want but the problem is that the terminal closes when i put the path. The terminal should be open because this is the only way that you can record.

---

### Post by linux-hack on 2010-09-28
```
#!/bin/bash
echo "Please enter the path and name for you file"
echo "Example : /home/shark/untitled.avi - Where untitled is the name of your file."
read pathAndFileName

if [ $pathAndFileName -ne "" ] then
    streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o $pathAndFileName
    wait # Waits for the process to finish
fi
```

---

### Post by Kognit on 2010-09-28
The terminal output when i launch script:
```
/home/shark/test: line 9: syntax error near unexpected token `fi'
/home/shark/test: line 9: `fi'

```

---

### Post by linux-hack on 2010-09-28
Or you can do it this way : 

```
#!/bin/bash
echo "Please enter the path and name for you file"
echo "Example : /home/shark/untitled.avi - Where untitled is the name of your file."
read pathAndFileName

if [ "$pathAndFileName" -ne "" ] 
then
    streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o $pathAndFileName &
    wait $!
fi
```

I forgot some quotes :P

---

### Post by Kognit on 2010-09-28
I get the same output - that the problem is with "fi"

---

### Post by Kognit on 2010-09-28
And now i get:
```
./test: line 6: [: /home/shark/Desktop/as.avi: integer expression expected

```

---

### Post by linux-hack on 2010-09-28
I rely don't know bash any more :D

```
#!/bin/bash
echo "Please enter the path and name for you file"
echo "Example : /home/shark/untitled.avi - Where untitled is the name of your file."
read pathAndFileName

if [ -z "$pathAndFileName" ]; then
    echo "String is empty"
else
    streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o $pathAndFileName &
    wait $!
fi
```

---

### Post by linux-hack on 2010-09-28
The above works for me

---

### Post by Kognit on 2010-09-28
Well, you know more bash than me :)

But the problem still occurs. I really don't know. I set the file to be exececutable but the problem is still here.

---

### Post by Kognit on 2010-09-28
It woooooooooooooooorks!!!!

I messed up something :)

---

### Post by linux-hack on 2010-09-28
You still get the error : for the `fi` ? what are the permissions of your file ? did you do a ```
 chmod +x script_name 
``` ?

---

### Post by linux-hack on 2010-09-28
Ok nice ... so problem solved ?

---

### Post by Kognit on 2010-09-28
It's cool now. Everything works now. Thank you for your help. Really. I learned today a lot.

But i have one additional question: how to put a permanent path in the script so that i will write only the name of the file?

thx

---

### Post by Kognit on 2010-09-28
Yes, it is solved now. Thx to you :)

---

### Post by linux-hack on 2010-09-28
> **Kognit said:**
> 
But i have one additional question: how to put a permanent path in the script so that i will write only the name of the file?

thx

You take the same script and change it a little bit like this :

```

#!/bin/bash
echo "Please enter the path and name for you file"
echo "Example : /home/shark/untitled.avi - Where untitled is the name of your file."
read fileName

if [ -z "$fileName" ]; then
    echo "No file name mentioned"
else
    streamer -q -c /dev/video0 -f rgb24 -r 24 -t 00:30:00 -o  /home/shark/$fileName &
    wait $!
fi

```

---

### Post by Kognit on 2010-09-28
Thanks a lot. You rule!  :)

---

### Post by linux-hack on 2010-09-28
Your welcome :D

---


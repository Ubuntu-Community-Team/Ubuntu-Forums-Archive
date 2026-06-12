---
title: "Please Help: Shell Script to Convert Videos using FFMPEG"
date: 2011-09-19
forum: Multimedia Software
---

### Post by tomascivinod on 2011-09-19
Hi Guys,
I have been trying the find or create a script to take any video files in a folder and to convert them to a certain format.

```
for m in *.mp4
	do
	ffmpeg -i /home/tom/Desktop/help/“$m” -acode aac -ab 128k -vcodec mpeg4 -b 1200k -s 480*272 -y /home/tom/Desktop/help1/”$m”
done
```
After I pieced together the ffmpeg command I found that it did not work, as the file had spaces and capitals in it's name.

So then I found this bit of code to remove the unwanted spaces and uppercase parts:

```
 # remove spaces
for m in *.[Mm][Pp][Gg]; do mv "$m" `echo $i | tr ' ' '_'`; done > /dev/null 2>&1 &

# remove uppercase
for m in *.[Mm][Pp][Gg]; do mv "$m" `echo $i | tr '[A-Z]' '[a-z]'`; done > /dev/null 2>&1 &

```

Now I am unsure of where to go for help. It does not remove any of the unwanted formatting and even when I remove it, the script still does not convert it. 

PLEASE HELP!!!!
Thanks,
Tom

---

### Post by sisco311 on 2011-09-20
Try something like:
```
#!/bin/bash

shopt -s nocaseglob nullglob

cd /home/user/Desktop/dir || exit 1
for file in ./*.**ext**
do
    ffmpeg -i "$file" OPTIONS -o "${file%.**ext**}.**new**"
done

```

Where **ext** is the extension of the files (e.g. mpg) and **new** is the new extension (e.g. mp4).

---

### Post by tomascivinod on 2011-09-20
Thanks for the quick response but I am not sure what is wrong with it, when I run it, it just returns cd: 5 : can't cd to /home/user/Desktop/help.

```
tom@freyr:~/Desktop$ sh 2.sh
2.sh: 3: shopt: not found
cd: 5: can't cd to /home/user/Desktop/help
```


I copied and changed the folders in your code to the ones that match my system.
Here is what I changed it to:

```
#!/bin/bash

shopt -s nocaseglob nullglob

cd /home/user/Desktop/help || exit 1
for file in ./*.ext
do
    ffmpeg -i "$file" -acode aac -ab 128k -vcodec mpeg4 -b 1200k -s 480*272 "${file%.mp4}.mpg"
done
```
Also, could you please explain what each part does?

---

### Post by sisco311 on 2011-09-20
sh is not bash. In Ubuntu, sh is a symlink to dash. Either run:
```
bash 2.sh
```
or make the file executable:
```
chmod +x 2.sh
```
and simply run:
```
./2.sh
```

And you forget to replace ./*.ext with the ./*.mp4

Oh, and don't use extension in the name of your scripts. Scripts define new commands that you can run, and commands are generally not given extensions. Also: bash scripts are *not* sh script (so don't use .sh) and the extension will only cause dependencies headaches if the script gets rewritten in another language.

For more details, check out BashFAQ #20 (link in my signature).

---

### Post by tomascivinod on 2011-09-20
Ok, I have changed the .ext to .mp4
I have removed the extension and run it again and the terminal returned this:

```
2: line 5: cd: /home/user/Desktop/help: No such file or directory

```

But that doesn't make sense because the folder is there and it has an mp4 in it.

Hmmm, what is wrong?

---

### Post by sisco311 on 2011-09-20
In the cd command, replace **user** with your username (**tom**).

Or instead of /home/tom you could use the HOME variable
```
cd "${HOME}/Desktop/help" || exit 1
```

---

### Post by tomascivinod on 2011-09-20
```
FACEPALM
```
I really am not with it today.
Sorry to everyone that has read this thread and to sisco that I am an idiot....

Edit: I also forgot to ask, if I run this as a cron job, it will just keep re-encoding the files, so, how do I delete each file after it is done? I need to convert to a few different formats as well.

So the workflow (sorry, coming from mac :( ) Strip formatting->Convert for iphone->Convert for Computer->Convert for ipad->Delete source file->Start with next file.

How do I add this?

Edit 2: I have stopped being lazy, I just run this afterwards...

```
cd /home/tom/Desktop/help
find . -exec rm -rf {} \;
done
```

---


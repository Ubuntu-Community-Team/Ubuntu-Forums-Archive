---
title: "makemkv install problems"
date: 2011-05-27
forum: Multimedia Software
---

### Post by motherboyxx on 2011-05-27
I am trying to install makemkv for ripping dvd/BR into .mkv files from lifehacker.com tutorial.  Here is my issue.  

Step1: ensure prerequisites installed...ran command Done
Step2: download oss and bin files from "makemkv" website and extract...done
Step3: cd into source package and enter commands

Step 3 is my problem i am typing "cd" into terminal and dragging the extracted folder into terminal.  This is what I get

$ cd'/home/dan/Downloads/makemkv_v1.6.8_oss' 
bash: cd/home/dan/Downloads/makemkv_v1.6.8_oss: No such file or directory

This happens for both the oss and bin.  I tried redownloading the files and no luck.   Help?
Oh and running natty

---

### Post by mc4man on 2011-05-27
> my problem i am typing "cd" into terminal and ....
type cd, hit the space bar, then D&D your folder. 
so it's 
```
cd '/home/dan/Downloads/makemkv_v1.6.8_oss'
```

---

### Post by motherboyxx on 2011-05-27
Well that worked, however I am apparently a huge noob because I am not getting a working app after all the input.  Here were my steps.

Same as listed above
 
used the cd "space" and file drag and drop
ran the new commands "make -f makefile.linux", and "sudo make -f makefile.linux install" for both the oss and bin file. 

I then got a user agreement window to which i replied yes.  terminal gave me a bunch of output and it looked good.  I closed terminal and user/bin/makemkv file does not exist. 

I repeated the installation steps and this is my output (that i saved this time). 

dan@dan-Inspiron-1545:~$ cd '/home/dan/Downloads/makemkv_v1.6.8_oss' 
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_oss$ make -f makefile.linux
type "sudo make -f makefile.linux install" to install
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_oss$ sudo make -f makefile.linux install
[sudo] password for dan: 
rm -f /usr/lib/libdriveio.so.0
rm -f /usr/lib/libmakemkv.so.1
rm -f /usr/bin/makemkv
install -t /usr/lib out/libdriveio.so.0 out/libmakemkv.so.1
ldconfig
install -t /usr/bin out/makemkv
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_oss$ cd '/home/dan/Downloads/makemkv_v1.6.8_bin' 
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_bin$ make -f makefile.linux
type "sudo make -f makefile.linux install" to install
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_bin$ sudo make -f makefile.linux install
rm -f /usr/bin/makemkvcon
rm -f /usr/bin/cddump
rm -f /usr/share/MakeMKV/*.mo.gz
install -d /usr/share/MakeMKV
install -t /usr/bin bin/amd64/makemkvcon
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_deu.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_jpn.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_spa.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_ptb.mo.gz
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_bin$ 
dan@dan-Inspiron-1545:~/Downloads/makemkv_v1.6.8_bin$ 

obviously you can see I hit enter at the end a couple times

Still no app to be found

---

### Post by motherboyxx on 2011-05-27
Oh Lord, I am sorry to have posted that last one...i am blaming this on heat stroke and a lingering migraine from yesterday.

All is well and working fine

---

### Post by motherboyxx on 2011-05-28
I marked this thread as solved.  Here was my problem/solution for anyone else who was working outside all day and then started doing computer work

ensure after you download the program you look in the right place (duh).  The file will be contained in usr/bin/makemkv, I however, read it as username/bin which is a more superficial file. usr/bin is where all the executable app files go (again duh).  Add a launcher in menu settings and enjoy.

---


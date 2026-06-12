---
title: "Avermedia A828"
date: 2010-10-19
forum: Multimedia Software
---

### Post by sedcomet on 2010-10-19
I used to use it with windows  but now I have found that ubuntu fits me better and I deleted windows...
I downloaded the 2.8 beta driver for linux([http://www.avermedia.com/avertv/Support/Download.aspx?Type=APDriver&tab=APDriver&id=31](http://www.avermedia.com/avertv/Support/Download.aspx?Type=APDriver&tab=APDriver&id=31)) and when   I'm opening .sh file in terminal  it says me...> "dialog" is not installed on your system, try to install.
Installing package "dialog", please wait a moment ....
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Verifying archive integrity...
Extracting archive...
Running installer...
"dialog" is not installed on this system. Press [enter] to abort.
What Am I doing wrong??

---

### Post by sohlinux on 2010-10-19
you need to be doing this as root, thats why you are getting Permission denied) type sudo file.sh

---

### Post by sedcomet on 2010-10-19
root?? sorry but new to linux

---

### Post by sedcomet on 2010-10-19
ok...I did it

---

### Post by sohlinux on 2010-10-19
> **sedcomet said:**
> root?? sorry but new to linux

In Linux there is a superuser named root for doing admin tasks like what you are trying to do.

you just need to open a terminal then cd (change directory) to the folder which contains your file that you want to execute then type 

sudo name_of_file.sh to install it.

sudo is the command for working as the root user

---

### Post by sedcomet on 2010-10-19
where can I find the 32bit driver? :P

---

### Post by sohlinux on 2010-10-19
> **sedcomet said:**
> ok...I did it

:guitar:

---

### Post by sohlinux on 2010-10-19
> **sedcomet said:**
> where can I find the 32bit driver? :P

same site under Linux x86

---

### Post by sedcomet on 2010-10-19
oh....Idid n't saw it :P 
Thanks you helped me a lot now i'm ready for:popcorn:
wich program can I use to see the composite??

---

### Post by sedcomet on 2010-10-19
???:confused:

---

### Post by sohlinux on 2010-10-19
> **sedcomet said:**
> ???:confused:

kdetv or tvtime will allow you to view the composite

---

### Post by sedcomet on 2010-10-20
I installed tvtime but whn i'm opening it it close imiidiently

---

### Post by sohlinux on 2010-10-20
> **sedcomet said:**
> I installed tvtime but whn i'm opening it it close imiidiently


open a terminal window and run tvtime then paste the error message here...

---

### Post by sedcomet on 2010-10-20
what's the command to run the program?

---

### Post by sedcomet on 2010-10-20
When Im typing "tvtime" it says me > evillie@evilliePriest:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/evillie/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/evillie/.tvtime/tvtime.xml: Permission denied.
videoinput: Cannot open capture device /dev/video0: No such file or directory
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
I/O error : Permission denied
I/O error : Permission denied


---

### Post by sohlinux on 2010-10-20
> **sedcomet said:**
> When Im typing "tvtime" it says me

run sudo tvtime then paste any errors here

---


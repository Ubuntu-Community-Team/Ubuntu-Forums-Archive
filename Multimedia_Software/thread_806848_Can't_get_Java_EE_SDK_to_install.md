---
title: "Can't get Java EE SDK to install"
date: 2008-05-25
forum: Multimedia Software
---

### Post by Mijoker on 2008-05-25
I am trying to install the file java_ee_sdk-5_05-linux.bin, and have run chmod +x java_ee_sdk-5_05-linux.bin, and then tried to run it and I keep getting the error:

bash: java_ee_sdk-5_05-linux.bin: command not found
or
bash: java_ee_sdk-5_05-linux: command not found

how do I get this thing to install?? I think I may have forgotten a step I did, but I can't remember at this time.

And judging by previous posts, I am NOT running the 64 version of ubuntu...
if you need anymore information, just ask. 
Thanks in advance.

ps: I LOVE ubuntu!!

---

### Post by LeoSolaris on 2008-05-25
Add the .bin on the end of the command.

[http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)

---

### Post by txcrackers on 2008-05-25
You have to pre-pend the file to execute with it's path - most directories are not in your $PATH. If you're in the directory where the .bin file is, try ```
./java_ee_sdk-5_05-linux.bin
```
Note the "./" at the beginning of the filename.

---

### Post by Mijoker on 2008-05-25
ok, I tried it in regular and superuser...

mijoker@mijoker-desktop:~/Desktop$ ./java_ee_sdk-5_05-linux.bin
./java_ee_sdk-5_05-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


root@mijoker-desktop:/home/mijoker/Desktop# ./java_ee_sdk-5_05-linux.bin
./java_ee_sdk-5_05-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

root@mijoker-desktop:/home/mijoker/Desktop# java_ee_sdk-5_05-linux.bin
bash: java_ee_sdk-5_05-linux.bin: command not found

---

### Post by Hadraniel on 2008-05-28
Install "libstdc++5" e.g. invoking

```
sudo apt-get install libstdc++5
```


I'm now stuck at
> $ ./java_ee_sdk-5_05-linux.bin
Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...
Extracting installation files...
Launching Java(TM) 2 Runtime Environment...

.. and all I got is a grey square, missing any text or controls.
Any hints?

---

### Post by miko777 on 2008-06-16
Try refreshing your window manager, usually under compiz, if you've installed it.

Failing that, log out and start a new session by clicking in the bottom left to choose "Select Session". Then choose "Failsafe Terminal" and log in as usual.

Try what you want from the terminal which can boot up GUI programs. Once complete, type "exit" at the command line in order to revert to log on screen and remember to change your session again by the above method but choose GNOME or whatever your usual session is. Log in as usual and see if it worked.

---

### Post by Hadraniel on 2008-06-17
Changing the AWT_TOOLKIT as described [here](http://ubuntuforums.org/showpost.php?p=5040968&postcount=4) finally worked for me.

Thanks anyway :)

---

### Post by 2ernest.kg on 2008-08-18
hello everyone
I am new to Ubuntu, have downloaded and installed 8.04TLS, installed under Windows,
Now i want to install netbeans that needs jvm
I downloaded java_ee_sdk-5_05-linux.bin
Please help me, how can i install it
*.bin file is on the desktop
I am trying
/Desktop$ sudo chmod +x java_ee_sdk-5_05-linux.bin
/Desktop$ ./java_ee_sdk-5_05-linux.bin
{it says}
./java_ee_sdk-5_05-linux.bin: error while loading shared libraries: libstdc+++.so.5: cannot open shared object file: No such file or directory

And here i read that i should install libstdc++5
I downloaded libstdc++5-3.3.6-3mdk.x86_64.rpm
please what to do me next, if after installing libstdc* it will be ok, how to install me this libstdc++5-3.3.6-3mdk.x86_64.rpm 

I read that RPM packages are installed in the next way
{lib*.rpm package is on desktop)
/Desktop$ sudo alien -i libstdc++5-3.3.6-3mdk.x86_64.rpm
{it says}
sudo: alien: command not found

Please i would be very glad if someone could help me to install this, this would be my first software installation on Ubuntu.

---

### Post by Hadraniel on 2008-08-18
Don't use RPMs on Ubuntu, as long there are native packages.

To solve the libstc++5 issue, simply read and understand the first lines of posting [#5](http://ubuntuforums.org/showpost.php?p=5063825&postcount=5) in this thread.

---

### Post by 2ernest.kg on 2008-08-18
thanks for hlp, Hadraniel
but i don't have an Internet, how can i install it(libstdc++5) install it from package.

---

### Post by 2ernest.kg on 2008-08-19
on
--------------------------------
$sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree
E: Couldn't find package libstdc++5
$
--------------------------------
That problem i have, i don't have an internet, and i think libstdc++5 is not on the source list of the APT, am i right?
so i should install from package,
I have libstdc++5-3.3.6-3mdk.x86_64.rpm only, if you suggest not to use .rpm, what can i do, give me other link, to dowload with another package format.
Please anyone help needed.

---

### Post by Hadraniel on 2008-08-21
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for the packages you need.
In your case, go for libstdc++5 and load the deb-file for your Ubuntu-Version and -Architecture.

Install the deb-file just as any other, e.g. with aptitude or dpkg.

[*I'm on vacation for 3 weeks now, so don't expect any more answers from me before mid September*]

---

### Post by vimalkrishna on 2008-09-04
Hi Mijoker

I had similar problem:
> java_ee_sdk-5_05-linux.bin:No such file or directory

First use 

> # file * 
in the directory you have kept .bin file

it may show:
java_ee_sdk-5_05-linux.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped

Here is clue: **it is 32-bit LSB executables**


Now see what you have
> # lsb_release -a

_No LSB modules are available._
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy


If LSB modules is missing get it installed

# apt-cache search LSB | more

see the result and select the LSB module and install by 

> # apt-get install LSB

after that do similarly

> # apt-get install ia32-libs


Now installation should succeed with

> ./java_ee_sdk-5_05-linux.bin 

ubuntu x86 64-bit refuses to install 32 bit application like java_ee_sdk-5_05-linux.bin  

Hope it helps

vimal krishna

---


---
title: "no wireless"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by AmerNewbieInDE on 2009-08-08
help, i just installed Ubuntu 9.04, i have a intel wireless 5100agn, out of the box i see the correct card, correct network ssid and security. I put in the network key but it does not connect... any ideas??? Yes, i reentered the key a number of times...but still no go.
 
also, i have a hp photosmart (C7280) wireless network printer, i tried the software from hp, but even with a wired network, i can not install the priner, it is not found.

---

### Post by AmerNewbieInDE on 2009-08-08
ok, i figured out i gotta move/copy a new file into /lib/firmware but now a stupid question... how.. i try but it tells me i dont have permission.. only root have access to modify the folder.

---

### Post by Crafty Kisses on 2009-08-08
Well this all depends if you're using the CLI or GUI. If you're using the GUI you can run the following:
```
gksu nautilus
```
Then from their you can copy/remove the files you need, if you're in the CLI you can always use the following command:
```
sudo mv && sudo cp
```

---

### Post by AmerNewbieInDE on 2009-08-08
thanks codename, i figured there should be a move/copy command, but do i make it from terminal? and add the complete from and to??? sorry, i am totally new to this.

---

### Post by Crafty Kisses on 2009-08-08
Don't be sorry! Well you could always do the first way, open a terminal and type:
```
gksu nautilus
```
That would probably be easier for you to copy/move files, but be careful, you are root when you're doing this. If you want to like copy/move files from the terminal, I'll give you a couple of examples:

**Copying a file:**
```
sudo cp /path/to/directory
```
[B]
Moving a file:[/B]
```
sudo mv filename /new/directory/filename
```
Those are the ways you can copy/move files around.

---

### Post by AmerNewbieInDE on 2009-08-09
hmm, ok, now another stupid question... lol, i got the file where it is supposed to be, but how do i associate the devise to the driver

---

### Post by AmerNewbieInDE on 2009-08-09
it is fixed, i just have to learn to read more..lol

---

### Post by AmerNewbieInDE on 2009-08-09
well, it is not fixed. everytime i restart the pc, i must reenter 
sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

 where do i put this so it automatically starts

---

### Post by Crafty Kisses on 2009-08-09
I think you need to put those modules in the /etc/modules configuration file, so what you can do is run:
```
sudo gedit /etc/modules
```
Then once in the file you can add these lines:
```
iwlagn
iwlagn 11n_disable=1 11n_disable50=1
```
If those are the modules you are having to constantly reload at boot, then put them in that file.

---

### Post by AmerNewbieInDE on 2009-08-09
thanks for the tip, i will try, but what is the use of the first line... why not just the second line

---

### Post by AmerNewbieInDE on 2009-08-09
well, i tried it, and it didnt work:( i still had to enter the code through terminal. anymore ideas

---

### Post by Crafty Kisses on 2009-08-09
Before you have to load the modules, I want you to go in a terminal and type:
```
lsmod | grep iwlagn
```
Then once you have actually loaded the modules, I want you to run:
```
lsmod | grep iwlagn
```

---

### Post by AmerNewbieInDE on 2009-08-09
ok, i rebooted...

BEFORE:
laptop:~$ lsmod | grep iwlagn
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
mac80211              217592  2 iwlagn,iwlcore
cfg80211               38288  3 iwlagn,iwlcore,mac80211

AFTER:

laptop:~$ lsmod | grep iwlagn
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
mac80211              217592  2 iwlagn,iwlcore
cfg80211               38288  3 iwlagn,iwlcore,mac80211
laptop:~$ 

looks the same to me, but before, it only shacks hands, after, it is invided in the door.. lol

---

### Post by Crafty Kisses on 2009-08-09
That's really weird, open up your modules configuration file again, by running:
```
gksudo gedit /etc/modules
```
Then once you're in there, remove the line:
```
iwlagn
```
Then just keep the following line:
```
iwlagn 11n_disable=1 11n_disable50=1
```
See if that makes a difference. It appears that the modules are loading at start, so not sure what's going on.

---

### Post by AmerNewbieInDE on 2009-08-09
ok, rebooted again, same thing... still had to manually code it

---

### Post by Crafty Kisses on 2009-08-09
This is really weird, I'm trying to think off the top my head if there is an autoload directory. Try and see if this directory exists:
```
/etc/modules.autoload.d/
```
As I'm not on a Linux box right now, check and see if this directory exists. Then tell me the contents of the file, from what I remember I think there is a list of kernels, or something and then you would put the module in the appropriate kernel.

---

### Post by AmerNewbieInDE on 2009-08-09
nope.. no such file or directory.. if it is easier or if you want.... im me on aim

---


---
title: "How to Install AE1000 rt2870 on xubuntu or ubuntu"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by ericrichards420 on 2011-03-06
Alright yall, I just got my wireless usb device to work on ubuntu 10.10. I did alot of searching and I finally figured it out. this is what I did.

1.Download the linux drivers from this post, its called Ralink_RT3572USB_drv2400.zip

2.Extract them to a directory.

3.Make sure you have *build-essential* installed on your computer. you can do this by opening a terminal
and typing ```
 sudo apt-get install *build-essential *
```

4.Now install linux headers so that you can compile the drivers.
```
 sudo apt-get install linux-headers-$(uname -r)

```

5.Now in your terminal goto where you extracted the Ralink_RT3572USB_drv2400 files.
once in that directory type ```
 sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk 
```

6.and then ```
 sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c 
```

7.Now then goto the directory where you extracted the Ralink_RT3572USB_drv2400 files and goto Ralink_RT3572USB_drv2400/include/os "NOTE your directory may be differnt!!!" just make sure your find the file called rt_linux.h and open it with a text editor.

8.Now that we have rt_linux.h opened goto line 1077 or search for string **usb_buffer_alloc** change this to [B]usb_alloc_coherent

[/B]9.Now on line 1078 change** usb_buffer_free **to** usb_free_coherent** and and save that file.

****10.Now you are ready to install the drivers. open your terminal and goto the directory where you extracted the drivers earlyer. and type 
```
 make && sudo make install 
```

11. restart your computer and make sure that your adapter is plugged in.

These instructions are for xubuntu, and ubuntu 10.10 and newer. if you are using ubuntu 10.04 or older then do this process skipping step 7. and 8.
I'm using the ae1000 on a 550 mhz computer with 256 megs of ram using xbuntu. I have an up to date computer as well, this one was just for the a project.

---

### Post by chili555 on 2011-03-06
I believe you need *build-essential* not *build essential*. Also, I think you'll need *linux-headers-generic*. Excellent HOWTO. Thanks.

---

### Post by ericrichards420 on 2011-03-06
Yeah, I forgot I downloaded my kernel source, I'm not sure if the source is needed or just the header files.

---

### Post by chili555 on 2011-03-06
> I'm not sure if the source is needed or just the header files.I am sure you need, at least, the headers. The source works, too; however the headers are smaller and quicker to download and install.

---

### Post by TheKorn2 on 2011-03-28
Thank you so much for writing this how-to!  I was following the instructions over on fedora forums and couldn't get them to work.  I followed these, and my adapter came right up!

Thanks again!

---

### Post by bcinman on 2011-04-14
I'm a noob....

I've followed your step by step instructions as exactly instructed and still have not been able to get my AE1000 wireless USB adapter working...

Any other ideas?

ver:  ubuntu 10.10

Brian...

---

### Post by jetbangdink on 2011-04-26
were you hardwired to a router for internet when you did this im not and getting responses like unable to locate build-essential package

---

### Post by jetbangdink on 2011-04-26
When I open terminal and type 
 
```
 sudo apt-get install build-essential 
```
 
I get this error 
 
```
 Reading package lists... Done
Building dependency tree
Reading state information...Done
E: Unable to locate package build-essential
```
 
 
so do you have to be connected to the internet through ethernet for this to work?
What do you mean by extract the ralink file to a directory, and how do you open that directory in terminal?

---

### Post by croozer on 2011-06-02
i am on a hardwired connection trying to follow your walkthrough, once i go into the directory that i unzipped the files to (/home/viziotech/Desktop/Ralink_RT3572USB_drv2400) i hit enter to enter that directory, then i enter in the code at line 5 and hit enter. then an error comes up that says, 

sed: can't read ./os/linux/config.mk: No such file or directory


any suggestions? im very new to linux, and i appreciate the help...

thanks!
croozer

---

### Post by ericrichards420 on 2011-06-05
jetbangdink you need to add sources in your repository. add 

```
http://archive.canonical.com/ubuntu lucid partner

``` 

and then

```
sudo apt-get update

```
then follow the tutorial.

---

### Post by ericrichards420 on 2011-06-05
croozer make it easyer by moving the folder with the drivers called Ralink_RT3572USB_drv2400 to your home directory. now rename this directory to ae1000
It looks like to me you might have miss typed something somewhere down the line. once you do that try it again.
also make sure your using the right commands. you said that you typed the name of that directory and hit enter make sure you type
```
 cd /home/viziotech/ae1000 
```that will take you to the directory where you will then enter step 5 of the walkthrough

---

### Post by subconscious on 2011-07-20
Worked beautifully. Thank you. 

Pretoia ZA

---

### Post by baddnady23 on 2011-07-21
Your a god send.  Thank you.

---

### Post by baddnady23 on 2011-07-23
.

---

### Post by saschamange on 2011-08-24
I had the same problem as croozer, i.e.

sed: can't read ./os/linux/config.mk: No such file or directory

Similarly for the rtusb_dev_id.c file. 

After extracting the archive downloaded from ericrichards420's first post, I renamed it ae1000 and put it in my /Desktop directory. In the terminal, I changed directory to:

me@TOSHIBA-NB305:~/Desktop/ae1000$

But after receiving the "no such file or directory" message re config.mk, I simply typed in the full file name, and so the command worked. Same for the "rtusb_dev_id.c" command, i.e. I ran:

sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' /home/me/Desktop/ae1000/2010_06_25_RT3572_Linux_STA_v2.4.0.0/common/rtusb_dev_id.c

So I got all the way up to step 10 with everything seeming to execute (after the above adjustments), but when I ran:

make && sudo make install

I got:

make: *** No targets specified and no makefile found.  Stop.

What might be the solution? Ive tried setting file permissions on the ae1000 folder and its files. Since I don't know anything about how to use a compute, I'm pretty much up a creek here. I'd really appreciate the help. Thanks.

---

### Post by Domonico on 2011-08-25
ok I hate to sound stupid even tho I am but how do I get to a folder in the terminal?

---

### Post by Domonico on 2011-08-25
ok I hate to sound stupid even tho I am but how do I get to a folder in the terminal? like my file for the driver is in my downloads folder and on my sd card so what do I type in to get to that folder under terminal?

---

### Post by Domonico on 2011-08-25
I did all that execpt change the file rt_linux.h cause there wasn't one but there was a rt_linux.c and my wireless adapter still doesnt work with ubuntu

> **ericrichards420 said:**
> Alright yall, I just got my wireless usb device to work on ubuntu 10.10. I did alot of searching and I finally figured it out. this is what I did.

1.Download the linux drivers from this post, its called Ralink_RT3572USB_drv2400.zip

2.Extract them to a directory.

3.Make sure you have *build-essential* installed on your computer. you can do this by opening a terminal
and typing ```
 sudo apt-get install *build-essential *
```4.Now install linux headers so that you can compile the drivers.
```
 sudo apt-get install linux-headers-$(uname -r)

```5.Now in your terminal goto where you extracted the Ralink_RT3572USB_drv2400 files.
once in that directory type ```
 sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk 
```6.and then ```
 sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c 
```7.Now then goto the directory where you extracted the Ralink_RT3572USB_drv2400 files and goto Ralink_RT3572USB_drv2400/include/os "NOTE your directory may be differnt!!!" just make sure your find the file called rt_linux.h and open it with a text editor.

8.Now that we have rt_linux.h opened goto line 1077 or search for string **usb_buffer_alloc** change this to [B]usb_alloc_coherent

[/B]9.Now on line 1078 change** usb_buffer_free **to** usb_free_coherent** and and save that file.

10.Now you are ready to install the drivers. open your terminal and goto the directory where you extracted the drivers earlyer. and type 
```
 make && sudo make install 
```11. restart your computer and make sure that your adapter is plugged in.

These instructions are for xubuntu, and ubuntu 10.10 and newer. if you are using ubuntu 10.04 or older then do this process skipping step 7. and 8.
I'm using the ae1000 on a 550 mhz computer with 256 megs of ram using xbuntu. I have an up to date computer as well, this one was just for the a project.

---

### Post by MidnightJava on 2011-08-29
Thanks, this worked for me. However, now and then (a couple times in the past two months), after installing updates in update-manager, the driver is wiped out and I have to make and make install again. How can I make it not be over-written by subsequent updates?

---

### Post by chili555 on 2011-08-29
> **MidnightJava said:**
> Thanks, this worked for me. However, now and then (a couple times in the past two months), after installing updates in update-manager, the driver is wiped out and I have to make and make install again. How can I make it not be over-written by subsequent updates?When a new kernel is pushed out by Update Manager, you must build the driver module for the newer kernel. That's just the way built-from-source modules work. Eventually, I can't say when, rt3572sta will be included. When that day comes, building from scratch will no longer be required.

---

### Post by MidnightJava on 2011-08-29
OK, thanks for the explanation.

---

### Post by saschamange on 2011-08-31
If there's any more information that would be of help to the community in answering my question (#15), please let me know. 

I'm pretty sure my problem (and croozer's) did not arise as a result of some kind of freak ctl+c ctl-v transcription error in entering the suggested commands, but that the solution is quite basic and has less to do with the specifics of installing ae1000 rt2870 on ubuntu and more to do with basic linux administration/terminal skills. But I could be wrong. I'm obviously wrong about something. 

I have just repeated the recommended steps, but once again, to be clear, this command:

--------------------------------
sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk
--------------------------------

results in this message in my terminal:

--------------------------------
sed: can't read ./os/linux/config.mk: No such file or directory
--------------------------------

I suppose I could once again be more specific, enter the full path with the file name and run the command successfully (as I reported doing in my first post), but I still anticipate that down the road at step 10 when I enter:

--------------------------------
make && sudo make install
--------------------------------

I will receive the same message:

--------------------------------
make: *** No targets specified and no makefile found. Stop. 
--------------------------------

I'm able to log in as su on my machine; I'm running Ubuntu 11.04 on a Toshiba NB305-N442BL netbook.

---

### Post by xllente on 2011-09-20
[ericrichards420]("http://ubuntuforums.org/member.php?u=979683"), Thank You! Your steps worked perfectly! :P

---

### Post by ericrichards420 on 2012-03-04
make sure you in the right directory
EXAMPLE: /home/viziotech/Desktop/Ralink_RT3572USB_drv2400

---

### Post by koji-lik on 2012-03-05
i come to step 10 and then

gore@gore-desktop:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1$ make && sudo make install
make -C tools
make[1]: Entering directory `/home/gore/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gore/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/gore/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/gore/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.32-38-generic/build SUBDIRS=/home/gore/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make: *** /lib/modules/2.6.32-38-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

please help

---

### Post by chili555 on 2012-03-05
In kernel version 2.6.32, the built-in rt2870sta should work pretty much out of the box. What is wrong?

---


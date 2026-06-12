---
title: "latest Realtek driver install: make: *** [all] Error 2"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by drspikes on 2010-04-06
Hi,

UNR 9.10.

I've been struggling to get my wifi working on my Samsung n210 netbook which has the Realtek rtl8192e PCI card.  I was emailed the most up-to-date driver and instructions on how to install, however, the first instruction caused an error.

/rtl8192e_linux_2.6.0013.0127.2010# make
make[1]: Entering directory `/lib/modules/2.6.31-21-generic/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.31-21-generic/build'
make: *** [all] Error 2

Can anyone give me some tips?

Many thanks

---

### Post by chili555 on 2010-04-06
Do you have *build-essential* and *linux-headers-generic* installed?

---

### Post by drspikes on 2010-04-06
> **chili555 said:**
> Do you have *build-essential* and *linux-headers-generic* installed?

Thanks for helping.

I didn't seem to have build-essential installed and there was an update for linux-headers-generic.  The strange thing is I have compiled 3 other programs prior to this.

#make still gives me same error post-update:
make[1]: Entering directory `/lib/modules/2.6.31-21-generic/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.31-21-generic/build'
make: *** [all] Error 2

---

### Post by chili555 on 2010-04-06
Can you please attach the tar.bz2 to your reply so I can examine it?

---

### Post by drspikes on 2010-04-06
> **chili555 said:**
> Can you please attach the tar.bz2 to your reply so I can examine it?

The file is just greater than the limit for this site.  I have uploaded it here:
[http://www.4shared.com/file/258556351/346cf300/rtl8192e_linux_26001301272010t.html](http://www.4shared.com/file/258556351/346cf300/rtl8192e_linux_26001301272010t.html)

---

### Post by chili555 on 2010-04-06
It makes perfectly for me, no errors and no warnings. Please do:```
ls /usr/src
uname -r
```Do you have linux-headers exactly matching your running kernel? Here is my example:> ls /usr/src
acerhk.tar.bz2                   linux-headers-2.6.31-16          linux-OLDVERSION.1269801631
bcmwl-5.10.91.9+bdcom            linux-headers-2.6.31-16-generic  linux-OLDVERSION.1269801644
linux                            linux-headers-2.6.31-17          linux-source-2.6.31
linux-headers-2.6.28-11-generic  linux-headers-2.6.31-17-generic  linux-source-2.6.31.tar.bz2
linux-headers-2.6.28-15-generic  linux-headers-2.6.31-19          modules
linux-headers-2.6.31-14-generic  linux-headers-2.6.31-19-generic  rt2570.tar.bz2
linux-headers-2.6.31-15          linux-headers-2.6.31-20
linux-headers-2.6.31-15-generic  [COLOR="Red"]linux-headers-2.6.31-20-generic[/COLOR]
# uname -r
[COLOR="Red"]2.6.31-20-generic[/COLOR]
If not, please do:```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by drspikes on 2010-04-07
> **chili555 said:**
> It makes perfectly for me, no errors and no warnings. Please do:```
ls /usr/src
uname -r
```Do you have linux-headers exactly matching your running kernel? Here is my example:If not, please do:```
sudo apt-get install linux-headers-`uname -r`
```
```

$ ls /usr/src
linux-headers-2.6.31-14          linux-headers-2.6.31-20-generic  linux-headers-lbm-2.6.31-21-generic
linux-headers-2.6.31-14-generic  linux-headers-2.6.31-21
linux-headers-2.6.31-20          linux-headers-2.6.31-21-generic
~$ sudo su
[sudo] password for chris: 
# uname -r
2.6.31-21-generic 
```

Sadly they match already, just for the hell of it I did the apt-get thing and then the make but got exactly the same message.

Thank you for your help but still feels so close yet so far!:(

---

### Post by chili555 on 2010-04-07
After you installed *build-essential* and did the updates above, please do:```
cd /directory/wherever/rtl8192etc.
sudo su
make clean 
make
```Does it error out at "*** No rule to make target `modules'. Stop." or elsewhere? Please copy and paste the last five lines before the error into your reply. Thanks.

---

### Post by drspikes on 2010-04-07
Just going to copy paste everything in the Terminal:
```

root@Sammy-lin:/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010# make clean
make[1]: Entering directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/HAL/rtl8192/rtl8192e'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Leaving directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/HAL/rtl8192/rtl8192e'
make[1]: Leaving directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/HAL/rtl8192'
make[1]: Entering directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/rtllib'
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
rm -rf Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010/rtllib'
root@Sammy-lin:/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010# make
make[1]: Entering directory `/lib/modules/2.6.31-21-generic/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.31-21-generic/build'
make: *** [all] Error 2
root@Sammy-lin:/media/Home/Chris/Downloads/rtl8192e_linux_2.6.0013.0127.2010#

```

C'est Tout!  Thank you for your patience.

---

### Post by chili555 on 2010-04-07
> make[1]: [COLOR="Blue"]Entering directory `/lib/modules/2.6.31-21-generic/build'[/COLOR]
Whoa! Did you make some changes to the Makefile? Here is the first few lines of my 'make':> make[1]: [COLOR="Red"]Entering directory `/usr/src/linux-headers-2.6.31-20-generic'[/COLOR]I am attaching a copy of my Makefile in case you need to revert to a known stock copy.

---

### Post by drspikes on 2010-04-07
I've compared your make file and it is identical.   Thank you for sending this on.

I wouldn't even think to change make file and am very new so generally just follow orders.

The first ever time I ran make, I got a similar error but not quite the same;

I don't have a log of it but from memory and it may be wrong it went along the lines of 

'directory not found /lib/modules/2.6.31-21-generic/build
the probably STOP'

So logically but probably very foolishly, I ran the command
#mkdir /lib/modules/2.6.31-21-generic/build

After this, issuing a make command always gives the same error report as seen above.

Still confused - this is still a very new system, am I getting to a point where it's best off just to reinstall ubuntu or maybe upgrade to to Ubuntu 10. beta?

---

### Post by chili555 on 2010-04-07
I think we can fix what's there now. Let's try to recreate what you did and undo it. Let's take a look at:```
ls /lib/modules/`uname -r`
ls /lib/modules/`uname -r`/build
```

---

### Post by drspikes on 2010-04-07
Thank you for your help. I'm at work until tomorrow now, so will get back to this tomorrow.   Just wanted to inform you why I'm not getting back to you imediately and I continue to be greatful for your patient help.

---

### Post by chili555 on 2010-04-07
I will be around. My suspicion is that, before you installed build-essential, it complained abot "no rule" etc., and you created a directory. I suspect that the directory may have over-written the correct files. My build directory looks like:> ls /lib/modules/`uname -r`/build
arch           firmware  Kbuild    modules.order   security  usr
block          fs        kernel    Module.symvers  sound
crypto         include   lib       net             source
Documentation  init      Makefile  samples         tools
drivers        ipc       mm        scripts         ubuntuWe shall see. This is repairable.

---

### Post by drspikes on 2010-04-08
Here is the output - I'm sure this isn't right!

```

# ls /lib/modules/'uname -r'
ls: cannot access /lib/modules/uname -r: No such file or directory

# ls /lib/modules/'uname -r' /build
ls: cannot access /lib/modules/uname -r: No such file or directory
ls: cannot access /build: No such file or directory


```

---

### Post by chili555 on 2010-04-08
It is not 'uname -r' with apostrophes, it's `uname -r` with backticks, on the same key with ~ on my US keyboard. Please try again.

`uname -r` is just a way the terminal understands of specifying 'whatever my currently running kernel is.'

---

### Post by chili555 on 2010-04-08
Let's cut right to the chase. Please reboot and at the very first appearance of the word GRUB, press Esc. The Grub menu will appear. Use the arrow keys to highlight the earlier kernel, 2.6.31-20. Boot into it.

(You are evidently running -21: Entering directory `/lib/modules/2.6.31-21-generic/build')

Open System > Administration > Synaptic and find linux-image-2.6.31-[COLOR="Red"]21[/COLOR]-generic and mark it for reinstallation. Also mark linux-headers-2.6.31-21-generic for reinstallation. Click Apply and let those two be recreated in all their new, unspoiled glory. After it's done, reboot into -21, which should happen automatically.

Run your process again:```
cd /directory/wherever/rtl8192etc.
sudo su
make clean 
make
make install
exit
```

---

### Post by drspikes on 2010-04-08
```
$ ls /lib/modules/`uname -r`
build   modules.alias      modules.dep          modules.inputmap   modules.order     modules.symbols      updates
initrd  modules.alias.bin  modules.dep.bin      modules.isapnpmap  modules.pcimap    modules.symbols.bin
kernel  modules.ccwmap     modules.ieee1394map  modules.ofmap      modules.seriomap  modules.usbmap
```

however...
```
$ls /lib/modules/`uname -r`/build
$

```

In other words - the directory is blank.

Looks like we are getting to the bottom of this.

---

### Post by chili555 on 2010-04-08
Indeed. If you do the reinstalls I recommended, I think all will be restored and the compile will go smoothly.

---

### Post by drspikes on 2010-04-08
Hi thanks for your help.  Shows the power to destroy of a new user and a little knowledge.

I did a clean install and works perfectly and I have wifi working.

---

### Post by chili555 on 2010-04-08
Glad it's working. Have fun and post back to the forum if you get stuck in the future. We'll be glad to help.

---


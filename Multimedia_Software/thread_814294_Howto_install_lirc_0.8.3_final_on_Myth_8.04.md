---
title: "Howto install lirc 0.8.3 final on Myth 8.04"
date: 2008-05-31
forum: Multimedia Software
---

### Post by Bubbel on 2008-05-31
Lirc does not start with my installation. I think because of an awkward remote control, the Soundgraph iMon PAD.
The kernel modules simply wouldn't start.

To get it working I tries to compile the lirc-module-sources, but to no avail. Then resorted to the original lirc site and downloaded the package. Here are the steps to get it working. They're in a terminal window


[LIST=1]
[*]Install Build essentials:```
sudo apt-get install build-essential linux-headers-`uname -r` autoconf
```Use back-tics with the uname, and put in your password.
[*]Download and extract the lirc 0.8.3```
wget -O- [http://prdownloads.sourceforge.net/lirc/lirc-0.8.3.tar.gz](http://prdownloads.sourceforge.net/lirc/lirc-0.8.3.tar.gz)|tar xz
```
[*]Go to the lirc folder:```
cd lirc-0.8.3
```
[*]Lookup the correct drivername, by looking under the --with-driver section of the following output (i.e. you can always replay the config/make/make install procedure if you have to do trial-and-error to find out the correct driver):```
./configure --help
```
[*]Create build package, replace ***<driver name> ***with the driver you found in step 4:```
./configure --with-moduledir=/lib/modules/`uname -r`/kernel/drivers/input/misc --prefix=/usr --with-x --with-driver=***<driver name>***
```
[*]Build the lot:```
make
```
[*]Install the package:```
sudo make install
```
[/LIST]
If you think you've screwed up, you can always redo the ./configure line again, and if you want to rebuild the whole lot (I don't think that it's in any case nessecary, but nevertheless), you can use make -B, instead of just make.

When testing this howto, I got problems compiling. I noticed that completely removing the lirc-0.8.3 folder and start over was the best option.

Now that I have LIRC running, I neet to configure it...anyone a clue?

:-? Bubbel

---

### Post by Trollslayer on 2008-06-01
What do you want to use it with?
Applications must be LIRC aware.

---

### Post by kenmiles on 2008-06-08
I get this when I try stage 1 -

/home/kenneth-->sudo apt-get install build-essentials linux-headers-`uname -r` autoconf
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essentials

Regards, Kenneth.

---

### Post by mastermindg on 2008-06-08
Hi Ken,

The correct package is build-essential

---

### Post by kenmiles on 2008-06-08
> **mastermindg said:**
> Hi Ken,

The correct package is build-essential

Thanks for getting back to me.
I have tried all ways to get this to work but I still have the same problem after reinstalling -

/home/kenneth/temp/lirc-0.8.3-->sudo /etc/init.d/lirc restart verbose
 * Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

I am seriously thinking of going for a wireless remote as there seems no proper answer to this judging by all the other posts I have read.
In Ubuntu 6.10 it worked perfectly but 8.04 will not.

Regards, Kenneth.

---

### Post by Bubbel on 2008-06-12
> **kenmiles said:**
> I get this when I try stage 1 -

/home/kenneth-->sudo apt-get install build-essentials linux-headers-`uname -r` autoconf
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essentials

Regards, Kenneth.
O, sorry, it is build essential, without the s, gonna correct it, thanx

---

### Post by Bubbel on 2008-06-12
> **Trollslayer said:**
> What do you want to use it with?
Applications must be LIRC aware.

Yes, I know. The problem is, in this configuration that the whole support (i.e. mythtv etc) is there, but the only thing lacking in my situation was the support for my specific remote control (a SoundGraph iMon PAD).

That's why I used the source package, since support was added to this release.

---

### Post by Bubbel on 2008-06-12
> **mastermindg said:**
> Hi Ken,

The correct package is build-essential

Thanx, it's fixed now in the original.

---

### Post by mastermindg on 2008-06-12
Ken,

Did you find your driver in the new release. If so, did you install with:

./configure --with-moduledir=/lib/modules/`uname -r`/kernel/drivers/input/misc --prefix=/usr --with-x --_with-driver=<driver name>_

???

---

### Post by kenmiles on 2008-06-12
> **mastermindg said:**
> Ken,

Did you find your driver in the new release. If so, did you install with:

./configure --with-moduledir=/lib/modules/`uname -r`/kernel/drivers/input/misc --prefix=/usr --with-x --_with-driver=<driver name>_

???

Yes I did all that. Two days ago there was a new lirc upgrade and that does not work either.
There are quite a lot of reports about this problem in hardy, this is the last thing that I have got to get working after my upgrade from 6.10.
Regards, Kenneth.

---

### Post by Bubbel on 2008-06-14
Ken,

Could it be that you need to install the package from the repository also?
In my situation (Mythbuntu) LIRC is already installed with the distro. I couldn't even uninstall it (Package required by mythbuntu-desktop).

Maybe by installing it thru apt-get or so, and then a make install on the source package again.

Greetings, The Bubbel :?

---


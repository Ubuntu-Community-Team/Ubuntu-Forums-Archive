---
title: "libgpod2 problem"
date: 2008-05-02
forum: Multimedia Software
---

### Post by ilSignorCarlo on 2008-05-02
Hi,
I'm using Ubuntu 8.04 Hardy Heron and I'd like to use my iPod classic 80 GiB with Amarok. 

I was reading a guide on Full Circle Magazine.

I get stucked on this step:

```
sudo apt-get build-dep libgpod2
```

Here is the output of the command:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for libgpod2


What can I do?
Thanks, bye

---

### Post by ilSignorCarlo on 2008-05-03
No ideas? :\

---

### Post by dentaku65 on 2008-05-04
What about libgpod3 instead of libgpod2?

---

### Post by ilSignorCarlo on 2008-05-04
> **dentaku65 said:**
> What about libgpod3 instead of libgpod2?

I tried.
It worked till the checkinstall. Here I get this error:

> 
...
...
...
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
chmod: changing permissions of `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/ilsignorcarlo/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/ilsignorcarlo/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/ilsignorcarlo/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/ilsignorcarlo/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ilsignorcarlo/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


The output is much longer, this is the last part and I can't understand it :\

---

### Post by dentaku65 on 2008-05-06
Afaik amarok + libgpod3 it works (at least my iPod video nano 4gb silver).

Why you don't try to install libgpod svn version?

Download needed sw:
```
sudo apt-get install build-essential svn
```

Create a dir in your home:
```
mkdir ~/libpodsvn
```

Go to this dir:
```
cd ~/libpodsvn
```

Grab svn code:
```
svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod
```

Go to trunk dir of libgpod:
```
cd gtkpod/libgpod/trunk/
```

Compile svn libgpod:
```
./autogen.sh
make
sudo make install

```

Now you have the last version of libgpod on your box.

---

### Post by andradx on 2008-05-06
Does it work on the sixth generation ipod classic?
I've just bought one recently and it's a real pain not being able to use it on Ubuntu.

I tried installing libgpod2 but also the checkinstall failed with the same output...
I suppose a bit more time and there'll be full support for these monopolistic devices.

Are there any other alternatives other than itunes?

---

### Post by dentaku65 on 2008-05-06
> **andradx said:**
> Does it work on the sixth generation ipod classic?
I've just bought one recently and it's a real pain not being able to use it on Ubuntu.

I tried installing libgpod2 but also the checkinstall failed with the same output...
I suppose a bit more time and there'll be full support for these monopolistic devices.

Are there any other alternatives other than itunes?

I supposed that you have already did the little hack for the new ipods... if not here the steps:

Plug and mount (usually automounting) the ipod to your box, then do:
```
sudo lsusb -v | grep -i Serial
```

The output should be something like:
```
iSerial 000A2700133125F5
```

Edit (or create) this file on your ipop:
```
nano /media/IPOD/iPod_Control/Device/SysInfo
```
* note: the /media/IPOD is the default mounting point of Ipod in Ubuntu (change with yours if different)

Add to SysInfo file the following line and save the file:
```
FirewireGuid: 0xffffffffffffffff
```
* change the ffffffffffffffff value with the value grabbed above with the lsusb command

Unmount the ipod.

Now you can install amarok (my favourite player :-) to use it with ipod:
```
sudo apt-get install amarok libgpod3
```

Plug the ipod again then open amarok and adding ipod as Devices

Instead of amarok you can use Exile or Rhythmbox as players (specific for Gnome env)

Hope this helps

---

### Post by andradx on 2008-05-07
Nobody mentioned that in the how to threads I've been reading. I did that, followed this guide [http://ubuntuforums.org/showthread.php?t=658523&page=8]("http://ubuntuforums.org/showthread.php?t=658523&page=8") and it's working. Allright:)

---

### Post by ilSignorCarlo on 2008-05-08
> **andradx said:**
> Nobody mentioned that in the how to threads I've been reading. I did that, followed this guide [http://ubuntuforums.org/showthread.php?t=658523&page=8]("http://ubuntuforums.org/showthread.php?t=658523&page=8") and it's working. Allright:)

I don't know how, or why, but my SysInfo file was ok. I followed this how to, to try to get it working with Amarok, but when I click on Autodetect Devices I get this messagei:

> No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.


What's this?

---

### Post by dentaku65 on 2008-05-08
I don't think that autodetection in Amarok works; try to configure it manually under Configure amarok -> Media devices -> Add device...
Choose Apple ipod media device and choose your mounting point (/media/IPOD)

---

### Post by ilSignorCarlo on 2008-05-08
> **dentaku65 said:**
> I don't think that autodetection in Amarok works; try to configure it manually under Configure amarok -> Media devices -> Add device...
Choose Apple ipod media device and choose your mounting point (/media/IPOD)

It doesn't work. I choose the right mounting point, but when back to the main amarok windows I choose "Devices" and click on the connect button, I get:

> Media Device: No mounted iPod found

But on top it says that the iPod is mounted.

---

### Post by andradx on 2008-05-08
I got that too. I noticed that the ipod wasn't mounted anymore, so I unplugged and plugged it back, ubuntu mounted it and then I could connect amarok to it, this is what I did when having the same error.

I'm using amarok and running gnome don't know if it's such a good option, amarok tends to grey out for quite a long time while reading ipod data, is gtkpod any better? I mean artwork is still an unresolved issue for me so for the while artwork support or not it's irrelevant.

---

### Post by ilSignorCarlo on 2008-05-08
> **andradx said:**
> I got that too. I noticed that the ipod wasn't mounted anymore, so I unplugged and plugged it back, ubuntu mounted it and then I could connect amarok to it, this is what I did when having the same error.

It doesn't seem to work for me :\

---

### Post by dentaku65 on 2008-05-09
Maybe you must use the amarok from Medibuntu repository.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by dentaku65 on 2008-05-09
> **andradx said:**
> I got that too. I noticed that the ipod wasn't mounted anymore, so I unplugged and plugged it back, ubuntu mounted it and then I could connect amarok to it, this is what I did when having the same error.

I'm using amarok and running gnome don't know if it's such a good option, amarok tends to grey out for quite a long time while reading ipod data, is gtkpod any better? I mean artwork is still an unresolved issue for me so for the while artwork support or not it's irrelevant.

I think Exile, Rhythmbox or Banshee are the players for Gnome

---

### Post by ilSignorCarlo on 2008-05-09
> **dentaku65 said:**
> Maybe you must use the amarok from Medibuntu repository.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

I am already using that Amarok. So that's not the problem.

---

### Post by dentaku65 on 2008-05-09
> **ilSignorCarlo said:**
> I am already using that Amarok. So that's not the problem.

But with other players? With gtkpod? When the Ipod is mounted are you able to use it?

---

### Post by andradx on 2008-05-11
I've unninstalled amarok and I wanted to install it back but with aptitude it will install libgpod2 which I don't want as libgpod3 is installed, so no use for libgpod2. If I unninstall the libgpod2 after installation will 6G ipod classic support continue to be available?

---

### Post by dentaku65 on 2008-05-13
> **andradx said:**
> I've unninstalled amarok and I wanted to install it back but with aptitude it will install libgpod2 which I don't want as libgpod3 is installed, so no use for libgpod2. If I unninstall the libgpod2 after installation will 6G ipod classic support continue to be available?

Yes, should be.
Libgpod2 is not available in the Hardy repos, I think that the one that you have is an older package

---

### Post by andradx on 2008-05-13
Thing is I'm running Gutsy Gibbon, upgrading to Hardy Heron will cost some time on reinstalling virtual machines on which I depend heavily this semester. Maybe during summertime I'll upgrade, anyway I'm sticking with rythmbox at least artwork feature is covered.

---

### Post by ilSignorCarlo on 2008-05-17
> **dentaku65 said:**
> But with other players? With gtkpod? When the Ipod is mounted are you able to use it?

I can use it with Rythmbox. Gtkpod doesn't seem to work fine. But I'd prefer to have Amarok working.

---


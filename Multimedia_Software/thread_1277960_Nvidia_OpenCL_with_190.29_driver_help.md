---
title: "Nvidia OpenCL with 190.29 driver help"
date: 2009-09-28
forum: Multimedia Software
---

### Post by sethhikari on 2009-09-28
Today Nvidia released openCL driver in their 190.29 packages. I am using Karmic but could not get it to work. Anyone else?

---

### Post by lwhitmore on 2009-10-24
I managed to break my computer trying to get this working ;)

Did you have any luck in the end?

---

### Post by beastrace91 on 2009-10-24
Are you having issues installing the driver itself or something else?

Also how did you "break" your system in the process? Hopefully we can remedy that as well :)

~Jeff

---

### Post by richiekAL on 2009-11-16
If their issue is anything like mine, I can install the drivers ok (once I've disabled Ubuntu hardware drivers for nvidia), I can compile the SDK examples, but the issue is that none of them work. Everything is failing on the call to clGetDeviceIDs - which always returns -1.
I'm running Karmic with everything compiled by gcc 4.4.

---

### Post by nss0000 on 2009-11-17
Hummm:

I think your driver is out-of-date. KK_9.1 Synaptic brings_down the NV-190.42 driver and NV-GUI on my system.

---

### Post by richiekAL on 2009-11-19
Going to [http://developer.nvidia.com/object/opencl-download.html#Linux ]("http://developer.nvidia.com/object/opencl-download.html#Linux")shows v190.29 as the latest Linux driver set that includes OpenCL drivers. Does the graphics driver v190.42 include the OpenCL drivers too? (I haven't checked it)

---

### Post by randomsearch on 2010-02-04
Hi

I have a similar problem - everything installed but various error messages from the examples.

The bandwidth test works.

Blackscholes gives this error:

---

Loading OpenCL program from file...

 !!! Error # 0 at line 138 , in file Source/oclBlackScholes.cpp !!!

Exiting...

---

Boxfilter gives:

--

bin/linux/release/oclBoxFilter Starting, using BoxFilter.cl...


 !!! Error # 0 at line 129 , in file oclBoxFilter.cpp !!!


Starting Cleanup...

TEST FAILED !!!...

--

Any ideas?

Thanks

RS

---

### Post by norman_h on 2010-02-17
The drivers and OpenCL work fine on 64bit karmic 9.10 with a clean install.  You just need to uninstall the latest drivers and use the 190.29 drivers.  

Get the drivers and SDK from here:
[http://developer.nvidia.com/object/opencl-download.html](http://developer.nvidia.com/object/opencl-download.html)

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR="Red"]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR="Red"]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR="Red"]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR="Red"]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```

**[COLOR="Red"]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```

**[COLOR="Red"]5[/COLOR])** Run the installer:  ```
sudo sh ./nvdrivers_2.3_linux_64_190.29.run
```

**[COLOR="Red"]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR="Red"]7[/COLOR])** Then restart your computer   ```
sudo reboot
```

**[COLOR="Red"]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: ```
sudo sh ./nvdrivers_2.3_linux_64_190.29.run --uninstall
```
or
```
sudo nvidia-uninstall
```

Good luck ;)

Thanks for the help in [http://ubuntuforums.org/newreply.php?do=newreply&p=6235436](http://ubuntuforums.org/newreply.php?do=newreply&p=6235436)

---


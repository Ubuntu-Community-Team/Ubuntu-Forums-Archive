---
title: "Belkin Wireless N Basic USB Adapter Trouble and RLT8192SU chip"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by xaxtree on 2010-05-25
Well this thread is started so that chili555 will help me through this publicly.  

I have a Belkin Wireless N Basic USB Adapter using on Ubuntu 10.04, and it is not working, all I know is it uses the RLT8192SU chipset which leads me to believe this could work. Currently wired to the internet.

EDIT:

lsusb

logik@nixmachine:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1532:0102 Razer USA, Ltd Tarantula Keyboard
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 050d:945a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
logik@nixmachine:~$ 

dmesg | grep 819 doesn't output anything other then the amount of bytes from a download

---

### Post by chili555 on 2010-05-25
I can find nothing on this usb.id. Is it a new device? If it has an RTL8192SU chipset, here is a clue from my computer:> /lib/modules/2.6.32-22-generic/kernel/drivers/staging/[COLOR="Red"]rtl8192su[/COLOR]/r8192s_usb.koHowever, r8192s_usb doesn't claim the device. It may not because the device is new and hasn't been added to the module yet.

We could:

* Try a few magic tricks to try to get the current driver to grab the device;
* Download the most current driver from Realtek, compile it and install it;
* Or, try the Windows drivers with ndiswrapper.

I think the strategy with the greatest chance of success in the shortest time is ndiswrapper. Do you have the install CD that came with the device?

What is your choice? I will be glad to help with any of the above.

---

### Post by xaxtree on 2010-05-25
> **chili555 said:**
> I can find nothing on this usb.id. Is it a new device? If it has an RTL8192SU chipset, here is a clue from my computer:However, r8192s_usb doesn't claim the device. It may not because the device is new and hasn't been added to the module yet.

We could:

* Try a few magic tricks to try to get the current driver to grab the device;
* Download the most current driver from Realtek, compile it and install it;
* Or, try the Windows drivers with ndiswrapper.

I think the strategy with the greatest chance of success in the shortest time is ndiswrapper. Do you have the install CD that came with the device?

What is your choice? I will be glad to help with any of the above.

Well I will go with whatever you recommend is best and you believe would have the best chance of being successful, and I'm not 100% sure where I read about it's chipset, but I not sure how new this device is.  If you explore the drivers CD I saw the .inf file net8192su.inf and a rlt8192su.sys, and I just extract all the .inf and .sys files from the cd for the drivers from the win2kxp folder.

---

### Post by chili555 on 2010-05-25
> If you explore the drivers CD I saw the .inf file net8192su.inf and a rlt8192su.sysExcellent. Please right-click your desktop and create a folder, I suggest calling it 8192. Now open System > Administration > Windows Wireless drivers and click it. Click Install New Driver. Navigate to Desktop/8192 and select net8192su.inf. You should be all set!

Post back with any questions, errors, problems, snags or compliments.

---

### Post by xaxtree on 2010-05-25
> **chili555 said:**
> Excellent. Please right-click your desktop and create a folder, I suggest calling it 8192. Now open System > Administration > Windows Wireless drivers and click it. Click Install New Driver. Navigate to Desktop/8192 and select net8192su.inf. You should be all set!

Post back with any questions, errors, problems, snags or compliments.

Hm, no windows appear when I click on Windows Wireless drivers, isn't that ndisgkt? or whatever the name for the ndiswrapper GUI is?  It prompts me to enter my password but thats about it.

---

### Post by chili555 on 2010-05-25
> It prompts me to enter my password but thats about it.Start it in the terminal and let's see what's going wrong:```
sudo ndisgtk
```Note any errors or warnings.

---

### Post by xaxtree on 2010-05-25
logik@nixmachine:~$ sudo ndisgtk
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 404, in <module>
    NdisGTK()
  File "/usr/sbin/ndisgtk", line 122, in __init__
    self.setup_driver_list()
  File "/usr/sbin/ndisgtk", line 150, in setup_driver_list
    self.get_driver_list()
  File "/usr/sbin/ndisgtk", line 162, in get_driver_list
    output,retcode = getoutput("ndiswrapper", "-l")
  File "/usr/sbin/ndisgtk", line 34, in getoutput
    myproc = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
logik@nixmachine:~$ 



I believe maybe it's because I don't have ndiswrapper itself installed?

---

### Post by chili555 on 2010-05-25
It could be. If you have an ethernet connection, you can shortcut the process:```
sudo apt-get install --reinstall ndis*
```That should reinstall ndiswrapper-1.9, ndiswrapper-common and ndisgtk.

---

### Post by xaxtree on 2010-05-25
I did that and it shows a lot of output and ends with this... 
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  abrowser-branding: Conflicts: firefox-3.5-branding
                     Conflicts: firefox-3.6-branding
                     Conflicts: firefox-branding
  firefox-branding: Conflicts: abrowser-3.5-branding
                    Conflicts: abrowser-3.6-branding
                    Conflicts: abrowser-branding
E: Broken packages
logik@nixmachine:~$ 

```

also it didn't change sudo ndisgtk

```

logik@nixmachine:~$ sudo ndisgtk
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 404, in <module>
    NdisGTK()
  File "/usr/sbin/ndisgtk", line 122, in __init__
    self.setup_driver_list()
  File "/usr/sbin/ndisgtk", line 150, in setup_driver_list
    self.get_driver_list()
  File "/usr/sbin/ndisgtk", line 162, in get_driver_list
    output,retcode = getoutput("ndiswrapper", "-l")
  File "/usr/sbin/ndisgtk", line 34, in getoutput
    myproc = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
logik@nixmachine:~$ 

```

---

### Post by xaxtree on 2010-05-25
I just fixed it myself, went into synaptic package manager, searched ndis, selected all ndiswrapper packages for reinstall and everything worked fine, now to test ndisgtk with the .inf file. Wish me luck!

---

### Post by chili555 on 2010-05-25
> The following packages have unmet dependencies:
  abrowser-branding: Conflicts: firefox-3.5-branding
                     Conflicts: firefox-3.6-branding
                     Conflicts: firefox-branding
  firefox-branding: Conflicts: abrowser-3.5-branding
                    Conflicts: abrowser-3.6-branding
                    Conflicts: abrowser-branding
E: Broken packages
You have been a busy little Ubuntuan, haven't you? Let's try:```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get install --reinstall ndis*
```

---

### Post by chili555 on 2010-05-25
> **xaxtree said:**
> I just fixed it myself, went into synaptic package manager, searched ndis, selected all ndiswrapper packages for reinstall and everything worked fine, now to test ndisgtk with the .inf file. Wish me luck!OK, good luck.

---

### Post by xaxtree on 2010-05-25
It's now giving me a warning/error saying 


Module could not be loaded. Error was:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. 
FATAL: Could not open 'lib/modules/2.6.32-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

---

### Post by Anonymous Citizen on 2010-05-25
I have that same driver (rtl8192su.sys and net8192su.inf), probably same chipset. I might jump in this thread and try along with xaxtree as I have tried but couldn't get it to work. I pretty much gave up but I really want to use WiFi. I'll do anything to try to get this to work, compile from source or whatever. Right now I'm encoding a bunch of video though so I'll get into this later.

Although I'm on 64-bit Karmic, AMD processor. I kept getting "bad magic" and a message about the drivers not being 64-bit (output of dmesg command). These were from the manufacturer's CD and not from the chipset manufacturer website. 

My wireless adapter is Belkin F7D2101 Surf & Share.

---

### Post by Anonymous Citizen on 2010-05-25
I think I suggested to him to remove ndiswrapper because he had the same problem I did with ubuntu not booting. I just followed these instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Install%20kernel%20headers") after reboot to try everything again.

---

### Post by xaxtree on 2010-05-25
Well I'm  back had some errands, but yesh anonymous those instructions did help thank you.  Hopefully you'll get something out of this thread too.  But right now I still have that error from ndisgtk that I posted above

---

### Post by chili555 on 2010-05-25
> FATAL: Could not open 'lib/modules/2.6.32-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directoryThis is an error; the others are warnings that shouldn't keep us from getting the driver installed. Please try:```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get install --reinstall ndis*
```

---

### Post by xaxtree on 2010-05-25
> **chili555 said:**
> This is an error; the others are warnings that shouldn't keep us from getting the driver installed. Please try:```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get install --reinstall ndis*
```

Did that, same broken packages error again.

---

### Post by chili555 on 2010-05-25
> The following packages have unmet dependencies:
abrowser-branding: Conflicts: firefox-3.5-branding
Conflicts: firefox-3.6-branding
Conflicts: firefox-branding
firefox-branding: Conflicts: abrowser-3.5-branding
Conflicts: abrowser-3.6-branding
Conflicts: abrowser-branding
E: Broken packages Any ideas how this could have happened? What experimental, tweak-it-till-it-breaks kinds of things have you been trying? I am a believer in experimentation; it sometimes takes a few steps to recover from a failed experiment.

You might try to remove everything mentioned:> abrowser-branding
firefox-3.6-branding
firefox-branding
abrowser-3.5-branding
abrowser-3.6-branding
Then try these commands again:```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get install --reinstall ndis*
```Proceed with care if you are asked to remove other packages. We can check and reinstall firefox later after we fix all this.

---

### Post by Joe Awsome on 2010-05-25
No problems with ndis, but was just wondering if anybody has had trouble connecting to WPA protected networks and what the status is. Thought I would ask seeing as how it's a live thread.I too am running the RLT8192SU chipset in my wireless n usb adapter. Mine is a Zenet ZEW2546 brand one though, I do have up to date drivers and can access unsecured networks.

---

### Post by Armadillo Kilr on 2010-06-24
is there any update on this matter? i too am attempting to install the belkin surf and share with little promise. i tried messing with gedit and all i got to was recognition of the USB adapter. i put the network key in and it never connects. the gedit codes were taken from this thread: 

[http://ubuntuforums.org/showthread.php?t=1509403&highlight=belkin](http://ubuntuforums.org/showthread.php?t=1509403&highlight=belkin) 

from post #2 and i changed the usb port to reflect where mine says "Belkin Component". 

i also tried using ndisgtk to install the .inf file i obtained from the windows driver and all it tells me is that net8192su is an "invalid driver!". am i putting the wrong .inf?

***btw using 10.4

---

### Post by eteq on 2010-08-24
I managed to get this adapter working under Ubuntu (lucid 64) with the Belkin surf and share (F7D2101).  Pretty straightforward actually... I got most of this from [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815) , although it required a some slight changes. 

Run this command:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```

And add this line to the file (which may be empty) and save:

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Then run this command:
```
sudo gedit /etc/modprobe.d/network_drivers.conf 
```

And add this file (and save)
```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

and copy it to the directory ```
/lib/firmware/RTL8192SU/ 
```

To summarize, the first two commands tell linux to load the correct driver when that particular USB device is plugged in (which I figured out with the lsusb command), and the firmware is used to load the information the wireless chip needs to run.

---

### Post by lukeymunk on 2010-11-19
plz reply 

I got a belkin wireless adapter while i was still using windows and it only came with a installation disc that  worked with windows so how do i install it on to ubuntu os

thanks                                  ):P

---


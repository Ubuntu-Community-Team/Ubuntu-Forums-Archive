---
title: "RaLink RT2500 Wireless Lan Card + UBUNTU 10.10"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by Jim Hornet on 2011-02-02
Hello

I am having probs connecting wireless for the first time with my Belkin router to my RaLink RT2500 Wireless Lan Card with UBUNTU 10.10.

My router is detected but when I connect - It tries to connect, unsuccessfully -I get a message "Disconnected you are now OFFLINE". 

I tried to work out a solution and followed the sticky I went to:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

to get linux drivers for the rt2500

and found the following driver:
[http://sourceforge.net/projects/rt2400/](http://sourceforge.net/projects/rt2400/)

I downloaded and now I am lost :

Instructions are:
> 
1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install

INVOCATION
====================
Load the driver:

    $ modprobe rt73 [ifname=<name>] [debug=<mask>] [firmName=<file>]

    <name> is the name of the device and defaults to "wlan%d". If more
    than one adapter is installed, successive devices will be named
    wlan0, wlan1, etc. If you wish to use a different scheme - say
    eth*, and there are already wired ethernet devices named eth0 and
    eth1, then specifying <name> as "eth%d" gives the adapter the name
    "eth2".

    <mask> is a decimal or hex number. See TESTING file. Ignored if
    driver compiled without debug support.

    <file> is the name of a firmware file and defaults to "rt73.bin"
    if omitted. Only the basename - not the full path - may be
    specified.

Start it up:

    $ ifup wlan0        # If using Debian - or
    $ ifconfig wlan0 up
    $ iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section. Otherwise,
check out the following install notes...

Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

    If you're looking for a GUI config tool we provide RutilT on our
    download page
    [[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]).

MANUAL CONFIG:

    1. Set the interface mode and bring it up
          # iwconfig wlan0 mode managed
          # ifconfig wlan0 up

    2. Set your target network / Access Point
       If you just want to join a wireless network, set its ESSID:
          # iwconfig wlan0 essid <ESSID>
       If you want to associate with a specific AP, set its MAC
       address:
          # iwconfig wlan0 ap <BSSID>

    3. Set encryption if needed

       a) WEP (802.11b)
          Choose the authentication mode (open/restricted):
             # iwconfig wlan0 key open
          Or:
             # iwconfig wlan0 key restricted
          Set the encryption key:
             # iwconfig wlan0 key <KEY>

       b) WPA (802.11g)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPAPSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=TKIP

       c) WPA2 (802.11i)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPA2PSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=AES

    4. Check that you're associated with an AP
          # iwconfig wlan0

If everything's ok, you can now configure the wlan0 interface
statically or dynamically (DHCP). If you need more wireless config
details and examples (Adhoc mode e.g.), see iwpriv_usage.txt (included
in driver sources). Otherwise, read the following config notes...I tried unpacking it my downloads folder and entered first command:

> : ~$ tar - xvzf rt73-cvs-daily.tar.gz
tar: You must specify one of the `-Acdtrux' or `--test-label'  options
Try `tar --help' or `tar --usage' for more information
:~$ cd ./rt73-cvs-YYYYMMDDHH/Module
bash: cd: ./rt73-cvs-YYYYMMDDHH/Module: No such file or directory
:~$ 
New to Linux and very lost any hints/tips - Am I at least heading in the right direction?

Need help please

---

### Post by Jim Hornet on 2011-02-03
BUMP

sorry guys just need some help to get me started 

when the instructions say:

> 1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install


does that mean I unpack the module with the command: $ tar -xvzf rt73-cvs-daily.tar.gz?

I saved the file I dloaded in my documents folder and unpacked it with the unpacker.

Can someone please point me in the right direction- at least with this first bit - 

I dont know much about commands etc am I doing something wrong

Thanks in advance

---

### Post by Jim Hornet on 2011-02-05
Still havent worked out how to can some please point me in right direction eg if I am doing something wrong in the commands script or I havent unpacked properly - sorry guys this isn't really my area of expertise. Thanks

---

### Post by boriswart on 2012-03-02
> **Jim Hornet said:**
> BUMP

sorry guys just need some help to get me started 

when the instructions say:



does that mean I unpack the module with the command: $ tar -xvzf rt73-cvs-daily.tar.gz?

I saved the file I dloaded in my documents folder and unpacked it with the unpacker.

Can someone please point me in the right direction- at least with this first bit - 

I dont know much about commands etc am I doing something wrong

Thanks in advance


I am a noob, but pretty good w/ linux.  I don't see anything wrong with the untar followed by the cd (change directory)  followed by the make to build the executable. where are you having a problem?  which command?

---

### Post by boriswart on 2012-03-03
The #make indicates that you need to be root or super-user to do the make instal so before the last command you need to do:

sudo su

when you are done be sure to get out of super-user.

exit

---


---
title: "Intel 5150 WiMAX Fail on a Samsung NC10"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by slklim on 2010-01-17
2.6.31-14-generic Ubuntu Netbook Remix 9.10 on a Samsung NC10 netbook. The netbook from Clear came with an Intel 5150 WiFi/WiMAX card preinstalled.

Everything works great out of the box, except for WiMAX. The Network Manager displays all of the WiFi networks in range, but under Wired Network (Intel(R) Intel (R) WiMAX Link 5150) it just says Auto wmx0. When I click on this, it looks like it's trying to connect, but fails with a popup window of Wired Network Disconnected.

WiMAX works great on this machine in the preinstalled Windows XP and the Moblin Live environment that I tested out. In both of those cases, instead of saying anything about Auto wmx0, they say Clear, which I can click on and connect to without any fuss. Interestingly, they both also never show any WiFi access points available, and Moblin won't even let me enable WiFi when WiMAX is enabled. I'm guessing the Intel 5150 card is an either/or situation, not allowing me to use both functionalities at the same time.

I'm in Chicago, where Clear has rolled out a huge WiMAX infrastructure, so there should be plenty of WiMAX signal reaching my machine. Sitting right here, in Windows, I have fine WiMAX connectivity.

So, how do I connect to Clear in Ubuntu?

dmesg:
[   12.119309] i2400m_usb 1-3:1.0: firmware: requesting i2400m-fw-usb-1.4.sbcf
[   12.171952] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   12.171962] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   12.172094] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.172108] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.172168] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5150AGN REV=0x44
[   12.242820] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.242910]   alloc irq_desc for 27 on node -1
[   12.242918]   alloc kstat_irqs on node -1
[   12.242952] iwlagn 0000:02:00.0: irq 27 for MSI/MSI-X
[   12.266537] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.564463] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5150-2.ucode
[   13.630356] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.2
[   13.797066] Registered led device: iwl-phy0::radio
[   13.797140] Registered led device: iwl-phy0::assoc
[   13.797201] Registered led device: iwl-phy0::RX
[   13.797261] Registered led device: iwl-phy0::TX
[   13.814009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.836683] sky2 eth0: enabling interface
[   13.837426] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.843179] i2400m_usb 1-3:1.0: Device is still initializing
[   13.867304] i2400m_usb 1-3:1.0: Device is still initializing
[   14.417408] i2400m_usb 1-3:1.0: firmware interface version 9.2.0
[   14.425337] i2400m_usb 1-3:1.0: WiMAX interface wmx0 (...) ready
[   14.430852] usbcore: registered new interface driver i2400m_usb
[   16.259616] ppdev: user-space parallel port driver
[   17.248562] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0

wlan0 then auto-authenticates on an access point in range. And when I try clicking on Auto wmx0 again, I get this:
[ 4496.493942] ADDRCONF(NETDEV_UP): wmx0: link is not ready

lsmod | grep -e iwl -e i2400:
iwlagn                109052  0 
iwlcore               112508  1 iwlagn
i2400m_usb             27612  0 
i2400m                 83656  1 i2400m_usb
led_class               4096  1 iwlcore
mac80211              181236  2 iwlagn,iwlcore
wimax                  26112  2 i2400m_usb,i2400m
cfg80211               93052  3 iwlagn,iwlcore,mac80211

lspci:
02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5050 Series

Google hasn't been much help on this particular problem. And most of the how-tos that I've been reading mention /etc/init.d/wimax and wimaxcu, both of which aren't on my system. Ideas?

ifconfig wmx0:
wmx0      Link encap:Ethernet  HWaddr ...
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:5 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig wmx0:
wmx0      no wireless extensions.

---

### Post by slklim on 2010-01-19
So, it appears that Ubuntu doesn't yet support Intel WiMAX cards. However, if you wish to depart from the Ubuntu idealism for a moment......

Solution:

Download, untar, configure, compile, and install the latest versions of WiMAX Network Service and Intel WiMAX Binary Supplicant from here:
[http://www.linuxwimax.org/Download](http://www.linuxwimax.org/Download)

Notes:

I had to apt-get install libnl-dev for the compile. There might be other required libraries that I just happened to have on my system as well.

--with-i2400m=/usr/src/linux-headers-2.6.31-17 or whatever your kernel release is.

By default, all of the wimax binaries get installed at /usr/local/ instead of at /. I had to play around with it a bit to get the binaries where I wanted them, but I think DESTDIR=/ is what did the trick. See the WiMAX Network Service README for more info.

Finally, just play around with wimaxcu (ron, scan, connect network) to get connected.

Enjoy!

---

### Post by jclb111181 on 2010-10-03
I have the 5150 card in Chicago too.  Great connection in Windows but nothing in Ubuntu.  Could you please detail what steps you took to get it to work?  Im just a noob:(

---

### Post by slklim on 2010-10-03
Sure. I took notes while I was doing it myself. This whole thing was a little while ago, though, so I'm not 100% sure this is wholly correct. We'll see :-)

Make a fresh directory in /home/yourUserName/ to use as a workspace. Put all of your files into there. Every line starting with an "$" is a command. Every command starting with "sudo" is meant to be run either as root or with sudo.

If you can connect your Linux box to the internet through either WiFi or Ethernet, use that connection to download the two tarballs (files that end in .tar.bz2) and to apt-get libnl-dev. Otherwise, you'll have to boot into Windows to download the two tarballs AND the Debian package (file that ends in .deb), copy the files over to Linux, and install libnl-dev manually.

First. you'll need libnl-dev_1.1-5build1_i386.deb for compiling. if you're connected to the internet, you can use this command:
$ sudo apt-get install libnl-dev

Otherwise, you'll have to download the deb package using Windows from [http://packages.ubuntu.com/es/lucid/i386/libnl-dev/download](http://packages.ubuntu.com/es/lucid/i386/libnl-dev/download), copy it to your folder in Linux, and install it manually with this command:
$ sudo dpkg -i libnl-dev_1.1-5build1_i386.deb

Now, download Intel-WiMAX-Binary-Supplicant-1.4.0.tar.bz2 and WiMAX-Network-Service-1.4.0.tar.bz2 from [http://www.linuxwimax.org/Download](http://www.linuxwimax.org/Download)

Note that those tarballs are a little old, so they're located under the section 1.4.0 instead of 1.5. In theory, if you wanted the latest and greatest code, you could download and play around with the 1.5 files. But this HowTo is written only for the 1.4.0 files. You're kinda on your own if you want the new stuff.

Put your two tarballs into your workspace folder. Open a command prompt and cd into that folder. Run the following commands:
$ tar -xjf Intel-WiMAX-Binary-Supplicant-1.4.0.tar.bz2
$ tar -xjf WiMAX-Network-Service-1.4.0.tar.bz2
$ cd Intel-WiMAX-Binary-Supplicant-1.4.0

Alright, now open install_supplicant.sh in a text editor and remove "local/" from line 42. Then run this:
$ sudo ./install_supplicant.sh install
$ cd ../WiMAX-Network-Service-1.4.0

Okay, so now you're going to need to know where the header files for your kernel are located. On my system, they're at /usr/src/linux-headers-2.6.32-21-generic. Yours are probably somewhere similar. Try replacing "2.6.32-21-generic" with the text that you get when you run this:
$ uname -r

Then do this. It take a while to compile:
$ ./configure --with-i2400m=/usr/src/linux-headers-2.6.32-21-generic --sysconfdir=/etc --localstatedir=/var --mandir=/usr/share/man --prefix=/usr
$ make all
$ sudo make install
$ sudo ldconfig
$ sudo rfkill unblock wimax

Hey, if all the above went well, you should be able to start WiMAX with this:
$ sudo /etc/init.d/wimax start

And then you connect to Clear Network with this:
$ sudo wimaxcu connect network 2

Does it work? You'll have to start WiMAX and connect to Clear with those two commands every time you reboot your machine. If you want to get all fancy and have your computer automatically connect, we can worry about that later. Let's focus on the basics for now ;-)

Lemme know if you have any troubles. Good luck!

---

### Post by jclb111181 on 2010-10-04
Ok.  Thanks for the quick reply.  I rushed home from work so I could try this out.  It was all good until the Make All command.  Then this...

john@ubuntu:~/new/WiMAX-Network-Service-1.4.0$ make all
make  all-recursive
make[1]: Entering directory `/home/john/new/WiMAX-Network-Service-1.4.0'
Making all in wimax-tools
make[2]: Entering directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools'
Making all in include
make[3]: Entering directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/include'
Making all in lib
make[3]: Entering directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib'
make  all-am
make[4]: Entering directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib'
gcc -DHAVE_CONFIG_H -I. -I../include -I../include  -I/usr/src/linux-headers-2.6.32-25-generic/include    -g -Wall -O2 -MT op-open.o -MD -MP -MF .deps/op-open.Tpo -c -o op-open.o op-open.c
op-open.c:223: error: conflicting types for ‘wimaxll_recv’
../include/wimaxll.h:312: note: previous declaration of ‘wimaxll_recv’ was here
op-open.c: In function ‘wimaxll_recv’:
op-open.c:254: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘ssize_t’
make[4]: *** [op-open.o] Error 1
make[4]: Leaving directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/new/WiMAX-Network-Service-1.4.0'
make: *** [all] Error 2

the "new" directory is my working directory which I created for this.  I replaced the header version per the instructions.  Do you know why I would get these errors?  I was so close, I could almost taste it.  I eagerly await any help/guidance/directions/help you can provide.  

Thanks again!

---

### Post by slklim on 2010-10-04
Umm...I'm not sure. I never had that issue while compiling. It looks like your version of GCC makes a distinction between int and ssize_t, while mine (and also presumably the version at Intel) does not. Post what version of GCC you have, found with this:
$ gcc --version

We'll see if there's any difference between your version and mine. It's a start, anyway....

Also, try this in the meantime to see if you can compile that file by itself:
$ cd /home/john/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib
$ gcc -DHAVE_CONFIG_H -I. -I../include -I../include   -I/usr/src/linux-headers-2.6.32-25-generic/include    -g -Wall -O2 -MT  op-open.o -MD -MP -MF .deps/op-open.Tpo -c -o op-open.o op-open.c

Good luck!

---

### Post by jclb111181 on 2010-10-06
I am running the following version: gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3


The following are the results of trying to compile just the one file by itself.  

john@ubuntu:~/new/WiMAX-Network-Service-1.4.0/wimax-tools/lib$ gcc -DHAVE_CONFIG_H -I. -I../include -I../include -I/usr/src/linux-headers-2.6.32-25-generic/include -g -Wall -O2 -MT op-open.o -MD -MP -MF .deps/op-open.Tpo -c -o op-open.o op-open.c
op-open.c:223: error: conflicting types for ‘wimaxll_recv’
../include/wimaxll.h:312: note: previous declaration of ‘wimaxll_recv’ was here
op-open.c: In function ‘wimaxll_recv’:
op-open.c:254: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘ssize_t’


Which version or gcc were you using?  I know it was a while ago, but maybe i could downgrade the gcc that I am using, then try to compile again.  

THanks for your help.

---

### Post by slklim on 2010-10-12
Hey,

Sorry for the late reply. I saw your post last week, realized that I still couldn't help you much, and kinda forgot about it till just now.... Turns out I'm using the same version of gcc as you. So, well, uhh....

I have no idea what the problem could be...................

Please let me know if you get it worked out. I'm really curious now!

---

### Post by jclb111181 on 2010-10-14
OK.  Started over with a fresh install of 10.10.  Updated everything to the max.  

I got all the way to this command:  sudo wimaxcu connect network 2

and I get this:

john@john:~/new/WiMAX-Network-Service-1.4.0$ sudo wimaxcu connect network 2
ERROR: Attempt to connect not successfull - SW Radio is OFF.


This may be a dumb question, but no dumber than any of my other questions.  How do I turn on the radio.  I currently have my wifi connected.  Should I disconnect? 

I thank you once again and eagerly await your suggestions.

---

### Post by slklim on 2010-10-14
Sweet! You're so close!

Are you sure you ran this command first:
$  sudo rfkill unblock wimax

That *should* enable the SW radio,  which is what your machine is complaining about. Give it another run,  perhaps?

After that, try the wimaxcu command again. If it still  doesn't work, try this:
$ sudo rfkill list

One of the sections  should look like this:
[blah blah blah]: WiMAX
        Soft  blocked: no
        Hard blocked: no

If either soft blocked or  hard blocked is set to yes, then that rfkill unblock command isn't  working for you, in which case you should check its man page for the  correct command:
$ man rfkill

If both soft and hard blocked  are set to no, then something else weird is going on, and we'll need to  diagnose it separately.

As far as I can tell, the Intel 5150 card  can only do either WiFi or WiMAX at any given time, not both  simultaneously. I'd be very happy to find out otherwise, but that's been  my impression so far....

Try disconnecting WiFi before trying to  connect through WiMAX. If that *still* doesn't work, try disabling WiFi  completely and try again. Reenabling WiFi is easy, so don't worry too  much about that.

So, yeah, you're close! Stuff seems to have  compiled and installed properly. Yay!

It's too bad we still don't  know what was up with your previous install. I'm glad you got around it  with a clean install, and I'm also glad that a fresh install works as  it should. But damn, I really am curious about what that gcc compile  problem was all about............

Best of luck!

---

### Post by jclb111181 on 2010-10-16
Here are the results of the rfkill list command:

0: i2400m-usb:1-2:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

How would I go about turning off my wifi altogether? I also tried wimaxcu connect network 0, but only got ERROR: Make sure WiMAX Network Service is running.  

Since I rebooted i cannot replicate the sw radio error.  all I get now is the wimax network service error.  

There is no manual for rfkill, at least that was loaded into my machine.  

Any suggestions?

---

### Post by jclb111181 on 2010-10-16
ignore that last post.  

I have had some more time to mess with it.  Do you know how to fix the last warning that it gave me in the list below?

john@john:~$ sudo rfkill list
0: i2400m-usb:1-2:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
john@john:~$ sudo rfkill block wifi
john@john:~$ sudo rfkill list
0: i2400m-usb:1-2:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
john@john:~$ sudo rfkill unblock wimax
john@john:~$ sudo rfkill list
0: i2400m-usb:1-2:1.0: WiMAX
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
john@john:~$ sudo wimaxcu ron
HW and SW Radios are ON.
john@john:~$ sudo wimaxcu connect network 0
WARNING: Network ID did not match with the known list.

Is there some sort of config file that I should edit to add network specifics for the Clear network?

---

### Post by jclb111181 on 2010-10-16
Got it!!  Thanks for all your help!


john@john:~$ sudo rfkill block wifi
[sudo] password for john: 
john@john:~$ sudo rfkill unblock wimax
john@john:~$ sudo /etc/init.d/wimax start
john@john:~$ sudo wimaxcu ron
HW and SW Radios are ON.
john@john:~$ sudo wimaxcu connect network 2
Connecting to Clear Network...
Connected.
john@john:~$ 

Now my next project is automating the process.  Is it possible to have the wifi auto-connect by wifi when my home network is available (which it already does automatically) or switch to automatically wimax when its not available?

Thanks again for all your help.

---

### Post by slklim on 2010-10-18
Holy cow! Awesome! Congrats :-)

> **jclb111181 said:**
> Now my next project is automating the process. Is it possible to have the wifi auto-connect by wifi when my home network is available (which it already does automatically) or switch to automatically wimax when its not available?

Yes, of course it's possible. The real question is how much work you're willing to put into it.

The first thing to remember is that WiMAX is still a very new thing, especially on Linux. The WiMAX tools that you've compiled and installed are pretty immature code-wise, and the whole user interface thing hasn't really been thought out yet. Notice how you have to connect using the command line, and how there's no icon or anything in your system tray or toolbar for, like, a graphical way of managing your WiMAX connection? Neither GNOME nor KDE (or XFCE or IceWM or any other desktop suite (or wicd, for that matter)) have any utility that manages WiFi and WiMAX together. If you're looking for a quick, easy little program to download and install, it ain't out there yet. Maybe in the near future gnome-network-manager will also take care of WiMAX, but not yet.

So, if you're really motivated to get it working, I'd recommend trying to do it with a nice little shell script. Do a Google search for "linux shell script" or as it looks like you're using bash, you could search for "bash script" too.

Basically, you're going to use your shell script to:
1) Enable WiFi
2) Get a text listing of all available WiFi networks
3) Parse that list and see if your home network is on it
4) If it is, connect to it
5) If it isn't, disable WiFi, enable WiMAX, and connect to Clear

WiFi should automatically be enabled when you boot up, so we'll ignore that for now.

There's a neat nifty little program in the wireless-tools package called iwlist. You use it from the command line to scan the area for WiFi networks. Really cool. Run it and pass its output through grep to find if your home network is one of the ones found:
$ sudo iwlist wlan0 scan | grep yourHomeNetworkName

If it exists, grep's return code is 0, and if not, grep returns a 1. You can use that as the condition for the "if it is, else" test in parts 4 and 5 above.

So, just a quick stab at this one here, but I'm thinking your bash script will be something like this:
#!/bin/sh
iwlist wlan0 scan | grep yourHomeNetworkName
if [ $? -eq 0 ]; then
  #Do whatever it is you do to connect through WiFi. Probably run gnome-network-manager.
else
  /etc/init.d/wimax start
  wimaxcu connect network 2
fi

Save all of that into a file and name it something useful, like wireless.sh. You'll have to change the permissions on it to be able to execute it. Run this:
$ chmod a+x wireless.sh

And to run this particular script, you'll need to be root or sudo and you'll have to specify the path to the file:
$ sudo ./wireless.sh

Does that work? It should be close, I think. I didn't bother with enabling or disabling WiFi because I don't need to on my machine, but your mileage may vary. Give all of that a try. Good luck, again :-)

---

### Post by iisaphd on 2010-12-20
> **jclb111181 said:**
> OK.  Started over with a fresh install of 10.10.  Updated everything to the max.  

I got all the way to this command:  sudo wimaxcu connect network 2

and I get this:

john@john:~/new/WiMAX-Network-Service-1.4.0$ sudo wimaxcu connect network 2
ERROR: Attempt to connect not successfull - SW Radio is OFF.


This may be a dumb question, but no dumber than any of my other questions.  How do I turn on the radio.  I currently have my wifi connected.  Should I disconnect? 

I thank you once again and eagerly await your suggestions.

So...no idea how you would fix the compilation problem short of reinstalling the OS?

---

### Post by slklim on 2010-12-21
No. Sorry. I'm still not sure what exactly was causing the compilation problem, so I have no idea what the solution would be. Still wondering about that one....

Reinstalling the OS (and "updating everything to the max") worked for that user. It may or may not work for you. Dunno. It should, but no guarantees.... *shrugs*

There's a solution that doesn't involve reinstalling everything, I'm sure. There has to be. All you have to do is pinpoint exactly what's different between your version of GCC and a "good" one, then make that one single reversion (and definitely post what you did to this thread, please!).

Good luck!

---

### Post by iisaphd on 2010-12-22
> **slklim said:**
> No. Sorry. I'm still not sure what exactly was causing the compilation problem, so I have no idea what the solution would be. Still wondering about that one....
 
Reinstalling the OS (and "updating everything to the max") worked for that user. It may or may not work for you. Dunno. It should, but no guarantees.... *shrugs*
 
There's a solution that doesn't involve reinstalling everything, I'm sure. There has to be. All you have to do is pinpoint exactly what's different between your version of GCC and a "good" one, then make that one single reversion (and definitely post what you did to this thread, please!).
 
Good luck!
 
Thanks. If I find a fix, I will update. Currently, I am running 10.10 and think that I have the latest versions of the compilers, etc, but still get that error. Have been googling around for other times when this error occurred, but haven't got a solution yet. Even if I find one, it may only be a solution that works for me. :(
 
Man..I really want my 4G to work!!

---


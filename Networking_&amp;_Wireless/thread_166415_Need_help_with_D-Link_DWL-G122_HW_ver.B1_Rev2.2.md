---
title: "Need help with D-Link DWL-G122 H/W ver.B1 Rev2.2"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by Princey on 2006-04-26
Hi folks, been stumping my head and reading my eyes out of my sockets for over a week through the forums and via google and haven't been able to make much of a progress. I have a USB D-Link Wireless Card I use on one of my Windows machines and seeing I did some re-arranging, I wanted to move my main computer to my workshop from which I run Kubuntu Breezy. I've followed [this]("http://www.ubuntuforums.org/showthread.php?t=106846") How To Guide step by step and didn't had much progress as can be seen with [this post]("http://www.ubuntuforums.org/showpost.php?p=952227&postcount=55") I have in the thread. I managed after much tinkering with the network interfaces to get the card to light up but after reboot, it resets to some default values not listed in the /etc/network/interfaces file. A copy of mine can be seen in the aforementioned linked post. 

I decided maybe it was some error on my part so I proceeded to redo the entire installation, copying and pasting as much as I was able making the minor edits to suit my installation. This time, before proceeding, I examined every output searching for any signs of error messages. That's where I need some input from more experiences Linux-ers out there. In step #2 of the HOWTO, it says: > sudo make install This I did but notice the error message in the output: > princey@MCES:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7'
princey@MCES:/usr/src/rt2570-1.1.0-b1/Module$ sudo make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/usr/src/rt2570-1.1.0-b1/Module modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7'
  INSTALL /usr/src/rt2570-1.1.0-b1/Module/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7'
**_grep: /etc/modprobe.conf: No such file or directory_**
*[I]append 'alias rausb0 rt2570' to /etc/modprobe.conf*[/I]


I assume the error message (made bold and underlined for emphasis in the terminal output) "No such file or directory" means that the proceeding line will fail. Is that why I can't get it to work and when I did have temporary success, a restart of the network interface defaulted to values which were incorrect? Is so, should I go about making the file */etc/modeprobe.conf* using a text editor and proceed with the rest of the installation?

Any help would be appreciated. Thanks in advance.

---

### Post by Princey on 2006-04-27
Update:

Ok, I've gone past the initial error (solved it by creating the file and building again) however, something tells me that this is wrong as nothing happens after this: Quote: > sudo lsmod -a result yields > Usage: lsmod If I ignore this message and continue, when I get to this point:
Code: > sudo echo rt2570 >> /etc/modules I get: > bash: /etc/modules: Permission denied 

iwconfig lists the usb wireless card but the frequency is wrong. I can correct it using > sudo iwconfig rausb0 2.437GHz but when I restart the network interface, it resorts back to 2.412which is channel 1, not channel 6. I can't get past this block.

__________
Edit:

After much tinkering and removing the auto line at the end, I finally got the card working. I'm using it right now to type here. Just one thing though, I must manually set it to run in the networking interface after booting as it won't boot automatically. Is there anything I can do? I already said that the code to make it load on bootup returned a bash error (see 2nd post). Any advice would be welcomed.

---


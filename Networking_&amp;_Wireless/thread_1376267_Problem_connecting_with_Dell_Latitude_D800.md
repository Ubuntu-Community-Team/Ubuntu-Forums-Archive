---
title: "Problem connecting with Dell Latitude D800"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Uziel126 on 2010-01-09
Hi, 

I recently installed Ubuntu onto my Dell laptop, the Karmic Koala release. I've had experience with Jaunty on my desktop, everything works fine there. However, I cannot use the wireless on this laptop. I've tried multiple fixes, but none of them work: firmware installation, driver installation through terminal as well as ndisgtk. 

I don't know if this is important, but the ndisgtk program says my driver is invalid... I had to manually download the driver, as I wiped the laptop before installing ubuntu.

Any help would be appreciated... Thanks

EDIT: ndiswrapper gives me this error: 
> user@user-laptop:~/bcm4306$ ndiswrapper -l
bcmwl5 : invalid driver!
but as far as I can tell, for my BCM4306 wireless network controller, this is the appropriate driver...

---

### Post by Uziel126 on 2010-01-09
bump

---

### Post by Uziel126 on 2010-01-10
I don't really want to be irritating, but it's quite urgent and I don't know what to do... So bump... Any suggestions on how I could troubleshoot the problem? Cause I'm not sure myself what it is...

---

### Post by bkratz on 2010-01-10
> **Uziel126 said:**
> I don't really want to be irritating, but it's quite urgent and I don't know what to do... So bump... Any suggestions on how I could troubleshoot the problem? Cause I'm not sure myself what it is...

This thread should help you (about halfway down)

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by bkratz on 2010-01-10
Oh I just noticed you originally used ndiswrapper. We will probably need to either remove it or blacklist a couple of files. I will search and find them and get back.

---

### Post by bkratz on 2010-01-10
Additional information--someone in the same state.

[http://ubuntuforums.org/showthread.php?t=1314852&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1314852&highlight=BCM4306)

Especially see post #3

---

### Post by Uziel126 on 2010-01-12
ok, I'll try those threads for help then... thanks for responding. :)

I get the feeling that in order to use any of the howtos, I need to undo a lot of my actions... But i don't know how to remove ndiswrapper, for one... Also, I don't see anything in Hardware Drivers, except NVIDIA...

---

### Post by Uziel126 on 2010-01-14
Before I screw up the computer any more... I'm not sure what I have to undo. This is my terminal history, could someone enlighten me as to what I'd have to do?

>   [FONT=Courier New]1  sudo aptget-install ndiswrapper-utils
    2  sudo apt-get install ndiswrapper-utils
    3  sudo ndiswrapper -i bcmwl5.inf
    4  ndiswrapper
    5  sudo apt-get install ndiswrapper-common
    6  sudo ndiswrapper -i bcmwl5.inf
    7  sudo lshw -C network
    8  sudo ndiswrapper -i /home/user/Desktop/bcmw5.inf
    9  sudo ndiswrapper -i /home/user/Desktop/bcmwl5.inf
   10  sudo modprobe ndiswrapper
   11  sudo lshw -C network
   12  sudo apt-get install b43-fwcutter
   13  ndiswrapper -l
   14  lspci -nn
   15  site:ndiswrapper.soureforge.net 14e4:4320
   16  mkdir ~/bcm4306
   17  mkdir ~/ndiswrapper
   18  sudo nano /etc/apt/sources.list
   19  sudo nano /etc/network/interfaces
   20  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
   21  sudo nano /etc/iftab
   22  sudo apt update
   23  sudo aptitude update
   24  sudo aptitude install build-essential
   25  user -r
   26  uname -r
   27  sudo aptitude install linux-headers-2.6.31-17-generic
   28  sudo ln -s /usr/src/linux-2.6.31-17-generic /lib/modules/2.6.31-17-generic/build
   29  wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
   30  cd
   31  sudo aptitude install cabextract
   32  cd ~/bcm4306
   33  cabextract sp33008.exe
   34  sudo ndiswrapper -i bcwl5.inf
   35  sudo modprobe ndiswrapper
   36  sudo depmod -a
   37  sudo modprobe ndiswrapper
   38  wconfig
   39  iwconfig
   40  lspci
   41  ndiswrapper
   42  sudo apt-get remove ndiswrapper
   43  ndiswrapper
   44  make uninstall ndiswrapper
   45  sudo apt-get remove ndiswrapper
   46  sudo rmmod ndiswrapper
   47  ndiswrapper
   48  sudo apt remove ndiswrapper
   49  apt remove ndiswrapper
   50  sudo apt-get remove ndiswrapper
   51  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
   52  gksu gedit /etc/udev/rules.d/70-persistent-net.rules
   53  sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz)
   54  tar xvzf ndiswrapper-1.28.tar.gz
   55  tar xvzf ndiswrapper-1.28.tar.gz
   56  cd ndiswrapper-1.46
   57  make distclean
   58  make
   59  sudo make install
   60  ndiswrapper
   61  ndiswrapper-1.46$ sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) -O${HOME}/sp33008.exe
   62  cd ndiswrapper-1.46
   63  sudo make install
   64  cd ~install_flash_player_10_linux
   65  sudo apt-get install linux headers- 'uname -r'
   66  user@ubuntu:~$ sudo apt-get update
   67  sudo apt-get install linux-headers-`uname -r`
   68  sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
   69  cd ndiswrapper-1.46
   70  ndiswrapper -v
   71  sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) -O${HOME}/sp33008.exe
   72  cd~
   73  cd ~
   74  mv sp33008.exe bcm4311
   75  cd bcm4306
   76  cabextract sp33008.exe
   77  sudo ndiswrapper -i bmcw15.inf
   78  sudo ndiswrapper -i bcmwl5.inf
   79  ndiswrapper -l
   80  installed drivers:
   81  xrandr --output VGA --mode 1024x768
   82  xrandr --output VGA --off
   83  cd /
   84  cd /lib/firmware/b43
   85  ls -alt
   86  cd ..
   87  cd /b43legacy
   88  cd b43
   89  ls
   90  ls l*
   91  cd ..
   92  cd /
   93  ls
   94  cd /lib/firmware/b43
   95  cd ..
   96  cd /b43legacy
   97  ls
   98  cd b43legacy
   99  ls -alt
  100  ndiswrapper -l
  101  whereis ndiswrapper
  102  man ndiswrapper
  103  pwd
  104  man ndiswrapper
  105  man ls
  106  h
  107  hist
  108  pwe
  109  pwd
  110  ls
  111  cat
  112  cd 7
  113  cd /
  114  ls
  115  cd boot
  116  ls
  117  cd ..
  118  ls
  119  cd etc
  120  ls
  121  cat ts.conf
  122  ls
  123  cat ts.conf | pg
  124  vi ts.conf
  125  vi xxx
  126  history > mycmds.txt
  127  history[/FONT]
sorry if it's long or messy...

---

### Post by bkratz on 2010-01-14
If you are still interested in removing ndiswrapper and trying the other methods see this thread. Or you could start over with nidswrapper and try again, your choice. I think I would try the native drivers first. You can always return to the ndiswrapper methodology if need be.

[http://ubuntuforums.org/showthread.php?t=507378](http://ubuntuforums.org/showthread.php?t=507378)

---

### Post by Uziel126 on 2010-01-15
after typing sudo modprobe -r ndiswrapper, i get this: 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

EDIT: after using synaptic to uninstall, ndiswrapper is now gone. But i'm still stuck without wireless, even after following the steps here: [http://ubuntuforums.org/showthread.php?t=1314852&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1314852&highlight=BCM4306)

I used the 3rd method, followed it as best as I could, but the wireless isn't up.

---

### Post by Uziel126 on 2010-01-19
bump

anybody? I don't know what i should do now...

---


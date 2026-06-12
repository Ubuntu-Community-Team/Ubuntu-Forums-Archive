---
title: "Howto: Setting up WiFi on a Toshiba nb100 with Ubuntu 8.10 Intrepid"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Tuliku on 2009-02-07
Hello, i spend the last week trying to get my wifi working on my new nb100, and it was hell. But finally got it working, and i thought i share it with you. 
Some parts below i took from other posts on this forum, and updated them a little.

**Here we go**

The device string displayed in a terminal by lspci -v
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at 92100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

Check under System / Administration / Harware Drivers and if you have the Atheros HAL and the Atheros wireless thing, disable them and then reboot.
In my case i had nothing there.

Then continue in a terminal with:
```
sudo apt-get install build-essential
```

Then:
```
sudo apt-get install subversion
```

Then download the latest Madwifi Hal driver:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
(at the moment of writing this it is the "madwifi-hal-0.10.5.6-current.tar.gz")

(I downloaded it in my browser, then saved it in a new directory, and extracted the files in that new directory)
Go in your terminal to the directory with the extracted files and do:

```
make
``` 

Then:
```
sudo make install
```

Then:
```
sudo gedit /etc/modules
```
Fill in your password, and add at the bottom of the file:
```
ath_pci
```

Save, close, reboot.

The only thing that changed for me now was that i had the greyed out line "Wireless Networks" in my network manager.

To make it work, i had to press Function Key + Wifi key (~), then Function key + Bluetooth key (F1), and again Function Key + Wifi key (~)

And then everything started working...
Hura...

If i turn off the bluetooth, then wifi also turns off for some reason.

Here some stats about my whole setup:

Toshiba NB 100
- 2 GB memory (1 gb was original)
- 320 GB toshiba hard disk (120 gb was original)

Wireless network
- WPA Personal
- Phrase key security/password

I hope my post will help all the others who struggle with the "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)" card.
I think it will also work on other notebooks, but cant guarantee it.
Good luck, and if you have any questions, let me know.

Tuliku

**PS**, i'm running kernel 2.6.27-9 cause the 2.6.27-11 kills my wired network connection.

---

### Post by ichi_730 on 2009-02-11
> **Tuliku said:**
> Hello, i spend the last week trying to get my wifi working on my new nb100, and it was hell. But finally got it working, and i thought i share it with you. 
Some parts below i took from other posts on this forum, and updated them a little.

**Here we go**

The device string displayed in a terminal by lspci -v
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at 92100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```


Check under System / Administration / Harware Drivers and if you have the Atheros HAL and the Atheros wireless thing, disable them and then reboot.
In my case i had nothing there.

Then continue in a terminal with:
```
sudo apt-get install build-essential
```

Then:
```
sudo apt-get install subversion
```

Then download the latest Madwifi Hal driver:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
(at the moment of writing this it is the "madwifi-hal-0.10.5.6-current.tar.gz")

(I downloaded it in my browser, then saved it in a new directory, and extracted the files in that new directory)
Go in your terminal to the directory with the extracted files and do:

```
make
``` 

Then:
```
sudo make install
```

Then:
```
sudo gedit /etc/modules
```
Fill in your password, and add at the bottom of the file:
```
ath_pci
```

Save, close, reboot.

The only thing that changed for me now was that i had the greyed out line "Wireless Networks" in my network manager.

To make it work, i had to press Function Key + Wifi key (~), then Function key + Bluetooth key (F1), and again Function Key + Wifi key (~)

And then everything started working...
Hura...

Here some stats about my whole setup:

Toshiba NB 100
- 2 GB memory (1 gb was original)
- 320 GB toshiba hard disk (120 gb was original)

Wireless network
- WPA Personal
- Phrase key security/password

I hope my post will help all the others who struggle with the "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)" card.
I think it will also work on other notebooks, but cant guarantee it.
Good luck, and if you have any questions, let me know.

Tuliku

**PS**, i'm running kernel 2.6.27-9 cause the 2.6.27-11 kills my wired network connection.

Hi there.. Nice one..

Im also using Toshiba NB100 using wubi intrepid 8.10 and I am having a hard time configuring my network because Im using a smartbro usb modem or what they called the dongle? or longcheer?

Is there any step by step guide on how to configure my Internet connection?

Thank you for youre time reading this one..
Newbi here...
:)

---

### Post by Tuliku on 2009-02-16
USB modem ? Hmm, no idea, but will ask around and let you know.

---

### Post by Potential Fossil on 2009-02-24
great step-by-step

as a noob I have a question:

when you say this:
(I downloaded it in my browser, then saved it in a new directory, and extracted the files in that new directory)
Go in your terminal to the directory with the extracted files and do:

how do i go to the directory with the extracted files?
I extracted them to a folder on my desktop and a folder in my home folder (the one with the same name as my username)

Many thanks!

---

### Post by Tuliku on 2009-02-26
Lets say your home folder is named "fossil" (same as your user name).
Open a terminal.
Type in "pwd"
It should say "/home/fossil"
If not, navigate to that folder, the commands you can find easily in google.
If yes, type "ls"
Now you should see somewhere a directory called something like this "madwifi-hal-0.10.5.6-r3942-20090205"
Type in "cd madwifi-hal-0.10.5.6-r3942-20090205"
And then continue with the "make" command..

---

### Post by Potential Fossil on 2009-02-28
Many thanks....all working now!

For users of Xubuntu, type in [FONT="Arial"]**nano**[/FONT] instead of [FONT="Arial"]**gedit**[/FONT]

---

### Post by martinb9999 on 2009-03-08
OK, did all that - including installing Linux headers with```
sudo apt-get install linux-headers-$(uname -r)
``` which is required for make to work. [Hat-tip]("http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo")

The hardware seems to be basically OK - it's detecting visible WAPs, but still no connection. Fails to connect to either of my WAPs, one running WEP and one WPA2. Logging on the WPA2 one (Apple Airport Extreme, not that it likely matters) suggests that I'm getting password failures, which I *know* to be untrue.

Wired network is working fine, btw.

(side-rant: what is the point of having hardware Ubuntu Certified if something as fundamental as WiFi doesn't work out of the box?)

(edit: Netbook is running Hardy presumably for LTS reasons, but that means that the ath5k issue noted in the 8.10 release notes isn't applicable)

---

### Post by Tuliku on 2009-03-09
If you use the Ubuntu Netbook Remix on the Toshiba NB100, wifi runs withou problems. I've tested that and it was ok for me. But i chose for Ubuntu 8.10 cause i didn't like the UNR too much, so i installed 8.10 intrepid version. As soon as jaunty comes out, i will play with that.

About your password issue's, no clue. Sorry. Hopefully someone else will be able to help.

---

### Post by martinb9999 on 2009-03-09
1) Clearly it doesn't
2) It's not a password issue; that's the WAP's best guess, but it's wrong.

---

### Post by freechiru on 2009-10-03
Followed this, but one major problem: my NB100 doesn't have bluetooth.  Any suggestions?

---

### Post by mandolin1888 on 2010-02-23
OK totally newbie here so apols for general dumbness.
 
I've been having problems with my NB100 wireless connection, I've followed the guide and gotten to the 'make' command where I get .....
 
Makefile.inc:66: *** /lib/modules/2.6.24-19-lpia/build is missing,
please set KERNELPATH. Stop.
 
Can anyone nudge me in the right direction?
 
All help greatly appreciated.
 
Here is the full terminal text...
 
#####[EMAIL="#####@TOSHIBA-User:~$"]@TOSHIBA-User:~$[/EMAIL] sudo which apt-get install build essential
[sudo] password for #####:
/usr/bin/apt-get
/usr/bin/install
#####[EMAIL="#####@TOSHIBA-User:~$"]@TOSHIBA-User:~$[/EMAIL] sudo which apt-get install subversion
/usr/bin/apt-get
/usr/bin/install
#####[EMAIL="#####@TOSHIBA-User:~$"]@TOSHIBA-User:~$[/EMAIL] pwd
/home/#####
#####[EMAIL="#####@TOSHIBA-User:~$"]@TOSHIBA-User:~$[/EMAIL] ls
case.doc                  Desktop    Examples
Music     Public     Videos
Documents  madwifi-0.9.4-r4119-20100201
Pictures  Templates
#####[EMAIL="#####@TOSHIBA-User:~$"]@TOSHIBA-User:~$[/EMAIL] cd madwifi-0.9.4-r4119-20100201
#####[EMAIL="#####@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$"]@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$[/EMAIL] make
cd: 1: can't cd to /lib/modules/2.6.24-19-lpia/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-lpia/build is missing,
please set KERNELPATH. Stop.
#####[EMAIL="#####@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$"]@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$[/EMAIL] make which
cd: 1: can't cd to /lib/modules/2.6.24-19-lpia/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-lpia/build is missing,
please set KERNELPATH. Stop.
#####[EMAIL="#####@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$"]@TOSHIBA-User:~/madwifi-0.9.4-r4119-20100201$[/EMAIL]

---


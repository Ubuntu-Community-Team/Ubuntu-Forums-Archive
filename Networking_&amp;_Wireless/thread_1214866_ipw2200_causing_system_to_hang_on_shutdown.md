---
title: "ipw2200 causing system to hang on shutdown"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Swammy on 2009-07-16
Good morning,

Introduction:
========
I've been running ubuntu "jaunty jackalope" for a few days now as an attempt to move away from the often buggy Windows environment. So far, I'm quite happy with the speed and friendliness of the Linux environment. I like that I can customize my workspace a lot more efficiently with free programs, without the hassle of adware and system bog-downs. I've been a windows user since '95 came out, and over the years have become a 'go to' guy for other people having computer problems. I'm somewhat of a geek, and until recently considered myself a very 'computer smart' person. With my experience of Linux, I've found that I'm merely a windows geek, and know hardly anything else about computers aside from hardware troubleshooting.

Problem:
======
I've gotten so far as to mount my shared drives from my desktop Vista machine to this linux laptop (Using the guide found here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)).  At first, I had the problem of the system hanging at shutdown with the following error codes:
> CIFS VFS: server not responding
CIFS VFS: no response for cmd ## mid ###but I solved that with the following code (from site: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)):

> 
sudo update-rc.d -f umountnfs.sh remove
sudo update-rc.d umountnfs.sh stop 15 0 6 .Now, I have a different problem which appears to be because of my wireless card. I'm running a Dell Latitude D810 laptop with a Intel Pro Wireless 2200 mini-pci card that I purchased new off of ebay for about 12 bucks.

Every time I shut down or restart my laptop, my system hangs and repeats the following error message over and over again:
> *ipw2200 Failed to send SYSTEM_CONFIG: Already sending a command.*I gotta say, I'm lost as heck. I've researched the problem through google, and all that I can come up with is that ipw2200 refers to my wireless card. People who have this issue are having it because of their WPA security on their network, but I don't have WPA implemented...I restrict my network by MAC address. 

If anyone can help me solve this, it would be very much appreciated. Keep in mind that I don't know very many of the terminal commands, so please explain when providing a solution. Thank you in advance, and I look forward to all your help.

[B]Solution:

Ok, After a clean install of Jaunty, I still felt the need to have my windows shared drives accessible through my network. I utilized the following process with success, and am no longer having the errors described previously.

Step 1: I installed Wicd Manager, which by some is referred to as a better alternative to NetworkManager. Installing this, in turn automatically uninstalled my NetworkManager.[/B]
> **sudo apt-get install wicd**[B]Step 2: I installed the smbfs module, which (as far as I know) is necessary in order to share network folders.
[/B]> **sudo apt-get install smbfs**[B]Step 3: I hit Alt+F2 to bring up the run dialog, and entered my shared folder as depicted below
[IMG]http://i31.tinypic.com/k9etna.png[/IMG]
In this case, 192.168.0.11 is the IP where my shared folders are, and Movies is the name of my shared folder. If typed in properly, then the shared folder pops up. I then hit Ctrl+D to add the bookmark.

I repeated step 3 above for each of my shared folders (4 of them for me). Now, all my shared folders show up in my 'Places>Bookmarks' menu..even after reboot (which is what I wanted in the first place). Also, upon reboot or restart, it is a smooth transition with no sign of the previous error messages.

Keep in mind, all this is done after a clean install of Jaunty. I'm not sure exactly WHAT was causing the original errors, nor do I care. It's possible that simply swapping out NetworkManager for wicd would have solved my problem, and all the rest has been done for nothing. Oh well...my problem is solved, and hopefully someone else can learn from my headache.

Again, Thanks to Chili and Martin for your help...I appreciate your time.[/B]

---

### Post by chili555 on 2009-07-16
I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104) and I was amused by this:> Since Jaunty final it is solved for me.It is not solved for you, and you are running Jaunty!

Let's try two things. First, let's stop the driver from scanning to associate and let Network Manager do the hard work. Open a terminal and do:```
sudo ifdown eth1
sudo rmmod  -f ipw2200
sudo modprobe ipw2200 associate=0
sudo ifup ipw2200
```Now do you see the error?

If that doesn't change anything, let's stop Network Manager and try to connect manually:```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig eth1 essid <your_network_essid>
sudo dhclient eth1
```Any errors? Did you connect?

---

### Post by Swammy on 2009-07-16
Yes, I came across that thread while trying to do the research on my own. Unfortunately, they lost me when they said to put "associate=0", as it doesn't seem ubuntu has the same config file required for that. Then again, I could be completely wrong and just not know enough about what I'm talking.

Unfortunately, neither one of those solved my problem. I am still able to connect to my network, no problem...and still able to browse the net, but I am also still getting the same errors upon restart / shutdown. :confused:

One thing that I might be doing wrong, I'm not sure. You said <your_network_essid>. My network ESSID is 3 words with spaces between. I tried typing it in as is, and it wouldn't take the command. However, I've read in another post that you have to include /040 instead of spaces. That said, that's what I typed. My network is called Jack and Jill, so I put for my essid: Jack/040and/040Jill. I guess I did it right, because it didn't show up with an error, and I am still connected to the internet. Could you please confirm that I'm doing it right?

On another note, thank you for taking the time to explain things to me in a third grader perspective. I'm very new to this, and am having trouble grasping it. My 30 year old brain doesn't learn as easily as my 15 year old brain did back in the day. But, also thank you for taking the time to explain to me exactly why I'm doing these commands...this will ultimately help me in "learning to fish", rather than just giving me fish outright. Your time and effort is very much appreciated, and I hope that you continue to help me see this through to the end solution. I'll have my wife bake you some cookies when it all gets solved :)

---

### Post by chili555 on 2009-07-16
> it doesn't seem ubuntu has the same config file required for that.The unwritten protocol is that if the file doesn't exist, you create it. Even more confusing is that effective with Jaunty, you would create */etc/modprobe.d/ipw2200.[COLOR="Red"]conf[/COLOR]*. We all knew that, right??? It doesn't matter much, because it doesn't change the behavior. Incidently, my suggestion was just a way to try it temporarily. It goes away on reboot or restart.> My network is called Jack and Jill, so I put for my essid: Jack/040and/040JillThe correct way is with quotes:```
sudo iwconfig eth1 essid "Jack and Jill"
```> My 30 year old brain doesn't learn as easilyWell, you can just imagine my 66 year old brain! You can learn all this just fine. However, be warned: the more you learn, the more you realize you don't know.

Let's see if the system logs can give us any clues:```
sudo cat /var/log/messages | grep ipw
```That means, roughly, read out the kernel messages file, but confine the output to those messages having to do with ipw. Post the result here and lets see what it reports. You can omit any repeats.

---

### Post by Swammy on 2009-07-16
Hrmm, you asked for it lol. Apologies in advance, I'm not sure which repeats to omit. To ensure that I don't omit the wrong thing, I'm posting it all in here. Again, I apologize that it's all a mess. Hopefully as I get more 'linux-smart', I'll be able to post proper logs. Here's the system logs:

> Jul 15 14:28:56 Laptop kernel: [   12.756785] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 15 14:28:56 Laptop kernel: [   12.756789] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 15 14:28:56 Laptop kernel: [   12.756896] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 15 14:28:56 Laptop kernel: [   12.757527] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 15 14:28:56 Laptop kernel: [   12.757566] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 15 14:28:56 Laptop kernel: [   12.990341] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 15 14:51:19 Laptop kernel: [   12.722760] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 15 14:51:19 Laptop kernel: [   12.722763] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 15 14:51:19 Laptop kernel: [   12.722866] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 15 14:51:19 Laptop kernel: [   12.723647] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 15 14:51:19 Laptop kernel: [   12.723688] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 15 14:51:19 Laptop kernel: [   12.956371] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 15 21:18:12 Laptop kernel: [   12.736546] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 15 21:18:12 Laptop kernel: [   12.736551] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 15 21:18:12 Laptop kernel: [   12.736662] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 15 21:18:12 Laptop kernel: [   12.737294] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 15 21:18:12 Laptop kernel: [   12.737335] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 15 21:18:12 Laptop kernel: [   12.949570] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 10:35:38 Laptop kernel: [   13.011745] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 10:35:38 Laptop kernel: [   13.011749] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 10:35:38 Laptop kernel: [   13.011908] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 10:35:38 Laptop kernel: [   13.014359] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 10:35:38 Laptop kernel: [   13.014399] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 10:35:38 Laptop kernel: [   13.243242] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 11:08:37 Laptop kernel: [   12.987846] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 11:08:37 Laptop kernel: [   12.987849] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 11:08:37 Laptop kernel: [   12.989457] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 11:08:37 Laptop kernel: [   12.994788] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 11:08:37 Laptop kernel: [   12.994828] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 11:08:37 Laptop kernel: [   13.243173] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 16:27:11 Laptop kernel: [19132.085621] ipw2200 0000:03:03.0: PCI INT A disabled
Jul 16 16:27:29 Laptop kernel: [19149.336196] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 16:27:29 Laptop kernel: [19149.336205] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 16:27:29 Laptop kernel: [19149.336315] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 16:27:29 Laptop kernel: [19149.336569] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 16:27:29 Laptop kernel: [19149.336645] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 16:27:29 Laptop kernel: [19149.476922] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 16:30:43 Laptop kernel: [   12.601305] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 16:30:43 Laptop kernel: [   12.601309] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 16:30:43 Laptop kernel: [   12.601408] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 16:30:43 Laptop kernel: [   12.602153] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 16:30:43 Laptop kernel: [   12.602193] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 16:30:43 Laptop kernel: [   12.801631] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 16:53:21 Laptop kernel: [   12.727034] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 16:53:21 Laptop kernel: [   12.727037] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 16:53:21 Laptop kernel: [   12.727140] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 16:53:21 Laptop kernel: [   12.733888] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 16:53:21 Laptop kernel: [   12.733934] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 16:53:21 Laptop kernel: [   13.004722] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 16:57:42 Laptop kernel: [   13.022096] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 16:57:42 Laptop kernel: [   13.022099] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 16:57:42 Laptop kernel: [   13.022347] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 16:57:42 Laptop kernel: [   13.023054] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 16:57:42 Laptop kernel: [   13.023093] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 16:57:42 Laptop kernel: [   13.238014] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 16 20:45:48 Laptop kernel: [   12.789092] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 20:45:48 Laptop kernel: [   12.789096] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 20:45:48 Laptop kernel: [   12.789198] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 20:45:48 Laptop kernel: [   12.790029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 20:45:48 Laptop kernel: [   12.790072] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 20:45:48 Laptop kernel: [   12.989306] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


EDIT: In hindsight, I see a whole bunch of repeats....simplified it looks to me like:
> 
Jul 16 20:45:48 Laptop kernel: [   12.789092] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 16 20:45:48 Laptop kernel: [   12.789096] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 16 20:45:48 Laptop kernel: [   12.789198] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 16 20:45:48 Laptop kernel: [   12.790029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 16 20:45:48 Laptop kernel: [   12.790072] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Jul 16 20:45:48 Laptop kernel: [   12.989306] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

I could be wrong though...but that looks like about the summary of the big gaggle I posted above. I'll still leave it there just in case.

---

### Post by chili555 on 2009-07-17
Looking at your kernel messages, I see that I am once again cursed with my favorite kind of problem: everything looks perfect, except it still doesn't work properly! In short, your messages look simply perfect.

It was not clear what the outcome was when you stopped Network Manager. I would like to determine if the problem is interaction between the ipw2200 driver and NM. Please stop NM and restart. Does your computer still hang?```
sudo /etc/init.d/NetworkManager stop
sudo reboot -f
```Also, you might open the package manager: System -> Administration -> Synaptic and search for 'backports.' See if you have *linux-backports-modules-jaunty* installed. If not, please do as it contains a newer ipw2200 driver. Unload the old and load the new:```
sudo ifdown eth1
sudo rmmod  -f ipw2200
sudo modprobe ipw2200 
sudo ifup eth1
```Any improvement in your issue?

---

### Post by Swammy on 2009-07-17
Ok, I think it's progress...when I stopped Network Manager and forced a restart, the computer rebooted just fine. I know it's only a temporary solution...but hopefully you can help me make that a permanent solution. Is there maybe a way to create a batch file (DOS term...forgive me, I don't know the linux terminology) that will do the same thing you just did?

As per updating the Jaunty backports..I did as you said. When I checked package manager, it wasn't installed so I installed it. I tried those set of commands that you gave me, and it came up with an error:
> FATAL: Error inserting ipw2200 (/lib/modules/2.6.28-13-generic/updates/ipw2200.kI'm not sure I did it right, because after I restarted and applied the same commands...it seemed to take. There was one small error code, but the wireless is still working. It still hangs on restart though....so I'm at a loss for the cause. Here's a copy of the error I got:
> swammy@Laptop:~$ sudo ifdown eth1
[sudo] password for swammy: 
Ignoring unknown interface eth1=eth1.
swammy@Laptop:~$ sudo rmmod -f ipw2200
swammy@Laptop:~$ sudo modprobe ipw2200
swammy@Laptop:~$ sudo ifup eth1
ifup: interface eth1 already configured
Again, I'm not sure if that's bad, as my wireless is still working...however I am still hanging on reboot/shutdown. Any more expertise you can provide would be awesome. Thanks in advance :)

---

### Post by martinbaselier on 2009-07-17
So networkmanager seems to be causing a conflict when you shut down. 

There are 2 ways to avoid this:

If you only use the laptop at home, you could remove the networkmanager and just set it up manually. 

You would need the following lines in /etc/network/interfaces
```

auto lo eth1
iface lo inet loopback
iface eth1 inet dhcp
wireless-essid SSID

```
replace SSID with the name of your home network. 
to edit the file, type in a terminal:
**sudo gedit /etc/network/interfaces**

The other way, would be to create a shutdown script, which stops the networkmanager. 

Normally it should already be there, could you list the contents of **/etc/rc0.d** and **/etc/rc6.d/**, the first one contains the links to the scripts for system halt, the other ones are for rebooting.

---

### Post by Swammy on 2009-07-17
Contents of my 2 folders are as follows
> swammy@Laptop:/etc/rc0.d$ dir
K01gdm         K63mountoverflowtmp             S30urandom
K02usplash     K74bluetooth                 S35networking
K15umountnfs.sh  K99laptop-mode                 S40umountfs
K20apport     README                     S60umountroot
K20winbind     S01linux-restricted-modules-common  S90halt
K25hwclock.sh     S15wpa-ifupdown
K50alsa-utils     S20sendsigs
swammy@Laptop:/etc/rc0.d$ cd /etc/rc6.d
swammy@Laptop:/etc/rc6.d$ dir
K01gdm         K63mountoverflowtmp             S30urandom
K02usplash     K74bluetooth                 S35networking
K15umountnfs.sh  K99laptop-mode                 S40umountfs
K20apport     README                     S60umountroot
K20winbind     S01linux-restricted-modules-common  S90reboot
K25hwclock.sh     S15wpa-ifupdown
K50alsa-utils     S20sendsigs


I just tried the gedit on my interfaces file...will reboot the computer a few times and let you know how it goes.

---

### Post by Swammy on 2009-07-17
Ok, editing the interfaces file: I'm sure I typed something wrong. I tried with my ssid as "Jack and Jill" (with quotes around it), I tried using Jack\040and\040Jill (something I found on another thread where they suggested using \040 in place of a space). Neither of the 2 settings worked...and I had no network connection whatsoever. It did work in getting rid of my error message though. However, since I had no network connection...it's not a very acceptable solution. It's very VERY possible I didn't put my SSID in properly, so if i'm doing it wrong then please tell me. I verified the spelling was correct, and that it was case sensitive.

---

### Post by martinbaselier on 2009-07-18
first way:
I would suggest to write the networkname like this:
```
Jack\ and\ Jill
```
**sudo service networking restart**
will restart your network, it's faster than rebooting. 

second way:
Both folders do not contain a shutdown link for the networkmanager. I do hope you listed the content, before removing it. If you reinstall the networkmanager.

and enter the follwing line in a terminal. 

sudo update-rc.d NetworkManager stop 10 0 6

There will a shortcut be created to stop the networkmanager when shutting down/rebooting.

---

### Post by Swammy on 2009-07-18
I'm a little lost on what I'm supposed to do. I tried method 1, and regardless on how I type my SSID, my laptop won't connect on startup. On method 2, I'm not sure how to reinstall network manager. I was under the assumption that I already had it. I went to synaptic package manager and it shows that I already have it installed. I'm also looking at the top right of my laptop screen and I have the wireless icon there with the ability to choose one of the several networks that are broadcasting around me. Am I wrong or is that the network manager?

I tried that **sudo update-rc.d NetworkManager stop 10 0 6 .** and ended up with the following error message:
>  System startup links for /etc/init.d/NetworkManager already exist.

I don't know....but I do know that I'm lost. I suppose the easiest solution would be to create a shortcut on my desktop that will utilize the following code:
> 
sudo /etc/init.d/NetworkManager stop
sudo reboot -fThat's quoted from the first page of this thread, and so far the only solution that has stopped the error message from showing up. How do I create a batch file on my desktop that would do that for me? (Or a script...if that's what it's called in linux-speak).

---

### Post by martinbaselier on 2009-07-18
I was under the impression you had removed the networkmanager, since you were using interfaces. See my explanation below.

There are 2 ways to connect to a network, you can either use NetworkManager or use /etc/network/interfaces. If networkmanager is running, interfaces is ignored. 

So test the interfaces file you would first have to stop the networkmanager and restart the network, till it works. When it works you can remove the networkmanager or prevent it from running automatically. 

About the current state of your problem, you are almost there. I've reread the manual of update-rc.d and when networkmanager is present in any of the /etc/rc?.d/ directories it won't change anything. 

There's another program which can create the change and make sure the networkmanager is stopped when rebooting:
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf --level 06 NetworkManager off

```

if you check **ls /etc/rc0.d/** there will now be a link, called K01NetworkManager. The same will be true for /etc/rc6.d/

If there's a link in both directory's the problem should be solved. 

To create a script: (script is the general name, used in all operating systems, You can write scripts in windows too. batch=file is only used for the dos variation)

Anyway, the easiest way to describe howm, is with some terminal commands. You can do the same thing from the graphical interface, but it takes much longer to describe. 
```

mkdir ~/scripts
cd ~/scripts
echo gksudo service NetworkManager stop > stopnetworkmanager
chmod +x stopnetworkmanager

```
Now, right click on the desktop, create launcher and give it a name like, stop networkmanager
the command would be: 
~/scripts/stopnetworkmanager

a little explanation;
~ is your personal home directory
You create a directory scripts in it, go to it, then create a script called stopnetworkmanager, with one line:
gksudo service NetworkManager stop
gksudo is a graphical version of sudo, which asks for the password in a small pop-up window. "service NetworkManager stop", is the same as "/etc/init.d/NetworkManager stop"
"chmod +x"will give the file the right to be executed.

---

### Post by isspeltwrong on 2009-07-18
Thanks for the help!

---

### Post by Swammy on 2009-07-19
> if you check **ls /etc/rc0.d/** there will now be a link, called K01NetworkManager. The same will be true for /etc/rc6.d/
I show files called K50NetworkManager in each directory.....is that a problem? I have a K01gdm in each directory.

---

### Post by martinbaselier on 2009-07-20
That should not really be a problem. The files in the directory are executed in alphabetical order. This also means the files with a lower number will be stopped first. You would only have to worry about that if you would have problems. I presume the problem is solved now, is it?

---

### Post by Swammy on 2009-07-20
When I tried your method, I get the following error window:
[IMG]http://i29.tinypic.com/24cecjr.png[/IMG]
I verified that the file "stopnetworkmanager" is in the proper directory, and I've verified that I typed everything exactly as you said. The stop networkmanager icon on my desktop is an executable file, and the stopnetworkmanager script it refers to has the following line in it:
> gksudo service NetworkManager stop

Any suggestions?

---

### Post by martinbaselier on 2009-07-20
The errormessage shows the script does not exist.

What is the output of 
```

ls ~/scripts -al

```
Why do you need the script? The networkmanager is shut down automatically now according to your output from /etc/rc0.d/. 
Does your system still hang when shutting down?

If so, try lowering the number: (this way it will be turned off earlier)
```

mv /etc/rc0.d/K50NetworkManager /etc/rc0.d/K10NetworkManager
mv /etc/rc6.d/K50NetworkManager /etc/rc6.d/K10NetworkManager

```

---

### Post by Swammy on 2009-07-20
To both Martin and Chili,

Thank you both for your assistance. I finally got tired of trying to deal with this and just re-installed Jaunty so I can start over from scratch. I imagine that I'll be doing this several times until I finally get the hang of what I'm doing. Oh well...this is how I learn best anyways: By breaking it. 

All I can gather from this problem in this thread is that it only comes up when I map my network drives. If I avoid mapping them, then I don't get the problem. Maybe that's helpful in figuring out the cause, I don't know. For now though, I'll avoid mapping my drive...which sucks, but I'd rather do that than deal with the slow reboot.

I appreciate both of your help, and the time you've taken to provide that help.

---

### Post by Swammy on 2009-07-20
Solution (will also post solution on page 1 for any passers-by that happen to have the same issue):

Ok, After a clean install of Jaunty, I still felt the need to have my windows shared drives accessible through my network. I utilized the following process with success, and am no longer having the errors described previously.

Step 1: I installed Wicd Manager, which by some is referred to as a better alternative to NetworkManager. Installing this, in turn automatically uninstalled my NetworkManager.
> sudo apt-get install wicdStep 2: I installed the smbfs module, which (as far as I know) is necessary in order to share network folders.
> sudo apt-get install smbfsStep 3: I hit Alt+F2 to bring up the run dialog, and entered my shared folder as depicted below
[IMG]http://i31.tinypic.com/k9etna.png[/IMG]
In this case, 192.168.0.11 is the IP where my shared folders are, and Movies is the name of my shared folder. If typed in properly, then the shared folder pops up. I then hit Ctrl+D to add the bookmark.

I repeated step 3 above for each of my shared folders (4 of them for me). Now, all my shared folders show up in my 'Places>Bookmarks' menu..even after reboot (which is what I wanted in the first place). Also, upon reboot or restart, it is a smooth transition with no sign of the previous error messages.

Keep in mind, all this is done after a clean install of Jaunty. I'm not sure exactly WHAT was causing the original errors, nor do I care. It's possible that simply swapping out NetworkManager for wicd would have solved my problem, and all the rest has been done for nothing. Oh well...my problem is solved, and hopefully someone else can learn from my headache.

Again, Thanks to Chili and Martin for your help...I appreciate your time. Will copy this post to page 1, and change thread title to [Solved].

---


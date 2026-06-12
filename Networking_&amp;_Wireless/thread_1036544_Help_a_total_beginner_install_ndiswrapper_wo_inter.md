---
title: "Help a total beginner install ndiswrapper w/o internet"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by BreadLust on 2009-01-10
Hello everyone, I am new to Linux and really like the whole "open source" concept... However I'm a bit intimidated by this whole business of entering commands in the terminal. I have the patience to learn, but most discussions have an assumed level of knowledge that is, frankly, far above my pay grade.

I have a hard drive with a Windows XP32 installation and another HD with Ubuntu 8.10, so I can download the ndiswrapper files on my Windows install and transfer them over to the Linux drive, but I have no clue what to do from there. I suppose I'm supposed to enter some commands into the terminal?

Once I get ndiswrapper all squared away, I'll need to install the drivers for this wireless card:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB300N](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB300N)

What I need here is for someone to walk me through the process of entering commands in the terminal and making this happen. Any help is appreciated... I really want to get into Ubuntu, but the difficulties inherent in this whole shell command process are daunting!

---

### Post by unutbu on 2009-01-10
Hi BreadLust, wecome to the forums.
Perhaps this will help you:

Here are instructions on opening a terminal:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

And here are instructions on installing ndiswrapper from an Ubuntu LiveCD:
[http://ubuntuforums.org/showpost.php?p=6364751&postcount=2](http://ubuntuforums.org/showpost.php?p=6364751&postcount=2)

---

### Post by BreadLust on 2009-01-11
Thanks for that! I'll keep reading up on terminal entry from the first link, and thanks to the second link I was finally able to install ndiswrapper.

I'm working on getting the wireless driver going now, based on some instructions I got elsewhere on the forums. Here's what I'm trying to follow:

------------------------------------------------------------------
Here is how I got it working, don't plug in the WUSB300N yet:

Download the drivers:
[http://www.atvnation.com/WUSB300N.tar](http://www.atvnation.com/WUSB300N.tar)

Extract them to /opt/ndis/:
# mkdir /opt/ndis
# tar xvf WUSB300N.tar -C /opt/ndis/
# cd /opt/ndis/Drivers

Install the Driver using NDISWrapper
# sudo ndiswrapper -i netmw245.inf

    installing netmw245 ...

# sudo ndiswrapper -l

    netmw245 : driver installed

# sudo modprobe ndiswrapper
... go ahead and plug in the adapter ...

# sudo dmesg | grep ndis

    "[ 9273.652000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
    [ 9273.712000] usbcore: registered new interface driver ndiswrapper
    [ 9340.364000] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded"

You should now be able to go to your Network Applet Icon and see wireless network in the list.

... or the command iwconfig should return an entry for wlan0, mine looks like this:

    wlan0 IEEE 802.11FH ESSID:off/any
    Mode:Managed Channel:0 Access Point: Not-Associated
    Bit Rate=1 Mb/s Sensitivity=-200 dBm
    RTS thr=2346 B Fragment thr=2346 B
    Encryption key:off
    Power Management:off
    Link Quality:0 Signal level:0 Noise level:0
    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

If you have an unprotected wireless hub, then issue this command to connect:
# sudo dhcpclient wlan0
-------------------------------------------------------------------


Unfortunately, I'm stuck at the very beginning of this process- making the /opt/ndis directory. When I input the "mkdir /opt/ndis" command, the response I get is "cannot create directory `/opt/ndis': Permission denied."

Apparently I don't have the permission to modify or even access folders in the root directory of the filesystem. I went to System>Administration>Users and Groups, unlocked my profile, gave myself all of the user privileges, and for some reason I still can't create folders. Where do I have to go to give myself the permission?

Thanks for any help, I hope these questions aren't too dumb but I'm pretty helpless with Linux.

---

### Post by Guille Damke on 2009-01-11
Hi,

You have to do it as superuser. This is why you see the "sudo" command in some stuff you have already done. Try this:

```
sudo mkdir /opt/ndis
```

You can see that the root is the owner of the /opt directory, that's why you cannot create the directory there. You can check it doing:
```
sudo ls -la /opt
```

Hope it helps.

---

### Post by BreadLust on 2009-01-11
Thanks... I was able to use the mkdir command successfully by putting 'sudo' in front.

However, I got tripped up on the next line:

Me: xvf WUSB300N.tar -C /opt/ndis
Terminal's response: open: No such file or directory

Now I can tell you with absolute certainty that WUSB300N.tar is on my computer and sitting on my desktop, but for some reason the terminal can't see it. Do I need to specify the location of the file? Or put it somewhere else so that it can be seen?

You've all been quite helpful, thank you.:)

---

### Post by unutbu on 2009-01-11
Type
```
sudo tar xvf WUSB300N.tar -C /opt/ndis
```

tar is the name of the command to (un)archive WUSB300N.tar. 
xvf mean to e(X)tract , (V)erbosely, the (F)ile WUSB300N.tar.
-C means to change the directory to /op/ndis, so the extracted files will be written to /opt/ndis. 

Since you (the normal user) are not the owner of /opt/ndis, you need to preface the command with "sudo" so the command is executed with root's superpowers.

---

### Post by BreadLust on 2009-01-11
Unutbu-

Thanks for explaining the commands to me, it definitely de-mystifies things a bit to actually know what my commands are doing.

That said, I'm still getting the "No such file or directory" response, even when using the "sudo" prefix. How can I get the terminal to see my WUSB300N.tar file?

---

### Post by kevdog on 2009-01-11
Im going to back up a step.  You might NOT need ndiswrapper -- I have no idea, but the ndiswrapper project is slowly dying.  Can you post the following:

lshw -C network
lspci -nnm

I'm assuming you either have an internal wireless card or external card.  If you have a USB device, can you post:
lsusb -v

---

### Post by BreadLust on 2009-01-12
I'm pretty sure I'm going to need ndiswrapper. At least that's how they made it seem in the thread I've been trying to follow:

[http://ubuntuforums.org/showthread.php?t=530772&highlight=wusb300n](http://ubuntuforums.org/showthread.php?t=530772&highlight=wusb300n)

Anyways, my wireless card is the WUSB300N, you can see what the forums support says about it here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB300N](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB300N)

I went into the terminal and entered the lsusb -v command and an insanely long string followed, so long actually that the terminal wouldn't display it all. From what I could see though, my wireless card wasn't on it. Is there something particularly you want me to show you?

This is turning into quite the project. I hope this doesn't die... If I can't get my wireless going, well, Linux just isn't going to happen for me. :(

---

### Post by unutbu on 2009-01-12
Hello BreadLust, the message "No such file or directory" means that 
you are either not in the right directory when you typed:
```

sudo tar xvf WUSB300N.tar -C /opt/ndis
```
or the filename is something other than what you typed. Most likely, we are not in the right directory.

When you type commands into the terminal, the commands generally act on the "current working directory". When you open a new terminal, that current working directory is /home/breadlust (assuming that's your username). 

If you see an icon for WUSB300N.tar on your Desktop, then it means the file is in /home/breadlust/Desktop.

In that case, you would need to type
```

cd ~/Desktop
sudo tar xvf WUSB300N.tar -C /opt/ndis
```

or
```

sudo tar xvf ~/Desktop/WUSB300N.tar -C /opt/ndis
```


or
```

sudo tar xvf /home/breadlust/Desktop/WUSB300N.tar -C /opt/ndis

```
(The shell expands ~/ to mean to the same thing as /home/breadlust/)

If you downloaded WUSB300N.tar into some other directory, then change ~/Desktop as appropriate.

Edit: Learning terminal commands (I think) is useful. However, there is a GUI way which my be useful too: Just type
```

gksu nautilus
```
This will open up a graphical file browser. "gksu" is like sudo -- it gives you root superpowers. Use gksu for graphical apps, use sudo for command-line apps. 

Now, simply navigate to the WUSB300N.tar file. Move the file to /opt/ndis. Double-click the file. Nautilus (the file browser) will automatically extract the files from the tar file for you.

---

### Post by BreadLust on 2009-01-12
Everyone who helped me-

I'm writing this post from Ubuntu- woohoo! It worked!

Thanks a lot everyone, I couldn't do it without you. Now I can really get to learning about this OS...

---

### Post by cbossi on 2009-01-17
> **BreadLust said:**
> Thanks for that! I'll keep reading up on terminal entry from the first link, and thanks to the second link I was finally able to install ndiswrapper.

I'm working on getting the wireless driver going now, based on some instructions I got elsewhere on the forums. Here's what I'm trying to follow:

------------------------------------------------------------------
Here is how I got it working, don't plug in the WUSB300N yet:

Download the drivers:
[http://www.atvnation.com/WUSB300N.tar](http://www.atvnation.com/WUSB300N.tar)

Extract them to /opt/ndis/:
# mkdir /opt/ndis
# tar xvf WUSB300N.tar -C /opt/ndis/
# cd /opt/ndis/Drivers

Install the Driver using NDISWrapper
# sudo ndiswrapper -i netmw245.inf

    installing netmw245 ...

# sudo ndiswrapper -l

    netmw245 : driver installed

# sudo modprobe ndiswrapper
... go ahead and plug in the adapter ...

# sudo dmesg | grep ndis

    "[ 9273.652000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
    [ 9273.712000] usbcore: registered new interface driver ndiswrapper
    [ 9340.364000] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded"

You should now be able to go to your Network Applet Icon and see wireless network in the list.

... or the command iwconfig should return an entry for wlan0, mine looks like this:

    wlan0 IEEE 802.11FH ESSID:off/any
    Mode:Managed Channel:0 Access Point: Not-Associated
    Bit Rate=1 Mb/s Sensitivity=-200 dBm
    RTS thr=2346 B Fragment thr=2346 B
    Encryption key:off
    Power Management:off
    Link Quality:0 Signal level:0 Noise level:0
    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

If you have an unprotected wireless hub, then issue this command to connect:
# sudo dhcpclient wlan0
-------------------------------------------------------------------


Unfortunately, I'm stuck at the very beginning of this process- making the /opt/ndis directory. When I input the "mkdir /opt/ndis" command, the response I get is "cannot create directory `/opt/ndis': Permission denied."

Apparently I don't have the permission to modify or even access folders in the root directory of the filesystem. I went to System>Administration>Users and Groups, unlocked my profile, gave myself all of the user privileges, and for some reason I still can't create folders. Where do I have to go to give myself the permission?

Thanks for any help, I hope these questions aren't too dumb but I'm pretty helpless with Linux.

Nice work....Thanks for the hint.

---


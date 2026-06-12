---
title: "no Network manager icon"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by earthshakergb on 2011-09-03
I have a vesion of ubuntu studio 10.04, I am trying to set it up on my network, the help file tells me to right click on the network manager icon, I don't have a network manager icon showing, how do I make it appear?

---

### Post by 2F4U on 2011-09-03
If I remember correctly, Network Manager can be set to automatically start in the auto start programs application.

---

### Post by jb.transfer on 2011-09-03
Hi,

I have just tested this on a UStud 10.4.
Please read to the end before trying.

Open Terminal (uxterm)
then type:
sudo apt-get install network-manager-gnome

Then:
Menu -> System -> Preferences -> Startup Applications

Make sure the checkbox for network-manager ist checked.
Logout/Login
Voila this has done it for me. Except that the net-mgr doesn't find
the ethernet device.

After Reboot the Icon is not shown. Checked the settings in
Startup Application. Net-mgr still checked. Logout/Login
no network-manager.

:lolflag:

Fuzzy Logic more fuzzy than logic

I  found that the applet is running but not shown in the notification are.

I killed the nm-applet process with killall nm-applet. Then I started
nm-applet from an Xterm. Three Messages Appear (shortened)
1.) applet now removed from notification area
2.) applet now embedded in notification area
3.) nm-applet:2477: DEBUG: old state indicates that this was not a disconnect 0

My System is Ubuntu Studio 10.4 64bit and the is highly updated.

---

### Post by earthshakergb on 2011-09-03
is the kill nm applet also entered in the terminal?
is the uxterm different than xterm?
I am a total nube here please be patient
feedback from website, couldn't find package network-manager-gnome
I will keep trying.

---

### Post by earthshakergb on 2011-09-03
Update I can see the network and work it on the straight version, but not in ustudio, not even there. No way to change anything that requires the network:confused:
Here is what I see on the boot up selection dialog, versions 2.6.32-21 no network not installed or what I don't know. 2.6.32-33 network works great, what is the difference? Both are ubuntu 1 is ustudio 2.6.32-21, the other is "normal" 2.6.32-33.

---

### Post by jb.transfer on 2011-09-04
Yes I use the terminal to kill because it will tell me more verbose if something goes
wrong.

uxterm= Unicode Xterm

Check if you have the Package Sources needed for the package via Synaptic.
You can look for the package in a terminal with: 'apt-cache search network-manager'

Please tell me what you need to configure.
I will tell you the appropriate steps to do it via shell commands and configuration files.

---

### Post by earthshakergb on 2011-09-04
not listed in synaptic, closest is net-tools
the apt-cache search network-manager yielded nothing except another command line

---

### Post by LinuxFanBoi on 2011-09-04
right click on the panel, select 'add to panel' from drop down menu, select 'notification area' from the list.

you may need to do an ALT-F2 and enter:

```
'nm-applet --nm-replace'
```

---

### Post by jb.transfer on 2011-09-04
Please check your repository's (Package Source as mentioned before) in /etc/apt/source.list
or via Synaptic.

When I do:
apt-cache search network-manager (ustudio 10.4) the network-manager-gnome shows
up besides many other packages starting with network-manager-....

Run Command -> nm-applet --nm-replace doesnt work

I get the following error message in a terminal from 'nm-applet --nm-replace':

** (nm-applet:2104): WARNING **: <WARN> constructor( ): Couldnt initialize the D-Bus manager.

---

### Post by earthshakergb on 2011-09-04
Tried that no workie, but when I did 'add to panel' then 'notification area' the icon showed up. When I tried to open fire fox, I got a server not found message.
When I right click the icon then properties I get 'network connection:lo' that tells me the network is loopback mode, now what do I do to change it's connection to something? in the basic system it is set to eth 0
I can switch from one the other, but it takes time to reboot every time

---

### Post by LinuxFanBoi on 2011-09-04
> **earthshakergb said:**
> Tried that no workie, but when I did 'add to panel' then 'notification area' the icon showed up. When I tried to open fire fox, I got a server not found message.
When I right click the icon then properties I get 'network connection:lo' that tells me the network is loopback mode, now what do I do to change it's connection to something? in the basic system it is set to eth 0
I can switch from one the other, but it takes time to reboot every time

Did you check to see if there is a wireless switch that can toggle your wireless functionality?  This can be either a hardware ore a software switch.  If it's software, it is often an alternate function of a function key.

I don't recall if you have enabled proprietary drivers for your network adapter, you may also wish to try that.

---

### Post by earthshakergb on 2011-09-04
Driver issue prob not, I am thinking, the network just wasn't enabled in the ustudio side of the install. networking works just fine in the core system side.
When I boot the machine I get 5 options, ustudio main and recovery, WinXP, and ubuntu core and recovery, I would post a screenshot but I can't right now, I decided to install maverick, on that machine and it is still working (kind of reminds me of swapping floppies in Win 95) takes forever.
After that gets done I will check on the network issue and see if it is still present, I am hoping not but we will see.

---

### Post by earthshakergb on 2011-09-04
We have liftoff, I installed Ustudio 10.10, network on line=D>. Thanks for all your help on this one. I'll be back (in my best arnold voice)

---


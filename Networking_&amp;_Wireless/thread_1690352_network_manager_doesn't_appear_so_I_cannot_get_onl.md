---
title: "network manager doesn't appear so I cannot get online"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by loucat on 2011-02-18
Hi all,

I'm having a lot of problems in getting online with ubuntu 10.10, that was installed recently so I'm a newbie.
At first I could connect with my home wifi but when I had to change the connection (I'm abroad now) there was no possibility as network manager didn't appear, even if it was installed, there was no possibility to use the interface (I've tried from the console too writing nm-applet).
I checked some config file as seen in the Italina forum but everything seemed ok.
I then unistalled it and tried to install wicd with a .deb sent me by a friend but it ended up in an error and I've tried many different packages without success.
I also tried with a live cd of ubuntu, either to mount my linux partition and solve the problem from there (but I'm not able to connect from the terminal after I enter as a root in my partition) or to install the normal network manager again from the cd, but anything happen or it shows error messages (sorry if I don't quote them but I'm in windows partition now and I got so many errors I just wouldn't know what to write).

I really don't know what to do and I really need to make it working :sad:
please any suggestion is useful!

thanks a lot,

lou

---

### Post by elbanaan on 2011-02-18
Even if nm or wicd are not working, we can still connect you to wifi with iwconfig (and it's easier for you to find help and give details once you are connected :) )

Let's see where the problem lies:
Try, and give the output of:

sudo lshw -C network
ifconfig
iwconfig
sudo iwlist scan

When posting results, you might want to blank out your MAC adress though.

Also, give the output of:
tail -f /var/syslog/*messages*  (in one terminal)
while you start up the nm applet (in terminal #2)

---

### Post by grahammechanical on 2011-02-18
First let us remember that you use to have a wireless connection when you where at home. So, the thing works!

What did you do when you went to another country that stopped it working? You need to get the Network Manger icon back.

The way to do that is to right click the top panel, select Add to panel, and select Notification Area from the list and then click Add.

Next go to System>Preferences>Startup Applications and make sure the Network Manager has a tick mark against it so that it is one of your startup applications.

If you have un-installed Network Manager you will need to install it. But you do not have an Interent connection. The program is on the install CD. You need to set the CD as one of your software sources.

Load up Ubuntu Software Centre. Click Edit. Select Software Sources. Enter your log in password. Put a tick mark for using the CD as a software source.

Try to find Network manager in the software centre and install it.

Regards.

---

### Post by loucat on 2011-02-18
thanks for your answers.

I did what elbanaan suggested and you can find the output in the attachment.

unfortunately I couldn't give the output of:
tail -f /var/syslog/*messages*  (in one terminal)
while you start up the nm applet (in terminal #2)

as I removed network manager, and I cannot install it again even with the ubuntu live cd, following the instruction of grahammechanical.
When I click on "install" it takes some minutes and it seems it's doing something, but then anything appear or change :(

hope you can find some tips from the output in the attachment.

thanks again!

---

### Post by elbanaan on 2011-02-18
[FONT=Verdana]It seems they are just disabled.
Maybe this will be an easy fix (to get internet back, I have no idea why you can't install nm)

try 

sudo ifconfig wlan0 up
ifconfig -a

if it doesn't work, give the output of
rfkill list
lsmod

if it does work, use 
sudo iwlist scan
to get the ESSID of the network you want to connect to
use
[FONT=Verdana]
[/FONT]iwconfig wlan0 essid [FONT=Verdana]networkessid[/FONT][FONT=Verdana]
[/FONT]iwconfig wlan0 key XXXXXXXXXX[/FONT]
[FONT=Verdana](and if your card does not support picking up the best channel)
iwconfig wlan0 channel X
[/FONT][FONT=Verdana]
and request an ip:

[/FONT]sudo dhclient wlan0 

you should be online if all went well (however unlikely on a first try) :)

PS: make sure any hardware switches are on (ie the wifi light indicator is burning ^^ )

---

### Post by loucat on 2011-02-18
unfortunately it seems that the first 2 commands don't work, so in the attachment you can find the output of [FONT=Verdana]:rfkill list, lsmod.

I do manage to obtain the essid of the network but I'm not online and I receive other errors if I try with the following commands.

If previously I thought that only network-manager had problems... now I'm more and more worried :(


[/FONT]

---

### Post by elbanaan on 2011-02-18
so, the scan command works? 

From the previous output we can conclude that you have a driver installed (iwl3945) and it's also running.

Also, the [FONT=Verdana]
ifconfig -a
command has no output? That's bizar.

Try [/FONT]again
sudo lshw -C network
 to see if the card is still disabled (but seeing as how the scan works, i think it's on)

Next problem: I was not specific enough, my suggestions would only have worked if you use WEP encryption. If it's your own router, maybe remove the encryption (or set it to WEP) just to check (it might be a wpa supplicant problem - also that MIGHT be the reason nm isn't working).

Note: use s:KEY insted of KEY if you have a string (and not hex) wep passw

Alternative: follow this post (following steps also depend on the type of your card and encryption)

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

It's explained much better than I ever could ^^

---

### Post by loucat on 2011-02-19
I'm online :P
I followed elbanaan's instruction and the ones included in the thread suggested.
So now I'm online through the command line but I still don't have network manager and I don't know exactly how to solve this problem as everything I've done before seemed to get the situation worse...
Unfortunately the router is not mine so I don't wanna mess up things changing the encryption, that is a wpa-2.

Any suggestion for having a network manager GUI again? :)

---

### Post by elbanaan on 2011-02-19
Let's see what error it gives when trying to install.

sudo apt-get install network-manager-gnome network-manager > file.txt

---

### Post by loucat on 2011-02-19
file.txt is empty, and the console has the explanation in Italian... a rough translation could be:

E: setting the lock  /var/lib/dpkg/lock is impossible - open (11:  temporary unavailable resource)
E: getting the lock for the ammininstration directory is impossibile  (/var/lib/dpkg/). Another process could have taken it

---

### Post by loucat on 2011-02-19
I think I have some problem with the repository.
I have a red triangle with exclamation mark in the notification area, I tried to follow the instructions and solve the problem, and I thought it was because the default server for me is the Italian one, so I chose the best option (now I'm in London) but it keeps telling me the same warning of my previous message :(

---

### Post by loucat on 2011-02-19
wait! (sorry for the 3 messages one after the other)

now file.txt has something written, sorry for my rough translation:
reading list of files...
generating dependencies tree...
reading status information...
the following NEW packages will be installed:
  network-manager network-manager-gnome
0 updated, 2 installed, 0 to remove e 0 not updates.
You need do download 902kB of archives.
After this operation, 3584kB space disk will be taken.
WARNING: the following packages can't be authenticated.
  network-manager network-manager-gnome
Installing them without verifying [s/N]?

---

### Post by loucat on 2011-02-19
SOLVED!

actually I still don't know what was wrong with network manager, as I installed WICD :D

thank for your great help!!

---


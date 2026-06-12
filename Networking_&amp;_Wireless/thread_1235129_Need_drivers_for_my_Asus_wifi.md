---
title: "Need drivers for my Asus wifi"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by netbookntn on 2009-08-08
Hi;
[[URL="http://ubuntuforums.org/showthread.php?t=1233540&page=5"]Here is a THREAD]("http://ubuntuforums.org/showthread.php?t=1233540&page=6") [/URL]I've been working in that was actually about before I installed Ubuntu.
but, I did install it, dual boot (xp wifi works fine), but for some reason, my Netbook wifi drivers are apparently not in Ubuntu.
Can anyone help here? 
I think I just need to get drivers so the OS recognizes the wifi card.
The thread might explain it a little better as far as any troubleshooting I've done.
Thanks!

[IMG]http://www.picvalley.net/u/1672/13585071773725048551249757685H39GFLA098SdaGWomV47.PNG[/IMG]

---

### Post by Vakman on 2009-08-08
Well the easiest way in my opinion would be to use Ndiswrapper but you could follow this first. [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
If you wish to use Ndiswrapper to do it.
1. Install Ndiswrapper ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))
2. Download .inf file for your driver, this site has it.
([http://www.atheros.cz/download.php?atheros=AR9285&system=2](http://www.atheros.cz/download.php?atheros=AR9285&system=2))
3. Open Ndiswrapper and install the driver.

---

### Post by netbookntn on 2009-08-08
WOW...Ok, I see my drivers there, I didn't know where I could find them.
Thanks!

-I'm not sure if my system is 64 or 32 bit? On system monitor in Ubuntu, it doesn't say.

-I'm assuming I need to download _one or all_ of these below and put those and the drivers on a thumb drive then xfer those to the netbook? My OS says Release 9.04 (jaunty) *whatever jaunty is> :)

Is this the right method?
and the Ndiswrapper will graphically step me thru the rest of the driver install?


For 9.04 Jaunty Jackalope 
[LIST=1]
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common) 
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9) 
[*][http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
[/LIST]

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> WOW...Ok, I see my drivers there, I didn't know where I could find them.
Thanks!

-I'm not sure if my system is 64 or 32 bit? On system monitor in Ubuntu, it doesn't say.

-I'm assuming I need to download _one or all_ of these below and put those and the drivers on a thumb drive then xfer those to the netbook? My OS says Release 9.04 (jaunty) *whatever jaunty is> :)

Is this the right method?
and the Ndiswrapper will graphically step me thru the rest of the driver install?


For 9.04 Jaunty Jackalope 
[LIST=1]
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common) 
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9) 
[*][http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
[/LIST]

Yeah Ndiswrapper is very easy. You just choose the .inf file and then you are done. To check if you system is x86 (32 bit) or x64 (64 bit), open terminal
```
uname -a
```
Wow, I answered this a bit backwards. No problem by the way. Lastly, yes you will need to put them on your netbook. Or connect an ethernet cable to the netbook for the time being.

---

### Post by netbookntn on 2009-08-08
> **Thisislaw said:**
>  
```
uname -a
``` 

2.6.28 -11 generic #42 Ubuntu SMP Fri Apr 17 time i686 GNU/Linux

??:confused:

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> 2.6.28 -11 generic #42 Ubuntu SMP Fri Apr 17 time i686 GNU/Linux

??:confused:
This means you need to download the x86 (32-bit) driver since you have a x86 system installed. i686 will mean that it is 32-bit. If it was x64 then it would have said x86-64 instead of i686. Now you can go ahead and install the driver :)

---

### Post by netbookntn on 2009-08-08
Ok..so..
[amd64]("http://packages.ubuntu.com/jaunty/amd64/ndiswrapper-utils-1.9/download")                  [i386]("http://packages.ubuntu.com/jaunty/i386/ndiswrapper-utils-1.9/download")Which one of those do I dnld then for the other files, the util and ndisgtk?
 it's not an amd processor, it's an atom, but it's not the 386...it's 686.
I feel so stupid...:(
Believe this or not, I actually have built systems ground up! (a few years ago now)
 But, I'm so new to Ubuntu..this is helping me learn tho.

THANKS....

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> Ok..so..
[amd64]("http://packages.ubuntu.com/jaunty/amd64/ndiswrapper-utils-1.9/download")                  [i386]("http://packages.ubuntu.com/jaunty/i386/ndiswrapper-utils-1.9/download")Which one of those do I dnld then for the other files, the util and ndisgtk?
 it's not an amd processor, it's an atom, but it's not the 386...it's 686.
I feel so stupid...:(
Believe this or not, I actually have built systems ground up! (a few years ago now)
 But, I'm so new to Ubuntu..this is helping me learn tho.

THANKS....
It is not a problem and don't feel stupid. Since you have a 32-bit system, you will always install things that say x86, i386, i686, and 32-bit. If you had x64 then you would install anything that said AMD64, x64, or 64-bit etc.

That should help you choose which to download.

---

### Post by netbookntn on 2009-08-08
OK..I give.
I put them on the drive, 
installed to the netbook, it said successful.
errrr...
NOW WHAT? I don't see "programs" to look thru. 
I've dug around, but I don't see anything that resembles what I installed.
messengers, cheeses, 
 LOL

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> OK..I give.
I put them on the drive, 
installed to the netbook, it said successful.
errrr...
NOW WHAT? I don't see "programs" to look thru. 
I've dug around, but I don't see anything that resembles what I installed.
messengers, cheeses, 
 LOL
Try going to Administration > System > Ndiswrapper.

---

### Post by netbookntn on 2009-08-08
I have:
Authorizations
Calibrate Touchscreen
Hardware Driers
Language Support
Log File Viewe
Login Window
Network Tools
Printing
Services
Software Sources
Synaptic package manager
System monitor
System testing
time/date
update mgr
users

---

### Post by Vakman on 2009-08-08
I am not quite sure why it did not install. I can't remember if you can simply install it by going to Applications > Add/Remove Programs or whatever it says and search for ndiswrapper but make sure you have the all selection selected rather than the default option, it will be near the top of Add/Remove once opened.

Hm, if you have installed all 3 deb packages I am not sure why you are not seeing this under anything. Either way try what I said. And ensure you have installed all the packages.
Make sure to reboot but I don't think that is even needed...

---

### Post by netbookntn on 2009-08-08
Ok.on reboot, it did show up at the bottom of Admin, it says 
Windows Wireless Drivers
I browsed to the inf file, two of them netathw and netathwx that came in that driver download.
It hung up in the install, said it wasn't responding, so I forced quit.
I rebooted.
I opened the Windows wireless drivers again and some message came up saying "unable to see if hardware is present".
 I click ok.

Now the Wireless Network Drivers GUI says:
Netathw Hardware present: Yes
netathwx Hardare present: Yes
:confused:
SOrry for being such a bother....

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> Ok.on reboot, it did show up at the bottom of Admin, it says 
Windows Wireless Drivers
I browsed to the inf file, two of them netathw and netathwx that came in that driver download.
It hung up in the install, said it wasn't responding, so I forced quit.
I rebooted.
I opened the Windows wireless drivers again and some message came up saying "unable to see if hardware is present".
 I click ok.

Now the Wireless Network Drivers GUI says:
Netathw Hardware present: Yes
netathwx Hardare present: Yes
:confused:
SOrry for being such a bother....

Not a bother. Windows Wireless Drivers is what you are looking for. Great so, unable to see if hardware is present. Post the output of ```
sudo modprobe ndiswrapper
```
Also if worst comes to worst, and we can't get Ndiswrapper to work, have a look here [http://ubuntuforums.org/showthread.php?p=7409939](http://ubuntuforums.org/showthread.php?p=7409939)

---

### Post by netbookntn on 2009-08-08
errrr....
> WARNING: All config files need .conf:/etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

Stir until well blended, then bake at 350?
:P
:confused:

---

### Post by netbookntn on 2009-08-08
Tried running this code:
```
sudo apt-get install linux-backports-modules-jaunty
```

in reference to that link.
I got:
Reading package lists....Done
Building dependency tree
Reading state information...Done
E:  Couldn't find package linux-backports-modules-jaunty

---

### Post by Vakman on 2009-08-08
So right now if you open "Windows Wireless Drivers" it will tell you "unable to see if hardware is present". Like it will always say this and you are sure you have no wireless currently? Also try ```
iwconfig
```

---

### Post by netbookntn on 2009-08-08
Well, as I said, I'm totally green here.
Yes, it says that same msg after every reboot.
BUT after I click ok, I get those other two drivers showing that say "Currently installed Windwos Drivers" netathw, hardware present YES
same for netathwx

now, all of this said, I could be doing something wrong with simply configuring the networking.
top upper right, I see the network (bar) symbol with a red x on it.
mousing over it says "No network connections"
I do have the wifi symbol key on F2.
I have Fn + F2 and nothing happens.
Config network button gets 
Could not find a network config tool" and click ok

Do I need to be changing something else in settings?
I know the wifi is up, my wife is surfing on it as we speak.

---

### Post by netbookntn on 2009-08-08
> **Thisislaw said:**
> So right now if you open "Windows Wireless Drivers" it will tell you "unable to see if hardware is present". Like it will always say this and you are sure you have no wireless currently? Also try ```
iwconfig
```

lo    no wireless extensions.

pan0 no wireless extensions

---

### Post by netbookntn on 2009-08-08
Double checking drivers here:
I clicked "download" [HERE]("http://www.atheros.cz/download.php?atheros=AR9285&system=2")
I downloaded the whole file, unzipped, put on a thumb, moved to desktop on netbook.
Opened the Windows Wireless tool in Admin, browsed to BOTH of those inf files included and installed from there.

Is there another way to install the drivers?

---

### Post by Vakman on 2009-08-08
> **netbookntn said:**
> Double checking drivers here:
I clicked "download" [HERE]("http://www.atheros.cz/download.php?atheros=AR9285&system=2")
I downloaded the whole file, unzipped, put on a thumb, moved to desktop on netbook.
Opened the Windows Wireless tool in Admin, browsed to BOTH of those inf files included and installed from there.

Is there another way to install the drivers?

Sorry about the long time that took to respond. Yeah, many different ways but this should be so quick and easy. Also, you should not have both .inf files. One is for x64 and other is for x86. So you only need one. And only one would work likely.
Get rid of both and use the x86, if that does not work try this. This is sort of his quote, just modified a line or two.
> **MadHatter21 said:**
> Download and install compatible wireless if that does not work. 

[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) (Choose first one for you)

then Unzip the directory then go into the terminal.

Then get into the directory of the unzipped file and run the following commands.

```

make
sudo make install
sudo make unload

```

after instalation go to etc directory and edit the modules file.

```

cd /etc
sudo gedit modules

```

then add your driver. For myself I have a atheros ar5b95 so I use ath9k. So I would add,

```

ath9k

```

then save and exit. Restart your computer and you should be set. Let ne know how it works.

---

### Post by netbookntn on 2009-08-08
> **Thisislaw said:**
> Sorry about the long time that took to respond. 
[COLOR=Red]No problem dood. I _surely_ appreciate your help. MAYBE this will help someone else along the way.[/COLOR]
Yeah, many different ways but this should be so quick and easy. Also, you should not have both .inf files. One is for x64 and other is for x86. So you only need one. And only one would work likely.
Get rid of both [COLOR=Red](DONE)[/COLOR] and use the x86, if that does not work[COLOR=Red] (DOESN'T work) [/COLOR]try this. This is sort of his quote, just modified a line or two.

I have some questions:
>                      Originally Posted by **MadHatter21**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7744131#post7744131")                 
                 [I]Download and install compatible wireless if that does not work. 


[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) (Choose first one for you)
[COLOR=Red]Do I choose the first one as well?[/COLOR]

then Unzip the directory [COLOR=Red](will do on the desktop pc and put on USB drive)[/COLOR]
 then go into the terminal. 
[COLOR=Red]("go" into the terminal just means go to the terminal prompt..right?)[/COLOR]

Then get into the directory of the unzipped file [COLOR=Red](How does one "go into the directory" of a file on Ubuntu? just go to the terminal and type the code below? make, sudo make...
does that get me to that directory?) [/COLOR]and run the following commands.

     Code:
     make
sudo make install
sudo make unload 
after instalation go to etc directory and edit the modules file.

     Code:
     cd /etc
sudo gedit modules 
then add your driver. For myself I have a atheros ar5b95 so I use ath9k. So I would add,

     Code:
     ath9k 
then save and exit. Restart your computer and you should be set. Let ne know how it works.[/I]
[B][COLOR=Red]
[/COLOR][/B][COLOR=Red]If you can think of anything I might be messing up in just the Ubuntu settings that would cause the wifi to not be "on", please let me know.[/COLOR][B][COLOR=Red]
[/COLOR][/B][CENTER][SIZE=6]**[COLOR=Red]THANK YOU![/COLOR]**
[/SIZE][/CENTER]

---

### Post by Crafty Kisses on 2009-08-09
You can resolve the following error when you're attempting to load the ndiswrapper module:
```
WARNING: All config files need .conf:/etc/modprobe.d/ndiswrapper, it will be ignored in a future release
```
What you can do is run the following in the terminal as root:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
Then try reloading the ndiswrapper module by running:
```
modprobe ndiswrapper
```

---

### Post by netbookntn on 2009-08-09
> **Codename said:**
> You can resolve the following error when you're attempting to load the ndiswrapper module:
```
WARNING: All config files need .conf:/etc/modprobe.d/ndiswrapper, it will be ignored in a future release
```What you can do is run the following in the terminal as root:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```Then try reloading the ndiswrapper module by running:
```
modprobe ndiswrapper
```

Thank you!
What does > run the following in the terminal as root mean? 
Just open terminal and type that? The "as root" part lost me.

---

### Post by netbookntn on 2009-08-09
> **Codename said:**
> You can resolve the following error when you're attempting to load the ndiswrapper module:
```
WARNING: All config files need .conf:/etc/modprobe.d/ndiswrapper, it will be ignored in a future release
```What you can do is run the following in the terminal as root:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
[COLOR=Red]I got "Permission denied".[/COLOR]
 
Sorry if I seem to be the devil's advocate here.
Seems like every suggestion I get from you helpful folks, I shoot down.
Not intentionally....

---

### Post by Crafty Kisses on 2009-08-09
> **netbookntn said:**
> Thank you!
What does  mean? 
Just open terminal and type that? The "as root" part lost me.
You can just run:
```
sudo -i
```
Then once you have done that you can run:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```

---


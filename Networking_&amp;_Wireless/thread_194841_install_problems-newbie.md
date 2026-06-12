---
title: "install problems-newbie"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by alexohara1 on 2006-06-12
hi folks...

im in deep *hit here... ive been trying to get onto a linux platform for months and every time ive seen one advertised on those magazines, id buy it....and try to install it...ive tried red hat, feduro, mandrake and none have happened to install correctly...why ?... i have no idea perhaps hardware confilcts...anyhow i have come across now ubuntu 5.04 and it installed and works great...and im loving it...however im new to the linux enviroment and to unbuntu.... im trying to connect my laptop to the net or even get the laptop to hook up to my xp box...now ive read all the info out there and i still dont now whats happening....my modem has a winmodem lucas driver (i obtained the info from that ModemData.txt, which i installed) now i have some how endedup here 
[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)
for the drivers... now do i have to download them all???i have download a few and put them on a memory stick then onto the laptop and have tried to install them but i notice no change or i get errors is there a step by step guide for beginners or would some be so greatful and take me thru the steps
regards alex

---

### Post by pellgarlic on 2006-06-12
winmodems are a pain in the neck for linux users - they depend quite heavily on windows code to work properly (they are oftened called "controllerless" or "software-controlled"). however, as is the linux way - there are people working on drivers for several winmodems. 

the best place to start is probably here: [http://linmodems.org/](http://linmodems.org/) - check out the "scanModem Tool", which can identify your modem's chipset, making it easier to find the right drivers. also check out: [http://start.at/modem](http://start.at/modem). 

it may take a bit of work to get your modem going. i got my intel 536ep winmodem working with a little bit of tinkering. once you find the right drivers for your modem (although there is a chance there are no drivers available for your modem) you should find instructions for compiling, configuring and installing the modem drivers within the download. (look for a "readme"). 

once you have installed the drivers, you need to set up networking by going into the "system > administration > networking" menu. this will open a dialog. click on the "location" drop-down menu, and enter something here (just a descriptive name - i found that if i didn't do this, the settings i entered next weren't saved). 

now click on the "Modem" icon in the main panel, then the "configure" button. click the "use this device" radio button, then enter the dialup details (phone number, username and password) and click ok. now, still having the modem selected, click on "activate". this will initiate dialup. to disconnect, click "deactivate".

a slightly less cumbersome method of dialling-up, is to install "gnome-ppp". this acts pretty much like the dial-up connection dialog in windows. it's pretty self-explanatory.

---

### Post by alexohara1 on 2006-06-12
thank you for your reply...
i already have been to [http://linmodems.org/](http://linmodems.org/)  and downloaded the tool...
i also went to the other site..thanks...
ok now the modem is working but how i dont know...
i followed the instructions from [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) typed a few things in and whamoooo... tested it and it worked...now im up to this stage as stated below from that site under "Modems supported by Lucent".......

[Since udev rewrites /dev on each boot, and some dialup programs rely on the existence of /dev/modem, you need to have a symlink created on boot (from /dev/ttyLTM0 to /dev/modem). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:]

now i belive this is telling me if i restart the laptop i will lose my connection...so to prevent it i must create this file...ok so if this is correct the way im interpreting it... how do i make a file or not so much the file but how do i get to that directory or create it... when in terminal mode, i only have a desktop folder... i cant seem to go back or even find a directory called /etc/udev/rules.d/10-local.rules  and 10-local.rules is this meant to be a folder or is this the document you must create and save it as .rules ....Any idea on how this section works?

oh... and another funny thing... i went to my site whilst on the linux laptop and it didnt work i only got that apache welcome message, but if i took out the www. then i had access to my site except it looks like my css didnt pick up...now i know its not a mozilla/firefox problem cause lasttime i tested it on a windows box with those browsers it worked...so any idea whats happening...i wrote some pretty heavy code in php at the start of my pages which detects what os and browser type your using then redirects to the correct css sheet so everything forms in place...but i have never tested it on a linux box..WOW...
regards alex

---

### Post by pellgarlic on 2006-06-13
[QUOTE=alexohara1]now i belive this is telling me if i restart the laptop i will lose my connection...so to prevent it i must create this file.[/QUOTE]

not exactly - it just means that some programs that need an internet connection will look for /dev/modem to connect, and if they don't find it, they won't be able to connect. 

a "symlink" is basically the same as a "shortcut" in windows - it just means that accessing /dev/modem (either by the user, or a program) actually accesses the device that it is "symlinked" to.

for example, my modem is installed as "/dev/536ep". so, if a program i use looks for a modem at /dev/modem, i have to make a symlink called /dev/modem which points to /dev/536ep so that when the program talks to /dev/modem, the information is passed on to /dev/536ep. get it?

the symlink has to be created at boot because "udev rewrites /dev on each boot". in other words, if you just create a symlink by hand , the next time you boot, the symlink will be gone, but not your whole modem - just the /dev/modem symlink to your your modem. so you need to make the "/etc/udev/rules.d/10-local.rules" file and insert the relevant lines. sorry, i don't know much about making symlinks, so i can't help you any more than that just now.

[QUOTE=alexohara1]i cant seem to go back or even find a directory called /etc/udev/rules.d/10-local.rules[/QUOTE]

"10-local.rules" is the file you need to create, and it should go in the "/etc/udev/rules.d" directory.

if you are in terminal, typing "cd" or "cd ~" and pressing enter will take you to / (root). now type "ls" to list the contents of your current directory. you should see a directory called "etc". now type "cd /etc/udev/rules.d" and press enter. 

if you are using nautilus (the file browser) you need to keep clicking on the "up" button until you can't go up any more, or double-click on "file system" in the left-hand panel. you should then see the "/etc" directory, along with various other system directories like /var and /usr.

hope that helps a bit.

---

### Post by pellgarlic on 2006-06-13
ah, wait - you said you had installed ubuntu 5.04 - i'm not sure if that uses udev... the instructions about udev symlinks on the page you linked to are notes for **Dapper Drake** (version 6.06). they may not be relevant to version 5.04. [Edit: actually, i'm wrong here - the dapper drake section doesn't encompass the udev bit. sorry. :) ]

i would suggest that if you are still quite near the beginning of setting everything up, that you get the newest version of ubuntu and install that instead. is there a particular reason you went for the 5.04 version?

---

### Post by kozimodo on 2006-08-13
Has anybody had any luck getting Intel 536ep working under AMD64?

---

### Post by alexohara1 on 2006-08-13
thanks for all the help guys...
but i have recieved the latest version 6.06 lts and everythings fine..
i didnt have to set anything up manually which was good. but after fiddling around with installing netbeans5.0 and some other programming utilties i have picked up how the directory structure works and how things go...i can proudly say, i have now advanced to a 3rd day begineer ;) 

only can someone advise me of the strongest software out there for linux..
which is similar to these below:

editplus2
flash
jcreator

ok for jcreator im using eclispe and netbeans(pending on what im doing) but im happy with those...

regards alex

---


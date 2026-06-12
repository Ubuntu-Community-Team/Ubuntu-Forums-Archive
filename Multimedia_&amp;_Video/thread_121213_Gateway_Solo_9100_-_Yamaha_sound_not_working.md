---
title: "Gateway Solo 9100 - Yamaha sound not working"
date: 2006-01-24
forum: Multimedia &amp; Video
---

### Post by PilotEd on 2006-01-24
Greetings...I have Breezy installed and working with the exception of sound.  I've searched the forums and found out that dapper does a wonderful job of detecting sound hardware and getting sound working.  I booted dapper and the sound works beautifully!  How can I get the sound configured under breezy?

Here is a link to the hardware specs for this laptop:
[http://support.gateway.com/s/Mobile/Solo_Series/P91tvd/P91tvdnv.shtml](http://support.gateway.com/s/Mobile/Solo_Series/P91tvd/P91tvdnv.shtml)

Thanks in advance...

---

### Post by christhemonkey on 2006-01-24
load module snd-opl3-sa2
sudo lsmod snd-opl3-sa2

(may have an _ instead of - between snd and opl3 (snd_opl3-sa2))

Then add to /home/your_user_name/.asoundsrc

pcm.opl3-sa2 {
           type hw
           card 0
        }

        ctl.opl3-sa2 {
           type hw
           card 0
        }
Using
sudo gedit ~/.asoundsrc

---

### Post by PilotEd on 2006-01-24
I found a module named snd-opl3sa2.  When I attempt to load the module (modprobe snd-opl3sa2), I get a "no such device" message.

---

### Post by josbak on 2006-02-13
I had to fight this issue with  FC4 on my solo 9100 and here is the issue.

-Alsa for some reason can't find the card even if modprobe is set correctly.
(while this was for fedora, I am sure you can apply this to other distributions)
So you need to:

1-disable sound on boot sound=0 
2-disable the alsa drivers and clear the modorbe.conf
3-Install legacy OSS drivers
4-Use the /usr/lib/oss/bin/soundconf(ig) utility to install the oss YMF715 driver.
5-Make sure the IRQ and ports are configured correctly (the utility provides a primitive UI for this)
6-Use the mixer command line utilities to set the volume
7-Make a call to /usr/lib/oss/bin/soundon in one of the init scripts in /etc
8-Uninstall the system-config-soundcard its useless.

---

### Post by oldfogie on 2006-02-22
[QUOTE=josbak]I had to fight this issue with  FC4 on my solo 9100 and here is the issue.

-Alsa for some reason can't find the card even if modprobe is set correctly.
(while this was for fedora, I am sure you can apply this to other distributions)
So you need to:

1-disable sound on boot sound=0 
2-disable the alsa drivers and clear the modorbe.conf
3-Install legacy OSS drivers
4-Use the /usr/lib/oss/bin/soundconf(ig) utility to install the oss YMF715 driver.
5-Make sure the IRQ and ports are configured correctly (the utility provides a primitive UI for this)
6-Use the mixer command line utilities to set the volume
7-Make a call to /usr/lib/oss/bin/soundon in one of the init scripts in /etc
8-Uninstall the system-config-soundcard its useless.[/QUOTE]
I have the exact same laptop as you PilotEd and I too have the "no sound" issue as well.  Presently I'm using the live CD to test before I go thru install.  But I anticipate that I will have the same issue once installed.  I even tried out Mepis.org's Simply Linux and I had no sound on that live CD either.  this is my first time experimenting with Linux.  Did the fix that josbak work for you?  do you per chance have anything else to add to what he wrote.  I would greatly appreciate your help.  I've been googling all day.  Now it looks like I have to figure out Josbak's greek LOL :D into my M$ brain to make this happen.  Thank you in advance.

---

### Post by PilotEd on 2006-02-28
Thanks for the reply josbak.  I tried Dapper to see if I would have the same problems.  I'm happy to report that Dapper does a wonderful job of legacy hardware detection and I have sound.

oldfogie, I would download Dapper and see if it will meet your needs.

---

### Post by oldfogie on 2006-03-02
Hi all!

Thanks for the info on dapper.  The sound did work however the OS is simply too resource intense for this old laptop.  For my other laptop I'm going to put 1 of the ubuntu's in.

I've had success with sound on Vector Linux; altho it to has some issues for me.  I'm going to try my hand again at the Damn Small Linux.

Here is a post of my goings on w/vector at DSL site where I had posted a request for help; but never got answered :( but is still a work in progress.

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=6;t=11774;](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=6;t=11774;)

Thanks again for the input all; it truly put me on the right path.

-Fogie.

---


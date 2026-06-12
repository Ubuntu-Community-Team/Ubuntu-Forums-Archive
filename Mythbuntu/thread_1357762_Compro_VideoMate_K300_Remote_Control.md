---
title: "Compro VideoMate K300 Remote Control"
date: 2009-12-17
forum: Mythbuntu
---

### Post by tonycollinet on 2009-12-17
Anyone know if one of these will work as a remote control?

Thanks

[http://www.overclockers.co.uk/showproduct.php?prodid=GX-028-CP](http://www.overclockers.co.uk/showproduct.php?prodid=GX-028-CP)

---

### Post by phantom_ on 2010-02-12
i own the exact model and managed to run the commander with LIRC running foreground (it does not work if LIRC is running as daemon, i did not understand why).

i am checking the functionality of the commander with [I]irw.

[/I]however, my goal is to use the commander with XBMC. i failed over XBMC.

anybody using Compro K300 commander with Ubuntu and/or XBMC?

---

### Post by phantom_ on 2010-02-13
here's some progress, i hope this helps some people ;)


[LIST]
[*]LIRC runs Compro K300's IR receiver if the receiver is defined as *Windows Media Center Transceivers/Remotes (all)* while configuring LIRC. you can always reconfigure LIRC by command: *dpkg-reconfigure lirc*.
[*]OS creates */dev/lirc0* file for the USB receiver. you should check if it exists.
[*]since K300 is not a Windows MCE commander, key configuration should be done. LIRC identifies the commander in a cfg. file; */etc/lirc/lircd.conf.*
[*]there is a program named *irrecord* for creating the lircd.conf. you can run it as *irrecord -d /dev/lirc0* */k300.txt*. program is text-based and self explaining. irrecord communicates with the receiver thru /dev/lirc0, and writes the cfg. to /k300.txt in this example.
[*]irrecord allows you to assign commander buttons to preset string. it calls the strings as namespace. it is a good idea to display the list with *irrecord --list-namespace *before start creating the cfg. file
[*]after creating the cfg. file (k300.txt), copy the file as */etc/lirc/lircd.conf*.
[*]after (re)starting the lirc daemon with *service lirc restart*, run the check program *irw* and press the buttons of the commander. if you are successful, you will see the assigned strings after pressing the relevant commander button.
[/LIST]
don't forget to perform the above with root privileges.

i succeeded in running XBMC 9.11 on Ubuntu 9.10 with Compro K300 commander. however, XBMC in particular needs configuration for mapping LIRC output to XBMC actions, and this is another story ;)

finally, LIRC stands for Linux IR Control.

---

### Post by Betelgeuse on 2010-03-15
> **phantom_ said:**
> here's some progress, i hope this helps some people ;)


[LIST]
[*]LIRC runs Compro K300's IR receiver if the receiver is defined as *Windows Media Center Transceivers/Remotes (all)* while configuring LIRC. you can always reconfigure LIRC by command: *dpkg-reconfigure lirc*.
[*]OS creates */dev/lirc0* file for the USB receiver. you should check if it exists.
[*]since K300 is not a Windows MCE commander, key configuration should be done. LIRC identifies the commander in a cfg. file; */etc/lirc/lircd.conf.*
[*]there is a program named *irrecord* for creating the lircd.conf. you can run it as *irrecord -d /dev/lirc0* */k300.txt*. program is text-based and self explaining. irrecord communicates with the receiver thru /dev/lirc0, and writes the cfg. to /k300.txt in this example.
[*]irrecord allows you to assign commander buttons to preset string. it calls the strings as namespace. it is a good idea to display the list with *irrecord --list-namespace *before start creating the cfg. file
[*]after creating the cfg. file (k300.txt), copy the file as */etc/lirc/lircd.conf*.
[*]after (re)starting the lirc daemon with *service lirc restart*, run the check program *irw* and press the buttons of the commander. if you are successful, you will see the assigned strings after pressing the relevant commander button.
[/LIST]
don't forget to perform the above with root privileges.

i succeeded in running XBMC 9.11 on Ubuntu 9.10 with Compro K300 commander. however, XBMC in particular needs configuration for mapping LIRC output to XBMC actions, and this is another story ;)

finally, LIRC stands for Linux IR Control.

Hello,

I'm planning to buy that remote control for use with XBMC on ubuntu. Can you give me the configuration files of this remote for LIRC and XBMC? if oyu paste the configuration files here it'll be realy helpful for us to use that remote easly. 


I have an imon VFD remote now but the remote dropped to floor and there is no visible damage on the remote but the codes that sent from remote to computer changed somehow. I've managed to get the changed codes and entered imon-pad config file but some of the buttons are not working so I'm thinking about buying K300 remote instead because it's cheaper.

---

### Post by cpeachey on 2010-06-08
I have just found this device. It is just what I am looking for to use with Ubuntu+XBMC. Are you guys still using it or is there something better I should look for?
Chris

---

### Post by phantom_ on 2010-06-08
yes, still using the commander. battery life seems good.

---


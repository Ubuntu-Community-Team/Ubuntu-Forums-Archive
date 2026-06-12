---
title: "lirc not working on bootup in mythtv"
date: 2009-09-06
forum: Mythbuntu
---

### Post by davidstoll on 2009-09-06
Every time I reboot my computer, my remote (MCE) does not work.  I have to go into the Mythbuntu Control Centre and disable/enable the IR transmitter or simply change the device to something random and then change it back to what it was.

This happened in 8.04 and still in 9.04.

How can I fix this?
I hope I gave enough info.
I'm a bit of a linux noob, so let me know what (if any) other info you need and where to get it.

Thank you so much!

---

### Post by williammanda on 2009-09-06
When the remote stops working. Do this:

william@C2Q:~$ sudo /etc/init.d/lirc restart
[sudo] password for william: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
william@C2Q:~$ 

If you type in the command and get nothing back then lirc isn't loaded. Also verify that you have the 3 files:

/etc/lirc/lircd.conf
/etc/lirc/hardware.conf
/home/yourusername/.lirc/mythtv

All these files have to have something in them.
Also if you need more help, send me a private message by clicking on my name and we can talk over skype.
Thanks

---

### Post by davidstoll on 2009-09-08
I do have all those files and lirc does restart giving it that command.  However, my problem is that after every reboot, my remote doesn't work in mythtv.  I have to disable and re-enable the ir device in the mythbuntu control pannel.

It's very strange that nobody else has this problem.  It happened in both 8.04 and still now in 9.04.  Back when I first installed MythBuntu, I even reformatted and reinstalled to see if that would fix it, but it didn't and I just live with the annoyance.  Then I thoought it would get fixed with 9.04, but again, no dice.

David



> **williammanda said:**
> When the remote stops working. Do this:

william@C2Q:~$ sudo /etc/init.d/lirc restart
[sudo] password for william: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
william@C2Q:~$ 

If you type in the command and get nothing back then lirc isn't loaded. Also verify that you have the 3 files:

/etc/lirc/lircd.conf
/etc/lirc/hardware.conf
/home/yourusername/.lirc/mythtv

All these files have to have something in them.
Also if you need more help, send me a private message by clicking on my name and we can talk over skype.
Thanks

---

### Post by Neon Dusk on 2009-09-08
Do you have more than 1 lirc device? Have you looked at [thread=892647]this thread[/thread]?

---

### Post by davidstoll on 2009-09-08
Yes, it looks like it is basically the same problem.  Thanks for finding that!

However, udevinfo does not seem to work for me....not only that, but it is a tad over my head...but I'm going to give it a try.  I wonder if my other remote (imon) is working upon startup rather than my MCE remote....hmmm.  I'll check tonight.

But basically, I guess I need help trying to get udevinfo running.  apt-get says I already have udev installed and it is the most current version.

Thank you again for the help!


> **Neon Dusk said:**
> Do you have more than 1 lirc device? Have you looked at [thread=892647]this thread[/thread]?

---

### Post by Neon Dusk on 2009-09-08
If you're running 9.04 I think you need to use udevadm instead of udevinfo. So it would be 
```

sudo udevadm info -a -p $(udevadm info -q path -n /dev/lirc0)
sudo udevadm info -a -p $(udevadm info -q path -n /dev/lirc1)

```

---

### Post by Powderking on 2009-12-25
Hi guys

I have th same problem, but I don't know, if it's because of the same reason. :confused:

ls /dev/lirc* gives me:
```
/dev/lirc0  /dev/lircd
```

I have attached the working configuration files
/etc/lirc/lircd.conf
/etc/lirc/hardware.conf
/home/yourusername/.lirc/mythtv

and the output of ```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/lirc0)
```

I created the file /etc/udev/rules.d/10-local.rules and changed /etc/lirc/hardware.conf but it wasn't successful :(

It would be great, if you could help me too :)

---


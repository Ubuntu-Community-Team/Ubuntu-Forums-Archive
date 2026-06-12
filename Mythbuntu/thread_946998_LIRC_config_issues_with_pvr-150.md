---
title: "LIRC config issues with pvr-150?"
date: 2008-10-13
forum: Mythbuntu
---

### Post by Supermort on 2008-10-13
I'm sorry if this has been addressed somewhere else, but I cant find anything and this has been driving me nuts. 

 I'm using Mythbuntu 8.04 with a Hauppauge pvr-150 and I noticed that some of the buttons on the remote are not linked to any commands in Myth (Prev Chan for example).  The basic buttons (up/down/vol/mute/ok/back) all work fine, and commands to Myth like Prev Chan work fine when using the keyboard.

I checked the /etc/lircd.conf file and the only thing not commented out was:
"include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

I checked that config file and it contains lots of config info for hauppauge remotes but not for the pvr-150, just the 350, wintv etc.

When I add the pvr-150 info (robbed from a example config file like this one: [http://www.pjd.nu/lirc/lircd_pvr150.conf](http://www.pjd.nu/lirc/lircd_pvr150.conf)) and comment out the rest the remote stops working completely after lirc restart.

Is there something I am missing? where exactly is the button mapping coming from, and how can I get the rest of the buttons working? 

Thanks for any help you can offer,

Mort

---

### Post by SiHa on 2008-10-14
Hi Mort.

First, try restoring your **/path/to/lircd.conf.hauppauge** to it's former state.

Then, open a terminal and run```
irw
```

Press buttons on your remote, you should get something like```
0x00001474 00 OK Hauppauge
0x00001473 01 Up Hauppauge
.
etc
.
.

```

Check all the keys.

Ctrl+C to quit from irw

Are your keys recognised?

If not, try the Mute, Vol+ and Vol- when not running Myth. If this controls the system sound then your LIRC is not setup properly and you just have Kernel IR support.

Post back with the results of your irw

Cheers,

Simon

---

### Post by Supermort on 2008-10-14
I make backups of all the config files before I changed anything, all is as it was originally installed now.  I tried irw and the keys were all recognized:

00000000000017a5 00 OK Hauppauge_350
etc..
etc..

All the keys worked and the outputs matched the config files under the section Hauppauge_350 in /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge. Makes sense.

So, the system is using info for a Hauppauge Pvr-350 which may or may not be a big deal, but I still need to tell Myth that keypresses for "blue" for example need to be associated with a given command in Myth.

Thanks for the help so far, it is greatly appreciated.

---

### Post by SiHa on 2008-10-15
> I make backups of all the config files before I changed anything
Always a good idea;)


OK, so LIRC is configured correctly, now you need the mapping file **lircrc** to pass the correct keypresses to Myth.

Check out this thread: [http://ubuntuforums.org/showthread.php?t=937498](http://ubuntuforums.org/showthread.php?t=937498) for how to add to your lircrc file

Also, if you want the arrow keys to send repeat keypresses, you will need to add something like```
repeat = 3
delay = 2

```
so:
```
begin
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 2
    delay = 2
end
```

**'repeat = n'** sends every n'th repeat event, and **'delay = n'** skips n events before it starts counting.

You can play with the numbers, but I've found the above (for me with a NovaT-500, and serial receiver) gives a reasonably quick scroll, but with a bit of a pause so that you don't get accidental double-presses.

Note, quite a few people seem to have a problem (myself included) with Hauppauge cards filtering out repeat events when using the internal IR receiver, so the above **may** not work.

HTH

Simon

---


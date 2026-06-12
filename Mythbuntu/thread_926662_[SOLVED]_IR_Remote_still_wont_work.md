---
title: "[SOLVED] IR Remote still wont work"
date: 2008-09-22
forum: Mythbuntu
---

### Post by MartinusEx on 2008-09-22
Again hi,

With my other post on the DVD prob i have this one as well unresolved:

I'm working on getting the hauppage ir remote to work that came with the nova-s plus.

hardware.conf, lircd.conf and lircrc is all set up
I'm already there that i can test it with **irw** and get the correct messages.

If I switch on the frontend and watch TV (for instance) I cannot get more response than before (Up, Down, Left, Right, OK and the numbers are working, but nothing else)

I tried to teach the system the keys, but when I press one of the buttons I want it tells me "unknown button".

As far as I know lirc tells mythtv (as set up in on of the conf files) which key it shall read if I press a certain button.

No response from mythtv.
One thing I'll have a look on is the spelling in the setup:
program=mythtv
Is it all lower case? or should it be "MythTV"
Any idea around?

Thx a lot in advance.

Martinus

PS: of course after having written this, a solution will come out of the blue, just when I do the same things as ever but suddenly it works. :)

---

### Post by stevanbt on 2008-09-22
Hi,
Please will you post the contents of your config files, the output from ```
ls -l /dev/input/
``` and ```
ls -l /dev/input/by-path
``` and ```
dmesg | grep -i dvb
```

Thanks, Steve.

---

### Post by SiHa on 2008-09-22
Hi Martinus,

If IRW is working then your actual LIRC configuration is good.

I think your .lircrc / lircd.conf link is broken somewhere. Essentially, remote keypressess are interpreted by lircd.conf so you get OK, ArrowUp, ArrowDown etc. Then they are fed into .lircrc to tell LIRC what actual keypresses to pass to the applications. 
**Important** the file should be called **.lircrc **- the '.' is important. It should be located here: ```
/home/<mythtvuser>/.lircrc
```.

Have you tried the auto-generator included with mythbuntu?

```
sudo mythbuntu-lirc-generator
```

This will parse your lircd.conf, and produce an .lircrc for Myth, Xine, Mplayer and a few others. It does rely on having the remote keys having standard names, like 'ArrowUp' instead of 'Up', but if you're using one of the predefined configs you should be OK.

If just the above doesn't fix it then can you post:
1) Your **lircd.conf**.
2) The actual configuration it points to if lircd.conf just consists of an include statement, **eg: /usr/share/lirc/remotes/hauppauge/hauppauge.conf**
3) Your **/home/<mythtvuser>/.lircrc**, 
4) Your **/home/<mythtvuser>/.lirc/mythtv**

Substituting <mythtvuser> for the user logged in when mythtv is running, of course.

**NB** After making any changes to LIRC, Mythfrontend must be restarted, and it's generally safer to restart LIRC as well:
```
sudo /etc/init.d/lirc restart
```

---

### Post by MartinusEx on 2008-09-22
Hi Steve and SiHa,

thanks for your inputs.
in fact .lircd and the files in .lirc where generated that way but it did not work and so i tweaked around until i had it running up to the point that irw responded.

Following SiHa's rules and using the generator made work throughout the system.

Now I'll try to find out what made the difference.

thx a lot again

Martinus

---


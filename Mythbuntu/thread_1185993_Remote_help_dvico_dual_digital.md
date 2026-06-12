---
title: "Remote help dvico dual digital"
date: 2009-06-12
forum: Mythbuntu
---

### Post by spleblem on 2009-06-12
hey guys
i have just finished building and still trying to set up my new media pc running mythbunutu 9.04, with a dvico dual digital 4 rev2 non-MCE remote.
looks like this
[http://lirc.sourceforge.net/remotes/...sionRemote.jpg](http://lirc.sourceforge.net/remotes/...sionRemote.jpg)
i have got the tuner to work, but can't get the remote to work.

I have looked at every post and tutorial and still cannot get it to work


please any help would be great
thanks

---

### Post by nasha on 2009-06-13
Have you looked here?
[HTML]http://ubuntuforums.org/showthread.php?t=616103[/HTML]

If you've followed that guide, and still no luck:

I use this card myself, and have succesfully set it up many times for other people using this guide. However, i seem to experience dropouts with my IR, sometimes it's loaded into the kernel at boot, othertimes its not even recognised.
Take a look at the output of 'dmesg | grep DVB' minus the quotes, you should find something like "input: IR-receiver inside an USB DVB receiver as /class/input/input6".

If you don't then your suffering a problem i've seen from many of these cards. I don't know  why it does it, and i've yet to find a solution :/

---

### Post by spleblem on 2009-06-14
ok im using that tutorial
would you please be able to explain these lines
```

tar xvjf lircx.tar.bz2

cd lircx

sudo cp -R lirc /etc

Install the basic lircrc config for mythtv

mv /etc/lirc/lircrc ~/.mythtv

ln -s ~/.mythtv/lircrc ~/.lircrc

sudo ln -s ~/.mythtv/lircrc /etc

sudo ln -s ~/.mythtv/lircrc /etc/lirc
```

i do get the something like "input: IR-receiver inside an USB DVB receiver as /class/input/input6".
and when i choose input6 in "dpkg-reconfigure lirc"
i can "irw" and get input from the remote
though i cant these inputs to work in mythtv
so if you would be able to explain what is happening in these line as i have problems with files/folders not being found
thanks for any help

---

### Post by nasha on 2009-06-14
```
download attached lirc1.tar.bz2 if you remote look like this

and download lirc2.tar.bz2 if you remote looks like this

replace lircx with lirc1 or lirc2 in terminal type

tar xvjf lircx.tar.bz2

```

You need to download the lirc1 or lirc2 file depending on what your remote looks like. lircx refers to whicgever version you download. Everything should work from there

The .lircrc file withing the bz2 file is what MythTV requires to recieve input from the remote.

Best of luck!

---

### Post by spleblem on 2009-06-15
i have followed the instructions down to the last detail
though when i try "irw" and press buttons nothing happens

any ideas?
thanks

---

### Post by nasha on 2009-06-15
you said earlier you were getting  input from irw....
What has changed? Downloading and installing that file shouldnt have effected the way irw operates, its merely a config file forlirc to communicate with mythtv.

Im afraid i cant offer much more help as i know nothing about the problems your experiencing, or whats causing it. Installing this remote is 5min task, with not much to go wrong. Retrace your steps. If all else fails, check your logs to try and find ut whats happening

---

### Post by spleblem on 2009-06-16
yea before i was getting and input now after following those instructions now im now
i also noticed im getting this error
when i type
/etc/init.d/lirc restart
is says
104: Can't open /etc/lirc/hardware.conf

i look there and the file is there and i can open it not sure why this is happening

---

### Post by nasha on 2009-06-16
Just to double check, your running 'sudo /etc/init.d/lirc restart' yes?
Have you in anyway modified your hardware.conf?
As i said, installing that one file shouldnt have effected the operation of anything other than buttnos in mythtv.

You sure you havent changed something else? Delete the hardware.conf and create a new one, copying the contents from the earlier posted link.
I'm about to reinstall a machine with the DD4, so if i encounter any issues i need to overcome, ill post back here. You using Jaunty?

---

### Post by spleblem on 2009-06-16
yea im using jaunty
nope i have done nothing else than what the it said in the link you gave me under remote.
using the hardware.conf file in the download from that site
is there a way to start again without reinstalling the os
as i have previously mucked around with many of these files following instructions from many sites to get this to work.
maybe if you could make a list of the locations of all the files
i could delete them and start over
thanks for your help so far

---

### Post by nasha on 2009-06-16
All required files are located in that post. There should be no need for a reinstall, i cant see that changing anything.

I'm probaby not the best persson to troubleshoot  this issue as my lirc knowledge is limited, but i'll help out where i can.

Does /dev/input/irremote exist?
Also take a look at the lirc logs in /var/log/

---

### Post by spleblem on 2009-06-16
yes /dev/input/irremote does exist.
i also opened the hardware file and noticed that it had something pointing to lircd.conf located at /etc/lircd/lircd.conf
so i made that folder and placed it there
as i stated before can you please make me a list of the file locations for these files such a hardware.conf lircd.cond .....
i know all the files are in the post above but i cant understand what is being typed into command and what is happening and it would be easy for me to go through and look if i new where everything was meant to be located.
as i am new to linux and still getting use to using the terminal and commands for this.

thanks so much for your help so far

---

### Post by spleblem on 2009-06-22
sorry for double posting, not sure if thats allowed on this forum or not
but i haven't had a reply in awhile
i am still getting the error when trying to 
'sudo /etc/init.d/lirc restart'
i get
104: Can't open /etc/lirc/hardware.conf

anyone know what could be causing this?

---

### Post by spleblem on 2009-06-25
finally got the remote sort of working at least
i followed this instructions 
[http://ubuntuforums.org/showthread.php?t=616103&page=15](http://ubuntuforums.org/showthread.php?t=616103&page=15)
though i know now if i do a restart the event numbers will change how do i fix this?
also the volume doesn't work and non of the buttons working while playing avi's in mplayer
anyhelp would be good thanks.

---


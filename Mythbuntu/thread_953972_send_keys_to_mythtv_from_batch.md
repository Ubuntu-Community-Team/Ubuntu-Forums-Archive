---
title: "send keys to mythtv from batch"
date: 2008-10-20
forum: Mythbuntu
---

### Post by lmclaren on 2008-10-20
Hi,
As the title says, can anyone suggest how to send a key stroke to the mythfrontend from a shell script.
I am using Mythbuntu 8.10


thanks

Lee McLaren

---

### Post by ian dobson on 2008-10-21
Hi,

Maybe this might help [http://ubuntuforums.org/showthread.php?t=45172](http://ubuntuforums.org/showthread.php?t=45172)

Regards
Ian Dobson

---

### Post by lmclaren on 2008-10-21
Thanks Ian,

Not sure thats going to work with Mythbuntu as the WM is different but I will give it a try tonight to see.

regards

Lee McLaren

---

### Post by ian dobson on 2008-10-21
Hi,

Your right, you'll need to use "dbus-send". I've not played with it myself but it should do what you want.

Regards
Ian Dobson

---

### Post by mrand on 2008-10-21
> **lmclaren said:**
> Hi,
As the title says, can anyone suggest how to send a key stroke to the mythfrontend from a shell script.
I am using Mythbuntu 8.10

thanks

Lee McLaren

mythfrontend has a telnet interface that is designed to do exactly that.

Check out any of the following links:

[http://code.google.com/p/rocketremote/](http://code.google.com/p/rocketremote/)
[http://www.mythtv.co.nz/mythtv/?s=virtual](http://www.mythtv.co.nz/mythtv/?s=virtual) - Myth Web Virtual Remote
[http://www.legatissimo.info/node/355](http://www.legatissimo.info/node/355) - iphone remote control
[http://svn.mythtv.org/trac/changeset/17645](http://svn.mythtv.org/trac/changeset/17645) - tkmythremote 

See also: mymote, mythetomer, mythRemote, and Remote Remote (for Apple). 

[http://www.mythtv.org/wiki/index.php/Telnet_socket](http://www.mythtv.org/wiki/index.php/Telnet_socket) has some useful info and links as well.

Have fun,
[INDENT]Marc[/INDENT]

---

### Post by lmclaren on 2008-10-21
Thanks Marc and Ian,

I was coming to the telnet conclusion my self, intend to use netcat to send the key strokes.

thanks

Lee McLaren

---


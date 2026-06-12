---
title: "ubuntu + mythtv - wierd remote control problems"
date: 2011-02-24
forum: Multimedia Software
---

### Post by farmershort on 2011-02-24
Hi All,

First off, I should say that I've spent a good few days trying to google and .conf file my way round this problem - but with no success.

Second off... I confess I'm fairly new to linux. That said, I'm working on installing CentOS and bacula at work at the moment, so I'm getting plenty of practice.

so, I have managed to get a mythtv + ubuntu 10.10 +hauppauge nova-td-500 V3.0 card setup and working. I can receive tv fine, but haven't tested much else yet. I'm using EIT for the EPG.

My next job is to get the working properly. I have been following this guide:

[http://www.acaciaclose.co.uk/31338/138355.html](http://www.acaciaclose.co.uk/31338/138355.html)

and have gotten to this point:

> 
Check Remote Works
Open 1 terminal and run this command as root
#/usr/sbin/lircd -H dev/input -d /dev/input/event2 -n

Open a second terminal and issue this command
>irw

Now press the keys on your remote and check that the output in the irw window is as it should be. ie right names to the right keys. 
Everything displays correctly in the terminal window - correct key press names, etc. I've also made sure that these names match up with my ~/.mythtv/lircrc file

For some reason, Mythtv  *still* wont register the advanced functions of the remote. the number buttons, and the arrow buttons work fine, but the EPG button, menu button, channel-up, channel-down, etc etc - won't work.

I am assuming that those functions of the remote that *do* work, must be coded in somewhere, but I have no idea where, and no idea how to change them!

The next part of the guide talks about yast. yast is not on ubuntu 10.10.... I don't know whether that step is needed on my system, and if it is, how else I should do it.

Clearly, I've skipped ahead a little bit, as I have configured my lircrc file, which is later on in that guide, but I wanted to show you that the test above is the last known working point.

Any help you could give me would be great!

Thanks

Adam

---

### Post by farmershort on 2011-02-25
If I've posted this in the wrong sub-forum, please let me know... I'm very very new to *nix forums.

---


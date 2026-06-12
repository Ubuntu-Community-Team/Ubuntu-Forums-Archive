---
title: "Getting remote control to start Mythbuntu"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by scweston on 2008-01-03
Hi,

I'm trying to get my remote control's power button to start the mythbuntu frontend. I seem to have my Hauppauge Nova-T 500 remote set up and working in mythtv itself, but I think the problem lies in how i'm setting up the irexec daemon (which I understand is necessary to start an application when on the desktop).

This is what i've done.... please if anyone could suggest where i've gone wrong or propose a different method, please do so. I haven't seen a proper 'How To' on this so i've kinda got little bits from various threads.

1-  First I edited the /etc/rc.local file to include the line: 

```
/usr/bin/irexec -d /home/mythtv/.lircrc
```

2- I edited the /home/mythtv/.lircrc file to include the following lines: 
```

#	Start MythTV from Desktop
begin
prog = irexec
button = Power
config = /usr/bin/mythfrontend
end
```

I then restarted the computer (not sure if this in entirely necessary, but just do it to be on the safe side), but the computer doesn't seem to respond to pressing the 'Power' button.

I would really appreciate the help from anybody in a similar situation and trying to figure this out or from anybody who actually knows what they're doing (i've been messing around with ubuntu a while now, but still consider myself a noobie).

Stephen

FYI - Using ubuntu 7.10 Gutsy (amd64)

Also, my appoligies for the accidental duplication of this thread!

---

### Post by scweston on 2008-01-03
Hi, I have some more information.

If I run irexec manually it seems to function correctly.. here's what I typed into a terminal: 

```
stephen@stephen-desktop:~$ sudo killall irexec
[sudo] password for stephen:
stephen@stephen-desktop:~$ sudo irexec -d /home/mythtv/.lircrc

```

But, I really don't want to be starting it manually like this. I want it to just work after starting up ubuntu.

Any suggestions?

Stephen

---

### Post by Awperator on 2008-03-14
Sorry to revive an old thread but I have the same problem and I would like to see if someone has been able to solve it. Thanks

---


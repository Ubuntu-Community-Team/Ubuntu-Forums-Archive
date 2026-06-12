---
title: "Dell Mini 1012 Digital TV Reciever not accessible/detectable"
date: 2011-06-02
forum: Multimedia Software
---

### Post by simonedge on 2011-06-02
I've followed various guides and walkthroughs and read more widely scatttered forum posts than I can count, and have got a bit lost.

It should - as far as I can tell [SIZE=1](which, admittedly, isn't all that far)[/SIZE] - work. It doesn't.

Here's what I have - 

lsusb shows
```
Bus 001 Device 004: ID 2040:2011 Hauppauge WinTV MiniCard [Dell Digital TV Receiver]
```

sudo lsmod shows these two with 'dvb' in their names
```

...
smsdvb                 18093  0 
...
dvb_core               90587  1 smsdvb
...

```

When I follow instructions about watching DVB-t in the program of your choice, I get as far as 

```
simon@haveblue:~$ scan /usr/share/doc/dvb-apps/examples/scan/dvb-t/uk-EmleyMoor -o zap | tee ~/channels.conf
scanning /usr/share/doc/dvb-apps/examples/scan/dvb-t/uk-EmleyMoor
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```

there is, as it says, no /dev/dvb/, so what am I missing?

---


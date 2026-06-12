---
title: "Hauppauge Nova-T-500 remote buttons"
date: 2007-11-12
forum: Mythbuntu
---

### Post by ColdBeer on 2007-11-12
I found the same problem when updated my system to 7.10, so majority of the remote buttons don't work :-(

You could make every buttons work with lirc just with some work:

Check your dmesg and find a line like this:

```
input: IR-receiver inside an USB DVB receiver as /class/input/input4
```

Take note of the number of the input taken by the receiver (don't worry so much, at least in my case, it doesn't change everyday).

Edit your hardware.conf:

```
sudo gedit /etc/lirc/hardware.conf
```

and modify the line:

```
DEVICE=""
```
in this way:
```
DEVICE="/dev/input/event4"
```

Remember to write the right number of the event with the number you wrote for the input. I'm not sure if 'events' and 'inputs' are the same in every case, if not, I'll agree you correct me and explain the way it works.

Now, you just need to restart lirc and check if it works:

```
DEVICE=user@machine:~$ sudo /etc/init.d/lirc restart
Stopping lirc daemon: lircmd lircd.
Starting lirc daemon: lircd.
user@machine:~$ irw
0000000000010162 00 Go NOVA-T500
0000000000010179 00 TV NOVA-T500
0000000000010073 00 VolumeUp NOVA-T500
0000000000010193 00 ChannelDown NOVA-T500
00000000000100cf 00 Play NOVA-T500
0000000000010002 00 1 NOVA-T500
00000000000100cf 00 Play NOVA-T500
0000000000010029 00 # NOVA-T500
000000000001018e 00 Red NOVA-T500
0000000000010191 00 Blue NOVA-T500
0000000000010190 00 Yellow NOVA-T500
```

I wish you could resolv the buttons trouble quickly.

PD: Sorry for my horrible English :KS

---

### Post by daemonk on 2007-11-13
Hi,

Not sure if this will help you, but last night I was having issues with my remote and only the number and the arrow buttons were working.

The issue that I had was that I copy and pasted the lirc config into the files. so I did a dos2unix on all the config files and the other buttons now work.

Thanks
Brent

---


---
title: "MythTV, Lirc and IguanaIR"
date: 2010-03-08
forum: Mythbuntu
---

### Post by Zack McCool on 2010-03-08
All right, I am having a horrible time getting this set to work.  I have MythBuntu 9.10 running, and I purchased an IguanaIR USB to allow me to use my remote control.  I have a Hauppage remote, and a proper conf for it.

iguanaIR loads OK, and if I run igclient I can see all of the remote codes being sent, so hardware works.

lirc loads OK, but if I run irw, I see nothing.  So, something is wrong here.  To complicate matters, if I stop lirc and run lircd -H iguanaIR, I see all the codes passing nicely, like this:

```

0000000000001795 00 Down Hauppauge_350
0000000000001795 01 Down Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001797 01 Right Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 01 Left Hauppauge_350
00000000000017ae 00 Green Hauppauge_350
00000000000017ae 01 Green Hauppauge_350
00000000000017a9 00 Blue Hauppauge_350
00000000000017a9 01 Blue Hauppauge_350
00000000000017b8 00 Yellow Hauppauge_350
00000000000017b8 01 Yellow Hauppauge_350
000000000000178b 00 Red Hauppauge_350
000000000000178b 01 Red Hauppauge_350

```

So, again, iguanaIR is good, lirc config is wrong, somewhere.

Also, when running lircd, as above, I don't get any control in Myth, so I am assuming that something is missing there, too.

So, here are my configs.  I'll include lircd.conf, hardware.conf, and lircrc.  If there's any other files that might help, let me know, and I'll put them right up.

I don't get any errors when running myth, or when running irw, I just don't get any control.

ANY help would be wildly appreciated!

Thanks,
Joe

---

### Post by Zack McCool on 2010-03-13
All right.  First problem is solved.  Adding 

```

REMOTE_LIRCD_ARGS="-H iguanair"

```

to hardware.conf solved the irw issue.  Now I am seeing all of my codes in irw.

On to the next part, being Myth.  I'll work on that tomorrow night, and see if I can finally get it to recognize my remote.  Anyone have any tips?

---


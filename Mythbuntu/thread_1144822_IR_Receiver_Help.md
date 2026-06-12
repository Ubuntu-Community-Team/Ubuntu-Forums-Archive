---
title: "IR Receiver Help"
date: 2009-05-01
forum: Mythbuntu
---

### Post by prof3205 on 2009-05-01
Good Evening All,

I'm trying to build a Mythbuntu box and I have installed a WinTV PVR-150 card that a friend gave me. The card came with a MCE RC6 remote, but no IR receiver. So, and I don't think this will work but what the hell, I went out and bought a generic USB IR made by Cables Unlimited (IrDA) receiver just to make sure.

Anyway, during the Myth install it asks for the remote control and the IR receiver. The options are somewhat confusing, so I selected WinTV PC Card for the remote, but I have no idea what to select for the receiver (there is a WinTV PVR150 option).

Any help ... first, will this work? and if so which settings should I use? And, second, if not, what is a good inexpensive IR receiver to buy and use.

Thanks in advance.

---

### Post by bhampton on 2009-05-01
Hi,

I'm a total newb but I would exit Myth and right click and choose "terminal here" and type 

lsusb

to find out what the system identifies the IR Receiver as.

That's where I would start. It it shows up as something supported you can choose that from within Myth and then go back to terminal and type

irw

Which will let you see it it gets commands send by your remote.

If you get that far... you would then likely need to edit lirc configuration files and you will be all set.

-Brian

---

### Post by AlecJ on 2009-05-01
> **prof3205 said:**
> Good Evening All,

I'm trying to build a Mythbuntu box and I have installed a WinTV PVR-150 card that a friend gave me. The card came with a MCE RC6 remote, but no IR receiver. So, and I don't think this will work but what the hell, I went out and bought a generic USB IR made by Cables Unlimited (IrDA) receiver just to make sure.

Anyway, during the Myth install it asks for the remote control and the IR receiver. The options are somewhat confusing, so I selected WinTV PC Card for the remote, but I have no idea what to select for the receiver (there is a WinTV PVR150 option).

Any help ... first, will this work? and if so which settings should I use? And, second, if not, what is a good inexpensive IR receiver to buy and use.

Thanks in advance.

You should select Microsoft MCE New remote.
I use the RC6 you can get a copy of my files here, just change hardware.conf to suit your reported IR receiver.
[http://ubuntuforums.org/showthread.php?t=1133689](http://ubuntuforums.org/showthread.php?t=1133689)

---

### Post by prof3205 on 2009-05-02
Thanks, I'll try working on it.

I just ran the "lsusb" on the computer and the result I get for the IR receiver is:

Bus 002 Device 002: ID9710:7780 MosChip Semiconductor MS7780 4MBPS Fast IRDA Adapter

It looks like the OS spots the IR receiver, but do you think it can be configured to receive the signals from the remote and pass them along.

Any ideas?

Again, your help is greatly appreciated.

---

### Post by bhampton on 2009-05-02
Hi,

I've only been using Mythbuntu for about a week but I did go a few rounds with configuring lirc.

It's great that you got info from the isusb and you had no trouble getting to terminal and running it.

You may want to check out the online lirc config tool...

[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

Seems like a great resource although I wasn't able to get it to help me with my particular config. I just thought I would share it because it looks like someone put a lot of energy into helping with this particular problem.

-Brian

---

### Post by AlecJ on 2009-05-02
> **prof3205 said:**
> Thanks, I'll try working on it.

I just ran the "lsusb" on the computer and the result I get for the IR receiver is:

Bus 002 Device 002: ID9710:7780 MosChip Semiconductor MS7780 4MBPS Fast IRDA Adapter

It looks like the OS spots the IR receiver, but do you think it can be configured to receive the signals from the remote and pass them along.

Any ideas?

Again, your help is greatly appreciated.

hardware.conf is the file you need to look at, this is where the modules and lirc.conf files are loaded. It should be just a case of telling it what module to load for the IR receiver and which lirc.conf file.
could you post up your /etc/lirc/hardware.conf
and the ouput of 
```
dmesg | grep usb
```

---


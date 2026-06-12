---
title: "netgear wireless"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by ckh1 on 2009-03-19
I just installed ubuntu 8.10 on my old dell inspiron 2650, and it actually works!
Now...how do i get my Netgear 54Mbps Wireless PC card (WG511v2)
to work?
I tried using the netgear resource cd but no luck. 
magic fairy dust? or maybe the puss from a rabid horny toad found in the swamp over yonder? or maybe from the witches newt in The Holy Grail?
anyway...thanks for the help in advance.

---

### Post by pytheas22 on 2009-03-20
There are instructions [here]("http://elehmann.wordpress.com/2006/12/23/netgear-wg511v2-wlan-card-on-ubuntu-edgy/") for making your card work on Ubuntu.  They're a bit old, but should still work on Ubuntu 8.10.  Please give them a try.

If they don't work or they're too hard to follow (which is understandable if you're totally new to Linux), let me know and I'll give you more specific instructions.  In that case, please post the output of this command:
```

lspci -nn
```

so that I can figure out exactly which kind of wireles card you have.

---

### Post by ckh1 on 2009-03-20
yeah, I am coming from windows where you don't need to know much and everything is point and click.I need to have my hand held through all of this please. More specific instructions.

my card is Netgear 54Mbps Wireless PC Card WG511 v2

thanks

---

### Post by pytheas22 on 2009-03-20
No problem, I'll provide more specific instructions, but please first open a terminal from the Applications>Accessories menu, run these commands and copy the output here:
```

lspci -nn
uname -rm
```

If I have that information, there won't be any guesswork involved in writing instructions for you.

---

### Post by ckh1 on 2009-03-21
OK!
I have the latest version of ndiswrapper installed in ubuntu...now what?
Atleast I think I have it installed

linux/ubuntu is difficult coming from windows...

---

### Post by pytheas22 on 2009-03-21
Now you need to load the Windows driver into ndiswrapper.  I will tell you exactly how to do that, but first I need you to open a terminal, run these two commands and copy the output here:
```

lspci -nn
uname -rm
```

I need that information before I can tell you what to do next.

---

### Post by ckh1 on 2009-03-21
found out that the "windows driver- 3Com..." is NOT activated.
The netgear driver is activated. I have the netgear cd.
the netgear driver is wg511v2.
I downloaded all the netgear files for the drivers.
on the netgear disk I can see the driver file WG511v2.INF


From the netgear disk I try and run setup.exe and or autorun.exe and for both I get a GConf error.

wouldn't it just be too easy if I could stick the netgear disk in and it all works, like it does in windows???


now what?

---

### Post by pytheas22 on 2009-03-21
You have to install the WG511v2.INF file into ndiswrapper with a command like this:
```

sudo ndiswrapper -i /path/to/WG511v2.INF
```

Then run this command so that ndiswrapper loads at boot:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

Finally, reboot and your device should work.

Don't run the Setup.exe file; it won't make your card work, even if the installer appears to complete successfully.

---

### Post by ckh1 on 2009-03-23
I went to the add/remove application in ubuntu and added ndiswrapper, successfully. then I went to the windows driver and installed the netgear driver, successfully. Ir said that it was present and active. I went to the terminal and wrote in the echo command, successfully. Now attempting to reboot...
so far so good. we'll see if it wants to reboot this time.
I am using the live cd session.
How will I be able to get my files and folders from windows to ubuntu?

---

### Post by ckh1 on 2009-03-23
okay...so i finally got it rebooted using the live cd after 5 or 6 tries.
an nothing was there as far as what I had installed before i logged out/in.
I re-did everything and my wireless card is actually blinking!!!!! green.
now what?
sorry for being so clueless. Thanks for your patience and help.

---

### Post by pytheas22 on 2009-03-23
> okay...so i finally got it rebooted using the live cd after 5 or 6 tries.
an nothing was there as far as what I had installed before i logged out/in.

Did you actually install Ubuntu to hard disk?  Or are you working from the live CD?  If you're running from the live CD, any changes you make will be forgotten forever when you reboot the computer--that's how the live CD works.

If you have Ubuntu installed to hard disk but are still having to reinstall ndiswrapper after each reboot, try running this command once; it will hopefully fix it:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

---


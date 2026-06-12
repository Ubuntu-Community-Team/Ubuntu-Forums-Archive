---
title: "HandbrakeCLI causing shutdowns"
date: 2011-12-18
forum: Mythbuntu
---

### Post by benherman on 2011-12-18
Running mythbuntu 11.04 64bit installed Handbrakecli and attempting to rip a dvd to mkv.

After running for a few minutes the pc shuts down with this message:

Encoding: task 1 of 1, 4.85 % (33.24 fps, avg 35.42 fps, ETA 01h02m10s)
Broadcast message from root@mythtv
    (unknown) at 16:44 ...

The system is going down for power off NOW!

The BIOS is set to shut down if temps get to hot, but I don't see it getting hot so fast.
this is a brand new build with a core i3.

I am going to attempt the conversion again tonight while running acpi -t to see just how high the temps go.

If the bios is in fact shutting the machine down, is there a log anywhere that will tell this? Or tell if I am in fact shutting down due to heat?

Thanks for your help

---

### Post by benherman on 2011-12-18
Just attempted this again, started out at 

Thermal 0: ok, 28.0 degrees C
after starting handbrake within a minute or so I had hit:

Thermal 0: ok, 54.0 degrees C

The box shuts down at 65C so I know that's the deal. I'm thinking that the fan isn't kicking in enough or the stock heat sink has come loose. Damn pins. 

The computer is at another location so I will have to check the heat sink tomorrow, if anyone else has any input it would be appreciated.

---

### Post by ian dobson on 2011-12-19
Hi,

100% temperature related. 

What heatsink are you using? 
What happens if you limit handbrake to only using 1/2 your cores?
Does the case have enough cooling?

Regards
Ian Dobson

---


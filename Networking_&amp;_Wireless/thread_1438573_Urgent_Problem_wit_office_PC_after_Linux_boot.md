---
title: "Urgent: Problem wit office PC after Linux boot"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by Gegenzeit on 2010-03-25
Hi,

I have made myself a bootable Ubuntu 9.1-USB-stick the other night. Then I had the brilliant idea to run a test on our office pc. Everything worked fine, but:

Since I rebooted to Windows, the network connection doesn't work anymore. 
The network symbol in the Windows task bar has a red X to it. If I got to the network control center, it says that the network cable was removed. 

What I've done so far:


- deactivated and reactivated the network connection
- removed and replugged all cables
- restarted the switch the pc is connected to
- rebooted the system multiple times
- compared the settings of the LAN-connection to the settings on the other pc's in the network (no difference:  IP is determined by DHCP automatically on all computers). 
- checked the device manager. No problems or missing drivers there. 

I also rebooted in Ubuntu - in Ubuntu everything is fine -  the network works. 

Any help would be greatly appreciated (It is the only pc the whole office crew works on - additionally: It is our pc for client presentations).

Jörg

---

### Post by Gegenzeit on 2010-03-25
More things I've done:

- rebooted in Ubuntu and compared the settings there with the settings in Windows (they   
  are the same - Ip is given automatically by DHCP)
- Looked up my IP-Adress when online with Ubuntu and tried entered it manually in  
  Windows - no success
- Disabled my onboard 10/100 Mb Lan card. No success.
- Tried different duplex modes, no success
- Tried to Restore my system to: yesterday 1 pm; Windows failed to do it

I'm running out of ideas ...

---

### Post by Dayofswords on 2010-03-25
walk over to the IT department

explain to them, "the internets, they have stopped"


ok seriously:
talk to the office IT, they are there for a reason

[SIZE="1"]
(i'm not helpful)[/SIZE]

---

### Post by byStanderone on 2010-03-25
...i think there is an option in windows, internet connection if i recall correctly...try repair network connection. review your control panel.

---

### Post by Cabalbl4 on 2010-03-25
1) Is the rx/tx led on card flashing as usual? Maybe a hardware problem? 
2) Are You sure that the cable is "not connected" and there is no problem of IP assignment e.t.c.?

When I first installed ubuntu, I have experienced network problems too. I spent 2 days trying to fix them. They were resolved only by removing dust from LAN card )))

---

### Post by Gegenzeit on 2010-03-25
- The light at the back is not flashing. 

- The hardware works perfectly under Ubuntu. The problem appears just under Windows.   
   So I guess it's not the hardware.

- Do not overestmate the size of our office ;) We are 4 people and the "It-departement" is 
  me and one colleague trying to keep everything up & running.



One more thing we (my colleague is here now too) tried, is to deinstall the network card and reboot. The card reinstalled itself, but it still says the cable was removed. 

Thanks for any advice on this!

Jörg


EDIT: I do not believe it is a problem of IP-assignement. The IP is given automatically, and until this morning everything had worked fine.

---

### Post by Cabalbl4 on 2010-03-25
So... if the LED is not flasing... The only thing I can think of is a driver. Maybe reinstalling/updating it can help. 
You can also try to reset winsock (maybe this can help) by running ```
netsh winsock reset
``` in term... command window. :D

---

### Post by Gegenzeit on 2010-03-25
restting winsock did not help either. hmmm...

---

### Post by matchett808 on 2010-03-25
try another cat5 cable, those things seem to die on me all the time....

---

### Post by Gegenzeit on 2010-03-25
> **matchett808 said:**
> try another cat5 cable, those things seem to die on me all the time....
 
But it works under Ubuntu ;)

---

### Post by Cabalbl4 on 2010-03-25
I am out of ideas... maybe some options within the driver (in hardware list there is usually a tab where device options are listed) are setting the card off.

Main thing is that (as You say) the LED is not working. This means that the card is disabled in windows (NOT a cable problem, if it works with ubuntu)
This can be due to:
- driver (it is somehow set to off)
- bios (some settings wrong)
- something within windows (an evil hand of MS disabling Your LAN because of ubuntu :D ) I just do not know what :-k

The last thing I can suggest is reinstalling windows...

---

### Post by new_tolinux on 2010-03-25
I guess it has nothing to do with Ubuntu at all.

Should be helpfull to know what windows-version you are using.

---

### Post by Gegenzeit on 2010-03-25
It's Windows Vista.

---

### Post by insecureboy on 2010-03-25
first i'd recommend u boot into ubuntu and backup ur files.

since u can connect on ubuntu ur problem is clearly software problem in Windows 

it may be a bug or it may be the case that ur NIC is old and vista didnot exist at the time of its creation and u have XP drivers running under some compatibility layer ( driver compatibility is a very common problem in vista )

tell me the model of ur NIC

and also do u have a router and all PC's connected to it ???

<<< or do u have one PC(I assume windows) online and have shared the network connection to other computers connected w/ a switch ( in this case, i assume you did the "setup home or office network wizard" in windows)


give me these info i may be able to help

---


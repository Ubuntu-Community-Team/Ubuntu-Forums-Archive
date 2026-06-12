---
title: "Troubleshooting a network printer--completely lost"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by litlfrog on 2009-05-10
I've done a tiny bit with Samba, but have no experience with networked printers. There's an HP Business Inkjet 2200 in our office. I'm trying to print to it today, but while I don't see any errors, nothing's printing either. When I go to System -> Administration -> Printing, I think I see the printer I need, but the Device URl is listed as file:///dev/null. I click the "Change . . ." button, look under "Network Printer," and see HP Business Inkjet 2200. That shows a listing of IPP Printer and next to "Host" it lists 192.168.107.254:631. However, a coworker shows a completely different internal IP address for the printer I'm trying to use. I'm really stumped and don't know what to check from here.

---

### Post by chili555 on 2009-05-10
> 192.168.107.254:631And when you try to add this as an IPP protocol printer, does it print?

This may be helpful:  [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_2200](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_2200)

---

### Post by litlfrog on 2009-05-10
I tried adding that as an IPP printer. When I clicked 'Verify,' I get an error saying "This print share is not accessible."

---

### Post by chili555 on 2009-05-10
> a coworker shows a completely different internal IP address for the printer I'm trying to use.I think I might try using the co-worker's URI in the setup for IPP printers. It should be *approximately*:```
ipp://192.what.ever.blah:631/printers/HP_2200
```

---

### Post by litlfrog on 2009-05-10
OK, I tried adding the printer that way. The icon shows up with a green checkmark in the printer configuration window, but the Printer State under properties lists "Stopped! unable to locate printer 'ipp'

---

### Post by chili555 on 2009-05-10
I don't even see 'printer state'! Is it set up similar to what I have posted?

---

### Post by litlfrog on 2009-05-10
Yep, if you look right in the middle of your screenshot, you'll see "Printer State: Idle." Thanks for your help, but I'm going to try something different. I'll hook the printer up locally and see if I can share it to a Windows machine.

---

### Post by chili555 on 2009-05-10
Pffft! I need a few more grinds on these greasy old trifocals! Thanks.

---

### Post by litlfrog on 2009-05-12
OK, I'm back fresh on this on a new days. Here's what I've determined.
1) I can print just fine to a different printer on our network, an HP Photosmart.
2) The one that's giving me a hard time is an HP Business Inkjet 2200 connected to a Windows XP machine and shared. A different Windows computer here in the office can print to it.
3) I'm getting confused by the two different ways to configure printers, the CUPS interface through the browser and the System -> Administration -> Printing command in Ubuntu. Are these different interfaces for doing the same thing or totally different programs?

What can I try from here? I appreciate the help; I'm a longtime power user, but I've got little education in networking and none in network printing.

---

### Post by litlfrog on 2009-05-12
Still nothing, huh? I also notice that when I delete this printer from the Printer Configuration Utility, it comes right back, so I'm presuming that Ubuntu is seeing SOMETHING on the network, however imperfectly. Are there steps I can take or logs I can look at to determine where the problem lies?

---

### Post by chili555 on 2009-05-12
I just read this: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/286080](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/286080) Especially this:> My current solution is to append the line " /etc/resolvconf/run/resolv.conf r," to /etc/apparmor.d/usr.sbin.cupsd. After that printing works fine.I believe the new line would go at the end of this part:```
/etc/papersize r,
/etc/pnm2ppa.conf r,
/etc/printcap rwl,
/etc/ssl/** r,
```Would you please try this, reboot and let us know?

---

### Post by litlfrog on 2009-05-12
When I print a simple text page, it still just sits in the queue saying "processing." I never did anything to set up this printer through Ubuntu; it just shows up on the network. I don't understand what the settings are SUPPOSED to be when I go in and look at the properties. I know the IP address of the other computer, but don't know what else Ubuntu needs. I've tried various combinations of 192.168.1.32:631/hp2200, with and without the port number, with "/printers" before hp2200. Could this have been set up improperly by another employee who runs Ubuntu on a different computer?

---

### Post by chili555 on 2009-05-12
> Could this have been set up improperly by another employee who runs Ubuntu on a different computer? Very doubtful. 

You said when you delete the printer it reappears. Can you check the reappeared printer's properties and see what it thinks the URI should be? An IPP printer should be, approximately:```
ipp://192.168.1.32:631/printers/HP_2200
```In most cases, a network printer will get detected and the configuration proposed in System -> Admin -> Printing.

Did you make the changes I suggested above? Any change in behavior?> I'm getting confused by the two different ways to configure printers, the CUPS interface through the browser and the System -> Administration -> Printing command in Ubuntu. Are these different interfaces for doing the same thingYes; one the GUI way and one the hard way.

You might also try to add the printer as a network printer and select Windows Printer via SAMBA.

---

### Post by litlfrog on 2009-05-12
I did make the changes you suggested to /etc/apparmor.d/usr.sbin.cupsd, but nothing seems to have changed.

My coworker has gone home for the day and I've discovered a little bit more. Here are the computers in question:
Dudley (my computer): Ubuntu 9.04
Nell (another computer on network, with HP printer attached and the printer shared): Windows XP
Snidely (coworker's computer): Ubuntu 9.04
Horse (printer): HP printer attached to Nell

Now that Snidely is shut down, Horse no longer shows up on my list of available printers. Why should Snidely have anything to do with it? Dudley is trying to see Horse, a local printer on Nell.

I tried adding Horse as a network printer and selecting Windows Printer via SAMBA, but when I click Browse, I'm not seeing any systems other than my own. I know I have networking set up at least partially correctly because I CAN print to Fenwick, a networked printer that's usually locked up in the boss's office.

---

### Post by chili555 on 2009-05-12
> Now that Snidely is shut down, Horse no longer shows up on my list of available printers. Why should Snidely have anything to do with it?The only thing I can hypothesize is that Horse is set up to share, as network printers should be. Snidley has incorrectly set the printer he sees on his computer to share. I'd guess you are seeing Horse not directly through the network, but through Snidley's share. In other words, a share of a share.> My coworker has gone home for the dayTomorrow, I'd check his computer to see if the printer is shared. It only should be shared on the computer or print server it's attached to. If you can stay late, you might shut down every computer except yours and Nell, the computer the HP 2200 is attached to and delete and re-install the HP 2200. Hopefully, the correct URI will be auto detected.

---


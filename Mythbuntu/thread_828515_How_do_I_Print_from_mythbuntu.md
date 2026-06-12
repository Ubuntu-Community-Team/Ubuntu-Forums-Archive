---
title: "How do I Print from mythbuntu?"
date: 2008-06-13
forum: Mythbuntu
---

### Post by allene222 on 2008-06-13
I want to print to a network printer from mythbuntu but cannot find any printer setup.

I have tried every idea I can find online.  I have everything correct per this post
[http://ubuntuforums.org/showthread.php?t=614138](http://ubuntuforums.org/showthread.php?t=614138) but since I have no setup dialog I can't do anything

I installed all the cups programs. 

I find one link with instructions to go to System->Administration->Printer but I have no administration under system and I don't have a printer icon anywhere.

I looked in the "Settings Manager" but there is no printer icon

This computer, 192.168.1.102 needs to print on a HPLJ that is on 192.168.1.1.

I had no problem setting up the print server on 192.168.1.1 but I can't find any of the system stuff I want on mythbuntu 8.04

Please help me.

Allen

---

### Post by allene222 on 2008-06-14
I think I am getting somewhere although I still cannot print.

After installing cups, I can go to this configuration page
[http://localhost:631](http://localhost:631)

However, entering what I think is correct, it still will not print a test page.

If someone knows what I should enter, and cares to take the time to share, I would be grateful.

remote machine is 192.168.1.1 and is called paloaltophoto
the printer queue on paloaltophoto is called "printer"
paloaltophoto is a fedora linux computer
The printer is a HP Laserjet 1200 
On my windows machine, I print to it using PCL 5
On windows, it is called \\PALOALTOPHOTO\printer

This is what I tried that does not work:
Description: hplj1200
Location: paloalotphoto
Printer Driver: HP LaserJet 1200 - CUPS+Gutenprint v5.0.2
Device URI: lpd://192.168.1.1/printer

---

### Post by bmwman on 2008-06-14
What version of Mythbuntu are you running? And is it just the Myhbuntu o you upgraded to Ubuntu desktop? If you did, you can go to System - Settings and open the Login Window Options. Then deselect the auto login option (that's default in mythbuntu) and log out. Next time you log in you can choose session type and choose Gnome. Then you'll have all the options for printers and everything else that you normally don't have in Xfce.

---

### Post by allene222 on 2008-06-15
I have straight mythbuntu, not an upgrade from ubuntu.  It is version 8.04.  I tried what you said anyway and as you would expect I did not have an option for gnome.  

Any other ideas?  I am still stuck.

Allen

---

### Post by bmwman on 2008-06-15
I would upgrade to Ubuntu Desktop. Since you're trying to print something I'm assuming you'll be using your machiine for more than just TV.

---

### Post by allene222 on 2008-06-16
What I am trying to print are instructions to configure various parts of mythtv.  I don't plan on doing anything other than web  and mythtv on this machine.  It would be nice to be able to print stuff from the web.

I had hoped someone out there had set up a remote printer using the  CUPS web interface and was willing to share how to do it.  It is surprising there isn't a clear example somewhere.

Oh well...

Allen

---

### Post by bmwman on 2008-06-16
Sorry I can't help. I'm still trying to configure my Mythbuntu and some things are just too complicated :)

What kind of TV card are you using BTW?

---

### Post by allene222 on 2008-06-16
I bought a second air2pc after seeing how much better it worked than the Pinnacle USB stick.  The price is right too.

I got all my parts today for my new 5400+ AMD based myth box.  I will put it together tomorrow.

Allen

---


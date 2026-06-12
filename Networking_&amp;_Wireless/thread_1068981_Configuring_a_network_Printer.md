---
title: "Configuring a network Printer"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Bazman on 2009-02-13
Hi there,

I am completely new to ubuntu, but am loving it so far. Its just so fast compared to XP!!!!!

Thing is I need to configure a network printer for my PC.

The printer is a HPLaserjet80196pr.

I'm really not sure how to set the printer up.

I've got as far as admin/printing but thats about it.

As for the printer I went to Jetdirect E10/I/O/Hostname/#cass80196pr.

But I don't really know what to do next or even what information I will need.

If someone can post up a step by step guide it would be wonderful!

Baz

---

### Post by Fire_Chief on 2009-02-13
Well, I've never heard of that numbered model of HP Laserjet...however

This should be pretty straightforward.

On the LaserJet menu, go to information, print configuration and have it print out the two page configuration.

There will be a Network IP address listed (if configured).

In Ubuntu, go to System -> Administration -> Printing and click the New button.
After the search disappears and you get the New Printer window, choose AppSocket/HP JetDirect from the list on the left.

Enter the IP address from the printout and click Forward. If a driver is not autoselected, then scroll down and select HP. Click Forward.

Choose the model that closest matches your printer from the list OR choose a generic one like Laserjet 4 or 5. In the window on the right, choose the selection that has (recommended) next to it and click Forward.

Fill out the name and description (if you like) and Apply.

Viola! Try a test print and make sure it looks right.

Cheers!

---

### Post by Bazman on 2009-02-13
wow worked straight away!

Thank you.

Baz

---


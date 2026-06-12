---
title: "How to connect to a printer for wireless printing?"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by glln0v on 2013-03-31
Is this an easy thing to accomplish? 

With a router giving WiFi and a laptop computer running 12.04. Is it possible to somehow set the printer so that users can print to the printer without having to physically connect a cable from the printer to the laptop?

I don't know how to set this up and was wondering if it's something I could setup myself. thanks.

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by glln0v on 2013-03-31
Thanks so much for this great info.

Based on your "road map" I was able to find the printer on a router network and use the same drivers I installed to print from cable. But when I try to add the printer for Network it asks for stuff I don't know about: AppSocket, IPP, HTTPS, IPP14, IPPS, LPD/LPR Host or printer. Which of these am I supposed to use? I tried a couple of them at random but the Test Page never prints.

---

### Post by sammiev on 2013-03-31
> **glln0v said:**
> Is this an easy thing to accomplish? 

With a router giving WiFi and a laptop computer running 12.04. Is it possible to somehow set the printer so that users can print to the printer without having to physically connect a cable from the printer to the laptop?

I don't know how to set this up and was wondering if it's something I could setup myself. thanks.

I added my WPA2 key to my wireless printer from the printer keypad and went into printer settings within ubuntu and selected network. It displayed my printer after a few seconds. I selected my printer and saved. Job done. :)

---

### Post by glln0v on 2013-03-31
> **sammiev said:**
> I added my WPA2 key to my wireless printer from the printer keypad and went into printer settings within ubuntu and selected network. It displayed my printer after a few seconds. I selected my printer and saved. Job done. :)

sounds complicated. I don't know how to add a WPA2 key. Where do I get that from?

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by sammiev on 2013-03-31
I have an Epson Artisan 730. My printer found my router and asked for the WPA2 key when I selected the wireless network. Whole setup time was less than 2 min. Darn, it took longer to unpack the printer from the box it came in.

---

### Post by glln0v on 2013-04-06
I am running a wireless router so my computers can access the internet via WiFi. My brother printer is a network capable printer--it has an RJ-45 port on the back. I connected ethernet cable from the router to the Brother printer.

With no "physical connection" between my laptop computer and the printer (the printer is only physically connected to the router via ethernet): When I open the ubuntu print section and "Add printer," ubuntu sees the brother printer. I set it up and get an icon. If I then type in the IP address of the printer, I can go into the printer's settings page and actually print "Lists" such as "user settings." But if I try to print a webpage or a work document or something like that, I always see this:

[B]The printer URI is incorrect or no longer exists.
[/B]
Does anyone know how to find out what URI one is supposed to use? when I open the Printer properties for the icon that was created when I setup the printer, I see an option for URI. How do I find out which one will work?

---


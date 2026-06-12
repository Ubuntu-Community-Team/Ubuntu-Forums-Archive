---
title: "Adding a Network Printer?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Bradj47 on 2009-04-30
I'm having problems adding a network printer. I go to the Printer configuration settings and click on New Printer. Then it scans and finds the one on I want to add. I click on it then click Forward then a window pops up saying 'searching for drivers' then it disappears and starts acting like nothing happened. What's going on? Can it not find drivers or is that a system bug?

---

### Post by chili555 on 2009-04-30
It can find drivers for most printers, but not all. Sometimes the driver for a close model will work. Please let us know the exact make and model and let's see if we can help.

---

### Post by Bradj47 on 2009-04-30
It's a Lexmark C544

---

### Post by chili555 on 2009-04-30
I went to Lexmark's website and searched for Ubuntu drivers for your printer. Download and extract it (right click and select 'Extract Here') and then you should be able to point the printer installer to the C544 .ppd file and be all set. Post back if you get stuck.

[http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

---

### Post by Bradj47 on 2009-04-30
Thanks, everything worked perfectly after I installed that driver. It successfully printed a test page and everything. Thanks!

---

### Post by PhilMize on 2009-05-01
Maybe I should make a new thread for this but anyone know workarounds for adding Canon's? I know they don't support Linux, but it would make my life so much easier if I didn't have to either fire up virtual box to print or remote into our servers here at work to print something. I'm at home right now and off the top of my head I can't remember the full name to one of the printers. I believe the one is a Canon IR2020. When I get to work tomorrow I'll make note of the printer names.

---

### Post by chili555 on 2009-05-01
> When I get to work tomorrow I'll make note of the printer names.I will look forward to it. By the way, there are printers that simply will not work; let's give this one our best shot.

---

### Post by PhilMize on 2009-05-01
OK so here's a short list of the Canon's in relative proximity of my cubicle. I just Looked up the installed drivers on our DNS server which they are all shared through.

Canon iR2020 PCL5e
Canon iR7200 PCL5e
Canon iR5020/iR6020 PCL6
Canon iR3570/iR4570 PCL5e

iR = Image Runner

All the listed iR printers off their website. I was browsing through the drivers list and yea theirs only available drivers for windows and os x. (possible newb question)I wonder what would happen if I emulated a driver in wine?:confused:

```
 Digital Copiers

        Department - Digital

          imageRUNNER 2230

          imageRUNNER 2830

          imageRUNNER 3530

          imageRUNNER 400V

          imageRUNNER 5070

          imageRUNNER C5870U

          imageRUNNER C6870U

          imageRUNNER 5570

          imageRUNNER 600V

          imageRUNNER 6570

          imageRUNNER 2270

          imageRUNNER 2870

          imageRUNNER 3570

          imageRUNNER 4570

          imageRUNNER C3170U

          imageRUNNER C3170i

          Color imageRUNNER C4580i

          Color imageRUNNER C5180i

          Color imageRUNNER C3380

          Color imageRUNNER C4080i

          Color imageRUNNER C5180

          Color imageRUNNER C4580

          Color imageRUNNER C4080

          Color imageRUNNER C3380i

          Color imageRUNNER C2880

          Color imageRUNNER C2880i

          imageRUNNER C6800

          imageRUNNER 3045

          imageRUNNER 2200

          imageRUNNER 3035

          imageRUNNER 2220N

          imageRUNNER 3030

          imageRUNNER 2220i

          imageRUNNER 5000V

          imageRUNNER 3025

          imageRUNNER 5075

          imageRUNNER 2800

          imageRUNNER 5065

          imageRUNNER 3300

          imageRUNNER 5055

          imageRUNNER 3320N

          imageRUNNER 3320i

          imageRUNNER 400S

          imageRUNNER 5000

          imageRUNNER 5020

          imageRUNNER 5020i

          imageRUNNER 6000

          imageRUNNER 6020

          imageRUNNER 6020i

          imageRUNNER C3100

          imageRUNNER 3245

          imageRUNNER 5050N

          imageRUNNER 5000E

          imageRUNNER C5800

          imageRUNNER 3300i

          imageRUNNER 5000i

          imageRUNNER 3245i

          imageRUNNER 5000EN

          imageRUNNER 3300E

          imageRUNNER 2018

          imageRUNNER 3235

          imageRUNNER 5050

          imageRUNNER 3300EN

          imageRUNNER 2018i

          imageRUNNER 3235i

          IR200L

          imageRUNNER 2022

          imageRUNNER 3230

          imageRUNNER 210N

          imageRUNNER 2022i

          imageRUNNER 3225

          imageRUNNER 2025i

          imageRUNNER 210S

          IR210E

          imageRUNNER 2030i

          imageRUNNER 330S

          imageRUNNER 330N

          imageRUNNER 400N

          imageRUNNER 550

          imageRUNNER 600

          imageRUNNER 60

          iR3250

        Desktop - Digital Copiers

          imageRUNNER 1310

          imageRUNNER 1023

          imageRUNNER 1330

          imageRUNNER 1370F

          imageRUNNER 1023iF

          imageRUNNER 1023N

          imageRUNNER 1630

          imageRUNNER 1670F

        Production - Digital

          imageRUNNER 105

          imageRUNNER 105+

          imageRUNNER 8070

          imageRUNNER 7105

          imageRUNNER 7095

          imageRUNNER 9070

          imageRUNNER 7086

          imageRUNNER 7200

          imageRUNNER 8500

          imageRUNNER 85

          imageRUNNER 110

          imageRUNNER Pro 150+

        Workgroup - Digital

          imageRUNNER 2016

          imageRUNNER 2016i

          imageRUNNER 2010F

          imageRUNNER 2020

          imageRUNNER 2020i

          imageRUNNER 1025

          imageRUNNER 1023

          imageRUNNER 1600

          imageRUNNER 1025iF

          imageRUNNER 1023iF

          imageRUNNER 2000

          imageRUNNER 1025N

          imageRUNNER 1023N
```

---

### Post by chili555 on 2009-05-01
Please check here: [http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_2020](http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_2020)

I notice the printer is supposed to use the *pxlmono* driver. You can download the .ppd file and point the printer installer to it. Please post back so the searchers know what worked...or not. As well, post back if you get stuck.

---

### Post by Bradj47 on 2009-05-01
I'm not sure if this would work but you could set up a windows print server.

---

### Post by PhilMize on 2009-05-01
> **chili555 said:**
> Please check here: [http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_2020](http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_2020)

I notice the printer is supposed to use the *pxlmono* driver. You can download the .ppd file and point the printer installer to it. Please post back so the searchers know what worked...or not. As well, post back if you get stuck.

Well its the weekend so I won't be able to do anything till Monday. I'll let you know then.:)

---

### Post by paw53 on 2009-05-06
Does anyone know how to connect an HPC5180 printer to a network. I bot a new Vista HP laptop and cannot figure it out--is this a totally linux?site?

---

### Post by chili555 on 2009-05-07
> is this a totally linux?site?Yes, it is. Me no speeka da windoz.

---

### Post by PhilMize on 2009-05-08
> **paw53 said:**
> Does anyone know how to connect an HPC5180 printer to a network. I bot a new Vista HP laptop and cannot figure it out--is this a totally linux?site?

What kind of network are you trying to connect it too? If its a home network you can just click Start>Control Panel> Printers Then right click on the printer (assuming you have the driver installed and everything) Right Click > Properties > Sharing Tab > check share this printer, type the name you want it to show up as on your network and depending on if your on a domain check list in directory, (if your not on a domain I don't think this option even shows) click apply > ok > then go to the computer you want to share it too, (assuming its a xp or vista machine) Start>Control Panel>Printers>add new printer>add a network printer> (if its vista it will search auto and xp you should see a box to type the name of the printer in)

Click connect and it will do its thing.
SIDENOTE:
Make sure when you type the name of the printer in the box, you put the name of the pc it's shared on first, then the printer name so it should look like this

\\ComputerName\Printername

Also make sure both computers are on the same work group and or domain. I've done it without them being on either but that takes a little more finesse :o

---

### Post by PhilMize on 2009-05-08
> **chili555 said:**
> I went to Lexmark's website and searched for Ubuntu drivers for your printer. Download and extract it (right click and select 'Extract Here') and then you should be able to point the printer installer to the C544 .ppd file and be all set. Post back if you get stuck.

[http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

K I have the ppd file and I browsed around a bit to find the right instructions but I'm still at a loss for how to get a driver installed...

---

### Post by chili555 on 2009-05-08
> how to get a driver installed...Go to System -> Administration -> Printing. Click New. Add a network printer, likely the IPP protocol. When you are confronted with a list of Canon printers and don't find your model, you should see the option to supply your ownn PPD file. Browse to it and add it.

You may also see an option to search for network printers and add your own PPD file when it detects the ir2020 but has no driver.

---

### Post by PhilMize on 2009-05-11
SWEET! That worked out perfectly with the ir2020! I don't have time currently to try it on another Canon, the one I want to try it with is passworded... So if I get a chance I'll try it and let you know how that works out. But I was surprised in the network directory it saw all the networked printers in the building just I couldn't connect to them without the driver.

---

### Post by chili555 on 2009-05-11
SWEET, indeed. Glad it's working for you!

---

### Post by PhilMize on 2009-05-15
K so I'm at another building... here we have an ir5050. Its not listed in the directory on linux foundation but i tired it with the ir5570 .ppd and it worked just fine. So for connecting ubuntu to canons refer too:
[http://openprinting.org/printer_list.cgi?make=Canon]("http://openprinting.org/printer_list.cgi?make=Canon"):p

---

### Post by meitham on 2011-04-27
> **PhilMize said:**
> K so I'm at another building... here we have an ir5050. Its not listed in the directory on linux foundation but i tired it with the ir5570 .ppd and it worked just fine. So for connecting ubuntu to canons refer too:
[http://openprinting.org/printer_list.cgi?make=Canon]("http://openprinting.org/printer_list.cgi?make=Canon"):p

That did not actually work for me, I used ir5570 to print on ir5050 printer and the one test page print ended up printing around 150 pages, and that was on a client site, so imagine the embarrassment :D

---

### Post by Crayz9000 on 2011-09-23
Sorry to bump an old thread, but I ran into this issue and found a resolution for the imageRunner 5050n printers. The "Canon imageRunner 5000 Foomatic/pxlmono (recommended)" PPD works perfectly with the 5050n on Ubuntu 11.10.

---


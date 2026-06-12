---
title: "Samsung ML-2010 Printer Throght Network"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by izizzle on 2009-02-09
So, here is the deal. I have a Samsung ML-2010 printer hooked up to our network, meaning it is not connected directly to my computer. I want to know how to go about installing this printer and configuring it to print through the network. I read a post about it somewhere in these forums a while back, but can't seem to find it now. Plus, are there any extra utilities/software I would need to install?

Thanks.

---

### Post by chili555 on 2009-02-09
System -> Administration -> Printing. Select New printer. Select Network printer and the IPP protocol. The device URI I am using is ```
ipp://192.168.1.105:631/printers/ML-2010
```You will be prompted to select a driver; the ML-2010 is on the list.

Without installing and configuring Samba, BIND and who knows what else, it's just that easy **IF** the computer the printer is actually attached to has a static IP address, 192.168.1.105, in my example.

If the computer the printer is actually attached to is a desktop machine that doesn't leave home to go to the internet cafe, then a static IP is perfect.

Post back if you hit a snag.

---

### Post by izizzle on 2009-02-10
Actually, the printer is not connected to any computers. It has its own D-Link router. But I'll still give it a go and see what I get. 

Thanks!

---

### Post by ddalley on 2009-02-18
I had no idea how to get Ubuntu to recognise my Samsung ML-2010 attached now to the D-Link DNS-323 NAS box, but I discovered Foomatic and installed it.

Setting this printer up on the network was as painless as how it was done by Vista. At least I was able to print a test page.:D

---

### Post by izizzle on 2009-02-22
Ok chili. I finally got a chance to try it, but I don't see any option that says 'Network Printer'. I tried it in 'Other' and 'AppSocket/HPJetDirect'. None of them worked. The printer is connected to a D-Link router. Do have any idea about what i should do next. Also, should I select the Foomatic driver or the default recommended one?

Thanks.

If it helps, the IP for the printer is 192.168.1.10 port 9100

---

### Post by izizzle on 2009-02-23
Bump....

---

### Post by chili555 on 2009-02-24
Do you see the option for 'Internet Printing Protocol'? You will probably see the option to search for queues and it will probably find your printer by itself. Otherwise, your host will likely be:```
ipp://192.168.1.10:9100
```and the queue will likely be ```
/printers/ML-2010
```> Also, should I select the Foomatic driver or the default recommended one?The default should work just perfectly.

---

### Post by izizzle on 2009-02-24
I don't think I saw an option for Internet Printing Protocol, unless you are talking about the one under "Other". I'll give it another try and get back to you.

---

### Post by chili555 on 2009-02-24
Under System -> Admin -> Printing, select New Printer and it should look like the attachment.

---

### Post by izizzle on 2009-02-24
There is my problem. I don't have the option for Internet Printing Protocol. I can see all the other options except this one. Would it make a difference if I am trying to set the printer up through the LiveCD? Thanks.

---

### Post by chili555 on 2009-02-25
I wouldn't think so, however I suppose it is possible that some things are omitted in order to fit on the CD. You might go to System -> Admin -> Synaptic and be sure that *cups, cups-common, cups-client, foomatic-db* and all their dependencies are installed. Install as needed.

See if IPP appears.

---

### Post by izizzle on 2009-02-25
Thanks, I'll try that.

---

### Post by izizzle on 2009-02-25
They are all installed, but IPP won't show up. All I see is LPT #1, Appsocket/HP Deskjet, Windows Printer VIA Samba, and Other. Any ideas on how to fix this? I want to make sure my printing works before I actually install. Thanks.

---

### Post by izizzle on 2009-02-26
Bump.... I would really like to find out why IPP is not showing up. Perhaps there is someone with an answer? Chili?

---

### Post by chili555 on 2009-02-27
I wish I knew. I have Googled for 'IPP LiveCD' quite extensively and see bugs reported extensively. I have one other suggestion, however. Open a terminal and type in:```
sudo tail -f /var/log/messages
```Leave the terminal open as you do the next step so you can watch for any interesting messages.

Please open Firefox or another browser and type in:```
http://127.0.0.1:631
```See if you can add your printer using the parameters previously discussed.

Network printing works perfectly for me with my ML-2010 attached to another linux computer. I have never tried a stand-alone print server, although I am anxious to try.

---

### Post by izizzle on 2009-02-28
I tried adding the printer from the site but IPP still doesn't show up. I pinged my print server and it is able to connect. What can the problem be?.....:confused:

---

### Post by chili555 on 2009-02-28
I just read this: [http://www.funnestra.org/ubuntu/intrepid/#ipp](http://www.funnestra.org/ubuntu/intrepid/#ipp)

Here:>    2.
         1. Go to the System > Administration menu and click on Printing.
         2. Click on the New Printer button.
         3. Select Other, and enter the following URI:

            http://$SERVER:631/printers/$PRINTER

            where $SERVER is the server hostname or IP address and $PRINTER is the printer name on the server, and then click Forward and follow the remaining steps as you would for local printer setup. You can see the names of all the printers shared by a server by visiting the following URL in your web browser:

            http://$SERVER:631/printers

            where $SERVER is the server hostname or IP address.

It suggests you select 'Other' and enter the printer details as an *http* URI, rather than *ipp.*

Please try:```
http://192.168.1.10:9100/printers/ML-2010
```Please let us know of your success.

---

### Post by chili555 on 2009-03-01
I also read this: [http://www.linuxquestions.org/questions/linux-networking-3/d-link-routers-usb-port-printer-problems-702488/](http://www.linuxquestions.org/questions/linux-networking-3/d-link-routers-usb-port-printer-problems-702488/)

It sounds like it is a systemic problem with the D-Link router.

---

### Post by izizzle on 2009-03-01
I tried it with http in "Other", but no luck. The print server is a D-Link DPR1260. Anything else I can try, or is this the end of the line for printing?

---

### Post by chili555 on 2009-03-02
Well, it's not the end of the line for printing. It may be the end of the line for this particular D-Link print server...or maybe not.

I went to the extent of downloading the LiveCD and running it. Before I could blink, when adding a printer, it said, "Detecting Printers" and found mine and selected the drivers and everything! It seems to me that the key element is if the printer is able to publish itself on the network.

Once I knew the model of your print server, D-Link DPR1260, I downloaded the user manual. I noticed it requires UPnP be installed and activated. Please see pages 10-13 in the manual.

At this point, this is less what I know and more what I guess. If any others on the forum can help, please jump right in!

There is a package available for installation in System->Admin->Synaptic called gupnp-tools. It may or may not help your computer discover the printer.

I wish I could help more.

---

### Post by izizzle on 2009-03-02
Thanks a whole lot chili. I'll definitely give it a go. All the help has been much, much, much appreciated. Thanks again.

I checked pages 10-13 of the manual, but it explains how to do it with windows. I will, however, try to install that package you mentioned.

---


---
title: "Printer sharing"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by malcmail on 2010-07-12
After making the jump to Lucid Lynx I'm having a printer nightmare. I am hoping to have the Ubuntu box running a print server for a number of windows machines. The one I'm working on at the moment being XP.
 
What I can do - server has fixed IP. Can ping from XP box to server. Can access server:631/printers from XP box so get the CUPS 1.4.3 utlity web window thingy.
 
What I can't do - browse the server for a printer (it is installed correctly) from the XP box. I tried entering the name of it but I'm no longer sure what the name of it is. Is it the ugly looking device URI? How much of that do I use.
 
ANy help gratefully received. If you need more info please shout. Thanks in advance.
 
PS for some odd reason I always have to add the IP of the client machine into the ufw before Ican open the web page. This was the same on 9.10 even though I've never turned the firewall on.

---

### Post by wookieshaver on 2010-07-12
You might try editing the samba configuration file as detailed here:
 
[http://www.petersblog.org/node/726](http://www.petersblog.org/node/726)

---

### Post by malcmail on 2010-07-13
Thanks for that - there were a couple of items missing and create mode was create mask. Is there a difference?
 
However.....I still can't browse to find the printer. The server is listed but when I click on it....nothing. Beginning to drive me round the twist. ANy other ideas?

---

### Post by Morbius1 on 2010-07-13
The default smb.conf should have worked as it was configured.

> However.....I still can't browse to find the printer.> What I can do - server has fixed IP.Then don't browse to it. Connect to it directly:

OnWindows:
Use the "Add Printer Wizard".

Start > Control Panel > Printers and Faxes > Add Printer > The Add Printer Wizard opens

Check "A network printer, or a printer attached to another computer"

Check "Connect to a printer on the internet or on a home or office network"

Enter it directly, for example:
```
URL: \\192.168.0.100\Linux_Printer_Name
```

---

### Post by malcmail on 2010-07-13
Now there's the problem lol. With my last version I named the printers then did the whole [\\new-server:631\printers\named-printer]("file://\\new-server:631\printers\named-printer") (or the http version, I cant recall). The thing is what is the name of the printer? I've a device URI that is not exactly user friendly. IS that it - or just part of it?

---

### Post by Morbius1 on 2010-07-13
```
The thing is what is the name of the printer?
```It's whatever you named it. If there is a doubt then run this command from a Terminal:
```
lpstat -t
```You'll see a line that looks something like this:
> system default destination: HP970HP970 in this case is the name of the printer.

---

### Post by malcmail on 2010-07-13
So that gives me "HP-LaserJet-3050". If I try to connect to [\\new-server:631\printers\HP-Laserjet-3050]("file://\\new-server:631\printers\HP-Laserjet-3050") I get that windows cannot connect to the printer. Yet I can examine all its properties if I browse to that address in a web browser on the client machine!
 
SOLVED! COpied and pasted the URL I had above into the print from net box instead - it looks like its installing. And working. Many thanks fella!  That's job 1 done. As I thought it should be - so not sure why it didnt work. Did I mention I love this place? :)

---


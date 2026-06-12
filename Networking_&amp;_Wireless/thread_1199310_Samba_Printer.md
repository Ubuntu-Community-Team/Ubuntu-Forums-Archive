---
title: "Samba Printer"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by notsomeone on 2009-06-28
I've installed a samba server on my desktop PC, and the file-sharing works pretty well, but I have one small question about sharing a printer.
Right now, the only way that I can print a file from a remote computer is to connect to the samba server like:

$ smbclient //<server>/<share>
smb: \> print <file>

The file does print, but I want the option to be able to print directly from the text editor.

I've gone to System Settings > Advanced > Printer Configuration > New Printer > New Network Printer.
And then maybe I am putting an incorrect address in the 'Enter Device URI' field, because the cursor just loads forever and nothing happens.

---

### Post by dmizer on 2009-06-28
Use the default printer sharing in Ubuntu. It works fine with Windows, and has a nice point-and-click interface.

---

### Post by notsomeone on 2009-06-28
What do you mean 'default printer sharing'? Within smb.conf?

My remote machine is also running Kubuntu.
Only a roommate has Windows and I don't know how it is working with him yet.

---

### Post by dmizer on 2009-06-28
You do not need to do anything with smb.conf to share a printer to Windows. There is a printer configuration applet in the system menu for Gnome, it should be somewhere similar to that in Kubuntu.

I am not sure where the printing service is located in Kubuntu, but you can also access it by browsing to [http://localhost:631](http://localhost:631)

Edit:
Found this -> [http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html](http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html)

---

### Post by notsomeone on 2009-06-28
> Found this -> [http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html](http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html)

I don't think I have that nice looking Print Manager with KDE4. I only have one that looks like this: [ATTACH]119295[/ATTACH]

I do have it on the desktop PC which uses KDE 3.5, but that's no help to the laptop.

I just tried ipp://<serveraddress>:631/printers/<printername> for the Device URI, and I thought it worked, because it got to the next step for once, but it didn't really work.


I can go to http://<servername>:631, and I set it to show printers shared by other systems and to Share published printers connected to this system.

Nothing seems to work.

---

### Post by dmizer on 2009-06-29
As odd as this may sound, when adding the printer to Windows you have to add it as a local printer. Here's more info:

[http://www-jerry.oit.duke.edu/community/howto/pc/add_tcpip_printer.html](http://www-jerry.oit.duke.edu/community/howto/pc/add_tcpip_printer.html)

Also, in the CUPS web administration tool under the "administration" tab, you'll need to make sure that both "Share published printers connected to this system" and "Allow printing from the Internet" are checked.

---


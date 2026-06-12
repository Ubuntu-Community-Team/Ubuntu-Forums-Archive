---
title: "printing to windows"
date: 2005-01-09
forum: Networking &amp; Wireless
---

### Post by danip on 2005-01-09
My roomate owns the printer and also runs windows xp.  I have his ip address and the printer name (mulva)  I went to computer > system config > printing and selected add a printer I then selected network printer and then selected windows smb printer.    I filled out the host name wich i assume is the ip address and then under the printer box i assumed that was the printer name so i entered mulva.  After this the printer is supposidly set up but i still cannot print to it.  I get the little printer icon in the corner like its trying to print but nothing happens.  Any ideas?

---

### Post by hardcandy on 2005-01-10
I believe you have to install the printer driver for linux on your machine. Linux is not able to use his WinXP driver.

---

### Post by rider343 on 2005-01-10
I don't remember the solution now, but it is a bug on cusps... I will find the answer and post soon

---

### Post by rider343 on 2005-01-10
edit the /etc/cups/printers.conf


the correct form is: smb://**workgroup**/username:password@server/printershare

---

### Post by danip on 2005-01-11
ok can you tell me if i entered this correctly.  this is what my /etc/cups/printers.conf looks like.

```
# Printer configuration file for CUPS v1.1.21rc1
# Written by cupsd on Sun Jan  9 21:00:39 2005
# smb://mshome/dan:rastaman05@cheetor/mulva

```

---

### Post by danip on 2005-01-11
also when i setup the printer as i described above it says in the setup that it is installing the printer driver on here.

---

### Post by bradpreston on 2005-01-11
I also had problems printing to a windows printer - I installed samba, and then ran nmbd and smbd before setting up the printer and I think thats what got it working for me.

---

### Post by danip on 2005-01-11
[QUOTE=bradpreston]I also had problems printing to a windows printer - I installed samba, and then ran nmbd and smbd before setting up the printer and I think thats what got it working for me.[/QUOTE]
 I have a working samba file and am able to share the files I want on here.  I just cant seem to print to windows.  Does anyone know of a good guide for this?  All I can ever find is printing windows to linux.

---

### Post by hardcandy on 2005-01-11
> # smb://mshome/dan:rastaman05@cheetor/mulva 

If that line has a # in front, delete it. A # tells a program that line is not to be used.

---

### Post by danip on 2005-01-11
ok so i deleted that now do i have to add a printer by going computer system config then printing or how do i use that printer now?

by the way are you the hard candy from the justlinux forums?

---

### Post by hardcandy on 2005-01-12
Add the printer via the print manager under Computer-->System Cinfiguyration.
And yes I am.  :-D

---

### Post by danip on 2005-01-13
Still cant get the thing to print.  It says its printing but just sits there.  Must be something wrong on his end or im still doing something wrong.

---

### Post by benjamin on 2005-01-26
In my /etc/cups/printer.conf I'havent the Workgroup, only the server  ....


... cut
Info printername
DeviceURI smb://user:password@server/printername
... cut

regards.

---

### Post by ktogias on 2005-05-12
I just runned into the same issues trying to setup a printer sared by a WinXP box. 

I was able to print to the printer, just after i did the following:

1. From Gnome Panel: System > system config > printing
At Global Settings Tab I checked "Detect LAN Printers" (I do not know I that step palyed any role in the solving of the problem...)

2. I Clicked "New Printer" -> Network Printer -> Windows Printer (SMB) 

3. At host name box I filled in the full path of the WinXP box as it shows up at Locations > Network Servers > Windows Network, Respecting the Case
(I wrote enterprise/NEMESIS - Note "NEMESIS" is what i saw in nautilus, not "nemesis")

4. At Printer box I fiiled in the name of the printer as it is found by smbclient -L nemesis

5. At username box I filled "guest"

6. I left the password box empty

(Steps 5 and 6 assume that The setup at the windows box does not require user authentication to access the printer)

7. I chose the printer make and model and after finishing with this dialog I was able to send a test page to the printer. The page was printed correctly.

I do not know which step of thew above was essential, and which not....

The resulting /etc/cups/printers.conf is this:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu May 12 11:49:33 2005
<DefaultPrinter DeskJet-960C>
Info DeskJet-960C
DeviceURI smb://guest:@enterprise/NEMESIS/hpdeskje
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

---


---
title: "Network printing with Maverick Meerkat"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by rlgoddard on 2010-10-27
Hi,

I am having some trouble getting one PC (Windows XP) to see the printer attached to the other PC (Ubuntu).  I went to System > Administration > Printing in Ubuntu and did the following:


[LIST]
[*]Checked the box next to "Publish shared printers connected to this system"
[*]Checked "Enabled", "Accepting jobs", and "Shared" in the properties of the printer.
[/LIST]

I have an HP Deskjet 5650.  Is there anything else I need to be doing?

Thanks,
Russ

---

### Post by rlgoddard on 2010-11-02
Anyone?

---

### Post by rlgoddard on 2010-11-10
No one?  Tapping microphone... Bueller?  Bueller?

---

### Post by Morbius1 on 2010-11-10
Can the Ubuntu machine itself list the printer when you run this command:
```
smbtree
```If it does not then run these two commands in this sequence and see if it does:
```
sudo service cups restart
``````
sudo service smbd restart
```

---

### Post by rlgoddard on 2010-11-11
> **Morbius1 said:**
> Can the Ubuntu machine itself list the printer when you run this command:
```
smbtree
```If it does not then run these two commands in this sequence and see if it does:
```
sudo service cups restart
``````
sudo service smbd restart
```

When running smbtree, it does not list the printer.  When I run sudo service smbd restart, it spits out the following error message:

```
restart: Unknown instance:
```Thanks!

---

### Post by Morbius1 on 2010-11-11
Then start it:
```
sudo service smbd start
```
Run smbtree again to see if Ubuntu will list it then see if the remote machine can see it.

---

### Post by rlgoddard on 2010-11-11
This is what I get:

```
WORKGROUP
    \\UBUNTU                 ubuntu server (Samba, Ubuntu)
        \\UBUNTU\deskjet-5600       hp deskjet 5650
        \\UBUNTU\IPC$               IPC Service (ubuntu server (Samba, Ubuntu))
        \\UBUNTU\print$             Printer Drivers
    \\LOLITA                 
    \\DBTOA000               

```I did not have Samba installed, which explains why I did not have smbd (tried to start smbd before I installed samba, but could not).  On \\LOLITA (the desktop running Windows XP Pro), I was about to see \\UBUNTU through Window XP's Add Printer dialog, but did not see the printer listed.  On \\DBTOA000 (the laptop running Windows XP Home), I was successful in adding the printer, including being able to see the printer.  Weird!

---

### Post by Morbius1 on 2010-11-11
Since it works on one WinXP and not the other Maybe LOLITA has a firewall in the way. Try disabling it temporarily and see if it can see the printer.

---

### Post by rlgoddard on 2010-11-11
I tried disabling the firewall.  No go.  However, I followed the instructions at this link: [http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html).  Both of my Windows machines can now see the printer.  I installed the drivers on the Windows machines as well from the drivers on each machine, rather than from Ubuntu.

However, I appear to be unable to print.  It looks like the print jobs aren't being sent to the printer.  In fact, it appears that Ubuntu never got the print jobs.  Any ideas?

---

### Post by Morbius1 on 2010-11-12
Instead of using Samba to share the printer with Windows:
Windows PC > LAN > Samba > CUPS

Go to CUPS directly:
Windows PC > LAN > CUPS
Samba represents unnecessary overhead.

In WinXP when you use the Add Printer Wizard select:

"Connect to a printer on the Internet or on a home or office network" and add the printer path with this type of format:
```
http://192.168.0.100/printers/LinuxPrinterName
```OR EVEN BETTER:
```
http://192.168.0.100:631/printers/LinuxPrinterName
```631 is the ipp port number that Linux uses for the CUPS server.

Change 192.168.0.100 to the ip address of the Machine with the printer.

---

### Post by rlgoddard on 2010-11-12
> **Morbius1 said:**
> Instead of using Samba to share the printer with Windows:
Windows PC > LAN > Samba > CUPS

Go to CUPS directly:
Windows PC > LAN > CUPS
Samba represents unnecessary overhead.

In WinXP when you use the Add Printer Wizard select:

"Connect to a printer on the Internet or on a home or office network" and add the printer path with this type of format:
```
[http://192.168.0.100/printers/LinuxPrinterName](http://192.168.0.100/printers/LinuxPrinterName)
```OR EVEN BETTER:
```
[http://192.168.0.100:631/printers/LinuxPrinterName](http://192.168.0.100:631/printers/LinuxPrinterName)
```631 is the ipp port number that Linux uses for the CUPS server.

Change 192.168.0.100 to the ip address of the Machine with the printer.

That worked!  Thanks!  I used the computer name of the other computer (UBUNTU) instead of the IP address, so it looks like [http://ubuntu:631/printers/deskjet-5600](http://ubuntu:631/printers/deskjet-5600).  Would the other two computers know to connect the UBUNTU even though UBUNTU's IP address might change?

---

### Post by Morbius1 on 2010-11-12
Yes. If using the machine name works then it will be good if the ip address changes. I should have mentioned that as an option but for most home networks it doesn't work as well as straight ip address. 

If you don't mind telling us - what is the make and model of your router. I'm developing a theory that some routers can actually get in the way of doing the kind of thing that seems to work for you and I.

---

### Post by rlgoddard on 2010-11-12
I have a WRT54G v.5 wireless router with DD-WRT firmware.

Ubuntu has come a long way since 6.06, my first foray into Ubuntu.   Wireless and video now works perfectly out of the box, but network  printing still remains a struggle.

---

### Post by Win-Smash on 2010-11-12
had the same problem did it with out samba make sure cups is set to share and the printer is working in Ubuntu 10.10 then on the Windows 7 computer

1. Install the printer as a local printer 1st.

       Start --> Devices and Printers --> add Printer --> Add a Local Printer --> Use Existing Port --> Remember to do a windows update here if the drivers of the printer you want to install is not in the list. I had to do the update a few times before the driver appeared. Select the printer driver --> Follow the prompts You dont have to share the printer or anything....

Remember to name the printer test or something
 
2. Install the network Printer

       Start --> Devices and Printers --> add Printer --> Add a network, wireless o Bluetooth printer --> THe printer I want isnt listed --> 
enter  
'http://***.***.*.***:631/printers/Canon-iP2600-series-2' without quotes (Canon-iP2600-series-2 is the queue Name on the ubuntu machine) into the Select a shared Printer by name field and click next

You will be prompted to select the printer driver here. Because you have already done a windows update and installed the printer locally in step 1, the driver should be listed here. If not repeat step1

Hope this helps

---

### Post by dougcumiskey123 on 2011-01-13
I too am having the same problem. IE printer is on meerkat, windows is client on a ethernet switch. The net works ok for other things but cant get Ubuntu to work as print server. I am a Newbe so it will take me some time to work through the post so can you check this thread in a couple of days and I will post if further help is needed.

Thanks Doug...

---

### Post by dougcumiskey123 on 2011-01-13
In WinXP when you use the Add Printer Wizard select:

"Connect to a printer on the Internet or on a home or office network" and add the printer path with this type of format:
Code:
[http://192.168.0.100/printers/LinuxPrinterName](http://192.168.0.100/printers/LinuxPrinterName)
OR EVEN BETTER:
Code:
[http://192.168.0.100:631/printers/LinuxPrinterName](http://192.168.0.100:631/printers/LinuxPrinterName)
631 is the ipp port number that Linux uses for the CUPS server.

Change 192.168.0.100 to the ip address of the Machine with the printer.
--------------------------------------------------------------------------------------------------------------

I have tried to follow the above instructions but windows is rejecting saying that the name is wrong or it has lost the connection.

I have  tried these variations.

[http://192.168.0.100:631/printers/LinuxPrinterDeskjet-F2400-series](http://192.168.0.100:631/printers/LinuxPrinterDeskjet-F2400-series)
and
[http://192.168.0.100:631/printers/Deskjet-F2400-series](http://192.168.0.100:631/printers/Deskjet-F2400-series)

Doug...

---

### Post by dougcumiskey123 on 2011-01-13
I have made some progress, I did not have Samba or Aptitude. Can anyone tell me if the details below are now correct, if so I will start looking at windows settings.


doug@ubuntu:~$ smbtree 
Enter doug's password: 
WORKGROUP 
	\\UBUNTU         		ubuntu server (Samba, Ubuntu) 
		\\UBUNTU\Deskjet-F2400-series	HP Deskjet F2400 series 
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu)) 
		\\UBUNTU\print$         	Printer Drivers 
MSHOME 
	\\DOUGLAPT-45FA9B		Laptop 
		\\DOUGLAPT-45FA9B\Printer        	Microsoft XPS Document Writer 
		\\DOUGLAPT-45FA9B\C$             	Default share 
		\\DOUGLAPT-45FA9B\ADMIN$         	Remote Admin 
		\\DOUGLAPT-45FA9B\Save           	 
		\\DOUGLAPT-45FA9B\Downloads      	 
		\\DOUGLAPT-45FA9B\SharedDocs     	 
		\\DOUGLAPT-45FA9B\print$         	Printer Drivers 
		\\DOUGLAPT-45FA9B\IPC$           	Remote IPC 
doug@ubuntu:~$ 


Thanks doug...

---


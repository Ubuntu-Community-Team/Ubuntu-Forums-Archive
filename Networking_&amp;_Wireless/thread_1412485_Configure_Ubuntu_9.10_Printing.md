---
title: "Configure Ubuntu 9.10 Printing"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by nadarm on 2010-02-21
[FONT=Arial][SIZE=4]I have Ubuntu 9.04 installed on a Virtualbox.  I am using Norton Security Suite.  The problem is I cannot see my windows printer nor can I attach to a windows share.  

Is there something I need to configure in the Norton Security Suite to allow the connection or is it something else?
[/SIZE][/FONT]

---

### Post by johnson.d on 2010-02-22
Is the printer/file share visible/usable when you disable Norton Security Suite?

---

### Post by nadarm on 2010-02-23
[SIZE=4]Yes, I have disabled the Norton Security Suite and I still cannot see the Windows Shared Printer.[/SIZE]

---

### Post by syncmasterpt on 2010-02-23
Is your on your virtual machine the network interface available, with an IP?

---

### Post by nadarm on 2010-02-23
[SIZE=3]Good question.  Please keep in mind I am new to Ubuntu.
Below is the information which appears does not have my address that I use on my network.  192.168.1.x
I however, am using the Sun VirtualBox to setup Ubuntu.

How do I fix this??

eth0      Link encap:Ethernet  HWaddr 08:00:27:0c:ca:cb  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe0c:cacb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1984 (1.9 KB)  TX bytes:12817 (12.8 KB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

[/SIZE]

---

### Post by johnson.d on 2010-02-24
Seems like you are using NAT networking for your VM.

If the printers and the share you are talking about are connected to the host OS itself, you cannot access both the printer and the share. In this case you can add another network interface in virtual box, which is host only connection, to access your windows share and the printer. This can be done using the following steps:

1) When the VM is in 'Powered off' condition, at virtual box window right-click on the Ubuntu 9.04 VM and click settings.
2) A window will open, click on Network and you will see four tabs- Adapter 1 to 4.
3) Click on Adapter 2, Check 'Enable Network Adapter'.
4) 'Attached to' drop down will highlight and you can select 'Host-only Adapter'.
5) Click OK and start the VM and try again.

If the Printer and the share are present in another machine other than your host machine, You can use the present setting and do the following steps:

Connecting to the printer:
1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click New.
3) At 'Enter Device URL' enter "smb://<ip-address>/<Printer-share-name>.
4) It will prompt for driver selection. Select the appropriate driver and continue suitably and finish the process.
5) Now you can try printing from the printer.

Connecting to the share:
1) Go to gnome menu-> Places-> Connect to server.
2) A window will open.
3) Drop down 'Service Type' and 'click Windows share'
4) And enter the details of the Windows machine and try again.

---

### Post by nadarm on 2010-02-25
[SIZE=3]Thank you for your help.  Your directions worked perfectly![/SIZE]

---

### Post by nadarm on 2010-03-05
[SIZE=3]I can connect to my printer as well as the Windows Share.  If I go to Places, Network and click on Windows Network, I do not see my other computers listed here.  Is there something else I need to configure to see the other computers on the network?[/SIZE]

---


---
title: "Help with RTL8187B"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by satan22o4 on 2009-02-22
Hello I'm new to ubuntu:D, Its been 20 days since I have installed Ubuntu 8.10, Now the problem is my RTL8187B USB internet doesn't work at all. I know its buggy in unix systems. It worked for sometime back in this month but only for 4 minutes or less.:( Now the problem is I have searched the whole thread and even tried "5.5 fixed thing" but .... Still my network doesnt work. It detects that I have internet connection with 30% but never connects it. I even mailed the realtek people and I recieved the latest drivers which they said will work with my Ubuntu 8.10 but the problem is I dont know how to use these drivers. I have attached the drivers too for you guys to help me out. Too help me better here is my output of ISUSB and ISPCI, I'm really new to unix based systems so kindly try to explain it I'm a complete idiot. LOL.


> fayaz@ubuntu:~$ lsusb
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fayaz@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
fayaz@ubuntu:~$ 




Thank you. I would love if you will guys help me out. Thank you very much. I love Ubuntu but life without internet is like hell. Kindly check the attachment of latest UNIX drivers and see if you can help me install the drivers and we can do the stuff to make this RTL8187B work for all. Im posting from my XP, If you need me to do anything I would love to switch to Ubuntu and do the thing.

---

### Post by kestrel1 on 2009-02-22
You need to unpack the file in the zip file & then unpack that file to a directory.
cd to the folder that is created & type```
sudo make
```
When that completes type```
sudo make install
```
You can then reboot your machine. The driver should be installed.

---

### Post by satan22o4 on 2009-02-22
Sorry dint get? What actually i have to do? I mean I can unzip the folder but where to put all those files?

Do should I go to terminal and then type " sudo make ? Thats it? how will it upload the selected directory ?


And is there any other solution. I have heard drivers don't work on this RTL8187B.

---

### Post by satan22o4 on 2009-02-22
Ok, I got what to do now. But how to cd to the folder. I mean how can I make terminal go to the selected drive and detect all the things in that driver folder to install?

---

### Post by Outdoor83 on 2009-02-22
Ok, I'll step-by-step this.

Save the drivers into your home directory:  /home/myusername.

You shouldn't copy / paste commands that anyone ever gives you over the forums (they can make you torch your box if they're in a bad mood) so you probably want someone else to look over these commands and verify that they're OK (they are, but don't take my word for it)

Type the following into the prompt:

> 
cd
mkdir deleteme-forums
cd deleteme-forums
mv ../rtl8187B_linux_26\[1\].1039.1107.2008.zip .
unzip rtl8187B_linux_26\[1\].1039.1107.2008.zip
tar xzf rtl8187B_linux_26[1].1039.1107.2008.tar.gz
cd rtl8187B_linux_26.1039.1107.2008/
make
sudo make install


Then reboot your machine.  If the drivers work as they should, you should be in business.

Assuming this all works: every time you upgrade your kernel on your machine (you see anything with 'kernel' in the name when updating the packages on your system, probably through Synaptic), you're going to have to repeat these steps.  So keep that .zip file around.

---

### Post by satan22o4 on 2009-02-22
Thanks Im going to Ubuntu and doing this. See if it works. :) But I dint get the comand "delete-me forums" lol What ever it is Im giving it a try.

---

### Post by satan22o4 on 2009-02-22
Ohhh my God this method worked dude. I think now its time to change the wiki page where it describes all the methods people try. The best method is to install the latest drivers in my post. Damn its working :) I'm happy. Thank you all who helped. 

Thread closed and solved.

---

### Post by kestrel1 on 2009-02-22
Sorry I never gave a step by step like Outdoor did, but good job.

---

### Post by satan22o4 on 2009-02-22
But this method worked. Hey now im in other problem. I can surf the internet very good. But when I used in windows some time I had to renew the ip to get it working so how do i do it in Ubuntu ? And other question is i was getting 40 kb download speed in XP but 10 or less in Ubuntu :(

---

### Post by satan22o4 on 2009-02-22
*BUMP* Need a quick reply please :D

---

### Post by kestrel1 on 2009-02-22
I believe this will release & renew your IP address```
sudo dhclient
```
However, with most DHCP servers there is a lease time, so you may well get the same IP address again.
You may be able to force the release of the IP with```
sudo dhclient -r
``` & then use```
sudo dhclient
```
to renew the IP address.
Not sure why your download speed has decreased, but it could be something with your ISP's servers at the time or the amount of users in your area reducing bandwidth.

---

### Post by satan22o4 on 2009-02-23
Thanks for th ehelp of providing "ipconfig" thing. But I'm still facing the same problem. Still using the dual boot. When I switch back to XP the speed is so fine and good browsing but at Ubuntu its like almost dead. It takes 4 to 7 sec to open google :( Kindly help

---

### Post by kestrel1 on 2009-02-23
It could be iptables that is causing the problem. If you install Firestarter you should be able to configure iptables a bit easier with the gui.

---

### Post by satan22o4 on 2009-02-23
I'm completely new to ubuntu. Din't get what you mean :(

---

### Post by satan22o4 on 2009-02-23
Still getting slow speed. I uninstalled the ubuntu and re-installed it with Ubuntu 8.10. Installed the latest drivers but still facing with the slow speed. :(

---

### Post by kestrel1 on 2009-02-23
OK, to install firestarter do the following from a terminal:```
sudo apt-get install firestarter
```
Once Firestarter is installed go to Applications -> Internet -> Firestarter
This should open up the Wizard. I assume that you are getting your IP address via DHCP, so put a tick in the box next to this option. Click next & just make sure things are set to your settings. at the end click save.

---

### Post by satan22o4 on 2009-02-23
Damn I finally fixed the slow speed proble. I dont want to start the new thread but I'm in new trouble. Some how I updated my Ubuntu. After updating the kernal changed to 2.6.27.11 but when I logged in my internet wasn't working, when I tried installing drivers they were not compatible. I switched back to older kernal while restatrting. 

Now I want to delete the new kernal. How do I do that as it doesnt support my New drivers.

---

### Post by kestrel1 on 2009-02-23
Instead of removing the new kernel, just re-compile the new drivers in the new kernel.
In other words, do what you did to get the drivers installed before.
How did you sort your speed problem? It may help others.

---

### Post by satan22o4 on 2009-03-28
Well speed worked it self some how !! may be some updates made it work. But new problem is that the new kernal still is buggy and I cant install the driver in that new kernal. It gives me some errors.

---


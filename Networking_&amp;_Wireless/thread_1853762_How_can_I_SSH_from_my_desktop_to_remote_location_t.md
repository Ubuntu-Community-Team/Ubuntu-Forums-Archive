---
title: "How can I SSH from my desktop to remote location to surf/email/etc remotely?"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by cilbuper on 2011-10-02
I am pretty sure that it is possible to run a SSH tunnel from one computer to another so that it looks like all the information is coming from the computer at the endo fo the tunnel (IP, etc).  The computer at the end will then pass all the info aback to my home computer allowing me to surf anonymously and without the fear of being tracked (at least back to where my SSH tunnel ends).  I figure if the SSH host doesn't leep logs this should be pretty good, would it not?  
I can see this as being a benefit for at work when on the rare occasion I need to check personal email or something.  

Can anyone help explain how to do this?  I am using Putty and I keep getting confused with the setup.  

Thanks a lot!

---

### Post by joneberger on 2011-10-02
If you use

ssh -X username@host

the X windows are ported through the SSH protocol and you can browse, email, etc. (run code, perform server and network maintenance, etc.) remotely.  The more bandwidth you have, the better.

---

### Post by cilbuper on 2011-10-03
> **joneberger said:**
> If you use

ssh -X username@host

the X windows are ported through the SSH protocol and you can browse, email, etc. (run code, perform server and network maintenance, etc.) remotely.  The more bandwidth you have, the better.

Am I correct that this is only for a machine that is running Linux of Mac?  I need something that will  route a windows machine through a linux remote server.  


I found this site and tried it word for word and it doesn't seem to work.  I've spent years trying to figure this out and have yet come to master it. Everyone says's "oh it's so easy" just do this...  but "this" never works for me....

---

### Post by SeijiSensei on 2011-10-03
Look into [OpenVPN]("http://openvpn.net/").  It supports tunnels on Windows, Linux, and Macs.

---

### Post by 2F4U on 2011-10-03
VNC or FreeNX would allow you to remotely control a computer:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by cilbuper on 2011-10-03
but none of this gets the good old anonymous SSH secure tunneling does it?

---

### Post by matt_symes on 2011-10-03
Hi

> **cilbuper said:**
> but none of this gets the good old anonymous SSH secure tunneling does it?

TOR is anonymous and secure. VPN's are secure. VNC is secure if you get a secure version.

You can just create a shell account with someone like cbj.net and route your traffic through that ssh tunnel if you want by configuring your browser. It will make browsing slower though.

There are loads of tutorials on the net to do this. What have you tried so far ?

Kind regards

---

### Post by anur.bhargav on 2011-10-03
> **cilbuper said:**
> but none of this gets the good old anonymous SSH secure tunneling does it?

See If the following procedure works.(Assuming Inter networking between a Desktop and a Laptop, works on any 2 computers)

1. First you need to install (SSH), on "both computers" open a terminal by going to > Applications > accessories > Terminal and type in this code:
```
sudo apt-get install ssh
```
it will ask you for your password, make sure to enter the correct password.

----Ur on the DESKTOP----
2. Next setup the folder you want to share (On Desktop). I called mine (TED Talks) and is on the desktop of one of the computers but you can put it anywhere, like your Home folder.

3. Right click the folder and choose ‘Sharing Options’. Make sure "Share this folder" is checked and has a name. 
Also check "Allow other people to write in this folder" if you want to be able to modify > add > or remove files from your main computer.

4. You will be prompted to install Samba, just follow the steps. After it is done, you will have to logout and log back in.

5. A Nautilus window will popup asking you if you want to add permissions, hit "add the permissions automatically". thats it you're done creating your share folder.

6. Next get the IP address from your Desktop computer that you want to share files with "where you made the share folder"
Right click on the network icon in the top right of the screen and click on "connection information"

7. Make sure to write the "IP Address" down you will need it.

8. Now you can connect the two computers to share the folder. Switch to the Laptop(or whatever) now

----LAPTOP PART BEGINS NOW-----
Go to > Places > Connect to Server 

9. i.  Service type: Choose SSH
  ii.  IP address of the Desktop computer in the "Server" field
 iii.  Enter 22 in the "Port" field
  iv.  In the "Folder" field, enter the path of the folder you   created i.e /home/username/Desktop/Foldername
   v.  Under "User Name" enter the username of the second computer.
  vi.  You could make a "Bookmark" of your share, just click the checkbox next to Bookmark and name it may be 'SSH tunnel to Desktop'

10. Click Connect. It'll ask for the login password for the Desktop, enter it to connect.

12. Repeat Steps 2 through 11 on Ur laptop too. Now U can SSH to the Desktop computer.

13. If u just enter the IP address of the other computer and say connect u can see the whole of the other computer. Including all the drives (NTFS) u've mounted. (I'm assuming tht u are dual booting)

See all the screen-shots to understand better Or Download the Document that I've attached, its better organised (I've split it into 3 parts as the forum doesn't allow me to upload a Doc more than 195KB) :)

---

### Post by SeijiSensei on 2011-10-03
Just a reminder that the OP wants a solution that works with Linux servers and Windows clients.

> **cilbuper said:**
> **I need something that will  route a windows machine through a linux remote server.**

> **cilbuper said:**
> but none of this gets the good old anonymous SSH secure tunneling does it?

VPNs are encrypted, just like SSH.  OpenVPN lets you choose from a selection of ciphers, with blowfish as the default.  If you're connecting through your home server, you won't be "anonymous."  All your external connections will be traceable back to that server.  Tor is better at protecting your anonymity, but I discourage people from using it for simple browsing or, worse, torrenting.  Tor was designed to protect the identity of political activists and others who might face persecution for expressing their opinions.

---

### Post by matt_symes on 2011-10-03
Hi

> **SeijiSensei said:**
> Just a reminder that the OP wants a solution that works with Linux servers and Windows clients.

This is a good point!

Use Putty to connect to an ssh server somewhere. I have one on cbj.net where you can open free shell accounts. 

I actually flashed my home router with dd-wrt, enabled ssh on the router with keys and set up its wan ip address to a name using dyndns and opened the correct ports on the router (if you go down this route understand the risks of bricking your router).

When the ssh tunnel is open, point your browser at the ssh port you opened. (firefox)  Edit->preferences->Advanced->network tab.

[http://oldsite.precedence.co.uk/nc/putty.html](http://oldsite.precedence.co.uk/nc/putty.html)

Like SeijiSensi, I also like VPN's. They (the servers) can also be configured on routers flashed with dd-wrt (on at least some of the builds). Client are trivial to set up under windows.

I think the main point here is you have a number of options to choose from.

Kind regards

---


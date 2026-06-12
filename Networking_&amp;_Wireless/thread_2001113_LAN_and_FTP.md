---
title: "LAN and FTP"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by acefromspace on 2012-06-10
I have a computer with Ubuntu 10.04 (lucid lynx) connected with a crossover network cable to another "computer" (it's actually a "modded" device... let's just call it "the box") I just need to do a simple lan connection to transfer files using FTP. I have done this before (using simple manual settings) but can't remember how (still learning about networks) The "box" also uses a linux system, and has settings for network: DHCP, manual (static), and FTP is enabled. The "box" has IP address 192.168.0.103 (subnet mask 255.255.255.0) How do I setup connection and setup FTP? I'm interested in auto DHCP but really want to do manual to learn more about how this works (I need specifics about IPs, gateway in creating manual connection) Also need walk thru on setting up FTP (used to gFTP but now using filezilla) Should I use Places, connect to server? How is this different from edit connections? I've searched and read many threads, but just getting more confused because I don't understand the basic terms (gateway, host, server, ect.) and which IP to use for my computer. Sorry, I don't usually ask for spoonfeeding, but I really need to transfer these files (my wife is patiently waiting)

---

### Post by Lars Noodén on 2012-06-10
The easiest, and secure, way to do the file transfer is to use SFTP instead.  Set up the package OpenSSH server on one machine and then use FileZilla to make the SFTP transfer from the other.  It's very easy.  FTP is not secure and is complicated to set up, so it should be avoided in cases like this.

---

### Post by acefromspace on 2012-06-10
Lars. I don't care about security. This is a simple LAN connection, no other systems or internet will see this. Also, please understand that the "box" has OS and network settings, but I cannot add any programs or other software (I'm avoiding mentioning what it is... hoping some will catch the hint... the "box") I use the "box" to watch videos on my old CRT TV because it is has TV connection and works great (it was gift from a friend... "modded" game system)

---

### Post by Lars Noodén on 2012-06-10
Right, and the other reason I mentioned OpenSSH is that it is the *easiest* to set up.  You install FileZilla on one machine and OpenSSH-server on the other and then connect the two.  When you're done, you can uninstall.

Edit: Sorry.  If you can't add programs then that solution won't work.  Can you clarify which programs (e.g. DHCPd and FTPd) are on which devices?  It may be just a matter of connecting the two and letting DHCP pick up an address before connecting.

---

### Post by acefromspace on 2012-06-10
Lars, thanks for replies. OK I will say it: the "box" is an older xbox (not 360) that is "soft-modded" to function as computer. Like I said, I have done this before so I know it works, but can't remember the settings I used to setup manual connection. To be more specific: xbox has IP 192.168.0.103 so should my computer have IP 192.168.0.x or 192.168.1.x , and what do I enter for gateway? Also, what IP do I use as host for FTP? No router, just crossover cable from my computer to xbox. I know this should be simple, but never quite understood networking or am I just missing something? By the way, I have XBMC and also older evox on xbox. A friend used to help me with networking, but he is tired of my "fifty-something" brain forgetting, so I need to learn this for myself. Can anyone point me to a tutorial on basic networking for Ubuntu?

---

### Post by HarryTorry on 2012-06-10
Your computer should be on the 192.168.0.xxx. In this case, 192.168.0.104 will do perfectly.
You don't need a default gateway on either of your machines.

That's for the networking part, I'll be able to help further once we know what software you have available!

---

### Post by Lars Noodén on 2012-06-10
If one computer has IP 192.168.0.103 the other computer have should have IP 192.168.0.x.  If one computer has a DHCP server, then the other computer can get an address from it automatically.  From there, connect directly to the IP number for the machine with the FTP server.  

Which box has the FTP server and which box has the DHCP server?

---

### Post by acefromspace on 2012-06-10
harry, thanks for the address tip... I tried 192.168.0.101 and 192.168.0.1 , so you are saying the last number should be higher not lower? You asked about software... do you mean like gftp or filezilla on my computer, or do you mean the xbox? It has wired network, settings for network and ftp like most computers, and has xbmc and evox... it was a gift so I don't know everything about how it works. Just to clarify: I get into edit connections, add my xbox and enter IP 192.168.0.104 , mask 255.255.255.0, and leave gateway blank (or zeros?) 
lars, "Which box has the FTP server and which box has the DHCP server?" That's my problem, I don't fully get the meaning of server, that's why I'm asking. Both can connect dhcp or manual, both can do ftp. I need to control transfer from my computer. thanks for helping.

---

### Post by TVTrukChik on 2012-06-10
It doesn't matter if that last number is higher or lower... just that it's not the same as the other device.  You're right about the netmask and gateway.  

If you only have the PC and the "box", then you probably don't have either one set up as a DHCP server.  In a home network, the router usually acts as the DHCP server.  So you'll need to use static IPs, as you are doing.  And it sounds like the "box" is the FTP server in this case, since you're using your PC to transfer files to/from it.

I just noticed that you asked if you should add the "box" in your network connections settings... There should be one connection there already, called something like Eth0.  That's your wired Ethernet connection.  Click on it, and then select Edit.  You want to change the settings on the tab labeled IPv4 Settings.  Make sure the Method is set to manual, then enter the numbers as described above.

Then, to connect to your "box"... do you know if you have to enter a username and password?  In gFTP, you put the IP address of your "box" (192.168.0.103) where it says Host.  I haven't used FileZilla in ages, but it should be similar.  Or in Nautilus you can select Connect to Server, and put the IP address of the "box" where it says Server.

---

### Post by HarryTorry on 2012-06-10
192.168.0.101 will work, 192.168.0.1 **SHOULD** work!

Just to add to TVTruk's post, in FileZilla you can just open the Site Manager (ctrl + S, and also in the File button at the top left), and add a new 'site' there. In your case, you can treat the site as the other machine!

---

### Post by acefromspace on 2012-06-10
YVTrukChick, Thank you so much for explaining in simple terms! That's how I understood this, and that's how I remember doing it before... maybe just have some setting wrong. I will try again. I do have a router and regular cables so I can do it that way also (I assume using dhcp) I found a very simple tutorial on you tube that is helping with the terminology... yes, the xbox is the server and my computer is the client (did I get that right?) So, I can use gftp OR places, connect to server... basically the same? Also, yes the box has user and password, both xbox (too easy!) I will write down details this time including all settings and error messages. If it works, I will have all settings tatooed on my forehead so I can't forget (backwards, of course, so I can read it in mirror) Also, haven't tried yet, but another thread said to use file manager and type [ftp://192.168.0.103](ftp://192.168.0.103) , does that sound right?

---

### Post by acefromspace on 2012-06-10
Tried again.. it works! I think I found the problem. When I was editing my xbox connection before, I tried disable networking first (don't think that was the best way), then after editing connection I enabled networking. This time I left enable networking and clicked disconnect, edited, then clicked on xbox connection and it worked. ftp also worked fine. Somehow my changes were not being applied... I noticed this a few times, but it didn't click (in my brain). I would mark this as solved, but need someone to confirm this was the problem. BTW, I used the old evox on the xbox (because it's so simple) but I know it also works with xbmc. The truth is, I'm getting a scan converter so won't need the xbox anymore, but the wife wants to keep it anyway. She will be home soon to find the xbox is loaded up ready to go! Thanks again to all.

---

### Post by TVTrukChik on 2012-06-10
Glad you got it working!  I'm not sure about your last question, I've never tried doing it that way.  I guess it makes sense that the settings you applied while networking was disabled wouldn't stick, though.

Yes, using Nautilus (file manager) and typing in ftp:// and the IP address is basically the same thing as using the Places/Connect to Server option.  

If you are going to hook up to your router and use DHCP, be careful.  The "D" in DHCP stands for "Dynamic", which means that the IP address won't always necessarily be the same.  Then you get in trouble when you're trying to access a device by IP address.  

You *can* set the device to DHCP and then create what is called a "reservation" in your router.  That means that the device will take whatever IP is assigned to it, but your router will always assign a particular address.  That sounds confusing, but think of it like this:  On your network, the device will always have the same address.  But if you pick it up and take it to a friend's house, it will get an address compatible with their network, without you having to change any settings.

---


---
title: "Wireless Print Server with Brother MFC440CN Printer"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2010-01-18
EDIT: Please see solution in final response.

Howdy Y'all,

So for awhile I had a Brother MFC-440CN multifunction printer hardwired to my Linksys router (ethernet cable). When it was hard wired, it seemed to run just fine and dandy on my Ubuntu 8.04 box with the following setup:

```

Static IP Address: 192.168.1.205
Device URI: lpd://192.168.1.205/binary_P1
Make and Model: Local Raw Printer (or something like that)

```

When I had the printer ethernetted to the router with the above configuration, as I said, it worked great. I had to put the binary_P1 queue onto the end of the device URI in order to get it to print legitimate stuff and not some binary mangled garbage (lots of smileys and wingdingish type symbols). 

Recently, I purchased a WPSM54G Linksys print server to use with this multifunction printer so that I wouldn't have to ethernet it to the router anymore. However, I am having trouble setting the print server up to work on Ubuntu. At first, I tried just manipulating the IP address in the device URI to the new print server address. That didn't work. I should note that I already setup the print server and printer with my roomate's Window's XP laptop and that everything is working just fine with that box. That is to say, the print server now has the following setup on my network:

```

Static IP: 192.168.1.202
user: [blank]
PW: ********
Printer: Brother MFC440CN hosted successfully, connected via USB cable.

```

This setup works just fine with the Windows XP box as I noted. I can log into the server directly by typing the IP address into the browser bar, just like I can my router. I can play around in it there and manipulate it. I just can't seem to print to it.

So, after trying to futz with the device URI I just decided to do a raw reinstall. I deleted the printer from my CUPS setup and removed all of the driver packages. I then reinstalled the driver packages and logged onto my cups web configuration UI at:

```

http://localhost:631/

```

Once here, I attempted to add a new printer. I input the appropriate name and description. I have tried both internet printing protocols (http and ipp). I selected the appropriate model from the make and manufacture list so as to install the correct drivers. 

The only problem I am having is figuring out the new, appropriate device URI. Essentially, I am running into two problems. First, no matter what queue suffix that I list on the URI (P1, L1, binary_P1,  binary_L1), the printer started printing all sorts of wingdings and garbage when I try printing again. Secondly, when I do try to print test pages from my linux box, I get mixed results of the responsiveness of the printer. That is, sometimes it prints immediately, sometimes I have to power cycle the printer and print server, sometimes the job eats up the whole print queue and makes it so that I can't print even from the windows box without doing multiple power cycles. 

So, that being said, here are the various device URI's I have tried:

```

http://admin:<PW>@192.168.1.202:631/ipp/binary_P1
ipp://admin:<PW>@192.168.1.202:631/ipp/binary_P1
ipp://admin:<PW>@192.168.1.202:631/ipp/P1
ipp://192.168.1.202:631/ipp/binary_P1
ipp://admin:<PW>@192.168.1.202:631/ipp/P1
ipp://admin:<PW>@192.168.1.202/ipp/binary_P1
ipp://admin:<PW>@192.168.1.202/ipp/P1
ipp://192.168.1.202/ipp/binary_P1
ipp://192.168.1.202/ipp/P1
ipp://192.168.1.202/binary_P1
ipp://192.168.1.202/P1

```

And I have probably tried a few more configurations. I attached the admin:<PW>@ prefix to the URI because, according to [this thread: 294136](http://ubuntuforums.org/archive/index.php/t-294136.html), that should help alleviate the concern regarding the clogging of the printing queue. Apparently, using a web interface with the print server requires the input of the logon name and password. So, that's how I tried to input it into the device URI. Of course, it's not working. However, I did notice that when I load those particular URI's (the one's with admin:<PW>@), the URI shown in the printer properties does not have that prefix. I figured it got dropped for security purposes but I honestly don't know.

So I guess what it boils down to is: How do I use a WPSM54G Linksys Wireless G Print Server with my Brother printer that I had, at one point, working correctly on my Ubuntu box via hardwire. Did I miss a step? Did I fubar something entirely? Is my queue suffix (P1, binary_P1, etc) inappropriate? Can anyone tell me what I am missing?

Just for giggles, I ran:

```

nmap -sV 192.168.1.202

```

...to port scan the print server and this was the output:

```

Interesting ports on WPSM54G (192.168.1.202):
Not shown: 1709 closed ports
PORT     STATE SERVICE    VERSION
23/tcp   open  telnet     Micronet or Linksys print server telnetd
80/tcp   open  http?
515/tcp  open  printer?
631/tcp  open  ipp?
9100/tcp open  jetdirect?
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at http://www.insecure.org/cgi-bin/servicefp-submit.cgi :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port80-TCP:V=4.53%I=7%D=1/17%Time=4B53A23C%P=i686-pc-linux-gnu%r(GetReq
SF:uest,8D,"HTTP/1\.0\x20401\x20Unauthorized\r\nServer:\x20PRINT_SERVER\x2
SF:0WEB\x201\.0\r\nContent-type:\x20text/html\r\nWWW-Authenticate:\x20Basi
SF:c\x20realm=\"WPSM54G\"\r\n\r\n401\x20Unauthorized");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port631-TCP:V=4.53%I=7%D=1/17%Time=4B53A23C%P=i686-pc-linux-gnu%r(GetRe
SF:quest,8D,"HTTP/1\.0\x20401\x20Unauthorized\r\nServer:\x20PRINT_SERVER\x
SF:20WEB\x201\.0\r\nContent-type:\x20text/html\r\nWWW-Authenticate:\x20Bas
SF:ic\x20realm=\"WPSM54G\"\r\n\r\n401\x20Unauthorized");
Service Info: Device: print server

```

Should I maybe be using port 80 for the http device URI?

Any insight would be greatly appreciated. I feel like I am very close but am just missing some minor detail. Please help.

Cheers,
Brady

---

### Post by BJ_Covert_Action on 2010-01-19
24 hour bump. Sorry guys, but I really need some input.

---

### Post by BJ_Covert_Action on 2010-01-22
Any ideas at all?

---

### Post by myth1914 on 2010-01-22
Going off what you have for your XP config, shouldn't your cups be something like

lpd://192.168.1.202/binary_P1

---

### Post by BJ_Covert_Action on 2010-01-22
I am pretty sure I tried that one and, so far, it has resulted in more wing ding prints. I can try it again. I don't know that the Linksys print server supports lpd protocol...

I kind of figured that the server itself needed http or ipp in the URI to work properly.

---

### Post by myth1914 on 2010-01-22
> **myth1914 said:**
> 

lpd://192.168.1.202/binary_P1

From CUPS config concerning Linksys print servers:

**Configuring Linksys Print Servers**

  The Linksys print servers can be configured using BOOTP or DHCP. Like older Axis print servers, an additional step must be performed to configure the TCP/IP portion of the print server for use with CUPS.
  Each print server contains a configuration file named CONFIG that contains a list of network parameters used by the server. To modify this file you must first download it from the print server using the ftp(1) program:
  ftp -n ip-address
Connected to ip-address.
220 Print Server Ready.
Remote system type is Print.
ftp> get CONFIG
local: CONFIG remote: CONFIG
200 Command OK.
150 Open ASCII Mode Connection.
WARNING! 68 bare linefeeds received in ASCII mode
File may not have transferred correctly.
226 Transfer complete.
##### bytes received in #.## seconds (##### Kbytes/s)
ftp> quit
221 Goodbye.
 Next, edit the file with your favorite text editor and locate the lines beginning with:
  0100 L1_PROUT:P1
0120 L2_PROUT:P1
0140 L3_PROUT:P1
 Change the port number for each parallel and serial port on the server as follows:
  0100 L1_PROUT:P1
0120 L2_PROUT:P2
0140 L3_PROUT:P3
 This maps each virtual printer with a physical port. Save the file and then upload the new CONFIG file using the ftp command:
  ftp -n ip-address
Connected to ip-address.
220 Print Server Ready.
Remote system type is Print.
ftp> put CONFIG
local: CONFIG remote: CONFIG
200 Command OK.
150 Open ASCII Mode Connection.
226 Transfer complete.
##### bytes received in #.## seconds (##### Kbytes/s)
ftp> quit
221 Goodbye.
 Your Linksys print server is now ready for use!

---

### Post by myth1914 on 2010-01-22
> **BJ_Covert_Action said:**
> I am pretty sure I tried that one and, so far, it has resulted in more wing ding prints. I can try it again. I don't know that the Linksys print server supports lpd protocol...

Printing is the key though... If you've been getting wing-ding, have you tried a different print driver to correct that?

I had a similar issue with my Netgear 606 print server.  I had to use a different printer driver.

---

### Post by BJ_Covert_Action on 2010-01-22
Holy crap, I didn't know it was possible to interface with a server like that through my command line. Where did you find that information if you don't mind my asking?

---

### Post by myth1914 on 2010-01-22
Sorry for yet another quick reply, have you installed the MFC440CN driver package?

aptitude -y install brother-cups-wrapper-bh7

---

### Post by BJ_Covert_Action on 2010-01-22
> **myth1914 said:**
> Printing is the key though... If you've been getting wing-ding, have you tried a different print driver to correct that?

I had a similar issue with my Netgear 606 print server.  I had to use a different printer driver.

Hmmm, well when I originally had it configured via hardwire it was displaying that Local Raw Printer as the driver, or whatever that option was....Now I am trying to use the official MFC440CN driver from Brother, so, yeah, maybe that is the problem. That's a good idea for another thing to dink around with.

---

### Post by BJ_Covert_Action on 2010-01-22
> **myth1914 said:**
> Sorry for yet another quick reply, have you installed the MFC440CN driver package?

aptitude -y install brother-cups-wrapper-bh7

Yes, and please don't apologize, this is very helpful.

---

### Post by myth1914 on 2010-01-22
> **BJ_Covert_Action said:**
> Holy crap, I didn't know it was possible to interface with a server like that through my command line. Where did you find that information if you don't mind my asking?

I'd love to say something inspiring that comes with experience, but the truth is I pulled it from the admin section of my CUPS server interface at <ipaddress>:631 as I was just in there playing with it this morning... my success is what drew me to your post...

---

### Post by BJ_Covert_Action on 2010-01-22
Intriguing. I don't think I ever poked around in the admin section much. I read some of the docs regarding URI formation, that was helpful, that's what gave me the idea of embedding the username and password in the URI to keep the queue from fussing up. I'll have to check that out when I get home.

---

### Post by myth1914 on 2010-01-22
Glad I could help.  I'll subscribe to this post as I will be playing with a similar setup soon and wouldn't mind the collaboration...

---

### Post by BJ_Covert_Action on 2010-01-22
Sounds good. I'll post sometime later this weekend to let you know if I got anything working.

Cheers,
Brady

---

### Post by BJ_Covert_Action on 2011-03-29
So, I realize this thread is over a year old, but I finally got around to figuring this problem out again, and I went through a combination of actions to make it work. I wanted to post the final configuration that worked, for anyone who was having trouble trying to install this printer on Ubuntu via a print server in the future.

So, without further ado, let me explain how I got this working. First off I actually have an MFC9440CN, not an MFC440CN. I think this same configuration will work for that model, but I am not sure. 

First and foremost I installed the appropriate brother driver packages via Synaptic. These included the following

```

brother-cups-wrapper-ac
brother-lpr-drivers-ac
brother-lpr-drivers-common

```

I also included an install of all the packages synaptic suggested were required when I went to install those. 

After installing the drivers, I went to ```
http://localhost:631
``` via FireFox and I clicked on the Administration tab. From there, I clicked "Add Printer." and I proceeded as follows.

Under the "Other Network Printers" Option, I selected "Internet Printing Protocol (http)" and clicked continue. Next I was prompted for the printer URI. This is the important step. For reference, my printer server was configured on my home network at the IP Address: 192.168.1.202. This is not the same IP address as my printer when it is connected to the network directly. However, the printer server URI is the appropriate one to use. Thus, the URI I input was as follows:

```

http://192.168.1.202:631/ipp/binary_P1

```

The final port suffix on the end was crucial to get my printer working correctly. After inputing the URI (again, using the printer server address for the root host, rather than the printer itself), I clicked continue. 

After that, the rest became pretty self explanatory. I input the appropriate descriptions on the next page, and then I went on to select the make as Brother, and the model form the drop down model list as MFC9440CN. After clicking through these two prompts, I clicked "Add the printer..." or whatever the final button was, and CUPS configured the printer correctly.

I was then taken to an admin page where I could print a test page using the Maintenance drop down menu. It printed out fine and dandy and printed like a dream.

So that's it. The URI I used is listed above. I realize this thread was late coming, but better late than never right? Hopefully this helps someone out.

Cheers,
Brady C. Jackson

---


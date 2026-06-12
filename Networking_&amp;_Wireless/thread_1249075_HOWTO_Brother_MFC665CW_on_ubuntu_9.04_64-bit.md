---
title: "HOWTO: Brother MFC665CW on ubuntu 9.04 64-bit"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2009-08-24
I am writing this as I have read over countless posts and googled tons of times with little success.  I finally figured out how to install my MFC665CW on my ubuntu boxes, so I would like to share with others.  

First, download both the LPR driver and CUPS driver from:
[http://solutions.brother.com/linux/en_us/download_prn.html]("http://solutions.brother.com/linux/en_us/download_prn.html")

Search for 665CW and click on each driver corresponding to the .deb 665CW. At the time of this writing, they appear as:

```
LPR driver 	deb 	1.0.1-1 	1087 KB 	2008.Feb.13
cupswrapper driver 	deb 	1.0.1-1 	13 KB 	2008.Feb.13
```


Then, open a terminal and cd to the directory where the files are.  If you're on 64-bit like me, first run: 

```
sudo apt-get -y install lib32stdc++6
```
which is a prerequisite to install the drivers.  

Next, you need to create a few folders that will prevent the install from completing successfully.  

```
sudo mkdir /usr/share/cups/MFC-665CW
sudo mkdir /usr/share/cups/model
```

Now, for the actual install.  
```

sudo dpkg -i --force-all --force-architecture mfc665cwlpr-1.0.1-1.i386.deb
sudo dpkg -i --force-all --force-architecture mfc665cwcupswrapper-1.0.1-1.i386.deb
```

Now, if you want to access it over the network(i.e. not just via usb), you need to change the URI to point to the I.P. address that is set up in the printer. 

*replace 192.168.1.50 with the address of YOUR printer. *
```
lpadmin -p MFC665CW -v "lpd://192.168.1.50/binary_p1"
```

After that, voila, all should be up and running.  I assume that following something similar would work for several other Brother printers as well.

---

### Post by BJ_Covert_Action on 2009-08-28
Hey, I realize I will probably be bumping an old thread, but this really helped me get my Brother MFC-440 CN configured over the network. Between this post and [Brother's Instructions](http://solutions.brother.com/linux/en_us/) I managed to get my printer recognized on the network and configured so that I can print to it from my ubuntu desktop.

However, I am having problems with one last thing. Whenever I try to print anything over the network to the brother printer, whatever I try to print gets garbled and comes out of the printer looking something akin to the wingdings font. I have both my desktop and printer connected to a Linksys 54g wireless router. I hacked the router open a while back and flashed the appropriate DD-WRT firmware onto it. I am afraid this might be causing some kind of data translation problem as the printed junk resembles something akin to binary data (the raw, ugly, machine code stuff, not the nice 1's and 0's). 

Has anyone ever seen a printer do this before through CUPS?

One thing I should mention is that the first time I tried to install the LPR debian package using the dpkg command, it ran into an error of not being able to find a 

```

/var/spool/lpd

```

directory. As such, I did a ```
sudo mkdri /var/spool/lpd
``` command to create one and, thus, the package install appeared to work fine. Am I maybe missing some sort of necessary lpd dependancy?

Any help or insight on this would be great. Thanks for taking the time to read and any help you can provide in advance.

Cheers,
Brady

---

### Post by senor_smile on 2009-08-28
I am using an old Linksys router flashed with DD-WRT that I am using as a wireless bridge and am printing just fine through it.  My main router is a standard WRT-54G.  I am glad that this helped someone else.  Hopefully, someone else has run into the problem you're describing and can shed some light.  

Are there any other windows machines/ any machines at all that have recently successfully printed to the the printer?  That would at least verify that it is possibly something to do with your setup, and not the printer itself.  

--shaun

---

### Post by BJ_Covert_Action on 2009-08-28
Well there is a windows XP laptop that I have been trying to get connected to the printer as well. It connects to the router just fine, but can't seem to see the printer through it at all for some stupid reason or another. I may end up having to do an nmap of each to see which ports are open and which aren't. I'd really rather avoid that though.

When I run the standard install instructions for the XP OS, the driver install test fails at the end. I need to do a little more research on why this is happening as the windows setup is 'supposed' to be easier than the Linux one.

There isn't much in the way of troubleshooting or techincal docs with the printer so I am going to need to dig more on line (damn user's manuals being written for the lowest common denominator). 

Another thought occurred to me, my Ubuntu desktop (8.04) is connected to the router via an encrypted wireless connection, as is the laptop. The printer, however, is hardwired to the router and, therefore, does not log onto the router with encryption protocols (to my knowledge). Would this possibly be causing the jumbling?

Hopefully someone else will have experience with this as you said. Thanks for the response.

Cheers,
Brady

---

### Post by ddgleasing1 on 2010-02-23
I'm a new Ubuntu 9.10 user and, following your instructions, I did get quite far on getting my MFC665CW printer at least to say "receiving data" when I push the Print button, but nothing comes out and the "receiving data" message never terminates. The Document Print Status message under the print icon indicates status:completed-printer warning with this message 'com.apple.print.recoverable.'

What am I doing wrong?

---

### Post by jcblll on 2010-04-06
Thanks for your post, this reduced my 64 Bit install time considerably.

---

### Post by senor_smile on 2010-04-06
I haven't been in the house where I had to connect to the brother printer for a while now.  Was there anything you had to do differently than I did to get connected?

---


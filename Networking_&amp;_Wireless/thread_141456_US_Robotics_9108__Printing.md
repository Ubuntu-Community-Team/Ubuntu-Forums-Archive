---
title: "US Robotics 9108 / Printing"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by MSDaytona on 2006-03-08
I succesfully installed my ADSL US Robotics 9108 and I can connect without
any problem to the internet etc.

Now I want to use the printer server features of the modem and attach via
the modems USB port my HP Business Deskjet 1100.  Whilst the printer works
perfect with an parallel port connection, I can't get that working via the modem.

I have used in Ubuntu the PRINTER set-up feature ( under Admistration ) but without
any luck.

Under  Windows XP ( I have a dual boot system ) the printer works perfectly via the
USR9108 server feature. Under wndows I had to use the following address:
http://192.168.1.1:1631/printers/"Printername"

What am I doing wrong ?

---

### Post by MSDaytona on 2006-03-09
Problem solved.

I configured the printer as an IPP one and after re-starting Ubuntu the printer was working.

---

### Post by sven1122 on 2006-10-08
Hi there,

could you excatly descipe what you did? I got the same router, but however i configure the port doesn't work. I tried 
ipp://192.168.1.1/printers/printername
as well but it doesn't work out. Could you please help me?

Regards

Sven

---

### Post by CassioBunana on 2007-01-02
Hi guys, have you  find out how to solve this problem?
I've set up CUPS with ipp//192.168.1.1:1631/printers/name but no printing seems to be possible....each document enters the spooling queue but nothing happens!
It seems just a connection problem...like firewall or similar...any idea?

Please MSDaytona, could you post more details about how did you solve the problem?

---

### Post by thedox on 2007-03-01
> **CassioBunana said:**
> Hi guys, have you  find out how to solve this problem?
I've set up CUPS with ipp//192.168.1.1:1631/printers/name but no printing seems to be possible....each document enters the spooling queue but nothing happens!
It seems just a connection problem...like firewall or similar...any idea?

Please MSDaytona, could you post more details about how did you solve the problem?

same problem... :popcorn:  , now i need windows to print :(

---

### Post by pazzaTgreat on 2007-03-26
guys - I too am having this problem with my 100% perfectly reliable 9108a router. 

From other posts I gleaned that as the CUPS version advanced, something was changed in the IPP printing section.  The last known version that worked the 9108 was CUPS 1.2.0.

All I did was go to [www.cups.org]("http://www.cups.org") and download version 1.2.0.
unzip it and compile it as instructed 
(just cd to dir, execute ./configure and then type <make><Enter> )
then install it by typing <make install> <Enter>. 

Restart CUPS or reboot. 

<you can test your CUPS version by typing [http://localhost:631](http://localhost:631) in your browser, the CUPs administration web interface displays the version here>

Set up the printer as IPP on [http://XXXXXXX:1631/printers/printername](http://XXXXXXX:1631/printers/printername) and the printserver works again!

I haven't had any problems running the printer, and I have not noticed any broken dependencies at the moment. This install probably takes it out of auto update but do you want to update CUPS and have your printer stop working again. :confused: 

I am running Feisty Fawn beta on two machines and neither have any problems at the moment.

Hope you are helped

Paul.

---

### Post by kenns on 2007-04-01
> **pazzaTgreat said:**
> guys - I too am having this problem with my 100% perfectly reliable 9108a router. 

From other posts I gleaned that as the CUPS version advanced, something was changed in the IPP printing section.  The last known version that worked the 9108 was CUPS 1.2.0.

All I did was go to [www.cups.org]("http://www.cups.org") and download version 1.2.0.
unzip it and compile it as instructed 
(just cd to dir, execute ./configure and then type <make><Enter> )
then install it by typing <make install> <Enter>. 

Restart CUPS or reboot. 

<you can test your CUPS version by typing [http://localhost:631](http://localhost:631) in your browser, the CUPs administration web interface displays the version here>

Set up the printer as IPP on [http://XXXXXXX:1631/printers/printername](http://XXXXXXX:1631/printers/printername) and the printserver works again!

I haven't had any problems running the printer, and I have not noticed any broken dependencies at the moment. This install probably takes it out of auto update but do you want to update CUPS and have your printer stop working again. :confused: 

I am running Feisty Fawn beta on two machines and neither have any problems at the moment.

Hope you are helped

Paul.

Thx, here it works!
 (usr5461, deskjet710C with usb cable, ubuntu 6.10)
I had the same problem.

I hope it will also works on the new version of Ubuntu 7.04.

---

### Post by thedox on 2007-04-02
> **pazzaTgreat said:**
> guys - I too am having this problem with my 100% perfectly reliable 9108a router. 

From other posts I gleaned that as the CUPS version advanced, something was changed in the IPP printing section.  The last known version that worked the 9108 was CUPS 1.2.0.

All I did was go to [www.cups.org]("http://www.cups.org") and download version 1.2.0.
unzip it and compile it as instructed 
(just cd to dir, execute ./configure and then type <make><Enter> )
then install it by typing <make install> <Enter>. 

Restart CUPS or reboot. 

<you can test your CUPS version by typing [http://localhost:631](http://localhost:631) in your browser, the CUPs administration web interface displays the version here>

Set up the printer as IPP on [http://XXXXXXX:1631/printers/printername](http://XXXXXXX:1631/printers/printername) and the printserver works again!

I haven't had any problems running the printer, and I have not noticed any broken dependencies at the moment. This install probably takes it out of auto update but do you want to update CUPS and have your printer stop working again. :confused: 

I am running Feisty Fawn beta on two machines and neither have any problems at the moment.

Hope you are helped

Paul.

grazie mille !!! :)

---

### Post by matrix_83 on 2007-06-19
where I can find 1.2.0 version? On the ufficial site there is only some version, but not 1.2.0. Here are subversions:

[http://www.cups.org/software.php#SVN](http://www.cups.org/software.php#SVN)

but I haven't any idea of compiling a source file!!!

---

### Post by matrix_83 on 2007-06-20
I have founded cups ve 1.2.0...I have compiled and installed it..but it doesn't work! When the installation is finished and I reboot my pc, I type localhost:631 on my browser, but the result is: 404 - Not found.
How I can do to downgrade from 1.2.8 to 1.2.0? Can anyone help me? Thanks.

---

### Post by fde on 2007-07-30
Hi!
Did you find a solution to this problem with Feisty Fawn? My CUPS version is 1.2.8, so I guess it should work, since apparently it worked with the 1.2.0 (it works with Windows XP, that sucks).

Thanks to anyone who can help me...

---

### Post by fde on 2007-07-30
Ok. According to [this]("https://bugzilla.novell.com/show_bug.cgi?id=217215") and [this,]("http://www.cups.org/str.php?L2185") the IPP protocol used by USR print server is not the standard IPP protocol, but an "IPP-like" protocol designed to fit the one used in Microsoft products. In older versions of CUPS, a "bug" in the IPP protocol made it compatible with the "IPP-like" protocol of USR, but now that is corrected, therefore it is not compatible anymore...

---

### Post by subvertigo on 2007-10-20
I have the same problem, using Ubuntu 7.10 Gutsy.

How can I fix it with this version?

---

### Post by subvertigo on 2007-10-23
Please help!

---

### Post by subvertigo on 2007-10-25
Nobody?

---

### Post by arkara on 2007-10-25
ok the same problem here i dont know what to do
i dont know if this will be fixed if i update the firmware but i don't want to risk my router becoming non-operational

---

### Post by subvertigo on 2007-10-25
I have the last router firmware... and doesn't work.
And it is supposed there are no new firmware updates planned...

---

### Post by arkara on 2007-10-25
i have just sent a contact on usr. i will w8 for an answer or a workaround and then i will inform the forum about this

---

### Post by subvertigo on 2007-10-25
> **arkara said:**
> i have just sent a contact on usr. i will w8 for an answer or a workaround and then i will inform the forum about this
Already done... the answer is "We do not support Linux".

---

### Post by arkara on 2007-10-26
oh.
this is unacceptable! they will hear a load of crap for that.
sorry for my vocabulary but i have bought a product and i want it to work correctly.
this is frustrating!!!

---

### Post by subvertigo on 2007-10-28
up.

---

### Post by arkara on 2007-10-31
up? i don't get it.
:P

---

### Post by arkara on 2007-10-31
still nothing..

---

### Post by mtn on 2007-11-05
> **pazzaTgreat said:**
> guys - I too am having this problem with my 100% perfectly reliable 9108a router. 

From other posts I gleaned that as the CUPS version advanced, something was changed in the IPP printing section.  The last known version that worked the 9108 was CUPS 1.2.0.

All I did was go to [www.cups.org]("http://www.cups.org") and download version 1.2.0.
unzip it and compile it as instructed 
(just cd to dir, execute ./configure and then type <make><Enter> )
then install it by typing <make install> <Enter>. 

Restart CUPS or reboot. 

<you can test your CUPS version by typing [http://localhost:631](http://localhost:631) in your browser, the CUPs administration web interface displays the version here>

Set up the printer as IPP on [http://XXXXXXX:1631/printers/printername](http://XXXXXXX:1631/printers/printername) and the printserver works again!

I haven't had any problems running the printer, and I have not noticed any broken dependencies at the moment. This install probably takes it out of auto update but do you want to update CUPS and have your printer stop working again. :confused: 

I am running Feisty Fawn beta on two machines and neither have any problems at the moment.

Hope you are helped

Paul.

Hi,
I am having the same problem with the U.S.Robotics USR9108 modem/router with built in print server. I'm running fully updated Feisty and trying to get an Epson Stylus D78 going, that works fine through USB with the D68 driver. I followed the instructions above including downloading the cups 1.2.0 from here [http://www.easysw.com/cups/software.php](http://www.easysw.com/cups/software.php) and stopping and starting cups...

```
sudo /etc/init.d/cupsys stop
```
and
```
sudo /etc/init.d/cupsys restart
```

I logged in to cups [http://localhost:631](http://localhost:631)  and setup the printer, all seems well, i.e. the green light is on the printer icon etc, but when I do a test print I get this message...

> **Unsupported format 'application/postscript'!**
or when printing a test page through the printer admin tool I get...
> Printing to 'EpsonD68' failed with error code: 1034
is the printer paused ?


I have followed a number of threads including this [detailed bug report ]("https://bugs.launchpad.net/ubuntu/+source/gs-esp/+bug/55283")with suggested solutions, including this one that looked promising...

> Geoff Jacobsen has the same problem in bug #36532.

He was able to solve the issue by reinstalling gs-esp with following commands:

$ sudo dpkg --purge --force-all gs-esp
$ sudo apt-get install gs-esp

Then you can add the comment in mime.convs again:
#application/vnd.cups-postscript application/vnd.cups-raster 100 pstoraster

You only need gs-esp, you can safely remove gs-afpl and gs-gpl with following command:
$ sudo apt-get --purge remove gs-afpl gs-gpl

I'm still getting the same error message though - very frustrating. If anyone can help with this I would be very grateful.

Cheers

---

### Post by mtn on 2007-11-06
UPDATE: the printer now works, locally and from the router!

Got it working by uncommenting the line (see below) In the file /etc/cups/mime.convs as was mentioned above. I think a file of the same name also lives in my home/cups folder and it was this one that I was editing before! What had confused me (as I'm not very bright) was that I was dealing with two different problems. 1) I had to install cups 1.2.0 as later versions don't work with the USR9108 router. 2) Cups 1.2.0 has a "bug" so that it didn't work with the Epson - until the line was uncommented. Anyway, I'm well happy.

```

application/octet-stream	application/vnd.cups-raw	0	-

```

To edit the file
```

sudo gedit  /etc/cups/mime.convs

```

---

### Post by mtn on 2007-11-07
New problem. I just installed Gutsy and I can't get the printer to work.

The results from ./configure don't look right to me.It is a fresh install, the only extra packages I have installed are build-essential. I have attached output from the terminal in a txt file. If anyone has any suggestions it would be greatly appreciated.

---

### Post by kenns on 2007-11-12
Hello

I've also send an e-mail to USR for support.

My answer that I recieved:

[I]Dear Customer Name,

Thank you for choosing USRobotics.

Unfortunately we would like to inform you that your request is outside the scope of services that we provide.
Linux ubuntu is not a supported OS.
I do apologize for all the inconvenience this may cause to you.

I hope this helps, if it doesn't please let me know.

Again, thank you for choosing USRobotics.

If you reply to this message, please click 'Reply' and include all previous correspondence. This allows us to track and resolve your issue more efficiently.

Sincerely,[/I]

---

### Post by mtn on 2007-11-14
I'm still messing around trying to get the print server working with Gutsy.

I set up the printer through the cups interface [http://localhost:631](http://localhost:631), and when I click the button "Print Self-Test Page", on the "Printers" tab, it prints a cups test page - amazing! I'm not sure if this is significant or not. Also, when I click the "Print Test Page" button on the same tab the printer cues up the paper, prints one or two blurry lines and spits the paper out - it then does this repeatedly until I power of the printer, it also give this error **"/usr/lib/cups/backend/ipp failed**".

Just for the record here is what I did to set up the printer.

1) Installed cups 1.2.0 (as above) and tested that the printer worked when plugged directly into the laptop via USB - it did.

2) Installed the printer (Epson Stylus D78 ) through the cups interface - [http://localhost:631](http://localhost:631) - as ipp, i.e.  ipp://192.168.1.1:1631/printers/EpsonD78

3) In the file **/etc/cups/mime.convs**
```
sudo gedit /etc/cups/mime.convs
``` Uncommented the line > application/vnd.cups-postscript	application/vnd.cups-raster	100	pstoraster
(This is a different line than mentioned above!)

That was about it I think.
Any ideas?

---

### Post by mtn on 2007-11-16
I wrote to US Robotics regrading the print server problem (see the attached txt file) and received a reply. Notably they say,

"We have recently determined that the new version of CUPS is not compatible with the print server but our engineers are working hard to solve this issue, I will suggest you to check our site periodically for updates on this."

It would be fantastic if this was resolved in the near future. I will post back with any updates.

---

### Post by amraam on 2008-04-11
Hello

There is a beta firmware from [http://www.hwupgrade.it/forum/showthread.php?t=1128324](http://www.hwupgrade.it/forum/showthread.php?t=1128324) to solve bug.


BETA firmware's link:

[http://web.tiscali.it/mlobina/USR9108_Beta_Dic_07.bin](http://web.tiscali.it/mlobina/USR9108_Beta_Dic_07.bin)


Works fine on Ubuntu 7.10; configured:

New printer

Other and enter uri: [http://192.168.1.1:1631/printers/xxx](http://192.168.1.1:1631/printers/xxx)

---

### Post by amraam on 2008-04-25
Evidently still working on Ubuntu 8.04

---

### Post by james.bashforth on 2008-05-30
Has anyone got this working yet, i have the us robotics 9107 same as the 9108 but no wireless just standard router.  i cant seem to get the print server working and us robotics say ubuntu is supported and they have lots of users who have linux/ubuntu working  fine with it, i find this hard to believe but when i try to get anything out of them regarding configuration they are pretty useless.  it seems that downgrading to cups 1.2 will work from what i have seen in other posts but i wouldnt know where to start, i am using ubuntu 8.04

any help is really appreciated

Thanks

---

### Post by b4rney on 2008-06-17
Confirmed beta firmware working in 8.04. I can now print for the first time from UBUNTU to my US Robotics 9108.

Remember it's beta so make backups. Having said that it worked fine for me!
For beta firmware see amraam's post. 
[http://ubuntuforums.org/showpost.php?p=4696020&postcount=30](http://ubuntuforums.org/showpost.php?p=4696020&postcount=30)

---


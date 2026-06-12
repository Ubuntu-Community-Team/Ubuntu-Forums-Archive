---
title: "Sharing Linux CUPS printer to Windows XP Home"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by mikispag on 2006-02-19
Hi all,

I've got a HP DeskJet 710C printer with my Ubuntu Breezy box.

It works perfectly.

I'd like to share it with a laptop with Win XP Home Edition. I set up Samba for file sharing and all works perfectly! But when I try to share my printer using Samba, it fails and when I do this using CUPS a strange thing happens:

if from my laptop write in the browser address bar```
http://192.168.0.100:631/printers/deskjet710c
``` all works, and I can see the printer and even print the test page from the web interface.

But when I go to the Printers window and enter in the URL box [http://192.168.0.100:631/printers/deskjet710c](http://192.168.0.100:631/printers/deskjet710c) it doesn't work and an error message pops up telling the printer doesn't exist.

I've disabled any firewall.

I paste below my *cupsd.conf* for your information.

```
ServerName 192.168.0.100

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /printers/deskjet710c>
Order Deny,Allow
Deny From None
Allow From All
AuthType None
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location> 
```

What's the matter?
Where's the problem?

I'm really getting mad with this, can anyone help me please?

Thank you all!

---

### Post by mikispag on 2006-02-20
Can't anyone help me?

---

### Post by jrb114 on 2006-02-28
Hi,

I've just managed to get CUPS to share my (usb only) HP PhotoSmart-7260 with a Windows XP laptop. I followed this how-to

[http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

Now I can even see other CUPS printers on my network too when I go to System->Administration->Printing; Global Settings->Detect Lan Printers. (My iBook has the PhotoSmart drivers installed on it too, and these are flagging up.)

N.B. I had a bit of a wrestle with the Windows drivers - since the Photosmart is a usb printer it isn't designed to be set up as a network printer (I guess) - I had to locally install the printer, then choose any arbitrary driver to install it as a network printer, then change it later to the correct driver. The hpijs drivers however, are a breeze :-)

HTH 

James

---

### Post by mikispag on 2006-03-01
Hi,

thank you for your reply.

The fact is that I have followed the istructions, but the Windows Laptop doesn't see the printer when I put the URL of my CUPS Printer ([http://192.168.0.1:631/printers/HPDeskjet710c)](http://192.168.0.1:631/printers/HPDeskjet710c)).

What can I do?

Thanks

---

### Post by jrb114 on 2006-03-04
Sorry that didn't work, but in my experience cups sharing with Windows can be an absolute nightmare. I spent all afternoon today trying to set up cups sharing on OS X for a Windows client. 

I was trying to set up a Lexmark 2200 printer on the Mac, and, whilst my ibook (running OS X too) could see the cups printer absolutely fine, the Windows box simply refused to talk to the printer (it could see it). I did the whole list of:
i) reinstall drivers on both systems
ii) close and reopen firewall ports (try turning it completely off)
iii) get really pissed off
iv) eventually I tried a different driver on the windows box to the "correct" driver and, again, just like the photosmart above, it worked (although I can't do all the nice stuff such as ink cartridge levels etc).

So, aside from trying all this, I'll copy you my /etc/cups/cupsd.conf

```

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location> 

```

My main observation (but I'm no expert) is that I don't have a section specifically listing my printer. I'd try removing that section (i.e. the
```

<Location /printers/deskjet710c>
Order Deny,Allow
Deny From None
Allow From All
AuthType None
</Location>

```

bit) and try restarting cupsys. If this doesn't work then I'm at a lose end. You could try checking the web interface for cups ([http://localhost:631](http://localhost:631)) although this is not "recommended" for ubuntu and is by default disabled. If you have a look at [http://192.168.0.100:631](http://192.168.0.100:631) from the windows client though it'll at least establish whether or not the firewalls are giving any problem.

Sorry for the rambling...

James

---

### Post by jrb114 on 2006-03-04
Actually, I've just reviewed the thread after adding that post.

At the top of your cupsd.conf you have

```

ServerName 192.168.0.100

```

but you point the windows printer to 192.168.0.1 (well at least you did in one of the later replies).

I don't know quite what role ServerName plays, but I'd be a bit suspicious and would probably try commenting it.

J

---


---
title: "Tsclient slower then mstsc?"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by thefish123 on 2010-04-22
Hi everyone,

I am an IT consultant.  I use both Windows and Linux a fair bit.  On my notebook (my primary computer) I am dual booting Ubuntu and Windows 7.

I am responsible for about 15 to 20 Windows-based servers across the GTA.  These servers are running various editions of Windows 2003 to Windows 2008.  I find that when I have to remote desktop into one of these servers that the tsclient program under Ubuntu is slower then mstsc.exe (the native Windows RDP client).  I have no idea why.

I have a copy of Windows XP Pro installed inside VirtualBox.  It seems that running mstsc.exe under a virtualized copy of XP is faster then using tsclient.

Does anyone have any idea why?  What can I do to correct this?  I hate to boot up a virtual copy of XP or reboot into Windows 7 just to RDP into a remote server.

Best regards,
The Fish

---

### Post by computer13137 on 2010-04-22
...How much slower?  I've never had any issues with it, but I never ran a side-by-side comparison.  If it's so slow that it's crippling, then I think there may be something wrong, but if you're upset about waiting an extra two seconds for the window to open, then I don't understand.  

Cheers,
Kirk

---

### Post by thefish123 on 2010-04-23
> **computer13137 said:**
> ...How much slower?  I've never had any issues with it, but I never ran a side-by-side comparison.  If it's so slow that it's crippling, then I think there may be something wrong, but if you're upset about waiting an extra two seconds for the window to open, then I don't understand.  

Cheers,
KirkOh, its defiantly not crippling...  the “extra two second” scenario is closer to the truth.  And I am not “upset” about it either.  But if every window, every menu, every time I click the start menu takes an extra second or two it really does get frustrating enough that I will just reboot into Windows or fire up VirtualBox.

These servers are high-end machines with 16 GB of RAM and so forth.  They are uber fast in real life.  To have that “kludgey” feel when using them remotely via tsclient (actually I think it's rdesktop – tsclient just being the front end) when I am trying to get something done is frustrating.

There has to be a reason for it and I thought perhaps I was overlooking something obvious.  Perhaps the defaults are different with tsclient then they are with mstsc.exe.  Perhaps an overlooked checkbox or a command-line switch somewhere is all that is needed.

I am very impressed with the quality of free software.  I am also very impressed with the level of Windows/Linux and Linux/Windows integration that exists these days.  I am not a fanboy of either system really.  I enjoy working with computers too much to be a fanboy in either camp.  I like software that works and does cool stuff.

Best regards,

The Fish

---

### Post by computer13137 on 2010-04-23
In reading my response, I can't believe how rude I sounded... I'm sorry about that. :(

> **thefish123 said:**
> Oh, its defiantly not crippling...  the “extra two second” scenario is closer to the truth.  And I am not “upset” about it either.  But if every window, every menu, every time I click the start menu takes an extra second or two it really does get frustrating enough that I will just reboot into Windows or fire up VirtualBox.

I was not referring to a 2 second delay for everything clicked.  In my experience, the time to establish the MSTSC connection took longer, but once it was connected it performed great.  

Just for kicks, try an SSH tunnel and see if it goes any faster.
ssh -L 3389:127.0.0.1:3389 user@ip  (SSH server on the RDP server computer)

Or:
ssh -L 3389:rdpserver:3389 user@somesshserver  (SSH server on your LAN but not the RDP server).

Then connect to 127.0.0.1:3389 from TSclient and see if it performs any better\worse for you.  I'd be curious.  I understand this is not practical to do all the time in your case, especially with so many computers to manage, but the answer to this question could be a start.

Cheers,
Kirk

---

### Post by thefish123 on 2010-04-27
> **computer13137 said:**
> In reading my response, I can't believe how rude I sounded... I'm sorry about that. :(That's quite alright :-)  but I also think I might have figured something out.  My wife just had a baby boy (my first born son!!) so I have not had much chance to try this out but...

I think the problem was/is a lack of compression.  I am accessing these systems via the Internet for the most part.  I tried the following command line:

rdesktop -f -z -P some.server.com

and it seems to be a fair bit faster.  The -f just means “fullscreen” but the -z means “enable rdp compression”.  I wonder if this is missing from the default when rdesktop is launched by tsclient.  I do not see a checkbox for this option in tsclient.

The option -P means to use bitmap caching which could also be responsible for making it feel faster but there is a checkbox for this in tsclient and I was using this all along so...  I think the main difference is the data compression.

I will try your other suggestions about SSH when things settle down around here.   New babies are exciting times!!

The Fish

---

### Post by computer13137 on 2010-04-27
You know, whenever I did an SSH tunnel I always had my SSH connection's compression enabled.  My performance boost using SSH could have also been due to compression.

Kirk

---

### Post by thefish123 on 2010-04-27
> **computer13137 said:**
> You know, whenever I did an SSH tunnel I always had my SSH connection's compression enabled.  My performance boost using SSH could have also been due to compression.

KirkI do also wonder why rdesktop does not support a handy little “slide down” control strip across the top of the screen like mstsc.exe does.  The only way to get out of a full screen rdesktop session is to press Ctrl+Alt+Enter and then minimize the window.

The Fish

---

### Post by thefish123 on 2010-05-19
> **thefish123 said:**
> I think the problem was/is a lack of compression.  I am accessing these systems via the Internet for the most part.  I tried the following command line:

rdesktop -f -z -P some.server.com

and it seems to be a fair bit faster.  The -f just means “fullscreen” but the -z means “enable rdp compression”.  I wonder if this is missing from the default when rdesktop is launched by tsclient.  I do not see a checkbox for this option in tsclient.I just wanted to follow up on my own post in case anyone finds this thread via Google.  I do indeed think the issue of slowness is a lack of compression.  The “tsclient” does not expose a checkbox to enable compression.  But this option can be enabled by launching rdesktop directly.

I have been using the command “rdesktop -z -f some.server.com” for weeks now and it works great.  So, problem solved!

The Fish

---

### Post by lykwydchykyn on 2010-05-19
Glad to hear it!  I though I'd mention, if you're missing the drop-down menu you might try krdc, the KDE front-end for rdesktop.  It doesn't have a tick box for compression, but it does allow you to add any rdesktop switches you want to add on a per-host basis.

---

### Post by Whoopie on 2010-05-20
Hi,

just FYI, there's a [LP report]("https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/254188") to add a checkbox for compression. But [grdc]("http://grdc.sourceforge.net") supports it.

Best regards,
Whoopie

---


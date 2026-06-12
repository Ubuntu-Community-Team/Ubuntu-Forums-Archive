---
title: "HP Printer doesn't work"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Pondoro on 2010-08-31
I am networked to a Windows machine. I can see and open files across the network. I can see and add my HP 6000 printer (it is on the Windows machine).  On my Ubuntu machine this printer has a check mark by "Enabled" and "shared" but I cannot set it as default (that option is ghosted) and when I try to print a test page it says "unable to connect to CIFS host"

I downloaded the HP Linux setup program. That program cannot locate the networked printer at all.

Any ideas?

---

### Post by MaindotC on 2010-08-31
I know you said you were "networked to a Windows machine" but I wasn't sure if that meant you were using the windows machine as an access point or if it's just on the same network on which you are connected.  Are you connected to an access point?  If so do you have uPnP enabled?

---

### Post by Pondoro on 2010-08-31
> **strAlan said:**
> I know you said you were "networked to a Windows machine" but I wasn't sure if that meant you were using the windows machine as an access point or if it's just on the same network on which you are connected.  Are you connected to an access point?  If so do you have uPnP enabled?

My printer is connected by USB to my Windows machine. Both the Ubuntu machine and the Windows machine are plugged in (via hard wire) to a Linksys router. As I said I can drag files across, see and install the printer on the Ubuntu machine. But I can't print.

I am not sure what uPnP is...

---

### Post by MaindotC on 2010-09-01
Well I'm sure you googled uPnP so I won't bore you with repeating what you've already read.  What documentation did you follow for sharing the printer with your Ubuntu machine?

---

### Post by Pondoro on 2010-09-01
> **strAlan said:**
> Well I'm sure you googled uPnP so I won't bore you with repeating what you've already read.  What documentation did you follow for sharing the printer with your Ubuntu machine?

I did not do anything to share the printer from the Windows side, but I can see it from Ubuntu Linux. I just get an error message when I print to it. And I did read all about uPnP but I cannot find how-to instructions for making it happen.

---

### Post by cavalier911 on 2010-09-01
You have to enable sharing of the printer on windows.How you do that depends on which version of windows your using.
This should get you started.
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by Pondoro on 2010-09-01
> **cavalier911 said:**
> You have to enable sharing of the printer on windows.How you do that depends on which version of windows your using.
This should get you started.
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Thanks! This worked!!

---

### Post by MaindotC on 2010-09-02
For future reference you can enable uPnP by logging into your access point.  The address you type and credentials you use depend on what kind of AP you have - just google your AP's model.  There will be a setting in that menu for uPnP which enables sharing of networked devices across your lan.  Good to see you got it working the other way though.

---


---
title: "Sharing a printer with Windows XP"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by Aidje on 2005-03-16
Warning: sob story of sorts. If all you want is information about what my actual problem is, skip the next paragraph.

Before I switched to Ubuntu, everyone in my house was using Windows XP, and since I'm the only one who doesn't have a laptop, my computer was the printer server. Now I'm using a dual-boot configuration. My problem is this: I can't figure out how to share a printer from Ubuntu so that everyone who's running XP can print using the printer that's connected to my printer. My parents are constantly making me reboot into XP, thus making it quite difficult to get anything accomplished.

Long story short: I need to set up my printer so that other people on the network can print from Windows XP. My printer is an HP LaserJet 2100 if that has any bearing on the issue. I've followed the [instructions in the FAQ](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#networkprinter), but to no avail. I've done everything that I can find on Google, but still I can't figure out how to get the XP computer to see the printer (much less use it). As far as I know, everything's set up just right on the Ubuntu side and I just haven't figured out how to set up the XP computer. I really can't tell. The page [NetworkPrintingFromWin2K](http://www.ubuntulinux.org/wiki/NetworkPrintingFromWin2K) on the wiki is useless. It doesn't contain any information.

Any help would be greatly appreciated, as I dislike constantly rebooting into Windows so that my parents can print things.

edit: I'm running Warty Warthog.

---

### Post by rmjokers on 2005-03-16
Well the next step after you do what is suggested in the FAQ is to attempt to browse the CUPS configuration from the windows boxes.  You should be able to go to [http://SERVERIP:631](http://SERVERIP:631) and get to the CUPS server page just like you can from the server machine with [http://localhost:631](http://localhost:631)
If you cant access this, then there is something wrong with your CUPS config or your firewall is blocking access.

If you can access this, then your next step is to actually add the printer to the windows box.  I believe you will have to manually type in the URL because windows will not automagically find it for you.  Finally, you have to let windows install a driver for the printer (it should identify it correctly at this point).

Lastly, I seem to remember having to change the /etc/cups/mime.types file in Fedora to allow for Raw Printing from windows.  I am not sure if it is necessary for Ubuntu.  Before I did this, I could add the printer in windows and send print jobs but they would either not print at all or print garbage text.  There is more information about this online.

---

### Post by wylfing on 2005-03-16
CUPS is the wrong way to share a printer with Windows boxen. You need samba.

1. sudo apt-get install samba samba-common
2. cd /etc/samba
3. sudo cp smb.conf smb.conf.O
4. sudo vim smb.conf
5. Edit the relevant lines to look like the ones below.

[global]

   printing = cups
   printcap name = cups
   load printers = yes
   use client driver = yes

; You'll probably want to use settings something like these
   guest account = nobody
   invalid users = root
   security = user

; Change this for the workgroup your Samba server will part of
   workgroup = WORKGROUP

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/smbprint
   printable = yes
   public = yes
   guest ok = yes
   guest account = smbprint
   writable = yes
   printer admin = btakle

[print$]
  comment = Printer Drivers
  path = /usr/share/cups/model
  browseable = yes
  guest ok = no
  read only = yes
  write list = root

6. sudo /etc/init.d/samba restart
7. With luck, your Windows users will now automatically see the shared printer. Since they were already printing to your shared printer, it should be fine. If it doesn't work, you might need to do a "fake" printer install on the Windows side. That is a lot of pain, and too variable to go in to here. (Either Windows networking stuff works, or it doesn't. Fixing it is a terror.)

Good luck.

---

### Post by Aidje on 2005-05-24
Thanks for the responses, and sorry about my slow response. I'm using Hoary Hedgehog now (yeah, it's been awhile).

I followed the instructions given by wylfing, or at least I attempted to. The Windows box can see the printer, but it gives an error when I try to print. The logfiles created on Ubuntu are blank, but they are created. The error given on Windows is incredibly vague and unhelpful (all it says is "error printing").

Perhaps someone could check out my smb.conf file and see if I'm missing something simple. I've uploaded it to [http://home.ripway.com/2004-10/193996/smb.conf](http://home.ripway.com/2004-10/193996/smb.conf).

edit: Since I waited so long and am now using Hoary, is this now in the wrong forum?

---

### Post by Aidje on 2005-05-24
I've tried changing security = user to security = domain

Now I keep getting this error message in the logfile (IL0015 is the workgroup of both the Linux and the Windows box):

[2005/05/24 20:42:57, 0] auth/auth_domain.c:check_ntdomain_security(284)
  check_ntdomain_security: could not fetch trust account password for domain 'IL0015'

I'm thinking that this problem would be solved if I could figure out how to set a trusted domain, but I could be way off, of course.

---

### Post by d1337 on 2005-06-26
Stumbled upon your dilemma while searching for issues on getting my printer going.  Not sure if it's stll an issue to you, but I've recently done this on my work network and will implement on my home network once I get my printer going.

Long story short, Win XP will print using IPP, (but you must use 'http' for the URI).  If you're using a somewhat structured intranet with static IP's, find the /etc dir on the XP boxes (? methinks in windows/system/win32).  There wil be two files in /etc, hosts and lmhosts.  Add your Ubuntu box to these files...like 192.168.0.254 'YOUR BOX NAME' (no quotes needed)

If your printer is working proper on your Ubuntu box, and it would work from the XP boxes (driver installed), you should be able to add a printer, on the network, specifying the URI such as

[http://YOURBOXNAME/printers/PrinterName](http://YOURBOXNAME/printers/PrinterName)
You may need to add in :631 after yourboxname, adjust the path, and remember that the PrinterName is case sensitive in regards to what is in your /etc/cups/printers.conf file on your Ubuntu box.


This is an article that was quite helpful to me

[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

This will allow you to skip Samba for printing.

Hope this helps,
d1337

---

### Post by skirkpatrick on 2005-07-07
I definitely recommend using IPP directly into Cups from XP machines.  They have a much faster response time than using Samba.  My experience with a Windows 98 machine is exactly the opposite.

This thread, [http://www.ubuntuforums.org/showthread.php?t=45945)](http://www.ubuntuforums.org/showthread.php?t=45945)), should help you with setting up to use IPP.

---


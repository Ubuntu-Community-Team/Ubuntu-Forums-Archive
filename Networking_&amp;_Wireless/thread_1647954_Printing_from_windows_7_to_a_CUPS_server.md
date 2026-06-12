---
title: "Printing from windows 7 to a CUPS server"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2010-12-18
the other day i set up a cups server, i have the printer going, drivers installed. i can print find from the ubuntu machine itself, but i want to be able to print from my laptop, running windows 7. how do i do that? and, if possible i dont want instructions to be as specific as possible. thanks!

---

### Post by gmargo on 2010-12-18
While there may be a way to make Windows talk directly to the Cups server, I generally install a Samba server and use it to interface with Cups and export the printer into the same workgroup as the Windows machine.

---

### Post by drdos2006 on 2010-12-18
You had better do some research on the Microsoft sites. Microsoft tech support have indicated that Windows 7 is a client OS and have removed IPP from Windows 7. Printing from XP is fine tho. If you have windows 7 and want to print to a LAN connected device, it appears Micro$oft want you to buy their server OS so you can print from Windows 7.

:(

regards

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2010-12-18
gmaro, thanks for the info, but im afraid i may need a little more. iv you have done this before, might you be able to tell me how to? or perhaps give me some documentation?

thanks

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2010-12-18
i have just installed samba, and now i can see my server on my windows machine. i can also see the printer, but it gives me an error when i try to connect, i have a theory that its to do with authentication, but i dont know for sure, and i dont know how to authenticate myself on the local machine.

---

### Post by quintum on 2010-12-20
You can print from Windows 7 client to Ubuntu CUPS server.  It wasn't any harder than setting up in WinXP.

I setup cups from Ubuntu gui but it didn't work for some reason. So I did the following.

Assuming you have samba and cups installed and running,
(sudo apt-get install cups samba .... or whatever)

1. Samba
Edit /etc/samba/smb.conf
Search for "CUPS Printing" section
Uncomment:
printing = cups
printcap name = cups

2. CUPS
Edit /etc/cups/cupsd.conf
Uncomment/add:
Browsing On
BrowseAllow all
BrowseAddress 192.168.1.*  # or your network address
<Location />
  Order allow,deny
  Allow all
</Location>

This is the very basic setup to get you printing with minimal configuration.  Once you check it works, you can tweak it.  Or not.

After restarting samba and cupsd, Win 7/XP should detect your cups server when you browse for network printer.  Make sure you have the correct printer driver installed in Windows.  (I chose the closest model I could find and it still worked.)

Hope it helps.

---

### Post by Stoatwblr on 2012-01-23
> **drdos2006 said:**
> You had better do some research on the Microsoft sites. Microsoft tech support have indicated that Windows 7 is a client OS and have removed IPP from Windows 7. Printing from XP is fine tho. If you have windows 7 and want to print to a LAN connected device, it appears Micro$oft want you to buy their server OS so you can print from Windows 7.

:(

regards

That's a bogus technote, sometimes MS's left hand and right hand don't communicate well.

On the win7 machine:

You have to enable the IPP client under print services and restart print spooler (or reboot)

You also need to punch a firewall hole for port 631 so that the winbox can see port 631 broadcasts.

---

### Post by dhokieff04 on 2012-04-12
my client using win 7, and server using samba cups.
printer from client using shared printer on server.
sometimes shared printer on server not shown so i can't print
from client, but if I print using cups to server no problem.
Question: why printer on server not shown from client, thx

---


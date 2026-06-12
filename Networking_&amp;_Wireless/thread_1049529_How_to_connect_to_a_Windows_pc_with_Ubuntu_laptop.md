---
title: "How to connect to a Windows pc with Ubuntu laptop?"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by turna on 2009-01-24
There is a desktop pc with windows xp. the wireless adsl modem has a connection with this pc via cable. My ubuntu laptop has a wireless connection with this adsl modem.

So, i want to connect to that pc to share files, and also the printer installed on it.

I don't know how to do.

---

### Post by dooglo on 2009-01-24
I'm in the same boat, but, I have another computer downstairs with wireless and Ubuntu 8.10 and want to connect to XP computer upstairs the same way.  

Oh, sorry for hijacking your thread.  Thought that if I bumped it a little it might get attention.

D.

---

### Post by Iowan on 2009-01-24
You probably want Samba. A few links:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://oreilly.com/catalog/samba/chapter/book/index.html]("http://oreilly.com/catalog/samba/chapter/book/index.html")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html")

---

### Post by cariboo on 2009-01-24
If you only want to connect to the windows computer and not the other way you don't need samba. Set up a directory to share, just like you would if it was on a windows only network. Give the share a name, preferably with out any spaces in the name. Do the same with your printer. Depending on the version of XP you are running sharing can usually be accessed by right-clicking on a directory or printer.

On your Ubuntu computer you may have to change the workgroup depending on what version of XP your are using. XP home defaults to MSHOME for a workgroup and XP pro defaults to workgroup. Tchange the workgroup in Ubuntu, press Alt-F2 and type:

```
gksu gconf-editor
```

Navigate to system-->smb right click on workgroup and click Edit Key, add your workgroup and close the program. You should now be able to access your windows computers if you are using DHCP to obtain ip addresses from your router.

Go to Palces-->Network and double click on Windows Network, If you have done everything right you should see your workgroup. Double-click the workgroup and you should see your Windows computer, Double-click the windows computer and you should see your shared directories.

To setup a printer connected to a Windows computer go to System-->Administration--Printing, click New, in the New Printer window select Windows Printer via SAMBA, click the browse button, and you should see your workgroup, click the arrow to the left, you should see your Windows computer, click the arrow to the left of your computername and you printer should show up. Click the Prompt user if authentication is required radio button, then click forward, if your printer isn't an HP you will have to select the Manufacturer, click forward and select the model use the recommended driver and click forward. Add the info about your printer and click apply.and you're done.

Before setting up the printer make sure it is supported, check the [OpenPrinting Database]("http:////www.openprinting.org/printer_list.cgi") for your printer.

Jim

---

### Post by turna on 2009-01-25
Works perfectly, thanks

---

### Post by Iowan on 2009-01-25
Hmmm... I read that at least three times, and thought OP wanted to share FROM Ubuntu TO Windows.  Thanks, **cariboo907.** That saved him the trouble of installing and setting up Samba - at least the server.  (Technically, he is still using Samba ;) )

---

### Post by Copitox on 2009-01-25
I tried to do this but i have a few problems.

The windows pc is configured with a DOMAIN, not a WORGROUP. un gconf-editor y just put the name of the domain. When did so, i was able to "see" the windows pc from Ubuntu, but i can't see the shared files from Windows. What do i do?

---

### Post by Iowan on 2009-01-26
[This]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html") How-To might help - at least to see if shares *can* be accessed.

---


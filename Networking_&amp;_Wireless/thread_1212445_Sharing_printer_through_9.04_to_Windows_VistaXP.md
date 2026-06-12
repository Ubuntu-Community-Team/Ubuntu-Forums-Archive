---
title: "Sharing printer through 9.04 to Windows Vista/XP"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by carl132 on 2009-07-13
I'm the printer server on a 3-PC home network. I'm using Ubuntu 9.04, but the others use Windows XP and Vista. We have the HP Deskjet F4280.
With CUPS, I can perfectly print anything on my PC. Problem arises when it comes to sharing.
First, I went to CUPS and enabled sharing, published shared printers, etc. Didn't work, and I found out it was not going to be that easy.
Ok, so I downloaded SAMBA (through apt-get install samba), and configured the smb.conf file according to the man page on cupsaddsmb. At the end, my smb.conf looks like this: [http://pastebin.com/f6949d397](http://pastebin.com/f6949d397)
Allright, then I got the windows drivers for printing ( ps5ui.dll , pscript.hlp , pscript.ntf , pscript5.dll) on the folder indicated by the smb.conf . I didn't worry about 64-bit versions since none of the PCs used 64-bit OSes.
I thought, great! - no. Still didn't work, Windows wouldn't print.
So, messing around, I came to the conclusion I needed to run some commands with cupsaddsmb . Looking at their man page, I decided the appropiate was:
```
cupsaddsmb -a -H localhost
```I ran it, typed in my password. It then goes to a blank line, and nothing happens. I waited for a long time, nothing. Tried to print from windows, but didn't work. Restarted SAMBA, and windows still complains. The exact error is among the lines "The RPC server is unavaliable".

So, what am I doing wrong? What do I have to do to share this printer?

---

### Post by carl132 on 2009-07-14
I continued to work on it. I went on a Windows machine, and successfully entered CUPS administration tool through 192.168.0.132:631
I managed to, through windows, make CUPS print a test page, which went without errors.
But still, I can't print with windows. I tried searching for printers, but all it finds is the old Windows sharing setup, back from when I used windows.
I have matched the workgroup, but Windows won't see Linux.
So I tried to tell windows to connect at [http://192.168.0.132:631/printers/F4280](http://192.168.0.132:631/printers/F4280)
It takes me to a next screen, where I select my printers model - done. After that, it begins processing, and freezes. Stops responding, I have to force it to quit through Alt+F4. I tried the same process again, nothing. I did it yet again, and when the processing part came, I left it there and went to lunch. I left for about half an hour, and when I come back, STILL nothing!

Any help on what to do?

Edit: I got the idea to look for logs, and out of /var/log/samba I got this interesting log: [http://pastebin.com/m736112d](http://pastebin.com/m736112d)
Apparently, there is a error when trying to write data. Is it possible this is a permission error? I remember being told to expect it.

---

### Post by martinbaselier on 2009-07-14
[Here's a simple howto.](http://ubuntuforums.org/showthread.php?t=806699)
[Check this for more information](http://www.google.nl/search?q=linux+share+printer+samba+site%3Aubuntuforums.org+tutorial)

---

### Post by ultimatebuster on 2009-07-14
I got the exact problem, However, I fixed mine using SAMBA and webmin.
Easy stuff. Follow me through.

First, you have to install SAMBA
```
sudo apt-get install samba smbfs
```

Second, you have to install [Webmin at this URL]("http://www.webmin.com/")

Now, add your printer so it would work with your local PC. In this case, it's done.

Third, Go to System -> Administration -> Printing. Select Server on the menu and click settings. Make sure you check "Publish shared printers connected through this system". Others are optional. 

***Here, I have a problem. Everytime I restart the system, the setting on the third step always don't save itself. However, the box is check. Basically, I have to go back to the settings, and click Apply/OK or else nothing will print remotely. Maybe someone can help me on this as well.**

Fourth, go to [https://localhost:10000](https://localhost:10000) in your browser. (allow the SSL connection) Login with your credentials and perform the following tasks.

[LIST=1]
[*]Go to Server -> SAMBA Windows File Sharing
[*]Go to Windows Networking and change the workgroup to whatever is on both of your windows machines.
[*]Back to the SAMBA Windows File Sharing page, and click **Create a new printer share below the table**
[*]In **Share Name**, enter an unique name.
[*]In **UNIX Printer**, select your printer
[*]Make sure it is available and browseable. You can enter a description in **Share Comment**.
[*]Click Create
[*]Click your newly created share printer, which brings up config.
[*]Click **Security and Access Control**
[*]Set **Guest Access** and **Writable** to yes.
[*]Click Save which bring back the printer editing page.
[*]Click **Printer Options**
[*]> If this printer is to be used by Windows clients and does not have a UNIX driver installed, enter its complete make and model into the Printer driver field. This must match exactly the name to which Windows refers to so clients know which driver to install. If None is selected, users adding this printer to their Windows systems will be asked to choose the printer model from a list, instead.

Or else you need to provide your own drive at the Windows side
[*]Click Save
[/LIST]
Now you can add a network printer on Windows, or at least, I hope you can. 
I had to struggle over this myself (still struggling, basically working), so if you need any help, feel free to PM me.

---

### Post by carl132 on 2009-07-14
Hey all, thanks a whole bunch for the answers! I felt [ultimatebuster]("http://ubuntuforums.org/member.php?u=535013")'s tutorial closer to my situation, so I went ahead and tried it.
Configuration went fine, everything was there. But, same problem with windows machine. I tell it to connect at [http://192.168.0.132:631/printers/F4280](http://192.168.0.132:631/printers/F4280) , select my printer model, and it freezes. Any help?

Here is a screen from the setup: [http://img33.imageshack.us/img33/6209/webmin.png](http://img33.imageshack.us/img33/6209/webmin.png)
Here is the current smb.conf , now edited by Webmin: [http://pastebin.com/m2b96a4b](http://pastebin.com/m2b96a4b)

---

### Post by martinbaselier on 2009-07-14
You could do it the other way around, install a local printer and select the correct driver. Then check the properties and create a new port, Choose tcp/ip, put in the printer and make the device use the selected port.

---

### Post by carl132 on 2009-07-14
Wait... I didn't understand what you said. Explain it better?

---

### Post by ultimatebuster on 2009-07-14
> **carl132 said:**
> Hey all, thanks a whole bunch for the answers! I felt [ultimatebuster]("http://ubuntuforums.org/member.php?u=535013")'s tutorial closer to my situation, so I went ahead and tried it.
Configuration went fine, everything was there. But, same problem with windows machine. I tell it to connect at [http://192.168.0.132:631/printers/F4280](http://192.168.0.132:631/printers/F4280) , select my printer model, and it freezes. Any help?

Here is a screen from the setup: [http://img33.imageshack.us/img33/6209/webmin.png](http://img33.imageshack.us/img33/6209/webmin.png)
Here is the current smb.conf , now edited by Webmin: [http://pastebin.com/m2b96a4b](http://pastebin.com/m2b96a4b)

Aha! Don't try to connect through TCP/IP (ie [http://192](http://192)...)

I don't know your ubuntu computer's config. But if it isn't static IP, you are going to have a problem later on (restart, lose connections etc.)

Try go on your windows side, go to my network places, or network on vista. Try to find your computer's **computer name**. Go into that and see if you can find the printer. Then add it.

Hopefully it helps.
If you have any other problems, let's try chatting on tinychat etc.

---

### Post by carl132 on 2009-07-14
OMIGODOMIGODOMIGOD I did it! Thanks! It worked on Windows XP, although I did have to use local drivers. I'm testing on vista, but still downloading the driver. Anyways, thanks so much! :D:D:D:D:D:D:D

EDIT: Worked on vista!

---


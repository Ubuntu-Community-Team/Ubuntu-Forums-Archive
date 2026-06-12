---
title: "Can't see printers from CUPS print server in Windows network"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2010-09-21
Hi Everybody:

I just setup a Ubuntu CUPS print server. However when I I try to browse to it, it tells me that I do not have permission to do so and does not let me see the printers or any shared folders. What is going on? 

Thanks in advance.

---

### Post by Morbius1 on 2010-09-21
You say you created a CUPS printer server yet you use the word "browse" implying your using Samba to get to cups so let's start with some basics first.

*You need to tell CUPS to share the printer:*
> Administration > Printing > Right Click the attached printer > Properties > Policies
Check Enabled, Accepting Jobs, and Shared
*You need to tell cups to publish the printer:*
> Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"
*Now you need to tell Samba to allow guest access to the CUPS printers:*
```
gksu gedit /etc/samba/smb.conf
```Look for this section:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]    guest ok = no[/COLOR]
    create mask = 0700And change "guest ok = no" to "guest ok = yes":
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]    guest ok = yes[/COLOR]
    create mask = 0700
Then restart samba:
```
sudo service smbd restart
```

---

### Post by elperrillo on 2010-09-21
Hi Morbius1

I can see the printers now, however I am having another issue. everytime try to connect to the server it prompts me for username and password for the windows domain. If I am inside the domain it does not ask me for usermane or password but if I am in a workgoup (which is connected to the same network) then it does. I need to be able to connect from a workgroup, install the printer on the computer. I can do this entering a password however when the computer reboots it will lose the connection and prompt the users for username and password again.

---

### Post by SeijiSensei on 2010-09-21
I've found it's sometimes easier in mixed networks to connect the printers to Windows machines and use CUPS to talk to them from the Ubuntu clients.  Is that an option for you?

---

### Post by elperrillo on 2010-09-21
Hi Senjisensei

"connect to windows machines and talk to them from the Ubuntu clients." I am not sure what you are trying to say. 

Al of my machines are windows (domain machines and workgroup machines), Ubuntu is my print server, I have another Windows print server, but I think it is easyer to make the ubuntu server stop asking for password than to do it for the windows server, I have done it before so I know it can work. 

I ran a litle program in one of my Windows workgroup machines which told me that, whenever I get asked for username and password the protocols trying to connect are:

netbios-ssn 
microsoft-ds

Right there is when I get asked for username and password.  The only thing I am doing is going to "my computer" entering the IP of the server \\192.168.1.5 and I get asked for username and password. Is the Windows domain considering the Ubuntu server as being part of the domain somehow? Where is this coming from?

---

### Post by elperrillo on 2010-09-21
PROBLEM SOLVED!!!!

I happened to stumble upon the answer in another forum, I just had to enter the followinf information on my smb.conf file

Under:

[B][global]
security = share[/B]

I then saved and closed the file and restarted samba isuing a simple

**restart smbd**

at the command prompt, that that was it!! it worked like a charm

---


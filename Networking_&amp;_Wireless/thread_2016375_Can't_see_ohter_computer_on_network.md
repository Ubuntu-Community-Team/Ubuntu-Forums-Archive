---
title: "Can't see ohter computer on network"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by rickm1945 on 2012-07-04
I have a wireless network and I use my printer on the network, plus my laptop and Desktop computer. I can't see either computer on the network nor can I connect via "Browse Network", I get this error message


I want to share file between by laptop and my Desktop how can I set this up?

In Windoze I used a workgroup setup and shared files. I am lost in Ubuntu and can't find anything relating to sharing between computers. I,m sure ut's here I just can't find it.

---

### Post by rukiaEnix on 2012-07-04
Have you installed samba?

---

### Post by rickm1945 on 2012-07-04
> **rukiaEnix said:**
> Have you installed samba?
yes I have installed Samba, and the other software it recommended during install. I have setup Shared files om my laptop with Samba, now do I need to install Samba on my Desktop as well to make the sharing both ways? In Network do I need to make the Network a Hotspot?

---

### Post by rukiaEnix on 2012-07-04
Can you please post your smb.conf configuration file?

And what are your computers IP addresses.

---

### Post by bab1 on 2012-07-04
> **rickm1945 said:**
> yes I have installed Samba, and the other software it recommended during install. I have setup Shared files om my laptop with Samba, now do I need to install Samba on my Desktop as well to make the sharing both ways? In Network do I need to make the Network a Hotspot?

If you are sharing files on both machines you need to set up Samba on both machines.  On the other hand if you are only sharing files on one machine (like the desktop) to the others then you only need Samba server on that machine.  All Ubuntu Desktop (including laptop) installs have Samba client software by default.

---

### Post by rickm1945 on 2012-07-05
> **bab1 said:**
> If you are sharing files on both machines you need to set up Samba on both machines.  On the other hand if you are only sharing files on one machine (like the desktop) to the others then you only need Samba server on that machine.  All Ubuntu Desktop (including laptop) installs have Samba client software by default.
I'm sharing files on both machines. I have Samba setup on both machines, have setup files to share and still can't connect. Do I need to change something in the Windows files? I have Drive C: set as shared.  What is command for Samba config. file?

---

### Post by Morbius1 on 2012-07-05
> **rickm1945 said:**
> I'm sharing files on both machines. I have Samba setup on both machines, have setup files to share and still can't connect. Do I need to change something in the Windows files? I have Drive C: set as shared.  What is command for Samba config. file?
You could help these folks by posting the output of the following commands:

This one will give them a more readable listing of your smb.conf:
```
testparm -s
```This one will give a listing of all the shares on your network or error messages if it finds something wrong:
```
smbtree
```

---

### Post by rickm1945 on 2012-07-05
> **Morbius1 said:**
> You could help these folks by posting the output of the following commands:

This one will give them a more readable listing of your smb.conf:
```
testparm -s
```This one will give a listing of all the shares on your network or error messages if it finds something wrong:
```
smbtree
```

```

```ichard@richard-HP-Pavilion-g6-Notebook-PC:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Pictures]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Documents]
    comment = Documents
    path = /home/richard/Documents
    valid users = richard
    read only = No

[Pictures]
    path = /home/richard/Pictures
    read only = No
    guest ok = Yes

[Downloads]
    path = /home/richard/Downloads
    read only = No
    guest ok = Yes
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ smbtree
Enter richard's password: 
WORKGROUP
    \\XPS8100                XPS8100 server (Samba, Ubuntu)
    \\RICHARD-HP-PAVI        richard-HP-Pavilion-g6-Notebook-PC server (Samba
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```

---

### Post by Morbius1 on 2012-07-05
If the other respondents don't mind the intrusion there is one thing you need to fix on the Linux end of this:
> ichard@[COLOR=Blue]**richard-HP-Pavilion-g6-Notebook-PC**[/COLOR]:~$ testparm -sEdit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add this line - right under the workgroup line:
```
netbios name = g6-notebook
```[COLOR=Blue]*It doesn't have to be that exact name but it has to be 15 characters or less in length.*[/COLOR]
Save the file and restart samba:
```
sudo service smbd restart
``````
sudo service nmbd restart
```

---

### Post by rukiaEnix on 2012-07-05
I see you have this for the printers:

```

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

```

change browseable = No to browseable = Yes

That may be the reason of why you can't see the shared printers.
Also add that line to your other shares.

---

### Post by rickm1945 on 2012-07-05
> **rukiaEnix said:**
> I see you have this for the printers:

```

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

```change browseable = No to browseable = Yes

That may be the reason of why you can't see the shared printers.
Also add that line to your other shares.
How do I edit these files now?

---

### Post by rukiaEnix on 2012-07-05
With an editor, for example I always use nano:

```

sudo nano /etc/samba/smb.conf

```

---

### Post by rickm1945 on 2012-07-05
> **rukiaEnix said:**
> With an editor, for example I always use nano:

```

sudo nano /etc/samba/smb.conf

```
I got to the printers and edited the Browse to yes, but how do I save the change?

---

### Post by rukiaEnix on 2012-07-05
under nano you can see with what Ctrl combination you can search, exit, save, and more. For saving is Ctrl+o

If you have problems  using this text editor why you don't try with other you are familiar with.

---

### Post by Morbius1 on 2012-07-05
Like ... oh I don't know ... this one:
> **Morbius1 said:**
> ```
gksu gedit /etc/samba/smb.conf
```
BTW, Changing browseable on the printers share will be ignored by samba since the [printers] share is not a browseable entity. If you run testparm after the edit you will see that samba sets it back to No because it assumes you were kidding.

Can I assume you didn't add the netbios name in smb.conf?

---

### Post by rukiaEnix on 2012-07-05
Even though try adding the browseable to your other shares.

---

### Post by rickm1945 on 2012-07-05
> **rukiaEnix said:**
> under nano you can see with what Ctrl combination you can search, exit, save, and more. For saving is Ctrl+o

If you have problems  using this text editor why you don't try with other you are familiar with.
This is all new to me as I have not edited a file like this before. After I did ctrl O it as what file to write to.

---

### Post by rukiaEnix on 2012-07-05
OK, you just press ENTER, you can change the name of the file but we don't want that, so just ENTER.

---

### Post by rickm1945 on 2012-07-05
> **Morbius1 said:**
> Like ... oh I don't know ... this one:

BTW, Changing browseable on the printers share will be ignored by samba since the [printers] share is not a browseable entity. If you run testparm after the edit you will see that samba sets it back to No because it assumes you were kidding.

Can I assume you didn't add the netbios name in smb.conf?
Oh, Ok Thank you. This would have driven me crazy. Now I will leave it alone. I wondered if I was doing this correct since I have never heard of browsing for a  printer.

---

### Post by rickm1945 on 2012-07-05
> **Morbius1 said:**
> Like ... oh I don't know ... this one:

BTW, Changing browseable on the printers share will be ignored by samba since the [printers] share is not a browseable entity. If you run testparm after the edit you will see that samba sets it back to No because it assumes you were kidding.

Can I assume you didn't add the netbios name in smb.conf?
Yes, I didn't add anything. Just set Browsable to yes, but it didn't change, it is still no.

---

### Post by rukiaEnix on 2012-07-05
Just try it with one of your other shares.

---


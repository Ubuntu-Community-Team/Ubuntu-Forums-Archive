---
title: "can't see xp network"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by zebraneo on 2009-09-29
I can't see one of my xp network, any ideas here is the smb.conf 


[global]
    workgroup = PRETTY
    netbios name = XP
    server string = Samba %v on (%h)
    security = SHARE
    printcap name = cups
    disable spoolss = Yes
    show add printer wizard = No

[printers]
    comment = Printer in Linux
    path = /var/spool/samba
    guest ok = Yes
    printable = Yes
    use client driver = Yes
    browseable = No

[Security]
    read only = No
    available = No

---

### Post by cariboo on 2009-09-29
Ubuntu connects to XP by default, you don't need samba. You do need samba running in order for your Windows computers to see your Ubuntu system.

Can you ping any of the windows computers on your network?

---

### Post by swerdna on 2009-09-30
The Samba packages must be installed and configured properly for you to see the xp machines. This is set correctly by default in Ubuntu but many things can prevent it from working properly, like changing the smb.conf file or the UFW firewall.

For starters I suggest adding this line into the [global] stanza of smb.conf (then reboot):```
name resolve order = bcast host lmhosts wins
```
[FFI: [Setting up a Samba Client (Browsing Only)]("http://ubuntu.swerdna.org/ubulanprimer.html#client")]

and turn off the UFW firewall temporarily to see if visibility improves, using this command:```
sudo ufw disable
```
[FFI: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")]

---

### Post by zebraneo on 2009-09-30
Yea I can ping the other computer, and I added the code but it still can't work I still can't get nto the computer

---

### Post by swerdna on 2009-09-30
> **zebraneo said:**
> Yea I can ping the other computer, and I added the code but it still can't work I still can't get nto the computer

Info is really sparse here, lets look at these:

[LIST]
[*]Do you mean that you can't get into the Ubuntu computer from another computer or vice versa.
[*]And what operating system is on the other computer?
[*]What does "can't get into mean"? Does it mean that you can't see the computer, that you can see the computer but not the share, or that you can see the computer and the share but when you click on the share access is denied?
[/LIST]

---

### Post by Iowan on 2009-09-30
The "missing" machine is in the same workgroup - and has a folder shared?

---

### Post by zebraneo on 2009-10-01
the computer that i can't see is xp, and they are on the same networks

---

### Post by swerdna on 2009-10-01
What does "can't get into mean"? Does it mean that you can't see the xp computer, that you can see the xp computer but not the share, or that you can see the xp computer and the share but when you click on the share access is denied?

---

### Post by zebraneo on 2009-10-01
I can't see the xp compter

---

### Post by swerdna on 2009-10-01
Here are four questions:
[LIST=1]
[*]There is a microsoft windows firewall on the xp computer. Turn it off and reboot both computers. Is there any difference? (I don't expect this will fix it but it must be done to eliminate one of the possibilities)
[*]Is there a third-party firewall on the xp computer (i.e. apart from the microsoft windows firewall)?
[*]What is the "workgroup" name on the xp computer? (GoTo Control Panel --> Classic View --> System ---> Computer Name --> Workgroup)
[*]What is the "full computer name" on the xp computer? (GoTo Control Panel --> Classic View --> System ---> Computer Name --> Full Computer Name)
[/LIST]

---


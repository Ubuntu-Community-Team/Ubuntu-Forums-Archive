---
title: "Wireless card issues"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by tal82k on 2006-02-01
Have tried Linux before but never got it quite right.  Then I  found Ubuntu and the install was Breezy as a Badger.  

I am trying to setup my wireless card (dwl-g650), but to do so, I need to use sudo.  When I do, I put in my password, and it just goes to a new shell command line (without displaying what I asked for).  For example:```
tal@simply:~$ sudo lshw
Password:
tal@simply:~$
```

Why is sudo not working?  

Similarly if I go System->Administration->Networking, It asks for the password which I give, but then nothing happens....

What shall I do?

---

### Post by Lambert on 2006-02-02
type this command 

```
groups name
``` 
replace name with user name and it will show what groups you're in.

then run this command

```
cat /etc/sudoers
``` 
You should see something like this

```
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

``` 
the sudoers file needs to have something else listed besides the root line and if it's a group you need to be a member of that group to have sudoers privledges.

Not sure if this is the answer but there are posts around the forum on this subject, just search for sudoers.

---

### Post by tal82k on 2006-02-02
I did groups and it said```
tal : tal adm dialout cdrom floppy audio dip video plugdev lpadmin scannner
```

I then did the cat command:```
tal@simply:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
```

Any suggestions?

---

### Post by tal82k on 2006-02-02
Logged in recovery mode and repeated above steps (didn't realize i had to be root).  There are only two uncommented lines to my sudoers.```
Defaults        !lecture, tty_tickets,!fqdn


root              ALL-(ALL) ALL
```  Is this right?

---

### Post by andy101 on 2006-02-02
Are you certian its sudo thats not working and not just lshw thats not working?

Does sudo work with other commands?

You could try:
```
cat /etc/sudoers
```

or you could try running sudo as session:
```

$ sudo -s
Password: [TYPE YOUR PASSWORD]
# lshw

```
(don't type $ or # they are ment to represent the terminal prompt. as root user yoo normally have a # prompt I think)
When you have finished type:
```
exit
```
The prompt shpuld change back to $ and you will no lonmger have root privs.

---

### Post by tal82k on 2006-02-02
lshw worked before without sudo it just said that you should run it with sudo (but you dont need to).  When I tried sudo -s, it prompted for password, which I gave.  Then it went back to the regular prompt... I tried lshw again, but again it said WARNING: you should run this as super-user

I just want to modprobe the atheros module...Why is it so mean to me?

---

### Post by Lambert on 2006-02-02
If you log into recovery mode, you should beable to run

```
visudo
```

which edits the sudoers file. Add your name or the admin group to the file and make it look like the root line. Then if you chose the group admin, add your self to the admin group. Go to system>administration>users and groups.

I'm not 100% on this so it might be helpful to search the forums. use keyword sudoers.

---

### Post by tal82k on 2006-02-03
So I visudoed, and added myself and all was good.  I modprobed and it worked.  I went into System-> Administration -> Networking.  The device was recognized.  I clicked configure and told it that my ESSID was 2WIRE170.  I told it to DHCP.  But something went wrong...The icon appears in the taskbar and says that I'm connected, but when I click the properties of that, I dont have an IP!  I am connected to the network somehow but now connected to the internet...Any ideas?

---

### Post by SickTwist on 2006-02-03
The reason sudo did not work earlier is because the user trying to run sudo was not part of the "admin" group. To correct this, run the following command from a user account that can already use sudo:

sudo adduser *USER* admin

*USER* is the name of the user you wish to add to the admin group.

As for the connection problem, try installing [NetworkManager]("http://www.gnome.org/projects/NetworkManager/") (It's in universe):

sudo apt-get install network-manager

To start it, press ALT+F2 and type "nm-applet" (without quotes) then press Enter. It will automatically connect to a wired network when one is available. Otherwise, it will search for wireless networks and let you select which one you would like to use. Once you have selected one, it will remember your preferred network and attempt to connect to it automatically whenever the wired connection is not available.

To have it start automatically, click System-->Preferences-->Sessions, click on the "Startup Programs" tab, click "Add", type "nm-applet" (again, without quotes), click "OK" and click "Close". Then it will automatically start with each session.

---

### Post by tal82k on 2006-02-09
Laptop is sort of offline right now (nice rip in the power cord), but once it gets back up and runnin I'll try that.  On the note of sudo, that user was the only non root user on the system...so would I do the user add command in the recovery mode?  Thanks!

---


---
title: "Wireless but no Wired Connection"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by olimb on 2010-08-17
On a Toshiba laptop I need both wired and wireless capability.
I started by installing Ubuntu 10 but couldn’t get any internet, wired or wireless and the wireless usb mouse didn’t work. So I deleted that and installed Ubuntu 9.10 now I can get wireless internet and the wireless usb mouse works, but no wired connection.

Next I read some of the forum threads and tried to using the terminal but commands that use sudo return
[sudo] password for t2
when I try to enter my password nothing will type.

lspci –nn
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:2930] (rev c1)

any help appreciated

---

### Post by bkratz on 2010-08-17
> **olimb said:**
> On a Toshiba laptop I need both wired and wireless capability.
I started by installing Ubuntu 10 but couldn’t get any internet, wired or wireless and the wireless usb mouse didn’t work. So I deleted that and installed Ubuntu 9.10 now I can get wireless internet and the wireless usb mouse works, but no wired connection.

Next I read some of the forum threads and tried to using the terminal but commands that use sudo return
[sudo] password for t2
when I try to enter my password nothing will type.

lspci –nn
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:2930] (rev c1)

any help appreciated

Don't know what you are trying to do, but when you use a "sudo" command the password is never echoed to the screen--just type it in and press enter, the command will execute.

---

### Post by dineshs on 2010-08-17
what do you get for
```
sudo lshw -C network
```

---

### Post by olimb on 2010-08-17
sudo lshw –C network
[sudo] password for t2:

After that all the keys on the keyboard are locked out only Enter works which produces

Sorry, try again
[sudo] password for t2:

---

### Post by Iowan on 2010-08-17
> **olimb said:**
> After that all the keys on the keyboard are locked out only Enter works which producesWhat is the indication that the keys are locked?

> **bkratz said:**
> Don't know what you are trying to do, but when you use a "sudo" command the password is never echoed to the screen--just type it in and press enter, the command will execute.What happens when you try this?
"The password is never echoed to the screen" means not even asterisks are displayed.

---

### Post by olimb on 2010-08-17
I tried all these

The password is never echoed to the screen
“The password is never echoed to the screen”
sudo The password is never echoed to the screen
sudo “The password is never echoed to the screen”

whenever I use sudo I get

[sudo] password for t2:   (nothing will type in here only pressing enter will do anything) 
Sorry, try again
[sudo] password for t2:
Sorry, try again
[sudo] password for t2:
Sorry, try again
sudo: 3 incorrect password attempts

---

### Post by Iowan on 2010-08-17
Sorry - I should have added a blank line. The "this" I referenced is:

---

### Post by Iowan on 2010-08-17
Sorry - I should have added a blank line. The "this" I referenced is:> **bkratz said:**
> -just type it (the password) in and press enter, the command will execute.

---

### Post by olimb on 2010-08-18
I’m still a bit new at using the terminal
I think you are saying to enter the password, which is t.

When I enter the password 
t
t: command not found

When I try
sudo t
[sudo] password for t2:
Sorry, try again
etc.

---

### Post by Iowan on 2010-08-18
If the password is "t", try this:
[COLOR="Blue"]sudo lshw &#8211;C network[/COLOR]
[sudo] password for t2:
[COLOR="Blue"]t[/COLOR] [enter]
(where [enter] is the key - not the word)
If it doesn't work, you may need to reset the password:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by olimb on 2010-08-20
I am going to wipe this drive and reinstall again from scratch
I had an error message during the install but didn’t pay any attention to it.
During the next install if I get the error again I’ll write it down.
Thanks to everyone who helped.

---


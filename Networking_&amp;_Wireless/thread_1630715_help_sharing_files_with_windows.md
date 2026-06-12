---
title: "help sharing files with windows"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by westkid on 2010-11-25
does anyone knows how to share files with windows 7 using ubuntu 10.04 over a wireles router? i share my internet connection with wifi devices and would love to share files with my cousin laptop running windows 7.

i have samba installed but cant get it configured. running "sudo vi /etc/samba/smb.conf" gives me this in terminal.


E325: ATTENTION
Found a swap file by the name "/var/tmp/smb.conf.swp"
          owned by: root   dated: Thu Nov 25 14:10:14 2010
         file name: /etc/samba/smb.conf
          modified: YES
         user name: root   host name: andykriss-desktop
        process ID: 30761
While opening file "/etc/samba/smb.conf"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/samba/smb.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/smb.conf.swp"
    to avoid this message.

"/etc/samba/smb.conf" [New DIRECTORY]
Press ENTER or type command to continue


and this after pressing continue


~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~        



need help plz.. tnk u

---

### Post by jonandrews on 2010-11-26
I have written a step-by-step guide to configuring file sharing between Ubuntu & Windows pc's..  Take a look:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by faial on 2010-12-07
Hi Jon Andrews,

Thanks for the great guides for us long-time low-tech Windows users recently converted to Ubuntu.

I'm trying to connect my Ubuntu machine to the pre-existing Windows network. I'm using your [Ubuntu 8.10 & 9.04/ Windows Networking]("http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm") guide.

It so happens that from the 3 Windows PC I can see and connect (read  & write) to the shared folder on the Ubuntu machine but not the other way round! Whenever  I click on the Windows network icon in Places->Network the "Unable  to mount location / Failed to retrieve share list from server" message  pops up. Where did I miss?

---

### Post by faial on 2010-12-07
UPDATE on previous post

After a few more reboots of the several machines I can now see WORKGROUP after clicking on the Windows network icon in Places->Network.

And I can even click the WORKGROUP icon and see the PC that are connected.

But, alas, when I click on the icons of the Windows-running machines nothing happens except the now usual message "Unable to mount location / Failed to retrieve share list from server" pops up. If I click on the Ubuntu machine icon I access - obviously? - the shared folder and printer.

Any ideas?

---

### Post by dandnsmith on 2010-12-07
Following a hint in these forums a couple of days ago, I tried:

Places|Network, connect to server
gave the server name, the share name, and the username
and then (after a password) was connected.

This seemed to work where the route you (and I) tried didn't.
Why - I haven't a clue, except it worked before I'd got as far as getting the Samba modules I wanted, and configuring them.

The other puzzling thing was that my Windows machines are on my own workgroup name, where the linux seemed to work with WORKGROUP.

HTH

---

### Post by faial on 2010-12-07
EUREKA! And I'm not Archimedes of Syracuse - or any other odd place.

It  turns out that my Windows-running PC had names "outcast" by the  network... And I thought we were in the XXI century... These names  worked perfectly with Windows but it seems Samba? Ubuntu? is more like  15+ years old Windows (IN THIS respect). I just couldn't know this  because when running smbtree in terminal the result was nil zero nothing  at all. I just had not run this command since  frozen-Windows-network-icon a few hours back. Mea culpa, mea maxima  culpa. Sooo, keep those network names short!

Anyway, thanks for the input dandnsmith.

---

### Post by faial on 2010-12-08
> **faial said:**
> EUREKA!
/.../
Sooo, keep those network names short!
/.../

I meant NetBIOS-short.

---

### Post by dandnsmith on 2010-12-08
> These names worked perfectly with Windows but it seems Samba? Ubuntu? is more like 15+ years old Windows (IN THIS respect).

You're quite right there.
Samba works according to the original (Msoft?) SMB definitions, whereas Windows these days may well not even have the SMB stuff loaded. Msoft feels quite free to ignore any rules it created, when inconvenient.

---


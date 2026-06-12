---
title: "File and Printer sharing problems between Ubuntu 10.04 - Vista"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by cheapsk8 on 2010-05-08
Hi, yes, I am a linux noob. The thread title gives the basic problem I am having now. I will elaborate on this below. First I want to describe my setup (shown in picture at the bottom):


[LIST]
[*]Desktop with XP and Ubuntu 10.04 (wired to netgear router)
[*]HP LaserJet 6P on LPT1 of Desktop (to be shared)
[*]Netgear Router with WPA2
[*]Laptop1 w/ Vista, wireless
[*]Laptop2 w/ XP, wireless
[/LIST]
With all machines running Windows products, I can share files and printers. Everything works as it should. This leads me to believe I have no router issues.

With the Desktop running Ubuntu 10.04, I have the following problems:

[LIST]
[*]Ubuntu cannot find the printer. It disappeared. I had it configured yesterday and printed some test pages from the ubuntu desktop. I started to do some research on how to get Vista to see it over the network but that is moot right now because Ubuntu can't see it. System>Administration>Printing gives me nothing. The window is blank and from there I can't goto Server>New>Printer. It won't let me. Server>Connect gives a CUPS server error.
[*]Ubuntu can't see shared files from the laptops. If I hit Places>Network it shows all three computers on the network but does not mount them "Unable to mount location."
[/LIST]

Successes so far:

[LIST]
[*]I have no problems connecting to the internet from any machine.
[*]I was actually able to setup a share folder in Ubuntu that is recognized as a mapped network drive in Vista. Samba and some editing did the trick there.
[/LIST]
NOTE: I haven't tried to do anything other than get on the internet with the XP laptop.

I did some reading here about using the "sudo etc/init.d/samba restart" command but that returns a "command not found" error. I also tried "sudo etc/init.d/smbd restart" but got the same error.

Any ideas?

Thanks

EDIT: To get Vista to see the shared Ubuntu folder (as mapped network drive) to begin with, I followed the procedure (customized for my particular setup) outlined here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=WINS+workgroup](http://ubuntuforums.org/showthread.php?t=202605&highlight=WINS+workgroup)

except that for Vista I ignored the section where talks about "**2. Changing network settings in Windows" **and I haven't yet implemented the Security considerations.

---

### Post by gordintoronto on 2010-05-08
Have you changed the workgroup name in Ubuntu to match your Windows machines? To change it, open Accessories/Terminal and enter this command:
gksudo gedit /etc/samba/smb.conf

The first "Global Setting" is the workgroup name.

I've never heard of a printer disappearing.

---

### Post by cheapsk8 on 2010-05-08
Yes, that was added before when I was trying to get Vista to see the Ubuntu Network drive.

---

### Post by cheapsk8 on 2010-05-08
Terminal Command:> sudo service cups startbrings my printer back up in Lucid. Will I have to write a script to run at login every time I reboot?

Now working on getting Vista to see the printer. Any hints?

---

### Post by cheapsk8 on 2010-05-08
Ok, to get Vista to see the printer across the network, make sure the following is done:


[LIST]
[*]System>Administration>Printing>Printer>Properties>Policies has the following checked: Enabled, Accepting Jobs, Shared
[*]System>Administration>Printing>Printer>Properties>Access Control has "Deny printing for everyone except these users:" selected and then add all of the relevant users
[*]System>Administration>Printing>Server>Settings has "Publish shared printers connected to this system" checked
[*]System>Administration>Users and Groups>Manage Groups> has "lpadmin" added
[/LIST]
As soon as this was done the printer showed up on the Network Window in Vista under the Ubuntu machine icon. From there I added the printer in Vista although it wanted to download the driver again. 

Now it works!

---

### Post by cheapsk8 on 2010-05-08
Now onto tackling the next problem: getting Ubuntu to see my shared Vista folders.

Still getting the "Unable to mount location" error.

---


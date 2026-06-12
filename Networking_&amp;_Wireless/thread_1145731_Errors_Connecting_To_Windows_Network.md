---
title: "Errors Connecting To Windows Network"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by ebanlague on 2009-05-01
Currently I'm having problems connecting to a Windows Machine with the intentions of using the printers plugged in to that computer. Here is my network set up.

Internet goes to modem, which plugs into a switch. The switch sends that signal to another ethernet port in my house, which then goes to my router, then the signal is sent back. My computer is plugged directly into the Router. The singal then goes back to the switch from another ethernet port, then all the other computers in the house are plugged into the switch.

Alright, now the base problem. When I go to  'Places > Network > Windows Network > [Then my Homegroup]' When I click the Homegroup it says

'Unable To Mount Location"
'Failed to retrieve share list from server'

I'm wondering what this is about, and how to remedy it. The computer I need to connect to is a Vista machine with 2 printers.

Thanks, Evan.

---

### Post by Merel 469 on 2009-05-02
You are not alone. Seems to be a common bug. I searched around for a solution. You might be helped by the following instructions. 

I copied the information [ from THIS TOPIC](http://ubuntuforums.org/showthread.php?t=1135842&highlight=Windows+Network)

1. Install winbind

sudo apt-get install winbind


2. Edit /etc/nsswitch.conf

sudo gedit /etc/nsswitch.conf


2.1 Look for the line : hosts: files (etc)

	If yours is like mine was when it didn't work, it'll read something like:
	hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

	.. .although what is there will vary but files and dns will be there.


2.2. What is missing is an entry for wins.
	
	You need to add wins after files so it looks like (alter as required):
	hosts: files wins mdns4_minimal [NOTFOUND=return] dns mdns4


2.3.  Save the modified file.

3. Reboot.

4. Please post your findings to this thread at (English) Ubuntu Forum : 
	[http://ubuntuforums.org/showthread.php?t=1134738](http://ubuntuforums.org/showthread.php?t=1134738)  



By the way : It didn't work for me.
I can see another PC in my existing Windows network (with all the shared folders) _but my own PC is not even detected as being part of the network_). 

I created a shared "TEST" folder on my own PC. As a result Ubuntu creates (not asking for permission for it) a "new" second network,named MSHOME, with ONLY my own PC, and this shared test file.

---


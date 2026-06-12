---
title: "file sharing - vista can see ubuntu, ubuntu cannot see vista"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by guest5 on 2010-11-24
After a reinstall of 10.10, I am able to turn on file sharing and so I set up a shared folder.  

Windows Vista can see this folder but in my network place, there is only one icon, and it's a "Windows Network" icon.  Upon clicking on that, I can see the local network, "Rompus Room".  

When I click on Rompus Room, nothing happens for a while, then I get a message saying, "Opening "ROMPUS ROOM".  Then I get the final message, "Unable to mount location", followed by, "Failed to retieve share list from server"

HELP ...

---

### Post by cariboo on 2010-11-24
To see what shares are available on the network, open a terminal and type:

```
smbtree
```

All the shared directories on your internal network should show up similar to this:

```
 smbtree
Enter cariboo's password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
		\\WILLY\TV2            	TV shows part 2
		\\WILLY\TV1            	TV shows part 1
		\\WILLY\Images         	iso images
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Documents      	Documents
		\\WILLY\Music          	Music
		\\WILLY\Movies         	Ripped DVDs
		\\WILLY\print$         	Printer Drivers
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
		\\RISKY\John
```

---

### Post by jonandrews on 2010-11-26
I'm not sure what you mean when your refer to your network as 'Rumpus Room'.  If that is the name you are using for your Windows workgroup, then that may well be the root of the problem. Take a look at my networking guides, and in particular the guide on Windows Workgroups, at  [www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by guest5 on 2010-11-26
Thank you both very much for the responses.  3 pc's, 2 Ubuntu 1 Vista.

cariboo907, 

Here are the results for the command "smbtree":

sail@sail--PC:~$ smbtree
Enter sail's password: 
WORKGROUP
	\\NATALIE        		
cli_start_connection: failed to connect to NATALIE<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
ROMPUS ROOM
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\share -helen   	
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\SAIL--PC       		sail--PC server (Samba, Ubuntu)
		\\SAIL--PC\share-10.10    	
		\\SAIL--PC\IPC$           	IPC Service (sail--PC server (Samba, Ubuntu))
		\\SAIL--PC\print$         	Printer Drivers
sail@sail--PC:~$ 

NATALIE is a vista pc.  ROMPUS ROOM is the name of the local simple file sharing network.  Hopefully this is clear enough to understand, if not please ask for further clarification.

Worthy of note, is that the other Ubuntu pc (helen) also receives the same error when trying to connect to this pc, "SAIL" but I connect fine to it.
Again, the windows pc can see me, SAIL, and use my shared folder.  The windows pc's can share files no prob.

jonandrews,
Thank you, I will look into your suggestion.

Thank you both for your input & I await a hopeful next step in the process.

Also, files are locked when they are exchanged in Ubuntu, with the owner being "Nobody".  Is there a way to use the files we share? chmod or something I can use ?   Sorry, sort of new at this...

---


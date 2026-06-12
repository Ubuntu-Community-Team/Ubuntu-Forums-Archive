---
title: "Connecting to Home Network."
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by DaHoov on 2011-05-28
[FONT=Times New Roman][SIZE=3]I am new to Ubuntu but I am fairly proficient in computers. I have what seems to be a simple question. However I can't seem to find an answer that actually works.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am trying to connect a Ubuntu (actually using Kubuntu) based computer to my Home Network. It is a typical windows based Home Network. It includes three windows seven machines and a home server (WHS). The server actually has SMB shares installed in order to talk to one of the media players.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The workgroup is named workgroup. I've tried everything over the last two days but can't seem to get the Ubuntu machine to recognize the workgroup. Currently the machine is hard wired into the network. [/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I would really like to get the machine working using Ubuntu. But if I can get file sharing to the server up and working, its really not worth the effort. [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Any ideas? Tkx![/SIZE][/FONT]

---

### Post by Zorael on 2011-05-28
Do you have the **[smbclient](apt://smbclient)**, **[samba](apt://samba)** and (optionally) the **[smbfs](apt://smbfs)** packages installed? If so, run '**smbtree**' from the terminal and see what it discovers.

```
$ smbtree
Enter zorael's password: *<no need to enter a password unless you have password-protected shares in the network>*
LAPPNET
        \\LETHE                         lethe server (Samba, Ubuntu)
                \\LETHE\1700n           Dell Laser Printer 1700n
                \\LETHE\p1505n          Hewlett-Packard HP LaserJet P1505n
                \\LETHE\IPC$            IPC Service (Kubuntu 11.04: lethe)
                \\LETHE\audio          
                \\LETHE\temp           
                \\LETHE\print$          Printer Drivers
```

**edit:** Oh, and take a look at [this thread](http://ubuntuforums.org/showthread.php?t=1169149) for a bunch more stuff.

If you want to mount shares to a local directory, you may want to take a look at **[Smb4K](apt://smb4k)**. Or just do it from the terminal, if you're so inclined. :3

---

### Post by DaHoov on 2011-05-28
Did it and got


lisa@lisa-Latitude-D620:~$ smbtree
Enter lisa's password: 
WORKGROUP
DUNE
        \\SERVERNAME                  Dune SMB server
cli_start_connection: failed to connect to SERVERNAME<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
lisa@lisa-Latitude-D620:~$ ^C
lisa@lisa-Latitude-D620:~$ 


I changes the name of the Server to SERVERNAME . DUNE is a networked media server Samba capabilities.

Not sure what this means but it saw the server???

---

### Post by Zorael on 2011-05-28
I don't recognize the error message but let's try setting up NetBIOS hostname resolving. Install the **[winbind](apt://winbind)** package, and then open up **/etc/nsswitch.conf** in a text editor with superuser permissions. Find the **hosts** line uptop and add **wins** before **dns**, as below;
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] **[COLOR="Green"]wins[/COLOR]** dns mdns4
networks:       file

**[...]**
```
Make sure you can ping SERVERNAME's ip (just incase), and then try pinging the host **SERVERNAME** itself. It should resolve now, with winbind installed and nsswitch.conf set up as above. Now try smbtree again. If it still spouts the same error message, try increasing the debugging output with the **-d** argument.
```
$ smbtree -d 3
*<lots of debugging output that might just be a tiny bit more revealing than simply NT_ERRORMESSAGE_NO_WORKY>*
```

---

### Post by DaHoov on 2011-05-28
Installed the winbind package. After that I'm lost. Sorry.. This is new territory for me. Maybe I'm in over my head.

---

### Post by Zorael on 2011-05-28
All right, we're hopefully almost done. :3

Pop up a run box (Alt+F2), enter '**kdesudo kate /etc/nsswitch.conf**'. Kate (the text editor) should start up with said file opened. Add **wins** there as in my previous post and save. Then try smbtree again.

---

### Post by DaHoov on 2011-05-28
[FONT=Courier New]
Got it

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
[/FONT]

---

### Post by DaHoov on 2011-05-28
[FONT=Courier New]Ran smbtree and got

Enter lisa's password: 
WORKGROUP
DUNE
        \\SERVERNAME                  Dune SMB server
cli_start_connection: failed to connect to SERVERNAME<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
lisa@lisa-Latitude-D620:~$ 
[/FONT]

---

### Post by Zorael on 2011-05-28
Curious.

Could it be related to [this bug](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/356022)? The last comment there is from January and has a few suggestsions you could try.

---

### Post by DaHoov on 2011-05-28
[FONT=Courier New] When I ran "smbtree d-3" i got a lot of info. It actually saw all the computers on the network. It just wont hook up???
[/FONT]

---

### Post by Zorael on 2011-05-28
Can you ping the other computers by their hostnames (computer names) now? Meaning, pinging 'dune' instead of its ip? Or was its name 'servername'...

```
$ ping dune
PING dune (192.168.1.10) 56(84) bytes of data.
64 bytes from dune (192.168.1.10): icmp_req=1 ttl=64 time=0.072 ms
64 bytes from lethe (192.168.1.10): icmp_req=2 ttl=64 time=0.055 ms
64 bytes from lethe (192.168.1.10): icmp_req=3 ttl=64 time=0.058 ms
64 bytes from lethe (192.168.1.10): icmp_req=4 ttl=64 time=0.054 ms
^C
--- dune ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.054/0.059/0.072/0.011 ms
```

Also try separately browsing with Dolphin now and see if it has gotten any wiser. Run box (Alt+F2): '**dolphin smb://dune**' or '**dolphin smb://servername**' or whatever the name was.

---

### Post by DaHoov on 2011-05-29
Cant ping the Dune. I get 
 
PING dune(207.223.0.140) 56(84) bytes of data
 
then i never get a prompt again. I think I reached my limit on this. Besides it doesnt look like I can get the wireless to work either. If I cant get wireless its pointless anyway. And by the looks of it a lot of people are having the same issue.
 
Darn. I like the OS. I was looking for something simple. Just wanred something to use on my old Dell Lat D620 to surf, e-mail, play a few tunes and vids. Tired of Windows poor @$$ preformance. Thought Ubuntu would be the trick. I am not afraid of a tech challenge but I do have a life away from the computer.:(

---


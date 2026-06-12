---
title: "[SOLVED] Intrepid - HDHomeRun - Gnome/network manager eth0 ip address is late"
date: 2008-09-20
forum: Mythbuntu
---

### Post by rob3435 on 2008-09-20
I'm currently testing a new backend (8.10-sep20) to replace my existing 8.04 backend.  (The old unit ran out of pci/memory slots and the onboard ethernet port just couldn't handle the 2 new HD streams from the HDHomeRun.)

The new backend is running myth well, but i've noticed a couple issues. 

1. Network Manager seems to override /etc/network/interfaces.. (workaround: setup the dhcp server to force a specific ip to the unit..)

2. The mythbackend loads before the network manager has received an ip address from the dhcp server, is their a quick way to have mythbackend load after a valid ip? (Current workaround, is to login into the backend and restart mythbackend, however this isn't ideal for a headless backend...)

mythbackend.log :  
Starting up as the master server.
2008-09-20 11:40:33.181 mythbackend: MythBackend started as master server
2008-09-20 11:40:33.397 HDHRChan(101440ab/0), Error: Unable to send discovery request
                        eno: Network is unreachable (101)
2008-09-20 11:40:33.404 mythbackend: Problem with capture cards: Card 1failed init
2008-09-20 11:40:33.409 HDHRChan(101440ab/1), Error: Unable to send discovery request
                        eno: Network is unreachable (101)
2008-09-20 11:40:33.413 mythbackend: Problem with capture cards: Card 2failed init
ERROR: no valid capture cards are defined in the database.

Regards,
Rob

---

### Post by ian dobson on 2008-09-20
Hi,

Try changing the startup script to start later in in the init process. On my box Mythtv-backend starts as /etc/rc2.d/S24mythtv-backend.

Just change your /etc/rc2.d/Sxxmythtv-backend to S99mythtv-backend so that it starts at the end of the init process.

Regards
Ian Dobson

---

### Post by rob3435 on 2008-09-20
Thanks Ian,

That works like a charm.

On my default install Network Manager was S30 so i moved mythtv-backend just after that..

```
sudo mv /etc/rc2.d/S24mythtv-backend /etc/rc2.d/S99mythtv-backend 
```

bazaar isn't working at the moment, so i can't determine where S24mythtv-backend is set in mythtv and write a patch for it. But for HDHomeRun/Network manager user's this might be a common problem.

---

### Post by verevi on 2008-11-12
I have the same issue.  I changed the services so that mythtv-backend was S99 and the networkmanager was S18.

It still seems to be connecting late.  If I try to change the network settings from DHCP to manual, it just changes back to DHCP when I restart.

If I restart the backend after starting up the PC, everything works fine with the HDHomeRun, so I'm pretty sure this is the same issue.

Any help would be greatly appreciated.

---

### Post by gungfujoe on 2009-01-17
I too am having this problem.  I moved the mythtv-backend to S99 and even moved the Network manager up a few slots, and that did not solve the problem.  My tuner (HDHomeRun) is still unavailable initially, unless I manually restart the mythtv backend after the system finishes loading.

Additionally, I can't get Network Manager to actually give me a static IP.  I set it to Manual, define an Address, Netmask, Gateway, and DNS, but it goes back to automatic when I restart.

---

### Post by Dewey_Oxberger on 2009-01-19
I had this problem and changing the order of files in rc2.d DID NOT fix the problem.  A little sniffing showed my system's eth0 just comes up slow.

From my post on the HDHomeRun forum:

[http://www.silicondust.com/forum/viewtopic.php?t=6125](http://www.silicondust.com/forum/viewtopic.php?t=6125)

So I created this script, called it S49WaitForHDHomeRun, and put it in /etc/rc2.d

let retries=0
echo -e "Waiting for network to reach HDHomeRun\n"
until hdhomerun_config discover >/dev/null
do
  if [ $retries -gt 15 ]; then
    eerror "Timed out, no HDHomeRun found"
    return 1
  fi
  echo -n "-"
  sleep 1
  let retries=retries+1
done
echo -e "HDHomeRun found\n"


Works everytime now.

---

### Post by linuxgrrl on 2009-10-26
I have the same problem ... Dewey, I tried your script and it seems to run fine from command line, saying "hd homerun found,"  but when placed in rc.d it throws an error like: "let: gt: unexpected argument" 

I put the script in and changed the permissions to match the other scripts in /etc/rc2.d, so if there is any clue as to what I'm doing wrong, please advise!

---

### Post by Dewey_Oxberger on 2009-10-26
Wow, old post.  Some of my mistakes die hard. ;)

The script was missing the "#!/bin/bash" on the first line.

In /etc/rc2.d I have NetworkManager running (S50NetworkManager), then this script running (S61WaitForHDHomeRun), then mythtv-backend (S62mythtv-backend).  Your exact positions may vary but the general order needs to be the same.  

Here is what I'm using now:

```
#!/bin/bash
let retries=0
echo -e "Waiting for network to reach HDHomeRun\n"
until hdhomerun_config discover >/dev/null
do
  if [ "$retries" -gt 15 ] 
  then
    echo -e " waited $retries seconds"
    echo -e "Timed out, no HDHomeRun found"
    exit 1
  fi
  echo -n "-"
  sleep 1
  let retries=retries+1
done
echo -e "HDHomeRun found\n"

```

I hope that helps.

---

### Post by luigidk on 2009-11-20
I hate asking but...

Do I have to do anything to that script to make it executable?  Any CHMOD commands or ???

---

### Post by Dewey_Oxberger on 2009-11-21
On my 8.10 system I have it set up like this:

The script is called S61WaitForHDHomeRun and it is in /etc/rc2.d directory

The script is set 777, owner root, group root.

The order of items has been tweeked:

S50NetworkManager
S61WaitForHDHomeRun
S62mythtv-backend

You can see what is happening during boot using Ctrl + Alt + F8

Ctrl + Alt + F7 changes you back to the GUI.

---


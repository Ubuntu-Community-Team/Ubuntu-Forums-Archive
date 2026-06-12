---
title: "Mythtv starts too fast"
date: 2009-03-08
forum: Mythbuntu
---

### Post by Familienvater on 2009-03-08
I have a Compact Flash-Card in my Mythbuntu-Frontend (Intrepid) and a separate backend. After changing this one to a newer and faster model my frontend now always starts before the network connection is established and I always get the blue screen with the message "Please select your preferred language". 1 second later I get this small window telling me that a network connection is established. Restart of Mythtv always helps.

It would be great if one of you could tell me

how to speed up connecting to the network

or slow down the start of Mythtv

or let Mythtv wait until network is established.

Thank you very much!

Familienvater

---

### Post by scary_jeff on 2009-03-08
I had this problem, and from my research, there were 3 things to try:

1) Re-order the starting of services in /etc/rc2.d using the update-rc.d command.
2) Modify the MythTV start script to wait for the network to be up.
3) Uninstall network manager, and use configuration files to set the network up.

1) didn't work for me, 2) I didn't try, and 3) worked in the end.

---

### Post by Familienvater on 2009-03-15
Thanks Scary Jeff,

I tried 1) because it sounded to be the easiest approach. But it did not work for me either.

So I will try your 3rd proposal.

Thanks again.

Familienvater

---

### Post by Hobgoblin on 2009-03-15
> **scary_jeff said:**
> I had this problem, and from my research, there were 3 things to try:

1) Re-order the starting of services in /etc/rc2.d using the update-rc.d command.
2) Modify the MythTV start script to wait for the network to be up.
3) Uninstall network manager, and use configuration files to set the network up.


4) start mythfrontend from a script with a suitably long sleep in front of it.

---

### Post by Da_Teach on 2009-03-16
> **Familienvater said:**
> Thanks Scary Jeff,

I tried 1) because it sounded to be the easiest approach. But it did not work for me either.

So I will try your 3rd proposal.

Thanks again.

Familienvater

Another option would be to create a script which waits for an IP number. I forgot how to do this (I suck at sh-scripts ;)) but I had this setup on my old frontend.

I need to find it again, but google is failing on me ;)  
(I have had the same issue as you but doesnt happen often)

---

### Post by freddyg on 2009-03-17
someone check me on this, but i think you can stop mythtv from starting in its normal fashion and then cause it to start with a delay.

command line: sudo rcconf --> tab down and deselect mythtv from the list by hitting the space bar, follow directions to close rcconf

command line: sudo vim /etc/rc.local   ----or use whatever editor you like and add these two lines at the end of the script: 
sleep 3 #may need to adjust number
/etc/init.d/mythtv-backend start
exit 0 #this line already exists

---

### Post by nickrout on 2009-03-17
> **freddyg said:**
> someone check me on this, but i think you can stop mythtv from starting in its normal fashion and then cause it to start with a delay.

command line: sudo rcconf --> tab down and deselect mythtv from the list by hitting the space bar, follow directions to close rcconf

command line: sudo vim /etc/rc.local   ----or use whatever editor you like and add these two lines at the end of the script: 
sleep 3 #may need to adjust number
/etc/init.d/mythtv-backend start
exit 0 #this line already exists

The OP is not using a backend. This only delays the start of the backend, which is irrelevant.

the frontend usually starts from the auto logged-in X user, you would need to add a delay (or check for IP address) in the frontend startup script.

---

### Post by Email on 2009-04-26
5) create a script that starts mythfrontend when the connection is established

NetworkManager calls the scripts placed in /etc/network/if-up.d/ as soon as a network becomes available, so all we need is a script there that starts mythfrontend. Only drawback is that mythfrontend will start (again and again) whenever a connection becomes up.

To do this I created this rather ingenius piece of script:

```

#!/bin/sh
#
# Start mythtv as soon as the network is up
#

sudo -u yourusernamehere -i DISPLAY=:0.0 /usr/bin/mythfrontend --service

```And placed this script as start-mythtvfrontend in /etc/network/if-up/ (make sure you are root as you edit the file, as only root can write stuff here). Be sure to change 'yourusernamehere' to your username.

The script has a sudo because the NetworkManager executes things as root. The DISPLAY environment variable makes sure the frontend pops up in the gnome (or what windowmanager you have)

Also, make sure the script is executable:
```
$ sudo chmod a+x /etc/network/if-up.d/start-mythtvfrontend
```Notsure what happens if someone with a different user name logs in, I suspect nothing because I think your user can't do anything on display :0.0 if this display belongs to another user.

---

### Post by nickrout on 2009-04-26
or get rid of networkmanager and use the traditional method of starting network services at boot (ie not at logon) by using /etc/network/interfaces

---

### Post by SnafuFlux on 2010-07-10
digging up an old thread.

I have this issue with my front end.  without fail, every time I boot, mythtv loads prior to the network manager being fully initialized.  

Is #3 of the second post still the preferred method?  If so, how the hell do I do it?  I have no idea how to manually configure the network services

---

### Post by ian dobson on 2010-07-10
Hi,

Network-manager is evil, if your running a server of any type. You shouldn't expect a application to start and at the same time start up the networking.

Just configure your network through /etc/network/interfaces and all will be well.

On every ubuntu desktop that I install, the first thing that I do is uninstall network-manager, and I've done about 25 boxes in the last few months (Simple email/internetboxes and normal users getting pissed off with windows/viruses)

Regards
Ian Dobson

---

### Post by nickrout on 2010-07-10
```
sudo aptitude remove network-manager-gnome
```

change /etc/network/interfaces to something like this:

> auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp

this assumes eth0 is your network interface and it gets it's config via dhcp.

---

### Post by SnafuFlux on 2010-07-10
the above code works, but it still loads to fast.  I still keep getting the setup screen for mythfrontend.   I can cancel out of it and load again, and it'll load.

---

### Post by ian dobson on 2010-07-11
Hi,

Then maybe just add a short delay (sleep 5) to the mythfrontend script, this script calls the mythfrontend.real after setting up the environment.

Regards
Ian Dobson

---

### Post by SnafuFlux on 2010-07-11
I would love to do this.  but I don't know how.  my linux skills are limited, at best.

---

### Post by ian dobson on 2010-07-11
Hi,

OK you need to edit the file  /usr/bin/mythfrontend using a simple editor (I imagine you'll need to be root), so go to a terminal window and type:-

sudo nano  /usr/bin/mythfrontend

the start of the file looks like this:-
```
#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007

pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

#source our dialog functions
. /usr/share/mythtv/dialog_functions.sh

#find the session, dialog, and su manager we will be using for display
find_session
find_dialog
find_su

#check that we are in the mythtv group
check_groups

#create a symbolic link for mysql.txt so it can't be overwritten
mkdir -p $HOME/.mythtv
if [ ! -e $HOME/.mythtv/mysql.txt ]; then
        ln -s /etc/mythtv/mysql.txt $HOME/.mythtv/mysql.txt
fi

if [ "$1" = "--service" ]; then
    #source frontend session settings
    if [ -f /etc/mythtv/session-settings ]; then
        . /etc/mythtv/session-settings
    fi
```

use the cursor keys to move down to the line above pidof mythfrontend.real " and enter "sleep 5". Now press control X to exit say yes to save and leave the filename the same.

Thats it, not too hard really.

Regards
Ian Dobson

---

### Post by SnafuFlux on 2010-07-12
hah, while I appreciate your detailed instructions.  I only meant, I didn't know where the startup script was.

this is perfect.  I shall try this when I get home.

thanks.

---

### Post by SnafuFlux on 2010-07-12
great success!  thanks all.  I found sleep 7 seems to be the sweet spot.

---


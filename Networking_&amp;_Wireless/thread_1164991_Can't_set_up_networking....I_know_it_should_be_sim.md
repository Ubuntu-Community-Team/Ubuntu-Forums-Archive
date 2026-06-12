---
title: "Can't set up networking....I know it should be simple...."
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by ozguitarplayer on 2009-05-20
Hi, 
i have for a while now tried to set up networking between 3 Hardy Heron computers.
I understand that I need to go to the folder to be shared, select properties then share and set the preferences.

This allows me to find the shared folders on the other computers however I cannot open them, I get a message 'Failed to mount windows share', so it's no go each time no matter what I try.

I can do it using samba and smb4k however I'd prefer to use the Ubuntu networking rather than Kubuntu applications..not that I have anything against Kubuntu.

Any help would be appreciated...

---

### Post by superprash2003 on 2009-05-20
try accessing them this way , its a nautilus bug [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by ozguitarplayer on 2009-05-20
thanks for that, I followed that link however I ended up at the same point where I can see the folders on the other computer but cannot open them...at no point am I asked for username and password...should I be asked for these?

---

### Post by superprash2003 on 2009-05-21
not necessarily , are you accessing by ip?? have you tried accessing directly? like , smb://x.x.x.x/sharename

---

### Post by ozguitarplayer on 2009-05-21
I didn't know that was possible until yesterday and if I'm correct I just type it into the search panel of Nautilus.....if this is correct then the search has no result.
am I supposed to use Network Settings in System > Administration?

---

### Post by superprash2003 on 2009-05-22
yes that is possible, what exactly did you type?

---

### Post by ozguitarplayer on 2009-05-22
typed...
smb://192.168.1.104/media/Niles/Downloads

tried to open other files also..all with no luck

---

### Post by doas777 on 2009-05-22
> **ozguitarplayer said:**
> typed...
smb://192.168.1.104/media/Niles/Downloads

tried to open other files also..all with no luck

ok, did you share the media directory?

---

### Post by ozguitarplayer on 2009-05-22
by that do you mean did I share it by right clicking and going into properties and setting the share options...which I did...and also using the samba gui

---

### Post by ozguitarplayer on 2009-05-22
doas777, I just reread your reply...no I didn't share the /media directory just some directories in /media...if I need to share Downloads in /media/Niles/Downloads do each of the directories along the way need to be shared also...as you can see I'm neww to this.

---

### Post by superprash2003 on 2009-05-22
go to the pc which has all these shares, and in that terminal type **smbtree** and post output here

---

### Post by ozguitarplayer on 2009-05-22
output from smbtree

nigel@MasterHeron:~$ sudo smbtree
[sudo] password for nigel: 
Password: 
WORKGROUP
	\\MUSUBU         		MusUbu server (Samba, Ubuntu)
		\\MUSUBU\iP3000         	Canon iP3000
		\\MUSUBU\PDF            	PDF
		\\MUSUBU\IPC$           	IPC Service (MusUbu server (Samba, Ubuntu))
		\\MUSUBU\Tabs           	
		\\MUSUBU\StuStuff       	
		\\MUSUBU\mp3            	
		\\MUSUBU\Keyboard       	
		\\MUSUBU\print$         	Printer Drivers
	\\MASTERHERON    		MasterHeron server (Samba, Ubuntu)
		\\MASTERHERON\iP4600_series  	Canon iP4600 series
		\\MASTERHERON\PDF            	PDF
		\\MASTERHERON\IPC$           	IPC Service (MasterHeron server (Samba, Ubuntu))
		\\MASTERHERON\NiFiles        	
		\\MASTERHERON\Keyboard       	
		\\MASTERHERON\StuStuff       	
		\\MASTERHERON\Tabs           	
		\\MASTERHERON\mp3            	
		\\MASTERHERON\print$         	Printer Drivers
	\\LAPUBU         		LapUbu server (Samba, Ubuntu)
		\\LAPUBU\desktops       	
		\\LAPUBU\Canon4600      	Canon4600
		\\LAPUBU\iP4600_series  	Canon iP4600 series
		\\LAPUBU\PDF            	PDF
		\\LAPUBU\IPC$           	IPC Service (LapUbu server (Samba, Ubuntu))
		\\LAPUBU\Downloads      	
		\\LAPUBU\NilesLapTop    	
		\\LAPUBU\print$         	Printer Drivers
nigel@MasterHeron:~$ 

how come they have back slashes?

have to go work for about 4 hours....

---

### Post by superprash2003 on 2009-05-22
smb://192.168.1.104/media/Niles/Downloads is invalid as its not something that has been shared.. try one of the shares given in the smbtree output , but instead of \\ use smb://

---

### Post by ozguitarplayer on 2009-05-22
smb://192.168.1.104/media/Niles/Downloads 
I used this which is the full address to /Downloads because I wasn't sure if I had to.
also tried; smb://192.168.1.104/Downloads without any luck, I have been using // each time, it is only the output from terminal that had the \\

---

### Post by ozguitarplayer on 2009-05-22
allow me to re-explain...each computer recoginizes the shared folders on the other computers, I am just unable to mount them using Places > Network, however having said that, the print$ that is there by default will always open without a problem. does this help?

---

### Post by superprash2003 on 2009-05-23
is 192.168.1.104 = LAPUBU?  is firestarter or anything similar installed?

---

### Post by ozguitarplayer on 2009-05-23
Yes, 192.168.1.104 = LAPUBU
firestarter is not installed, I haven't installed anything similiar, and I don't know if anything is installed by default when installing the operating system

---

### Post by doas777 on 2009-05-23
ok, the path you want is:
smb://192.168.1.104/Downloads

---

### Post by ozguitarplayer on 2009-05-23
thanks, however that has been tried with no result...bit of a mystery

---

### Post by ozguitarplayer on 2009-05-23
if anyone has the time can you step me through how you would set up sharing between two Ubuntu 8.04 computers of your own please..

---

### Post by doas777 on 2009-05-23
I've never been able to get it to work reliably with the user-space sharing that you can use with the GUI tools. 

check out this guide on setting up the smb.conf: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I have an smb.conf customized for my network that i tweak a touch for each new machine, and add the share definitions at the bottom. it's not perfect (browsing will always be touchy i think) . start building your own template and it'll help you our a lot.

also if you wanna run samba without using user-space sharing, you will not be able to use network-manager, unless you add ```
gksu /etc/init.d/samba restart
```  to your "StartUp Applications" list. since the samba service will attempt to start at boot, but the network interface it binds to won't exist until after login, so samba will exit. the best answer to this problem for a server is to take network-manager out of the mix, (/etc/network/interfaces).

heres a summary of my experience on the differance between gui sharing (user space) and configuring the samba service traditionally. please keep in mind, this is just my experience. your milage may vary.

Userspace sharing:
Pros:
use a gui to share folders
don't need to use sudo/gksu to create shares
works with user-space network manager
Cons:
only runs when user is logged in.
seems unreliable
problematic for sharing directories not owned by the sharing user (or out of the home dir).
the gui does not seem to do everything needed to share a dir by itself.

Service sharing:
Pros: 
runs all the time that the PC is booted. no one need be logged in at all.
works well for shares within users profile or without.
reasonably reliable.

Cons: 
configuration uses a text file that the administrator will need to configure
administration requires sudo/gksu

---

### Post by ozguitarplayer on 2009-05-23
thanks doas777, I'll think on all that and start it all again

---


---
title: "File backup from Windows to Linux with Samba"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Volume on 2009-12-29
Hey everyone.

I'm in the process of setting up my Samba server (Ubuntu) to connect with my 2 Windows machines.  What I am trying to do is be able to use the Linux machine for file backup--and file serving.

Can anyone offer any advice as to how, or what programs I could use to get this done?  From the forums, I saw some recommendations to use rsync, and maybe some scripts, but I am not sure how to do that.

Any advice?

Volume

---

### Post by metalf8801 on 2009-12-29
Hmm this sounds like a great idea and its like something I'm already doing only I'm only backing up file manually
I used webmin  [www.webmin.com/](www.webmin.com/) to set up my samba file server the web interface is really nice to have 

for the rest (which I haven't done but I would really like to know how it goes for you so please post your results!) I found this in the community documentation 
[https://help.ubuntu.com/community/BackupPC](https://help.ubuntu.com/community/BackupPC)

---

### Post by Volume on 2009-12-29
FYI, I currently have SAMBA working--I am able to access the "Public" Folder on my two vista boxes from Linux at this time.

Here is my smb.conf file if it helps anyone out:

```
[global]
    ; General server settings
;	netbios name = Engineer
	server string = 
	workgroup = WORKGROUP
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

;	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
	path = /home/mokrunka/Windows
;	browseable = yes
;	writeable = no
	create mask = 0644
;	directory mask = 0755
	force user = mokrunka
	force group = mokrunka
	valid users = mokrunka, nobody
```


Note at this time, since my Windows boxes are not password protected, I do not require a password to browse the share folders

Hope that helps

---

### Post by metalf8801 on 2010-01-05
here is a program that runs on windows that works with rsync 
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

and if that doesn't work for you or isn't what you want take a look at this site [http://www.downloadsquad.com/2008/10/12/13-great-free-backup-programs-for-windows-mac-and-linux/](http://www.downloadsquad.com/2008/10/12/13-great-free-backup-programs-for-windows-mac-and-linux/)

I hope this stuff helps 
Dan 

PS please post and results you have

---

### Post by shairozan on 2010-01-05
If you're looking at backing up Windows to a Linux source, it may be easier for you to manage the actual backups in windows. 2brightSparks provides a great freeware application called syncback that you can use for your backup. It will allow you to select directories to backup, where to back them up to, and then run on a schedule. Might be easier than trying to pull from the server. 

[http://www.2brightsparks.com]("http://www.2brightsparks.com")

---

### Post by pricetech on 2010-01-05
I agree with doing the backups from winders, assuming I am understanding what you're looking to accomplish.

SyncToy, a free download from ms, works for me.  It's not automated, but I've not had it fail me synchronizing my date between here and home using my thumbdrive to carry it from place to place.

---

### Post by mendo on 2010-01-05
i just finished (will i ever really be done messing with it?) setting up an ubuntu server for file serving and am trying to come up with a backup strategy as well.

synctoy can't write to my samba shares for some reason.

dos xcopy scripts seem to have the same problem.

i cannot figure out what i'm doing wrong with synctoy or xcopy.

i am going to explore the rsync & 2brightsparks options.

i will be back here to share feedback.  great thread.

---

### Post by pricetech on 2010-01-05
Can you write to the shares manually ??  May be a permissions problem having nothing to do with what software you are using.

---

### Post by shairozan on 2010-01-05
I agree. The first thing to check would be whether or not you can manually copy files across. If you receive an error attempting to manually move files, there's more than likely a permissions issue that you'll have to address. 

Do you have guest browsing and guest read write enabled, or are samba users and passwords required for the setup. Also, is there a reason the MyFiles directory on the samba server has 

browseable = yes commented out along with writeable=no? Might want to set it to being a writeable directory. Just to help me out with the whole flow, are you backing up from your Vista machines to the MyFiles directory on the samba server, or somewhere else?

---

### Post by mendo on 2010-01-05
syncback SE isn't free.  it's a 30 day trial.  bummer.

---

### Post by shairozan on 2010-01-05
It is free, but SE isn't. SE includes some nuts and bolts that aren't necessary. 

[http://www.2brightsparks.com/downloads.html#](http://www.2brightsparks.com/downloads.html#)

If you click on downloads at the top there is an option for freeware. That's where they list the free version.

---

### Post by mendo on 2010-01-05
i think this ought to be as easy as some scheduled .bat files on the windows side using xcopy.  the only thing i can't figure out is why xcopy commands from the c: prompt will return:

"Access denied
Unable to create directory - z:\xxx"

for some directories when i can drag the same directory over to the server from windows.

if i could figure that out, then i would be all set.

i think that would be a lot easier than learning rsync, though i may end up doing that eventually anyways.

---

### Post by mendo on 2010-01-05
It IS free!  i'm running a hastily created backup right now.  it's copying My Documents to a Samba share on the ubuntu server w/o any issues.  i'll keep working with it and report my findings.  hooray!

thanks shairozan!

---

### Post by mendo on 2010-01-05
it's wonderful!  i don't even have to have the network drive mapped on the winxp machine.  sweeeeet.

---

### Post by shairozan on 2010-01-06
Haha not a problem! We use it as a user backup solution where I work. We push the program down to everyone through the group policy and force a variable based syncback profile. Keeps everyone's my docs, desktop, favorites, and some more constantly backed up :) It's a good piece of software.

---


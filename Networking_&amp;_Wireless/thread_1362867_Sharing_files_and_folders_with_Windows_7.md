---
title: "Sharing files and folders with Windows 7"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by theboyparker on 2009-12-23
Hi, total newbie to Ubuntu, but i thought i would give it a try :)

I'm trying to use Ubuntu desktop on an old computer, so that i can store all my media files etc on it, but im having trouble getting Windows 7 (installed on a laptop) to pick up the shared folder.

Can someone tell me in plain english how to do this, i've read several posts on here but nothing seems to work!

A step by step would be good:confused:

Thanks 

Stew

---

### Post by Morbius1 on 2009-12-23
Can you post your share definition please:

Open **Terminal**
Type** net usershare info**
Type **sudo net usershare info**
Type [B]tertparm -s

[/B][COLOR=Blue]EDIT: there's one more command that will tell us if the Win7 firewall is in the way:[/COLOR]

**nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the linux machine.*[/COLOR]
You probably don't have nmap installed but issuing the above command will prompt you if you want it installed .

---

### Post by theboyparker on 2009-12-27
Hi thanks for the reply

the first command gives me

[pictures]
path=/home/stewart/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

and so on for each folder i've shared including

[stewubuntu]
path=/home/stewart
comment=
usershare_acl=Everyone:F,
guest_ok=n

the second command asks me for my password which i enter and then returns back to the promt,

the third command tells me that "no command tertparm found, did you mean etc..."

the forth on gives

   *[SIZE=2]Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-12-27 18:15 GMT[/SIZE]*
    *[SIZE=2]Interesting ports on office.home (192.168.1.71):[/SIZE]*
    *[SIZE=2]Not shown: 997 closed ports[/SIZE]*
    *[SIZE=2]PORT     STATE SERVICE[/SIZE]*
    *[SIZE=2]139/tcp  open  netbios-ssn[/SIZE]*
    *[SIZE=2]445/tcp  open  microsoft-ds[/SIZE]*
    *[SIZE=2]5900/tcp open  vnc[/SIZE]*
    
    *[SIZE=2]Interesting ports on 192.168.1.253:[/SIZE]*
    *[SIZE=2]Not shown: 998 closed ports[/SIZE]*
    *[SIZE=2]PORT    STATE SERVICE[/SIZE]*
    *[SIZE=2]139/tcp open  netbios-ssn[/SIZE]*
    *[SIZE=2]515/tcp open  printer[/SIZE]*
    
    *[SIZE=2]Interesting ports on api.home (192.168.1.254):[/SIZE]*
    *[SIZE=2]Not shown: 997 filtered ports[/SIZE]*
    *[SIZE=2]PORT     STATE SERVICE[/SIZE]*
    *[SIZE=2]80/tcp   open  http[/SIZE]*
    *[SIZE=2]443/tcp  open  https[/SIZE]*
    *[SIZE=2]1723/tcp open  pptp[/SIZE]*
      
  *[SIZE=2][FONT=&quot]Nmap done: 1024 IP addresses (3 hosts up) scanned in 47.29 seconds[/FONT][/SIZE]*  

[SIZE=2]Any ideas??[/SIZE]


Cheers 



Stew

---

### Post by Morbius1 on 2009-12-27
That should have been **testparm -s**. My appologies.

---

### Post by Morbius1 on 2009-12-27
I noticed that you do not have guest access enabled on the two shares you posted.

Are they all like that?

If they are did you create users on your Linux box to correspond to the users that you are requiring authentication from?

Can Win7 see the linux box and not gain access to the share, or can Win7 not even see the linux box at all?

---

### Post by theboyparker on 2009-12-27
Hi the Testparm came back with the following

   *Load smb config files from /etc/samba/smb.conf*
  **
  *Processing section "[printers]"*
  **
  *Processing section "[print$]"*
  **
  *Processing section "[Music]"*
  **
  *Loaded services file OK.*
  **
  *Server role: ROLE_STANDALONE*
  **
  *[global]*
  **
  *            server string = %h server (Samba, Ubuntu)*
  **
  *            map to guest = Bad User*
  **
  *            obey pam restrictions = Yes*
  **
  *            pam password change = Yes*
  **
  *            passwd program = /usr/bin/passwd %u*
  **
  *            passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .*
  **
  *            unix password sync = Yes*
  **
  *            syslog = 0*
  **
  *            log file = /var/log/samba/log.%m*
  **
  *            max log size = 1000*
  **
  *            dns proxy = No*
  **
  *            wins support = Yes*
  **
  *            usershare allow guests = Yes*
  **
  *            panic action = /usr/share/samba/panic-action %d*
  **
    * *
  *[printers]*
  **
  *            comment = All Printers*
  **
  *            path = /var/spool/samba*
  **
  *            create mask = 0700*
  **
  *            printable = Yes*
  **
  *            browseable = No*
  **
      [I]            browsable = No 
[/I]
  * *
  *[print$]*
  **
  *            comment = Printer Drivers*
  **
  *            path = /var/lib/samba/printers*
  **
  * *
    *[Music]*
  **
  *            path = /home/stewart/Music*
  **
  *[FONT=&quot]            guest ok = Yes[/FONT]*

---

### Post by theboyparker on 2009-12-27
> **Morbius1 said:**
> I noticed that you do not have guest access enabled on the two shares you posted.

Are they all like that?

If they are did you create users on your Linux box to correspond to the users that you are requiring authentication from?

Can Win7 see the linux box and not gain access to the share, or can Win7 not even see the linux box at all?

Hi, yes they are all like that,

No i didnt creat the user to match, should i have?

and no Win7 cann ot see the drive, but this is intermittant, sometimes it can others it can't. Not sure why though!

thanks for your replies

Stew

---

### Post by Morbius1 on 2009-12-27
I don't know at the moment if this will fix the problem but let's try a few things.

One, there are two ways to share folders in linux and you seem to be using both. Worse you seem to be overlapping methods:

*/home/stewart/Music* allows guest access

/home/stewart does not.

I would unshare /home/stewart/Music and /home/stewart.

When you're done with that open a Terminal and type: **sudo service samba restart**


Second, I would try something simple first. 
Open Nautilus
Right click on a folder that you have not shared yet, let's say it's /home/stewart/Documents.
Check off all the boxes including guest access

Now see if you can see the documents share from Win7

---

### Post by theboyparker on 2009-12-27
Ok i've got the icon within Network on Win7, but when i click on it it comes up with an error message saying "Windows cannot Access \\MEDIA

I've had this before and gone through the the diagnose part but still nothing.

Sorry for being a pain

Stew

---

### Post by Morbius1 on 2009-12-27
Just to make sure I understand what's been done.

(1) If you do a testparm -s again is this gone:
> *[Music]*
  
  *            path = /home/stewart/Music*
  
  *[FONT=&quot]            guest ok = Yes[/FONT]*

(2) I don't know how many shares you created but can you post the entire output of **net usershare info** 

(3) Is \\MEDIA the name of the Linux box?

---

### Post by Iowan on 2009-12-27
Ordinarily, the /home directories are owned by the individual user (*/home/stewart* is owned by stewart). Samba cannot relax permissions - only tighten them. You may need to make the directory accessible (via **chmod**) or move the files to a directory which can be accessed by anyone.

---

### Post by theboyparker on 2009-12-27
1st question is a no, its still there.

I've attached the net usershare info in a doc...

and \\media is the name of the box.

thanks

stew

---

### Post by Morbius1 on 2009-12-27
OK. Let me read the attachment. In the mean time let's get rid of the smb.conf share:

Open **Terminal**
Type [B]shares-admin
[/B]
Go to the "Shared Folders" tab > select the Music share > and click on the Delete button. This will remove the share ( not the actual folder ).

I don't know if the shares-admin utility automatically restarts samba so 
Open **Terminal**
Type **sudo service samba restart**

Wait abour 4 minutes and see if that itself allows Win7 to see the rest of your shares. I don't think this by itself will fix it but you never know.

---

### Post by Morbius1 on 2009-12-27
There's only one share defined in your attachment. Should there have been more?

What happened to these:
> [pictures]
path=/home/stewart/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

and so on for each folder i've shared including

[stewubuntu]
path=/home/stewart
comment=
usershare_acl=Everyone:F,
guest_ok=n

---

### Post by Morbius1 on 2009-12-27
> **Iowan said:**
> Ordinarily, the /home directories are owned by the individual user (*/home/stewart* is owned by stewart). Samba cannot relax permissions - only tighten them. You may need to make the directory accessible (via **chmod**) or move the files to a directory which can be accessed by anyone.

That's where the simplicity of nautilus-share becomes evident. It will modify permissions for you automatically.

For example, try this yourself:
mkdir /home/Iowan/test
chmod 0700 /home/Iowan/test

Now go to nautilus, right click on /home/Iowan/test
Select "Sharing Options" > Select "Share this folder", and "guest access", then "Create Share"

You'll notice that the permissions changed from 0700 to 0755
If you want write access it will change from 0700 to 0777

The permission change isn't recursive but nautilus-share even has a way of fixing that without doing a chmod.

[COLOR=Blue]EDIT: You know I just looked at your avatar and noticed you're using 8.04. I don't know if 8.04 has nautilus-share implemented.[/COLOR]

---

### Post by theboyparker on 2009-12-27
> **Morbius1 said:**
> There's only one share defined in your attachment. Should there have been more?

What happened to these:

Sorry i removed them, i thought it best to start afresh! I can re-do them if needed.

i've also just removed the shares from the Shares-admin command you put, so i will let you know hoe i get on in approx 5 min lol

cheers

Stew

---

### Post by theboyparker on 2009-12-27
Ok, i've let it for a few min, and although i get the icon in the Networking page, when i double click on it, it keeps coming up with an error message, the same one as before "Windows cannot Access \\MEDIA"

any more ideas?

cheers

stew

---

### Post by theboyparker on 2009-12-29
For some unknown reason and a little playing around with a few things last night, i eventually got the sharing to work with Win7. God knows how, but i'm sure it must have been something you told me to do, so a big thanks....:)

---

### Post by Morbius1 on 2009-12-30
In the last 2 weeks there have been about a half dozen ( possibly more ) posts on Win7 ( specifically ) / Linux networking problems - all of then unsolved. If you ever figure out what you did to get it to work post it here. You'll be loved and admired and heralded a hero.

---

### Post by theboyparker on 2009-12-30
I've have a look today and try to remember what i've done, i need to get it working on the other halfs Vista laptop so that might be another issue :(

---


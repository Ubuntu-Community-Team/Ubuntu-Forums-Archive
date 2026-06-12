---
title: "accessing NAS via router - RHYTHMBOX can do it but nothing else!"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Nibbos on 2010-05-30
Hi,
I'm new to Ubuntu, just installed 9.10 and was amazed that (nearly) everything worked first time...
However, I cannot access any of the files/folders on the family NAS box (WD MyBookWorld) connected to my Ubuntu machine via Netgear router (wired).
I can get internet fine and, bizarrely, Rhythmbox media player has found the 'Shared Music' folder on the NAS so I'm typing this whilst listening to music from the NAS box.
However, I can't browse to any files/folders on the NAS.
I can't get to them via 'Places > Network > Windows Network > Workgroup' - all I get is 'Unable to mount location: Failed to retrieve share list from server'
I've read many pages of 'help' about samba/nfs etc. and tried editing various files around the place, but nothing seems to work.
Why is it that Rhythmbox 'found' the NAS box and can access it but I can't get near it?
Thanks in advance for any assistance.
If you can also get my windows machine to 'see' the printer attached to my Ubuntu machine that would also be nice!

Nibbos

PS I can access both the router and the control panel for the NAS box via Firefox browser '192.168.1.XXX'
I can also PING the ROUTER and NAS box successfully.

---

### Post by Iowan on 2010-05-30
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To *might* help.

[Here]("http://ubuntuforums.org/showthread.php?t=1467071") is a similar thread to check.

---

### Post by Nibbos on 2010-05-30
Thanks for the links - but been there and tried that...

What is bizarre is that I did manage once to connect via 'Places > Network > Windows Network > Workgroup' and then got into the MyBookWorld. It even created a desktop shortcut to it!
However, the next time I booted up it had disappeared and the ability to get in via 'Places' had gone!
This is really pi**ing me off because I can't ubderstand how Rhythmbox manages to see all my music files but I can't get anywhere near the NAS box at all!

Nibbos

---

### Post by Jeroensum on 2010-05-30
The reason for your rhythmbox to detect the NAS is probably because the NAS broadcasts it's presence trough mDNS aka autoconfig. This has nothing to do however with the smb/cifs or nfs protocol.

The NAS has dissapeared from your Places because it needs to be mounted first which is a manual action you will need to perform.

To try and see if your linux box can 'see' the NAS trough the SMB/CIFS protocol, open up a terminal and type:  smbtree , give in your own password when asked.
If all goes well, you should get a listing of all the windows boxes and their shares, on your current subnet.

If this lists the share(s) of the NAS then you should be able to mount a share, if it doesn't just be stubborn and give it a go anyway like so:
mkdir music
sudo mount -t smbfs //NAS/music music -o username=validusername,password=validpassword


If your box starts talking trash and calling you names for not being able to mount ;), try adding smbfs support to your system:
sudo apt-get install smbfs
This will most probably install 2 packages, after which you may try again. :)

If it still won't work, there may be a problem with nameresolving, just try using the IP of the NAS instead of it's hostname.

After a reboot however, your mount will be gone, the only rauncy remedy for this is to add a line to your /etc/fstab including your (plaintext) password. I'll tell you how in my next post, please first let me know if this is working for you :)

Footnote for knowledge:
SMB is the younger stepbrother of CIFS, MS introduced CIFS a few years ago to overcome some security issues aswell as a few technical problems (2gb file limit for one).

---

### Post by Nibbos on 2010-05-31
OMG - your advice worked!

I managed to make directory  /media/mybookworld/

then I did the 'sudo mount' thing, but it failed using the 'mybookworld' name so I replaced this with the IP address and it liked it!

I just tried saving a file to it from an OpenOffice app and I could browse to the /media/mybookworld/ folder and IT WAS IDENTICAL to the contenets on the actual mybookworld!

(I had tried this method previously but kept getting 'access denied' errors. Then I tried putting the username and password for the MyBookWorld, but that didn't work. It seems that you have to put the username and password for THIS i.e. ubuntu, machine to make it work...)

So, next task is to edit the '/etc/fstab' file to make this mount on bootup. One concern, though, if I have to enter my password in plaintext, is that not easily findable by someone, since I guess it's a well-known procedure to have drives mounted on boot-up and lots of passwords in plaintext files can't be a good thing, can it?

Thanks thus far, awaiting your next instalment with bated breath. The wife and kids will love me (even more!) if I can get this problem fixed.

Many thanks again, Jeroensum.

Nibbos

[Note: I have been able to browse the MyBookWorld because I did a 'Windows Share' from the 'Places' menu, this gave me the mybookworld in the Nautilus browser and added a shortcut to the desktop - however, this did not make the mybookworld visible to applications, hence my initial posting. The Windows SHare also re-appears on boot-up so it's been useful so far, but not to apps that need to save things on it!]

---

### Post by Jeroensum on 2010-06-01
Great to hear that you're now able to access all your files again, you're welcome :)

Adding a line including your password would indeed allow anyone with a useraccount on your linux machine to discover your password for the MyBooKWorld share. You could ask yourself how much of a problem this is regarding the fact probably only you, your wife/kids and maybe a relative or friend would be using your machine. But that's ultimately up to you. so I will provide you with several options to try.

1.) 
Check if your apps really can't find the share. You say that you can mount it trough the Places->Windows Share option. If that share is usable/accessable for you then all you should need to do in any application is point it to:
~/.gvfs/<name of the share you see in nautilus>

(The ~/ is a reference to your homedir, if you enter cd ~/ in bash you would end up in your homedir, it's a nice shortcut)  :)

To make things easier you could make a symlink (kind of like a shortcut in windows) in your homedir to the directory like so:

ln -s /home/jeroensum/.gvfs/sharename/ /home/jeroensum/music
(mind the / at the end of the sharename, it really needs to be there)

2.)
Do as i suggested and add a line to your /etc/fstab like so:
//bookworld/share /media/mybookworld/ smbfs credentials=/etc/cifspw 0 0
Next, make a file in /etc named cifspw with these contents:
username=bookworld_username
password=bookworld_password
Reboot or use (as root):  mount -a

3.)
I wrote a small script which connects to samba shares and let's you enter a password when needed (graphically).

```

#!/bin/bash
#Adding a few needed variables:
share=//mybook/share
mount=/your/local/mountpoint
username=mybook_username
#Getting the password for the share
pass=$(zenity --entry --title="MyBookWorld $share mount" --text="Please enter your MyBookWorld password for user: $username" --hide-text)
#Asking for permission and mounting the share
gksudo -D MyBookWorldMounter "mount -t smbfs $share $mount -o username=$username,password=$pass"
#Dropping the privileges 
sudo -k

```

Just edit the variables so they match your environment and you're done.

Which ever one you pick, they all should work :) I'll check back here if it all worked out for you :)

---

### Post by Nibbos on 2010-06-01
Thanks again.

I'll look at some of those options.

Having quickly scanned your suggestions there is one thing that still puzzles me.

You talk about the password to MyBookWorld share. However, the password I put in the 'mount' command was the one for my ubuntu machine. I do have a password for the admin account on the MyBookWorld, but that hadn't seemed to have worked when I tried previously.

Am I getting this right or have I misunderstood something?

Regards

Nibbos

---

### Post by Nibbos on 2010-06-01
[solved]

OK. All working tickety-boo!

edited fstab, made credentials file (although elsewhere I see permissions as sometimes 0400, sometimes 700 - don't really understand what this means...)

used password to ubuntu machine - worked fine, or possibly no password needed? - again, don't really understand...)

re-booted and saw a shiny new 'drive' on my desktop, called 'mybookworld'.

I can browse in it, other applications can see it.

I guess if it works I'll just leave it at that!

Thanks for your altruism and patience.

Regards

Nibbos

---


---
title: "Samba public share, XP Guest is asked for password"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by semmelbroesel on 2009-03-20
Hi,
I just installed my first Ubuntu Server (I am pretty much a beginner in Linux) and used a lot of the information I found here to setup my Samba share, so thanks for all the posts everyone is making!

It seems to work well now after some difficulties, except when I try to connect from my laptop running Windows XP Pro.

Here's the situation:
I am running VMWare Server and installed Ubuntu on a VM - this will be my "training grounds" for when I install the same onto an actual PC to act as my new file server at home.
I have another VM with Windows XP Pro on it, and I have no trouble using the share.
But on the actual computer that is running the VMWare server I cannot get in, and I have a suspicion.

I setup the share to be 100% public and open, using Share security. I want this to become our file server that can be accessed from any computer in my house.

When I attempt to open the shared folder on this laptop using XP Pro, I cannot simply get in anonymously, but I am asked for a password for the user Guest, and I cannot change the user. On my other XP Pro VM, it never asks for a password.

The main user I setup in Ubuntu is the same user name that my Windows XP Pro laptop uses, so I have a suspicion that this could be the issue. The XP VM does not have a password set and has a different main user name.

So now my questions are:

1. Is my suspicion correct? Am I getting prompted for a guest password because the two computer already established that they are using the same user name but different password?

2. What would you suggest as a solution? Can I setup a Guest password even though I do not want any passwords to be used? Or would it be easier just to set my Ubuntu password to the same as my Windows password? Or change the main user name in Ubuntu?

Here's my smb.conf file:


[global]
    ; General server settings
    netbios name = testserver
    server string =
    workgroup = MUSIC
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   ; passdb backend = tdbsam
    security = share
    null passwords = true
  ;  username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    usershare owner only = false
    usershare allow guests = yes


  ;  wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[public]
  comment = Public Folder
  path = /home/richard/Public/share1/
  guest ok = yes
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = richard
  force group = nogroup



Thanks!

---

### Post by semmelbroesel on 2009-03-20
After testing a little, I found something else that I don't understand.
On my VM XP system I originally only had one user setup that automatically opens on Windows boot.
As soon as I create a second user and log in as that user, I again get prompted for a Guest password, no matter what the user name is, and even if I go back to the original user.
Only reverting the VM to its previous state gets me back in normally.

On the other hand, if I tell XP to map the share into a network drive letter, then it always works first try.

I would still like to avoid the Guest password query, though, because sometimes I will want to access shares that are a little more "hidden" than others - our pictures will be mounted as a drive letter on my wife's computer, but my backup folder will not, and I may want to use //servername/sharename to access it from my own computer and through the backup software.

Thanks!

---

### Post by semmelbroesel on 2009-03-20
Aw geeze, I think I answered my own question, and I feel like an idiot...

It seems the problem was not the user name at all - it was that I had defined "public" as a share twice - once through smb.conf and once through the GUI - of course things got messed up!

I found the solution when I experimented with adding a second hard drive and sharing it as "share2", and I found that it worked without any problems.
So I renamed "public" to "share1" and found that now I had THREE shared folders:
public, share1 and share2
And public was shared through the GUI...
I turned that off, and now everything seems to work.

Sorry for the false alarm...

Hopefully someone will stumble into the same problem once and find my information here useful ;)

---


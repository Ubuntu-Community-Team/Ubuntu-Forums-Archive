---
title: "Smb share on desktop without pw?"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Error403 on 2009-01-30
Hi, I just reinstalled my box today, and I was wondering if there is a way to have an icon to my network share on the desktop, and make it remember my password because my kids don't want to guess all my passwords on it.

I'm ready to make a passwordless user on my smb box if I have to, but security would be a tad upper if my tv box could simply remember the password!  ;)

---

### Post by Error403 on 2009-01-31
bump

---

### Post by FishRCynic on 2009-01-31
see 
[http://ubuntuforums.org/showthread.php?t=449145](http://ubuntuforums.org/showthread.php?t=449145)
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

i.e.
try adding in fstab

//SERVER/SHARE	/mnt/folder smbfs dmask=777,username=,password=	 0 0



this would be more secure:
[http://anothersysadmin.wordpress.com/2007/12/17/howto-mount-samba-shares-in-fstab-using-a-credential-file/](http://anothersysadmin.wordpress.com/2007/12/17/howto-mount-samba-shares-in-fstab-using-a-credential-file/)


you might be better off using the actual ip address instead of the share name as samba with gvfs2 seems to be having issues - hardy and intrepid

this may be fixed already (i haven't automounted since october)
note: i have had past issues with this using wireless as the shares seem to load prior to the actual connection being made. 
sudo mount -a in terminal should load them to last as long as the session does - (you could make a script to run as the last item in session loading)

---

### Post by Error403 on 2009-01-31
I tried this but doesn't work:

```
#smbfs
//galactica/salon/pub /media/share smbfs dmask=777,username=myusernamegoeshere,password=mypasswordgoeshere 0 0
```

Any ideas?  I put it in /media/share for making "share" appear on the desktop.

Thanks!

---

### Post by FishRCynic on 2009-01-31
you might be better off using the actual ip address instead of the share name as samba with gvfs2 seems to be having issues - hardy and intrepid


//galactica/salon/pub /media/share smbfs dmask=777,username=myusernamegoeshere,password=mypasswordgoeshere 0 0

replace galactica with its actual co-ordinates :-}

ie for me it would 192.168.0.xxx where xxx is the last part of the actual machine address

i will try one myself
*********************************************************

change smbfs to cifs 
dmask=   to dir_mode=0

where TVshows is the directory to mount to

in terminal
mkdir /media/TVshows

in fstab
//192.168.0.xxx/shows /media/TVshows cifs dir_mode=0777,username=shareusername,password=sharepassword 0 0

this worked for me

will now try with netbios name

---

### Post by FishRCynic on 2009-01-31
netbios name did not work

so you would have to ensure that /media/share has been created first
eg in terminal
sudo mkdir /media/share

in fstab
//galactica/salon/pub /media/share smbfs dmask=777,username=myusernamegoeshere,password=mypasswordgoeshere 0 0

becomes

//xxx.xxx.xxx.xxx/sharename /media/share cifs dir_mode=0777,username=shareusernamegoeshere,password=sharepasswordgoeshere 00

where xxx.xxx.xxx.xxx is the network ip address of the sharing machine
and the sharename is the share name setup on the sharing machine.
the username and password come from the sharing machine

sharing machine = the my network share first mentioned in your post

---

### Post by Error403 on 2009-02-01
Hi again

I got it to kinda work the way you explain it, but for some reason my symbolic links are ignored. I don't understand that one; I thought they would be preserved.

So I tried this:
//192.168.2.90/salon /media/share cifs dir_mode=0777,username=salon,password=mypassword 0 0

and it works, but I don't see a symbolic link that I previously configured on the server as "pub" that is /mnt/archive/pub 

and if I try
//192.168.2.90/salon/pub /media/share cifs dir_mode=0777,username=salon,password=123 0 0

I get a mounted broken share in /media called /media/mnt/archive/pub

Honnestly that is beyond my understanding.
Any clues?

Thanks for the replies  ;)
btw "salon" is french for "living room" because it's a pvr pc under my tv, in the living room. So I called it "living room".

---

### Post by Error403 on 2009-02-01
AHAH!!! I found it!!

> Edit the configuration of your Samba server and disable unix extensions:

  /etc/samba/smb.conf:

    [global]
      unix extensions = no


here:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126723.html]("https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126723.html")

fixed the problem

> I'm surprised that the samba forums didn't have the answer.

I'm surprised it's not disabled by default! Made me scratch my head for a while! ;)

Also added _netdev:
> The option _netdev is always recommended for cifs mounts in fstab. Option _netdev delays mounting until the network has been enabled.
[http://www.swerdna.net.au/linhowtosambacifs.html]("http://www.swerdna.net.au/linhowtosambacifs.html")

---

### Post by FishRCynic on 2009-02-01
glad its working - bookmarked the link for future reference 
(i don't seem to need the _netdev option - comes up without it on this machine anyway - 8.10 amd64)

with the browsing issue(s) that nautilus / gvfs2 is having currently i guess i will adopt this myself to ensure quick access to my network shares

---


---
title: "Can't access Windows shares from Ubuntu 12.04"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by salrtivardfast on 2012-09-19
I run my laptop on a corporate IT network that is unfortunately totally  MS-centric. I had been running 11.04 happily for the best part of  a year and able to access all smb shares and cifs servers I required  access to. Last week I upgraded to 12.04, and suddenly I can only  access shares within the workgroup "WORKGROUP", which doesn't contain  anything useful. All attempts to access shared folders on servers in  other workgroups fail, either with errors like  "Failed to mount Windows share"  or  "Cannot display location "smb://xxxyyyy/"  Failed to  retrieve share list from server".    I'm using the various network GUI tools, as I'm too much of a wimp to use the smb/cifs mount commands.  

I did try editing samba.conf  and changing the "WORKGROUP" reference to the name of our main corporate  domain I need to access. Then I restarted Samba, but it didn't help at  all.

What the heck changed between these two versions in the smb/cifs client side??  I'm seriously considering reverting back to Natty....  :(

---

### Post by salrtivardfast on 2012-09-21
Bump time folks!  

In the past day or so, I've messed around with various samba.conf parameters, including changing the name resolve order, and as I expected saw no improvement.  I guess the smb client settings actually live somewhere else.  I also tried switching off the firewall, just in the unlikely case that was what was interfering with traffic to the main corporate domain.

 I also read somewhere that Samba has been changed to make it more secure,  and  I now suspect this is some kind of a permissions issue. The main corporate domain is visible but when you click on it in Gigolo, it gives the message,"**Failed to retrieve share list from server**". However, I do have full access rights into the Windoze servers in that domain and can access them from other machines running Win 7 or  my previously-installed Natty.  Anyone know what that's about?

So I unless a solution materializes today, the Pangolin gets it!  :twisted:

---

### Post by luvshines on 2012-09-22
Hi
Your shares reside on Windows machine and you are trying to access them from Ubuntu client, right ?
If yes, then you don't need 'samba' to be running on your client. Samba server is to be run only if one intends to create CIFS share on linux.

That being said, can you try listing/accessing the windows share from terminal
```

## List the shares
smbclient -L <windows-server-ip> -U<username>  ## It will prompt for password

## Access a share. Choose the one which you have access to from the list above
smbclient //<windows-server-ip>/<share-name> -U<username>  ## It will prompt for password

```

Is command line access working ?

---

### Post by ourkid2000 on 2012-09-24
I am interested in this thread as well. Last time I tried Ubuntu I could not access my Windows network shares. Is there any kind of tutorial on here? I have been searching quite a bit.

---

### Post by salrtivardfast on 2012-09-27
So far the only good fix I've been able to find is to run 11.04 - and that's what I've reluctantly now done.  It appears something got changed (more like broken) in the Samba client some time after 11.04. I tried 11.10 using a LiveDVD and appeared to be getting the same results.

I've seen this problem also reported in recent revs of other distros, such as Fedora.

@luvshines, I'll have to try your suggestion using a LiveDVD, since I'm no longer running Pangolin, although I suspect I won't see any improvement.

---

### Post by ourkid2000 on 2012-09-27
We can't be the only ones out there with this problem! LOL

---

### Post by gromacs on 2012-09-27
> **salrtivardfast said:**
> So far the only good fix I've been able to find is to run 11.04 - and that's what I've reluctantly now done.  It appears something got changed (more like broken) in the Samba client some time after 11.04. I tried 11.10 using a LiveDVD and appeared to be getting the same results.

I've seen this problem also reported in recent revs of other distros, such as Fedora.
 I'm experiencing the same problem with 12.04. I do recall being able to access shares on Windows Server just fine a couple years ago, so this makes sense to me that 11.04 and earlier would work. I suppose that's why many people are still using it lol.

I eventually found that the 'new' method is using cifs, something like this...
```
sudo mount -t cifs //SERVER/Public /mnt/Public -o username=gromacs,domain=gromacs,iocharset=utf8,file_mode=0777,dir_mode=0777
```
Obviously replace the paths to your server's share, path to an empty folder to mount said share, your username, and domain. You will also need to install a couple packages if you don't have them already, terminal will let you know which ones.

I'm not sure if it has anything to do with cifs, however file transfers for me go at 500kB/s on Ubuntu, while they go at 5mB/s on Windows. I'm not sure if it's because the drivers suck, access point wireless settings incompatibility, or just pebkac... hope to figure this out because even getting file lists are slow at these speeds lol.

---

